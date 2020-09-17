---
title: 如何：将消息写入数据流块和从数据流块读取消息
ms.date: 09/10/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
ms.openlocfilehash: 8eb92d917bb2b03c2a505a2ba238598e0c1a450c
ms.sourcegitcommit: 6d4ee46871deb9ea1e45bb5f3784474e240bbc26
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2020
ms.locfileid: "90022852"
---
# <a name="how-to-write-and-read-messages-from-a-dataflow-block"></a><span data-ttu-id="4b8bb-102">如何：将消息写入数据流块和从数据流块读取消息</span><span class="sxs-lookup"><span data-stu-id="4b8bb-102">How to: Write and read messages from a Dataflow block</span></span>

<span data-ttu-id="4b8bb-103">本文介绍如何使用任务并行库 (TPL) 数据流库将消息写入数据流块和从数据流块读取消息。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-103">This article describes how to use the Task Parallel Library (TPL) Dataflow Library to write messages to and read messages from a dataflow block.</span></span> <span data-ttu-id="4b8bb-104">TPL 数据流库同时提供用于从数据流块写入和读取消息的同步和异步方法。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-104">The TPL Dataflow Library provides both synchronous and asynchronous methods for writing messages to and reading messages from a dataflow block.</span></span> <span data-ttu-id="4b8bb-105">本文介绍如何使用 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> 类。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-105">This article shows how to uses the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="4b8bb-106"><xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 类可缓冲消息，既充当消息源，又充当消息目标。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-106">The <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class buffers messages and behaves as both a message source and a message target.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-and-reading-synchronously"></a><span data-ttu-id="4b8bb-107">同步写入和读取</span><span class="sxs-lookup"><span data-stu-id="4b8bb-107">Writing and reading synchronously</span></span>

<span data-ttu-id="4b8bb-108">下面的示例使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> 方法写入 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 数据流块，使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> 方法从同一对象读取。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-108">The following example uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method to write to a <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> dataflow block and the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method to read from the same object.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="2":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="2":::

<span data-ttu-id="4b8bb-109">如以下示例所示，还可以使用 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法从数据流块读取。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-109">You can also use the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method to read from a dataflow block, as shown in the following example.</span></span> <span data-ttu-id="4b8bb-110"><xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法不会阻止当前线程，而且在偶尔轮询数据时非常有用。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-110">The <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method does not block the current thread and is useful when you occasionally poll for data.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="3":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="3":::

<span data-ttu-id="4b8bb-111">由于 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> 方法是同步运行的，前面示例中的 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 对象会在第二个循环读取数据之前接收所有数据。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-111">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method acts synchronously, the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> object in the previous examples receives all data before the second loop reads data.</span></span> <span data-ttu-id="4b8bb-112">下面的示例对第一个示例进行了扩展，使用 <xref:System.Threading.Tasks.Task.WhenAll(System.Threading.Tasks.Task[])?displayProperty=nameWithType> 同时读取和写入消息块。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-112">The following example extends the first example by using <xref:System.Threading.Tasks.Task.WhenAll(System.Threading.Tasks.Task[])?displayProperty=nameWithType> to read from and write to the message block concurrently.</span></span> <span data-ttu-id="4b8bb-113">由于 <xref:System.Threading.Tasks.Task.WhenAll%2A> 并发执行操作，因此不会按任何特定的顺序将值写入 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 对象。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-113">Because <xref:System.Threading.Tasks.Task.WhenAll%2A> performs actions concurrently, the values are not written to the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> object in any specific order.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="4":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="4":::

## <a name="writing-and-reading-asynchronously"></a><span data-ttu-id="4b8bb-114">异步写入和读取</span><span class="sxs-lookup"><span data-stu-id="4b8bb-114">Writing and reading asynchronously</span></span>

