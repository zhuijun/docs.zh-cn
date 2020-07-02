---
title: 绑定声明概述
description: 了解如何在 XAML 中声明用于应用程序开发 Windows Presentation Foundation （WPF）中的绑定。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- markup extensions [WPF]
- data binding [WPF], declarations
- object element syntax [WPF]
- binding data [WPF], declarations
- syntax [WPF], object elements
- binding declarations [WPF]
ms.assetid: b97fd626-4c0d-4761-872a-2bca5820da2c
ms.openlocfilehash: 8d4943de0cacb5fe0b5a0c37a5a68f15243ad528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619632"
---
# <a name="binding-declarations-overview"></a>绑定声明概述

本主题讨论声明绑定的不同方法。

<a name="Prereq"></a>

## <a name="prerequisites"></a>先决条件

在阅读本主题之前，请务必熟悉标记扩展的概念和使用。 有关标记扩展的详细信息，请参阅[标记扩展和 WPF XAML](../advanced/markup-extensions-and-wpf-xaml.md)。

本主题未涉及数据绑定概念。 有关数据绑定概念的讨论，请参阅[数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)。

<a name="BindinginXAML"></a>

## <a name="declaring-a-binding-in-xaml"></a>在 XAML 中声明绑定

本部分介绍如何在 XAML 中声明绑定。

<a name="MarkupExtensionSyntax"></a>

### <a name="markup-extension-usage"></a>标记扩展使用

<xref:System.Windows.Data.Binding> 是标记扩展。 使用绑定扩展声明绑定时，声明包含一系列子句，这些子句跟在 `Binding` 关键字后面，并由逗号 (,) 分隔。 绑定声明中的子句可以按任意顺序排列，有多种可能的组合。 子句*是名称* = *值*对，其中*name*是属性的名称 <xref:System.Windows.Data.Binding> ，*值*是要为属性设置的值。

在标记中创建绑定声明字符串时，必须将这些字符串附加到目标对象的特定依赖属性。 下面的示例演示如何 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> 使用绑定扩展绑定属性，指定 <xref:System.Windows.Data.Binding.Source%2A> 和 <xref:System.Windows.Data.Binding.Path%2A> 属性。

[!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]

可以通过 <xref:System.Windows.Data.Binding> 这种方式指定类的大多数属性。 有关绑定扩展以及 <xref:System.Windows.Data.Binding> 无法使用绑定扩展进行设置的属性列表的详细信息，请参阅[绑定标记扩展](../advanced/binding-markup-extension.md)概述。

<a name="ObjectElementSyntax"></a>

### <a name="object-element-syntax"></a>对象元素语法

对象元素语法是创建绑定声明的替代方法。 在大多数情况下，使用标记扩展或对象元素语法没有特定的优势。 不过，如果标记扩展不支持你的方案，例如，当属性值是不存在任何类型转换的非字符串类型时，需要使用对象元素语法。

下面是对象元素语法和标记扩展使用的示例：

