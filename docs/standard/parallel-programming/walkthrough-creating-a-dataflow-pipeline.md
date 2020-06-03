---
title: 演练：创建数据流管道
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow pipelines, creating with TPL
- Task Parallel Library, dataflows
- TPL dataflow library, creating dataflow pipeline
ms.assetid: 69308f82-aa22-4ac5-833d-e748533b58e8
ms.openlocfilehash: cfe3296815dc344b0d9d1f7bad1ab4a130380e2b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284606"
---
# <a name="walkthrough-creating-a-dataflow-pipeline"></a><span data-ttu-id="3b54c-102">演练：创建数据流管道</span><span class="sxs-lookup"><span data-stu-id="3b54c-102">Walkthrough: Creating a Dataflow Pipeline</span></span>
<span data-ttu-id="3b54c-103">尽管可以使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType>、<xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType> 方法从源块接收消息，但也可以连接消息块来形成一个*数据流管道*。</span><span class="sxs-lookup"><span data-stu-id="3b54c-103">Although you can use the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType> methods to receive messages from source blocks, you can also connect message blocks to form a *dataflow pipeline*.</span></span> <span data-ttu-id="3b54c-104">数据流管道是一系列组件或“数据流块”，每个组件或数据流块执行一个有助于实现更大目标的特定任务。</span><span class="sxs-lookup"><span data-stu-id="3b54c-104">A dataflow pipeline is a series of components, or *dataflow blocks*, each of which performs a specific task that contributes to a larger goal.</span></span> <span data-ttu-id="3b54c-105">数据流管道中的每个数据流块会在收到来自另一数据流块的消息时执行工作。</span><span class="sxs-lookup"><span data-stu-id="3b54c-105">Every dataflow block in a dataflow pipeline performs work when it receives a message from another dataflow block.</span></span> <span data-ttu-id="3b54c-106">这就好比是汽车制造装配线。</span><span class="sxs-lookup"><span data-stu-id="3b54c-106">An analogy to this is an assembly line for automobile manufacturing.</span></span> <span data-ttu-id="3b54c-107">每辆汽车通过装配线时，一站组装车架，下一站则安装引擎，以此类推。</span><span class="sxs-lookup"><span data-stu-id="3b54c-107">As each vehicle passes through the assembly line, one station assembles the frame, the next one installs the engine, and so on.</span></span> <span data-ttu-id="3b54c-108">因为装配线可以同时装配多辆汽车，所以比一次装配整辆车拥有更高的产出。</span><span class="sxs-lookup"><span data-stu-id="3b54c-108">Because an assembly line enables multiple vehicles to be assembled at the same time, it provides better throughput than assembling complete vehicles one at a time.</span></span>

 <span data-ttu-id="3b54c-109">本文档演示了一个数据流管道，用于从网站上下载书籍《The Iliad of Homer》并搜索文本以将各个单词与反转第一个单词字符的单词相匹配。</span><span class="sxs-lookup"><span data-stu-id="3b54c-109">This document demonstrates a dataflow pipeline that downloads the book *The Iliad of Homer* from a website and searches the text to match individual words with words that reverse the first word's characters.</span></span> <span data-ttu-id="3b54c-110">本文档中数据流管道的形成包括以下步骤：</span><span class="sxs-lookup"><span data-stu-id="3b54c-110">The formation of the dataflow pipeline in this document consists of the following steps:</span></span>  
  
1. <span data-ttu-id="3b54c-111">创建参与管道的数据流块。</span><span class="sxs-lookup"><span data-stu-id="3b54c-111">Create the dataflow blocks that participate in the pipeline.</span></span>  
  
2. <span data-ttu-id="3b54c-112">连接每个数据流块与管道中的下一个块。</span><span class="sxs-lookup"><span data-stu-id="3b54c-112">Connect each dataflow block to the next block in the pipeline.</span></span> <span data-ttu-id="3b54c-113">每个块将管道中前一个块的输出作为输入接收。</span><span class="sxs-lookup"><span data-stu-id="3b54c-113">Each block receives as input the output of the previous block in the pipeline.</span></span>  
  