<span data-ttu-id="4b8bb-115">下面的示例使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> 方法异步写入 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 对象，使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> 方法从同一对象异步读取。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-115">The following example uses the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> method to asynchronously write to a <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> object and the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> method to asynchronously read from the same object.</span></span> <span data-ttu-id="4b8bb-116">本示例使用 [async](../../csharp/language-reference/keywords/async.md) 和 [await](../../csharp/language-reference/operators/await.md) 运算符（Visual Basic 中为 [Async](../../visual-basic/language-reference/modifiers/async.md) 和 [Await](../../visual-basic/language-reference/operators/await-operator.md)）以异步方式向目标块发送数据以及从中读取数据。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-116">This example uses the [async](../../csharp/language-reference/keywords/async.md) and [await](../../csharp/language-reference/operators/await.md) operators ([Async](../../visual-basic/language-reference/modifiers/async.md) and [Await](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic) to asynchronously send data to and read data from the target block.</span></span> <span data-ttu-id="4b8bb-117">必须启用数据流块来推迟消息时，<xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> 方法很有用。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-117">The <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> method is useful when you must enable a dataflow block to postpone messages.</span></span> <span data-ttu-id="4b8bb-118">希望在数据可用时对此数据进行操作时，<xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> 方法很有用。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-118">The <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> method is useful when you want to act on data when that data becomes available.</span></span> <span data-ttu-id="4b8bb-119">有关消息在消息块之间如何传播的详细信息，请参阅[数据流](dataflow-task-parallel-library.md)中的“消息传递”一节。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-119">For more information about how messages propagate among message blocks, see the section Message Passing in [Dataflow](dataflow-task-parallel-library.md).</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="5":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="5":::

## <a name="a-complete-example"></a><span data-ttu-id="4b8bb-120">完整示例</span><span class="sxs-lookup"><span data-stu-id="4b8bb-120">A complete example</span></span>

<span data-ttu-id="4b8bb-121">以下示例显示本文中的所有代码。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-121">The following example shows all of the code for this article.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="1":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="1":::

## <a name="next-steps"></a><span data-ttu-id="4b8bb-122">后续步骤</span><span class="sxs-lookup"><span data-stu-id="4b8bb-122">Next steps</span></span>

<span data-ttu-id="4b8bb-123">本示例演示如何直接从消息块读取和写入。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-123">This example shows how to read from and write to a message block directly.</span></span> <span data-ttu-id="4b8bb-124">还可以连接数据流块来形成管道  （这是数据流块的线性序列）或网络  （这是数据流块的图形）。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-124">You can also connect dataflow blocks to form *pipelines*, which are linear sequences of dataflow blocks, or *networks*, which are graphs of dataflow blocks.</span></span> <span data-ttu-id="4b8bb-125">在管道或网络中，当数据可用时源向目标异步传播数据。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-125">In a pipeline or network, sources asynchronously propagate data to targets as that data becomes available.</span></span> <span data-ttu-id="4b8bb-126">有关创建基本数据流管道的示例，请参阅[演练：创建数据流管道](walkthrough-creating-a-dataflow-pipeline.md)。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-126">For an example that creates a basic dataflow pipeline, see [Walkthrough: Creating a Dataflow Pipeline](walkthrough-creating-a-dataflow-pipeline.md).</span></span> <span data-ttu-id="4b8bb-127">有关创建更复杂的数据流网络的示例，请参阅[演练：在 Windows 窗体应用程序中使用数据流](walkthrough-using-dataflow-in-a-windows-forms-application.md)。</span><span class="sxs-lookup"><span data-stu-id="4b8bb-127">For an example that creates a more complex dataflow network, see [Walkthrough: Using Dataflow in a Windows Forms Application](walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4b8bb-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b8bb-128">See also</span></span>

- [<span data-ttu-id="4b8bb-129">数据流（任务并行库）</span><span class="sxs-lookup"><span data-stu-id="4b8bb-129">Dataflow (Task Parallel Library)</span></span>](dataflow-task-parallel-library.md)
