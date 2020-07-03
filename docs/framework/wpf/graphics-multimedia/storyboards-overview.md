---
title: 演示图板概述
desription: Organize and apply animations in storyboards. Use property-targeting syntax and combine timelines in Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboard syntax [WPF]
- syntax [WPF], Storyboard
- timelines [WPF]
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
ms.openlocfilehash: 50f45953da3801bf73016c09b78a6a1b54878bc0
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853646"
---
# <a name="storyboards-overview"></a>演示图板概述

本主题演示如何使用 <xref:System.Windows.Media.Animation.Storyboard> 对象来组织和应用动画。 它介绍了如何以交互方式操作 <xref:System.Windows.Media.Animation.Storyboard> 对象并描述间接属性目标语法。

## <a name="prerequisites"></a>必备条件

若要了解本主题，应熟悉不同的动画类型及其基本功能。 有关动画的简介，请参阅[动画概述](animation-overview.md)。 还应了解如何使用附加属性。 有关附加属性的详细信息，请参阅[附加属性概述](../advanced/attached-properties-overview.md)。

<a name="whatisatimeline"></a>

## <a name="what-is-a-storyboard"></a>什么是情节提要？

动画并非唯一有用的时间线类型。 还提供了其他时间线类来帮助组织时间线集，并将时间线应用于属性。 容器时间线派生自 <xref:System.Windows.Media.Animation.TimelineGroup> 类，并包括 <xref:System.Windows.Media.Animation.ParallelTimeline> 和 <xref:System.Windows.Media.Animation.Storyboard> 。

<xref:System.Windows.Media.Animation.Storyboard>是一种为其所包含的时间线提供目标信息的容器时间线。 情节提要可以包含任何类型 <xref:System.Windows.Media.Animation.Timeline> ，包括其他容器时间线和动画。 <xref:System.Windows.Media.Animation.Storyboard>使用对象，您可以将影响各种对象和属性的时间线合并为单个时间线树，以便于组织和控制复杂的计时行为。 例如，假设需要一个执行以下三个操作的按钮。

- 当用户选择该按钮时，按钮增大并更改颜色。

- 当用户单击该按钮时，按钮缩小并恢复其原始大小。

- 当该按钮变为禁用状态时，按钮缩小且不透明度缩减到 50%。

在此情况下，有多组动画适用于同一对象，并且需要根据按钮的状态在不同的时间播放它们。 <xref:System.Windows.Media.Animation.Storyboard>使用对象可以组织动画并将它们按组应用到一个或多个对象。

<a name="wherecanyouuseastoryboard"></a>

## <a name="where-can-you-use-a-storyboard"></a>何处可以使用情节提要？

<xref:System.Windows.Media.Animation.Storyboard>可用于对动画处理类的依赖属性进行动画处理（有关如何动画处理类的详细信息，请参阅[动画概述](animation-overview.md)）。 但是，因为情节提要是一个框架级别功能，所以该对象必须属于 <xref:System.Windows.NameScope> <xref:System.Windows.FrameworkElement> 或的 <xref:System.Windows.FrameworkContentElement> 。

例如，你可以使用 <xref:System.Windows.Media.Animation.Storyboard> 来执行以下操作：

- 对 <xref:System.Windows.Media.SolidColorBrush> 绘制按钮背景（一种类型）的（非框架元素）进行动画处理 <xref:System.Windows.FrameworkElement> ，

- 对 <xref:System.Windows.Media.SolidColorBrush> 使用（）绘制的（非 <xref:System.Windows.Media.GeometryDrawing> 框架元素）填充的（非框架元素）进行动画处理 <xref:System.Windows.Controls.Image> <xref:System.Windows.FrameworkElement> 。

- 在代码中， <xref:System.Windows.Media.SolidColorBrush> 如果将包含的类声明为，则对它的声明进行动画处理 <xref:System.Windows.FrameworkElement> <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.FrameworkElement> 。

但是，您不能使用 <xref:System.Windows.Media.Animation.Storyboard> 对未向或注册其名称的进行动画处理，也不能使用来 <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> 设置或的属性 <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> 。

<a name="applyanimationswithastoryboard"></a>

## <a name="how-to-apply-animations-with-a-storyboard"></a>如何使用情节提要应用动画

