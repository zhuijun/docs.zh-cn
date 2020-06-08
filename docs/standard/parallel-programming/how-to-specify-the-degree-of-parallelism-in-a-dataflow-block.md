---
title: 如何：指定数据流块中的并行度
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow block, specifying parallelism in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, specifying parallelism
ms.assetid: e4088541-ee05-40db-95f5-147cfe62fde7
ms.openlocfilehash: 75302c98177a92b921996944f2862298fc612f31
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288103"
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a><span data-ttu-id="cff1d-102">如何：指定数据流块中的并行度</span><span class="sxs-lookup"><span data-stu-id="cff1d-102">How to: Specify the Degree of Parallelism in a Dataflow Block</span></span>
<span data-ttu-id="cff1d-103">本文档介绍如何设置 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> 属性使执行数据流块一次处理多条消息。</span><span class="sxs-lookup"><span data-stu-id="cff1d-103">This document describes how to set the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> property to enable an execution dataflow block to process more than one message at a time.</span></span> <span data-ttu-id="cff1d-104">当数据流块需要执行长时间运行的计算并且可从并行处理消息中获益时，这种做法很有用。</span><span class="sxs-lookup"><span data-stu-id="cff1d-104">Doing this is useful when you have a dataflow block that performs a long-running computation and can benefit from processing messages in parallel.</span></span> <span data-ttu-id="cff1d-105">此示例使用 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> 类并发执行多个数据流操作；但是，您可以对 TPL 数据流库提供的任何预定义的执行块类型（<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>、<xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>）指定最大并行度。</span><span class="sxs-lookup"><span data-stu-id="cff1d-105">This example uses the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> class to perform multiple dataflow operations concurrently; however, you can specify the maximum degree of parallelism in any of the predefined execution block types that the TPL Dataflow Library provides, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a><span data-ttu-id="cff1d-106">示例</span><span class="sxs-lookup"><span data-stu-id="cff1d-106">Example</span></span>  
 <span data-ttu-id="cff1d-107">下面的示例执行两个数据流计算并输出每个计算所需的运行时间。</span><span class="sxs-lookup"><span data-stu-id="cff1d-107">The following example performs two dataflow computations and prints the elapsed time that is required for each computation.</span></span> <span data-ttu-id="cff1d-108">第一个计算指定最大并行度为 1，这是默认值。</span><span class="sxs-lookup"><span data-stu-id="cff1d-108">The first computation specifies a maximum degree of parallelism of 1, which is the default.</span></span> <span data-ttu-id="cff1d-109">最大并行度 1 会使数据流块按顺序处理消息。</span><span class="sxs-lookup"><span data-stu-id="cff1d-109">A maximum degree of parallelism of 1 causes the dataflow block to process messages serially.</span></span> <span data-ttu-id="cff1d-110">第二个计算与第一个类似，但指定的最大并行度与可用处理器的数量相等。</span><span class="sxs-lookup"><span data-stu-id="cff1d-110">The second computation resembles the first, except that it specifies a maximum degree of parallelism that is equal to the number of available processors.</span></span> <span data-ttu-id="cff1d-111">这使数据流块能够并行执行多个操作。</span><span class="sxs-lookup"><span data-stu-id="cff1d-111">This enables the dataflow block to perform multiple operations in parallel.</span></span>  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="cff1d-112">可靠编程</span><span class="sxs-lookup"><span data-stu-id="cff1d-112">Robust Programming</span></span>  
 <span data-ttu-id="cff1d-113">默认情况下，每个预定义的数据流块会按照接收消息的顺序将消息传播出去。</span><span class="sxs-lookup"><span data-stu-id="cff1d-113">By default, each predefined dataflow block propagates out messages in the order in which the messages are received.</span></span>  <span data-ttu-id="cff1d-114">虽然在指定的最大并行度大于 1 时会同时处理多条消息，但这些消息仍然按被接收的顺序进行传播。</span><span class="sxs-lookup"><span data-stu-id="cff1d-114">Although multiple messages are processed simultaneously when you specify a maximum degree of parallelism that is greater than 1, they are still propagated out in the order in which they are received.</span></span>  
  
 <span data-ttu-id="cff1d-115">由于 <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> 属性表示最大并行度，因此数据流块执行时的并行度可能小于指定的值。</span><span class="sxs-lookup"><span data-stu-id="cff1d-115">Because the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> property represents the maximum degree of parallelism, the dataflow block might execute with a lesser degree of parallelism than you specify.</span></span> <span data-ttu-id="cff1d-116">为了满足功能需求或需要考虑可用系统资源不足的问题时，数据流块可以使用较小的并行度。</span><span class="sxs-lookup"><span data-stu-id="cff1d-116">The dataflow block can use a lesser degree of parallelism to meet its functional requirements or to account for a lack of available system resources.</span></span> <span data-ttu-id="cff1d-117">数据流块选择的并行度从不会大于您指定的值。</span><span class="sxs-lookup"><span data-stu-id="cff1d-117">A dataflow block never chooses a greater degree of parallelism than you specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff1d-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cff1d-118">See also</span></span>

- [<span data-ttu-id="cff1d-119">数据流</span><span class="sxs-lookup"><span data-stu-id="cff1d-119">Dataflow</span></span>](dataflow-task-parallel-library.md)
