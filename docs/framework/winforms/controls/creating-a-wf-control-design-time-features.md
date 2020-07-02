---
title: 创建利用 Visual Studio 设计时功能的控件
description: 了解如何在 Windows 窗体中为自定义控件创建自定义设计器，以利用设计时功能。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms controls, creating
- design-time functionality [Windows Forms], Windows Forms
- DocumentDesigner class [Windows Forms]
- walkthroughs [Windows Forms], controls
ms.assetid: 6f487c59-cb38-4afa-ad2e-95edacb1d626
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 03c04578ecb01b689f58d41a46eef5793fb1182c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613905"
---
# <a name="walkthrough-create-a-control-that-takes-advantage-of-design-time-features"></a>演练：创建利用设计时功能的控件

通过创作关联的自定义设计器，可以增强自定义控件的设计时体验。

本文说明如何为自定义控件创建自定义设计器。 您将实现一个 `MarqueeControl` 名为的类型和一个关联的设计器类 `MarqueeControlRootDesigner` 。

该 `MarqueeControl` 类型实现的显示类似于具有动画光和闪烁文本的剧院字幕。

此控件的设计器与设计环境交互，以提供自定义的设计时体验。 使用自定义设计器，可以 `MarqueeControl` 在许多组合中使用动态光源和闪烁文本来组装自定义实现。 可以像任何其他 Windows 窗体控件一样使用窗体上的组合控件。

完成本演练后，自定义控件将如下所示：

![该应用显示了文本和 "开始" 和 "停止" 按钮的选框。](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

有关完整的代码列表，请参阅[如何：创建利用设计时功能的 Windows 窗体控件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))。

## <a name="prerequisites"></a>先决条件

若要完成本演练，你将需要 Visual Studio。

## <a name="create-the-project"></a>创建项目

第一步是创建应用程序项目。 将使用此项目生成承载自定义控件的应用程序。

在 Visual Studio 中，创建一个新的 Windows 窗体应用程序项目，并将其命名为**MarqueeControlTest**。

## <a name="create-the-control-library-project"></a>创建控件库项目

1. 将 Windows 窗体控件库项目添加到解决方案。 将项目命名为**MarqueeControlLibrary**。

2. 使用**解决方案资源管理器**，通过删除名为 "UserControl1.cs" 或 "UserControl1" 的源文件来删除项目的默认控件，具体取决于您选择的语言。

3. 向 <xref:System.Windows.Forms.UserControl> 项目中添加新项 `MarqueeControlLibrary` 。 为新的源文件指定基名称**MarqueeControl**。

4. 使用**解决方案资源管理器**在项目中创建一个新文件夹 `MarqueeControlLibrary` 。

5. 右键单击**设计**文件夹并添加一个新类。 将其命名为**MarqueeControlRootDesigner**。

6. 需要使用来自 System.object 程序集的类型，因此请将此引用添加到 `MarqueeControlLibrary` 项目。

## <a name="reference-the-custom-control-project"></a>引用自定义控件项目

您将使用该 `MarqueeControlTest` 项目来测试自定义控件。 向程序集添加项目引用时，测试项目将会感知自定义控件 `MarqueeControlLibrary` 。

在 `MarqueeControlTest` 项目中，添加对程序集的项目引用 `MarqueeControlLibrary` 。 请确保使用 "**添加引用**" 对话框中的 "**项目**" 选项卡，而不是 `MarqueeControlLibrary` 直接引用程序集。

## <a name="define-a-custom-control-and-its-custom-designer"></a>定义自定义控件及其自定义设计器

自定义控件将派生自 <xref:System.Windows.Forms.UserControl> 类。 这允许控件包含其他控件，并使控件具有大量默认功能。

自定义控件将具有关联的自定义设计器。 这允许您创建专为自定义控件定制的独特设计体验。

使用类将控件与其设计器相关联 <xref:System.ComponentModel.DesignerAttribute> 。 由于您正在开发自定义控件的整个设计时行为，因此自定义设计器将实现该 <xref:System.ComponentModel.Design.IRootDesigner> 接口。

### <a name="to-define-a-custom-control-and-its-custom-designer"></a>定义自定义控件及其自定义设计器

