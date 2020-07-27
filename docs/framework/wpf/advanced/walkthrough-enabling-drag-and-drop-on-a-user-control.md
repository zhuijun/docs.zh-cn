---
title: 演练：在用户控件上启用拖放功能
description: 了解如何创建可参与 Windows Presentation Foundation 中拖放数据传输的自定义用户控件。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: 12ad47035a09995094014841b083062743fc2574
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168278"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a>演练：在用户控件上启用拖放功能

本演练演示如何创建可在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中参与拖放数据传输的自定义用户控件。

在本演练中，您将创建一个 <xref:System.Windows.Controls.UserControl> 表示圆形形状的自定义 WPF。 你将在该控件上实现可通过拖放进行数据传输的功能。 例如，如果从一个圆形控件拖到另一个圆形控件，则会将填充颜色数据从源圆形复制到目标圆形。 如果从圆圈控件拖动到 <xref:System.Windows.Controls.TextBox> ，则填充颜色的字符串表示形式将复制到 <xref:System.Windows.Controls.TextBox> 。 你还将创建一个包含两个 panel 控件的小型应用程序和一个 <xref:System.Windows.Controls.TextBox> 用于测试拖放功能的。 你将编写可使面板处理放置的圆形数据的代码，这样就可以将圆形从一个面板的 Children 集合移动或复制到其他面板。

本演练阐释了以下任务：

- 创建自定义用户控件。

- 使用户控件成为拖动源。

- 使用户控件成为拖放目标。

- 使面板能够接收用户控件中放置的数据。

## <a name="prerequisites"></a>先决条件

若要完成本演练，必须具有 Visual Studio。

## <a name="create-the-application-project"></a>创建应用程序项目
 在本部分中，你将创建应用程序基础结构，其中包括一个具有两个面板和的主页 <xref:System.Windows.Controls.TextBox> 。

1. 在 Visual Basic 或 Visual C# 中创建名为 `DragDropExample` 的新 WPF 应用程序项目。 有关详细信息，请参阅[演练：我的第一个 WPF 桌面应用程序](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。

2. 打开 MainWindow.xaml。

3. 在开始标记和结束标记之间添加以下标记 <xref:System.Windows.Controls.Grid> 。

     此标记将创建用于测试应用程序的用户界面。

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a>向项目添加新的用户控件
 本节将介绍如何向项目添加新的用户控件。

1. 在“项目”菜单中，选择“添加用户控件”****。

2. 在 "**添加新项**" 对话框中，将 "名称" 更改为 `Circle.xaml` ，然后单击 "**添加**"。

     Circle.xaml 及其代码隐藏内容将添加到项目中。

3. 打开 Circle.xaml。

     此文件将包含用户控件的用户界面元素。

4. 将以下标记添加到根目录 <xref:System.Windows.Controls.Grid> ，以创建一个包含蓝色圆圈作为其 UI 的简单用户控件。

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. 打开 Circle.xaml.cs 或 Circle.xaml.vb。

6. 在 c # 中，将以下代码添加到无参数构造函数之后，以创建复制构造函数。 在 Visual Basic 中，添加以下代码以创建无参数构造函数和复制构造函数。

     若要允许复制用户控件，需在代码隐藏文件中添加复制构造函数方法。 在简化的圆形用户控件中，将只复制该用户控件的填充和大小。

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a>向主窗口添加用户控件

1. 打开 MainWindow.xaml。

