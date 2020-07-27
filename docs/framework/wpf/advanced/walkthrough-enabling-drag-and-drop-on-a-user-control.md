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
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="617b4-103">演练：在用户控件上启用拖放功能</span><span class="sxs-lookup"><span data-stu-id="617b4-103">Walkthrough: Enabling Drag and Drop on a User Control</span></span>

<span data-ttu-id="617b4-104">本演练演示如何创建可在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中参与拖放数据传输的自定义用户控件。</span><span class="sxs-lookup"><span data-stu-id="617b4-104">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>

<span data-ttu-id="617b4-105">在本演练中，您将创建一个 <xref:System.Windows.Controls.UserControl> 表示圆形形状的自定义 WPF。</span><span class="sxs-lookup"><span data-stu-id="617b4-105">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="617b4-106">你将在该控件上实现可通过拖放进行数据传输的功能。</span><span class="sxs-lookup"><span data-stu-id="617b4-106">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="617b4-107">例如，如果从一个圆形控件拖到另一个圆形控件，则会将填充颜色数据从源圆形复制到目标圆形。</span><span class="sxs-lookup"><span data-stu-id="617b4-107">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="617b4-108">如果从圆圈控件拖动到 <xref:System.Windows.Controls.TextBox> ，则填充颜色的字符串表示形式将复制到 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-108">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="617b4-109">你还将创建一个包含两个 panel 控件的小型应用程序和一个 <xref:System.Windows.Controls.TextBox> 用于测试拖放功能的。</span><span class="sxs-lookup"><span data-stu-id="617b4-109">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="617b4-110">你将编写可使面板处理放置的圆形数据的代码，这样就可以将圆形从一个面板的 Children 集合移动或复制到其他面板。</span><span class="sxs-lookup"><span data-stu-id="617b4-110">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>

<span data-ttu-id="617b4-111">本演练阐释了以下任务：</span><span class="sxs-lookup"><span data-stu-id="617b4-111">This walkthrough illustrates the following tasks:</span></span>

- <span data-ttu-id="617b4-112">创建自定义用户控件。</span><span class="sxs-lookup"><span data-stu-id="617b4-112">Create a custom user control.</span></span>

- <span data-ttu-id="617b4-113">使用户控件成为拖动源。</span><span class="sxs-lookup"><span data-stu-id="617b4-113">Enable the user control to be a drag source.</span></span>

- <span data-ttu-id="617b4-114">使用户控件成为拖放目标。</span><span class="sxs-lookup"><span data-stu-id="617b4-114">Enable the user control to be a drop target.</span></span>

- <span data-ttu-id="617b4-115">使面板能够接收用户控件中放置的数据。</span><span class="sxs-lookup"><span data-stu-id="617b4-115">Enable a panel to receive data dropped from the user control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="617b4-116">先决条件</span><span class="sxs-lookup"><span data-stu-id="617b4-116">Prerequisites</span></span>

<span data-ttu-id="617b4-117">若要完成本演练，必须具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="617b4-117">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="617b4-118">创建应用程序项目</span><span class="sxs-lookup"><span data-stu-id="617b4-118">Create the Application Project</span></span>
 <span data-ttu-id="617b4-119">在本部分中，你将创建应用程序基础结构，其中包括一个具有两个面板和的主页 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-119">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>

1. <span data-ttu-id="617b4-120">在 Visual Basic 或 Visual C# 中创建名为 `DragDropExample` 的新 WPF 应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="617b4-120">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="617b4-121">有关详细信息，请参阅[演练：我的第一个 WPF 桌面应用程序](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。</span><span class="sxs-lookup"><span data-stu-id="617b4-121">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

2. <span data-ttu-id="617b4-122">打开 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="617b4-122">Open MainWindow.xaml.</span></span>

3. <span data-ttu-id="617b4-123">在开始标记和结束标记之间添加以下标记 <xref:System.Windows.Controls.Grid> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-123">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>

     <span data-ttu-id="617b4-124">此标记将创建用于测试应用程序的用户界面。</span><span class="sxs-lookup"><span data-stu-id="617b4-124">This markup creates the user interface for the test application.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a><span data-ttu-id="617b4-125">向项目添加新的用户控件</span><span class="sxs-lookup"><span data-stu-id="617b4-125">Add a New User Control to the Project</span></span>
 <span data-ttu-id="617b4-126">本节将介绍如何向项目添加新的用户控件。</span><span class="sxs-lookup"><span data-stu-id="617b4-126">In this section, you will add a new user control to the project.</span></span>

