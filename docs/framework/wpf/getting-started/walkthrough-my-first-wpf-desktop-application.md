---
title: 在 Visual Studio 2019 中创建第一个 WPF 应用-.NET Framework
titleSuffix: ''
description: 开发 Windows Presentation Foundation （WPF）桌面应用程序，其中包括大多数 WPF 应用程序所共有的元素。
ms.date: 09/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
ms.topic: tutorial
ms.custom: mvc,vs-dotnet
ms.openlocfilehash: c9af988bcf291325b11df4fd22827b47090c0b48
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853892"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a>教程：在 Visual Studio 2019 中创建第一个 WPF 应用程序

本文介绍如何开发 Windows Presentation Foundation （WPF）桌面应用程序，该应用程序包括大多数 WPF 应用程序所共有的元素： Extensible Application Markup Language （XAML）标记、代码隐藏、应用程序定义、控件、布局、数据绑定和样式。 若要开发应用程序，请使用 Visual Studio。

在本教程中，你将了解：
> [!div class="checklist"]
>
> - 创建 WPF 项目。
> - 使用 XAML 设计应用程序的用户界面（UI）的外观。
> - 编写代码以生成应用程序的行为。
> - 创建应用程序定义以管理应用程序。
> - 添加控件并创建用于撰写应用程序 UI 的布局。
> - 在应用程序的 UI 中创建样式以实现一致的外观。
> - 将 UI 绑定到数据，从数据填充 UI，并使数据和 UI 同步。

本教程结束时，将生成一个独立的 Windows 应用程序，允许用户查看所选人员的费用报表。 应用程序由多个承载于浏览器样式窗口中的 WPF 页组成。

> [!TIP]
> 本教程中使用的示例代码可用于 Visual Basic 和 c #[教程 WPF 应用程序示例代码](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp)。
>
> 您可以使用此页顶部的语言选择器来切换 c # 和 Visual Basic 之间示例代码的代码语言。

## <a name="prerequisites"></a>必备条件

