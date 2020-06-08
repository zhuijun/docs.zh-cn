---
title: 如何：使用屏障来使并发操作保持同步
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
ms.openlocfilehash: 2e13dfb277807eb0a9f256f74c2845f5a4d2a047
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279292"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="8972a-102">如何：使用屏障来使并发操作保持同步</span><span class="sxs-lookup"><span data-stu-id="8972a-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>
<span data-ttu-id="8972a-103">下面的示例展示了如何将并发任务与 <xref:System.Threading.Barrier> 同步。</span><span class="sxs-lookup"><span data-stu-id="8972a-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8972a-104">示例</span><span class="sxs-lookup"><span data-stu-id="8972a-104">Example</span></span>  
 <span data-ttu-id="8972a-105">下面的程序用于统计两个线程使用随机算法重新随机选择字词，分别在同一阶段查找一半解决方案时所需的迭代次数（或阶段数）。</span><span class="sxs-lookup"><span data-stu-id="8972a-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="8972a-106">在每个线程随机选择字词后，屏障后阶段操作会比较两个结果，以确定整个句子是否按正确的字词顺序呈现。</span><span class="sxs-lookup"><span data-stu-id="8972a-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="8972a-107"><xref:System.Threading.Barrier> 对象可防止并行操作中的各个任务在所有任务到达屏障前继续执行。</span><span class="sxs-lookup"><span data-stu-id="8972a-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="8972a-108">如果并行操作分阶段执行，且每个阶段需要在任务之间进行同步，此对象就很有用。</span><span class="sxs-lookup"><span data-stu-id="8972a-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="8972a-109">在此示例中，操作分两个阶段执行。</span><span class="sxs-lookup"><span data-stu-id="8972a-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="8972a-110">在第一阶段中，每个任务都用数据填充缓冲部分。</span><span class="sxs-lookup"><span data-stu-id="8972a-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="8972a-111">在每个任务填充完缓冲部分后，任务向屏障发出信号，指明可以继续执行，然后等待。</span><span class="sxs-lookup"><span data-stu-id="8972a-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="8972a-112">当所有任务都向屏障发出信号后，就会取消阻止它们，此时第二阶段开始。</span><span class="sxs-lookup"><span data-stu-id="8972a-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="8972a-113">屏障是必要的，因为第二阶段要求每个任务都有权访问此时生成的所有数据。</span><span class="sxs-lookup"><span data-stu-id="8972a-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="8972a-114">如果没有屏障，首先完成的任务可能会尝试从其他任务尚未填充的缓冲读取数据。</span><span class="sxs-lookup"><span data-stu-id="8972a-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="8972a-115">可以按照这种方式同步任意数量的阶段。</span><span class="sxs-lookup"><span data-stu-id="8972a-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8972a-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8972a-116">See also</span></span>

- [<span data-ttu-id="8972a-117">用于并行编程的数据结构</span><span class="sxs-lookup"><span data-stu-id="8972a-117">Data Structures for Parallel Programming</span></span>](../parallel-programming/data-structures-for-parallel-programming.md)