2. 将以下 XAML 添加到开始 <xref:System.Windows.Window> 标记，以创建对当前应用程序的 XML 命名空间引用。

    ```xaml
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. 在第一 <xref:System.Windows.Controls.StackPanel> 种情况下，添加以下 XAML 以便在第一个面板中创建 Circle 用户控件的两个实例。

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     此面板的完整 XAML 如下所示。

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a>在用户控件中实现拖动源事件
 在本部分中，将重写 <xref:System.Windows.UIElement.OnMouseMove%2A> 方法并启动拖放操作。

 如果已启动拖动（按下鼠标按钮并移动鼠标），则会打包要传输到中的数据 <xref:System.Windows.DataObject> 。 在这种情况下，圆形控件将打包三个数据项：其填充颜色的字符串表示形式、其高度的双精度表示形式以及其自身的副本。

### <a name="to-initiate-a-drag-and-drop-operation"></a>启动拖放操作

1. 打开 Circle.xaml.cs 或 Circle.xaml.vb。

2. 添加以下 <xref:System.Windows.UIElement.OnMouseMove%2A> 替代，以便为事件提供类处理 <xref:System.Windows.UIElement.MouseMove> 。

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     此 <xref:System.Windows.UIElement.OnMouseMove%2A> 替代执行以下任务：

    - 检查移动鼠标时是否按下了鼠标左键。

    - 将圆圈数据打包成 <xref:System.Windows.DataObject> 。 在这种情况下，圆形控件将打包三个数据项：其填充颜色的字符串表示形式、其高度的双精度表示形式以及其自身的副本。

    - 调用静态 <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> 方法以启动拖放操作。 将以下三个参数传递给 <xref:System.Windows.DragDrop.DoDragDrop%2A> 方法：

        - `dragSource` – 对此控件的引用。

        - `data`– <xref:System.Windows.DataObject> 在前面的代码中创建的。

        - `allowedEffects`–允许的拖放操作，即 <xref:System.Windows.DragDropEffects.Copy> 或 <xref:System.Windows.DragDropEffects.Move> 。

3. 按 F5 生成并运行应用程序。

4. 单击其中一个圆圈控件，并将其拖动到面板、另一个圆圈和上 <xref:System.Windows.Controls.TextBox> 。 在拖动时 <xref:System.Windows.Controls.TextBox> ，光标会更改以指示移动。

5. 将圆圈拖动到上时 <xref:System.Windows.Controls.TextBox> ，按**Ctrl**键。 请注意光标是如何更改以指示复制的。

6. 将一个圆圈拖放到 <xref:System.Windows.Controls.TextBox> 。 圆圈填充颜色的字符串表示形式将追加到 <xref:System.Windows.Controls.TextBox> 。

     ![圆的填充颜色的字符串表示形式](./media/dragdrop-colorstring.png "DragDrop_ColorString")

默认情况下，光标会在拖放操作过程中更改，以指示放置数据会产生的效果。 您可以通过处理 <xref:System.Windows.UIElement.GiveFeedback> 事件并设置不同的游标，自定义为用户提供的反馈。

## <a name="give-feedback-to-the-user"></a>向用户提供反馈

1. 打开 Circle.xaml.cs 或 Circle.xaml.vb。

2. 添加以下 <xref:System.Windows.UIElement.OnGiveFeedback%2A> 替代，以便为事件提供类处理 <xref:System.Windows.UIElement.GiveFeedback> 。

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     此 <xref:System.Windows.UIElement.OnGiveFeedback%2A> 替代执行以下任务：

    - 检查 <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> 在放置目标的 <xref:System.Windows.UIElement.DragOver> 事件处理程序中设置的值。

    - 基于值设置自定义光标 <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> 。 该光标旨在向用户提供关于放置数据所产生的效果的可视反馈。

3. 按 F5 生成并运行应用程序。

4. 将一个圆形控件拖动到面板、另一个圆形和上 <xref:System.Windows.Controls.TextBox> 。 请注意，这些游标现在是在重写中指定的自定义游标 <xref:System.Windows.UIElement.OnGiveFeedback%2A> 。

     ![使用自定义光标拖放](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")

5. `green`从中选择文本 <xref:System.Windows.Controls.TextBox> 。

6. 将 `green` 文本拖到一个圆形控件上。 请注意，将显示默认光标以指示拖放操作效果。 反馈光标始终由拖动源设置。

## <a name="implement-drop-target-events-in-the-user-control"></a>在用户控件中实现放置目标事件
 在本节中，你将指定用户控件为拖放目标，替代可使用户控件成为拖放目标的方法，并处理用户控件上放置的数据。

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a>使用户控件成为拖放目标

1. 打开 Circle.xaml。

2. 在开始 <xref:System.Windows.Controls.UserControl> 标记中，添加 <xref:System.Windows.UIElement.AllowDrop%2A> 属性，并将其设置为 `true` 。

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<xref:System.Windows.UIElement.OnDrop%2A>当 <xref:System.Windows.UIElement.AllowDrop%2A> 属性设置为 `true` ，并将拖动源中的数据放置在圆形用户控件上时，将调用方法。 在这种方法中，将处理已放置的数据，并将这些数据应用于圆形。

### <a name="to-process-the-dropped-data"></a>处理已放置的数据

1. 打开 Circle.xaml.cs 或 Circle.xaml.vb。

2. 添加以下 <xref:System.Windows.UIElement.OnDrop%2A> 替代，以便为事件提供类处理 <xref:System.Windows.UIElement.Drop> 。

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     此 <xref:System.Windows.UIElement.OnDrop%2A> 替代执行以下任务：

    - 使用 <xref:System.Windows.DataObject.GetDataPresent%2A> 方法检查拖动后的数据是否包含字符串对象。

    - 使用 <xref:System.Windows.DataObject.GetData%2A> 方法提取字符串数据（如果存在）。

    - 使用 <xref:System.Windows.Media.BrushConverter> 尝试将字符串转换为 <xref:System.Windows.Media.Brush> 。

    - 如果转换成功，则将画笔应用于 <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> 提供 Circle 控件的 UI 的的。

    - 将 <xref:System.Windows.UIElement.Drop> 事件标记为已处理。 应将放置事件标记为已处理，这样接收此事件的其他元素才会知道圆形用户控件已处理了该事件。

3. 按 F5 生成并运行应用程序。

4. 选择中的文本 `green` <xref:System.Windows.Controls.TextBox> 。

5. 将文本拖放到一个圆形控件上。 该圆形会从蓝色变为绿色。

     ![将字符串转换为画笔](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")

6. 键入中的文本 `green` <xref:System.Windows.Controls.TextBox> 。

7. 选择中的文本 `gre` <xref:System.Windows.Controls.TextBox> 。

8. 将其拖放到一个圆形控件上。 请注意，光标会更改以指示允许放置，但圆形的颜色不会更改，因为 `gre` 不是有效颜色。

9. 从绿色圆形控件拖放到蓝色圆形控件。 该圆形会从蓝色变为绿色。 请注意，显示哪个光标取决于 <xref:System.Windows.Controls.TextBox> 或圆形是否为拖动源。

将 <xref:System.Windows.UIElement.AllowDrop%2A> 属性设置为 `true` 并处理删除的数据是使元素成为放置目标所需的全部。 但是，若要提供更好的用户体验，还应处理 <xref:System.Windows.UIElement.DragEnter> 、 <xref:System.Windows.UIElement.DragLeave> 和 <xref:System.Windows.UIElement.DragOver> 事件。 在这些事件中，你可以在放置数据前执行检查并向用户提供其他反馈。

将数据拖动到圆形用户控件上时，该控件应通知拖动源它是否可以处理所拖动的数据。 如果该控件不知如何处理这些数据，则它应拒绝放置。 为此，您将处理 <xref:System.Windows.UIElement.DragOver> 事件并设置 <xref:System.Windows.DragEventArgs.Effects%2A> 属性。

### <a name="to-verify-that-the-data-drop-is-allowed"></a>验证是否允许数据放置

1. 打开 Circle.xaml.cs 或 Circle.xaml.vb。

2. 添加以下 <xref:System.Windows.UIElement.OnDragOver%2A> 替代，以便为事件提供类处理 <xref:System.Windows.UIElement.DragOver> 。

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     此 <xref:System.Windows.UIElement.OnDragOver%2A> 替代执行以下任务：

    - 将 <xref:System.Windows.DragEventArgs.Effects%2A> 属性设置为 <xref:System.Windows.DragDropEffects.None>。

    - 执行在方法中执行的相同检查， <xref:System.Windows.UIElement.OnDrop%2A> 以确定 Circle 用户控件是否可以处理拖动的数据。

    - 如果用户控件可以处理数据，则将属性设置 <xref:System.Windows.DragEventArgs.Effects%2A> 为 <xref:System.Windows.DragDropEffects.Copy> 或 <xref:System.Windows.DragDropEffects.Move> 。

3. 按 F5 生成并运行应用程序。

4. 选择中的文本 `gre` <xref:System.Windows.Controls.TextBox> 。

5. 将文本拖到一个圆形控件上。 请注意，光标此时会更改以指示不允许放置，因为 `gre` 不是有效颜色。

 可通过应用拖放操作预览进一步增强用户体验。 对于圆圈用户控件，将重写 <xref:System.Windows.UIElement.OnDragEnter%2A> 和 <xref:System.Windows.UIElement.OnDragLeave%2A> 方法。 将数据拖动到控件上方时，当前背景 <xref:System.Windows.Shapes.Shape.Fill%2A> 将保存在占位符变量中。 然后，将该字符串转换为画笔，并将其应用于 <xref:System.Windows.Shapes.Ellipse> 提供圆形 UI 的。 如果在不删除数据的情况下将数据拖出圆圈，则 <xref:System.Windows.Shapes.Shape.Fill%2A> 会将原始值重新应用于该圆形。

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a>预览拖放操作的效果

1. 打开 Circle.xaml.cs 或 Circle.xaml.vb。

2. 在 Circle 类中，声明一个 <xref:System.Windows.Media.Brush> 名为的私有变量 `_previousFill` ，并将其初始化为 `null` 。

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. 添加以下 <xref:System.Windows.UIElement.OnDragEnter%2A> 替代，以便为事件提供类处理 <xref:System.Windows.UIElement.DragEnter> 。

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     此 <xref:System.Windows.UIElement.OnDragEnter%2A> 替代执行以下任务：

    - <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> 在变量中保存的属性 `_previousFill` 。

    - 执行在方法中执行的相同检查， <xref:System.Windows.UIElement.OnDrop%2A> 以确定是否可以将数据转换为 <xref:System.Windows.Media.Brush> 。

    - 如果数据转换为有效 <xref:System.Windows.Media.Brush> ，则将其应用于 <xref:System.Windows.Shapes.Shape.Fill%2A> 的 <xref:System.Windows.Shapes.Ellipse> 。

4. 添加以下 <xref:System.Windows.UIElement.OnDragLeave%2A> 替代，以便为事件提供类处理 <xref:System.Windows.UIElement.DragLeave> 。

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     此 <xref:System.Windows.UIElement.OnDragLeave%2A> 替代执行以下任务：

    - 将 <xref:System.Windows.Media.Brush> 变量中保存的 `_previousFill` 保存到 <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> 提供 CIRCLE 用户控件的 UI 的的。

5. 按 F5 生成并运行应用程序。

6. 选择中的文本 `green` <xref:System.Windows.Controls.TextBox> 。

7. 将该文本拖到一个圆形控件上而不放置。 该圆形会从蓝色变为绿色。

     ![预览拖动&#45;和&#45;拖放操作的效果](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")

8. 将文本拖离该圆形控件。 该圆形会从绿色变回蓝色。

## <a name="enable-a-panel-to-receive-dropped-data"></a>启用面板以接收已删除的数据

在本部分中，将启用承载圆圈用户控件的面板，使其充当拖动的圆形数据的拖放目标。 您将实现代码，使您可以将一个圆形从一个面板移动到另一个面板，或通过按住**Ctrl**键的同时拖动和放置圆圈来创建圆形控件的副本。

1. 打开 MainWindow.xaml。

2. 如下面的 XAML 中所示，在每个 <xref:System.Windows.Controls.StackPanel> 控件中，为和事件添加处理程序 <xref:System.Windows.UIElement.DragOver> <xref:System.Windows.UIElement.Drop> 。 将 <xref:System.Windows.UIElement.DragOver> 事件处理程序命名为， `panel_DragOver` 并将 <xref:System.Windows.UIElement.Drop> 事件命名为 `panel_Drop` 。

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. 打开 MainWindows.xaml.cs 或 MainWindow.xaml.vb。

4. 为 <xref:System.Windows.UIElement.DragOver> 事件处理程序添加以下代码。

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     此 <xref:System.Windows.UIElement.DragOver> 事件处理程序执行以下任务：

    - 检查拖动后的数据是否包含 "对象" 数据，该数据 <xref:System.Windows.DataObject> 由圆圈用户控件打包并传入对的调用 <xref:System.Windows.DragDrop.DoDragDrop%2A> 。

    - 如果存在 "对象" 数据，则检查是否按下了**Ctrl**键。

    - 如果按下了**Ctrl**键，则将 <xref:System.Windows.DragEventArgs.Effects%2A> 属性设置为 <xref:System.Windows.DragDropEffects.Copy> 。 否则，请将 <xref:System.Windows.DragEventArgs.Effects%2A> 属性设置为 <xref:System.Windows.DragDropEffects.Move> 。

5. 为 <xref:System.Windows.UIElement.Drop> 事件处理程序添加以下代码。

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     此 <xref:System.Windows.UIElement.Drop> 事件处理程序执行以下任务：

    - 检查是否已 <xref:System.Windows.UIElement.Drop> 处理事件。 例如，如果在处理事件的另一个圆上放置一个圆圈 <xref:System.Windows.UIElement.Drop> ，则不希望包含该圆圈的面板也处理该事件。

    - 如果 <xref:System.Windows.UIElement.Drop> 未处理该事件，将检查是否按下了**Ctrl**键。

    - 如果在发生此情况时按下**Ctrl**键，则将 <xref:System.Windows.UIElement.Drop> 生成圆圈控件的副本，并将其添加到 <xref:System.Windows.Controls.Panel.Children%2A> 的集合中 <xref:System.Windows.Controls.StackPanel> 。

    - 如果未按下**Ctrl**键，则将圆圈从 <xref:System.Windows.Controls.Panel.Children%2A> 其父面板的集合移动到 <xref:System.Windows.Controls.Panel.Children%2A> 拖放到的面板的集合中。

    - 设置 <xref:System.Windows.DragEventArgs.Effects%2A> 属性以通知 <xref:System.Windows.DragDrop.DoDragDrop%2A> 方法是否执行了移动或复制操作。

6. 按 F5 生成并运行应用程序。

7. `green`从中选择文本 <xref:System.Windows.Controls.TextBox> 。

8. 将文本拖放到一个圆形控件上。

9. 将一个圆形控件从左面板拖放到右面板。 将从左侧面板的集合中删除该圆形 <xref:System.Windows.Controls.Panel.Children%2A> ，并将其添加到右侧面板的 "子项" 集合中。

10. 将一个圆形控件从它所在的面板拖动到另一个面板，按**Ctrl**键。 复制圆圈，并将副本添加到 <xref:System.Windows.Controls.Panel.Children%2A> 接收面板的集合中。

     ![按住 Ctrl 键的同时拖动圆形](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")

## <a name="see-also"></a>另请参阅

- [拖放概述](drag-and-drop-overview.md)