- 安装了 **.net 桌面开发**工作负载的[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 。

   有关安装最新版本的 Visual Studio 的详细信息，请参阅[安装 Visual studio](/visualstudio/install/install-visual-studio)。

## <a name="create-the-application-project"></a>创建应用程序项目

第一步是创建应用程序基础结构，其中包括应用程序定义、两页和映像。

1. 在名为的 Visual Basic 或 Visual c # 中创建新的 WPF 应用程序项目 **`ExpenseIt`** ：

   1. 打开 Visual Studio，然后在 "**入门**" 菜单下选择 "**创建新项目**"。

      此时将打开 "新建**项目**" 对话框。

   2. 在 "**语言**" 下拉列表中，选择 " **c #** " 或 " **Visual Basic**"。

   3. 选择 " **WPF 应用（.NET Framework）** " 模板，然后选择 "**下一步**"。

      ![“创建新项目”对话框](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)

      此时将打开 "**配置新项目**" 对话框。

   4. 输入项目名称 **`ExpenseIt`** ，然后选择 "**创建**"。

      !["配置新项目" 对话框](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      Visual Studio 将创建项目并打开名为**mainwindow.xaml**的默认应用程序窗口的设计器。

2. 打开*Application .xaml* （Visual Basic）或*app.xaml* （c #）。

    此 XAML 文件定义了 WPF 应用程序和任何应用程序资源。 你还可以使用此文件来指定在应用程序启动时自动显示的 UI，在本例中为*mainwindow.xaml。*

    XAML 中的 Visual Basic 应如下所示：

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    与 c # 中的类似：

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. 打开*mainwindow.xaml*。

    此 XAML 文件是应用程序的主窗口，并显示在页中创建的内容。 <xref:System.Windows.Window>类定义窗口的属性，例如其标题、大小或图标，并处理事件，例如关闭或隐藏。

4. 将 <xref:System.Windows.Window> 元素更改为 <xref:System.Windows.Navigation.NavigationWindow> ，如下面的 XAML 所示：

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   此应用根据用户输入导航到不同的内容。 这就是主要 <xref:System.Windows.Window> 需要更改为的原因 <xref:System.Windows.Navigation.NavigationWindow> 。 <xref:System.Windows.Navigation.NavigationWindow>继承的所有属性 <xref:System.Windows.Window> 。 <xref:System.Windows.Navigation.NavigationWindow>XAML 文件中的元素创建类的实例 <xref:System.Windows.Navigation.NavigationWindow> 。 有关详细信息，请参阅[导航概述](../app-development/navigation-overview.md)。

5. 删除 <xref:System.Windows.Controls.Grid> 标记之间的元素 <xref:System.Windows.Navigation.NavigationWindow> 。

6. 在元素的 XAML 代码中更改以下属性 <xref:System.Windows.Navigation.NavigationWindow> ：

    - 将 <xref:System.Windows.Window.Title%2A> 属性设置为 " `ExpenseIt` "。

    - 将 <xref:System.Windows.FrameworkElement.Height%2A> 属性设置为350像素。

    - 将 <xref:System.Windows.FrameworkElement.Width%2A> 属性设置为500像素。

    XAML 应该如下所示 Visual Basic：

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    对于 c #，与下面类似：

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. 打开*mainwindow.xaml*或*MainWindow.xaml.cs*。

    此文件是一个代码隐藏文件，其中包含处理*mainwindow.xaml*中声明的事件的代码。 此文件包含在 XAML 中定义的窗口的分部类。

8. 如果使用的是 c #，请将 `MainWindow` 类更改为派生自 <xref:System.Windows.Navigation.NavigationWindow> 。 （在 Visual Basic 中，当你更改 XAML 中的窗口时会自动发生这种情况。）C # 代码现在应如下所示：

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a>向应用程序添加文件

本部分将向应用程序添加两个页面和一个图像。

1. 向项目添加一个新页面，并将其命名为 *`ExpenseItHome.xaml`* ：

   1. 在**解决方案资源管理器**中，右键单击 **`ExpenseIt`** 项目节点，然后选择 "**添加**  >  **页**"。

   1. 在 "**添加新项**" 对话框中，已选择 "**页（WPF）** 模板"。 输入名称 **`ExpenseItHome`** ，然后选择 "**添加**"。

    此页是应用程序启动时显示的第一页。 它将显示要从中进行选择的人员的列表，以便为显示费用报表。

1. 打开 *`ExpenseItHome.xaml`* 。

1. 将设置 <xref:System.Windows.Controls.Page.Title%2A> 为 " `ExpenseIt - Home` "。

1. 将设置 `DesignHeight` 为350像素，将设置为 `DesignWidth` 500 像素。

    XAML 现在如下 Visual Basic 显示：

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    对于 c #，与下面类似：

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. 打开*mainwindow.xaml*。

1. 将 <xref:System.Windows.Navigation.NavigationWindow.Source%2A> 属性添加到 <xref:System.Windows.Navigation.NavigationWindow> 元素，并将其设置为 " `ExpenseItHome.xaml` "。

    这会将设置 *`ExpenseItHome.xaml`* 为应用程序启动时第一个打开的页。

    Visual Basic 中的示例 XAML：

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    C # 中的和：

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > 您还可以在 "**属性**" 窗口的 "**杂项**" 类别中设置**Source**属性。
   >
   > ![属性窗口中的源属性](./media/properties-source.png)

1. 向项目中添加另一个新的 WPF 页，并将其命名为*expensereportpage.xaml*：：

   1. 在**解决方案资源管理器**中，右键单击 **`ExpenseIt`** 项目节点，然后选择 "**添加**  >  **页**"。

   1. 在 "**添加新项**" 对话框中，选择 "**页（WPF）** " 模板。 输入名称**expensereportpage.xaml**，然后选择 "**添加**"。

    此页将显示页面上所选人员的费用报表 **`ExpenseItHome`** 。

1. 打开*expensereportpage.xaml*。

1. 将设置 <xref:System.Windows.Controls.Page.Title%2A> 为 " `ExpenseIt - View Expense` "。

1. 将设置 `DesignHeight` 为350像素，将设置为 `DesignWidth` 500 像素。

    在 Visual Basic 中， *expensereportpage.xaml*现在如下所示：

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    与 c # 中的类似：

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. 打开*expenseithome.xaml*和*expensereportpage.xaml*，或*ExpenseItHome.xaml.cs*和*ExpenseReportPage.xaml.cs*。

    创建新的页面文件时，Visual Studio 会自动创建其*代码隐藏*文件。 这些代码隐藏文件处理响应用户输入的逻辑。

    你的代码应类似于以下 **`ExpenseItHome`** 内容：

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    对于**expensereportpage.xaml**，如下所示：

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. 将名为*watermark.png*的图像添加到项目。 你可以创建自己的映像，从示例代码复制文件，或者从[microsoft/WPF 示例](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png)GitHub 存储库获取它。

    1. 右键单击项目节点并选择 "**添加**  >  **现有项**"，或按**Shift** + **Alt** + **A**。

    2. 在 "**添加现有项**" 对话框中，将 "文件筛选器" 设置为 "**所有文件**或**图像文件**"，浏览到想要使用的图像文件，然后选择 "**添加**"。

## <a name="build-and-run-the-application"></a>生成并运行应用程序

1. 若要生成并运行应用程序，请按**F5**或从 "**调试**" 菜单中选择 "**启动调试**"。

    下图显示了具有以下按钮的应用程序 <xref:System.Windows.Navigation.NavigationWindow> ：

    ![生成并运行应用程序。](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. 关闭要返回到 Visual Studio 的应用程序。

## <a name="create-the-layout"></a>创建布局

布局提供了放置 UI 元素的有序方式，还可在调整 UI 大小时管理这些元素的大小和位置。 通常使用以下布局控件之一来创建布局：

- <xref:System.Windows.Controls.Canvas>-定义一个区域，可在其中使用相对于画布区域的坐标显式定位子元素。
- <xref:System.Windows.Controls.DockPanel>-定义一个区域，您可以在其中彼此水平或垂直排列子元素。
- <xref:System.Windows.Controls.Grid>-定义由列和行组成的灵活的网格区域。
- <xref:System.Windows.Controls.StackPanel>-将子元素排列到可以水平或垂直方向的单个行中。
- <xref:System.Windows.Controls.VirtualizingStackPanel>-在水平或垂直方向的单个行上排列和虚拟化内容。
- <xref:System.Windows.Controls.WrapPanel>-按从左至右的顺序位置定位子元素，在包含框的边缘处将内容分解到下一行。 后续排序按从上到下或从右到左的顺序进行，具体取决于 "方向" 属性的值。

其中每个布局控件都支持其子元素的特定类型的布局。 `ExpenseIt`可以调整页的大小，并且每个页面都具有与其他元素水平和垂直排列的元素。 在此示例中，用作 <xref:System.Windows.Controls.Grid> 应用程序的布局元素。

> [!TIP]
> 有关元素的详细信息 <xref:System.Windows.Controls.Panel> ，请参阅[面板概述](../controls/panels-overview.md)。 有关布局的详细信息，请参阅[布局](../advanced/layout.md)。

在本部分中，通过将列和行定义添加到中的来创建包含三行和10像素边距的单列表 <xref:System.Windows.Controls.Grid> *`ExpenseItHome.xaml`* 。

1. 在中 *`ExpenseItHome.xaml`* ，将 <xref:System.Windows.FrameworkElement.Margin%2A> 元素的属性设置 <xref:System.Windows.Controls.Grid> 为 "10，0，10，10"，这对应于 "左"、"上"、"右" 和 "下" 边距：

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > 您还可以在 "**属性**" 窗口中的 "**布局**" 类别下设置**边距**值：
   >
   > ![属性窗口中的边距值](./media/properties-margin.png)

2. 在标记之间添加以下 XAML <xref:System.Windows.Controls.Grid> 以创建行和列定义：

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <xref:System.Windows.Controls.RowDefinition.Height%2A>两行的均设置为 <xref:System.Windows.GridLength.Auto%2A> ，这意味着根据行中的内容调整行的大小。 默认值 <xref:System.Windows.Controls.RowDefinition.Height%2A> 为 <xref:System.Windows.GridUnitType.Star> 大小调整，这意味着行高为可用空间的加权比例。 例如，如果两个行都具有 <xref:System.Windows.Controls.RowDefinition.Height%2A> "*"，则每个行都具有一半的可用空间。

    <xref:System.Windows.Controls.Grid>现在应包含以下 XAML：

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a>添加控件

在本部分中，你将更新主页 UI 以显示人员列表，你可以在其中选择一个人员来显示其费用报表。 控件是允许用户与应用程序交互的 UI 对象。 有关详细信息，请参阅[控件](../controls/index.md)。

若要创建此 UI，你需要将以下元素添加到 *`ExpenseItHome.xaml`* ：

- 一个 <xref:System.Windows.Controls.ListBox> （适用于用户列表）。
- 一个 <xref:System.Windows.Controls.Label> （用于列表标头）。
- 一个 <xref:System.Windows.Controls.Button> （单击此项可查看列表中所选人员的费用报表）。

每个控件都 <xref:System.Windows.Controls.Grid> 通过设置附加属性放置在的一行中 <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> 。 有关附加属性的详细信息，请参阅[附加属性概述](../advanced/attached-properties-overview.md)。

1. 在中 *`ExpenseItHome.xaml`* ，在标记之间添加以下 XAML <xref:System.Windows.Controls.Grid> ：

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > 还可以通过将控件从 "**工具箱**" 窗口拖到设计窗口，然后在 "**属性**" 窗口中设置其属性来创建控件。

2. 生成并运行应用程序。

    下图显示了您创建的控件：

![显示名称列表的 ExpenseIt 示例屏幕截图](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a>添加图像和标题

在本部分中，将使用图像和页面标题更新主页 UI。

1. 在中 *`ExpenseItHome.xaml`* ，将另一列添加到 <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> 具有固定 <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 的230像素的中：

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewColumn)]

2. 向添加另一行 <xref:System.Windows.Controls.Grid.RowDefinitions%2A> ，总计四行：

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewRows)]

