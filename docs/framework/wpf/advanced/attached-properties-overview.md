---
title: 附加属性概述
description: 了解 Windows Presentation Foundation 中的附加属性，这些属性是可在任何对象上设置的全局属性。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
ms.openlocfilehash: 993f65024fcfc4f39a408c81af43b798360e6cf6
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168380"
---
# <a name="attached-properties-overview"></a>附加属性概述

附加属性是由 XAML 定义的概念。 附加属性旨在用作可在任何对象上设置的一类全局属性。 在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中，附加属性通常定义为没有常规属性“包装器”的依赖性属性的专用形式。

## <a name="prerequisites"></a>先决条件 <a name="prerequisites"></a>

本文假设你从类的现有依赖属性的使用者角度了解依赖属性 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ，并且已阅读[依赖属性概述](dependency-properties-overview.md)。 若要遵循本文中的示例，还应了解 XAML 并了解如何编写 WPF 应用程序。

## <a name="why-use-attached-properties"></a>为什么使用附加属性<a name="attached_properties_usage"></a>

附加属性的一个用途是允许不同的子元素为父元素中定义的属性指定唯一的值。 此方案的一个具体应用是，让子元素通知父元素它们在 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中的呈现方式。 一个示例是 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 属性。 该 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 属性是作为附加属性创建的，因为它设计为在中包含的元素上设置，而不是在自身中包含的元素上设置 <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.DockPanel> 。 <xref:System.Windows.Controls.DockPanel>类定义 <xref:System.Windows.DependencyProperty> 名为的静态字段 <xref:System.Windows.Controls.DockPanel.DockProperty> ，然后提供 <xref:System.Windows.Controls.DockPanel.GetDock%2A> 和 <xref:System.Windows.Controls.DockPanel.SetDock%2A> 方法作为附加属性的公共访问器。

## <a name="attached-properties-in-xaml"></a>XAML 中的附加属性<a name="attached_properties_xaml"></a>

在 XAML 中，可以使用语法 AttachedPropertyProvider**.PropertyName** 来设置附加属性

下面是如何 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 在 XAML 中设置的示例：