1. `MarqueeControl`在**代码编辑器**中打开源文件。 在该文件的顶部，导入以下命名空间：

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. 将添加 <xref:System.ComponentModel.DesignerAttribute> 到 `MarqueeControl` 类声明中。 这会将自定义控件与其设计器相关联。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. `MarqueeControlRootDesigner`在**代码编辑器**中打开源文件。 在该文件的顶部，导入以下命名空间：

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. 更改的声明 `MarqueeControlRootDesigner` 以从 <xref:System.Windows.Forms.Design.DocumentDesigner> 类继承。 应用， <xref:System.ComponentModel.ToolboxItemFilterAttribute> 以指定与**工具箱**的设计器交互。

   > [!NOTE]
   > 类的定义已 `MarqueeControlRootDesigner` 包含在名为 MarqueeControlLibrary 的命名空间中。 此声明将设计器置于为设计相关类型保留的特殊命名空间中。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. 定义类的构造函数 `MarqueeControlRootDesigner` 。 <xref:System.Diagnostics.Trace.WriteLine%2A>在构造函数主体中插入语句。 这对于调试很有用。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="create-an-instance-of-your-custom-control"></a>创建自定义控件的实例

1. 向 <xref:System.Windows.Forms.UserControl> 项目中添加新项 `MarqueeControlTest` 。 为新的源文件指定基名称**DemoMarqueeControl**。

2. `DemoMarqueeControl`在**代码编辑器**中打开文件。 在该文件的顶部，导入 `MarqueeControlLibrary` 命名空间：

   ```vb
   Imports MarqueeControlLibrary
   ```

   ```csharp
   using MarqueeControlLibrary;
   ```

3. 更改的声明 `DemoMarqueeControl` 以从 `MarqueeControl` 类继承。

4. 生成项目。

5. 在 Windows 窗体设计器中打开 "Form1"。

6. 找到 "**工具箱**" 中的 " **MarqueeControlTest 组件**" 选项卡并将其打开。 将 `DemoMarqueeControl` 从 "**工具箱**" 拖到窗体上。

7. 生成项目。

## <a name="set-up-the-project-for-design-time-debugging"></a>设置项目以进行设计时调试

开发自定义设计时体验时，必须调试控件和组件。 可以通过一种简单的方式将项目设置为允许在设计时进行调试。 有关详细信息，请参阅[演练：在设计时调试自定义 Windows 窗体控件](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)。

1. 右键单击该 `MarqueeControlLibrary` 项目，然后选择 "**属性**"。

2. 在 " **MarqueeControlLibrary 属性页**" 对话框中，选择 "**调试**" 页。

3. 在 "**启动操作**" 部分中，选择 "**启动外部程序**"。 你将调试单独的 Visual Studio 实例，因此单击 " ![ Visual studio 属性窗口中的省略号按钮（...）， ](./media/visual-studio-ellipsis-button.png) 浏览 VISUAL studio IDE。 可执行文件的名称是 devenv.exe 的，如果安装到默认位置，其路径为 *% ProgramFiles （x86）% \ Microsoft Visual Studio\2019 \\ \<edition>\Common7\IDE\devenv.exe*。

4. 选择“确定”以关闭该对话框。****

5. 右键单击 "MarqueeControlLibrary" 项目，然后选择 "**设为启动项目**" 来启用此调试配置。

## <a name="checkpoint"></a>检查点

你现在已准备好调试自定义控件的设计时行为。 确定正确设置了调试环境后，可以测试自定义控件和自定义设计器之间的关联。

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>测试调试环境和设计器关联

1. 在**代码编辑器**中打开 MarqueeControlRootDesigner 源文件，并在语句中放置一个断点 <xref:System.Diagnostics.Trace.WriteLine%2A> 。

2. 按**F5**启动调试会话。

   创建 Visual Studio 的新实例。

3. 在 Visual Studio 的新实例中，打开 MarqueeControlTest 解决方案。 通过从 "**文件**" 菜单中选择 "**最近使用的项目**"，可以轻松地找到解决方案。 MarqueeControlTest 解决方案文件将作为最近使用过的文件列出。

4. `DemoMarqueeControl`在设计器中打开。

   Visual Studio 的调试实例获取焦点，并在断点处停止执行。 按**F5**继续调试会话。

此时，所有内容都已准备就绪，可用于开发和调试自定义控件及其关联的自定义设计器。 本文的其余部分重点介绍了实现控件和设计器功能的详细信息。