3. 将控件移动到第二列，方法是将 <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> 这三个控件（边框、列表框和按钮）中每个控件的属性设置为1。

4. 将每个控件的值向下移动一行， <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> 为三个控件中的每一个（边框、列表框和按钮）和 Border 元素递增1。

   这三个控件的 XAML 现在如下所示：

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>通过将以下 XAML 添加到和标记之间的任意位置，将属性设置为*watermark.png*的图像文件 `<Grid>` `</Grid>` ：

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. 在 <xref:System.Windows.Controls.Border> 元素之前，添加一个 <xref:System.Windows.Controls.Label> 具有内容 "查看支出报表" 的。 此标签是页面的标题。

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. 生成并运行应用程序。

下图显示刚刚添加的内容的结果：

![显示新图像背景和页面标题的 ExpenseIt 示例屏幕截图](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a>添加代码以处理事件

1. 在中 *`ExpenseItHome.xaml`* ，向 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 元素添加一个事件处理程序 <xref:System.Windows.Controls.Button> 。 有关详细信息，请参阅[如何：创建简单的事件处理程序](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))。

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. 打开 *`ExpenseItHome.xaml.vb`* 或 *`ExpenseItHome.xaml.cs`* 。

3. 将下面的代码添加到 `ExpenseItHome` 类，以添加按钮单击事件处理程序。 该事件处理程序将打开**expensereportpage.xaml**页。

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a>创建 Expensereportpage.xaml 的 UI

