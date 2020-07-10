---
title: 演练：使用设计器创建带有 ListView 和 TreeView 控件的资源管理器样式界面
description: 了解如何使用设计器创建具有 Windows 窗体 ListView 和 TreeView 控件的资源管理器样式界面。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Explorer-style applications [Windows Forms], walkthroughs
- TreeView control [Windows Forms], ListView controls used with
- ListView control [Windows Forms], TreeView controls used with
- Explorer-style applications
- TreeView control [Windows Forms], using for explorer-style interface
- ListView control [Windows Forms], explorer style interface
- ListView control [Windows Forms], explorer-style interface
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
ms.openlocfilehash: 44d4db1ef3da85dbf411498f486882b86a05c140
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174622"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a><span data-ttu-id="4d90b-103">演练：使用设计器创建带有 ListView 和 TreeView 控件的资源管理器样式界面</span><span class="sxs-lookup"><span data-stu-id="4d90b-103">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>

<span data-ttu-id="4d90b-104">Visual Studio 的一个优点是，可以在短时间内创建专业外观的 Windows 窗体应用程序。</span><span class="sxs-lookup"><span data-stu-id="4d90b-104">One of the benefits of Visual Studio is the ability to create professional-looking Windows Forms applications in a short of amount of time.</span></span> <span data-ttu-id="4d90b-105">常见的方案是使用与 <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.TreeView> windows 操作系统的 Windows 资源管理器功能类似的和控件创建 (UI) 的用户界面。</span><span class="sxs-lookup"><span data-stu-id="4d90b-105">A common scenario is creating a user interface (UI) with <xref:System.Windows.Forms.ListView> and <xref:System.Windows.Forms.TreeView> controls that resembles the Windows Explorer feature of Windows operating systems.</span></span> <span data-ttu-id="4d90b-106">Windows 资源管理器显示用户计算机上的文件和文件夹的层次结构。</span><span class="sxs-lookup"><span data-stu-id="4d90b-106">Windows Explorer displays a hierarchical structure of the files and folders on a user's computer.</span></span>

### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a><span data-ttu-id="4d90b-107">创建包含 ListView 和 TreeView 控件的窗体</span><span class="sxs-lookup"><span data-stu-id="4d90b-107">To create the form containing a ListView and TreeView control</span></span>

1. <span data-ttu-id="4d90b-108">在 **“文件”** 菜单上，指向 **“新建”**，再单击 **“项目”**。</span><span class="sxs-lookup"><span data-stu-id="4d90b-108">On the **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="4d90b-109">在“新建项目”\*\*\*\* 对话框中执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="4d90b-109">In the **New Project** dialog box, do the following:</span></span>

    1. <span data-ttu-id="4d90b-110">在 "类别" 中，选择 " **Visual Basic** " 或 " **Visual c #**"。</span><span class="sxs-lookup"><span data-stu-id="4d90b-110">In the categories, choose either **Visual Basic** or **Visual C#**.</span></span>

    2. <span data-ttu-id="4d90b-111">在模板列表中，选择 " **Windows 窗体应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="4d90b-111">In the list of templates, choose **Windows Forms Application**.</span></span>

3. <span data-ttu-id="4d90b-112">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="4d90b-112">Click **OK**.</span></span> <span data-ttu-id="4d90b-113">这将创建一个新的 Windows 窗体项目。</span><span class="sxs-lookup"><span data-stu-id="4d90b-113">A new Windows Forms project is created.</span></span>

4. <span data-ttu-id="4d90b-114">向 <xref:System.Windows.Forms.SplitContainer> 窗体添加一个控件，并将 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 其属性设置为 <xref:System.Windows.Forms.DockStyle.Fill> 。</span><span class="sxs-lookup"><span data-stu-id="4d90b-114">Add a <xref:System.Windows.Forms.SplitContainer> control to the form and set its <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

5. <span data-ttu-id="4d90b-115">向 <xref:System.Windows.Forms.ImageList> 窗体添加一个名为 `imageList1` 的，并使用属性窗口按顺序添加两个图像：文件夹图像和文档图像。</span><span class="sxs-lookup"><span data-stu-id="4d90b-115">Add an <xref:System.Windows.Forms.ImageList> named `imageList1` to the form and use the Properties window to add two images: a folder image and a document image, in that order.</span></span>

6. <span data-ttu-id="4d90b-116">向 <xref:System.Windows.Forms.TreeView> 窗体添加一个名为 `treeview1` 的控件，并将其定位在控件的左侧 <xref:System.Windows.Forms.SplitContainer> 。</span><span class="sxs-lookup"><span data-stu-id="4d90b-116">Add a <xref:System.Windows.Forms.TreeView> control named `treeview1` to the form, and position it on the left side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="4d90b-117">在属性窗口中， `treeView1` 执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="4d90b-117">In the Properties window for `treeView1` do the following:</span></span>

    1. <span data-ttu-id="4d90b-118">将 <xref:System.Windows.Forms.Control.Dock%2A> 属性设置为 <xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="4d90b-118">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    2. <span data-ttu-id="4d90b-119">将 <xref:System.Windows.Forms.TreeView.ImageList%2A> 属性设置为 `imagelist1.`</span><span class="sxs-lookup"><span data-stu-id="4d90b-119">Set the <xref:System.Windows.Forms.TreeView.ImageList%2A> property to `imagelist1.`</span></span>