## <a name="implement-the-custom-control"></a>实现自定义控件

只 `MarqueeControl` 需进行 <xref:System.Windows.Forms.UserControl> 一些自定义。 它公开了两个方法： `Start` ，用于启动字幕动画和 `Stop` ，这会停止动画。 由于 `MarqueeControl` 包含实现接口的子控件 `IMarqueeWidget` ， `Start` 并 `Stop` 枚举每个子控件并 `StartMarquee` `StopMarquee` 分别在实现的每个子控件上调用和方法 `IMarqueeWidget` 。

和控件的外观 `MarqueeBorder` `MarqueeText` 依赖于布局，因此 `MarqueeControl` 重写 <xref:System.Windows.Forms.Control.OnLayout%2A> <xref:System.Windows.Forms.Control.PerformLayout%2A> 此类型的子控件上的方法和调用。

这是自定义的范围 `MarqueeControl` 。 运行时功能由 `MarqueeBorder` 和 `MarqueeText` 控件实现，设计时功能由 `MarqueeBorderDesigner` 和 `MarqueeControlRootDesigner` 类实现。

### <a name="to-implement-your-custom-control"></a>实现自定义控件

1. `MarqueeControl`在**代码编辑器**中打开源文件。 实现 `Start` 和 `Stop` 方法。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. 重写 <xref:System.Windows.Forms.Control.OnLayout%2A> 方法。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="create-a-child-control-for-your-custom-control"></a>为自定义控件创建子控件

`MarqueeControl`将承载两种类型的子控件： `MarqueeBorder` 控件和 `MarqueeText` 控件。

- `MarqueeBorder`：此控件围绕边缘绘制 "光源" 边框。 灯光按顺序闪烁，使其看起来像是在边框上移动。 光源的闪烁速度由一个名为的属性控制 `UpdatePeriod` 。 其他几个自定义属性确定控件外观的其他方面。 两个称为和的方法 `StartMarquee` `StopMarquee` 控制动画的开始和停止时间。

- `MarqueeText`：此控件绘制闪烁的字符串。 与 `MarqueeBorder` 控件一样，文本闪烁的速度由 `UpdatePeriod` 属性控制。 `MarqueeText`控件还具有 `StartMarquee` `StopMarquee` 与控件共有的和方法 `MarqueeBorder` 。

在设计时，可以将 `MarqueeControlRootDesigner` 这两个控件类型添加到中的 `MarqueeControl` 任意组合。

这两个控件的常见功能分解为一个名为的接口 `IMarqueeWidget` 。 这样， `MarqueeControl` 就可以发现任何与选框相关的子控件，并使它们特别对待。

若要实现定期动画功能，您将使用 <xref:System.ComponentModel.BackgroundWorker> 命名空间中的对象 <xref:System.ComponentModel?displayProperty=nameWithType> 。 可以使用 <xref:System.Windows.Forms.Timer> 对象，但当存在许多 `IMarqueeWidget` 对象时，单个 UI 线程可能无法跟上动画。

### <a name="to-create-a-child-control-for-your-custom-control"></a>为自定义控件创建子控件

1. 向项目中添加一个新的类项 `MarqueeControlLibrary` 。 为新的源文件命名为 "IMarqueeWidget" 的基名称。

2. `IMarqueeWidget`在**代码编辑器**中打开源文件，并将声明从更改 `class` 为 `interface` ：

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. 将以下代码添加到 `IMarqueeWidget` 接口，以公开操作字幕动画的两个方法和属性：

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. 向项目中添加一个新的**自定义控件**项 `MarqueeControlLibrary` 。 为新的源文件命名为 "MarqueeText" 的基名称。

5. 将 <xref:System.ComponentModel.BackgroundWorker> 组件从 "**工具箱**" 拖到 `MarqueeText` 控件上。 此组件允许 `MarqueeText` 控件以异步方式更新自身。

6. 在 "**属性**" 窗口中，将 <xref:System.ComponentModel.BackgroundWorker> 组件的 `WorkerReportsProgress` 和属性设置为 " <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> **true**"。 这些设置使 <xref:System.ComponentModel.BackgroundWorker> 组件可以定期引发 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件并取消异步更新。

   有关详细信息，请参阅[BackgroundWorker 组件](backgroundworker-component.md)。

