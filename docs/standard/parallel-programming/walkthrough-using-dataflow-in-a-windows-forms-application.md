---
title: 演练：在 Windows 窗体应用程序中使用数据流
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
ms.openlocfilehash: 7cd82ffde5fccf938027a6ab6ea15fef226fef6f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288428"
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a><span data-ttu-id="5b95f-102">演练：在 Windows 窗体应用程序中使用数据流</span><span class="sxs-lookup"><span data-stu-id="5b95f-102">Walkthrough: Using Dataflow in a Windows Forms Application</span></span>
<span data-ttu-id="5b95f-103">本文档演示如何创建在 Windows 窗体应用程序中执行图像处理的数据流块网络。</span><span class="sxs-lookup"><span data-stu-id="5b95f-103">This document demonstrates how to create a network of dataflow blocks that perform image processing in a Windows Forms application.</span></span>  
  
 <span data-ttu-id="5b95f-104">此示例从指定的文件夹加载图像文件、创建复合图像，并显示结果。</span><span class="sxs-lookup"><span data-stu-id="5b95f-104">This example loads image files from the specified folder, creates a composite image, and displays the result.</span></span> <span data-ttu-id="5b95f-105">本示例使用数据流模型通过网络路由图像。</span><span class="sxs-lookup"><span data-stu-id="5b95f-105">The example uses the dataflow model to route images through the network.</span></span> <span data-ttu-id="5b95f-106">在数据流模型中，程序的独立组件之间通过发送消息进行通信。</span><span class="sxs-lookup"><span data-stu-id="5b95f-106">In the dataflow model, independent components of a program communicate with one another by sending messages.</span></span> <span data-ttu-id="5b95f-107">某个组件收到一条消息时，它会执行某项操作，然后将结果传递给另一个组件。</span><span class="sxs-lookup"><span data-stu-id="5b95f-107">When a component receives a message, it performs some action and then passes the result to another component.</span></span> <span data-ttu-id="5b95f-108">相比之下，在控制流模型中，应用程序使用控制结构（例如条件语句和循环等等）控制程序中操作的顺序。</span><span class="sxs-lookup"><span data-stu-id="5b95f-108">Compare this with the control flow model, in which an application uses control structures, for example, conditional statements, loops, and so on, to control the order of operations in a program.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5b95f-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="5b95f-109">Prerequisites</span></span>  
 <span data-ttu-id="5b95f-110">开始本演练之前，请阅读[数据流](dataflow-task-parallel-library.md)。</span><span class="sxs-lookup"><span data-stu-id="5b95f-110">Read [Dataflow](dataflow-task-parallel-library.md) before you start this walkthrough.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="sections"></a><span data-ttu-id="5b95f-111">部分</span><span class="sxs-lookup"><span data-stu-id="5b95f-111">Sections</span></span>  
 <span data-ttu-id="5b95f-112">本演练包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="5b95f-112">This walkthrough contains the following sections:</span></span>  
  
