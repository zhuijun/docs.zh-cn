---
title: XAML 中 xml:lang 的处理
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 92d1eda62ff394df54d9607bab46d9950681e603
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548203"
---
# <a name="xmllang-handling-in-xaml"></a>XAML 中 xml:lang 的处理

`xml:lang`特性是一个 xml 定义的特性，用于声明 xml 中某个元素的语言和区域性信息。 此属性的相同含义在 XAML 中持续存在；但有一些其他注意事项。

## <a name="xaml-attribute-usage"></a>XAML 属性用法

```xaml
<object xml:lang="rfc3066lang" />
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|*rfc3066lang*|派生自 [RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) 标准的字符串，并标识一种语言或语言-地区。 当为后者时，将由一个连字符分隔语言和区域。 请参阅 <xref:System.Windows.Markup.XmlLanguage> ，以了解有关值和格式的更多信息。|

## <a name="remarks"></a>备注

中属性的定义 `xml:lang` [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 派生自 `xml:lang` 万维网联合会 (W3C) for XML 中定义为 "特殊特性"。 语言和区域性信息可能由元素根据其实现以不同方式进行处理；但是， [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 属性没有默认的 `xml:lang` 处理方式。

`xml:lang` 属性的默认值是属性级空字符串。

当由作用于 `xml:lang` 值的系统进行解释时， `xml:lang` 属性效果和属性值通常永久保留到子元素中。

当由 .NET XAML 服务的 XAML 编写器进行解释时， `xml:lang` 值 <xref:System.Windows.Markup.XmlLanguage> 可以 <xref:System.Globalization.CultureInfo> 在基础对象表示形式中创建或对象; 但是，该行为取决于为指定的值是否为 `xml:lang` 这些类的有效构造。

通过将 `xml:lang` 应用到属性，框架可以在 XML 中创建框架定义属性和 <xref:System.Windows.Markup.XmlLangPropertyAttribute> 含义之间的关联。

## <a name="wpf-usage-nodes"></a>WPF 使用情况节点

对于身为 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement>派生类的元素，可以使用等效 <xref:System.Windows.FrameworkElement.Language%2A> 依赖项属性取代 `xml:lang` 属性。 默认情况下，如果未通过属性或通过处理 <xref:System.Windows.FrameworkElement.Language%2A> 属性来另外设置 `xml:lang` 属性，则它使用“en-US”。

## <a name="see-also"></a>请参阅

- [WPF 的全球化](/dotnet/desktop/wpf/advanced/globalization-for-wpf)