7. `MarqueeText`在**代码编辑器**中打开源文件。 在该文件的顶部，导入以下命名空间：

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. 更改的声明 `MarqueeText` 以从和中继承 <xref:System.Windows.Forms.Label> 以实现 `IMarqueeWidget` 接口：

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. 声明与公开的属性相对应的实例变量，并在构造函数中对其进行初始化。 `isLit`字段确定是否要以属性指定的颜色绘制文本 `LightColor` 。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. 实现 `IMarqueeWidget` 接口。

    `StartMarquee`和 `StopMarquee` 方法调用 <xref:System.ComponentModel.BackgroundWorker> 组件的 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 和 <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> 方法来启动和停止动画。

    <xref:System.ComponentModel.CategoryAttribute.Category%2A>和 <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> 特性应用于 `UpdatePeriod` 属性，使其显示在名为 "Marquee" 属性窗口的自定义部分中。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. 实现属性访问器。 将向客户端公开两个属性： `LightColor` 和 `DarkColor` 。 <xref:System.ComponentModel.CategoryAttribute.Category%2A>和 <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> 属性应用于这些属性，因此属性显示在名为 "Marquee" 属性窗口的自定义部分中。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. 实现 <xref:System.ComponentModel.BackgroundWorker> 组件和事件的处理程序 <xref:System.ComponentModel.BackgroundWorker.DoWork> <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 。

    <xref:System.ComponentModel.BackgroundWorker.DoWork>事件处理程序休眠指定的毫秒数 `UpdatePeriod` ，并引发 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件，直到代码通过调用停止动画 <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> 。

    <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件处理程序在其亮状态和暗状态之间切换文本，以显示闪烁的外观。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. 重写 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法以启用动画。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. 按 **F6** 以生成解决方案。

## <a name="create-the-marqueeborder-child-control"></a>创建 MarqueeBorder 子控件

`MarqueeBorder`控件比控件稍微复杂一些 `MarqueeText` 。 它具有更多属性，并且方法中的动画 <xref:System.Windows.Forms.Control.OnPaint%2A> 更多。 原则上，它非常类似于 `MarqueeText` 控件。

由于 `MarqueeBorder` 控件可以有子控件，因此需要知道 <xref:System.Windows.Forms.Control.Layout> 事件。

### <a name="to-create-the-marqueeborder-control"></a>创建 MarqueeBorder 控件

1. 向项目中添加一个新的**自定义控件**项 `MarqueeControlLibrary` 。 为新的源文件命名为 "MarqueeBorder" 的基名称。

2. 将 <xref:System.ComponentModel.BackgroundWorker> 组件从 "**工具箱**" 拖到 `MarqueeBorder` 控件上。 此组件允许 `MarqueeBorder` 控件以异步方式更新自身。

3. 在 "**属性**" 窗口中，将 <xref:System.ComponentModel.BackgroundWorker> 组件的 `WorkerReportsProgress` 和属性设置为 " <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> **true**"。 这些设置使 <xref:System.ComponentModel.BackgroundWorker> 组件可以定期引发 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件并取消异步更新。 有关详细信息，请参阅[BackgroundWorker 组件](backgroundworker-component.md)。

4. 在 "**属性**" 窗口中，选择 "**事件**" 按钮。 为和事件附加处理程序 <xref:System.ComponentModel.BackgroundWorker.DoWork> <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 。

