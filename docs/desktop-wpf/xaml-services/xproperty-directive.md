---
title: x:Property 指令
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: d4294b39ff262198f8082863d23eb6f4edbc7054
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549296"
---
# <a name="xproperty-directive"></a><span data-ttu-id="93d61-102">x:Property 指令</span><span class="sxs-lookup"><span data-stu-id="93d61-102">x:Property Directive</span></span>

<span data-ttu-id="93d61-103">声明标记中的 XAML 属性。</span><span class="sxs-lookup"><span data-stu-id="93d61-103">Declares a XAML property in markup.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="93d61-104">XAML 对象元素用法</span><span class="sxs-lookup"><span data-stu-id="93d61-104">XAML Object Element Usage</span></span>

```xaml
<object x:Class="className">
  <x:Members>
    <x:Property Name="propertyName" Type="propertyType"/>
    additionalProperties
  </x:Members>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="93d61-105">XAML 值</span><span class="sxs-lookup"><span data-stu-id="93d61-105">XAML Values</span></span>

|||
|-|-|
|`className`|<span data-ttu-id="93d61-106">XAML 生产的备用类或分部类的名称。</span><span class="sxs-lookup"><span data-stu-id="93d61-106">Name of the backing class or partial class for the XAML production.</span></span>|
|`propertyName`|<span data-ttu-id="93d61-107">正在定义的属性的成员名称。</span><span class="sxs-lookup"><span data-stu-id="93d61-107">Member name of the property being defined.</span></span>|
|`propertyType`|<span data-ttu-id="93d61-108">指定此属性类型的类型名称（或特定于框架的字符串形式）。</span><span class="sxs-lookup"><span data-stu-id="93d61-108">Type name (or other string form, framework-specific) that specifies the type of this property.</span></span>|

## <a name="remarks"></a><span data-ttu-id="93d61-109">备注</span><span class="sxs-lookup"><span data-stu-id="93d61-109">Remarks</span></span>

<span data-ttu-id="93d61-110">.NET XAML 服务实现中的。</span><span class="sxs-lookup"><span data-stu-id="93d61-110">In .NET XAML Services implementation, .</span></span> <span data-ttu-id="93d61-111">`x:Property` 没有直接的类型支持，但受 <xref:System.Windows.Markup.PropertyDefinition> 类支持。</span><span class="sxs-lookup"><span data-stu-id="93d61-111">`x:Property` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.PropertyDefinition> class.</span></span> <span data-ttu-id="93d61-112">在 XAML 节点流中，`x:Property` 元素表示为 XAML 语言 XAML 命名空间中名为 `Property` 的成员。</span><span class="sxs-lookup"><span data-stu-id="93d61-112">In a XAML node stream, an `x:Property` element is represented as a member named `Property`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="93d61-113">成员 `Property` 拥有标记声明的属性。</span><span class="sxs-lookup"><span data-stu-id="93d61-113">The member `Property` hold attributes as declared by markup.</span></span>

<span data-ttu-id="93d61-114">和的含义 `Name` 在 `Type` .Net XAML 服务级别未赋值。</span><span class="sxs-lookup"><span data-stu-id="93d61-114">The meaning of `Name` and `Type` are not assigned at .NET XAML Services level.</span></span> <span data-ttu-id="93d61-115">它们作为字符串值存储在初始的 XAML 节点流中，将在之后根据可能由特定框架强加的规则进行解释。</span><span class="sxs-lookup"><span data-stu-id="93d61-115">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="93d61-116">该含义可能与 XAML 名称和 XAML 类型含义一致，或者可能仅在备用类型系统中有效，这取决于实现。</span><span class="sxs-lookup"><span data-stu-id="93d61-116">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>

<span data-ttu-id="93d61-117">若要支持将 `x:Members` 实际用作一种在标记中指定成员定义的方法，成员必须与可修改的类相关联。</span><span class="sxs-lookup"><span data-stu-id="93d61-117">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="93d61-118">预期模型是 `x:Members` 作为指定 `x:Class` 的类型的成员存在。</span><span class="sxs-lookup"><span data-stu-id="93d61-118">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="93d61-119">但是，在 .NET XAML 服务级别不支持关联类型和成员或用于生成动态成员定义的机制。</span><span class="sxs-lookup"><span data-stu-id="93d61-119">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at .NET XAML Services level.</span></span> <span data-ttu-id="93d61-120">此功能由具有支持 XAML 的成员定义的应用程序模型的单个框架实现。</span><span class="sxs-lookup"><span data-stu-id="93d61-120">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="93d61-121">通常，需要 MSBUILD 生成操来支持此功能，这些操作以标记编译 XAML 并将其与隐藏代码相集成或者从 XMAL 生成纯程序集。</span><span class="sxs-lookup"><span data-stu-id="93d61-121">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>

## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="93d61-122">适用于 Windows Workflow Foundation 的 x:Property</span><span class="sxs-lookup"><span data-stu-id="93d61-122">x:Property for Windows Workflow Foundation</span></span>

<span data-ttu-id="93d61-123">对于 Windows Workflow Foundation，`x:Property` 定义完全在 XAML 中构成的自定义活动的成员，或具有隐藏代码的活动设计器的 XMAL 定义的动态成员。</span><span class="sxs-lookup"><span data-stu-id="93d61-123">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="93d61-124">此外，必须在 XAML 生产的根元素上指定 `x:Class`。</span><span class="sxs-lookup"><span data-stu-id="93d61-124">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="93d61-125">这不是 .NET XAML 服务级别的要求，但当 XAML 生产由支持自定义活动和 Windows Workflow Foundation XAML 的 MSBUILD 生成操作加载时，就会成为一项要求。</span><span class="sxs-lookup"><span data-stu-id="93d61-125">This is not a requirement at .NET XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="93d61-126">Windows Workflow Foundation 不使用纯 XAML 类型名称作为该属性的预期值 `x:Property` `Type` ，而是使用此处未介绍的约定。</span><span class="sxs-lookup"><span data-stu-id="93d61-126">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="93d61-127">有关详细信息，请参阅 [DynamicActivity 创建](/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="93d61-127">For more information, see [DynamicActivity Creation](/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span></span>