1. <span data-ttu-id="617b4-127">在“项目”菜单中，选择“添加用户控件”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="617b4-127">On the Project menu, select **Add User Control**.</span></span>

2. <span data-ttu-id="617b4-128">在 "**添加新项**" 对话框中，将 "名称" 更改为 `Circle.xaml` ，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="617b4-128">In the **Add New Item** dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>

     <span data-ttu-id="617b4-129">Circle.xaml 及其代码隐藏内容将添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="617b4-129">Circle.xaml and its code-behind is added to the project.</span></span>

3. <span data-ttu-id="617b4-130">打开 Circle.xaml。</span><span class="sxs-lookup"><span data-stu-id="617b4-130">Open Circle.xaml.</span></span>

     <span data-ttu-id="617b4-131">此文件将包含用户控件的用户界面元素。</span><span class="sxs-lookup"><span data-stu-id="617b4-131">This file will contain the user interface elements of the user control.</span></span>

4. <span data-ttu-id="617b4-132">将以下标记添加到根目录 <xref:System.Windows.Controls.Grid> ，以创建一个包含蓝色圆圈作为其 UI 的简单用户控件。</span><span class="sxs-lookup"><span data-stu-id="617b4-132">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. <span data-ttu-id="617b4-133">打开 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="617b4-133">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

6. <span data-ttu-id="617b4-134">在 c # 中，将以下代码添加到无参数构造函数之后，以创建复制构造函数。</span><span class="sxs-lookup"><span data-stu-id="617b4-134">In C#, add the following code after the parameterless constructor to create a copy constructor.</span></span> <span data-ttu-id="617b4-135">在 Visual Basic 中，添加以下代码以创建无参数构造函数和复制构造函数。</span><span class="sxs-lookup"><span data-stu-id="617b4-135">In Visual Basic, add the following code to create both a parameterless constructor and a copy constructor.</span></span>

     <span data-ttu-id="617b4-136">若要允许复制用户控件，需在代码隐藏文件中添加复制构造函数方法。</span><span class="sxs-lookup"><span data-stu-id="617b4-136">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="617b4-137">在简化的圆形用户控件中，将只复制该用户控件的填充和大小。</span><span class="sxs-lookup"><span data-stu-id="617b4-137">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a><span data-ttu-id="617b4-138">向主窗口添加用户控件</span><span class="sxs-lookup"><span data-stu-id="617b4-138">Add the user control to the main window</span></span>