7. <span data-ttu-id="4d90b-120">向 <xref:System.Windows.Forms.ListView> 窗体添加一个名为 `listView1` 的控件，并将其定位在控件的右侧 <xref:System.Windows.Forms.SplitContainer> 。</span><span class="sxs-lookup"><span data-stu-id="4d90b-120">Add a <xref:System.Windows.Forms.ListView> control named `listView1` to the form, and position it on the right side of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="4d90b-121">在属性窗口中， `listview1` 执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="4d90b-121">In the Properties window for `listview1` do the following:</span></span>

    1. <span data-ttu-id="4d90b-122">将 <xref:System.Windows.Forms.Control.Dock%2A> 属性设置为 <xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="4d90b-122">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    2. <span data-ttu-id="4d90b-123">将 <xref:System.Windows.Forms.ListView.View%2A> 属性设置为 <xref:System.Windows.Forms.View.Details>。</span><span class="sxs-lookup"><span data-stu-id="4d90b-123">Set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>

    3. <span data-ttu-id="4d90b-124">通过 ![ 在 Visual Studio 的属性窗口中单击省略号按钮 ( ... )  (省略号按钮打开 "ColumnHeader 集合编辑器"。 ](./media/visual-studio-ellipsis-button.png)) 在 <xref:System.Windows.Forms.ListView.Columns%2A> 属性 **.** 中。</span><span class="sxs-lookup"><span data-stu-id="4d90b-124">Open the ColumnHeader Collection Editor by clicking the ellipses (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) in the <xref:System.Windows.Forms.ListView.Columns%2A> property **.**</span></span> <span data-ttu-id="4d90b-125">添加三列，并分别将其 <xref:System.Windows.Forms.ColumnHeader.Text%2A> 属性设置为 `Name` 、 `Type` 和 `Last Modified` 。</span><span class="sxs-lookup"><span data-stu-id="4d90b-125">Add three columns and set their <xref:System.Windows.Forms.ColumnHeader.Text%2A> property to `Name`, `Type`, and `Last Modified`, respectively.</span></span> <span data-ttu-id="4d90b-126">单击“确定”  关闭对话框。</span><span class="sxs-lookup"><span data-stu-id="4d90b-126">Click **OK** to close the dialog box.</span></span>

    4. <span data-ttu-id="4d90b-127">将 <xref:System.Windows.Forms.ListView.SmallImageList%2A> 属性设置为 `imageList1.`</span><span class="sxs-lookup"><span data-stu-id="4d90b-127">Set the <xref:System.Windows.Forms.ListView.SmallImageList%2A> property to `imageList1.`</span></span>

8. <span data-ttu-id="4d90b-128">实现代码以 <xref:System.Windows.Forms.TreeView> 用节点和子节点填充。</span><span class="sxs-lookup"><span data-stu-id="4d90b-128">Implement the code to populate the <xref:System.Windows.Forms.TreeView> with nodes and subnodes.</span></span> <span data-ttu-id="4d90b-129">将此代码添加到 `Form1` 类。</span><span class="sxs-lookup"><span data-stu-id="4d90b-129">Add this code to the `Form1` class.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]

9. <span data-ttu-id="4d90b-130">由于前面的代码使用 System.IO 命名空间，因此请在窗体顶部添加适当的 using 或 import 语句。</span><span class="sxs-lookup"><span data-stu-id="4d90b-130">Since the previous code uses the System.IO namespace, add the appropriate using or import statement at the top of the form.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]

10. <span data-ttu-id="4d90b-131">在窗体的构造函数或事件处理方法中，调用上一步中的设置方法 <xref:System.Windows.Forms.Form.Load> 。</span><span class="sxs-lookup"><span data-stu-id="4d90b-131">Call the set-up method from the previous step in the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span> <span data-ttu-id="4d90b-132">将此代码添加到窗体构造函数中。</span><span class="sxs-lookup"><span data-stu-id="4d90b-132">Add this code to the form constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]