[!code-xaml[PropertiesOvwSupport#APBasicUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]

用法在某种程度上类似于静态属性;始终引用 <xref:System.Windows.Controls.DockPanel> 拥有和注册附加属性的类型，而不是引用任何由 name 指定的实例。

此外，由于 XAML 中的附加属性是在标记中设置的属性，因此，只有设置操作具有相关性。 尽管存在一些用于比较值的间接机制（如在样式中触发），但无法直接在 XAML 中直接获取属性（有关详细信息，请参阅[样式设置和模板化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)）。

### <a name="attached-property-implementation-in-wpf"></a>WPF 中的附加属性实现

在中 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ，WPF 类型上大多数与 UI 相关的附加属性都作为依赖属性实现。 附加属性是 XAML 概念，而依赖属性是 WPF 概念。 因为 WPF 附加属性是依赖属性，所以它们支持依赖属性概念（如属性元数据）和来自该属性元数据的默认值。

## <a name="how-attached-properties-are-used-by-the-owning-type"></a>所属类型使用附加属性的方式<a name="howused"></a>

尽管可以在任何对象上设置附加属性，但这并不自动意味着设置该属性会产生实际的结果，或者该值会被其他对象使用。 通常，附加属性是为了使来自各种可能的类层次结构或逻辑关系的对象都可以向用于定义附加属性的类型报告公用信息。 定义附加属性的类型通常采用以下模型之一：

- 设计定义附加属性的类型，以便它可以是将为附加属性设置值的元素的父元素。 随后，该类型将在内部逻辑中对照某些对象树结构循环访问其子对象，获取值，并以某种方式作用于这些值。

- 定义附加属性的类型将用作各种可能的父元素和内容模型的子元素。

- 定义附加属性的类型表示一项服务。 其他类型为该附加属性设置值。 然后，当在服务的上下文中计算设置该属性的元素时，将通过服务类的内部逻辑获取附加属性的值。

### <a name="an-example-of-a-parent-defined-attached-property"></a>父级定义的附加属性示例

WPF 定义附加属性的最典型方案是：当父元素支持子元素集合时，还实现了一种行为，其中为每个子元素单独报告了行为的细节。

<xref:System.Windows.Controls.DockPanel>定义 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 附加属性，并将 <xref:System.Windows.Controls.DockPanel> 类级代码作为其呈现逻辑的一部分（具体而言， <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> 和 <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A> ）。 <xref:System.Windows.Controls.DockPanel>实例将始终检查其任意直接子元素是否已设置的值 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 。 如果已设置，这些值将变为应用于该特定子元素的呈现逻辑的输入。 嵌套 <xref:System.Windows.Controls.DockPanel> 实例分别处理它们自己的直接子元素集合，但该行为是特定于实现的，其 <xref:System.Windows.Controls.DockPanel> 处理值的方式 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 。 理论上，可以有影响直接父级之外的元素的附加属性。 如果 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 在没有父元素的元素上设置附加属性 <xref:System.Windows.Controls.DockPanel> ，则不会引发错误或异常。 这只是表示已设置全局属性值，但没有 <xref:System.Windows.Controls.DockPanel> 可使用该信息的当前父级。

## <a name="attached-properties-in-code"></a>代码中的附加属性<a name="attached_properties_code"></a>

WPF 中的附加属性没有用于轻松获取/设置访问的典型 CLR "包装器" 方法。 这是因为，附加属性不一定是设置了属性的实例的 CLR 命名空间的一部分。 但是，分析 XAML 时，XAML 处理器必须能够设置这些值。 若要支持有效的附加属性用法，附加属性的所有者类型必须以**Get_PropertyName_** 和**Set_PropertyName_** 形式实现专用访问器方法。 这些专用访问器方法对在代码中设置附加属性也很有帮助。 从代码的角度来看，附加属性类似于具有方法访问器而不是属性访问器的支持字段，且支持字段可在任何对象上存在，无需专门定义。

下面的示例演示如何在代码中设置附加属性。 在此示例中， `myCheckBox` 是类的实例 <xref:System.Windows.Controls.CheckBox> 。

[!code-csharp[PropertiesOvwSupport#APCode](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
[!code-vb[PropertiesOvwSupport#APCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]

类似于 XAML 情况，如果 `myCheckBox` 尚未添加为第四行代码的的子元素 `myDockPanel` ，则第五行代码不会引发异常，但属性值不会与父级交互， <xref:System.Windows.Controls.DockPanel> 因此不会执行任何操作。 只有 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 在子元素上设置的值与父元素的存在结合使用 <xref:System.Windows.Controls.DockPanel> 将导致呈现的应用程序中出现有效的行为。 （在这种情况下，可以设置附加属性，然后附加到树。 或者，可以先附加到该树中，然后设置附加属性。 这两种操作顺序结果都相同。）

## <a name="attached-property-metadata"></a>附加属性元数据<a name="attached_properties_metadata"></a>

注册属性时，将 <xref:System.Windows.FrameworkPropertyMetadata> 设置为指定属性的特性，例如属性是否影响呈现、度量等。 附加属性的元数据通常与依赖属性上的元数据基本上都相同。 如果在附加属性元数据替代中指定默认值，该值将成为替代类实例上显式附加属性的默认值。 具体而言，当某些进程通过该属性的 `Get` 方法访问器请求附加属性值，并指定在其中指定元数据的类的示例时，将报告默认值，而不会设置该附加属性的值。

如果希望对属性启用属性值继承，应使用附加属性，而不是非附加的依赖属性。 有关详细信息，请参阅[属性值继承](property-value-inheritance.md)。

## <a name="custom-attached-properties"></a>自定义附加属性<a name="custom"></a>

### <a name="when-to-create-an-attached-property"></a>何时创建附加属性<a name="create_attached_properties"></a>

当需要有一个可用于定义类之外的其他类的属性设置机制时，建议创建附加属性。 对于这一情况，最常见的方案是布局。 现有布局属性的示例包括 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 、 <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> 和 <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType> 。 这里启用的方案是，作为布局控制元素的子元素存在的元素能够分别向其布局父级元素表达布局要求，其中每个元素都设置一个被父级定义为附加属性的属性值。

使用附加属性的另一种情况是，你的类表示一种服务，且你希望类能够以更透明的方式继承该服务。

但另一种情况是接收 Visual Studio WPF 设计器支持，如 "**属性**" 窗口编辑。 有关详细信息，请参阅[控件创作概述](../controls/control-authoring-overview.md)。

如前文所述，如果想要使用属性值继承，你应该注册为附加属性。

### <a name="how-to-create-an-attached-property"></a>如何创建附加属性<a name="how_do_i_create_attached_properties"></a>

如果你的类将严格定义附加属性以用于其他类型，则该类不必派生自 <xref:System.Windows.DependencyObject> 。 但 <xref:System.Windows.DependencyObject> 如果遵循的是总体 WPF 模型，而此模型的整体 WPF 模型也是依赖属性，则需要从派生。

通过声明类型的字段，将附加属性定义为依赖属性 `public static readonly` <xref:System.Windows.DependencyProperty> 。 使用方法的返回值定义此字段 <xref:System.Windows.DependencyProperty.RegisterAttached%2A> 。 字段名称必须与附加的属性名称相匹配，并附加字符串 `Property` ，才能遵循为标识字段命名的已建立 WPF 模式，而不是它们所表示的属性。 附加属性提供程序还必须提供静态**Get_PropertyName_** 和**Set_PropertyName_** 方法作为附加属性的访问器;如果无法执行此操作，则属性系统无法使用您的附加属性。

> [!NOTE]
> 如果省略附加属性的 get 访问器，则属性上的数据绑定将无法在设计工具（如 Visual Studio 和 Blend for Visual Studio）中工作。

#### <a name="the-get-accessor"></a>Get 访问器

**Get_PropertyName_** 访问器的签名必须是：

`public static object GetPropertyName(object target)`

- `target` 对象在实现中可以指定为更具体的类型。 例如，方法将 <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> 参数类型 <xref:System.Windows.UIElement> 设置为，因为附加属性只用于在实例上进行设置 <xref:System.Windows.UIElement> 。

- 返回值在实现中可以指定为更具体的类型。 例如，方法将 <xref:System.Windows.Controls.DockPanel.GetDock%2A> 其类型设置为 <xref:System.Windows.Controls.Dock> ，因为只能将值设置为该枚举。

#### <a name="the-set-accessor"></a>Set 访问器

**Set_PropertyName_** 访问器的签名必须是：

`public static void SetPropertyName(object target, object value)`

- `target` 对象在实现中可以指定为更具体的类型。 例如，方法将 <xref:System.Windows.Controls.DockPanel.SetDock%2A> 其类型设置为 <xref:System.Windows.UIElement> ，因为附加属性只用于在实例上进行设置 <xref:System.Windows.UIElement> 。

- `value` 对象在实现中可以指定为更具体的类型。 例如，方法将 <xref:System.Windows.Controls.DockPanel.SetDock%2A> 其类型设置为 <xref:System.Windows.Controls.Dock> ，因为只能将值设置为该枚举。 请记住，此方法的值是 XAML 加载器在标记中的附加属性用法中遇到附加属性时的输入。 该输入是在标记中指定为 XAML 属性值的值。 因此必须存在可用于你所使用的类型的类型转换、值序列化程序或标记扩展支持，以便可以从属性值（最终仅仅是一个字符串）创建相应的类型。

下面的示例演示了依赖属性注册（使用 <xref:System.Windows.DependencyProperty.RegisterAttached%2A> 方法）以及**Get_PropertyName_** 和**Set_PropertyName_** 访问器。 在此示例中，附加属性名称为 `IsBubbleSource`。 因此，访问器必须名为 `GetIsBubbleSource` 和 `SetIsBubbleSource`。

[!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
[!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]

#### <a name="attached-property-attributes"></a>附加属性特性

WPF 定义了多个 .NET 特性，旨在向反射进程提供附加属性的相关信息，并定义了反射的典型用户和属性信息（如设计器）。 由于附加属性的类型没有范围限制，因此设计者需要一种方法来避免用户查看全局列表时，看到使用 XAML 的特定技术实现中定义的所有附加属性。 WPF 为附加属性定义的 .NET 特性可用于确定应该在 "属性" 窗口中显示给定附加属性的情况的作用域。 你还可考虑对自己的自定义附加属性应用这些特性。 .NET 特性的目的和语法在相应的参考页上进行了说明：

- <xref:System.Windows.AttachedPropertyBrowsableAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>

- <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>

## <a name="learning-more-about-attached-properties"></a>了解有关附加属性的详细信息<a name="more"></a>

- 有关如何创建附加属性的详细信息，请参阅[注册附加属性](how-to-register-an-attached-property.md)。

- 有关依赖属性和附加属性的更多高级使用方案，请参阅[自定义依赖属性](custom-dependency-properties.md)。

- 还可将属性注册为附加属性和依赖属性，但仍需公开“包装器”实现。 在这种情况下，属性可在该元素上设置，也可通过 XAML 附加属性语法在任何元素上设置。 具有适用于标准和附加用法的适当方案的属性示例是 <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType> 。

## <a name="see-also"></a>另请参阅

- <xref:System.Windows.DependencyProperty>
- [依赖项属性概述](dependency-properties-overview.md)
- [自定义依赖项属性](custom-dependency-properties.md)
- [XAML 概述 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [注册附加属性](how-to-register-an-attached-property.md)