*Expensereportpage.xaml*显示页面上所选人员的费用报表 **`ExpenseItHome`** 。 在本部分中，你将为**expensereportpage.xaml**创建 UI。 还将向各种 UI 元素添加背景色和填充颜色。

1. 打开*expensereportpage.xaml*。

2. 在标记之间添加以下 XAML <xref:System.Windows.Controls.Grid> ：

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    此 UI 类似于 *`ExpenseItHome.xaml`* ，只不过报表数据显示在中 <xref:System.Windows.Controls.DataGrid> 。

3. 生成并运行应用程序。

4. 选择 "**视图**" 按钮。

    出现费用报告页。 另请注意，"后退" 导航按钮已启用。

下图显示了添加到*expensereportpage.xaml*的 UI 元素。

![ExpenseIt 示例屏幕截图，显示刚刚为 Expensereportpage.xaml 创建的 UI。](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a>样式控件

对于 UI 中同一类型的所有元素，各种元素的外观通常是相同的。 UI 使用[样式](../../../desktop-wpf/fundamentals/styles-templates-overview.md)使外观在多个元素中可重用。 样式的可重用性有助于简化 XAML 创建和管理。 本部分替换在以前步骤中通过样式定义的按元素划分的属性。

1. 打开*Application .xaml*或*app.xaml*。

2. 在标记之间添加以下 XAML <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> ：

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    此 XAML 将添加以下样式：

    - `headerTextStyle`：可设置页标题 <xref:System.Windows.Controls.Label>的格式。

    - `labelStyle`：可设置 <xref:System.Windows.Controls.Label> 控件的格式。

    - `columnHeaderStyle`：可设置 <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>的格式。

    - `listHeaderStyle`：可设置列表标头 <xref:System.Windows.Controls.Border> 控件的格式。

    - `listHeaderTextStyle`：用于设置列表标头的格式 <xref:System.Windows.Controls.Label> 。

    - `buttonStyle`：用于设置的 <xref:System.Windows.Controls.Button> 格式 `ExpenseItHome.xaml` 。

    请注意，样式是属性元素的资源和子级 <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> 。 在此位置中，这些样式将应用到应用程序中的所有元素。 有关在 .NET 应用中使用资源的示例，请参阅[使用应用程序资源](../advanced/how-to-use-application-resources.md)。

3. 在中 *`ExpenseItHome.xaml`* ，将元素之间的所有内容替换 <xref:System.Windows.Controls.Grid> 为以下 XAML：

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    应用样式会删除和替换定义每个控件外观的属性（如 <xref:System.Windows.VerticalAlignment> 和 <xref:System.Windows.Media.FontFamily> 。 例如，将 `headerTextStyle` 应用于 "查看支出报表" <xref:System.Windows.Controls.Label> 。

4. 打开*expensereportpage.xaml*。

5. 将元素之间的所有内容替换 <xref:System.Windows.Controls.Grid> 为以下 XAML：

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    此 XAML 将样式添加到 <xref:System.Windows.Controls.Label> 和 <xref:System.Windows.Controls.Border> 元素。

6. 生成并运行应用程序。 窗口外观与以前相同。

    ![与上一节中的外观相同的 ExpenseIt 示例屏幕快照。](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. 关闭要返回到 Visual Studio 的应用程序。

## <a name="bind-data-to-a-control"></a>将数据绑定到控件

在本部分中，将创建绑定到各种控件的 XML 数据。

1. 在中 *`ExpenseItHome.xaml`* ，在开始 <xref:System.Windows.Controls.Grid> 元素之后，添加以下 XAML 以创建一个 <xref:System.Windows.Data.XmlDataProvider> 包含每个用户的数据的：

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    数据作为 <xref:System.Windows.Controls.Grid> 资源创建。 通常，此数据将作为文件加载，但为简单起见，数据是以内联方式添加的。

2. 在 `<Grid.Resources>` 元素中，添加以下 `<xref:System.Windows.DataTemplate>` 元素，该元素定义如何在中的 <xref:System.Windows.Controls.ListBox> 元素后显示数据 `<XmlDataProvider>` ：

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    有关数据模板的详细信息，请参阅[数据模板化概述](../data/data-templating-overview.md)。

3. 将现有的替换 <xref:System.Windows.Controls.ListBox> 为以下 XAML：

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    此 XAML 将 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 的属性绑定 <xref:System.Windows.Controls.ListBox> 到数据源，并应用数据模板作为 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 。

## <a name="connect-data-to-controls"></a>将数据连接到控件

接下来，您将添加代码以检索在页面上选择的名称 **`ExpenseItHome`** ，并将其传递给**expensereportpage.xaml**的构造函数。 **Expensereportpage.xaml**用传递的项设置其数据上下文，这是在*expensereportpage.xaml*中定义的控件绑定到的内容。

1. 打开*expensereportpage.xaml*或*ExpenseReportPage.xaml.cs*。

2. 添加获取对象的构造函数，以便传递所选人员的费用报表数据。

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. 打开 *`ExpenseItHome.xaml.vb`* 或 *`ExpenseItHome.xaml.cs`* 。

4. 更改 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件处理程序以调用传递所选人员的费用报表数据的新构造函数。

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a>数据模板的样式数据

在本部分中，将使用数据模板更新数据绑定列表中每个项的 UI。

1. 打开*expensereportpage.xaml*。

2. 将 "名称" 和 "部门" 元素的内容绑定 <xref:System.Windows.Controls.Label> 到相应的数据源属性。 有关数据绑定的详细信息，请参阅[数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)。

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. 在开始 <xref:System.Windows.Controls.Grid> 元素之后，添加以下数据模板，这些数据模板定义如何显示费用报表数据：

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. 将元素替换为 <xref:System.Windows.Controls.DataGridTextColumn> <xref:System.Windows.Controls.DataGridTemplateColumn> 元素下的元素 <xref:System.Windows.Controls.DataGrid> ，并将模板应用于这些元素。

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. 生成并运行应用程序。

6. 选择一个用户，然后选择 "**查看**" 按钮。

下图显示了应用程序的两个页面 `ExpenseIt` ，并应用了控件、布局、样式、数据绑定和数据模板：

![应用的两个页面均显示名称列表和支出报表。](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> 此示例演示了 WPF 的特定功能，并且不遵循安全性、本地化和辅助功能等功能的所有最佳实践。 有关 WPF 和 .NET 应用开发最佳做法的全面介绍，请参阅以下主题：
>
> - [辅助功能](../../ui-automation/accessibility-best-practices.md)
> - [安全性](../security-wpf.md)
> - [WPF 全球化和本地化](../advanced/wpf-globalization-and-localization-overview.md)
> - [WPF 性能](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a>后续步骤

在本演练中，您学习了使用 Windows Presentation Foundation （WPF）创建 UI 的多种方法。 现在，你应基本了解数据绑定 .NET 应用的构建基块。 有关 WPF 体系结构和编程模型的详细信息，请参阅以下主题：

- [WPF 体系结构](../advanced/wpf-architecture.md)
- [XAML 概述（WPF）](../../../desktop-wpf/fundamentals/xaml.md)
- [依赖属性概述](../advanced/dependency-properties-overview.md)
- [布局](../advanced/layout.md)

有关创建应用程序的详细信息，请参阅以下主题：

- [应用程序开发](../app-development/index.md)
- [控件](../controls/index.md)
- [数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)
- [图形和多媒体](../graphics-multimedia/index.md)
- [WPF 中的文档](../advanced/documents-in-wpf.md)

## <a name="see-also"></a>另请参阅

- [面板概述](../controls/panels-overview.md)
- [数据模板化概述](../data/data-templating-overview.md)
- [生成 WPF 应用程序](../app-development/building-a-wpf-application-wpf.md)
- [样式和模板](../controls/styles-and-templates.md)
