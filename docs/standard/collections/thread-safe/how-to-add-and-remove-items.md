---
title: 如何：在 ConcurrentDictionary 中添加和移除项
ms.date: 05/04/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
ms.openlocfilehash: 6c093e907e43f9f2b978624a986dfe5d8a49869f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287895"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a><span data-ttu-id="51a38-102">如何：在 ConcurrentDictionary 中添加和移除项</span><span class="sxs-lookup"><span data-stu-id="51a38-102">How to: Add and Remove Items from a ConcurrentDictionary</span></span>

<span data-ttu-id="51a38-103">本示例演示如何在 <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> 中添加、检索、更新和删除项。</span><span class="sxs-lookup"><span data-stu-id="51a38-103">This example shows how to add, retrieve, update, and remove items from a <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="51a38-104">此集合类是一个线程安全实现。</span><span class="sxs-lookup"><span data-stu-id="51a38-104">This collection class is a thread-safe implementation.</span></span> <span data-ttu-id="51a38-105">建议在多个线程可能同时尝试访问元素时使用此集合类。</span><span class="sxs-lookup"><span data-stu-id="51a38-105">We recommend that you use it whenever multiple threads might be attempting to access the elements concurrently.</span></span>

<span data-ttu-id="51a38-106"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> 提供了多个便捷的方法，这些方法使代码在尝试添加或移除数据之前无需先检查键是否存在。</span><span class="sxs-lookup"><span data-stu-id="51a38-106"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> provides several convenience methods that make it unnecessary for code to first check whether a key exists before it attempts to add or remove data.</span></span> <span data-ttu-id="51a38-107">下表列出了这些便捷的方法，并说明在何种情况下这些方法。</span><span class="sxs-lookup"><span data-stu-id="51a38-107">The following table lists these convenience methods and describes when to use them.</span></span>

| <span data-ttu-id="51a38-108">方法</span><span class="sxs-lookup"><span data-stu-id="51a38-108">Method</span></span> | <span data-ttu-id="51a38-109">何时使用…</span><span class="sxs-lookup"><span data-stu-id="51a38-109">Use when…</span></span> |
|--|--|
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> | <span data-ttu-id="51a38-110">需要为指定键添加新值，如果此键已存在，则需要替换其值。</span><span class="sxs-lookup"><span data-stu-id="51a38-110">You want to add a new value for a specified key and, if the key already exists, you want to replace its value.</span></span> |
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> | <span data-ttu-id="51a38-111">需要检索指定键的现有值，如果此键不存在，则需要指定一个键/值对。</span><span class="sxs-lookup"><span data-stu-id="51a38-111">You want to retrieve the existing value for a specified key and, if the key does not exist, you want to specify a key/value pair.</span></span> |
| <span data-ttu-id="51a38-112"><xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A></span><span class="sxs-lookup"><span data-stu-id="51a38-112"><xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A></span></span> | <span data-ttu-id="51a38-113">需要添加、获取、更新或移除键/值对，如果此键已存在或因任何其他原因导致尝试失败，则需执行某种备选操作。</span><span class="sxs-lookup"><span data-stu-id="51a38-113">You want to add, get, update, or remove a key/value pair, and, if the key already exists or the attempt fails for any other reason, you want to take some alternative action.</span></span> |

## <a name="example"></a><span data-ttu-id="51a38-114">示例</span><span class="sxs-lookup"><span data-stu-id="51a38-114">Example</span></span>

<span data-ttu-id="51a38-115">下面的示例使用两个 <xref:System.Threading.Tasks.Task> 实例将一些元素同时添加到 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 中，然后输出所有内容，指明元素已成功添加。</span><span class="sxs-lookup"><span data-stu-id="51a38-115">The following example uses two <xref:System.Threading.Tasks.Task> instances to add some elements to a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> concurrently, and then outputs all of the contents to show that the elements were added successfully.</span></span> <span data-ttu-id="51a38-116">此示例还演示如何使用 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>、<xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> 和 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> 方法在集合中添加、更新、检索和删除项目。</span><span class="sxs-lookup"><span data-stu-id="51a38-116">The example also shows how to use the <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>, and <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> methods to add, update, and retrieve items from the collection.</span></span>