[!code-xaml[BindConversionMarkup#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]

该示例 <xref:System.Windows.Controls.TextBlock.Foreground%2A> 通过使用扩展语法声明绑定来绑定属性。 属性的绑定声明 <xref:System.Windows.Controls.TextBlock.Text%2A> 使用对象元素语法。

有关其他术语的详细信息，请参阅 [XAML 语法详述](../advanced/xaml-syntax-in-detail.md)。

<a name="MBandPB"></a>

### <a name="multibinding-and-prioritybinding"></a>MultiBinding 和 PriorityBinding

<xref:System.Windows.Data.MultiBinding>和 <xref:System.Windows.Data.PriorityBinding> 不支持 XAML 扩展语法。 因此，如果在 XAML 中声明或，则必须使用对象元素语法 <xref:System.Windows.Data.MultiBinding> <xref:System.Windows.Data.PriorityBinding> 。

<a name="BindinginCode"></a>

## <a name="creating-a-binding-in-code"></a>在代码中创建绑定

指定绑定的另一种方法是直接在代码中的对象上设置属性 <xref:System.Windows.Data.Binding> 。 下面的示例演示如何创建 <xref:System.Windows.Data.Binding> 对象并在代码中指定属性。  在此示例中， `TheConverter` 是一个实现接口的对象 <xref:System.Windows.Data.IValueConverter> 。

[!code-csharp[BindConversion#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
[!code-vb[BindConversion#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]

如果要绑定的对象是或， <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> 则可以直接对对象调用 `SetBinding` 方法，而不是使用 <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> 。 有关示例，请参阅[在代码中创建绑定](how-to-create-a-binding-in-code.md)。

<a name="Path_Syntax"></a>

## <a name="binding-path-syntax"></a>绑定路径语法

使用 <xref:System.Windows.Data.Binding.Path%2A> 属性指定要绑定到的源值：

- 在最简单的情况下， <xref:System.Windows.Data.Binding.Path%2A> 属性值是要用于绑定的源对象的属性的名称，例如 `Path=PropertyName` 。

- 可以通过类似于 c # 中的类似语法来指定属性的子属性。 例如，子句 `Path=ShoppingCart.Order` 设置与对象或属性 `ShoppingCart` 的子属性 `Order` 的绑定。

- 若要绑定到附加属性，请将附加属性置于括号中。 例如，若要绑定到附加属性 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ，语法为 `Path=(DockPanel.Dock)` 。

- 可以在已应用索引器的属性名后面的方括号内指定属性的索引器。 例如，子句 `Path=ShoppingCart[0]` 将绑定设置为与属性的内部索引处理文本字符串“0”的方式对应的索引。 还支持嵌套索引器。

- 可以在 `Path` 子句中混用索引器和子属性，例如 `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`

- 可以在索引器内使用多个由逗号 (,) 分隔的索引器参数。 可以使用括号指定每个参数的类型。 例如，可以使用 `Path="[(sys:Int32)42,(sys:Int32)24]"`，其中 `sys` 将映射到 `System` 命名空间。

- 如果源是集合视图，则可以使用斜杠 (/) 指定当前项。 例如，子句 `Path=/` 设置与视图中当前项的绑定。 如果源是集合，则此语法指定默认集合视图的当前项。

- 可以组合使用属性名和斜杠，以遍历作为集合的属性。 例如，`Path=/Offices/ManagerName` 指定源集合的当前项，源集合中包含的 `Offices` 属性也是一个集合。 它的当前项是一个包含 `ManagerName` 属性的对象。

- 句点 (.) 路径也可以用于绑定到当前源。 例如，`Text="{Binding}"` 与 `Text="{Binding Path=.}"` 等效。

### <a name="escaping-mechanism"></a>转义机制

- 在索引器 ([ ]) 内部，脱字符号 (^) 用于对下一个字符进行转义。

- 如果 <xref:System.Windows.Data.Binding.Path%2A> 在 XAML 中设置，还需要对 xml 语言定义的特殊字符进行转义（使用 xml 实体）：

  - 使用 `&amp;` 对字符“&”进行转义。

  - 使用 `&gt;` 对结束标记“>”进行转义。

- 此外，如果在属性中使用标记扩展语法描述整个绑定，需要（使用反斜杠 \\）对 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 标记扩展分析器专用的字符进行转义：

  - 反斜杠 (\\) 本身是转义字符。

  - 等号 (=) 将属性名与属性值分隔开。

  - 逗号 (,) 用于分隔属性。

  - 右大括号 (}) 是标记扩展的结尾。

<a name="Default"></a>

## <a name="default-behaviors"></a>默认行为

如果未在声明中指定默认行为，则默认行为如下所示。

- 创建一个默认转换器，尝试在绑定源值和绑定目标值之间执行类型转换。 如果不能进行转换，默认转换器会返回 `null`。

- 如果未设置，则 <xref:System.Windows.Data.Binding.ConverterCulture%2A> 绑定引擎将使用 `Language` 绑定目标对象的属性。 在 XAML 中，此属性默认为“en-US”，如果已显式设置了一个值，则从页面的根元素（或任何元素）继承该值。

- 只要绑定已具有数据上下文（例如，来自父元素的继承数据上下文），并且该上下文返回的任何项或集合无需进一步修改路径即适用于绑定，则绑定声明可以不必使用任何子句：`{Binding}`。这通常是为数据样式指定绑定所用的方法，其中该绑定作用于某个集合。 有关详细信息，请参阅[绑定源概述](binding-sources-overview.md)中的“整个对象用作绑定源”一节。

- 根据所 <xref:System.Windows.Data.Binding.Mode%2A> 绑定的依赖属性，默认值不同于单向和双向。 始终可以显式声明绑定模式，以确保绑定具有所需行为。 通常，用户可编辑的控件属性（如 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> 和 <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType> ）默认为双向绑定，而其他大多数属性默认为单向绑定。

- 默认 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> 在和之间也不同， <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> 具体取决于绑定的依赖项属性。 大多数依赖属性的默认值为 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>，而 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> 属性的默认值为 <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>。

## <a name="see-also"></a>请参阅

- [数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)
- [操作指南主题](data-binding-how-to-topics.md)
- [数据绑定](../advanced/optimizing-performance-data-binding.md)
- [PropertyPath XAML 语法](../advanced/propertypath-xaml-syntax.md)