3. <span data-ttu-id="3b54c-114">对每个数据流块，创建一个延续任务，该延续任务在上一个块完成后将下一个块的状态设置为已完成状态。</span><span class="sxs-lookup"><span data-stu-id="3b54c-114">For each dataflow block, create a continuation task that sets the next block to the completed state after the previous block finishes.</span></span>  
  
4. <span data-ttu-id="3b54c-115">将数据发布到管道的开头。</span><span class="sxs-lookup"><span data-stu-id="3b54c-115">Post data to the head of the pipeline.</span></span>  
  
5. <span data-ttu-id="3b54c-116">将管道的开头标记为已完成。</span><span class="sxs-lookup"><span data-stu-id="3b54c-116">Mark the head of the pipeline as completed.</span></span>  
  
6. <span data-ttu-id="3b54c-117">等待管道完成所有工作。</span><span class="sxs-lookup"><span data-stu-id="3b54c-117">Wait for the pipeline to complete all work.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3b54c-118">先决条件</span><span class="sxs-lookup"><span data-stu-id="3b54c-118">Prerequisites</span></span>  
 <span data-ttu-id="3b54c-119">开始本演练之前，请阅读[数据流](dataflow-task-parallel-library.md)。</span><span class="sxs-lookup"><span data-stu-id="3b54c-119">Read [Dataflow](dataflow-task-parallel-library.md) before you start this walkthrough.</span></span>  
  
## <a name="creating-a-console-application"></a><span data-ttu-id="3b54c-120">创建控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="3b54c-120">Creating a Console Application</span></span>  
 <span data-ttu-id="3b54c-121">在 Visual Studio 中，创建 Visual C# 或 Visual Basic“控制台应用程序”项目。</span><span class="sxs-lookup"><span data-stu-id="3b54c-121">In Visual Studio, create a Visual C# or Visual Basic Console Application project.</span></span> <span data-ttu-id="3b54c-122">安装 System.Threading.Tasks.Dataflow NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="3b54c-122">Install the System.Threading.Tasks.Dataflow NuGet package.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

 <span data-ttu-id="3b54c-123">将以下代码添加到项目中以创建基本应用程序。</span><span class="sxs-lookup"><span data-stu-id="3b54c-123">Add the following code to your project to create the basic application.</span></span>  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromesemptymain.vb#2)]  
  
## <a name="creating-the-dataflow-blocks"></a><span data-ttu-id="3b54c-124">创建数据流块</span><span class="sxs-lookup"><span data-stu-id="3b54c-124">Creating the Dataflow Blocks</span></span>  
 <span data-ttu-id="3b54c-125">将以下代码添加到 `Main` 方法以创建参与管道的数据流块。</span><span class="sxs-lookup"><span data-stu-id="3b54c-125">Add the following code to the `Main` method to create the dataflow blocks that participate in the pipeline.</span></span> <span data-ttu-id="3b54c-126">下表总结了管道的每个成员的角色。</span><span class="sxs-lookup"><span data-stu-id="3b54c-126">The table that follows summarizes the role of each member of the pipeline.</span></span>  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|<span data-ttu-id="3b54c-127">成员</span><span class="sxs-lookup"><span data-stu-id="3b54c-127">Member</span></span>|<span data-ttu-id="3b54c-128">类型</span><span class="sxs-lookup"><span data-stu-id="3b54c-128">Type</span></span>|<span data-ttu-id="3b54c-129">描述</span><span class="sxs-lookup"><span data-stu-id="3b54c-129">Description</span></span>|  
