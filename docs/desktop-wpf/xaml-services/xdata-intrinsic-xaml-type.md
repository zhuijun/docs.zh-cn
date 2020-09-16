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
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData 内部 XAML 类型
启用 XML 数据岛在 XAML 生产中的放置。 `x:XData`XAML 处理器不应处理中的 XML 元素，就好像它们是正在操作的默认 xaml 命名空间或任何其他 XAML 命名空间的一部分。 `x:XData` 可以包含任意格式正确的 XML。

## <a name="xaml-object-element-usage"></a>XAML 对象元素用法

```xaml
<x:XData>
  <elementDataRoot>
    [elementData]
  </elementDataRoot>
</x:XData>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`elementDataRoot`|括起来的数据岛的单个根元素。 对于最终使用者而言，没有单个根的 XML 被视为无效。 特别是，如果要 `x:XData` 用作 WPF 的 xml 数据源，或使用 xml 源进行数据绑定的许多其他技术，则需要单个根。|
|`[elementData]`|可选。 表示 XML 数据的 XML。 可以将任意数量的元素包含为元素数据，嵌套元素可以包含在其他元素中;但是，XML 的一般规则是适用的。|

## <a name="remarks"></a>备注

对象中的 XML 元素 `x:XData` 可以在数据中重新声明包含 XMLDOM 的所有可能的命名空间和前缀。

可以通过类以编程方式访问 XML 数据和 `x:XData` 内部 xaml 类型 <xref:System.Windows.Markup.XData> 。

## <a name="wpf-usage-notes"></a>WPF 用法说明

`x:XData`对象主要用作的子对象 <xref:System.Windows.Data.XmlDataProvider> ，或者作为 <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> (在 XAML 中的属性的子对象，这通常用属性元素语法) 来表示。

通常，数据会将数据岛中的基本 XML 命名空间重新定义为新的默认 XML 命名空间 (设置为空字符串) 。 对于简单的数据岛，这是最简单的，因为 <xref:System.Windows.Data.Binding.XPath%2A> 用于引用和绑定到数据的表达式可避免包含前缀。 更复杂的数据岛可能会为数据定义多个前缀，并在根处为 XML 命名空间使用特定的前缀。 在这种情况下，所有 <xref:System.Windows.Data.Binding.XPath%2A> 表达式引用应包括相应的命名空间映射前缀。 有关详细信息，请参阅 [数据绑定概述](../data/data-binding-overview.md)。

从技术上讲， `x:XData` 可以用作类型的任何属性的内容 <xref:System.Xml.Serialization.IXmlSerializable> 。 不过， <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> 是唯一的主要实现。

## <a name="see-also"></a>请参阅

- <xref:System.Windows.Data.XmlDataProvider>
- [数据绑定概述](../data/data-binding-overview.md)
- [绑定标记扩展](/dotnet/desktop/wpf/advanced/binding-markup-extension)