5. `MarqueeBorder`在**代码编辑器**中打开源文件。 在该文件的顶部，导入以下命名空间：

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. 更改的声明 `MarqueeBorder` 以从和中继承 <xref:System.Windows.Forms.Panel> 以实现 `IMarqueeWidget` 接口。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. 声明两个枚举，用于管理 `MarqueeBorder` 控件的状态： `MarqueeSpinDirection` ，确定灯光围绕边框的 "旋转" 方向， `MarqueeLightShape` 确定光源的形状（方形或圆形）。 将这些声明放在 `MarqueeBorder` 类声明之前。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. 声明与公开的属性相对应的实例变量，并在构造函数中对其进行初始化。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. 实现 `IMarqueeWidget` 接口。

    `StartMarquee`和 `StopMarquee` 方法调用 <xref:System.ComponentModel.BackgroundWorker> 组件的 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 和 <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> 方法来启动和停止动画。

    由于 `MarqueeBorder` 控件可以包含子控件，因此该 `StartMarquee` 方法将枚举所有子控件，并调用 `StartMarquee` 实现的这些子控件 `IMarqueeWidget` 。 `StopMarquee`方法具有类似的实现。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. 实现属性访问器。 `MarqueeBorder`控件具有几个用于控制其外观的属性。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. 实现 <xref:System.ComponentModel.BackgroundWorker> 组件和事件的处理程序 <xref:System.ComponentModel.BackgroundWorker.DoWork> <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 。

    <xref:System.ComponentModel.BackgroundWorker.DoWork>事件处理程序休眠指定的毫秒数 `UpdatePeriod` ，并引发 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件，直到代码通过调用停止动画 <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> 。

    该 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件处理程序会递增 "基本" 光源的位置，从该光源确定另一个光源的亮/暗状态，并调用 <xref:System.Windows.Forms.Control.Refresh%2A> 方法来使控件重绘自身。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. 实现帮助器方法 `IsLit` 和 `DrawLight` 。

    `IsLit`方法确定指定位置的光线颜色。 "亮" 的灯光以属性给定的颜色进行绘制 `LightColor` ，而 "深色" 的光源则以属性给定的颜色进行绘制 `DarkColor` 。

    `DrawLight`方法使用适当的颜色、形状和位置绘制光。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. 替代 <xref:System.Windows.Forms.Control.OnLayout%2A> 和 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。

    <xref:System.Windows.Forms.Control.OnPaint%2A>方法沿控件边缘绘制灯光 `MarqueeBorder` 。

    由于 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法依赖于控件的尺寸，因此 `MarqueeBorder` 每当布局发生更改时都需要调用该方法。 若要实现此目的，请重写 <xref:System.Windows.Forms.Control.OnLayout%2A> 并调用 <xref:System.Windows.Forms.Control.Refresh%2A> 。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="create-a-custom-designer-to-shadow-and-filter-properties"></a>创建自定义设计器以隐藏和筛选属性

`MarqueeControlRootDesigner`类提供根设计器的实现。 除了在上运行的此设计器外， `MarqueeControl` 还需要一个专门与控件关联的自定义设计器 `MarqueeBorder` 。 此设计器提供适用于自定义根设计器的上下文的自定义行为。

具体而言， `MarqueeBorderDesigner` 将 "隐藏" 并筛选控件上的某些属性 `MarqueeBorder` ，更改与设计环境的交互。

截获对组件的属性访问器的调用称为 "隐藏"。 它允许设计器跟踪用户设置的值，还可以选择将该值传递给所设计的组件。

在此示例中， <xref:System.Windows.Forms.Control.Visible%2A> 和 <xref:System.Windows.Forms.Control.Enabled%2A> 属性将由隐藏 `MarqueeBorderDesigner` ，这会阻止用户在 `MarqueeBorder` 设计时使控件不可见或处于禁用状态。

设计器还可以添加和移除属性。 在此示例中， <xref:System.Windows.Forms.Control.Padding%2A> 将在设计时删除属性，因为 `MarqueeBorder` 控件以编程方式基于属性指定的灯光大小设置填充 `LightSize` 。

的基类 `MarqueeBorderDesigner` 为 <xref:System.ComponentModel.Design.ComponentDesigner> ，它具有可在设计时更改控件所公开的特性、属性和事件的方法：

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

使用这些方法更改组件的公共接口时，请遵循以下规则：

- 仅在方法中添加或删除项 `PreFilter`

- 仅修改方法中的现有项 `PostFilter`

- 始终在方法中首先调用基实现 `PreFilter`

- 始终在方法中最后调用基本实现 `PostFilter`

遵循这些规则可确保设计时环境中的所有设计器都具有设计中所有组件的一致视图。

<xref:System.ComponentModel.Design.ComponentDesigner>类提供字典，用于管理隐藏属性的值，从而使您不必创建特定的实例变量。

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>创建用于隐藏和筛选属性的自定义设计器

1. 右键单击**设计**文件夹并添加一个新类。 为源文件指定基名称**MarqueeBorderDesigner**。

