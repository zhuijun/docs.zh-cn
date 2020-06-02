---
title: 特性
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: 12a67d75a5f9642408cca69b2e3764a67f101549
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280577"
---
# <a name="attributes"></a><span data-ttu-id="f66db-102">特性</span><span class="sxs-lookup"><span data-stu-id="f66db-102">Attributes</span></span>

<span data-ttu-id="f66db-103"><xref:System.Attribute?displayProperty=nameWithType>用于定义自定义属性的基类。</span><span class="sxs-lookup"><span data-stu-id="f66db-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>

 <span data-ttu-id="f66db-104">特性是可以添加到编程元素（如程序集、类型、成员和参数）的批注。</span><span class="sxs-lookup"><span data-stu-id="f66db-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="f66db-105">它们存储在程序集的元数据中，并且可在运行时使用反射 Api 进行访问。</span><span class="sxs-lookup"><span data-stu-id="f66db-105">They are stored in the metadata of the assembly and can be accessed at run time using the reflection APIs.</span></span> <span data-ttu-id="f66db-106">例如，.NET 定义 <xref:System.ObsoleteAttribute> 属性，该属性可应用于类型或成员，以指示类型或成员已弃用。</span><span class="sxs-lookup"><span data-stu-id="f66db-106">For example, .NET defines the <xref:System.ObsoleteAttribute> attribute, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>

 <span data-ttu-id="f66db-107">特性可以具有一个或多个属性，这些属性包含与特性相关的其他数据。</span><span class="sxs-lookup"><span data-stu-id="f66db-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="f66db-108">例如， `ObsoleteAttribute` 可能会携带有关已弃用类型或成员的发布的附加信息，以及替换已过时 api 的新 api 的说明。</span><span class="sxs-lookup"><span data-stu-id="f66db-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and a description of the new API that replaces the obsolete API.</span></span>

 <span data-ttu-id="f66db-109">应用特性时，必须指定特性的某些属性。</span><span class="sxs-lookup"><span data-stu-id="f66db-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="f66db-110">它们被称为必需的属性或必需的参数，因为它们表示为位置构造函数参数。</span><span class="sxs-lookup"><span data-stu-id="f66db-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="f66db-111">例如， <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> 的属性 <xref:System.Diagnostics.ConditionalAttribute> 是必需的属性。</span><span class="sxs-lookup"><span data-stu-id="f66db-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>

 <span data-ttu-id="f66db-112">应用特性时不一定要指定的属性称为可选属性（或可选参数）。</span><span class="sxs-lookup"><span data-stu-id="f66db-112">Properties that don't necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="f66db-113">它们由可设置的属性表示。</span><span class="sxs-lookup"><span data-stu-id="f66db-113">They are represented by settable properties.</span></span> <span data-ttu-id="f66db-114">应用特性时，编译器提供了用于设置这些属性的特殊语法。</span><span class="sxs-lookup"><span data-stu-id="f66db-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="f66db-115">例如， <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> 属性表示可选参数。</span><span class="sxs-lookup"><span data-stu-id="f66db-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>

 <span data-ttu-id="f66db-116">✔️命名具有后缀 "Attribute" 的自定义属性类。</span><span class="sxs-lookup"><span data-stu-id="f66db-116">✔️ DO name custom attribute classes with the suffix "Attribute."</span></span>

 <span data-ttu-id="f66db-117">✔️将应用 <xref:System.AttributeUsageAttribute> 到自定义属性。</span><span class="sxs-lookup"><span data-stu-id="f66db-117">✔️ DO apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>

 <span data-ttu-id="f66db-118">✔️提供可选参数的可设置属性。</span><span class="sxs-lookup"><span data-stu-id="f66db-118">✔️ DO provide settable properties for optional arguments.</span></span>

 <span data-ttu-id="f66db-119">✔️确实提供必需参数的只需属性。</span><span class="sxs-lookup"><span data-stu-id="f66db-119">✔️ DO provide get-only properties for required arguments.</span></span>

 <span data-ttu-id="f66db-120">✔️提供构造函数参数来初始化对应于所需参数的属性。</span><span class="sxs-lookup"><span data-stu-id="f66db-120">✔️ DO provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="f66db-121">每个参数都应具有与相应属性相同的名称（但大小写不同）。</span><span class="sxs-lookup"><span data-stu-id="f66db-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>

 <span data-ttu-id="f66db-122">❌避免提供构造函数参数来初始化对应于可选参数的属性。</span><span class="sxs-lookup"><span data-stu-id="f66db-122">❌ AVOID providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>

 <span data-ttu-id="f66db-123">换句话说，不能使用构造函数和 setter 来设置属性。</span><span class="sxs-lookup"><span data-stu-id="f66db-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="f66db-124">此准则非常明确，哪些参数是可选的，哪些是必需的，并且避免了两种方法来执行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="f66db-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>

 <span data-ttu-id="f66db-125">❌避免重载自定义特性构造函数。</span><span class="sxs-lookup"><span data-stu-id="f66db-125">❌ AVOID overloading custom attribute constructors.</span></span>

 <span data-ttu-id="f66db-126">只有一个构造函数清楚地向用户传达需要哪些参数，哪些参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="f66db-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>

 <span data-ttu-id="f66db-127">如果可能，✔️确实密封自定义特性类。</span><span class="sxs-lookup"><span data-stu-id="f66db-127">✔️ DO seal custom attribute classes, if possible.</span></span> <span data-ttu-id="f66db-128">这样可以更快地查找属性。</span><span class="sxs-lookup"><span data-stu-id="f66db-128">This makes the look-up for the attribute faster.</span></span>

 <span data-ttu-id="f66db-129">*部分 &copy; 2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="f66db-129">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="f66db-130">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="f66db-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="f66db-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f66db-131">See also</span></span>

- [<span data-ttu-id="f66db-132">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="f66db-132">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="f66db-133">使用准则</span><span class="sxs-lookup"><span data-stu-id="f66db-133">Usage Guidelines</span></span>](usage-guidelines.md)
