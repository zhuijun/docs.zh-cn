---
title: 类型等效性和嵌入的互操作类型
description: 了解 .NET 类型与具有托管程序集的成员之间的类型等效性，以及嵌入到该程序集中的 COM 类型。 适用于 .NET 4 及更高版本。
ms.date: 03/30/2017
helpviewer_keywords:
- type equivalence
- embedded interop types
- primary interop assemblies,not necessary in CLR version 4
- NoPIA
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
ms.openlocfilehash: a096c6bd0703c19c6049ad5ab2532b4b05f6ede0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558818"
---
# <a name="type-equivalence-and-embedded-interop-types"></a><span data-ttu-id="86b2b-104">类型等效性和嵌入的互操作类型</span><span class="sxs-lookup"><span data-stu-id="86b2b-104">Type equivalence and embedded interop types</span></span>

<span data-ttu-id="86b2b-105">从 .NET Framework 4 开始，公共语言运行时支持将 COM 类型的类型信息直接嵌入到托管程序集中，而不要求托管程序集从互操作程序集中获取 COM 类型的类型信息。</span><span class="sxs-lookup"><span data-stu-id="86b2b-105">Beginning with the .NET Framework 4, the common language runtime supports embedding type information for COM types directly into managed assemblies, instead of requiring the managed assemblies to obtain type information for COM types from interop assemblies.</span></span> <span data-ttu-id="86b2b-106">由于嵌入式类型信息仅包含托管程序集实际使用的类型和成员，因此两个托管程序集可能具有相同 COM 类型的不同视图。</span><span class="sxs-lookup"><span data-stu-id="86b2b-106">Because the embedded type information includes only the types and members that are actually used by a managed assembly, two managed assemblies might have very different views of the same COM type.</span></span> <span data-ttu-id="86b2b-107">每个托管程序集都有不同的 <xref:System.Type> 对象来表示其 COM 类型视图。</span><span class="sxs-lookup"><span data-stu-id="86b2b-107">Each managed assembly has a different <xref:System.Type> object to represent its view of the COM type.</span></span> <span data-ttu-id="86b2b-108">公共语言运行时支持接口、结构、枚举和委托等不同视图之间的类型等效性。</span><span class="sxs-lookup"><span data-stu-id="86b2b-108">The common language runtime supports type equivalence between these different views for interfaces, structures, enumerations, and delegates.</span></span>

<span data-ttu-id="86b2b-109">类型等效性意味着从一个托管程序集传递到另一个托管程序集的 COM 对象可以转换为接收程序集中适当的托管类型。</span><span class="sxs-lookup"><span data-stu-id="86b2b-109">Type equivalence means that a COM object that is passed from one managed assembly to another can be cast to the appropriate managed type in the receiving assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="86b2b-110">类型等效性和嵌入式互操作类型简化了使用 COM 组件的应用程序和加载项的部署，因为无需与应用程序一起部署互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="86b2b-110">Type equivalence and embedded interop types simplify the deployment of applications and add-ins that use COM components, because it is not necessary to deploy interop assemblies with the applications.</span></span> <span data-ttu-id="86b2b-111">如果共享 COM 组件的开发人员希望较早版本的 .NET Framework 使用其组件，他们仍须创建主互操作程序集 (PIA)。</span><span class="sxs-lookup"><span data-stu-id="86b2b-111">Developers of shared COM components still have to create primary interop assemblies (PIAs) if they want their components to be used by earlier versions of the .NET Framework.</span></span>

## <a name="type-equivalence"></a><span data-ttu-id="86b2b-112">类型等效性</span><span class="sxs-lookup"><span data-stu-id="86b2b-112">Type equivalence</span></span>

 <span data-ttu-id="86b2b-113">COM 类型的等效性支持接口、结构、枚举和委托。</span><span class="sxs-lookup"><span data-stu-id="86b2b-113">Equivalence of COM types is supported for interfaces, structures, enumerations, and delegates.</span></span> <span data-ttu-id="86b2b-114">如果满足以下所有条件，则 COM 类型符合等效条件：</span><span class="sxs-lookup"><span data-stu-id="86b2b-114">COM types qualify as equivalent if all of the following are true:</span></span>

- <span data-ttu-id="86b2b-115">类型是两个接口、两个结构、两个枚举或两个委托。</span><span class="sxs-lookup"><span data-stu-id="86b2b-115">The types are both interfaces, or both structures, or both enumerations, or both delegates.</span></span>

