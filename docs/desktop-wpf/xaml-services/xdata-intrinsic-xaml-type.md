---
title: x:XData 内部 XAML 类型
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: d78c2fd63192dc499b119e5b038b92555511a695
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544799"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="8dd79-102">x:XData 内部 XAML 类型</span><span class="sxs-lookup"><span data-stu-id="8dd79-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="8dd79-103">启用 XML 数据岛在 XAML 生产中的放置。</span><span class="sxs-lookup"><span data-stu-id="8dd79-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="8dd79-104">`x:XData`XAML 处理器不应处理中的 XML 元素，就好像它们是正在操作的默认 xaml 命名空间或任何其他 XAML 命名空间的一部分。</span><span class="sxs-lookup"><span data-stu-id="8dd79-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="8dd79-105">`x:XData` 可以包含任意格式正确的 XML。</span><span class="sxs-lookup"><span data-stu-id="8dd79-105">`x:XData` can contain arbitrary well-formed XML.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="8dd79-106">XAML 对象元素用法</span><span class="sxs-lookup"><span data-stu-id="8dd79-106">XAML Object Element Usage</span></span>

```xaml
<x:XData>
  <elementDataRoot>
    [elementData]
  </elementDataRoot>
</x:XData>
```

## <a name="xaml-values"></a><span data-ttu-id="8dd79-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="8dd79-107">XAML Values</span></span>

|||
|-|-|
|`elementDataRoot`|<span data-ttu-id="8dd79-108">括起来的数据岛的单个根元素。</span><span class="sxs-lookup"><span data-stu-id="8dd79-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="8dd79-109">对于最终使用者而言，没有单个根的 XML 被视为无效。</span><span class="sxs-lookup"><span data-stu-id="8dd79-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="8dd79-110">特别是，如果要 `x:XData` 用作 WPF 的 xml 数据源，或使用 xml 源进行数据绑定的许多其他技术，则需要单个根。</span><span class="sxs-lookup"><span data-stu-id="8dd79-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|
|`[elementData]`|<span data-ttu-id="8dd79-111">可选。</span><span class="sxs-lookup"><span data-stu-id="8dd79-111">Optional.</span></span> <span data-ttu-id="8dd79-112">表示 XML 数据的 XML。</span><span class="sxs-lookup"><span data-stu-id="8dd79-112">XML that represents the XML data.</span></span> <span data-ttu-id="8dd79-113">可以将任意数量的元素包含为元素数据，嵌套元素可以包含在其他元素中;但是，XML 的一般规则是适用的。</span><span class="sxs-lookup"><span data-stu-id="8dd79-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8dd79-114">备注</span><span class="sxs-lookup"><span data-stu-id="8dd79-114">Remarks</span></span>

<span data-ttu-id="8dd79-115">对象中的 XML 元素 `x:XData` 可以在数据中重新声明包含 XMLDOM 的所有可能的命名空间和前缀。</span><span class="sxs-lookup"><span data-stu-id="8dd79-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>

<span data-ttu-id="8dd79-116">可以通过类以编程方式访问 XML 数据和 `x:XData` 内部 xaml 类型 <xref:System.Windows.Markup.XData> 。</span><span class="sxs-lookup"><span data-stu-id="8dd79-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="8dd79-117">WPF 用法说明</span><span class="sxs-lookup"><span data-stu-id="8dd79-117">WPF Usage Notes</span></span>

<span data-ttu-id="8dd79-118">`x:XData`对象主要用作的子对象 <xref:System.Windows.Data.XmlDataProvider> ，或者作为 <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> (在 XAML 中的属性的子对象，这通常用属性元素语法) 来表示。</span><span class="sxs-lookup"><span data-stu-id="8dd79-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>

<span data-ttu-id="8dd79-119">通常，数据会将数据岛中的基本 XML 命名空间重新定义为新的默认 XML 命名空间 (设置为空字符串) 。</span><span class="sxs-lookup"><span data-stu-id="8dd79-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="8dd79-120">对于简单的数据岛，这是最简单的，因为 <xref:System.Windows.Data.Binding.XPath%2A> 用于引用和绑定到数据的表达式可避免包含前缀。</span><span class="sxs-lookup"><span data-stu-id="8dd79-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="8dd79-121">更复杂的数据岛可能会为数据定义多个前缀，并在根处为 XML 命名空间使用特定的前缀。</span><span class="sxs-lookup"><span data-stu-id="8dd79-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="8dd79-122">在这种情况下，所有 <xref:System.Windows.Data.Binding.XPath%2A> 表达式引用应包括相应的命名空间映射前缀。</span><span class="sxs-lookup"><span data-stu-id="8dd79-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="8dd79-123">有关详细信息，请参阅 [数据绑定概述](../data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="8dd79-123">For more information, see [Data Binding Overview](../data/data-binding-overview.md).</span></span>

<span data-ttu-id="8dd79-124">从技术上讲， `x:XData` 可以用作类型的任何属性的内容 <xref:System.Xml.Serialization.IXmlSerializable> 。</span><span class="sxs-lookup"><span data-stu-id="8dd79-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="8dd79-125">不过， <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> 是唯一的主要实现。</span><span class="sxs-lookup"><span data-stu-id="8dd79-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="8dd79-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="8dd79-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="8dd79-127">数据绑定概述</span><span class="sxs-lookup"><span data-stu-id="8dd79-127">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="8dd79-128">绑定标记扩展</span><span class="sxs-lookup"><span data-stu-id="8dd79-128">Binding Markup Extension</span></span>](/dotnet/desktop/wpf/advanced/binding-markup-extension)
