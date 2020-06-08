---
title: 如何：向集合添加限制和阻塞功能
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
ms.openlocfilehash: 57a01726e897f4ddbf8df5ede53609c198012d80
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287869"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a><span data-ttu-id="f1202-102">如何：向集合添加限制和阻塞功能</span><span class="sxs-lookup"><span data-stu-id="f1202-102">How to: Add Bounding and Blocking Functionality to a Collection</span></span>
<span data-ttu-id="f1202-103">本示例演示如何通过实现类中的 <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> 接口，然后将类实例用作 <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> 的内部存储机制，来向自定义集合类添加限制和阻塞功能。</span><span class="sxs-lookup"><span data-stu-id="f1202-103">This example shows how to add bounding and blocking functionality to a custom collection class by implementing the <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> interface in the class, and then using a class instance as the internal storage mechanism for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f1202-104">有关限制和阻塞的详细信息，请参阅 [BlockingCollection 概述](blockingcollection-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f1202-104">For more information about bounding and blocking, see [BlockingCollection Overview](blockingcollection-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1202-105">示例</span><span class="sxs-lookup"><span data-stu-id="f1202-105">Example</span></span>  
 <span data-ttu-id="f1202-106">自定义集合类是一个基本优先级别队列，优先级别在其中表示为 <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> 对象的数组。</span><span class="sxs-lookup"><span data-stu-id="f1202-106">The custom collection class is a basic priority queue in which the priority levels are represented as an array of <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="f1202-107">在每个队列中不进行其他排序。</span><span class="sxs-lookup"><span data-stu-id="f1202-107">No additional ordering is performed within each queue.</span></span>  
  
 <span data-ttu-id="f1202-108">客户端代码中启动了三个任务。</span><span class="sxs-lookup"><span data-stu-id="f1202-108">In the client code, three tasks are started.</span></span> <span data-ttu-id="f1202-109">第一个任务仅轮询键盘键击以便在执行过程中的任意时刻启用取消。</span><span class="sxs-lookup"><span data-stu-id="f1202-109">The first task just polls for keyboard strokes to enable cancellation at any point during execution.</span></span> <span data-ttu-id="f1202-110">第二个任务是制造者线程；它会向阻塞集合添加新项并根据随机值为每个项分配一个优先级。</span><span class="sxs-lookup"><span data-stu-id="f1202-110">The second task is the producer thread; it adds new items to the blocking collection and gives each item a priority based on a random value.</span></span> <span data-ttu-id="f1202-111">第三个任务在项可用时将其从集合中移除。</span><span class="sxs-lookup"><span data-stu-id="f1202-111">The third task removes items from the collection as they become available.</span></span>  
  
 <span data-ttu-id="f1202-112">可以通过使其中一个线程运行速度快于另一个线程来调整应用程序的行为。</span><span class="sxs-lookup"><span data-stu-id="f1202-112">You can adjust the behavior of the application by making one of the threads run faster than the other.</span></span> <span data-ttu-id="f1202-113">如果制造者运行速度更快，则在阻塞集合阻止添加项（如果该集合已包含构造函数中所指定的项数）时，你会注意到限制功能。</span><span class="sxs-lookup"><span data-stu-id="f1202-113">If the producer runs faster, you will notice the bounding functionality as the blocking collection prevents items from being added if it already contains the number of items that is specified in the constructor.</span></span> <span data-ttu-id="f1202-114">如果使用者运行速度更快，则在使用者等待添加新项时，你会注意到阻塞功能。</span><span class="sxs-lookup"><span data-stu-id="f1202-114">If the consumer runs faster, you will notice the blocking functionality as the consumer waits for a new item to be added.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 <span data-ttu-id="f1202-115">默认情况下，<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> 的存储为 <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f1202-115">By default, the storage for a <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> is <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1202-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f1202-116">See also</span></span>

- [<span data-ttu-id="f1202-117">线程安全集合</span><span class="sxs-lookup"><span data-stu-id="f1202-117">Thread-Safe Collections</span></span>](index.md)
