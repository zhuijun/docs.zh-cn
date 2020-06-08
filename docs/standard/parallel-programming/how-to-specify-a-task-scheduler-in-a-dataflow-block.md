---
title: 如何：在数据流块中指定任务计划程序
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, linking to task scheduler in TPL
- Task Parallel Library, dataflows
- task scheduler, linking from TPL
ms.assetid: 27ece374-ed5b-49ef-9cec-b20db34a65e8
ms.openlocfilehash: 76c9e75f787c28657af143b46bb22d08039e2dc4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288129"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a><span data-ttu-id="b7e8c-102">如何：在数据流块中指定任务计划程序</span><span class="sxs-lookup"><span data-stu-id="b7e8c-102">How to: Specify a Task Scheduler in a Dataflow Block</span></span>
<span data-ttu-id="b7e8c-103">本文档演示在应用程序中使用数据流时如何关联特定任务计划程序。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-103">This document demonstrates how to associate a specific task scheduler when you use dataflow in your application.</span></span> <span data-ttu-id="b7e8c-104">示例在 Windows 窗体应用程序中使用 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> 类来显示读取器任务处于活动状态的时间和编写器任务处于活动状态的时间。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-104">The example uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> class in a Windows Forms application to show when reader tasks are active and when a writer task is active.</span></span> <span data-ttu-id="b7e8c-105">它还使用 <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> 方法使数据流块能够在用户界面线程上运行。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-105">It also uses the <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method to enable a dataflow block to run on the user-interface thread.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="b7e8c-106">创建 Windows 窗体应用程序</span><span class="sxs-lookup"><span data-stu-id="b7e8c-106">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="b7e8c-107">创建一个 Visual C# 或 Visual Basic“Windows 窗体应用程序”项目  。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-107">Create a Visual C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="b7e8c-108">在以下步骤中，该项目命名为 `WriterReadersWinForms`。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-108">In the following steps, the project is named `WriterReadersWinForms`.</span></span>  
  
2. <span data-ttu-id="b7e8c-109">在主窗体的窗体设计器中，Form1.cs（对于 Visual Basic 则为 Form1.vb）添加了四个 <xref:System.Windows.Forms.CheckBox> 控件。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-109">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add four <xref:System.Windows.Forms.CheckBox> controls.</span></span> <span data-ttu-id="b7e8c-110">将 `checkBox1`、`checkBox2`、`checkBox3`、`checkBox4` 的 <xref:System.Windows.Forms.Control.Text%2A> 属性分别设置为“读取器 1”、“读取器 2”、“读取器 3”和“编写器”。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-110">Set the <xref:System.Windows.Forms.Control.Text%2A> property to **Reader 1** for `checkBox1`, **Reader 2** for `checkBox2`, **Reader 3** for `checkBox3`, and **Writer** for `checkBox4`.</span></span> <span data-ttu-id="b7e8c-111">将每个控件的 <xref:System.Windows.Forms.Control.Enabled%2A> 属性设置为 `False`。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-111">Set the <xref:System.Windows.Forms.Control.Enabled%2A> property for each control to `False`.</span></span>  
  
3. <span data-ttu-id="b7e8c-112">在窗体上添加一个 <xref:System.Windows.Forms.Timer> 控件。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-112">Add a <xref:System.Windows.Forms.Timer> control to the form.</span></span> <span data-ttu-id="b7e8c-113">将 <xref:System.Windows.Forms.Timer.Interval%2A> 属性设置为 `2500`。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-113">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `2500`.</span></span>  
  
## <a name="adding-dataflow-functionality"></a><span data-ttu-id="b7e8c-114">添加数据流功能</span><span class="sxs-lookup"><span data-stu-id="b7e8c-114">Adding Dataflow Functionality</span></span>  
 <span data-ttu-id="b7e8c-115">本节介绍如何创建参与应用程序的数据流块以及如何将每个数据流块与任务计划程序关联。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-115">This section describes how to create the dataflow blocks that participate in the application and how to associate each one with a task scheduler.</span></span>  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a><span data-ttu-id="b7e8c-116">在应用程序中添加数据流功能</span><span class="sxs-lookup"><span data-stu-id="b7e8c-116">To Add Dataflow Functionality to the Application</span></span>  
  