2. 在**代码编辑器**中打开 MarqueeBorderDesigner 源文件。 在该文件的顶部，导入以下命名空间：

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. 更改的声明 `MarqueeBorderDesigner` 以从继承 <xref:System.Windows.Forms.Design.ParentControlDesigner> 。

    由于 `MarqueeBorder` 控件可以包含子控件，因此 `MarqueeBorderDesigner` 继承自 <xref:System.Windows.Forms.Design.ParentControlDesigner> ，后者处理父子交互。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. 重写的基实现 <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A> 。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. 实现 <xref:System.Windows.Forms.Control.Enabled%2A> 和 <xref:System.Windows.Forms.Control.Visible%2A> 属性。 这些实现将隐藏控件的属性。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handle-component-changes"></a>处理组件更改

`MarqueeControlRootDesigner`类为你的实例提供自定义的设计时体验 `MarqueeControl` 。 大多数设计时功能都是从类继承的 <xref:System.Windows.Forms.Design.DocumentDesigner> 。 你的代码将实现两个特定的自定义：处理组件更改和添加设计器谓词。

当用户设计其 `MarqueeControl` 实例时，你的根设计器将跟踪及其 `MarqueeControl` 子控件的更改。 设计时环境提供了一种方便的服务， <xref:System.ComponentModel.Design.IComponentChangeService> 用于跟踪对组件状态的更改。

通过使用方法查询环境来获取对此服务的引用 <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> 。 如果查询成功，设计器可以为事件附加处理程序， <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> 并执行在设计时保持一致状态所需的任何任务。

对于 `MarqueeControlRootDesigner` 类，您将 <xref:System.Windows.Forms.Control.Refresh%2A> 对包含的每个对象调用方法 `IMarqueeWidget` `MarqueeControl` 。 这会使 `IMarqueeWidget` 对象在其父级的属性（如属性）发生更改时正确重绘自身 <xref:System.Windows.Forms.Control.Size%2A> 。

### <a name="to-handle-component-changes"></a>处理组件更改

1. `MarqueeControlRootDesigner`在**代码编辑器**中打开源文件，并重写 <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> 方法。 调用的基实现 <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> ，并查询 <xref:System.ComponentModel.Design.IComponentChangeService> 。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. 实现 <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> 事件处理程序。 测试发送组件的类型，如果它是 `IMarqueeWidget` ，则调用其 <xref:System.Windows.Forms.Control.Refresh%2A> 方法。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="add-designer-verbs-to-your-custom-designer"></a>将设计器谓词添加到自定义设计器

设计器谓词是与事件处理程序链接的菜单命令。 设计器谓词在设计时添加到组件的快捷菜单中。 有关详细信息，请参阅 <xref:System.ComponentModel.Design.DesignerVerb>。

你将向设计器添加两个设计器谓词：**运行测试**和**停止测试**。 这些谓词允许您在设计时查看的运行时行为 `MarqueeControl` 。 这些谓词将添加到 `MarqueeControlRootDesigner` 。

调用 "**运行测试**" 时，verb 事件处理程序将对调用 `StartMarquee` 方法 `MarqueeControl` 。 调用**停止测试**时，verb 事件处理程序将对调用 `StopMarquee` 方法 `MarqueeControl` 。 和方法的实现 `StartMarquee` `StopMarquee` 在实现的包含控件上调用这些方法 `IMarqueeWidget` ，因此任何包含 `IMarqueeWidget` 的控件也将参与测试。

### <a name="to-add-designer-verbs-to-your-custom-designers"></a>将设计器谓词添加到自定义设计器

1. 在 `MarqueeControlRootDesigner` 类中，添加名为和的事件处理程序 `OnVerbRunTest` `OnVerbStopTest` 。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. 将这些事件处理程序连接到相应的设计器谓词。 `MarqueeControlRootDesigner`<xref:System.ComponentModel.Design.DesignerVerbCollection>从其基类继承。 您将创建两个新 <xref:System.ComponentModel.Design.DesignerVerb> 的对象，并在方法中将它们添加到此集合中 <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> 。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="create-a-custom-uitypeeditor"></a>创建自定义 UITypeEditor

为用户创建自定义设计时体验时，通常需要创建与属性窗口的自定义交互。 可以通过创建来实现此目的 <xref:System.Drawing.Design.UITypeEditor> 。

