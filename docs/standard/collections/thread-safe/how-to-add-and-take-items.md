---
title: 如何：在 BlockingCollection 中逐个添加和取出项
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
ms.openlocfilehash: f895be4c20a0cccad23e27db3d488355a614cbfc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287882"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a><span data-ttu-id="42ba6-102">如何：在 BlockingCollection 中逐个添加和取出项</span><span class="sxs-lookup"><span data-stu-id="42ba6-102">How to: Add and Take Items Individually from a BlockingCollection</span></span>
<span data-ttu-id="42ba6-103">此示例展示了如何以阻止性和非阻止性方式在 <xref:System.Collections.Concurrent.BlockingCollection%601> 中添加和删除项。</span><span class="sxs-lookup"><span data-stu-id="42ba6-103">This example shows how to add and remove items from a <xref:System.Collections.Concurrent.BlockingCollection%601> in both a blocking and a non-blocking manner.</span></span> <span data-ttu-id="42ba6-104">有关 <xref:System.Collections.Concurrent.BlockingCollection%601> 的详细信息，请参阅 [BlockingCollection 概述](blockingcollection-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="42ba6-104">For more information on <xref:System.Collections.Concurrent.BlockingCollection%601>, see [BlockingCollection Overview](blockingcollection-overview.md).</span></span>  
  
 <span data-ttu-id="42ba6-105">有关如何枚举 <xref:System.Collections.Concurrent.BlockingCollection%601> 直至其为空且不再添加更多元素的示例，请参阅[如何：使用 ForEach 移除 BlockingCollection 中的项](how-to-use-foreach-to-remove.md)。</span><span class="sxs-lookup"><span data-stu-id="42ba6-105">For an example of how to enumerate a <xref:System.Collections.Concurrent.BlockingCollection%601> until it is empty and no more elements will be added, see [How to: Use ForEach to Remove Items in a BlockingCollection](how-to-use-foreach-to-remove.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="42ba6-106">示例</span><span class="sxs-lookup"><span data-stu-id="42ba6-106">Example</span></span>  
 <span data-ttu-id="42ba6-107">第一个示例展示了如何添加和取出项，以便在集合暂时为空（取出时）或达到最大容量（添加时），或超过指定超时期限时，阻止相应操作。</span><span class="sxs-lookup"><span data-stu-id="42ba6-107">This first example shows how to add and take items so that the operations will block if the collection is either temporarily empty (when taking) or at maximum capacity (when adding), or if a specified timeout period has elapsed.</span></span> <span data-ttu-id="42ba6-108">注意，仅当已创建 BlockingCollection 且构造函数中指定了最大容量时，才会启用在达到最大容量时进行阻止的功能。</span><span class="sxs-lookup"><span data-stu-id="42ba6-108">Note that blocking on maximum capacity is only enabled when the BlockingCollection has been created with a maximum capacity specified in the constructor.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="42ba6-109">示例</span><span class="sxs-lookup"><span data-stu-id="42ba6-109">Example</span></span>  
 <span data-ttu-id="42ba6-110">第二个示例演示如何添加和取出项以便不会阻止操作。</span><span class="sxs-lookup"><span data-stu-id="42ba6-110">This second example shows how to add and take items so that the operations will not block.</span></span> <span data-ttu-id="42ba6-111">如果没有任何项、已达到绑定集合的最大容量或已超过超时期限，<xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> 或 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> 操作返回 false。</span><span class="sxs-lookup"><span data-stu-id="42ba6-111">If no item is present, maximum capacity on a bounded collection has been reached, or the timeout period has elapsed, then the <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> or <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operation returns false.</span></span> <span data-ttu-id="42ba6-112">这样一来，线程可以暂时执行其他一些有用的工作，并在稍后再次尝试检索新项，或尝试添加先前无法添加的相同项。</span><span class="sxs-lookup"><span data-stu-id="42ba6-112">This allows the thread to do some other useful work for a while and then try again later to either retrieve a new item, or try to add the same item that could not be added previously.</span></span> <span data-ttu-id="42ba6-113">该程序还演示如何在访问 <xref:System.Collections.Concurrent.BlockingCollection%601> 时实现取消。</span><span class="sxs-lookup"><span data-stu-id="42ba6-113">The program also demonstrates how to implement cancellation when accessing a <xref:System.Collections.Concurrent.BlockingCollection%601>.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a><span data-ttu-id="42ba6-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="42ba6-114">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="42ba6-115">BlockingCollection 概述</span><span class="sxs-lookup"><span data-stu-id="42ba6-115">BlockingCollection Overview</span></span>](blockingcollection-overview.md)
