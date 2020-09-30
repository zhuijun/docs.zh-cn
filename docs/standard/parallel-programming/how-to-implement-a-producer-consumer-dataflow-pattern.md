---
title: 如何：实现生成方-使用方数据流模式
description: 了解如何使用 .NET 中的 TPL 数据流库实现生成方-使用方数据流模式。
ms.date: 09/24/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, implementing producer-consumer pattern
- Task Parallel Library, dataflows
- producer-consumer patterns, implementing [TPL]
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
ms.openlocfilehash: fc68d9e678dab88ec5008b6c15ef17a5d20f25ae
ms.sourcegitcommit: d04388f94dbcd756ffd608536c869aee3242cdb0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91206375"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a><span data-ttu-id="49d3b-103">如何：实现生成方-使用方数据流模式</span><span class="sxs-lookup"><span data-stu-id="49d3b-103">How to: Implement a producer-consumer dataflow pattern</span></span>

<span data-ttu-id="49d3b-104">本文介绍如何使用 TPL 数据流库实现生成方-使用方模式。</span><span class="sxs-lookup"><span data-stu-id="49d3b-104">In this article, you'll learn how to use the TPL dataflow library to implement a producer-consumer pattern.</span></span> <span data-ttu-id="49d3b-105">在此模式下，制造者向消息块发送消息，使用者从该块读取消息。</span><span class="sxs-lookup"><span data-stu-id="49d3b-105">In this pattern, the *producer* sends messages to a message block, and the *consumer* reads messages from that block.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="49d3b-106">示例</span><span class="sxs-lookup"><span data-stu-id="49d3b-106">Example</span></span>

<span data-ttu-id="49d3b-107">下面的示例演示使用数据流的基本制造者-使用者模型。</span><span class="sxs-lookup"><span data-stu-id="49d3b-107">The following example demonstrates a basic producer- consumer model that uses dataflow.</span></span> <span data-ttu-id="49d3b-108">`Produce` 方法将包含随机字节数据的数组写入 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> 对象，而 `Consume` 方法从 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> 对象中读取字节。</span><span class="sxs-lookup"><span data-stu-id="49d3b-108">The `Produce` method writes arrays that contain random bytes of data to a <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> object and the `Consume` method reads bytes from a <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="49d3b-109">通过对 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> 和 <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> 接口（而非其派生类型）的操作，可以编写可对多种数据流块类型执行的可重用代码。</span><span class="sxs-lookup"><span data-stu-id="49d3b-109">By acting on the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> and <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> interfaces, instead of their derived types, you can write reusable code that can act on a variety of dataflow block types.</span></span> <span data-ttu-id="49d3b-110">此示例使用 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 类。</span><span class="sxs-lookup"><span data-stu-id="49d3b-110">This example uses the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class.</span></span> <span data-ttu-id="49d3b-111">由于 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 类既充当源块又充当目标块，制造者和使用者可以使用共享对象来传输数据。</span><span class="sxs-lookup"><span data-stu-id="49d3b-111">Because the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> class acts as both a source block and as a target block, the producer and the consumer can use a shared object to transfer data.</span></span>

 <span data-ttu-id="49d3b-112">`Produce` 方法在循环中调用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> 方法，以将数据同步写入目标块。</span><span class="sxs-lookup"><span data-stu-id="49d3b-112">The `Produce` method calls the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> method in a loop to synchronously write data to the target block.</span></span> <span data-ttu-id="49d3b-113">在 `Produce` 方法将所有数据写入目标块后，它将调用 <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> 方法来表明此块将不再有其他数据可用。</span><span class="sxs-lookup"><span data-stu-id="49d3b-113">After the `Produce` method writes all data to the target block, it calls the <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> method to indicate that the block will never have additional data available.</span></span> <span data-ttu-id="49d3b-114">`Consume` 方法使用 [async](../../csharp/language-reference/keywords/async.md) 和 [await](../../csharp/language-reference/operators/await.md) 运算符（Visual Basic 中的 [Async](../../visual-basic/language-reference/modifiers/async.md) 和 [Await](../../visual-basic/language-reference/operators/await-operator.md)），异步计算从 <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> 对象收到的总字节数。</span><span class="sxs-lookup"><span data-stu-id="49d3b-114">The `Consume` method uses the [async](../../csharp/language-reference/keywords/async.md) and [await](../../csharp/language-reference/operators/await.md) operators ([Async](../../visual-basic/language-reference/modifiers/async.md) and [Await](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic) to asynchronously compute the total number of bytes that are received from the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> object.</span></span> <span data-ttu-id="49d3b-115">为了异步操作，`Consume` 方法会调用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> 方法，以便在源块有可用数据和源块不再有其他可用数据时收到通知。</span><span class="sxs-lookup"><span data-stu-id="49d3b-115">To act asynchronously, the `Consume` method calls the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> method to receive a notification when the source block has data available and when the source block will never have additional data available.</span></span>

 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]

## <a name="robust-programming"></a><span data-ttu-id="49d3b-116">可靠编程</span><span class="sxs-lookup"><span data-stu-id="49d3b-116">Robust programming</span></span>

 <span data-ttu-id="49d3b-117">前面的示例只使用一个使用者来处理源数据。</span><span class="sxs-lookup"><span data-stu-id="49d3b-117">The preceding example uses just one consumer to process the source data.</span></span> <span data-ttu-id="49d3b-118">如果您的应用程序中有多个使用者，请使用 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法从源块读取数据，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="49d3b-118">If you have multiple consumers in your application, use the <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method to read data from the source block, as shown in the following example.</span></span>

 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]

 <span data-ttu-id="49d3b-119">没有可用数据时，<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> 方法将返回 `False`。</span><span class="sxs-lookup"><span data-stu-id="49d3b-119">The <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> method returns `False` when no data is available.</span></span> <span data-ttu-id="49d3b-120">当多个使用者必须并发访问源块时，此机制可确保在调用 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> 后数据仍然可用。</span><span class="sxs-lookup"><span data-stu-id="49d3b-120">When multiple consumers must access the source block concurrently, this mechanism guarantees that data is still available after the call to <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="49d3b-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="49d3b-121">See also</span></span>

- [<span data-ttu-id="49d3b-122">数据流</span><span class="sxs-lookup"><span data-stu-id="49d3b-122">Dataflow</span></span>](dataflow-task-parallel-library.md)
