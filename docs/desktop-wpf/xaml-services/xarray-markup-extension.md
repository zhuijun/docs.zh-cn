---
title: x:Array 标记扩展
ms.date: 03/30/2017
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
ms.openlocfilehash: b812939cbaa74576361de534c0d39ba45536cbcf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555167"
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="6e023-102">x:Array 标记扩展</span><span class="sxs-lookup"><span data-stu-id="6e023-102">x:Array Markup Extension</span></span>

<span data-ttu-id="6e023-103">通过标记扩展为 XAML 中的对象数组提供常规支持。</span><span class="sxs-lookup"><span data-stu-id="6e023-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="6e023-104">这对应于 `x:ArrayExtension` [ms-chap] 中的 XAML 类型。</span><span class="sxs-lookup"><span data-stu-id="6e023-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="6e023-105">XAML 对象元素用法</span><span class="sxs-lookup"><span data-stu-id="6e023-105">XAML Object Element Usage</span></span>

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a><span data-ttu-id="6e023-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="6e023-106">XAML Values</span></span>

|||
|-|-|
|`typeName`|<span data-ttu-id="6e023-107">你将包含的类型的名称 `x:Array` 。</span><span class="sxs-lookup"><span data-stu-id="6e023-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="6e023-108">`typeName` 可以 (，并且通常) 包含 XAML 类型定义的 XAML 命名空间的前缀。</span><span class="sxs-lookup"><span data-stu-id="6e023-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|
|`arrayContents`|<span data-ttu-id="6e023-109">分配给内部属性的项内容 `ArrayExtension.Items` 。</span><span class="sxs-lookup"><span data-stu-id="6e023-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="6e023-110">通常，这些项被指定为一个或多个包含在 `x:Array` 开始和结束标记中的对象元素。</span><span class="sxs-lookup"><span data-stu-id="6e023-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="6e023-111">此处指定的对象应可分配给在中指定的 XAML 类型 `typeName` 。</span><span class="sxs-lookup"><span data-stu-id="6e023-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6e023-112">备注</span><span class="sxs-lookup"><span data-stu-id="6e023-112">Remarks</span></span>

<span data-ttu-id="6e023-113">`Type` 是所有对象元素的必需属性 `x:Array` 。</span><span class="sxs-lookup"><span data-stu-id="6e023-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="6e023-114">`Type`参数值无需使用 `x:Type` 标记扩展; 类型的短名称为 XAML 类型，可以将其指定为字符串。</span><span class="sxs-lookup"><span data-stu-id="6e023-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>

<span data-ttu-id="6e023-115">在 .NET XAML 服务实现中，所创建数组的输入 XAML 类型和输出 CLR 之间的关系受 <xref:System.Type> 标记扩展的服务上下文影响。</span><span class="sxs-lookup"><span data-stu-id="6e023-115">In .NET XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="6e023-116">输出 <xref:System.Type> 是 <xref:System.Xaml.XamlType.UnderlyingType%2A> 输入 xaml 类型的，在 <xref:System.Xaml.XamlType> 根据 XAML 架构上下文和上下文提供的服务查找必要后 <xref:System.Windows.Markup.IXamlTypeResolver> 。</span><span class="sxs-lookup"><span data-stu-id="6e023-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>

<span data-ttu-id="6e023-117">处理后，数组内容将分配给 `ArrayExtension.Items` 内部属性。</span><span class="sxs-lookup"><span data-stu-id="6e023-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="6e023-118">在 <xref:System.Windows.Markup.ArrayExtension> 实现中，这由表示 <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="6e023-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="6e023-119">在 .NET XAML 服务实现中，对此标记扩展的处理由类定义 <xref:System.Windows.Markup.ArrayExtension> 。</span><span class="sxs-lookup"><span data-stu-id="6e023-119">In .NET XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="6e023-120"><xref:System.Windows.Markup.ArrayExtension> 不是密封的，并且可用作自定义数组类型的标记扩展实现的基础。</span><span class="sxs-lookup"><span data-stu-id="6e023-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>