[!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
[!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]

<span data-ttu-id="51a38-117"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> 专为多线程方案而设计。</span><span class="sxs-lookup"><span data-stu-id="51a38-117"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> is designed for multithreaded scenarios.</span></span> <span data-ttu-id="51a38-118">无需在代码中使用锁定即可在集合中添加或移除项。</span><span class="sxs-lookup"><span data-stu-id="51a38-118">You do not have to use locks in your code to add or remove items from the collection.</span></span> <span data-ttu-id="51a38-119">但始终可能出现以下情况：一个线程检索一个值，而另一线程通过为同一键赋予新值来立即更新集合。</span><span class="sxs-lookup"><span data-stu-id="51a38-119">However, it is always possible for one thread to retrieve a value, and another thread to immediately update the collection by giving the same key a new value.</span></span>

<span data-ttu-id="51a38-120">此外，尽管 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 的所有方法都是线程安全的，但并非所有方法都是原子的，尤其是 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> 和 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>。</span><span class="sxs-lookup"><span data-stu-id="51a38-120">Also, although all methods of <xref:System.Collections.Concurrent.ConcurrentDictionary%602> are thread-safe, not all methods are atomic, specifically <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> and <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>.</span></span> <span data-ttu-id="51a38-121">传递给这些方法的用户委托将在词典的内部锁之外调用（此操作旨在防止未知代码阻止所有线程）。</span><span class="sxs-lookup"><span data-stu-id="51a38-121">The user delegate that is passed to these methods is invoked outside of the dictionary's internal lock (this is done to prevent unknown code from blocking all threads).</span></span> <span data-ttu-id="51a38-122">因此，可能发生以下事件序列：</span><span class="sxs-lookup"><span data-stu-id="51a38-122">Therefore, it is possible for this sequence of events to occur:</span></span>

1. <span data-ttu-id="51a38-123">threadA 调用 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>，未找到项，通过调用 `valueFactory` 委托创建要添加的新项  。</span><span class="sxs-lookup"><span data-stu-id="51a38-123">_threadA_ calls <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, finds no item and creates a new item to add by invoking the `valueFactory` delegate.</span></span>

1. <span data-ttu-id="51a38-124">threadB 并发调用 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>，其 `valueFactory` 委托受到调用，并且它在 threadA 之前到达内部锁，并将其新键值对添加到词典中   。</span><span class="sxs-lookup"><span data-stu-id="51a38-124">_threadB_ calls <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> concurrently, its `valueFactory` delegate is invoked and it arrives at the internal lock before _threadA_, and so its new key-value pair is added to the dictionary.</span></span>

1. <span data-ttu-id="51a38-125">threadA 的用户委托完成，此线程到达锁位置，但现在发现已有项存在  。</span><span class="sxs-lookup"><span data-stu-id="51a38-125">_threadA's_ user delegate completes, and the thread arrives at the lock, but now sees that the item exists already.</span></span>

1. <span data-ttu-id="51a38-126">threadA 执行“Get”，返回之前由 threadB 添加的数据   。</span><span class="sxs-lookup"><span data-stu-id="51a38-126">_threadA_ performs a "Get" and returns the data that was previously added by _threadB_.</span></span>

<span data-ttu-id="51a38-127">因此，无法保证 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> 返回的数据与线程的 `valueFactory` 创建的数据相同。</span><span class="sxs-lookup"><span data-stu-id="51a38-127">Therefore, it is not guaranteed that the data that is returned by <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> is the same data that was created by the thread's `valueFactory`.</span></span> <span data-ttu-id="51a38-128">调用 <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> 时可能发生相似的事件序列。</span><span class="sxs-lookup"><span data-stu-id="51a38-128">A similar sequence of events can occur when <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="51a38-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="51a38-129">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="51a38-130">线程安全集合</span><span class="sxs-lookup"><span data-stu-id="51a38-130">Thread-Safe Collections</span></span>](index.md)