- <span data-ttu-id="86b2b-116">类型具有相同标识，如下节所述。</span><span class="sxs-lookup"><span data-stu-id="86b2b-116">The types have the same identity, as described in the next section.</span></span>

- <span data-ttu-id="86b2b-117">两种类型都符合类型等效性，如[针对类型等效性标记 COM 类型](#marking-com-types-for-type-equivalence)部分所述。</span><span class="sxs-lookup"><span data-stu-id="86b2b-117">Both types are eligible for type equivalence, as described in the [Marking COM types for type equivalence](#marking-com-types-for-type-equivalence) section.</span></span>

### <a name="type-identity"></a><span data-ttu-id="86b2b-118">类型标识</span><span class="sxs-lookup"><span data-stu-id="86b2b-118">Type identity</span></span>

<span data-ttu-id="86b2b-119">范围和标识匹配时，确定两种类型具有相同标识，换句话说，如果它们各自具有 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 属性，并且两个属性都具有匹配的 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> 和 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="86b2b-119">Two types are determined to have the same identity when their scopes and identities match, in other words, if they each have the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute, and the two attributes have matching <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> and <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> properties.</span></span> <span data-ttu-id="86b2b-120"><xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> 的比较不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="86b2b-120">The comparison for <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> is case-insensitive.</span></span>

<span data-ttu-id="86b2b-121">如果一个类型不具有 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 属性，或者如果它有一个不指定范围和标识符的 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 属性，仍可将该类型视为等效性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="86b2b-121">If a type does not have the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute, or if it has a <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute that does not specify scope and identifier, the type can still be considered for equivalence as follows:</span></span>

- <span data-ttu-id="86b2b-122">对于接口，使用 <xref:System.Runtime.InteropServices.GuidAttribute> 的值而不使用 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> 属性，使用 <xref:System.Type.FullName%2A?displayProperty=nameWithType> 属性（即类型名称，包括命名空间），而不使用 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> 属性。</span><span class="sxs-lookup"><span data-stu-id="86b2b-122">For interfaces, the value of the <xref:System.Runtime.InteropServices.GuidAttribute> is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=nameWithType> property, and the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property (that is, the type name, including the namespace) is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="86b2b-123">对于结构、枚举和委托，使用包含程序集的 <xref:System.Runtime.InteropServices.GuidAttribute> 而不使用 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> 属性，使用 <xref:System.Type.FullName%2A?displayProperty=nameWithType> 属性而不使用 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="86b2b-123">For structures, enumerations, and delegates, the <xref:System.Runtime.InteropServices.GuidAttribute> of the containing assembly is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> property, and the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property is used instead of the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> property.</span></span>

### <a name="marking-com-types-for-type-equivalence"></a><span data-ttu-id="86b2b-124">针对类型等效性标记 COM 类型</span><span class="sxs-lookup"><span data-stu-id="86b2b-124">Marking COM types for type equivalence</span></span>

 <span data-ttu-id="86b2b-125">可通过两种方式将类型标记为符合类型等效性：</span><span class="sxs-lookup"><span data-stu-id="86b2b-125">You can mark a type as eligible for type equivalence in two ways:</span></span>

- <span data-ttu-id="86b2b-126">将 <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> 属性应用于该类型。</span><span class="sxs-lookup"><span data-stu-id="86b2b-126">Apply the <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> attribute to the type.</span></span>

- <span data-ttu-id="86b2b-127">将该类型设为 COM 导入类型。</span><span class="sxs-lookup"><span data-stu-id="86b2b-127">Make the type a COM import type.</span></span> <span data-ttu-id="86b2b-128">若接口有 <xref:System.Runtime.InteropServices.ComImportAttribute> 属性，则它是 COM 导入类型。</span><span class="sxs-lookup"><span data-stu-id="86b2b-128">An interface is a COM import type if it has the <xref:System.Runtime.InteropServices.ComImportAttribute> attribute.</span></span> <span data-ttu-id="86b2b-129">如果定义了其程序集具有 <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> 属性，则接口、结构、枚举或委托是 COM 导入类型。</span><span class="sxs-lookup"><span data-stu-id="86b2b-129">An interface, structure, enumeration, or delegate is a COM import type if the assembly in which it is defined has the <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute> attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="86b2b-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="86b2b-130">See also</span></span>

- <xref:System.Type.IsEquivalentTo%2A>
- <span data-ttu-id="86b2b-131">[在托管代码中使用 COM 类型](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="86b2b-131">[Using COM Types in Managed Code](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="86b2b-132">将类型库作为程序集导入</span><span class="sxs-lookup"><span data-stu-id="86b2b-132">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