1. <span data-ttu-id="617b4-139">打开 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="617b4-139">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="617b4-140">将以下 XAML 添加到开始 <xref:System.Windows.Window> 标记，以创建对当前应用程序的 XML 命名空间引用。</span><span class="sxs-lookup"><span data-stu-id="617b4-140">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>

    ```xaml
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. <span data-ttu-id="617b4-141">在第一 <xref:System.Windows.Controls.StackPanel> 种情况下，添加以下 XAML 以便在第一个面板中创建 Circle 用户控件的两个实例。</span><span class="sxs-lookup"><span data-stu-id="617b4-141">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     <span data-ttu-id="617b4-142">此面板的完整 XAML 如下所示。</span><span class="sxs-lookup"><span data-stu-id="617b4-142">The full XAML for the panel looks like the following.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a><span data-ttu-id="617b4-143">在用户控件中实现拖动源事件</span><span class="sxs-lookup"><span data-stu-id="617b4-143">Implement Drag Source Events in the User Control</span></span>
 <span data-ttu-id="617b4-144">在本部分中，将重写 <xref:System.Windows.UIElement.OnMouseMove%2A> 方法并启动拖放操作。</span><span class="sxs-lookup"><span data-stu-id="617b4-144">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>

 <span data-ttu-id="617b4-145">如果已启动拖动（按下鼠标按钮并移动鼠标），则会打包要传输到中的数据 <xref:System.Windows.DataObject> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-145">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="617b4-146">在这种情况下，圆形控件将打包三个数据项：其填充颜色的字符串表示形式、其高度的双精度表示形式以及其自身的副本。</span><span class="sxs-lookup"><span data-stu-id="617b4-146">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="617b4-147">启动拖放操作</span><span class="sxs-lookup"><span data-stu-id="617b4-147">To initiate a drag-and-drop operation</span></span>

1. <span data-ttu-id="617b4-148">打开 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="617b4-148">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="617b4-149">添加以下 <xref:System.Windows.UIElement.OnMouseMove%2A> 替代，以便为事件提供类处理 <xref:System.Windows.UIElement.MouseMove> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-149">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     <span data-ttu-id="617b4-150">此 <xref:System.Windows.UIElement.OnMouseMove%2A> 替代执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="617b4-150">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="617b4-151">检查移动鼠标时是否按下了鼠标左键。</span><span class="sxs-lookup"><span data-stu-id="617b4-151">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>

    - <span data-ttu-id="617b4-152">将圆圈数据打包成 <xref:System.Windows.DataObject> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-152">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="617b4-153">在这种情况下，圆形控件将打包三个数据项：其填充颜色的字符串表示形式、其高度的双精度表示形式以及其自身的副本。</span><span class="sxs-lookup"><span data-stu-id="617b4-153">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

    - <span data-ttu-id="617b4-154">调用静态 <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> 方法以启动拖放操作。</span><span class="sxs-lookup"><span data-stu-id="617b4-154">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="617b4-155">将以下三个参数传递给 <xref:System.Windows.DragDrop.DoDragDrop%2A> 方法：</span><span class="sxs-lookup"><span data-stu-id="617b4-155">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>

        - <span data-ttu-id="617b4-156">`dragSource` – 对此控件的引用。</span><span class="sxs-lookup"><span data-stu-id="617b4-156">`dragSource` – A reference to this control.</span></span>

        - <span data-ttu-id="617b4-157">`data`– <xref:System.Windows.DataObject> 在前面的代码中创建的。</span><span class="sxs-lookup"><span data-stu-id="617b4-157">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>

        - <span data-ttu-id="617b4-158">`allowedEffects`–允许的拖放操作，即 <xref:System.Windows.DragDropEffects.Copy> 或 <xref:System.Windows.DragDropEffects.Move> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-158">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="617b4-159">按 F5 生成并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="617b4-159">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="617b4-160">单击其中一个圆圈控件，并将其拖动到面板、另一个圆圈和上 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-160">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="617b4-161">在拖动时 <xref:System.Windows.Controls.TextBox> ，光标会更改以指示移动。</span><span class="sxs-lookup"><span data-stu-id="617b4-161">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>

5. <span data-ttu-id="617b4-162">将圆圈拖动到上时 <xref:System.Windows.Controls.TextBox> ，按**Ctrl**键。</span><span class="sxs-lookup"><span data-stu-id="617b4-162">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the **Ctrl** key.</span></span> <span data-ttu-id="617b4-163">请注意光标是如何更改以指示复制的。</span><span class="sxs-lookup"><span data-stu-id="617b4-163">Notice how the cursor changes to indicate a copy.</span></span>

6. <span data-ttu-id="617b4-164">将一个圆圈拖放到 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-164">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="617b4-165">圆圈填充颜色的字符串表示形式将追加到 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-165">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>

     <span data-ttu-id="617b4-166">![圆的填充颜色的字符串表示形式](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="617b4-166">![String representation of Circle's fill color](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>

<span data-ttu-id="617b4-167">默认情况下，光标会在拖放操作过程中更改，以指示放置数据会产生的效果。</span><span class="sxs-lookup"><span data-stu-id="617b4-167">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="617b4-168">您可以通过处理 <xref:System.Windows.UIElement.GiveFeedback> 事件并设置不同的游标，自定义为用户提供的反馈。</span><span class="sxs-lookup"><span data-stu-id="617b4-168">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>

## <a name="give-feedback-to-the-user"></a><span data-ttu-id="617b4-169">向用户提供反馈</span><span class="sxs-lookup"><span data-stu-id="617b4-169">Give feedback to the user</span></span>

1. <span data-ttu-id="617b4-170">打开 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="617b4-170">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="617b4-171">添加以下 <xref:System.Windows.UIElement.OnGiveFeedback%2A> 替代，以便为事件提供类处理 <xref:System.Windows.UIElement.GiveFeedback> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-171">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     <span data-ttu-id="617b4-172">此 <xref:System.Windows.UIElement.OnGiveFeedback%2A> 替代执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="617b4-172">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="617b4-173">检查 <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> 在放置目标的 <xref:System.Windows.UIElement.DragOver> 事件处理程序中设置的值。</span><span class="sxs-lookup"><span data-stu-id="617b4-173">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

    - <span data-ttu-id="617b4-174">基于值设置自定义光标 <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-174">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="617b4-175">该光标旨在向用户提供关于放置数据所产生的效果的可视反馈。</span><span class="sxs-lookup"><span data-stu-id="617b4-175">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>

3. <span data-ttu-id="617b4-176">按 F5 生成并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="617b4-176">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="617b4-177">将一个圆形控件拖动到面板、另一个圆形和上 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-177">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="617b4-178">请注意，这些游标现在是在重写中指定的自定义游标 <xref:System.Windows.UIElement.OnGiveFeedback%2A> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-178">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>

     <span data-ttu-id="617b4-179">![使用自定义光标拖放](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="617b4-179">![Drag and drop with custom cursors](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>

5. <span data-ttu-id="617b4-180">`green`从中选择文本 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-180">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

6. <span data-ttu-id="617b4-181">将 `green` 文本拖到一个圆形控件上。</span><span class="sxs-lookup"><span data-stu-id="617b4-181">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="617b4-182">请注意，将显示默认光标以指示拖放操作效果。</span><span class="sxs-lookup"><span data-stu-id="617b4-182">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="617b4-183">反馈光标始终由拖动源设置。</span><span class="sxs-lookup"><span data-stu-id="617b4-183">The feedback cursor is always set by the drag source.</span></span>

## <a name="implement-drop-target-events-in-the-user-control"></a><span data-ttu-id="617b4-184">在用户控件中实现放置目标事件</span><span class="sxs-lookup"><span data-stu-id="617b4-184">Implement Drop Target Events in the User Control</span></span>
 <span data-ttu-id="617b4-185">在本节中，你将指定用户控件为拖放目标，替代可使用户控件成为拖放目标的方法，并处理用户控件上放置的数据。</span><span class="sxs-lookup"><span data-stu-id="617b4-185">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="617b4-186">使用户控件成为拖放目标</span><span class="sxs-lookup"><span data-stu-id="617b4-186">To enable the user control to be a drop target</span></span>

1. <span data-ttu-id="617b4-187">打开 Circle.xaml。</span><span class="sxs-lookup"><span data-stu-id="617b4-187">Open Circle.xaml.</span></span>

2. <span data-ttu-id="617b4-188">在开始 <xref:System.Windows.Controls.UserControl> 标记中，添加 <xref:System.Windows.UIElement.AllowDrop%2A> 属性，并将其设置为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="617b4-188">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<span data-ttu-id="617b4-189"><xref:System.Windows.UIElement.OnDrop%2A>当 <xref:System.Windows.UIElement.AllowDrop%2A> 属性设置为 `true` ，并将拖动源中的数据放置在圆形用户控件上时，将调用方法。</span><span class="sxs-lookup"><span data-stu-id="617b4-189">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="617b4-190">在这种方法中，将处理已放置的数据，并将这些数据应用于圆形。</span><span class="sxs-lookup"><span data-stu-id="617b4-190">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>

### <a name="to-process-the-dropped-data"></a><span data-ttu-id="617b4-191">处理已放置的数据</span><span class="sxs-lookup"><span data-stu-id="617b4-191">To process the dropped data</span></span>

1. <span data-ttu-id="617b4-192">打开 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="617b4-192">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="617b4-193">添加以下 <xref:System.Windows.UIElement.OnDrop%2A> 替代，以便为事件提供类处理 <xref:System.Windows.UIElement.Drop> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-193">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     <span data-ttu-id="617b4-194">此 <xref:System.Windows.UIElement.OnDrop%2A> 替代执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="617b4-194">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="617b4-195">使用 <xref:System.Windows.DataObject.GetDataPresent%2A> 方法检查拖动后的数据是否包含字符串对象。</span><span class="sxs-lookup"><span data-stu-id="617b4-195">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>

    - <span data-ttu-id="617b4-196">使用 <xref:System.Windows.DataObject.GetData%2A> 方法提取字符串数据（如果存在）。</span><span class="sxs-lookup"><span data-stu-id="617b4-196">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>

    - <span data-ttu-id="617b4-197">使用 <xref:System.Windows.Media.BrushConverter> 尝试将字符串转换为 <xref:System.Windows.Media.Brush> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-197">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="617b4-198">如果转换成功，则将画笔应用于 <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> 提供 Circle 控件的 UI 的的。</span><span class="sxs-lookup"><span data-stu-id="617b4-198">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>

    - <span data-ttu-id="617b4-199">将 <xref:System.Windows.UIElement.Drop> 事件标记为已处理。</span><span class="sxs-lookup"><span data-stu-id="617b4-199">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="617b4-200">应将放置事件标记为已处理，这样接收此事件的其他元素才会知道圆形用户控件已处理了该事件。</span><span class="sxs-lookup"><span data-stu-id="617b4-200">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>

3. <span data-ttu-id="617b4-201">按 F5 生成并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="617b4-201">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="617b4-202">选择中的文本 `green` <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-202">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="617b4-203">将文本拖放到一个圆形控件上。</span><span class="sxs-lookup"><span data-stu-id="617b4-203">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="617b4-204">该圆形会从蓝色变为绿色。</span><span class="sxs-lookup"><span data-stu-id="617b4-204">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="617b4-205">![将字符串转换为画笔](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="617b4-205">![Convert a string to a brush](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>

6. <span data-ttu-id="617b4-206">键入中的文本 `green` <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-206">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="617b4-207">选择中的文本 `gre` <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-207">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="617b4-208">将其拖放到一个圆形控件上。</span><span class="sxs-lookup"><span data-stu-id="617b4-208">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="617b4-209">请注意，光标会更改以指示允许放置，但圆形的颜色不会更改，因为 `gre` 不是有效颜色。</span><span class="sxs-lookup"><span data-stu-id="617b4-209">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>

9. <span data-ttu-id="617b4-210">从绿色圆形控件拖放到蓝色圆形控件。</span><span class="sxs-lookup"><span data-stu-id="617b4-210">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="617b4-211">该圆形会从蓝色变为绿色。</span><span class="sxs-lookup"><span data-stu-id="617b4-211">The Circle changes from blue to green.</span></span> <span data-ttu-id="617b4-212">请注意，显示哪个光标取决于 <xref:System.Windows.Controls.TextBox> 或圆形是否为拖动源。</span><span class="sxs-lookup"><span data-stu-id="617b4-212">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>

<span data-ttu-id="617b4-213">将 <xref:System.Windows.UIElement.AllowDrop%2A> 属性设置为 `true` 并处理删除的数据是使元素成为放置目标所需的全部。</span><span class="sxs-lookup"><span data-stu-id="617b4-213">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="617b4-214">但是，若要提供更好的用户体验，还应处理 <xref:System.Windows.UIElement.DragEnter> 、 <xref:System.Windows.UIElement.DragLeave> 和 <xref:System.Windows.UIElement.DragOver> 事件。</span><span class="sxs-lookup"><span data-stu-id="617b4-214">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="617b4-215">在这些事件中，你可以在放置数据前执行检查并向用户提供其他反馈。</span><span class="sxs-lookup"><span data-stu-id="617b4-215">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>

<span data-ttu-id="617b4-216">将数据拖动到圆形用户控件上时，该控件应通知拖动源它是否可以处理所拖动的数据。</span><span class="sxs-lookup"><span data-stu-id="617b4-216">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="617b4-217">如果该控件不知如何处理这些数据，则它应拒绝放置。</span><span class="sxs-lookup"><span data-stu-id="617b4-217">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="617b4-218">为此，您将处理 <xref:System.Windows.UIElement.DragOver> 事件并设置 <xref:System.Windows.DragEventArgs.Effects%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="617b4-218">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>

### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="617b4-219">验证是否允许数据放置</span><span class="sxs-lookup"><span data-stu-id="617b4-219">To verify that the data drop is allowed</span></span>

1. <span data-ttu-id="617b4-220">打开 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="617b4-220">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="617b4-221">添加以下 <xref:System.Windows.UIElement.OnDragOver%2A> 替代，以便为事件提供类处理 <xref:System.Windows.UIElement.DragOver> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-221">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     <span data-ttu-id="617b4-222">此 <xref:System.Windows.UIElement.OnDragOver%2A> 替代执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="617b4-222">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="617b4-223">将 <xref:System.Windows.DragEventArgs.Effects%2A> 属性设置为 <xref:System.Windows.DragDropEffects.None>。</span><span class="sxs-lookup"><span data-stu-id="617b4-223">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>

    - <span data-ttu-id="617b4-224">执行在方法中执行的相同检查， <xref:System.Windows.UIElement.OnDrop%2A> 以确定 Circle 用户控件是否可以处理拖动的数据。</span><span class="sxs-lookup"><span data-stu-id="617b4-224">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>

    - <span data-ttu-id="617b4-225">如果用户控件可以处理数据，则将属性设置 <xref:System.Windows.DragEventArgs.Effects%2A> 为 <xref:System.Windows.DragDropEffects.Copy> 或 <xref:System.Windows.DragDropEffects.Move> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-225">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="617b4-226">按 F5 生成并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="617b4-226">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="617b4-227">选择中的文本 `gre` <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-227">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="617b4-228">将文本拖到一个圆形控件上。</span><span class="sxs-lookup"><span data-stu-id="617b4-228">Drag the text to a Circle control.</span></span> <span data-ttu-id="617b4-229">请注意，光标此时会更改以指示不允许放置，因为 `gre` 不是有效颜色。</span><span class="sxs-lookup"><span data-stu-id="617b4-229">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>

 <span data-ttu-id="617b4-230">可通过应用拖放操作预览进一步增强用户体验。</span><span class="sxs-lookup"><span data-stu-id="617b4-230">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="617b4-231">对于圆圈用户控件，将重写 <xref:System.Windows.UIElement.OnDragEnter%2A> 和 <xref:System.Windows.UIElement.OnDragLeave%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="617b4-231">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="617b4-232">将数据拖动到控件上方时，当前背景 <xref:System.Windows.Shapes.Shape.Fill%2A> 将保存在占位符变量中。</span><span class="sxs-lookup"><span data-stu-id="617b4-232">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="617b4-233">然后，将该字符串转换为画笔，并将其应用于 <xref:System.Windows.Shapes.Ellipse> 提供圆形 UI 的。</span><span class="sxs-lookup"><span data-stu-id="617b4-233">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="617b4-234">如果在不删除数据的情况下将数据拖出圆圈，则 <xref:System.Windows.Shapes.Shape.Fill%2A> 会将原始值重新应用于该圆形。</span><span class="sxs-lookup"><span data-stu-id="617b4-234">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="617b4-235">预览拖放操作的效果</span><span class="sxs-lookup"><span data-stu-id="617b4-235">To preview the effects of the drag-and-drop operation</span></span>

1. <span data-ttu-id="617b4-236">打开 Circle.xaml.cs 或 Circle.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="617b4-236">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="617b4-237">在 Circle 类中，声明一个 <xref:System.Windows.Media.Brush> 名为的私有变量 `_previousFill` ，并将其初始化为 `null` 。</span><span class="sxs-lookup"><span data-stu-id="617b4-237">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. <span data-ttu-id="617b4-238">添加以下 <xref:System.Windows.UIElement.OnDragEnter%2A> 替代，以便为事件提供类处理 <xref:System.Windows.UIElement.DragEnter> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-238">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     <span data-ttu-id="617b4-239">此 <xref:System.Windows.UIElement.OnDragEnter%2A> 替代执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="617b4-239">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="617b4-240"><xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> 在变量中保存的属性 `_previousFill` 。</span><span class="sxs-lookup"><span data-stu-id="617b4-240">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>

    - <span data-ttu-id="617b4-241">执行在方法中执行的相同检查， <xref:System.Windows.UIElement.OnDrop%2A> 以确定是否可以将数据转换为 <xref:System.Windows.Media.Brush> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-241">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="617b4-242">如果数据转换为有效 <xref:System.Windows.Media.Brush> ，则将其应用于 <xref:System.Windows.Shapes.Shape.Fill%2A> 的 <xref:System.Windows.Shapes.Ellipse> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-242">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>

4. <span data-ttu-id="617b4-243">添加以下 <xref:System.Windows.UIElement.OnDragLeave%2A> 替代，以便为事件提供类处理 <xref:System.Windows.UIElement.DragLeave> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-243">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     <span data-ttu-id="617b4-244">此 <xref:System.Windows.UIElement.OnDragLeave%2A> 替代执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="617b4-244">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="617b4-245">将 <xref:System.Windows.Media.Brush> 变量中保存的 `_previousFill` 保存到 <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> 提供 CIRCLE 用户控件的 UI 的的。</span><span class="sxs-lookup"><span data-stu-id="617b4-245">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>

5. <span data-ttu-id="617b4-246">按 F5 生成并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="617b4-246">Press **F5** to build and run the application.</span></span>

6. <span data-ttu-id="617b4-247">选择中的文本 `green` <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-247">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="617b4-248">将该文本拖到一个圆形控件上而不放置。</span><span class="sxs-lookup"><span data-stu-id="617b4-248">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="617b4-249">该圆形会从蓝色变为绿色。</span><span class="sxs-lookup"><span data-stu-id="617b4-249">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="617b4-250">![预览拖动&#45;和&#45;拖放操作的效果](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="617b4-250">![Preview the effects of a drag&#45;and&#45;drop operation](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>

8. <span data-ttu-id="617b4-251">将文本拖离该圆形控件。</span><span class="sxs-lookup"><span data-stu-id="617b4-251">Drag the text away from the Circle control.</span></span> <span data-ttu-id="617b4-252">该圆形会从绿色变回蓝色。</span><span class="sxs-lookup"><span data-stu-id="617b4-252">The Circle changes from green back to blue.</span></span>

## <a name="enable-a-panel-to-receive-dropped-data"></a><span data-ttu-id="617b4-253">启用面板以接收已删除的数据</span><span class="sxs-lookup"><span data-stu-id="617b4-253">Enable a Panel to Receive Dropped Data</span></span>

<span data-ttu-id="617b4-254">在本部分中，将启用承载圆圈用户控件的面板，使其充当拖动的圆形数据的拖放目标。</span><span class="sxs-lookup"><span data-stu-id="617b4-254">In this section, you enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="617b4-255">您将实现代码，使您可以将一个圆形从一个面板移动到另一个面板，或通过按住**Ctrl**键的同时拖动和放置圆圈来创建圆形控件的副本。</span><span class="sxs-lookup"><span data-stu-id="617b4-255">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the **Ctrl** key while dragging and dropping a Circle.</span></span>

1. <span data-ttu-id="617b4-256">打开 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="617b4-256">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="617b4-257">如下面的 XAML 中所示，在每个 <xref:System.Windows.Controls.StackPanel> 控件中，为和事件添加处理程序 <xref:System.Windows.UIElement.DragOver> <xref:System.Windows.UIElement.Drop> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-257">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="617b4-258">将 <xref:System.Windows.UIElement.DragOver> 事件处理程序命名为， `panel_DragOver` 并将 <xref:System.Windows.UIElement.Drop> 事件命名为 `panel_Drop` 。</span><span class="sxs-lookup"><span data-stu-id="617b4-258">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. <span data-ttu-id="617b4-259">打开 MainWindows.xaml.cs 或 MainWindow.xaml.vb。</span><span class="sxs-lookup"><span data-stu-id="617b4-259">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>

4. <span data-ttu-id="617b4-260">为 <xref:System.Windows.UIElement.DragOver> 事件处理程序添加以下代码。</span><span class="sxs-lookup"><span data-stu-id="617b4-260">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     <span data-ttu-id="617b4-261">此 <xref:System.Windows.UIElement.DragOver> 事件处理程序执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="617b4-261">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="617b4-262">检查拖动后的数据是否包含 "对象" 数据，该数据 <xref:System.Windows.DataObject> 由圆圈用户控件打包并传入对的调用 <xref:System.Windows.DragDrop.DoDragDrop%2A> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-262">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>

    - <span data-ttu-id="617b4-263">如果存在 "对象" 数据，则检查是否按下了**Ctrl**键。</span><span class="sxs-lookup"><span data-stu-id="617b4-263">If the "Object" data is present, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="617b4-264">如果按下了**Ctrl**键，则将 <xref:System.Windows.DragEventArgs.Effects%2A> 属性设置为 <xref:System.Windows.DragDropEffects.Copy> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-264">If the **Ctrl** key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="617b4-265">否则，请将 <xref:System.Windows.DragEventArgs.Effects%2A> 属性设置为 <xref:System.Windows.DragDropEffects.Move> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-265">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>

5. <span data-ttu-id="617b4-266">为 <xref:System.Windows.UIElement.Drop> 事件处理程序添加以下代码。</span><span class="sxs-lookup"><span data-stu-id="617b4-266">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     <span data-ttu-id="617b4-267">此 <xref:System.Windows.UIElement.Drop> 事件处理程序执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="617b4-267">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="617b4-268">检查是否已 <xref:System.Windows.UIElement.Drop> 处理事件。</span><span class="sxs-lookup"><span data-stu-id="617b4-268">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="617b4-269">例如，如果在处理事件的另一个圆上放置一个圆圈 <xref:System.Windows.UIElement.Drop> ，则不希望包含该圆圈的面板也处理该事件。</span><span class="sxs-lookup"><span data-stu-id="617b4-269">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>

    - <span data-ttu-id="617b4-270">如果 <xref:System.Windows.UIElement.Drop> 未处理该事件，将检查是否按下了**Ctrl**键。</span><span class="sxs-lookup"><span data-stu-id="617b4-270">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="617b4-271">如果在发生此情况时按下**Ctrl**键，则将 <xref:System.Windows.UIElement.Drop> 生成圆圈控件的副本，并将其添加到 <xref:System.Windows.Controls.Panel.Children%2A> 的集合中 <xref:System.Windows.Controls.StackPanel> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-271">If the **Ctrl** key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>

    - <span data-ttu-id="617b4-272">如果未按下**Ctrl**键，则将圆圈从 <xref:System.Windows.Controls.Panel.Children%2A> 其父面板的集合移动到 <xref:System.Windows.Controls.Panel.Children%2A> 拖放到的面板的集合中。</span><span class="sxs-lookup"><span data-stu-id="617b4-272">If the **Ctrl** key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>

    - <span data-ttu-id="617b4-273">设置 <xref:System.Windows.DragEventArgs.Effects%2A> 属性以通知 <xref:System.Windows.DragDrop.DoDragDrop%2A> 方法是否执行了移动或复制操作。</span><span class="sxs-lookup"><span data-stu-id="617b4-273">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>

6. <span data-ttu-id="617b4-274">按 F5 生成并运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="617b4-274">Press **F5** to build and run the application.</span></span>

7. <span data-ttu-id="617b4-275">`green`从中选择文本 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="617b4-275">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="617b4-276">将文本拖放到一个圆形控件上。</span><span class="sxs-lookup"><span data-stu-id="617b4-276">Drag the text over a Circle control and drop it.</span></span>

9. <span data-ttu-id="617b4-277">将一个圆形控件从左面板拖放到右面板。</span><span class="sxs-lookup"><span data-stu-id="617b4-277">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="617b4-278">将从左侧面板的集合中删除该圆形 <xref:System.Windows.Controls.Panel.Children%2A> ，并将其添加到右侧面板的 "子项" 集合中。</span><span class="sxs-lookup"><span data-stu-id="617b4-278">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>

10. <span data-ttu-id="617b4-279">将一个圆形控件从它所在的面板拖动到另一个面板，按**Ctrl**键。</span><span class="sxs-lookup"><span data-stu-id="617b4-279">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the **Ctrl** key.</span></span> <span data-ttu-id="617b4-280">复制圆圈，并将副本添加到 <xref:System.Windows.Controls.Panel.Children%2A> 接收面板的集合中。</span><span class="sxs-lookup"><span data-stu-id="617b4-280">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>

     <span data-ttu-id="617b4-281">![按住 Ctrl 键的同时拖动圆形](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="617b4-281">![Dragging a Circle while pressing the CTRL key](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>

## <a name="see-also"></a><span data-ttu-id="617b4-282">另请参阅</span><span class="sxs-lookup"><span data-stu-id="617b4-282">See also</span></span>

- [<span data-ttu-id="617b4-283">拖放概述</span><span class="sxs-lookup"><span data-stu-id="617b4-283">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