- [<span data-ttu-id="5b95f-113">创建 Windows 窗体应用程序</span><span class="sxs-lookup"><span data-stu-id="5b95f-113">Creating the Windows Forms Application</span></span>](#winforms)  
  
- [<span data-ttu-id="5b95f-114">创建数据流网络</span><span class="sxs-lookup"><span data-stu-id="5b95f-114">Creating the Dataflow Network</span></span>](#network)  
  
- [<span data-ttu-id="5b95f-115">将数据流网络连接到用户界面</span><span class="sxs-lookup"><span data-stu-id="5b95f-115">Connecting the Dataflow Network to the User Interface</span></span>](#ui)  
  
- [<span data-ttu-id="5b95f-116">完整示例</span><span class="sxs-lookup"><span data-stu-id="5b95f-116">The Complete Example</span></span>](#complete)  
  
<a name="winforms"></a>
## <a name="creating-the-windows-forms-application"></a><span data-ttu-id="5b95f-117">创建 Windows 窗体应用程序</span><span class="sxs-lookup"><span data-stu-id="5b95f-117">Creating the Windows Forms Application</span></span>  
 <span data-ttu-id="5b95f-118">本节介绍如何创建基本 Windows 窗体应用程序并将控件添加到主窗体。</span><span class="sxs-lookup"><span data-stu-id="5b95f-118">This section describes how to create the basic Windows Forms application and add controls to the main form.</span></span>  
  
### <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="5b95f-119">创建 Windows 窗体应用程序</span><span class="sxs-lookup"><span data-stu-id="5b95f-119">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="5b95f-120">在 Visual Studio 中，创建 Visual C# 或 Visual Basic“Windows 窗体应用程序”  项目。</span><span class="sxs-lookup"><span data-stu-id="5b95f-120">In Visual Studio, create a Visual C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="5b95f-121">在本文档中，该项目名为 `CompositeImages`。</span><span class="sxs-lookup"><span data-stu-id="5b95f-121">In this document, the project is named `CompositeImages`.</span></span>  
  
2. <span data-ttu-id="5b95f-122">在主窗体的窗体设计器中，Form1.cs（对于 Visual Basic，则为 Form1.vb）添加了 <xref:System.Windows.Forms.ToolStrip> 控件。</span><span class="sxs-lookup"><span data-stu-id="5b95f-122">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3. <span data-ttu-id="5b95f-123">向 <xref:System.Windows.Forms.ToolStrip> 控件添加 <xref:System.Windows.Forms.ToolStripButton> 控件。</span><span class="sxs-lookup"><span data-stu-id="5b95f-123">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="5b95f-124">将 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 属性设置为 <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>，并将 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 属性设置为“Choose Folder”  。</span><span class="sxs-lookup"><span data-stu-id="5b95f-124">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Choose Folder**.</span></span>  
  
4. <span data-ttu-id="5b95f-125">向 <xref:System.Windows.Forms.ToolStrip> 控件再添加一个 <xref:System.Windows.Forms.ToolStripButton> 控件。</span><span class="sxs-lookup"><span data-stu-id="5b95f-125">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="5b95f-126">将 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> 属性设置为 <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>，将 <xref:System.Windows.Forms.ToolStripItem.Text%2A> 属性设置为“Cancel”  ，并将 <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> 属性设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="5b95f-126">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5. <span data-ttu-id="5b95f-127">向主窗体添加 <xref:System.Windows.Forms.PictureBox> 对象。</span><span class="sxs-lookup"><span data-stu-id="5b95f-127">Add a <xref:System.Windows.Forms.PictureBox> object to the main form.</span></span> <span data-ttu-id="5b95f-128">将 <xref:System.Windows.Forms.Control.Dock%2A> 属性设置为 <xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="5b95f-128">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
<a name="network"></a>
## <a name="creating-the-dataflow-network"></a><span data-ttu-id="5b95f-129">创建数据流网络</span><span class="sxs-lookup"><span data-stu-id="5b95f-129">Creating the Dataflow Network</span></span>  
 <span data-ttu-id="5b95f-130">本节介绍如何创建执行图像处理的数据流网络。</span><span class="sxs-lookup"><span data-stu-id="5b95f-130">This section describes how to create the dataflow network that performs image processing.</span></span>  
  
### <a name="to-create-the-dataflow-network"></a><span data-ttu-id="5b95f-131">创建数据流网络</span><span class="sxs-lookup"><span data-stu-id="5b95f-131">To Create the Dataflow Network</span></span>  
  
1. <span data-ttu-id="5b95f-132">向项目中添加对 System.Threading.Tasks.Dataflow.dll 的引用。</span><span class="sxs-lookup"><span data-stu-id="5b95f-132">Add a reference to System.Threading.Tasks.Dataflow.dll to your project.</span></span>  
  
2. <span data-ttu-id="5b95f-133">确保 Form1.cs（对于 Visual Basic，则为 Form1.vb）包含以下 `using`（Visual Basic 中为 `Using`）语句：</span><span class="sxs-lookup"><span data-stu-id="5b95f-133">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Using` in Visual Basic) statements:</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3. <span data-ttu-id="5b95f-134">将以下数据成员添加到 `Form1` 类：</span><span class="sxs-lookup"><span data-stu-id="5b95f-134">Add the following data members to the `Form1` class:</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4. <span data-ttu-id="5b95f-135">将下面的 `CreateImageProcessingNetwork` 方法添加到 `Form1` 类。</span><span class="sxs-lookup"><span data-stu-id="5b95f-135">Add the following method, `CreateImageProcessingNetwork`, to the `Form1` class.</span></span> <span data-ttu-id="5b95f-136">此方法创建图像处理网络。</span><span class="sxs-lookup"><span data-stu-id="5b95f-136">This method creates the image processing network.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5. <span data-ttu-id="5b95f-137">实现 `LoadBitmaps` 方法。</span><span class="sxs-lookup"><span data-stu-id="5b95f-137">Implement the `LoadBitmaps` method.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6. <span data-ttu-id="5b95f-138">实现 `CreateCompositeBitmap` 方法。</span><span class="sxs-lookup"><span data-stu-id="5b95f-138">Implement the `CreateCompositeBitmap` method.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    > <span data-ttu-id="5b95f-139">C# 版本的 `CreateCompositeBitmap` 方法使用指针启用高效处理 <xref:System.Drawing.Bitmap?displayProperty=nameWithType> 对象。</span><span class="sxs-lookup"><span data-stu-id="5b95f-139">The C# version of the `CreateCompositeBitmap` method uses pointers to enable efficient processing of the <xref:System.Drawing.Bitmap?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="5b95f-140">因此，若要使用 [unsafe](../../csharp/language-reference/keywords/unsafe.md) 关键字，必须在项目中启用“允许不安全代码”选项。</span><span class="sxs-lookup"><span data-stu-id="5b95f-140">Therefore, you must enable the **Allow unsafe code** option in your project in order to use the [unsafe](../../csharp/language-reference/keywords/unsafe.md) keyword.</span></span> <span data-ttu-id="5b95f-141">有关如何在 Visual C# 项目中启用不安全代码的详细信息，请参阅[“项目设计器”->“生成”页 (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)。</span><span class="sxs-lookup"><span data-stu-id="5b95f-141">For more information about how to enable unsafe code in a Visual C# project, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="5b95f-142">下表描述了网络的成员。</span><span class="sxs-lookup"><span data-stu-id="5b95f-142">The following table describes the members of the network.</span></span>  
  
|<span data-ttu-id="5b95f-143">成员</span><span class="sxs-lookup"><span data-stu-id="5b95f-143">Member</span></span>|<span data-ttu-id="5b95f-144">类型</span><span class="sxs-lookup"><span data-stu-id="5b95f-144">Type</span></span>|<span data-ttu-id="5b95f-145">描述</span><span class="sxs-lookup"><span data-stu-id="5b95f-145">Description</span></span>|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="5b95f-146">将文件夹路径用作输入，并生成一组 <xref:System.Drawing.Bitmap> 对象作为输出。</span><span class="sxs-lookup"><span data-stu-id="5b95f-146">Takes a folder path as input and produces a collection of <xref:System.Drawing.Bitmap> objects as output.</span></span>|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="5b95f-147">将一组 <xref:System.Drawing.Bitmap> 对象用作输入，并生成复合位图作为输出。</span><span class="sxs-lookup"><span data-stu-id="5b95f-147">Takes a collection of <xref:System.Drawing.Bitmap> objects as input and produces a composite bitmap as output.</span></span>|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|<span data-ttu-id="5b95f-148">在窗体上显示复合位图。</span><span class="sxs-lookup"><span data-stu-id="5b95f-148">Displays the composite bitmap on the form.</span></span>|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|<span data-ttu-id="5b95f-149">显示图像以表示操作取消并使用户能够选择其他文件夹。</span><span class="sxs-lookup"><span data-stu-id="5b95f-149">Displays an image to indicate that the operation is canceled and enables the user to select another folder.</span></span>|  
  
 <span data-ttu-id="5b95f-150">为了连接数据流块以形成网络，此示例使用 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="5b95f-150">To connect the dataflow blocks to form a network, this example uses the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method.</span></span> <span data-ttu-id="5b95f-151"><xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> 方法包含重载版本，需要使用 <xref:System.Predicate%601> 对象确定目标数据流块是接受还是拒绝消息。</span><span class="sxs-lookup"><span data-stu-id="5b95f-151">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method contains an overloaded version that takes a <xref:System.Predicate%601> object that determines whether the target block accepts or rejects a message.</span></span> <span data-ttu-id="5b95f-152">此筛选机制使消息块只接收特定值。</span><span class="sxs-lookup"><span data-stu-id="5b95f-152">This filtering mechanism enables message blocks to receive only certain values.</span></span> <span data-ttu-id="5b95f-153">在此示例中，网络能以两种方式进行分支。</span><span class="sxs-lookup"><span data-stu-id="5b95f-153">In this example, the network can branch in one of two ways.</span></span> <span data-ttu-id="5b95f-154">主分支从磁盘加载图像，创建复合图像并在窗体上显示该图像。</span><span class="sxs-lookup"><span data-stu-id="5b95f-154">The main branch loads the images from disk, creates the composite image, and displays that image on the form.</span></span> <span data-ttu-id="5b95f-155">备用分支取消当前操作。</span><span class="sxs-lookup"><span data-stu-id="5b95f-155">The alternate branch cancels the current operation.</span></span> <span data-ttu-id="5b95f-156">借助 <xref:System.Predicate%601> 对象，主分支的数据流块可以拒绝特定消息，从而切换到替换分支。</span><span class="sxs-lookup"><span data-stu-id="5b95f-156">The <xref:System.Predicate%601> objects enable the dataflow blocks along the main branch to switch to the alternative branch by rejecting certain messages.</span></span> <span data-ttu-id="5b95f-157">例如，如果用户取消了操作，数据流块 `createCompositeBitmap` 将生成 `null`（在 Visual Basic 中为 `Nothing`）作为其输出。</span><span class="sxs-lookup"><span data-stu-id="5b95f-157">For example, if the user cancels the operation, the dataflow block `createCompositeBitmap` produces `null` (`Nothing` in Visual Basic) as its output.</span></span> <span data-ttu-id="5b95f-158">数据流块 `displayCompositeBitmap` 拒绝 `null` 输入值，因此该消息将传递到 `operationCancelled`。</span><span class="sxs-lookup"><span data-stu-id="5b95f-158">The dataflow block `displayCompositeBitmap` rejects `null` input values, and therefore, the message is offered to `operationCancelled`.</span></span> <span data-ttu-id="5b95f-159">数据流块 `operationCancelled` 接受所有消息，并因此显示图像以表示操作取消。</span><span class="sxs-lookup"><span data-stu-id="5b95f-159">The dataflow block `operationCancelled` accepts all messages and therefore, displays an image to indicate that the operation is canceled.</span></span>  
  
 <span data-ttu-id="5b95f-160">下图显示图像处理网络：</span><span class="sxs-lookup"><span data-stu-id="5b95f-160">The following illustration shows the image processing network:</span></span>  
  
 ![显示图像处理网络的插图。](./media/walkthrough-using-dataflow-in-a-windows-forms-application/dataflow-winforms-image-processing.png)  
  
 <span data-ttu-id="5b95f-162">因为 `displayCompositeBitmap` 和 `operationCancelled` 数据流块是在用户界面上操作，所以这些操作要在用户界面线程上执行，这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="5b95f-162">Because the `displayCompositeBitmap` and `operationCancelled` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="5b95f-163">为此，在构造期间，每个对象都提供将 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> 属性设置为 <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> 的 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> 对象。</span><span class="sxs-lookup"><span data-stu-id="5b95f-163">To accomplish this, during construction, these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5b95f-164"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> 方法会创建一个在当前同步上下文中执行工作的 <xref:System.Threading.Tasks.TaskScheduler> 对象。</span><span class="sxs-lookup"><span data-stu-id="5b95f-164">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="5b95f-165">因为 `CreateImageProcessingNetwork` 方法是通过“选择文件夹”  按钮的处理程序调用的，而该处理程序在用户界面线程上运行，所以 `displayCompositeBitmap` 和 `operationCancelled` 数据流块的操作也在用户界面线程上运行。</span><span class="sxs-lookup"><span data-stu-id="5b95f-165">Because the `CreateImageProcessingNetwork` method is called from the handler of the **Choose Folder** button, which runs on the user-interface thread, the actions for the `displayCompositeBitmap` and `operationCancelled` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="5b95f-166">此示例使用共享的取消令牌，而不是设置 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> 属性，因为 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> 属性永久取消数据流块执行。</span><span class="sxs-lookup"><span data-stu-id="5b95f-166">This example uses a shared cancellation token instead of setting the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution.</span></span> <span data-ttu-id="5b95f-167">利用取消标记，此示例可多次重复使用同一数据流网络，即使用户取消一个或多个操作也是如此。</span><span class="sxs-lookup"><span data-stu-id="5b95f-167">A cancellation token enables this example to reuse the same dataflow network multiple times, even when the user cancels one or more operations.</span></span> <span data-ttu-id="5b95f-168">有关使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> 永久取消数据流块执行的示例，请参阅[如何：取消数据流块](how-to-cancel-a-dataflow-block.md)。</span><span class="sxs-lookup"><span data-stu-id="5b95f-168">For an example that uses <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> to permanently cancel the execution of a dataflow block, see [How to: Cancel a Dataflow Block](how-to-cancel-a-dataflow-block.md).</span></span>  
  
<a name="ui"></a>
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a><span data-ttu-id="5b95f-169">将数据流网络连接到用户界面</span><span class="sxs-lookup"><span data-stu-id="5b95f-169">Connecting the Dataflow Network to the User Interface</span></span>  
 <span data-ttu-id="5b95f-170">本节介绍如何将数据流网络连接到用户界面。</span><span class="sxs-lookup"><span data-stu-id="5b95f-170">This section describes how to connect the dataflow network to the user interface.</span></span> <span data-ttu-id="5b95f-171">复合图像创建和操作取消都是从“选择文件夹”  和“取消”  按钮启动的。</span><span class="sxs-lookup"><span data-stu-id="5b95f-171">The creation of the composite image and cancellation of the operation are initiated from the **Choose Folder** and **Cancel** buttons.</span></span> <span data-ttu-id="5b95f-172">用户选择以上任一按钮时，都会以异步方式启动相应操作。</span><span class="sxs-lookup"><span data-stu-id="5b95f-172">When the user chooses either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a><span data-ttu-id="5b95f-173">将数据流网络连接到用户界面</span><span class="sxs-lookup"><span data-stu-id="5b95f-173">To Connect the Dataflow Network to the User Interface</span></span>  
  
1. <span data-ttu-id="5b95f-174">在主窗体的窗体设计器中，创建“选择文件夹”按钮的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="5b95f-174">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Choose Folder** button.</span></span>  
  
2. <span data-ttu-id="5b95f-175">实现“选择文件夹”按钮的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="5b95f-175">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Choose Folder** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3. <span data-ttu-id="5b95f-176">在主窗体的窗体设计器中，创建“取消”按钮的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="5b95f-176">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Cancel** button.</span></span>  
  
4. <span data-ttu-id="5b95f-177">实现“取消”按钮的 <xref:System.Windows.Forms.ToolStripItem.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="5b95f-177">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>
## <a name="the-complete-example"></a><span data-ttu-id="5b95f-178">完整示例</span><span class="sxs-lookup"><span data-stu-id="5b95f-178">The Complete Example</span></span>  
 <span data-ttu-id="5b95f-179">下面的示例显示此演练的完整代码。</span><span class="sxs-lookup"><span data-stu-id="5b95f-179">The following example shows the complete code for this walkthrough.</span></span>  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 <span data-ttu-id="5b95f-180">下图显示公共 \Sample Pictures\ 文件夹的典型输出。</span><span class="sxs-lookup"><span data-stu-id="5b95f-180">The following illustration shows typical output for the common \Sample Pictures\ folder.</span></span>  
  
 <span data-ttu-id="5b95f-181">![Windows 窗体应用程序](media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")</span><span class="sxs-lookup"><span data-stu-id="5b95f-181">![The Windows Forms Application](media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")</span></span>  

## <a name="see-also"></a><span data-ttu-id="5b95f-182">请参阅</span><span class="sxs-lookup"><span data-stu-id="5b95f-182">See also</span></span>

- [<span data-ttu-id="5b95f-183">数据流</span><span class="sxs-lookup"><span data-stu-id="5b95f-183">Dataflow</span></span>](dataflow-task-parallel-library.md)