11. <span data-ttu-id="4d90b-133">处理的 <xref:System.Windows.Forms.TreeView.NodeMouseClick> 事件 `treeview1` **，** 并在单击节点时实现代码以填充 `listview1` 节点的内容。</span><span class="sxs-lookup"><span data-stu-id="4d90b-133">Handle the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event for `treeview1`**,** and implement the code to populate `listview1` with a node's contents when a node is clicked.</span></span> <span data-ttu-id="4d90b-134">将此代码添加到 `Form1` 类。</span><span class="sxs-lookup"><span data-stu-id="4d90b-134">Add this code to the `Form1` class.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]

     <span data-ttu-id="4d90b-135">如果使用的是 c #，请确保事件与其 <xref:System.Windows.Forms.TreeView.NodeMouseClick> 事件处理方法关联。</span><span class="sxs-lookup"><span data-stu-id="4d90b-135">If you are using C#, make sure you have the <xref:System.Windows.Forms.TreeView.NodeMouseClick> event associated with its event-handling method.</span></span> <span data-ttu-id="4d90b-136">将此代码添加到窗体构造函数中。</span><span class="sxs-lookup"><span data-stu-id="4d90b-136">Add this code to the form constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]

## <a name="testing-the-application"></a><span data-ttu-id="4d90b-137">测试应用程序</span><span class="sxs-lookup"><span data-stu-id="4d90b-137">Testing the Application</span></span>

<span data-ttu-id="4d90b-138">你现在可以对窗体进行测试，以确保它按预期方式运行。</span><span class="sxs-lookup"><span data-stu-id="4d90b-138">You can now test the form to make sure it behaves as expected.</span></span>

#### <a name="to-test-the-form"></a><span data-ttu-id="4d90b-139">测试窗体</span><span class="sxs-lookup"><span data-stu-id="4d90b-139">To test the form</span></span>

- <span data-ttu-id="4d90b-140">按 F5 运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="4d90b-140">Press F5 to run the application.</span></span>

     <span data-ttu-id="4d90b-141">你将看到一个拆分窗体，该窗体包含一个 <xref:System.Windows.Forms.TreeView> 控件，该控件在左侧显示你的项目目录，在右侧显示一个 <xref:System.Windows.Forms.ListView> 具有三列的控件。</span><span class="sxs-lookup"><span data-stu-id="4d90b-141">You will see a split form containing a <xref:System.Windows.Forms.TreeView> control that displays your project directory on the left side, and a <xref:System.Windows.Forms.ListView> control on the right side with three columns.</span></span> <span data-ttu-id="4d90b-142">您可以 <xref:System.Windows.Forms.TreeView> 通过选择目录节点遍历，并 <xref:System.Windows.Forms.ListView> 使用所选目录的内容进行填充。</span><span class="sxs-lookup"><span data-stu-id="4d90b-142">You can traverse the <xref:System.Windows.Forms.TreeView> by selecting directory nodes, and the <xref:System.Windows.Forms.ListView> is populated with the contents of the selected directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4d90b-143">后续步骤</span><span class="sxs-lookup"><span data-stu-id="4d90b-143">Next Steps</span></span>

<span data-ttu-id="4d90b-144">此应用程序提供了一种使用和控制的方式的示例 <xref:System.Windows.Forms.TreeView> <xref:System.Windows.Forms.ListView> 。</span><span class="sxs-lookup"><span data-stu-id="4d90b-144">This application gives you an example of a way you can use <xref:System.Windows.Forms.TreeView> and <xref:System.Windows.Forms.ListView> controls together.</span></span> <span data-ttu-id="4d90b-145">有关这些控件的详细信息，请参阅以下主题：</span><span class="sxs-lookup"><span data-stu-id="4d90b-145">For more information on these controls, see the following topics:</span></span>

- [<span data-ttu-id="4d90b-146">如何：向 TreeView 或 ListView 控件添加自定义信息（Windows 窗体）</span><span class="sxs-lookup"><span data-stu-id="4d90b-146">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)

- [<span data-ttu-id="4d90b-147">如何：向 ListView 控件添加搜索功能</span><span class="sxs-lookup"><span data-stu-id="4d90b-147">How to: Add Search Capabilities to a ListView Control</span></span>](how-to-add-search-capabilities-to-a-listview-control.md)

- [<span data-ttu-id="4d90b-148">如何：将快捷菜单附加到 TreeView 节点</span><span class="sxs-lookup"><span data-stu-id="4d90b-148">How to: Attach a ShortCut Menu to a TreeView Node</span></span>](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)

## <a name="see-also"></a><span data-ttu-id="4d90b-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4d90b-149">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [<span data-ttu-id="4d90b-150">ListView 控件</span><span class="sxs-lookup"><span data-stu-id="4d90b-150">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="4d90b-151">如何：添加和删除 Windows 窗体 TreeView 控件中的节点</span><span class="sxs-lookup"><span data-stu-id="4d90b-151">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="4d90b-152">如何：使用 Windows 窗体 ListView 控件添加和移除项</span><span class="sxs-lookup"><span data-stu-id="4d90b-152">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [<span data-ttu-id="4d90b-153">如何：向 Windows 窗体 ListView 控件中添加列</span><span class="sxs-lookup"><span data-stu-id="4d90b-153">How to: Add Columns to the Windows Forms ListView Control</span></span>](how-to-add-columns-to-the-windows-forms-listview-control.md)
