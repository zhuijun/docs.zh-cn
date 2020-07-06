---
title: Windows Presentation Foundation 简介
description: 本文概述了与 .NET Core 相关的 Windows Presentation Foundation (WPF) 是什么以及它提供了哪些功能。
ms.date: 07/18/2019
ms.topic: overview
ms.openlocfilehash: 63b2e431b5ab5fd3875887b8b574a77aa12018a6
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2020
ms.locfileid: "85840264"
---
# <a name="what-is-windows-presentation-foundation"></a>Windows Presentation Foundation 简介

欢迎使用 Windows Presentation Foundation (WPF) 桌面指南，WPF 是一个可创建适用于 Windows 的桌面客户端应用程序的 UI 框架。 WPF 开发平台支持广泛的应用程序开发功能，包括应用程序模型、控件、图形和数据绑定。 WPF 使用 Extensible Application Markup Language (XAML) 为应用程序编程提供声明性模型。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

WPF 有两种实现：

01. 托管于 [GitHub](https://github.com/dotnet/wpf) 上的开放源代码实现。 此版本在 .NET Core 3.0 上运行。 适用于 XAML 的 WPF 视觉对象设计器最低要求 [Visual Studio 2019 版本 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+desktopguide)。

01. 受 Visual Studio 2019 和 Visual Studio 2017 支持的 .NET Framework 实现。

本桌面指南适用于 .NET Core 3.0 和 WPF。 如需详细了解使用 .NET Framework 的 WPF 的现有文档，请参阅 [Framework Windows Presentation Foundation](../../framework/wpf/index.md)。

## <a name="xaml"></a>XAML

XAML 是一种基于 XML 的声明语言，WPF 使用它来定义资源或 UI 元素等内容。 XAML 中定义的元素表示程序集中对象的实例化。 XAML 与大多数其他标记语言不同，后者在运行时进行解释，且与后备类型系统无直接关系。

以下示例演示如何创建 UI 中的按钮。 此示例旨在让你了解 XAML 如何表示对象，其中 `Button` 是类型，`Content` 是属性。

```xaml
<StackPanel>
    <Button Content="Click Me!" />
</StackPanel>
```

<!--For more information, see [XAML overview (WPF)](../../../framework/wpf/advanced/xaml-overview-wpf.md).-->

### <a name="xaml-extensions"></a>XAML 扩展

XAML 为标记扩展提供了语法。 标记扩展可用于以特性形式、属性元素形式或同时采用这两种形式来提供属性的值。

例如，上述 XAML 代码定义了一个按钮，其中可见内容设置为文本字符串 `"Click Me!"`，但该内容可以改由受支持的标记扩展进行设置。 标记扩展是通过一对大括号 (`{ }`) 来定义的。 然后，由紧跟在左大括号后面的字符串标记来标识标记扩展的类型。

```xaml
<StackPanel>
    <Button Content="{MarkupType}" />
</StackPanel>
```

WPF 为 XAML 提供了不同的标记扩展，例如用于数据绑定的 `{Binding}`。

有关详细信息，请参阅[标记扩展和 WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。

## <a name="property-system"></a>属性系统

WPF 提供一组服务，这些服务可用于扩展类型的[属性](../../standard/base-types/common-type-system.md#properties)的功能。 这些服务统称为 WPF 属性系统。 由 WPF 属性系统支持的属性称为依赖属性。

依赖属性通过提供支持属性的 <xref:System.Windows.DependencyProperty> 类型来扩展属性功能。 依赖项属性类型是使用专用字段支持属性的标准模式的替代实现。

### <a name="dependency-property"></a>依赖属性

在 WPF 中，依赖属性通常公开为标准 .NET [属性](../../standard/base-types/common-type-system.md#properties)。 在基本级别，可以直接与这些属性交互，而不必了解它们是以依赖属性的形式实现的。

依赖属性的用途在于提供一种方法来基于其他输入的值计算属性值。 这些其他输入可能包括系统属性（如主题和用户首选项）或者来自数据绑定和动画的实时属性。

可以实现依赖属性来提供验证、默认值以及监视对其他属性的更改的回调。 派生类还可以通过重写依赖属性元数据（而不是新建属性或重写现有属性）来更改现有属性的某些具体特征。

### <a name="dependency-object"></a>依赖对象

WPF 属性系统的另一个重要类型是 <xref:System.Windows.DependencyObject>。 此类型定义可以注册和拥有依赖属性的基类。 <xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A> 方法为依赖对象实例提供了依赖属性的支持实现。

以下示例演示的依赖对象定义一个名为 `ValueProperty` 的单一依赖属性标识符。 此依赖属性通过使用 `Value` .NET 属性创建而成。

```csharp
public class TextField: DependencyObject
{
    public static readonly DependencyProperty ValueProperty =
        DependencyProperty.Register("Value", typeof(string), typeof(TextField), new PropertyMetadata(""));

    public string Value
    {
        get { return (string)GetValue(ValueProperty); }
        set { SetValue(ValueProperty, value); }
    }
}
```

此依赖属性被定义为依赖对象类型的静态成员，例如上例中的 `TextField`。 此依赖属性必须通过依赖对象注册。

上例中的 `Value` 属性包装此依赖属性，从而提供了你可能较为熟悉的标准 .NET 属性模式。

<!--For more information, see [Dependency properties overview](../../../framework/wpf/advanced/dependency-properties-overview.md).-->

## <a name="events"></a>事件

WPF 提供了一个位于熟悉的 .NET 公共语言运行时 (CLR) 事件之上的事件系统。 这些 WPF 事件称为路由事件。

路由事件是一个 CLR 事件，它由 `RoutedEvent` 类的实例提供支持并向 WPF 事件系统注册。 从事件注册中获取的 `RoutedEvent` 实例通常保留为特定类的 `public static readonly` 字段成员，该类注册路由事件并因此“拥有”路由事件。 与同名 CLR 事件（有时称为“包装器”事件）的连接是通过替代 CLR 事件的 `add` 和 `remove` 实现来完成的。 路由事件的支持和连接机制在概念上与以下机制相似：[依赖属性](#dependency-property)是一个 CLR 属性，该属性由 `DependencyProperty` 类提供支持并向 WPF 属性系统注册。

路由事件系统的主要优点是，这类事件会上升到控制元素树上来查找处理程序。 例如，由于 WPF 具有丰富的内容模型，你可以将图像控件设置为按钮控件的内容。 在图像控件上单击鼠标时，你可能期望它使用鼠标事件，从而中断导致按钮调用 `Click` 事件的命中测试。 在传统 CLR 事件模型中，你需要通过向图像和按钮附加相同的处理程序来规避此限制。 但是，通过路由事件，在图像控件上调用的鼠标事件（例如选择它）会上升到父级按钮控件。

<!--For more information, including other types of event models, see [Events overview](../../../framework/wpf/advanced/routed-events-overview.md).-->

## <a name="data-binding"></a>数据绑定

WPF 数据绑定为应用程序呈现数据并与数据交互提供了一种简单且一致的方式。 元素能够以公共语言运行时 (CLR) 对象和 XML 的形式，绑定到不同类型数据源中的数据。 WPF 还提供了通过拖放操作传输数据的机制。

数据绑定是在应用程序 UI 和业务逻辑之间建立连接的过程。 如果绑定具有正确的设置，并且数据提供适当的通知，则在数据更改其值时，绑定到该数据的元素会自动反映更改。 数据绑定还意味着，如果元素中数据的外部表示形式发生更改，则基础数据会自动进行更新以反映更改。 例如，如果用户编辑 TextBox 元素中的值，则基础数据值会自动更新以反映该更改。

数据绑定可以通过 `{Binding}` 标记扩展以 XAML 配置。 以下示例演示绑定到数据对象的 `ButtonText` 属性。 如果绑定失败，则会使用 `Click Me!` 的值。

```xaml
<StackPanel>
    <Button Content="{Binding ButtonText, FallbackValue='Click Me!'}" />
</StackPanel>
```

有关详细信息，请参阅[数据绑定概述](../data/data-binding-overview.md)。

## <a name="ui-components"></a>UI 组件

WPF 提供许多几乎在所有 Windows 应用程序中都会使用的常见 UI 组件，如`Button`、`Label`、`TextBox`、`Menu` 和 `ListBox`。 以前，这些对象称为控件。 虽然 WPF SDK 继续使用术语“控件”泛指任何代表应用程序中可见对象的类，但请务必注意，类不必从 `Control` 类继承即可具有可见外观。 从 `Control` 类继承的类包含一个 `ControlTemplate`，它允许控件的使用方在无需创建新子类的情况下从根本上改变控件的外观。

## <a name="styles-and-templates"></a>样式和模板

WPF 样式设置和模板化是指一套功能（样式、模板、触发器和情节提要），可使应用程序、文档和 UI 设计者创建极具视觉表现力的应用程序，并为其产品创建标准化的特定外观。

WPF 样式模型的另一个功能是呈现内容和逻辑的分离，这意味着，设计人员可以使用 XAML 来处理应用程序的外观，而开发人员可以在其他位置处理编程逻辑。

此外，了解资源很重要，正是这些资源使样式和模板能够重复使用。

有关详细信息，请参阅[样式和模板](../fundamentals/styles-templates-overview.md)。

## <a name="resources"></a>资源

WPF 资源是可以在应用程序中的不同位置重复使用的对象。 资源示例包括样式、模板和颜色画笔。 可以采用代码和 XAML 格式定义和引用资源。

每个框架级别元素（<xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement>）都具有 `Resources` 属性，该属性是包含已定义资源的 <xref:System.Windows.ResourceDictionary> 类型。 由于所有元素都继承自框架级别元素，因此所有元素都可以定义资源。 但是，最常见的做法是在 XAML 文档的根元素上定义资源。

<!--For more information, see [XAML Resources](../../../framework/wpf/advanced/xaml-resources.md).-->

## <a name="next-steps"></a>后续步骤

- [创建 WPF 应用程序](https://docs.microsoft.com/visualstudio/get-started/csharp/tutorial-wpf?toc=/dotnet/desktop-wpf/toc.json&bc=/dotnet/breadcrumb/toc.json)。
- [探索与 .NET Framework 的差异](../migration/differences-from-net-framework.md)。
- [了解 XAML](../fundamentals/xaml.md)。