`MarqueeBorder`控件公开属性窗口中的多个属性。 其中两个属性， `MarqueeSpinDirection` 由 `MarqueeLightShape` 枚举表示。 为了说明 UI 类型编辑器的用法，该 `MarqueeLightShape` 属性将具有关联的 <xref:System.Drawing.Design.UITypeEditor> 类。

### <a name="to-create-a-custom-ui-type-editor"></a>创建自定义 UI 类型编辑器

1. `MarqueeBorder`在**代码编辑器**中打开源文件。

2. 在类的定义中 `MarqueeBorder` ，声明一个 `LightShapeEditor` 派生自的类 <xref:System.Drawing.Design.UITypeEditor> 。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. 声明一个 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> 名为的实例变量 `editorService` 。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. 重写 <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> 方法。 此实现返回 <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown> ，它指示设计环境如何显示 `LightShapeEditor` 。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. 重写 <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> 方法。 此实现查询对象的设计环境 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> 。 如果成功，它将创建一个 `LightShapeSelectionControl` 。 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A>调用方法来启动 `LightShapeEditor` 。 此调用的返回值将返回到设计环境。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="create-a-view-control-for-your-custom-uitypeeditor"></a>为自定义 UITypeEditor 创建视图控件

`MarqueeLightShape`属性支持两种类型的光源形状： `Square` 和 `Circle` 。 您将创建一个仅用于以图形方式在属性窗口中显示这些值的自定义控件。 此自定义控件将由用于 <xref:System.Drawing.Design.UITypeEditor> 与属性窗口进行交互。

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>为自定义 UI 类型编辑器创建视图控件

1. 向 <xref:System.Windows.Forms.UserControl> 项目中添加新项 `MarqueeControlLibrary` 。 为新的源文件指定基名称**LightShapeSelectionControl**。

2. 将两个 <xref:System.Windows.Forms.Panel> 控件从**工具箱**拖到上 `LightShapeSelectionControl` 。 将它们命名为 `squarePanel` 和 `circlePanel` 。 并排排列它们。 将 <xref:System.Windows.Forms.Control.Size%2A> 这两个控件的属性设置 <xref:System.Windows.Forms.Panel> 为 **（60，60）**。 将 <xref:System.Windows.Forms.Control.Location%2A> 控件的属性设置 `squarePanel` 为 **（8，10）**。 将 <xref:System.Windows.Forms.Control.Location%2A> 控件的属性设置 `circlePanel` 为 **（80，10）**。 最后，将 <xref:System.Windows.Forms.Control.Size%2A> 的属性设置 `LightShapeSelectionControl` 为 **（150，80）**。

3. `LightShapeSelectionControl`在**代码编辑器**中打开源文件。 在该文件的顶部，导入 <xref:System.Windows.Forms.Design?displayProperty=nameWithType> 命名空间：

   ```vb
   Imports System.Windows.Forms.Design
   ```

   ```csharp
   using System.Windows.Forms.Design;
   ```

4. <xref:System.Windows.Forms.Control.Click>为和控件实现事件处理程序 `squarePanel` `circlePanel` 。 这些方法调用 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> 以结束自定义 <xref:System.Drawing.Design.UITypeEditor> 编辑会话。

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

5. 声明一个 <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> 名为的实例变量 `editorService` 。

   ```vb
   Private editorService As IWindowsFormsEditorService
   ```

   ```csharp
   private IWindowsFormsEditorService editorService;
   ```

6. 声明一个 `MarqueeLightShape` 名为的实例变量 `lightShapeValue` 。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

7. 在 `LightShapeSelectionControl` 构造函数中，将 <xref:System.Windows.Forms.Control.Click> 事件处理程序附加到 `squarePanel` 和控件的 `circlePanel` <xref:System.Windows.Forms.Control.Click> 事件。 另外，定义将 `MarqueeLightShape` 设计环境中的值分配给字段的构造函数重载 `lightShapeValue` 。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

8. 在 <xref:System.ComponentModel.Component.Dispose%2A> 方法中，分离 <xref:System.Windows.Forms.Control.Click> 事件处理程序。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

9. 在“解决方案资源管理器”**** 中，单击“显示所有文件”**** 按钮。 打开 LightShapeSelectionControl.Designer.cs 或 LightShapeSelectionControl 文件，并删除该方法的默认定义 <xref:System.ComponentModel.Component.Dispose%2A> 。

10. 实现 `LightShape` 属性。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

