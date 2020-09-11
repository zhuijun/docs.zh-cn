---
title: 数据绑定概述
description: 了解可在适用于 .NET Core 的 Windows Presentation Foundation 中添加到项目的不同数据源。 数据源可以绑定到 XAML 元素以创建动态应用。
author: adegeo
ms.date: 09/19/2019
ms.author: adegeo
dev_langs:
- csharp
- vb
ms.openlocfilehash: 3c9615d7d79b5da1c180bb505f5f37b99aeae775
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271992"
---
# <a name="data-binding-overview-in-wpf"></a>WPF 中的数据绑定概述

Windows Presentation Foundation (WPF) 中的数据绑定为应用呈现数据并与数据交互提供了一种简单而一致的方法。 元素能够以 .NET 对象和 XML 的形式绑定到各种数据源中的数据。 所有 <xref:System.Windows.Controls.ContentControl>（例如 <xref:System.Windows.Controls.Button>）以及所有 <xref:System.Windows.Controls.ItemsControl>（例如 <xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.ListView>）都具有内置功能，使单个数据项或数据项集合可以灵活地进行样式设置。 可基于数据生成排序、筛选和分组视图。

WPF 中的数据绑定功能与传统模型相比具有几个优点，包括本质上支持数据绑定的大量属性、灵活的数据 UI 表示形式以及业务逻辑与 UI 的完全分离。

本文首先讨论 WPF 数据绑定的基本概念，然后介绍 <xref:System.Windows.Data.Binding> 类的用法和数据绑定的其他功能。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-data-binding"></a>什么是数据绑定？

数据绑定是在应用 UI 与其显示的数据之间建立连接的过程。 如果绑定具有正确的设置，并且数据提供适当的通知，则在数据更改其值时，绑定到该数据的元素会自动反映更改。 数据绑定还意味着，如果元素中数据的外部表示形式发生更改，则基础数据可以自动进行更新以反映更改。 例如，如果用户编辑 `TextBox` 元素中的值，则基础数据值会自动更新以反映该更改。

数据绑定的典型用法是将服务器或本地配置数据放置到窗体或其他 UI 控件中。 此概念在 WPF 中得到扩展，包括将大量属性绑定到各种数据源。 在 WPF 中，元素的依赖属性可以绑定到 .NET 对象（包括 ADO.NET 对象或与 Web 服务和 Web 属性关联的对象）和 XML 数据。

有关数据绑定的示例，请参阅[数据绑定演示][data-binding-demo]（显示拍卖项的列表）中的以下应用 UI。

![数据绑定示例屏幕截图](./media/data-binding-overview/demo.png "DataBinding_DataBindingDemo")

应用演示了数据绑定的以下功能：

- ListBox 的内容已绑定到 *AuctionItem* 对象的集合。 *AuctionItem* 对象具有 *Description*、*StartPrice*、*StartDate*、*Category*、*SpecialFeatures* 等属性。

