---
title: 使用 foreach 删除 BlockingCollection 中的项
ms.date: 05/04/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collection
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
ms.openlocfilehash: 46638d2cd8078fefebc0eacc4b8f7798ffe178ff
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288896"
---
# <a name="use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="f3fb8-102">使用 foreach 删除 BlockingCollection 中的项</span><span class="sxs-lookup"><span data-stu-id="f3fb8-102">Use foreach to remove items in a BlockingCollection</span></span>

<span data-ttu-id="f3fb8-103">除了使用 <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> 和 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> 方法从 <xref:System.Collections.Concurrent.BlockingCollection%601> 中提取项之外，还可结合使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md)（在 Visual Basic 中为 [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md)）和 <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> 删除项，直至添加完成且集合为空。</span><span class="sxs-lookup"><span data-stu-id="f3fb8-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="f3fb8-104">由于与典型的 `foreach` (`For Each`) 循环不同，此枚举器通过删除项来修改源集合，因此将其称作*转变枚举*或*耗用枚举*。</span><span class="sxs-lookup"><span data-stu-id="f3fb8-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>

## <a name="example"></a><span data-ttu-id="f3fb8-105">示例</span><span class="sxs-lookup"><span data-stu-id="f3fb8-105">Example</span></span>

<span data-ttu-id="f3fb8-106">以下示例演示如何使用 `foreach` (`For Each`) 循环删除 <xref:System.Collections.Concurrent.BlockingCollection%601> 中的所有项。</span><span class="sxs-lookup"><span data-stu-id="f3fb8-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

<span data-ttu-id="f3fb8-107">此示例将 `foreach` 循环与耗用线程中的 <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> 方法结合使用，这会导致在枚举每个项时将其从集合中删除。</span><span class="sxs-lookup"><span data-stu-id="f3fb8-107">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="f3fb8-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> 随时限制集合中所包含的最大项数。</span><span class="sxs-lookup"><span data-stu-id="f3fb8-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="f3fb8-109">按照此方式枚举集合会在没有项可用或集合为空时阻止使用者线程。</span><span class="sxs-lookup"><span data-stu-id="f3fb8-109">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="f3fb8-110">在此示例中，由于制造者线程添加项的速度快于消耗项的速度，因此不需要考虑阻止问题。</span><span class="sxs-lookup"><span data-stu-id="f3fb8-110">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>

<span data-ttu-id="f3fb8-111"><xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> 返回了 `IEnumerable<T>`，因此无法保证顺序。</span><span class="sxs-lookup"><span data-stu-id="f3fb8-111">The <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> returns an `IEnumerable<T>`, thus order cannot be guaranteed.</span></span> <span data-ttu-id="f3fb8-112">但是，在内部将 <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> 用作基础集合类型，这将按照先进先出 (FIFO) 的顺序取消对象的排队。</span><span class="sxs-lookup"><span data-stu-id="f3fb8-112">However, internally a <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> is used as the underlying collection type - which will dequeue objects following first-in-first-out (FIFO) ordering.</span></span> <span data-ttu-id="f3fb8-113">如果对 <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> 进行了并发调用，这些调用会争用。</span><span class="sxs-lookup"><span data-stu-id="f3fb8-113">If concurrent calls to <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> are made, they will compete.</span></span> <span data-ttu-id="f3fb8-114">无法在一个枚举中观察到在另一个枚举中使用（已取消排队）的项目。</span><span class="sxs-lookup"><span data-stu-id="f3fb8-114">One item consumed (dequeued) in one enumeration cannot be observed in the other.</span></span>

<span data-ttu-id="f3fb8-115">若要枚举集合而不对其进行修改，只需使用 `foreach` (`For Each`) 即可，无需使用 <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f3fb8-115">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="f3fb8-116">但是，务必要了解此类枚举表示的是某个精确时间点的集合快照。</span><span class="sxs-lookup"><span data-stu-id="f3fb8-116">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="f3fb8-117">如果其他线程在你执行循环的同时添加或删除项，则循环可能不会表示集合的实际状态。</span><span class="sxs-lookup"><span data-stu-id="f3fb8-117">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3fb8-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="f3fb8-118">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="f3fb8-119">并行编程</span><span class="sxs-lookup"><span data-stu-id="f3fb8-119">Parallel Programming</span></span>](../../parallel-programming/index.md)