若要使用 <xref:System.Windows.Media.Animation.Storyboard> 来组织和应用动画，请将动画添加为的子时间线 <xref:System.Windows.Media.Animation.Storyboard> 。 <xref:System.Windows.Media.Animation.Storyboard>类提供 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> 属性和附加属性。 可以在动画上设置这些属性以指定其目标对象和属性。

若要将动画应用于其目标，请 <xref:System.Windows.Media.Animation.Storyboard> 使用触发器操作或方法开始。 在中 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，可以使用 <xref:System.Windows.Media.Animation.BeginStoryboard> 具有 <xref:System.Windows.EventTrigger> 、或的对象 <xref:System.Windows.Trigger> <xref:System.Windows.DataTrigger> 。 在代码中，还可以使用 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法。

下表显示支持每个开始技术的不同位置 <xref:System.Windows.Media.Animation.Storyboard> ：每个实例、样式、控件模板和数据模板。 “基于实例”是指直接将动画或情节提要应用于对象实例（而不是在样式、控件模板或数据模板中应用）的技术。

|情节提要开始时使用…|基于实例|Style|控件模板|数据模板|示例|
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|
|<xref:System.Windows.Media.Animation.BeginStoryboard>和<xref:System.Windows.EventTrigger>|是|是|是|是|[使用情节提要对属性进行动画处理](how-to-animate-a-property-by-using-a-storyboard.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard>和属性<xref:System.Windows.Trigger>|否|是|是|是|[在属性值更改时触发动画](how-to-trigger-an-animation-when-a-property-value-changes.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard>和<xref:System.Windows.DataTrigger>|否|是|是|是|[如何：在数据更改时触发动画](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法|是|No|否|否|[使用情节提要对属性进行动画处理](how-to-animate-a-property-by-using-a-storyboard.md)|

下面的示例使用 <xref:System.Windows.Media.Animation.Storyboard> 对某个元素的 <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> 和 <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> 用于绘制该 <xref:System.Windows.Shapes.Rectangle> 的的的。

[!code-xaml[storyboards_ovw_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]

[!code-csharp[storyboards_ovw_snip#100](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]

以下部分 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> 更详细地介绍了和附加属性。

<a name="targetingelementsandfreezables"></a>

## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>以框架元素、框架内容元素和 Freezable 元素为目标

上一节提到过，对于要查找其目标的动画，必须知道目标的名称和要进行动画处理的属性。 指定要进行动画处理的属性是一种直接的方式：只需 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> 用要进行动画处理的属性的名称进行设置。  通过设置动画的属性，指定要为其设置动画的属性的对象的名称 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> 。

要使 <xref:System.Windows.Setter.TargetName%2A> 属性正常工作，目标对象必须具有名称。 为 <xref:System.Windows.FrameworkElement> 或在中分配名称与 <xref:System.Windows.FrameworkContentElement> 为 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 对象分配名称不同 <xref:System.Windows.Freezable> 。

框架元素是从类继承的类 <xref:System.Windows.FrameworkElement> 。 框架元素的示例包括 <xref:System.Windows.Window> 、 <xref:System.Windows.Controls.DockPanel> 、 <xref:System.Windows.Controls.Button> 和 <xref:System.Windows.Shapes.Rectangle> 。 实质上，所有窗口、面板和控件都是元素。 框架内容元素是从类继承的类 <xref:System.Windows.FrameworkContentElement> 。 框架内容元素的示例包括 <xref:System.Windows.Documents.FlowDocument> 和 <xref:System.Windows.Documents.Paragraph> 。 如果不确定某个类型是框架元素还是框架内容元素，请查看它是否具有 Name 属性。 如果具有 Name 属性，则可能是框架元素或框架内容元素。 若要进一步确定，请检查其类型页面的“继承性分层”部分。

若要在中启用框架元素或框架内容元素的目标 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，请设置其 <xref:System.Windows.FrameworkElement.Name%2A> 属性。 在代码中，还需要使用 <xref:System.Windows.NameScope.RegisterName%2A> 方法来向已为其创建的元素注册元素的名称 <xref:System.Windows.NameScope> 。

下面的示例摘自前面的示例，它为指定了名称 `MyRectangle` a <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.FrameworkElement> 。

[!code-xaml[storyboards_ovw_snip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]

[!code-csharp[storyboards_ovw_snip#102](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]

在该元素具有名称后，可以对其属性进行动画处理。

[!code-xaml[storyboards_ovw_snip_XAML#5](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]

[!code-csharp[storyboards_ovw_snip#105](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]

<xref:System.Windows.Freezable>类型是从类继承的类 <xref:System.Windows.Freezable> 。 的示例 <xref:System.Windows.Freezable> 包括 <xref:System.Windows.Media.SolidColorBrush> 、 <xref:System.Windows.Media.RotateTransform> 和 <xref:System.Windows.Media.GradientStop> 。

若要 <xref:System.Windows.Freezable> 在中启用动画的目标 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，可以使用[x：Name 指令](../../../desktop-wpf/xaml-services/xname-directive.md)为其分配名称。 在代码中，使用 <xref:System.Windows.NameScope.RegisterName%2A> 方法将其名称注册到已为其创建的元素 <xref:System.Windows.NameScope> 。

下面的示例将一个名称分配给 <xref:System.Windows.Freezable> 对象。

[!code-xaml[storyboards_ovw_snip_XAML#3](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]

[!code-csharp[storyboards_ovw_snip#103](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]

然后动画便可以该对象为目标。

[!code-xaml[storyboards_ovw_snip_XAML#7](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]

[!code-csharp[storyboards_ovw_snip#107](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]

<xref:System.Windows.Media.Animation.Storyboard>对象使用名称范围来解析 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 属性。 有关 WPF 名称范围的详细信息，请参阅 [WPF XAML 名称范围](../advanced/wpf-xaml-namescopes.md)。 如果 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 省略该属性，则动画将以定义它的元素为目标; 对于样式为样式的元素。

有时，不能将名称分配给 <xref:System.Windows.Freezable> 对象。 例如，如果 <xref:System.Windows.Freezable> 声明为资源或用于设置样式中的属性值，则不能为其指定名称。 由于该对象没有名称，因此不能直接以它为目标，但可以间接以它为目标。 下面几节描述如何使用间接目标。

<a name="pathsyntaxforchangeable"></a>

## <a name="indirect-targeting"></a>间接目标

有时 <xref:System.Windows.Freezable> 动画无法直接定位，例如，当 <xref:System.Windows.Freezable> 声明为资源或用于设置样式中的属性值时。 在这些情况下，即使您不能直接将其作为目标，您仍然可以对对象进行动画处理 <xref:System.Windows.Freezable> 。 不是将属性设置为的 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 名称，而是 <xref:System.Windows.Freezable> 为其提供 "所属" 的元素的名称 <xref:System.Windows.Freezable> 。 例如， <xref:System.Windows.Media.SolidColorBrush> 用于设置 <xref:System.Windows.Shapes.Shape.Fill%2A> 矩形元素的属于该矩形的。 若要对画笔进行动画处理，请设置动画的 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> 属性链，该链以 <xref:System.Windows.Freezable> 用于设置的属性和结束于要 <xref:System.Windows.Freezable> 进行动画处理的属性结束。

[!code-xaml[storyboards_ovw_snip_XAML#33](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]

[!code-csharp[storyboards_ovw_snip#134](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]

请注意，如果 <xref:System.Windows.Freezable> 冻结，将进行克隆，并对该克隆进行动画处理。 发生这种情况时，原始对象的 <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> 属性将继续返回 `false` ，因为原始对象并未进行动画处理。 有关克隆的详细信息，请参阅 "[冻结对象概述](../advanced/freezable-objects-overview.md)"。

另请注意，当使用间接属性目标时，可能会以不存在的对象为目标。 例如，你可能会假设使用 <xref:System.Windows.Controls.Control.Background%2A> 设置了特定按钮的， <xref:System.Windows.Media.SolidColorBrush> 并尝试对其颜色进行动画处理（事实上， <xref:System.Windows.Media.LinearGradientBrush> 使用来设置按钮的背景）。 在这些情况下，不会引发异常;由于不 <xref:System.Windows.Media.LinearGradientBrush> 会对属性的更改做出反应，动画无法获得可见效果 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 。

下面几节详细介绍间接属性目标语法。

<a name="xamlsyntaxchangeableproperty"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>在 XAML 中间接以 Freezable 的属性为目标

若要以可冻结的属性为目标 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，请使用以下语法。

| |
|-|
|*ElementPropertyName* `.` *FreezablePropertyName*|

位置

- *ElementPropertyName*是用于设置的的属性 <xref:System.Windows.FrameworkElement> <xref:System.Windows.Freezable> ，以及

- *FreezablePropertyName*是 <xref:System.Windows.Freezable> 要进行动画处理的的属性。

下面的代码演示如何对 <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> 用于设置矩形元素的的的进行动画处理 <xref:System.Windows.Shapes.Shape.Fill%2A> 。

[!code-xaml[storyboards_ovw_snip_XAML#32](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]

有时，需要以集合或数组中包含的 Freezable 为目标。

若要以集合中包含的 Freezable 为目标，可以使用以下路径语法。

| |
|-|
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|

其中， *CollectionIndex*是对象在其数组或集合中的索引。

例如，假设某个矩形有一个 <xref:System.Windows.Media.TransformGroup> 应用于其属性的资源 <xref:System.Windows.UIElement.RenderTransform%2A> ，并且您想要对它所包含的其中一个转换进行动画处理。

[!code-xaml[storyboards_ovw_snip_XAML#34](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]

下面的代码演示如何对 <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform> 上一个示例中所示的的属性进行动画处理。

[!code-xaml[storyboards_ovw_snip_XAML#35](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]

<a name="targetingpropertyofchangeableincode"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>在代码中间接以 Freezable 的属性为目标

在代码中，您将创建一个 <xref:System.Windows.PropertyPath> 对象。 当您创建时 <xref:System.Windows.PropertyPath> ，可以指定 <xref:System.Windows.PropertyPath.Path%2A> 和 <xref:System.Windows.PropertyPath.PathParameters%2A> 。

若要创建 <xref:System.Windows.PropertyPath.PathParameters%2A> ，请创建一个类型为的数组， <xref:System.Windows.DependencyProperty> 其中包含依赖项属性标识符字段的列表。 第一个标识符字段用于的属性 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> <xref:System.Windows.Freezable> 用于设置的。 下一个标识符字段表示目标为的属性 <xref:System.Windows.Freezable> 。 将其视为一系列将连接到对象的属性 <xref:System.Windows.Freezable> <xref:System.Windows.FrameworkElement> 。

下面是依赖属性链的一个示例，它 <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> 以用于设置矩形元素的的为目标 <xref:System.Windows.Shapes.Shape.Fill%2A> 。

[!code-csharp[storyboards_ovw_snip#135](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]

还需要指定 <xref:System.Windows.PropertyPath.Path%2A> 。 <xref:System.Windows.PropertyPath.Path%2A> <xref:System.String> ，它指示 <xref:System.Windows.PropertyPath.Path%2A> 如何解释其 <xref:System.Windows.PropertyPath.PathParameters%2A> 。 它使用以下语法。

| |
|-|
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|

位置

- *OwnerPropertyArrayIndex*是数组的索引，该 <xref:System.Windows.DependencyProperty> 数组包含 <xref:System.Windows.FrameworkElement> 用于设置的对象属性的标识符 <xref:System.Windows.Freezable> ，以及

- *FreezablePropertyArrayIndex*是 <xref:System.Windows.DependencyProperty> 包含目标属性的标识符的数组的索引。

下面的示例演示 <xref:System.Windows.PropertyPath.Path%2A> <xref:System.Windows.PropertyPath.PathParameters%2A> 前面的示例中定义的。

[!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]

下面的示例合并了前面的示例中的代码，以对 <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> 用于设置 <xref:System.Windows.Shapes.Shape.Fill%2A> 矩形元素的的的进行动画处理。

[!code-csharp[storyboards_ovw_snip#137](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]

有时，需要以集合或数组中包含的 Freezable 为目标。 例如，假设某个矩形有一个 <xref:System.Windows.Media.TransformGroup> 应用于其属性的资源 <xref:System.Windows.UIElement.RenderTransform%2A> ，并且您想要对它所包含的其中一个转换进行动画处理。

[!code-xaml[storyboards_ovw_snip#142](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]

若要以 <xref:System.Windows.Freezable> 集合中包含的为目标，请使用以下路径语法。

| |
|-|
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|

其中， *CollectionIndex*是对象在其数组或集合中的索引。

若要面向的 <xref:System.Windows.Media.RotateTransform.Angle%2A> 属性 <xref:System.Windows.Media.RotateTransform> （中的第二个转换）， <xref:System.Windows.Media.TransformGroup> 请使用以下 <xref:System.Windows.PropertyPath.Path%2A> 和 <xref:System.Windows.PropertyPath.PathParameters%2A> 。

[!code-csharp[storyboards_ovw_snip#139](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]

下面的示例演示了用于对中包含的的进行动画处理的完整代码 <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.TransformGroup> 。

[!code-csharp[storyboards_ovw_snip#138](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]

### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>间接以 Freezable 为目标并将其作为起点

前面的部分介绍了如何 <xref:System.Windows.Freezable> 通过从 <xref:System.Windows.FrameworkElement> 或开始 <xref:System.Windows.FrameworkContentElement> 向子属性创建属性链来间接地定位 <xref:System.Windows.Freezable> 。 你还可以使用 <xref:System.Windows.Freezable> 作为起点，并间接定位其 <xref:System.Windows.Freezable> 子属性之一。 当使用作为间接目标的起点时，还可以使用另一种限制 <xref:System.Windows.Freezable> ：起始位置 <xref:System.Windows.Freezable> 以及 <xref:System.Windows.Freezable> 它与间接目标的子属性之间的每一个都不能冻结。

<a name="controllable_storyboards"></a>

## <a name="interactively-controlling-a-storyboard-in-xaml"></a>在 XAML 中以交互方式控制情节提要

若要在中启动情节提要 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ，请使用 <xref:System.Windows.Media.Animation.BeginStoryboard> 触发器操作。 <xref:System.Windows.Media.Animation.BeginStoryboard>将动画分发到它们动画处理的对象和属性，并启动情节提要。 （有关此过程的详细信息，请参阅[动画和计时系统概述](animation-and-timing-system-overview.md)。）如果 <xref:System.Windows.Media.Animation.BeginStoryboard> 通过指定名称的属性来指定名称 <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> ，则会使其成为可控制的情节提要。 然后，可以在情节提要启动后以交互方式对它进行控制。 下面列出了可与事件触发器一起使用来控制情节提要的可控制情节提要操作。

- <xref:System.Windows.Media.Animation.PauseStoryboard>：暂停情节提要。

- <xref:System.Windows.Media.Animation.ResumeStoryboard>：恢复暂停的情节提要。

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>：更改情节提要的速度。

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>：使情节提要前进到其填充期的末尾（如果有一个）。

- <xref:System.Windows.Media.Animation.StopStoryboard>：停止情节提要。

- <xref:System.Windows.Media.Animation.RemoveStoryboard>：删除情节提要。

在下面的示例中，使用可控制的情节提要操作来以交互方式控制情节提要。

[!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]

<a name="controllable_storyboards_procedural"></a>

## <a name="interactively-controlling-a-storyboard-by-using-code"></a>使用代码以交互方式控制情节提要

前面的示例已演示了如何使用触发器操作进行动画处理。 在代码中，你还可以使用类的交互式方法控制情节提要 <xref:System.Windows.Media.Animation.Storyboard> 。 <xref:System.Windows.Media.Animation.Storyboard>若要在代码中使成为交互，必须使用情节提要的方法的适当重载， <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 并指定 `true` 以使其可控制。 有关详细信息，请参阅<xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29>页。

以下列表显示了可用于在启动后操作的方法 <xref:System.Windows.Media.Animation.Storyboard> ：

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>

使用这些方法的优点是不需要创建 <xref:System.Windows.Trigger> 或 <xref:System.Windows.TriggerAction> 对象; 只需引用要操作的可控制对象即可 <xref:System.Windows.Media.Animation.Storyboard> 。

> [!NOTE]
> 对执行的所有交互操作 <xref:System.Windows.Media.Animation.Clock> ，因此，也会在 <xref:System.Windows.Media.Animation.Storyboard> 计时引擎的下一计时周期发生，这将在下一次呈现之前发生。 例如，如果使用 <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> 方法跳转到动画中的其他点，则属性值不会立即更改，而是在计时引擎的下一计时周期更改。

下面的示例演示如何使用类的交互式方法来应用和控制动画 <xref:System.Windows.Media.Animation.Storyboard> 。

[!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
[!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]

<a name="usingstoryboardsinstyles"></a>

## <a name="animate-in-a-style"></a>在样式中进行动画处理

可以使用 <xref:System.Windows.Media.Animation.Storyboard> 对象定义中的动画 <xref:System.Windows.Style> 。 使用在中的进行动画处理 <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Style> 类似于在 <xref:System.Windows.Media.Animation.Storyboard> 其他地方使用，具有以下三个例外：

- 不指定 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ; <xref:System.Windows.Media.Animation.Storyboard> 始终以应用到的元素为目标 <xref:System.Windows.Style> 。 若要以对象为目标 <xref:System.Windows.Freezable> ，必须使用间接目标。 有关间接目标的详细信息，请参阅[间接目标](#pathsyntaxforchangeable)部分。

- 不能 <xref:System.Windows.EventTrigger.SourceName%2A> 为 <xref:System.Windows.EventTrigger> 或指定 <xref:System.Windows.Trigger> 。

- 不能使用动态资源引用或数据绑定表达式设置 <xref:System.Windows.Media.Animation.Storyboard> 或动画属性值。 这是因为内的所有内容都 <xref:System.Windows.Style> 必须是线程安全的，并且计时系统必须具有 <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> 对象，才能使它们线程安全。 <xref:System.Windows.Media.Animation.Storyboard>如果无法冻结，则为; 否则它的子时间线包含动态资源引用或数据绑定表达式。 有关冻结和其他功能的详细信息 <xref:System.Windows.Freezable> ，请参阅 "[冻结对象概述](../advanced/freezable-objects-overview.md)"。

- 在中 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，不能为 <xref:System.Windows.Media.Animation.Storyboard> 或动画事件声明事件处理程序。

有关演示如何在样式中定义情节提要的示例，请参阅在[样式示例中进行动画处理](how-to-animate-in-a-style.md)。

<a name="defineAStoryboardInAControlTemplateSection"></a>

## <a name="animate-in-a-controltemplate"></a>在 ControlTemplate 中进行动画处理

可以使用 <xref:System.Windows.Media.Animation.Storyboard> 对象定义中的动画 <xref:System.Windows.Controls.ControlTemplate> 。 使用在中的进行动画处理 <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Controls.ControlTemplate> 类似于在 <xref:System.Windows.Media.Animation.Storyboard> 其他位置使用，但有以下两个例外：

- <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>只能引用的子对象 <xref:System.Windows.Controls.ControlTemplate> 。 如果 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> 未指定，动画将以应用到的元素为目标 <xref:System.Windows.Controls.ControlTemplate> 。

- <xref:System.Windows.EventTrigger.SourceName%2A> <xref:System.Windows.EventTrigger> 或的 <xref:System.Windows.Trigger> 只能引用的子对象 <xref:System.Windows.Controls.ControlTemplate> 。

- 不能使用动态资源引用或数据绑定表达式设置 <xref:System.Windows.Media.Animation.Storyboard> 或动画属性值。 这是因为内的所有内容都 <xref:System.Windows.Controls.ControlTemplate> 必须是线程安全的，并且计时系统必须具有 <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> 对象，才能使它们线程安全。 <xref:System.Windows.Media.Animation.Storyboard>如果无法冻结，则为; 否则它的子时间线包含动态资源引用或数据绑定表达式。 有关冻结和其他功能的详细信息 <xref:System.Windows.Freezable> ，请参阅 "[冻结对象概述](../advanced/freezable-objects-overview.md)"。

- 在中 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，不能为 <xref:System.Windows.Media.Animation.Storyboard> 或动画事件声明事件处理程序。

有关演示如何在中定义情节提要的示例 <xref:System.Windows.Controls.ControlTemplate> ，请参阅[system.windows.controls.controltemplate> 示例中的动画](how-to-animate-in-a-controltemplate.md)。

<a name="animateWhenAPropertyValueChanges"></a>

## <a name="animate-when-a-property-value-changes"></a>在属性值更改时进行动画处理

在样式和控件模板中，当属性更改时，可以使用 Trigger 对象来启动情节提要。 有关示例，请参阅在 System.windows.controls.controltemplate> 中[更改属性值并对](how-to-trigger-an-animation-when-a-property-value-changes.md)其[进行动画处理](how-to-animate-in-a-controltemplate.md)时触发动画。

属性对象应用的动画的 <xref:System.Windows.Trigger> 行为方式比 <xref:System.Windows.EventTrigger> 使用方法启动动画或动画更复杂 <xref:System.Windows.Media.Animation.Storyboard> 。  它们使用其他对象定义的动画 "切换" <xref:System.Windows.Trigger> ，但使用 <xref:System.Windows.EventTrigger> 和方法触发的动画进行组合。

## <a name="see-also"></a>另请参阅

- [动画概述](animation-overview.md)
- [属性动画技术概述](property-animation-techniques-overview.md)
- [Freezable 对象概述](../advanced/freezable-objects-overview.md)