- `ListBox` 中显示的数据（*AuctionItem* 对象）已进行模板化，以便显示每个项的说明和当前价格。 通过使用 <xref:System.Windows.DataTemplate> 来创建模板。 此外，每个项的外观取决于要显示的 *AuctionItem* 的 *SpecialFeatures* 值。 如果 *AuctionItem* 的 *SpecialFeatures* 值为 *Color*，则该项具有蓝色边框。 如果值为 *Highlight*，则该项具有橙色边框和一个星号。 [数据模板化](#data-templating)部分提供了数据模板化的相关信息。

- 用户可以使用提供的 `CheckBoxes` 对数据进行分组、筛选或排序。 在上图中，选中了“按类别分组”和“按类别和日期排序”`CheckBoxes` 。 你可能已注意到，数据按产品类别分组，类别名称按字母顺序排序。 这些项还按每个类别中的开始日期排序，但难以从图中注意到这一点。 排序使用*集合视图*实现。 [绑定到集合](#binding-to-collections)部分讨论了集合视图。

- 当用户选择某个项时，<xref:System.Windows.Controls.ContentControl> 显示所选项的详细信息。 此体验称为*主-从方案*。 [主-从方案](#master-detail-binding-scenario)部分提供有关此绑定类型的信息。

- *StartDate* 属性的类型为 <xref:System.DateTime>，该类型返回一个包括精确到毫秒的时间的日期。 在此应用中，使用了一个自定义转换器，以便显示较短的日期字符串。 [数据转换](#data-conversion)部分提供有关转换器的信息。

当用户选择“添加产品”按钮时，会出现以下窗体。

![“添加产品清单”页](./media/data-binding-overview/demo-addproductlisting.png "DataBinding_Demo_AddProductListing")

用户可以编辑窗体中的字段，使用简略或详细预览窗格预览产品清单，然后选择 `Submit` 以添加新的产品清单。 任何现有的分组、筛选和排序设置都将应用于新条目。 在这种特殊情况下，上图中输入的项会作为 *Computer* 类别中的第二项显示。

“开始日期”<xref:System.Windows.Controls.TextBox> 中提供的验证逻辑未在此图中显示。 如果用户输入一个无效日期（格式无效或日期已过），则会通过 <xref:System.Windows.Controls.ToolTip> 和 <xref:System.Windows.Controls.TextBox> 旁边显示的红色感叹号来通知用户。 [数据验证](#data-validation)一节讨论了如何创建验证逻辑。

在详细介绍数据绑定的上述不同功能之前，我们会先讨论对理解 WPF 数据绑定非常重要的基本概念。

## <a name="basic-data-binding-concepts"></a>数据绑定基本概念

不论要绑定什么元素，也不论数据源是什么性质，每个绑定都始终遵循下图所示的模型。

![显示基本数据绑定模型的图。](./media/data-binding-overview/basic-data-binding-diagram.png)

如图所示，数据绑定实质上是绑定目标与绑定源之间的桥梁。 该图演示了以下基本的 WPF 数据绑定概念：

- 通常情况下，每个绑定具有四个组件：

  - 绑定目标对象。
  - 目标属性。
  - 绑定源。
  - 指向绑定源中要使用的值的路径。
  
  > 例如，如果要将 `TextBox` 的内容绑定到 `Employee.Name` 属性，则目标对象是 `TextBox`，目标属性是 <xref:System.Windows.Controls.TextBox.Text%2A> 属性，要使用的值是 *Name*，源对象是 *Employee* 对象。

- 目标属性必须为依赖属性。 大多数 <xref:System.Windows.UIElement> 属性都是依赖属性，而大多数依赖属性（只读属性除外）默认支持数据绑定。 （仅派生自 <xref:System.Windows.DependencyObject> 的类型才能定义依赖属性；所有 <xref:System.Windows.UIElement> 类型都派生自 `DependencyObject`。）

- 尽管未在图中显示，但请注意，绑定源对象不限于自定义 .NET 对象。 WPF 数据绑定支持 .NET 对象和 XML 形式的数据。 例如，绑定源可以是 <xref:System.Windows.UIElement>、任何列表对象、ADO.NET 或 Web 服务对象，或包含 XML 数据的 XmlNode。 有关详细信息，请参阅[绑定源概述](../../framework/wpf/data/binding-sources-overview.md)。

请务必记住，在建立绑定时，需要将绑定目标*绑定到*绑定源。 例如，如果要使用数据绑定在 <xref:System.Windows.Controls.ListBox> 中显示一些基础 XML 数据，则需要将 `ListBox` 绑定到 XML 数据。

若要建立绑定，请使用 <xref:System.Windows.Data.Binding> 对象。 本文的其余部分讨论了与 `Binding` 对象相关的许多概念以及该对象的一些属性和用法。

### <a name="direction-of-the-data-flow"></a>数据流的方向

正如上图中的箭头所示，绑定的数据流可以从绑定目标流向绑定源（例如，当用户编辑 `TextBox` 的值时，源值会发生更改）和/或（在绑定源提供正确通知的情况下）从绑定源流向绑定目标（例如，`TextBox` 内容会随绑定源中的更改而进行更新）。

你可能希望应用允许用户更改数据，然后将该数据传播回源对象。 或者，可能不希望允许用户更新源数据。 可以通过设置 <xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType> 来控制数据流。

此图演示了不同类型的数据流：

![数据绑定数据流](./media/data-binding-overview/databinding-dataflow.png "DataBinding_DataFlow")

- 通过 <xref:System.Windows.Data.BindingMode.OneWay> 绑定，对源属性的更改会自动更新目标属性，但对目标属性的更改不会传播回源属性。 如果绑定的控件为隐式只读，则此类型的绑定适用。 例如，可能会绑定到股票行情自动收录器这样的源，也可能目标属性没有用于进行更改的控件接口（例如表的数据绑定背景色）。 如果无需监视目标属性的更改，则使用 <xref:System.Windows.Data.BindingMode.OneWay> 绑定模式可避免 <xref:System.Windows.Data.BindingMode.TwoWay> 绑定模式的系统开销。

- 通过 <xref:System.Windows.Data.BindingMode.TwoWay> 绑定，更改源属性或目标属性时会自动更新另一方。 此类型的绑定适用于可编辑窗体或其他完全交互式 UI 方案。 大多数属性默认为 <xref:System.Windows.Data.BindingMode.OneWay> 绑定，但某些依赖属性（通常为用户可编辑控件的属性，例如 <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType> 和 [CheckBox.IsChecked](xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked)）默认为 <xref:System.Windows.Data.BindingMode.TwoWay> 绑定。 用于确定依赖属性绑定在默认情况下是单向还是双向的编程方法是：使用 <xref:System.Windows.DependencyProperty.GetMetadata%2A?displayProperty=nameWithType> 获取属性元数据，然后检查 <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A?displayProperty=nameWithType> 属性的布尔值。

- <xref:System.Windows.Data.BindingMode.OneWayToSource> 绑定与 <xref:System.Windows.Data.BindingMode.OneWay> 绑定相反；当目标属性更改时，它会更新源属性。 一个示例方案是只需要从 UI 重新计算源值的情况。

- <xref:System.Windows.Data.BindingMode.OneTime> 绑定未在图中显示，该绑定会使源属性初始化目标属性，但不传播后续更改。 如果数据上下文发生更改，或者数据上下文中的对象发生更改，则更改*不会*在目标属性中反映。 如果适合使用当前状态的快照或数据实际为静态数据，则此类型的绑定适合。 如果你想使用源属性中的某个值来初始化目标属性，且提前不知道数据上下文，则此类型的绑定也有用。 此模式实质上是 <xref:System.Windows.Data.BindingMode.OneWay> 绑定的一种简化形式，它在源值不更改的情况下提供更好的性能。

若要检测源更改（适用于 <xref:System.Windows.Data.BindingMode.OneWay> 和 <xref:System.Windows.Data.BindingMode.TwoWay> 绑定），则源必须实现合适的属性更改通知机制，例如 <xref:System.ComponentModel.INotifyPropertyChanged>。 请参阅[如何：实现属性更改通知](../../framework/wpf/data/how-to-implement-property-change-notification.md)，获取 <xref:System.ComponentModel.INotifyPropertyChanged> 实现的示例。

<xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType> 属性提供有关绑定模式的详细信息，以及如何指定绑定方向的示例。

### <a name="what-triggers-source-updates"></a>触发源更新的因素

<xref:System.Windows.Data.BindingMode.TwoWay> 或 <xref:System.Windows.Data.BindingMode.OneWayToSource> 绑定侦听目标属性中的更改，并将更改传播回源（称为更新源）。 例如，可以编辑文本框的文本以更改基础源值。

但是，在编辑文本时或完成文本编辑后控件失去焦点时，源值是否会更新？ <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> 属性确定触发源更新的因素。 下图中右箭头的点说明了 <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> 属性的角色。

![显示 UpdateSourceTrigger 属性的角色的图。](./media/data-binding-overview/data-binding-updatesource-trigger.png)

如果 `UpdateSourceTrigger` 值为 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged?displayProperty=nameWithType>，则目标属性更改后，<xref:System.Windows.Data.BindingMode.TwoWay> 或 <xref:System.Windows.Data.BindingMode.OneWayToSource> 绑定的右箭头指向的值会立即更新。 但是，如果 `UpdateSourceTrigger` 值为 <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>，则仅当目标属性失去焦点时才会使用新值更新该值。

与 <xref:System.Windows.Data.Binding.Mode%2A> 属性类似，不同的依赖属性具有不同的默认 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值。 大多数依赖属性的默认值为 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>，而 `TextBox.Text` 属性的默认值为 <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>。 `PropertyChanged` 表示源更新通常在每次目标属性更改时发生。 即时更改适用于 CheckBox 和其他简单控件。 但对于文本字段，每次击键后都进行更新会降低性能，用户也没有机会在提交新值之前使用 Backspace 键修改键入错误。

有关如何查找依赖属性的默认值的信息，请参阅 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 属性页。

下表以 <xref:System.Windows.Controls.TextBox> 为例，提供每个 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值的示例方案。

| UpdateSourceTrigger 值 | 源值更新时间 | TextBox 的示例方案 |
| ------------------------- | ---------------------------------- | ---------------------------- |
| `LostFocus`（<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> 的默认值） | TextBox 控件失去焦点时。 | 与验证逻辑关联的 TextBox（请参阅下文的[数据验证](#data-validation)）。 |
| `PropertyChanged` | 键入 <xref:System.Windows.Controls.TextBox> 时。 | 聊天室窗口中的 TextBox 控件。 |
| `Explicit` | 应用调用 <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> 时。 | 可编辑窗体中的 TextBox 控件（仅当用户单击“提交”按钮时才更新源值）。 |

有关示例，请参见 [如何：控制 TextBox 文本更新源的时间](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)。

## <a name="creating-a-binding"></a>创建绑定

前面部分中讨论的一些概念可以重申为：使用 <xref:System.Windows.Data.Binding> 对象建立绑定，且每个绑定通常具有四个组件：绑定目标、目标属性、绑定源以及指向要使用的源值的路径。 本节讨论如何设置绑定。

请考虑以下示例，其中的绑定源对象是一个名为 *MyData* 的类，该类在 *SDKSample* 命名空间中定义。 出于演示目的，*MyData* 具有名为 *ColorName* 的字符串属性，其值设置为“Red”。 因此，此示例生成一个具有红色背景的按钮。

[!code-xaml[BindNonTextProperty](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColor)]

有关绑定声明语法的详细信息以及如何在代码中设置绑定的示例，请参阅[绑定声明概述](../../framework/wpf/data/binding-declarations-overview.md)。

如果将此示例应用于基本关系图，则生成的图如下所示。 此图描述 <xref:System.Windows.Data.BindingMode.OneWay> 绑定，因为 Background 属性默认支持 <xref:System.Windows.Data.BindingMode.OneWay> 绑定。

![显示数据绑定 Background 属性的图。](./media/data-binding-overview/data-binding-button-background-example.png)

你可能会想知道，此绑定为何在 *ColorName* 属性的类型为字符串而 <xref:System.Windows.Controls.Control.Background%2A> 属性的类型为 <xref:System.Windows.Media.Brush> 的情况下也会起作用。 此绑定使用默认类型转换，这会在[数据转换](#data-conversion)部分中进行讨论。

### <a name="specifying-the-binding-source"></a>指定绑定源

请注意，在前面的示例中，通过设置 [DockPanel.DataContext](xref:System.Windows.FrameworkElement.DataContext) 属性指定绑定源。 然后，<xref:System.Windows.Controls.Button> 从其父元素 <xref:System.Windows.Controls.DockPanel> 继承 <xref:System.Windows.FrameworkElement.DataContext%2A> 值。 重申一下，绑定源对象是绑定的四个必需组件之一。 因此，如果未指定绑定源对象，则绑定将没有任何作用。

可通过多种方法指定绑定源对象。 将多个属性绑定到同一个源时，可以使用父元素上的 <xref:System.Windows.FrameworkElement.DataContext%2A> 属性。 不过，有时在个别绑定声明中指定绑定源可能更为合适。 对于前面的示例，不使用 <xref:System.Windows.FrameworkElement.DataContext%2A> 属性，而是通过在按钮的绑定声明中直接设置 <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> 属性来指定绑定源，如以下示例所示。

[!code-xaml[BindNonTextPropertyCompactBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColorCompactBinding)]

除直接在元素中设置 <xref:System.Windows.FrameworkElement.DataContext%2A> 属性、从上级元素（例如第一个示例中的按钮）继承 <xref:System.Windows.FrameworkElement.DataContext%2A> 值以及通过在绑定上设置 <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> 属性（例如最后一个示例中的按钮）来显式指定绑定源外，你还可以使用 <xref:System.Windows.Data.Binding.ElementName?displayProperty=nameWithType> 属性或 <xref:System.Windows.Data.Binding.RelativeSource?displayProperty=nameWithType> 属性指定绑定源。 当绑定到应用中的其他元素时（例如，使用滑块调整按钮的宽度时），<xref:System.Windows.Data.Binding.ElementName%2A> 属性非常有用。 在 <xref:System.Windows.Controls.ControlTemplate> 或 <xref:System.Windows.Style> 中指定绑定时，可以使用 <xref:System.Windows.Data.Binding.RelativeSource%2A> 属性。 有关详细信息，请参阅[如何：指定绑定源](../../framework/wpf/data/how-to-specify-the-binding-source.md)。

### <a name="specifying-the-path-to-the-value"></a>指定指向值的路径

如果绑定源是一个对象，则使用 <xref:System.Windows.Data.Binding.Path?displayProperty=nameWithType> 属性指定要用于绑定的值。 如果要绑定到 XML 数据，则使用 <xref:System.Windows.Data.Binding.XPath?displayProperty=nameWithType> 属性指定值。 在某些情况下，使用 <xref:System.Windows.Data.Binding.Path%2A> 属性（即使数据为 XML）可能更为合适。 例如，如果要访问返回的 XmlNode（作为 XPath 查询的结果）的 Name 属性，则除 <xref:System.Windows.Data.Binding.XPath%2A> 属性外，还应使用 <xref:System.Windows.Data.Binding.Path%2A> 属性。

有关详细信息，请参阅 <xref:System.Windows.Data.Binding.Path%2A> 和 <xref:System.Windows.Data.Binding.XPath%2A> 属性。

虽然我们已强调要使用的值的 <xref:System.Windows.Data.Binding.Path%2A> 是绑定的四个必需组件之一，但在要绑定到整个对象的方案中，要使用的值会与绑定源对象相同。 在这些情况下，可以不指定 <xref:System.Windows.Data.Binding.Path%2A>。 请看下面的示例。

[!code-xaml[EmptyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/EmptyBinding.xaml#EmptyBinding)]

以上示例使用空绑定语法：{Binding}。 在此示例中，<xref:System.Windows.Controls.ListBox> 从父 DockPanel 元素继承 DataContext（此示例中未显示）。 未指定路径时，默认为绑定到整个对象。 换句话说，此示例中的路径已省略，因为要将 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 属性绑定到整个对象。 （有关深入讨论，请参阅[绑定到集合](#binding-to-collections)部分。）

除了绑定到集合以外，在希望绑定到整个对象，而不是仅绑定到对象的单个属性时，也可以使用此方案。 例如，如果源对象的类型为 <xref:System.String>，则可能仅希望绑定到字符串本身。 另一种常见情况是希望将一个元素绑定到一个具有多个属性的对象。

你可能需要应用自定义逻辑，以便数据对于绑定的目标属性有意义。 如果不存在默认类型转换，则自定义逻辑可能采用自定义转换器的形式。 有关转换器的信息，请参阅[数据转换](#data-conversion)。

### <a name="binding-and-bindingexpression"></a>Binding 和 BindingExpression

在介绍数据绑定的其他功能和用法前，先介绍一下 <xref:System.Windows.Data.BindingExpression> 类会很有用。 如前面部分所述，<xref:System.Windows.Data.Binding> 类是用于绑定声明的高级类；该类提供许多供用户指定绑定特征的属性。 相关类 <xref:System.Windows.Data.BindingExpression> 是维持源与目标之间连接的基础对象。 一个绑定包含了可以在多个绑定表达式之间共享的所有信息。 <xref:System.Windows.Data.BindingExpression> 是无法共享的实例表达式，并包含 <xref:System.Windows.Data.Binding> 的所有实例信息。

举例来说，假设 `myDataObject` 是 `MyData` 类的实例，`myBinding` 是源 <xref:System.Windows.Data.Binding> 对象，而 `MyData` 是包含名为 `ColorName` 的字符串属性的定义类。 此示例将 <xref:System.Windows.Controls.TextBlock> 的实例 `myText` 的文本内容绑定到 `ColorName`。

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ManualBinding.cs#CodeOnlyBinding)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ManualBinding.vb#CodeOnlyBinding)]

可以使用同一 *myBinding* 对象来创建其他绑定。 例如，可使用 myBinding 对象将复选框的文本内容绑定到 ColorName 。 在该方案中，将有两个 <xref:System.Windows.Data.BindingExpression> 实例共享 *myBinding* 对象。

通过对数据绑定对象调用 <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> 来返回 <xref:System.Windows.Data.BindingExpression> 对象。 以下文章演示了 <xref:System.Windows.Data.BindingExpression> 类的一些用法：

- [从绑定目标属性获取绑定对象](../../framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)

- [控制 TextBox 文本更新源的时间](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)

## <a name="data-conversion"></a>数据转换

在[创建绑定](#creating-a-binding)部分中，该按钮为红色，因为其 <xref:System.Windows.Controls.Control.Background%2A> 属性绑定到值为“Red”的字符串属性。 此字符串值有效是因为 <xref:System.Windows.Media.Brush> 类型中存在类型转换器，可用于将字符串值转换为 <xref:System.Windows.Media.Brush>。

将此信息添加到[创建绑定](#creating-a-binding)部分的关系图中，使其如下所示。

![显示数据绑定 Default 属性的图。](./media/data-binding-overview/data-binding-button-default-conversion.png)

但是，如果绑定源对象拥有的不是字符串类型的属性，而是 <xref:System.Windows.Media.Color> 类型的 *Color* 属性，该怎么办？ 在这种情况下，为了使绑定正常工作，首先需要将 *Color* 属性值转换为 <xref:System.Windows.Controls.Control.Background%2A> 属性可接受的值。 需要通过实现 <xref:System.Windows.Data.IValueConverter> 接口来创建一个自定义转换器，如以下示例所示。

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ColorBrushConverter.cs#ColorBrushConverter)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ColorBrushConverter.vb#ColorBrushConverter)]

有关更多信息，请参见<xref:System.Windows.Data.IValueConverter>。

现在，使用的是自定义转换器而不是默认转换，关系图如下所示。

![显示数据绑定自定义转换器的图。](./media/data-binding-overview/data-binding-converter-color-example.png)

重申一下，由于要绑定到的类型中提供了类型转换器，因此可以使用默认转换。 此行为取决于目标中可用的类型转换器。 如果无法确定，请创建自己的转换器。

下面提供了一些典型方案，在这些方案中，实现数据转换器非常有意义：

- 数据应根据区域性以不同方式显示。 例如，可能需要根据在特定区域性中使用的约定，实现货币转换器或日历日期/时间转换器。

- 使用的数据不一定会更改属性的文本值，但会更改其他某个值（如图像的源，或显示文本的颜色或样式）。 在这种情况下，可以通过转换可能不合适的属性绑定（如将文本字段绑定到表单元格的 Background 属性）来使用转换器。

- 多个控件或控件的多个属性会绑定到相同数据。 在这种情况下，主绑定可能仅显示文本，而其他绑定则处理特定的显示问题，但仍使用同一绑定作为源信息。

- 目标属性具有绑定集合，称为 <xref:System.Windows.Data.MultiBinding>。 对于 <xref:System.Windows.Data.MultiBinding>，使用自定义 <xref:System.Windows.Data.IMultiValueConverter> 从绑定的值中生成最终值。 例如，可以从红色、蓝色和绿色的值来计算颜色，这些值可能来自相同绑定源对象，也可能来自不同绑定源对象。 有关示例和信息，请参阅 <xref:System.Windows.Data.MultiBinding>。

## <a name="binding-to-collections"></a>绑定到集合

绑定源对象可以被视为其属性包含数据的单个对象，也可以被视为通常组合在一起的多态对象的数据集合（例如数据库查询的结果）。 目前为止，我们仅讨论了绑定到单个对象， 但绑定到数据集合也是常见方案。 例如，一种常见方案是使用 <xref:System.Windows.Controls.ItemsControl>（例如 <xref:System.Windows.Controls.ListBox>、<xref:System.Windows.Controls.ListView> 或 <xref:System.Windows.Controls.TreeView>）来显示数据集合，如在[什么是数据绑定](#what-is-data-binding)部分所示的应用中。

幸运的是，基本关系图仍然适用。 如果将 <xref:System.Windows.Controls.ItemsControl> 绑定到集合，则关系图如下所示。

![显示数据绑定 ItemsControl 对象的图。](./media/data-binding-overview/data-binding-itemscontrol.png)

如图所示，若要将 <xref:System.Windows.Controls.ItemsControl> 绑定到集合对象，则需要使用 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A?displayProperty=nameWithType> 属性。 你可以将 `ItemsSource` 视为 <xref:System.Windows.Controls.ItemsControl> 的内容。 绑定为 <xref:System.Windows.Data.BindingMode.OneWay>，因为 `ItemsSource` 属性默认支持 `OneWay` 绑定。

### <a name="how-to-implement-collections"></a>如何实现集合

你可以枚举实现 <xref:System.Collections.IEnumerable> 接口的任何集合。 但是，若要设置动态绑定，以便集合中的插入或删除操作可以自动更新 UI，则集合必须实现 <xref:System.Collections.Specialized.INotifyCollectionChanged> 接口。 此接口公开一个事件，只要基础集合发生更改，就应该引发该事件。

WPF 提供 <xref:System.Collections.ObjectModel.ObservableCollection%601> 类，该类是公开 <xref:System.Collections.Specialized.INotifyCollectionChanged> 接口的数据集合的内置实现。 若要完全支持将数据值从源对象传输到目标，支持可绑定属性的集合中的每个对象还必须实现 <xref:System.ComponentModel.INotifyPropertyChanged> 接口。 有关详细信息，请参阅[绑定源概述](../../framework/wpf/data/binding-sources-overview.md)。

在实现自己的集合前，请考虑使用 <xref:System.Collections.ObjectModel.ObservableCollection%601> 或现有集合类之一，例如 <xref:System.Collections.Generic.List%601>、<xref:System.Collections.ObjectModel.Collection%601> 和 <xref:System.ComponentModel.BindingList%601> 等。 如果有高级方案并且希望实现自己的集合，请考虑使用 <xref:System.Collections.IList>，它提供可以按索引逐个访问的对象的非泛型集合，因而可提供最佳性能。

### <a name="collection-views"></a>集合视图

在 <xref:System.Windows.Controls.ItemsControl> 绑定到数据集合后，你可能希望对数据进行排序、筛选或分组。 为此，应使用集合视图，这些视图是实现 <xref:System.ComponentModel.ICollectionView> 接口的类。

#### <a name="what-are-collection-views"></a>什么是集合视图？

集合视图这一层基于绑定源集合，它允许基于排序、筛选和分组查询来导航并显示源集合，而无需更改基础源集合本身。 集合视图还维护一个指向集合中当前项的指针。 如果源集合实现 <xref:System.Collections.Specialized.INotifyCollectionChanged> 接口，则 <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> 事件引发的更改会传播到视图。

由于视图不会更改基础源集合，因此每个源集合都可以有多个关联的视图。 例如，可以有 *Task* 对象的集合。 使用视图，可以通过不同方式显示相同数据。 例如，可能希望在页面左侧显示按优先级排序的任务，而在页面右侧显示按区域分组的任务。

#### <a name="how-to-create-a-view"></a>如何创建视图

创建并使用视图的一种方式是直接实例化视图对象，然后将它用作绑定源。 以[什么是数据绑定](#what-is-data-binding)部分中所示的[数据绑定演示][data-binding-demo]应用为例。 该应用的实现方式是将 <xref:System.Windows.Controls.ListBox> 绑定到基于数据集合的视图，而不是直接绑定到数据集合。 下面的示例摘自[数据绑定演示][data-binding-demo]应用。 <xref:System.Windows.Data.CollectionViewSource> 类是从 <xref:System.Windows.Data.CollectionView> 继承的类的 XAML 代理。 在此特定示例中，视图的 <xref:System.Windows.Data.CollectionViewSource.Source%2A> 绑定到当前应用对象的 *AuctionItem* 集合（类型为 <xref:System.Collections.ObjectModel.ObservableCollection%601>）。

[!code-xaml[CollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#CollectionView)]

资源 *listingDataView* 随后用作应用中元素（例如 <xref:System.Windows.Controls.ListBox>）的绑定源。

[!code-xaml[ListBoxCollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxCollectionView)]

若要为同一集合创建另一个视图，则可以创建另一个 <xref:System.Windows.Data.CollectionViewSource> 实例，并为其提供不同的 `x:Key` 名称。

下表显示作为默认集合视图创建或由 <xref:System.Windows.Data.CollectionViewSource> 根据源集合类型创建的视图数据类型。

| 源集合类型                    | 集合视图类型 | 说明 |
| ----------------------------------------- | -------------------- | ----- |
| <xref:System.Collections.IEnumerable>     | 基于 <xref:System.Windows.Data.CollectionView> 的内部类型 | 无法对项进行分组。 |
| <xref:System.Collections.IList>           | <xref:System.Windows.Data.ListCollectionView> | 最快。 |
| <xref:System.ComponentModel.IBindingList> | <xref:System.Windows.Data.BindingListCollectionView> | |

#### <a name="using-a-default-view"></a>使用默认视图

创建并使用集合视图的一种方式是指定集合视图作为绑定源。 WPF 还会为用作绑定源的每个集合创建一个默认集合视图。 如果直接绑定到集合，WPF 会绑定到该集合的默认视图。 此默认视图由同一集合的所有绑定共享，因此一个绑定控件或代码对默认视图所做的更改（例如排序或对当前项指针的更改，下文将对此进行讨论）会在同一集合的所有其他绑定中反映。

若要获取默认视图，请使用 <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> 方法。 有关示例，请参阅[获取数据集合的默认视图](../../framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)。

#### <a name="collection-views-with-adonet-datatables"></a>包含 ADO.NET DataTables 的集合视图

为了提高性能，ADO.NET <xref:System.Data.DataTable> 或 <xref:System.Data.DataView> 对象的集合视图将排序和筛选委托给 <xref:System.Data.DataView>，这导致排序和筛选在数据源的所有集合视图之间共享。 若要使每个集合视图都能独立进行排序和筛选，请使用每个集合视图自己的 <xref:System.Data.DataView> 对象进行初始化。

#### <a name="sorting"></a>排序

如前所述，视图可以将排序顺序应用于集合。 如同在基础集合中一样，数据可能具有或不具有相关的固有顺序。 借助集合视图，可以根据自己提供的比较条件来强制确定顺序，或更改默认顺序。 由于这是基于客户端的数据视图，因此一种常见情况是用户可能希望根据列对应的值，对多列表格数据进行排序。 通过使用视图，可以应用这种用户实施的排序，而无需对基础集合进行任何更改，甚至不必再次查询集合内容。 有关示例，请参阅[在单击标题时对 GridView 列进行排序](../../framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)。

以下示例演示了[什么是数据绑定](#what-is-data-binding)部分中的应用 UI 的“按类别和日期排序”<xref:System.Windows.Controls.CheckBox> 的排序逻辑。

[!code-csharp[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#AddSortChecked)]
[!code-vb[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#AddSortChecked)]

#### <a name="filtering"></a>筛选

视图还可以将筛选器应用于集合，以便视图仅显示完整集合的特定子集。 可以根据条件在数据中进行筛选。 例如，正如[什么是数据绑定](#what-is-data-binding)部分中的应用所做的那样，“仅显示成交商品”<xref:System.Windows.Controls.CheckBox> 包含了筛选出成交价等于或大于 25 美元的项的逻辑。 如果选择了 <xref:System.Windows.Controls.CheckBox>，则会执行以下代码将 *ShowOnlyBargainsFilter* 设置为 <xref:System.Windows.Data.CollectionViewSource.Filter> 事件处理程序。

[!code-csharp[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingViewFilter)]
[!code-vb[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingViewFilter)]

*ShowOnlyBargainsFilter* 事件处理程序具有以下实现。

[!code-csharp[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#FilterEvent)]
[!code-vb[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#FilterEvent)]

如果直接使用其中一个 <xref:System.Windows.Data.CollectionView> 类而不是 <xref:System.Windows.Data.CollectionViewSource>，则可以使用 <xref:System.Windows.Data.CollectionView.Filter%2A> 属性指定回叫。 有关示例，请参阅[筛选视图中的数据](../../framework/wpf/data/how-to-filter-data-in-a-view.md)。

#### <a name="grouping"></a>分组

除了用来查看 <xref:System.Collections.IEnumerable> 集合的内部类之外，所有集合视图都支持*分组*功能，用户可以利用此功能将集合视图中的集合划分成逻辑组。 这些组可以是显式的，由用户提供组列表；也可以是隐式的，这些组依据数据动态生成。

以下示例演示了“按类别分组”<xref:System.Windows.Controls.CheckBox> 的逻辑。

[!code-csharp[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingGroupCheck)]
[!code-vb[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingGroupCheck)]

有关其他分组示例，请参阅[对实现 GridView 的 ListView 中的项进行分组](../../framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md)。

#### <a name="current-item-pointers"></a>当前项指针

视图还支持当前项的概念。 可以在集合视图中的对象之间导航。 在导航时，你是在移动项指针，该指针可用于检索存在于集合中特定位置的对象。 有关示例，请参阅[在数据 CollectionView 中的对象之间导航](../../framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md)。

由于 WPF 只通过使用视图（你指定的视图或集合的默认视图）绑定到集合，因此集合的所有绑定都有一个当前项指针。 绑定到视图时，`Path` 值中的斜杠（“/”）字符用于指定视图的当前项。 在下面的示例中，数据上下文是一个集合视图。 第一行绑定到集合。 第二行绑定到集合中的当前项。 第三行绑定到集合中当前项的 `Description` 属性。

```xaml
<Button Content="{Binding }" />
<Button Content="{Binding Path=/}" />
<Button Content="{Binding Path=/Description}" />
```

还可以连着使用斜杠和属性语法以遍历集合的分层。 以下示例绑定到一个名为 `Offices` 的集合的当前项，此集合是源集合的当前项的属性。

```xaml
<Button Content="{Binding /Offices/}" />
```

当前项指针可能会受对集合应用的任何排序或筛选操作的影响。 排序操作将当前项指针保留在所选的最后一项上，但集合视图现已围绕此指针重构。 （或许所选项以前曾位于列表的开头，但现在所选项可能位于中间的某个位置。）如果所选内容在筛选之后保留在视图中，则筛选操作会保留所选项。 否则，当前项指针会设置为经过筛选的集合视图的第一项。

#### <a name="master-detail-binding-scenario"></a>主-从绑定方案

当前项的概念不仅适用于集合中各项的导航，也适用于主-从绑定方案。 再考虑一下[什么是数据绑定](#what-is-data-binding)部分中的应用 UI。 在该应用中，<xref:System.Windows.Controls.ListBox> 中的选择确定 <xref:System.Windows.Controls.ContentControl> 中显示的内容。 换句话说，选择 <xref:System.Windows.Controls.ListBox> 项目时，<xref:System.Windows.Controls.ContentControl> 显示所选项的详细信息。

只需将两个或更多控件绑定到同一视图即可实现主-从方案。 [数据绑定演示][data-binding-demo]中的以下示例演示了在[什么是数据绑定](#what-is-data-binding)部分中的应用 UI 上看到的 <xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.ContentControl> 的标记。

[!code-xaml[ListBoxContentControl](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxContentControl)]

请注意，这两个控件都绑定到同一个源，即 *listingDataView* 静态资源（请参阅[如何创建视图](#how-to-create-a-view)部分中关于此资源的定义）。 此绑定有效是因为将单一实例对象（在本例中为 <xref:System.Windows.Controls.ContentControl>）绑定到集合视图时，它会自动绑定到该视图的 <xref:System.Windows.Data.CollectionView.CurrentItem%2A>。 <xref:System.Windows.Data.CollectionViewSource> 对象会自动同步货币和选择。 如果列表控件未像本示例中那样绑定到 <xref:System.Windows.Data.CollectionViewSource> 对象，则需要将其 <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> 属性设置为 `true` 才能起作用。

有关其他示例，请参阅[绑定到集合并基于选择显示信息](../../framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)和[对层次结构数据使用主-从模式](../../framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)。

你可能已经注意到上述示例使用了一个模板。 实际上，如果不使用模板（<xref:System.Windows.Controls.ContentControl> 显式使用的模板以及 <xref:System.Windows.Controls.ListBox> 隐式使用的模板），数据不会按照我们希望的方式显示。 现在，我们开始介绍下一节中的数据模板化。

## <a name="data-templating"></a>数据模板化

如果不使用数据模板，[什么是数据绑定](#what-is-data-binding)部分中的应用 UI 将如下所示。

![没有数据模板的数据绑定演示](./media/data-binding-overview/demo-no-template.png)

如前面部分中的示例所示，<xref:System.Windows.Controls.ListBox> 控件和 <xref:System.Windows.Controls.ContentControl> 都绑定到 *AuctionItem* 的整个集合对象（更具体地说，是绑定到集合对象视图）。 如果未提供如何显示数据集合的特定说明，则 <xref:System.Windows.Controls.ListBox> 会以字符串形式显示基础集合中的每个对象，<xref:System.Windows.Controls.ContentControl> 会以字符串形式显示绑定到的对象。

为了解决该问题，应用定义了 <xref:System.Windows.DataTemplate?text=DataTemplates>。 如前面部分中的示例所示，<xref:System.Windows.Controls.ContentControl> 显式使用 *detailsProductListingTemplate* 数据模板。 显示集合中的 *AuctionItem* 对象时，<xref:System.Windows.Controls.ListBox> 控件隐式使用以下数据模板。

[!code-xaml[AuctionItemDataTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#AuctionItemDataTemplate)]

使用这两个 DataTemplate 时，生成的 UI 即为[什么是数据绑定](#what-is-data-binding)部分中所示的 UI。 如屏幕截图所示，除了可以在控件中放置数据以外，使用 DataTemplate 还可以为数据定义引人注目的视觉对象。 例如，上述 <xref:System.Windows.DataTemplate> 中使用了 <xref:System.Windows.DataTrigger>，因而 *SpecialFeatures* 值为 *HighLight* 的 *AuctionItem* 会显示为带有橙色边框和一个星号。

有关数据模板的详细信息，请参阅[数据模板化概述](../../framework/wpf/data/data-templating-overview.md)。

## <a name="data-validation"></a>数据验证

接受用户输入的大多数应用都需要具有验证逻辑，以确保用户输入了预期信息。 可基于类型、范围、格式或特定于应用的其他要求执行验证检查。 本部分讨论数据验证在 WPF 中的工作原理。

### <a name="associating-validation-rules-with-a-binding"></a>将验证规则与绑定关联

WPF 数据绑定模型允许将 <xref:System.Windows.Data.Binding.ValidationRules%2A> 与 <xref:System.Windows.Data.Binding> 对象关联。 例如，以下示例将 <xref:System.Windows.Controls.TextBox> 绑定到名为 `StartPrice` 的属性，并将 <xref:System.Windows.Controls.ExceptionValidationRule> 对象添加到 <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> 属性。

[!code-xaml[TextboxStartPrice](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartPrice)]

<xref:System.Windows.Controls.ValidationRule> 对象检查属性的值是否有效。 WPF 有两种类型的内置 <xref:System.Windows.Controls.ValidationRule> 对象：

- <xref:System.Windows.Controls.ExceptionValidationRule> 检查在绑定源属性更新期间引发的异常。 在以上示例中，`StartPrice` 为整数类型。 当用户输入的值无法转换为整数时，将引发异常，这会导致将绑定标记为无效。 用于显式设置 <xref:System.Windows.Controls.ExceptionValidationRule> 的替代语法是在 <xref:System.Windows.Data.Binding> 或 <xref:System.Windows.Data.MultiBinding> 对象上将 <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> 属性设置为 `true`。

- <xref:System.Windows.Controls.DataErrorValidationRule> 对象检查实现 <xref:System.ComponentModel.IDataErrorInfo> 接口的对象所引发的错误。 有关使用此验证规则的示例，请参阅 <xref:System.Windows.Controls.DataErrorValidationRule>。 用于显式设置 <xref:System.Windows.Controls.DataErrorValidationRule> 的替代语法是在 <xref:System.Windows.Data.Binding> 或 <xref:System.Windows.Data.MultiBinding> 对象上将 <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> 属性设置为 `true`。

还可以通过从 <xref:System.Windows.Controls.ValidationRule> 类派生并实现 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法来创建自己的验证规则。 以下示例演示了[什么是数据绑定](#what-is-data-binding)部分中*添加产品清单*“起始日期”<xref:System.Windows.Controls.TextBox> 所用的规则。

[!code-csharp[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/FutureDateRule.cs#FutureDateRule)]
[!code-vb[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/FutureDateRule.vb#FutureDateRule)]

*StartDateEntryForm* <xref:System.Windows.Controls.TextBox> 使用此 *FutureDateRule*，如以下示例所示。

[!code-xaml[TextboxStartDate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartDate)]

因为 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值为 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>，所以绑定引擎会在每次击键时更新源值，这意味着它还会在每次击键时检查 <xref:System.Windows.Data.Binding.ValidationRules%2A> 集合中的每条规则。 我们会在“验证过程”一节中对此深入讨论。

### <a name="providing-visual-feedback"></a>提供视觉反馈

如果用户输入的值无效，你可能希望在应用 UI 上提供一些有关错误的反馈。 提供此类反馈的一种方法是将 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> 附加属性设置为自定义 <xref:System.Windows.Controls.ControlTemplate>。 如前面部分所示，*StartDateEntryForm* <xref:System.Windows.Controls.TextBox> 使用名为 *validationTemplate* 的 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A>。 以下示例显示了 *validationTemplate* 的定义。

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#ControlTemplate)]

<xref:System.Windows.Controls.AdornedElementPlaceholder> 元素指定应放置待装饰控件的位置。

此外，还可以使用 <xref:System.Windows.Controls.ToolTip> 来显示错误消息。 *StartDateEntryForm* 和 *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox> 都使用样式 *textStyleTextBox*，该样式创建显示错误消息的 <xref:System.Windows.Controls.ToolTip>。 以下示例显示了 *textStyleTextBox* 的定义。 如果绑定元素属性上的一个或多个绑定出错，则附加属性 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 为 `true`。

[!code-xaml[TextBoxStyle](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextBoxStyle)]

使用自定义 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> 和 <xref:System.Windows.Controls.ToolTip> 时，*StartDateEntryForm* <xref:System.Windows.Controls.TextBox> 在发生验证错误时如下所示。

![数据绑定验证错误](./media/data-binding-overview/demo-validation-date.png "DataBindingDemo_Validation")

如果 <xref:System.Windows.Data.Binding> 具有关联的验证规则，但未在绑定控件上指定 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A>，则发生验证错误时，将使用默认的 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> 通知用户。 默认的 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> 是一个控件模板，它在装饰层中定义红色边框。 使用默认的 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> 和 <xref:System.Windows.Controls.ToolTip> 时，*StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> 的 UI 在发生验证错误时如下所示。

![数据绑定验证错误](./media/data-binding-overview/demo-validation-price.png "DataBindingDemo_ValidationDefault")

有关如何提供逻辑以验证对话框中所有控件的示例，请参阅[对话框概述](../../framework/wpf/app-development/dialog-boxes-overview.md)中的“自定义对话框”部分。

### <a name="validation-process"></a>验证过程

通常，在目标的值传输到绑定源属性时会进行验证。 此传输在 <xref:System.Windows.Data.BindingMode.TwoWay> 和 <xref:System.Windows.Data.BindingMode.OneWayToSource> 绑定上发生。 重申一下，导致源更新的因素取决于 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 属性的值，如[触发源更新的因素](#what-triggers-source-updates)部分所述。

以下各项描述了*验证*过程。 只要验证过程中发生验证错误或其他类型的错误，该过程就会中断：

1. 绑定引擎检查是否为该 <xref:System.Windows.Data.Binding> 定义了任何将 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 设置为 <xref:System.Windows.Controls.ValidationStep.RawProposedValue> 的自定义 <xref:System.Windows.Controls.ValidationRule> 对象，在这种情况下，绑定引擎将对每个 <xref:System.Windows.Controls.ValidationRule> 调用 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法，直到其中一个出错或直到全部通过。

2. 绑定引擎随后会调用转换器（如果存在）。

3. 如果转换器成功，则绑定引擎会检查是否为该 <xref:System.Windows.Data.Binding> 定义了任何将 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 设置为 <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> 的自定义 <xref:System.Windows.Controls.ValidationRule> 对象，在这种情况下，绑定引擎将对每个 <xref:System.Windows.Controls.ValidationRule>（将 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 设置为 <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue>）调用 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法，直到其中一个出错或直到全部通过。

4. 绑定引擎设置源属性。

5. 绑定引擎检查是否为该 <xref:System.Windows.Data.Binding> 定义了任何将 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 设置为 <xref:System.Windows.Controls.ValidationStep.UpdatedValue> 的自定义 <xref:System.Windows.Controls.ValidationRule> 对象，在这种情况下，绑定引擎将对每个 <xref:System.Windows.Controls.ValidationRule>（将 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 设置为 <xref:System.Windows.Controls.ValidationStep.UpdatedValue>）调用 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法，直到其中一个出错或直到全部通过。 如果 <xref:System.Windows.Controls.DataErrorValidationRule> 与绑定关联并且其 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 设置为默认的 <xref:System.Windows.Controls.ValidationStep.UpdatedValue>，则此时将检查 <xref:System.Windows.Controls.DataErrorValidationRule>。 此时检查将 <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> 设置为 `true` 的所有绑定。

6. 绑定引擎检查是否为该 <xref:System.Windows.Data.Binding> 定义了任何将 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 设置为 <xref:System.Windows.Controls.ValidationStep.CommittedValue> 的自定义 <xref:System.Windows.Controls.ValidationRule> 对象，在这种情况下，绑定引擎将对每个 <xref:System.Windows.Controls.ValidationRule>（将 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 设置为 <xref:System.Windows.Controls.ValidationStep.CommittedValue>）调用 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法，直到其中一个出错或直到全部通过。

如果 <xref:System.Windows.Controls.ValidationRule> 在整个过程中的任何时间都没有通过，则绑定引擎会创建 <xref:System.Windows.Controls.ValidationError> 对象并将其添加到绑定元素的 <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> 集合中。 绑定引擎在任何给定步骤运行 <xref:System.Windows.Controls.ValidationRule> 对象之前，它会删除在执行该步骤期间添加到绑定元素的 <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> 附加属性的所有 <xref:System.Windows.Controls.ValidationError>。 例如，如果将 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 设置为 <xref:System.Windows.Controls.ValidationStep.UpdatedValue> 的 <xref:System.Windows.Controls.ValidationRule> 失败，则下次执行验证过程时，绑定引擎会在调用将 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> 设置为 <xref:System.Windows.Controls.ValidationStep.UpdatedValue> 的任何 <xref:System.Windows.Controls.ValidationRule> 之前删除 <xref:System.Windows.Controls.ValidationError>。

如果 <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> 不为空，则元素的 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加属性设置为 `true`。 此外，如果 <xref:System.Windows.Data.Binding> 的 <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> 属性设置为 `true`，则绑定引擎将在元素上引发 <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> 附加事件。

另请注意，任何方向（目标到源或源到目标）的有效值传输操作都会清除 <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> 附加属性。

如果绑定具有关联的 <xref:System.Windows.Controls.ExceptionValidationRule>，或将 <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> 属性设置为 `true`，并且在绑定引擎设置源时引发异常，则绑定引擎将检查是否存在 <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>。 可以选择使用 <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> 回叫来提供用于处理异常的自定义处理程序。 如果未在 <xref:System.Windows.Data.Binding> 上指定 <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>，则绑定引擎会创建具有异常的 <xref:System.Windows.Controls.ValidationError> 并将其添加到绑定元素的 <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> 集合中。

## <a name="debugging-mechanism"></a>调试机制

可以在与绑定相关的对象上设置附加属性 <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType>，以接收有关特定绑定状态的信息。

## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [绑定到 LINQ 查询的结果](../../framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)
- [数据绑定](../../framework/wpf/advanced/optimizing-performance-data-binding.md)
- [数据绑定演示][data-binding-demo]
- [操作指南文章](../../framework/wpf/data/data-binding-how-to-topics.md)
- [绑定到 ADO.NET 数据源](../../framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)

[data-binding-demo]: https://github.com/microsoft/WPF-Samples/tree/master/Sample%20Applications/DataBindingDemo "数据绑定演示应用"