<span data-ttu-id="6e023-121">`x:Array` 更适用于 XAML 中的常规语言扩展性。</span><span class="sxs-lookup"><span data-stu-id="6e023-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="6e023-122">但 `x:Array` 也可用于指定某些属性的 xaml 值，这些属性采用支持 XAML 的集合作为其结构化属性内容。</span><span class="sxs-lookup"><span data-stu-id="6e023-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="6e023-123">例如，可以指定具有用法的属性的内容 <xref:System.Collections.IEnumerable> `x:Array` 。</span><span class="sxs-lookup"><span data-stu-id="6e023-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>

<span data-ttu-id="6e023-124">`x:Array` 是标记扩展。</span><span class="sxs-lookup"><span data-stu-id="6e023-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="6e023-125">当要求转义特性值应为非文本值或非处理程序名称时，通常会实现标记扩展，相对于只在某些类型或属性上放置类型转换器而言，此需求更具有全局性。</span><span class="sxs-lookup"><span data-stu-id="6e023-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="6e023-126">`x:Array` 部分是该规则的例外情况，因为它不提供备用属性值处理，而是 `x:Array` 提供其内部文本内容的替代处理。</span><span class="sxs-lookup"><span data-stu-id="6e023-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="6e023-127">此行为使现有内容模型可能不支持的类型可以分组到数组中，稍后通过访问命名数组在代码隐藏中进行引用;可以调用 <xref:System.Array> 方法来获取单个数组项。</span><span class="sxs-lookup"><span data-stu-id="6e023-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>

<span data-ttu-id="6e023-128">XAML 中的所有标记扩展在其特性语法中使用大括号 ({,} `)` ，这是 xaml 处理器识别标记扩展必须处理特性值的约定。</span><span class="sxs-lookup"><span data-stu-id="6e023-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="6e023-129">有关常规标记扩展的详细信息，请参阅 [XAML 的类型转换器和标记扩展](type-converters-and-markup-extensions.md)。</span><span class="sxs-lookup"><span data-stu-id="6e023-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions.md).</span></span>

<span data-ttu-id="6e023-130">在 XAML 2009 中， `x:Array` 定义为语言基元，而不是标记扩展。</span><span class="sxs-lookup"><span data-stu-id="6e023-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="6e023-131">有关详细信息，请参阅 [常见 XAML 语言基元的内置类型](types-for-primitives.md)。</span><span class="sxs-lookup"><span data-stu-id="6e023-131">For more information, see [Built-in Types for Common XAML Language Primitives](types-for-primitives.md).</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="6e023-132">WPF 用法说明</span><span class="sxs-lookup"><span data-stu-id="6e023-132">WPF Usage Notes</span></span>

<span data-ttu-id="6e023-133">通常，填充的对象元素 `x:Array` 不是 XAML 命名空间中存在的元素 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ，需要映射到非默认的 xaml 命名空间。</span><span class="sxs-lookup"><span data-stu-id="6e023-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>

<span data-ttu-id="6e023-134">例如，下面是一个包含两个字符串的简单数组，其中 `sys` 前缀 (，还 `x` 在数组级别定义) 。</span><span class="sxs-lookup"><span data-stu-id="6e023-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

<span data-ttu-id="6e023-135">对于用作数组元素的自定义类型，该类还必须支持在 XAML 中实例化为对象元素的要求。</span><span class="sxs-lookup"><span data-stu-id="6e023-135">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="6e023-136">有关详细信息，请参阅 [WPF 的 XAML 和自定义类](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)。</span><span class="sxs-lookup"><span data-stu-id="6e023-136">For more information, see [XAML and Custom Classes for WPF](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf).</span></span>

## <a name="see-also"></a><span data-ttu-id="6e023-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="6e023-137">See also</span></span>

- [<span data-ttu-id="6e023-138">标记扩展和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="6e023-138">Markup Extensions and WPF XAML</span></span>](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
- [<span data-ttu-id="6e023-139">从 WPF 迁移到 System.Xaml 的类型</span><span class="sxs-lookup"><span data-stu-id="6e023-139">Types Migrated from WPF to System.Xaml</span></span>](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
