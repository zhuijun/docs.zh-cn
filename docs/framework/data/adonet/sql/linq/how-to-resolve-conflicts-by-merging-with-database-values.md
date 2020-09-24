---
title: 如何：通过与数据库值合并解决冲突
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
ms.openlocfilehash: fb77c4a23a4c4fa93dc55e63858ee41783c197ee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166178"
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a><span data-ttu-id="5e341-102">如何：通过与数据库值合并解决冲突</span><span class="sxs-lookup"><span data-stu-id="5e341-102">How to: Resolve Conflicts by Merging with Database Values</span></span>

<span data-ttu-id="5e341-103">若要先对帐预期数据库值与实际数据库值之间的差异，再尝试重新提交更改，则可以使用 <xref:System.Data.Linq.RefreshMode.KeepChanges> 将数据库值与当前客户端成员值合并。</span><span class="sxs-lookup"><span data-stu-id="5e341-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepChanges> to merge database values with the current client member values.</span></span> <span data-ttu-id="5e341-104">有关详细信息，请参阅 [乐观 Concurrency：概述](optimistic-concurrency-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="5e341-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e341-105">在所有情况下，都会先通过从数据库中检索更新后的数据来刷新客户端上的记录。</span><span class="sxs-lookup"><span data-stu-id="5e341-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="5e341-106">此操作确保了下一次更新尝试将通过相同的并发检查。</span><span class="sxs-lookup"><span data-stu-id="5e341-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e341-107">示例</span><span class="sxs-lookup"><span data-stu-id="5e341-107">Example</span></span>  

 <span data-ttu-id="5e341-108">在本方案中，当 User1 尝试提交更改时将引发 <xref:System.Data.Linq.ChangeConflictException> 异常，原因是 User2 同时已更改了 Assistant 和 Department 列。</span><span class="sxs-lookup"><span data-stu-id="5e341-108">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="5e341-109">下表说明了这种情况。</span><span class="sxs-lookup"><span data-stu-id="5e341-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="5e341-110">Manager</span><span class="sxs-lookup"><span data-stu-id="5e341-110">Manager</span></span>|<span data-ttu-id="5e341-111">Assistant</span><span class="sxs-lookup"><span data-stu-id="5e341-111">Assistant</span></span>|<span data-ttu-id="5e341-112">部门</span><span class="sxs-lookup"><span data-stu-id="5e341-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="5e341-113">原始数据库在被 User1 和 User2 查询时的状态。</span><span class="sxs-lookup"><span data-stu-id="5e341-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="5e341-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="5e341-114">Alfreds</span></span>|<span data-ttu-id="5e341-115">Maria</span><span class="sxs-lookup"><span data-stu-id="5e341-115">Maria</span></span>|<span data-ttu-id="5e341-116">Sales</span><span class="sxs-lookup"><span data-stu-id="5e341-116">Sales</span></span>|  
|<span data-ttu-id="5e341-117">User1 准备提交这些更改。</span><span class="sxs-lookup"><span data-stu-id="5e341-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="5e341-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="5e341-118">Alfred</span></span>||<span data-ttu-id="5e341-119">Marketing</span><span class="sxs-lookup"><span data-stu-id="5e341-119">Marketing</span></span>|  
|<span data-ttu-id="5e341-120">User2 已经提交了这些更改。</span><span class="sxs-lookup"><span data-stu-id="5e341-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="5e341-121">Mary</span><span class="sxs-lookup"><span data-stu-id="5e341-121">Mary</span></span>|<span data-ttu-id="5e341-122">服务</span><span class="sxs-lookup"><span data-stu-id="5e341-122">Service</span></span>|  
  
 <span data-ttu-id="5e341-123">User1 决定通过将数据库值与当前客户端成员值合并来解决此冲突。</span><span class="sxs-lookup"><span data-stu-id="5e341-123">User1 decides to resolve this conflict by merging database values with the current client member values.</span></span> <span data-ttu-id="5e341-124">结果将是，数据库值仅在当前变更集也修改了该值时才会被覆盖。</span><span class="sxs-lookup"><span data-stu-id="5e341-124">The result will be that database values are overwritten only when the current changeset has also modified that value.</span></span>  
  
 <span data-ttu-id="5e341-125">User1 通过使用 <xref:System.Data.Linq.RefreshMode.KeepChanges> 解决了此冲突后，数据库中的结果将如下表所示：</span><span class="sxs-lookup"><span data-stu-id="5e341-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepChanges>, the result in the database is as in the following table:</span></span>  
  
||<span data-ttu-id="5e341-126">Manager</span><span class="sxs-lookup"><span data-stu-id="5e341-126">Manager</span></span>|<span data-ttu-id="5e341-127">Assistant</span><span class="sxs-lookup"><span data-stu-id="5e341-127">Assistant</span></span>|<span data-ttu-id="5e341-128">部门</span><span class="sxs-lookup"><span data-stu-id="5e341-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="5e341-129">解决冲突后的新状态。</span><span class="sxs-lookup"><span data-stu-id="5e341-129">New state after conflict resolution.</span></span>|<span data-ttu-id="5e341-130">Alfred</span><span class="sxs-lookup"><span data-stu-id="5e341-130">Alfred</span></span><br /><br /> <span data-ttu-id="5e341-131">（来自 User1）</span><span class="sxs-lookup"><span data-stu-id="5e341-131">(from User1)</span></span>|<span data-ttu-id="5e341-132">Mary</span><span class="sxs-lookup"><span data-stu-id="5e341-132">Mary</span></span><br /><br /> <span data-ttu-id="5e341-133">（来自 User2）</span><span class="sxs-lookup"><span data-stu-id="5e341-133">(from User2)</span></span>|<span data-ttu-id="5e341-134">Marketing</span><span class="sxs-lookup"><span data-stu-id="5e341-134">Marketing</span></span><br /><br /> <span data-ttu-id="5e341-135">（来自 User1）</span><span class="sxs-lookup"><span data-stu-id="5e341-135">(from User1)</span></span>|  
  
 <span data-ttu-id="5e341-136">下面的示例演示如何将数据库值与当前客户端成员值合并（除非此客户端也已经更改了该值）。</span><span class="sxs-lookup"><span data-stu-id="5e341-136">The following example shows how to merge database values with the current client member values (unless the client has also changed that value).</span></span> <span data-ttu-id="5e341-137">未对各个成员冲突进行检查或自定义处理。</span><span class="sxs-lookup"><span data-stu-id="5e341-137">No inspection or custom handling of individual member conflicts occurs.</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="5e341-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="5e341-138">See also</span></span>

- [<span data-ttu-id="5e341-139">如何：通过重写数据库值解决冲突</span><span class="sxs-lookup"><span data-stu-id="5e341-139">How to: Resolve Conflicts by Overwriting Database Values</span></span>](how-to-resolve-conflicts-by-overwriting-database-values.md)
- [<span data-ttu-id="5e341-140">如何：通过保留数据库值解决冲突</span><span class="sxs-lookup"><span data-stu-id="5e341-140">How to: Resolve Conflicts by Retaining Database Values</span></span>](how-to-resolve-conflicts-by-retaining-database-values.md)
- [<span data-ttu-id="5e341-141">如何：管理更改冲突</span><span class="sxs-lookup"><span data-stu-id="5e341-141">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