1. <span data-ttu-id="b7e8c-117">在项目中，添加对 System.Threading.Tasks.Dataflow.dll 的引用。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="b7e8c-118">确保 Form1.cs（对于 Visual Basic 则为 Form1.vb）包含以下 `using` 语句（Visual Basic 中为 `Imports`）。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. <span data-ttu-id="b7e8c-119">将 <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> 数据成员添加到 `Form1` 类。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-119">Add a <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> data member to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. <span data-ttu-id="b7e8c-120">在 `Form1` 构造函数中，在调用 `InitializeComponent` 后，创建一个 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 对象，该对象将切换 <xref:System.Windows.Forms.CheckBox> 对象的状态。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-120">In the `Form1` constructor, after the call to `InitializeComponent`, create an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that toggles the state of <xref:System.Windows.Forms.CheckBox> objects.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. <span data-ttu-id="b7e8c-121">在 `Form1` 构造函数中，创建一个 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> 对象和四个 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 对象，每个 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 对象对应一个 <xref:System.Windows.Forms.CheckBox> 对象。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-121">In the `Form1` constructor, create a <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object and four <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objects, one <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object for each <xref:System.Windows.Forms.CheckBox> object.</span></span> <span data-ttu-id="b7e8c-122">对每个 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 对象，指定一个 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> 对象，该对象将读取器的 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> 属性设置为 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> 属性，将编写器的设置为 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-122">For each <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object, specify a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> property for the readers, and the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> property for the writer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. <span data-ttu-id="b7e8c-123">在 `Form1` 构造函数中，启动 <xref:System.Windows.Forms.Timer> 对象。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-123">In the `Form1` constructor, start the <xref:System.Windows.Forms.Timer> object.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. <span data-ttu-id="b7e8c-124">在主窗体的窗体设计器中，为计时器的 <xref:System.Windows.Forms.Timer.Tick> 事件创建事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-124">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
8. <span data-ttu-id="b7e8c-125">实现计时器的 <xref:System.Windows.Forms.Timer.Tick> 事件。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-125">Implement the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 <span data-ttu-id="b7e8c-126">因为 `toggleCheckBox` 数据流块是在用户界面上操作，所以此操作要在用户界面线程上执行，这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-126">Because the `toggleCheckBox` dataflow block acts on the user interface, it is important that this action occur on the user-interface thread.</span></span> <span data-ttu-id="b7e8c-127">为此，在构造期间，此对象提供一个将 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> 属性设置为 <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> 的 <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> 对象。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-127">To accomplish this, during construction this object provides a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b7e8c-128"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> 方法会创建一个在当前同步上下文中执行工作的 <xref:System.Threading.Tasks.TaskScheduler> 对象。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-128">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="b7e8c-129">因为 `Form1` 构造函数是从用户界面线程中调用的，所以 `toggleCheckBox` 数据流块的操作也会在用户线程中运行。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-129">Because the `Form1` constructor is called from the user-interface thread, the action for the `toggleCheckBox` dataflow block also runs on the user-interface thread.</span></span>  
  
 <span data-ttu-id="b7e8c-130">对于在同一 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> 对象上运行的所有其他数据流块，此示例还使用了 <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> 类使某些数据流块能够并发操作，而使其他数据流块能够单独执行。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-130">This example also uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> class to enable some dataflow blocks to act concurrently, and another dataflow block to act exclusive with respect to all other dataflow blocks that run on the same <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object.</span></span> <span data-ttu-id="b7e8c-131">当多个数据流块共享资源，但有些需要对该资源独占访问时，这种技术很有用，因为它不需要手动同步对该资源的访问。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-131">This technique is useful when multiple dataflow blocks share a resource and some require exclusive access to that resource, because it eliminates the requirement to manually synchronize access to that resource.</span></span> <span data-ttu-id="b7e8c-132">手动同步的消除会使代码更高效。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-132">The elimination of manual synchronization can make code more efficient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7e8c-133">示例</span><span class="sxs-lookup"><span data-stu-id="b7e8c-133">Example</span></span>  
 <span data-ttu-id="b7e8c-134">下面的示例演示 Form1.cs（对于 Visual Basic 则为 Form1.vb）的完整代码。</span><span class="sxs-lookup"><span data-stu-id="b7e8c-134">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="b7e8c-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b7e8c-135">See also</span></span>

- [<span data-ttu-id="b7e8c-136">数据流</span><span class="sxs-lookup"><span data-stu-id="b7e8c-136">Dataflow</span></span>](dataflow-task-parallel-library.md)