11. 重写 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。 此实现将绘制实心正方形和圆圈。 它还将通过在一个形状周围绘制边框来突出显示选定的值。

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="test-your-custom-control-in-the-designer"></a>在设计器中测试自定义控件

此时，您可以生成 `MarqueeControlLibrary` 项目。 通过创建从类继承的控件 `MarqueeControl` 并在窗体上使用它来测试您的实现。

### <a name="to-create-a-custom-marqueecontrol-implementation"></a>创建自定义 MarqueeControl 实现

1. 在 Windows 窗体设计器中打开 `DemoMarqueeControl`。 这会创建类型的实例 `DemoMarqueeControl` ，并将其显示在类型的实例中 `MarqueeControlRootDesigner` 。

2. 在 "**工具箱**" 中，打开 " **MarqueeControlLibrary 组件**" 选项卡。你将看到 `MarqueeBorder` 和 `MarqueeText` 控件可供选择。

3. 将控件的一个实例拖 `MarqueeBorder` 到 `DemoMarqueeControl` 设计图面上。 将此 `MarqueeBorder` 控件停靠到父控件。

4. 将控件的一个实例拖 `MarqueeText` 到 `DemoMarqueeControl` 设计图面上。

5. 生成解决方案。

6. 右键单击 `DemoMarqueeControl` ，然后从快捷菜单中选择 "**运行测试**" 选项以启动动画。 单击 "**停止测试**" 以停止动画。

7. 在设计视图中打开“Form1”****。

8. 将两个 <xref:System.Windows.Forms.Button> 控件置于窗体上。 将它们 `startButton` 命名 `stopButton` 为和，并 <xref:System.Windows.Forms.Control.Text%2A> 分别将属性值更改为 "**启动**" 和 "**停止**"。

9. <xref:System.Windows.Forms.Control.Click>为这两个控件实现事件处理程序 <xref:System.Windows.Forms.Button> 。

10. 在 "**工具箱**" 中，打开 " **MarqueeControlTest 组件**" 选项卡。你将看到 `DemoMarqueeControl` 可供选择。

11. 将的一个实例拖 `DemoMarqueeControl` 到**Form1**设计图面上。

12. 在 <xref:System.Windows.Forms.Control.Click> 事件处理程序中，调用 `Start` 上的和 `Stop` 方法 `DemoMarqueeControl` 。

    ```vb
    Private Sub startButton_Click(sender As Object, e As System.EventArgs)
        Me.demoMarqueeControl1.Start()
    End Sub 'startButton_Click

    Private Sub stopButton_Click(sender As Object, e As System.EventArgs)
    Me.demoMarqueeControl1.Stop()
    End Sub 'stopButton_Click
    ```

    ```csharp
    private void startButton_Click(object sender, System.EventArgs e)
    {
        this.demoMarqueeControl1.Start();
    }

    private void stopButton_Click(object sender, System.EventArgs e)
    {
        this.demoMarqueeControl1.Stop();
    }
    ```

13. 将 `MarqueeControlTest` 项目设置为 "启动项目" 并运行该项目。 你将看到显示的窗体 `DemoMarqueeControl` 。 选择 "**启动**" 按钮以启动动画。 应会看到文本闪烁，而灯光在边框上移动。

## <a name="next-steps"></a>后续步骤

`MarqueeControlLibrary`演示自定义控件和关联设计器的简单实现。 可以通过多种方式使此示例更加复杂：

- `DemoMarqueeControl`在设计器中更改的属性值。 添加更多 `MarqueBorder` 控件并将它们停靠在其父实例中以创建嵌套效果。 试验的不同设置以及与 `UpdatePeriod` 光源相关的属性。

- 创作自己的实现 `IMarqueeWidget` 。 例如，可以创建一个闪烁的 "霓虹灯号" 或包含多个图像的动画符号。

- 进一步自定义设计时体验。 您可以尝试隐藏比和更 <xref:System.Windows.Forms.Control.Enabled%2A> 多 <xref:System.Windows.Forms.Control.Visible%2A> 的属性，并且可以添加新属性。 添加新的设计器谓词以简化诸如停靠子控件等常见任务。

- 许可 `MarqueeControl` 。

- 控制如何序列化控件，以及如何为控件生成代码。 有关详细信息，请参阅[动态源代码生成和编译](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)。

## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