|------------|----------|-----------------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="3b54c-130">从 Web 下载该书的文本。</span><span class="sxs-lookup"><span data-stu-id="3b54c-130">Downloads the book text from the Web.</span></span>|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="3b54c-131">将该书的文本分成单词的数组。</span><span class="sxs-lookup"><span data-stu-id="3b54c-131">Separates the book text into an array of words.</span></span>|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="3b54c-132">删除短词和单词数组中的重复项。</span><span class="sxs-lookup"><span data-stu-id="3b54c-132">Removes short words and duplicates from the word array.</span></span>|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|<span data-ttu-id="3b54c-133">查找经过筛选的单词数组集合中所有将字母反转后仍在单词数组中出现的单词。</span><span class="sxs-lookup"><span data-stu-id="3b54c-133">Finds all words in the filtered word array collection whose reverse also occurs in the word array.</span></span>|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|<span data-ttu-id="3b54c-134">向控制台显示单词及对应的倒序词。</span><span class="sxs-lookup"><span data-stu-id="3b54c-134">Displays words and the corresponding reverse words to the console.</span></span>|  
  
 <span data-ttu-id="3b54c-135">虽然可以将本示例中数据流管道的多个步骤合并为一个步骤，不过本示例阐释了组合多个独立数据流任务来执行较大任务的概念。</span><span class="sxs-lookup"><span data-stu-id="3b54c-135">Although you could combine multiple steps in the dataflow pipeline in this example into one step, the example illustrates the concept of composing multiple independent dataflow tasks to perform a larger task.</span></span> <span data-ttu-id="3b54c-136">示例通过使用 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> 使管道的每个成员能对其输入数据执行操作并将结果发送到管道中的下一步骤。</span><span class="sxs-lookup"><span data-stu-id="3b54c-136">The example uses <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> to enable each member of the pipeline to perform an operation on its input data and send the results to the next step in the pipeline.</span></span> <span data-ttu-id="3b54c-137">管道的 `findReversedWords` 成员是一个 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> 对象，因为该成员会为每个输入生成多个独立输出。</span><span class="sxs-lookup"><span data-stu-id="3b54c-137">The `findReversedWords` member of the pipeline is a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> object because it produces multiple independent outputs for each input.</span></span> <span data-ttu-id="3b54c-138">管道的结尾 `printReversedWords` 是一个 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 对象，因为它会对其输入执行一个操作，但不产生结果。</span><span class="sxs-lookup"><span data-stu-id="3b54c-138">The tail of the pipeline, `printReversedWords`, is an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object because it performs an action on its input, and does not produce a result.</span></span>  
  
## <a name="forming-the-pipeline"></a><span data-ttu-id="3b54c-139">形成管道</span><span class="sxs-lookup"><span data-stu-id="3b54c-139">Forming the Pipeline</span></span>  
 <span data-ttu-id="3b54c-140">添加以下代码将每个块与管道中的下一个块连接。</span><span class="sxs-lookup"><span data-stu-id="3b54c-140">Add the following code to connect each block to the next block in the pipeline.</span></span>  
  
 <span data-ttu-id="3b54c-141">当您调用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> 方法将源数据流块连接到目标数据流块时，源数据流块会在数据可用时将数据传播到目标块。</span><span class="sxs-lookup"><span data-stu-id="3b54c-141">When you call the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> method to connect a source dataflow block to a target dataflow block, the source dataflow block propagates data to the target block as data becomes available.</span></span> <span data-ttu-id="3b54c-142">如果你还提供 <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions>，并将 <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.PropagateCompletion> 设置为 true，则在管道中成功或未成功完成一个块都将导致管道中下一个块的完成。</span><span class="sxs-lookup"><span data-stu-id="3b54c-142">If you also provide <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> with <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.PropagateCompletion> set to true, successful or unsuccessful completion of one block in the pipeline will cause completion of the next block in the pipeline.</span></span>
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## <a name="posting-data-to-the-pipeline"></a><span data-ttu-id="3b54c-143">将数据发布到管道</span><span class="sxs-lookup"><span data-stu-id="3b54c-143">Posting Data to the Pipeline</span></span>  
 <span data-ttu-id="3b54c-144">添加以下代码，以将《The Iliad of Homer》一书的 URL 发布到数据流管道的开头。</span><span class="sxs-lookup"><span data-stu-id="3b54c-144">Add the following code to post the URL of the book *The Iliad of Homer* to the head of the dataflow pipeline.</span></span>  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 <span data-ttu-id="3b54c-145">此示例使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> 将数据同步发送到管道的开头。</span><span class="sxs-lookup"><span data-stu-id="3b54c-145">This example uses <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> to synchronously send data to the head of the pipeline.</span></span> <span data-ttu-id="3b54c-146">在必须将数据异步发送到数据流节点时，请使用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="3b54c-146">Use the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> method when you must asynchronously send data to a dataflow node.</span></span>  
  
