---
title: x:Key 指令
ms.date: 03/30/2017
f1_keywords:
- xKey
- Key
- x:Key
helpviewer_keywords:
- x:Key attribute [XAML Services]
- Key attribute in XAML [XAML Services]
- XAML [XAML Services], x:Key attribute
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
ms.openlocfilehash: 7e4e9cbded01297818f9f01df01e95e94d7dc4af
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548268"
---
# <a name="xkey-directive"></a>x:Key 指令
唯一标识在 XAML 定义的字典中创建和引用的元素。 `x:Key`在 XAML 对象元素中添加值是在资源字典中标识资源的最常见方法，例如在 WPF 中 <xref:System.Windows.ResourceDictionary> 。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性用法  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>XAML 特性用法 (特定于 WPF 的)   
  
```xaml  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`stringKeyValue`|要用作键的文本字符串。 文本字符串必须符合 [XamlName 语法](xamlname-grammar.md)。|  
|`markupExtensionUsage`|标记扩展分隔符中的 {} 标记扩展用法，提供要用作键的对象。 请参阅“备注”。|  
  
## <a name="remarks"></a>备注  
 `x:Key` 支持 XAML 资源字典概念。 作为语言的 XAML 不会定义资源字典实现，该实现留给特定的 UI 框架。 若要了解有关如何在 WPF 中实现 XAML 资源字典的详细信息，请参阅 [Xaml 资源](../fundamentals/xaml-resources-define.md)。  
  
 在 XAML 2006 和 WPF 中， `x:Key` 必须作为属性提供。 你仍可以使用非字符串键，但这需要使用标记扩展用法来提供属性窗体中的非字符串值。 如果你使用的是 XAML 2009，则 `x:Key` 可将指定为元素，以显式支持由对象类型（而非字符串）键控的字典，而不需要标记扩展中间。 请参阅本主题中的 "XAML 2009" 部分。 备注部分的剩余部分专门适用于 XAML 2006 实现。  
  
 的属性值 `x:Key` 可以是 [XamlName 语法](xamlname-grammar.md) 中定义的任何字符串，也可以是通过标记扩展进行计算的对象。 有关 WPF 的示例，请参阅 "WPF 使用说明"。  
  
 作为实现的父元素的子元素 <xref:System.Collections.IDictionary> 通常必须包括一个 `x:Key` 属性，该属性指定字典中的唯一键值。 框架可能实现用别名替换特定类型的键属性 `x:Key` ; 定义此类属性的类型应采用特性化 <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> 。  
  
 等效于指定的代码 `x:Key` 是用于基础的键 <xref:System.Collections.IDictionary> 。 例如， `x:Key` `key` <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> 当你在代码中将资源添加到 wpf 时，适用于 wpf 中某个资源的标记的将与的参数的值等效 <xref:System.Windows.ResourceDictionary> 。  
  
## <a name="wpf-usage-notes"></a>WPF 用法说明  
 <xref:System.Collections.IDictionary>作为实现（如 WPF）的父对象的子对象 <xref:System.Windows.ResourceDictionary> 通常必须包含 `x:Key` 特性，并且键值在该字典中必须是唯一的。 有两个值得注意的异常：  
  
- 一些 WPF 类型声明了字典使用的隐式键。 例如， <xref:System.Windows.Style> 具有 <xref:System.Windows.Style.TargetType%2A> 、或的 <xref:System.Windows.DataTemplate> <xref:System.Windows.DataTemplate.DataType%2A> 可以位于， <xref:System.Windows.ResourceDictionary> 并使用隐式键。  
  
- WPF 支持合并资源字典概念。 可以在合并字典之间共享密钥，并可以使用访问共享密钥行为 <xref:System.Windows.FrameworkContentElement.FindResource%2A> 。 有关详细信息，请参阅 [合并资源字典](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries)。  
  
 在整个 WPF XAML 实现和应用程序模型中，XAML 标记编译器不会检查密钥的唯一性。 相反，缺少值或非唯一 `x:Key` 值会导致加载时 XAML 分析器错误。 但是，Visual Studio for WPF 字典处理通常会在设计阶段记录此类错误。  
  
 请注意，在显示的语法中， <xref:System.Windows.ResourceDictionary> 对象是隐式的，因为 WPF XAML 处理器如何生成用于填充 <xref:System.Windows.FrameworkElement.Resources%2A> 集合的集合。 <xref:System.Windows.ResourceDictionary>通常不会在标记中显式提供为元素，但在某些情况下，如果需要清楚起见，它可能是在属性元素和内的项之间 (集合对象元素， <xref:System.Windows.FrameworkElement.Resources%2A> 该元素) 填充字典。 有关集合对象在标记中几乎始终为隐式元素的原因的信息，请参阅 [XAML 语法（详细](/dotnet/desktop/wpf/advanced/xaml-syntax-in-detail)）。  
  
 在 WPF XAML 实现中，资源字典键的处理由 <xref:System.Windows.ResourceKey> 抽象类定义。 不过，WPF XAML 处理器基于它们的用法为密钥生成不同的基础扩展类型。 例如， <xref:System.Windows.DataTemplate> 或任何派生类的键单独处理，并生成一个不同的 <xref:System.Windows.DataTemplateKey> 对象。  
  
 键和名称 `x:Key` `x:Name` 在基本 XAML 定义 (与) 使用不同的指令和语言元素。 键和名称还可用于 WPF 定义和应用这些概念的不同情况。 有关详细信息，请参阅 [WPF XAML 名称范围](/dotnet/desktop/wpf/advanced/wpf-xaml-namescopes)。  
  
 如前所述，密钥的值可以通过标记扩展提供，也可以是字符串值以外的值。 WPF 方案的一个示例是，的值 `x:Key` 可以是 [ComponentResourceKey](/dotnet/desktop/wpf/advanced/componentresourcekey-markup-extension)。 某些控件为自定义样式资源公开该类型的样式键，该资源会影响该控件的外观和行为的一部分，而不会完全替换样式。 此类键的一个示例是 <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A> 。  
  
 WPF 合并字典功能引入了有关密钥唯一性和键查找行为的其他注意事项。 有关详细信息，请参阅 [合并资源字典](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries)。  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 放宽 `x:Key` 属性形式始终提供的限制。  
  
 在 WPF 中，可以使用 XAML 2009 功能，但仅针对未进行标记编译的 XAML。 WPF 的已编译标记的 XAML 以及 XAML 的 BAML 形式当前不支持 XAML 2009 关键字和功能。  
  
 在 XAML 2009 下，可以 `x:Key` 通过以下用法指定元素：  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>XAML 元素用法 (仅限 XAML 2009)   
  
```xaml  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`keyObject`|对象的对象元素，该对象用作专用字典中给定的的键 `object` 。|  
  
- 此类用途的容器/父项未在此处显示。 `object` 应为表示专用字典实现的对象元素的子元素。 `keyObject` 应为对象实例 (或值类型的值) ，此值适合作为特定专用字典实现的键。  
  
- WPF 不实现需要此用法的字典。 对象键是 XAML 语言的常规功能，对于在 XAML 中创建字典的某些自定义字典方案可能很有用。 对于使用资源的非字符串密钥的隐式样式等 WPF 功能，存在用于建立或指定密钥的其他方法，因此不需要使用对象密钥。  
  
- `keyObject` 也可以是对象元素窗体中的标记扩展用法，而不是直接对象实例。  
  
## <a name="silverlight-usage-notes"></a>Silverlight 使用说明  
 `x:Key` 对于 Silverlight，单独记录。 有关详细信息，请参阅 [XAML 命名空间 (x： ) 语言功能 (Silverlight) ](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95))。  
  
## <a name="see-also"></a>请参阅

- [XAML 资源](../fundamentals/xaml-resources-define.md)
- [资源和代码](/dotnet/desktop/wpf/advanced/resources-and-code)
- [StaticResource 标记扩展](/dotnet/desktop/wpf/advanced/staticresource-markup-extension)