## <a name="completing-pipeline-activity"></a><span data-ttu-id="3b54c-147">完成管道活动</span><span class="sxs-lookup"><span data-stu-id="3b54c-147">Completing Pipeline Activity</span></span>  
 <span data-ttu-id="3b54c-148">添加以下代码将管道的开头标记为已完成。</span><span class="sxs-lookup"><span data-stu-id="3b54c-148">Add the following code to mark the head of the pipeline as completed.</span></span> <span data-ttu-id="3b54c-149">管道的开头在处理了所有缓冲的消息后传播其完成。</span><span class="sxs-lookup"><span data-stu-id="3b54c-149">The head of the pipeline propagates its completion after it processes all buffered messages.</span></span>
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 <span data-ttu-id="3b54c-150">此示例通过要处理的数据流管道发送一个 URL。</span><span class="sxs-lookup"><span data-stu-id="3b54c-150">This example sends one URL through the dataflow pipeline to be processed.</span></span> <span data-ttu-id="3b54c-151">如果要通过管道发送多个输入，请在提交了所有输入后调用 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="3b54c-151">If you send more than one input through a pipeline, call the <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> method after you submit all the input.</span></span> <span data-ttu-id="3b54c-152">如果您的应用程序没有表示数据不再可用或应用程序不必等待管道完成的定义完善的点，则可以忽略此步骤。</span><span class="sxs-lookup"><span data-stu-id="3b54c-152">You can omit this step if your application has no well-defined point at which data is no longer available or the application does not have to wait for the pipeline to finish.</span></span>  
  
## <a name="waiting-for-the-pipeline-to-finish"></a><span data-ttu-id="3b54c-153">等待管道完成</span><span class="sxs-lookup"><span data-stu-id="3b54c-153">Waiting for the Pipeline to Finish</span></span>  
 <span data-ttu-id="3b54c-154">添加以下代码以等待管道完成。</span><span class="sxs-lookup"><span data-stu-id="3b54c-154">Add the following code to wait for the pipeline to finish.</span></span> <span data-ttu-id="3b54c-155">管道的结尾完成时完成整个操作。</span><span class="sxs-lookup"><span data-stu-id="3b54c-155">The overall operation is finished when the tail of the pipeline finishes.</span></span>  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 <span data-ttu-id="3b54c-156">可以同时等待任一线程或多个线程的数据流完成。</span><span class="sxs-lookup"><span data-stu-id="3b54c-156">You can wait for dataflow completion from any thread or from multiple threads at the same time.</span></span>  
  
## <a name="the-complete-example"></a><span data-ttu-id="3b54c-157">完整示例</span><span class="sxs-lookup"><span data-stu-id="3b54c-157">The Complete Example</span></span>  
 <span data-ttu-id="3b54c-158">下面的示例显示此演练的完整代码。</span><span class="sxs-lookup"><span data-stu-id="3b54c-158">The following example shows the complete code for this walkthrough.</span></span>  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="3b54c-159">后续步骤</span><span class="sxs-lookup"><span data-stu-id="3b54c-159">Next Steps</span></span>  
 <span data-ttu-id="3b54c-160">此示例发送一个通过数据流管道处理的 URL。</span><span class="sxs-lookup"><span data-stu-id="3b54c-160">This example sends one URL to process through the dataflow pipeline.</span></span> <span data-ttu-id="3b54c-161">如果要通过管道发送多个输入值，可以将并行的形式引入应用程序，这与零件在汽车厂中移动的方式类似。</span><span class="sxs-lookup"><span data-stu-id="3b54c-161">If you send more than one input value through a pipeline, you can introduce a form of parallelism into your application that resembles how parts might move through an automobile factory.</span></span> <span data-ttu-id="3b54c-162">当管道的第一个成员将其结果发送给第二个成员时，它可以在第二个成员处理第一个结果时并行处理另一个项。</span><span class="sxs-lookup"><span data-stu-id="3b54c-162">When the first member of the pipeline sends its result to the second member, it can process another item in parallel as the second member processes the first result.</span></span>  
  
 <span data-ttu-id="3b54c-163">通过使用数据流管道实现的并行称为*粗粒度并行*，因为它通常由几个较大的任务组成。</span><span class="sxs-lookup"><span data-stu-id="3b54c-163">The parallelism that is achieved by using dataflow pipelines is known as *coarse-grained parallelism* because it typically consists of fewer, larger tasks.</span></span> <span data-ttu-id="3b54c-164">此外，你也可以在数据流管道中对短时间运行的较小任务使用*粒度较细的并行*。</span><span class="sxs-lookup"><span data-stu-id="3b54c-164">You can also use a more *fine-grained parallelism* of smaller, short-running tasks in a dataflow pipeline.</span></span> <span data-ttu-id="3b54c-165">在本示例中，管道的 `findReversedWords` 成员使用 [PLINQ](introduction-to-plinq.md) 并行处理工作列表中的多个项。</span><span class="sxs-lookup"><span data-stu-id="3b54c-165">In this example, the `findReversedWords` member of the pipeline uses [PLINQ](introduction-to-plinq.md) to process multiple items in the work list in parallel.</span></span> <span data-ttu-id="3b54c-166">在粗粒度的管道中使用细粒度并行可以提高总吞吐量。</span><span class="sxs-lookup"><span data-stu-id="3b54c-166">The use of fine-grained parallelism in a coarse-grained pipeline can improve overall throughput.</span></span>  
  
 <span data-ttu-id="3b54c-167">另外，还可以将数据流块连接到多个目标块，以创建“数据流网络”。</span><span class="sxs-lookup"><span data-stu-id="3b54c-167">You can also connect a source dataflow block to multiple target blocks to create a *dataflow network*.</span></span> <span data-ttu-id="3b54c-168"><xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> 方法采用一个 <xref:System.Predicate%601> 对象，该对象定义了目标块是否根据其值来接受每个消息。</span><span class="sxs-lookup"><span data-stu-id="3b54c-168">The overloaded version of the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> method takes a <xref:System.Predicate%601> object that defines whether the target block accepts each message based on its value.</span></span> <span data-ttu-id="3b54c-169">大多数充当源的数据流块类型按目标块连接的顺序向所有已连接的目标块提供消息，直到其中一个块接受此消息。</span><span class="sxs-lookup"><span data-stu-id="3b54c-169">Most dataflow block types that act as sources offer messages to all connected target blocks, in the order in which they were connected, until one of the blocks accepts that message.</span></span> <span data-ttu-id="3b54c-170">通过使用此筛选机制，您可以创建已连接数据流块的系统，指示某些数据通过一条路径，其他数据通过另一条路径。</span><span class="sxs-lookup"><span data-stu-id="3b54c-170">By using this filtering mechanism, you can create systems of connected dataflow blocks that direct certain data through one path and other data through another path.</span></span> <span data-ttu-id="3b54c-171">有关使用筛选来创建数据流网络的示例，请参阅[演练：在 Windows 窗体应用程序中使用数据流](walkthrough-using-dataflow-in-a-windows-forms-application.md)。</span><span class="sxs-lookup"><span data-stu-id="3b54c-171">For an example that uses filtering to create a dataflow network, see [Walkthrough: Using Dataflow in a Windows Forms Application](walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b54c-172">请参阅</span><span class="sxs-lookup"><span data-stu-id="3b54c-172">See also</span></span>

- [<span data-ttu-id="3b54c-173">数据流</span><span class="sxs-lookup"><span data-stu-id="3b54c-173">Dataflow</span></span>](dataflow-task-parallel-library.md)
