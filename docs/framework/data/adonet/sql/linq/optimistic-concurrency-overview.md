---
title: 乐观并发：概述
ms.date: 03/30/2017
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
ms.openlocfilehash: 7a1bc23d9f012b2f3541c1411a25b7527e696873
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169383"
---
# <a name="optimistic-concurrency-overview"></a><span data-ttu-id="f2415-102">乐观并发：概述</span><span class="sxs-lookup"><span data-stu-id="f2415-102">Optimistic Concurrency: Overview</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f2415-103">支持开放式并发控制。</span><span class="sxs-lookup"><span data-stu-id="f2415-103">supports optimistic concurrency control.</span></span> <span data-ttu-id="f2415-104">下表描述了适用于文档中的开放式并发的术语 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="f2415-104">The following table describes terms that apply to optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation:</span></span>  
  
|<span data-ttu-id="f2415-105">术语</span><span class="sxs-lookup"><span data-stu-id="f2415-105">Terms</span></span>|<span data-ttu-id="f2415-106">描述</span><span class="sxs-lookup"><span data-stu-id="f2415-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f2415-107">concurrency</span><span class="sxs-lookup"><span data-stu-id="f2415-107">concurrency</span></span>|<span data-ttu-id="f2415-108">两个或更多用户同时尝试更新同一数据库行的情形。</span><span class="sxs-lookup"><span data-stu-id="f2415-108">The situation in which two or more users at the same time try to update the same database row.</span></span>|  
|<span data-ttu-id="f2415-109">并发冲突 (concurrency conflict)</span><span class="sxs-lookup"><span data-stu-id="f2415-109">concurrency conflict</span></span>|<span data-ttu-id="f2415-110">两个或更多用户同时尝试向一行的一列或多列提交冲突值的情形。</span><span class="sxs-lookup"><span data-stu-id="f2415-110">The situation in which two or more users at the same time try to submit conflicting values to one or more columns of a row.</span></span>|  
|<span data-ttu-id="f2415-111">并发控制</span><span class="sxs-lookup"><span data-stu-id="f2415-111">concurrency control</span></span>|<span data-ttu-id="f2415-112">用于解决并发冲突的技术。</span><span class="sxs-lookup"><span data-stu-id="f2415-112">The technique used to resolve concurrency conflicts.</span></span>|  
|<span data-ttu-id="f2415-113">开放式并发控制</span><span class="sxs-lookup"><span data-stu-id="f2415-113">optimistic concurrency control</span></span>|<span data-ttu-id="f2415-114">先调查其他事务是否已更改了行中的值，再允许提交更改的技术。</span><span class="sxs-lookup"><span data-stu-id="f2415-114">The technique that first investigates whether other transactions have changed values in a row before permitting changes to be submitted.</span></span><br /><br /> <span data-ttu-id="f2415-115">与 *悲观并发控制*相反，它会锁定记录以避免并发冲突。</span><span class="sxs-lookup"><span data-stu-id="f2415-115">Contrast with *pessimistic concurrency control*, which locks the record to avoid concurrency conflicts.</span></span><br /><br /> <span data-ttu-id="f2415-116">所谓*乐观*控制，因为它会将一个事务干扰另一个事务的几率视为不太可能。</span><span class="sxs-lookup"><span data-stu-id="f2415-116">*Optimistic* control is so termed because it considers the chances of one transaction interfering with another to be unlikely.</span></span>|  
|<span data-ttu-id="f2415-117">冲突解决</span><span class="sxs-lookup"><span data-stu-id="f2415-117">conflict resolution</span></span>|<span data-ttu-id="f2415-118">通过重新查询数据库刷新出现冲突的项，然后协调差异的过程。</span><span class="sxs-lookup"><span data-stu-id="f2415-118">The process of refreshing a conflicting item by querying the database again and then reconciling differences.</span></span><br /><br /> <span data-ttu-id="f2415-119">刷新对象时，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 更改跟踪器会保留以下数据：</span><span class="sxs-lookup"><span data-stu-id="f2415-119">When an object is refreshed, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] change tracker holds the following data:</span></span><br /><br /> <span data-ttu-id="f2415-120">-最初从数据库获取并用于更新检查的值。</span><span class="sxs-lookup"><span data-stu-id="f2415-120">-   The values originally taken from the database and used for the update check.</span></span><br /><span data-ttu-id="f2415-121">-来自后续查询的新数据库值。</span><span class="sxs-lookup"><span data-stu-id="f2415-121">-   The new database values from the subsequent query.</span></span><br /><br /> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f2415-122">随后会确定相应对象是否发生冲突（即它的一个或多个成员值是否已发生更改）。</span><span class="sxs-lookup"><span data-stu-id="f2415-122">then determines whether the object is in conflict (that is, whether one or more of its member values has changed).</span></span> <span data-ttu-id="f2415-123">如果此对象发生冲突，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 下一步会确定它的哪些成员发生冲突。</span><span class="sxs-lookup"><span data-stu-id="f2415-123">If the object is in conflict, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] next determines which of its members are in conflict.</span></span><br /><br /> <span data-ttu-id="f2415-124">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 发现的任何成员冲突都会添加到冲突列表中。</span><span class="sxs-lookup"><span data-stu-id="f2415-124">Any member conflict that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] discovers is added to a conflict list.</span></span>|  
  
 <span data-ttu-id="f2415-125">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 对象模型中，当以下两个条件均为 true 时，将发生 *开放式并发冲突* ：</span><span class="sxs-lookup"><span data-stu-id="f2415-125">In the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model, an *optimistic concurrency conflict* occurs when both of the following conditions are true:</span></span>  
  
- <span data-ttu-id="f2415-126">客户端尝试向数据库提交更改。</span><span class="sxs-lookup"><span data-stu-id="f2415-126">The client tries to submit changes to the database.</span></span>  
  
- <span data-ttu-id="f2415-127">数据库中的一个或多个更新检查值自客户端上次读取它们以来已得到更新。</span><span class="sxs-lookup"><span data-stu-id="f2415-127">One or more update-check values have been updated in the database since the client last read them.</span></span>  
  
 <span data-ttu-id="f2415-128">此冲突的解决过程包括查明对象的哪些成员发生冲突，然后决定您希望如何进行处理。</span><span class="sxs-lookup"><span data-stu-id="f2415-128">Resolution of this conflict includes discovering which members of the object are in conflict, and then deciding what you want to do about it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2415-129">只有映射为 <xref:System.Data.Linq.Mapping.UpdateCheck.Always> 或 <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> 的成员才会参与开放式并发检查。</span><span class="sxs-lookup"><span data-stu-id="f2415-129">Only members mapped as <xref:System.Data.Linq.Mapping.UpdateCheck.Always> or <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> participate in optimistic concurrency checks.</span></span> <span data-ttu-id="f2415-130">对于标记为 <xref:System.Data.Linq.Mapping.UpdateCheck.Never> 的成员，不执行检查。</span><span class="sxs-lookup"><span data-stu-id="f2415-130">No check is performed for members marked <xref:System.Data.Linq.Mapping.UpdateCheck.Never>.</span></span> <span data-ttu-id="f2415-131">有关详细信息，请参阅 <xref:System.Data.Linq.Mapping.UpdateCheck>。</span><span class="sxs-lookup"><span data-stu-id="f2415-131">For more information, see <xref:System.Data.Linq.Mapping.UpdateCheck>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2415-132">示例</span><span class="sxs-lookup"><span data-stu-id="f2415-132">Example</span></span>  

 <span data-ttu-id="f2415-133">例如，在下面的情况中，User1 通过查询数据库中的某一行开始准备更新。</span><span class="sxs-lookup"><span data-stu-id="f2415-133">For example, in the following scenario, User1 starts to prepare an update by querying the database for a row.</span></span> <span data-ttu-id="f2415-134">User1 收到包含 Alfreds、Maria 和 Sales 值的一行。</span><span class="sxs-lookup"><span data-stu-id="f2415-134">User1 receives a row with values of Alfreds, Maria, and Sales.</span></span>  
  
 <span data-ttu-id="f2415-135">User1 希望将 Manager 列的值更改为 Alfred，将 Department 列的值更改为 Marketing。</span><span class="sxs-lookup"><span data-stu-id="f2415-135">User1 wants to change the value of the Manager column to Alfred and the value of the Department column to Marketing.</span></span> <span data-ttu-id="f2415-136">在 User2 将更改提交到数据库后，User1 才能提交这些更改。</span><span class="sxs-lookup"><span data-stu-id="f2415-136">Before User1 can submit those changes, User2 has submitted changes to the database.</span></span> <span data-ttu-id="f2415-137">所以，现在 Assistant 列的值已更改为 Mary，Department 列的值已更改为 Service。</span><span class="sxs-lookup"><span data-stu-id="f2415-137">So now the value of the Assistant column has been changed to Mary and the value of the Department column to Service.</span></span>  
  
 <span data-ttu-id="f2415-138">当 User1 现在尝试提交更改时，提交失败并且引发 <xref:System.Data.Linq.ChangeConflictException> 异常。</span><span class="sxs-lookup"><span data-stu-id="f2415-138">When User1 now tries to submit changes, the submission fails and a <xref:System.Data.Linq.ChangeConflictException> exception is thrown.</span></span> <span data-ttu-id="f2415-139">出现这种结果是因为 Assistant 列和 Department 列的数据库值并不是他们所预期的那些值。</span><span class="sxs-lookup"><span data-stu-id="f2415-139">This result occurs because the database values for the Assistant column and the Department column are not those that were expected.</span></span> <span data-ttu-id="f2415-140">表示 Assistant 和 Department 列的成员发生了冲突。</span><span class="sxs-lookup"><span data-stu-id="f2415-140">Members representing the Assistant and Department columns are in conflict.</span></span> <span data-ttu-id="f2415-141">下表对这种情形作了总结。</span><span class="sxs-lookup"><span data-stu-id="f2415-141">The following table summarizes the situation.</span></span>  
  
||<span data-ttu-id="f2415-142">Manager</span><span class="sxs-lookup"><span data-stu-id="f2415-142">Manager</span></span>|<span data-ttu-id="f2415-143">Assistant</span><span class="sxs-lookup"><span data-stu-id="f2415-143">Assistant</span></span>|<span data-ttu-id="f2415-144">部门</span><span class="sxs-lookup"><span data-stu-id="f2415-144">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="f2415-145">原始状态</span><span class="sxs-lookup"><span data-stu-id="f2415-145">Original state</span></span>|<span data-ttu-id="f2415-146">Alfreds</span><span class="sxs-lookup"><span data-stu-id="f2415-146">Alfreds</span></span>|<span data-ttu-id="f2415-147">Maria</span><span class="sxs-lookup"><span data-stu-id="f2415-147">Maria</span></span>|<span data-ttu-id="f2415-148">Sales</span><span class="sxs-lookup"><span data-stu-id="f2415-148">Sales</span></span>|  
|<span data-ttu-id="f2415-149">User1</span><span class="sxs-lookup"><span data-stu-id="f2415-149">User1</span></span>|<span data-ttu-id="f2415-150">Alfred</span><span class="sxs-lookup"><span data-stu-id="f2415-150">Alfred</span></span>||<span data-ttu-id="f2415-151">Marketing</span><span class="sxs-lookup"><span data-stu-id="f2415-151">Marketing</span></span>|  
|<span data-ttu-id="f2415-152">User2</span><span class="sxs-lookup"><span data-stu-id="f2415-152">User2</span></span>||<span data-ttu-id="f2415-153">Mary</span><span class="sxs-lookup"><span data-stu-id="f2415-153">Mary</span></span>|<span data-ttu-id="f2415-154">服务</span><span class="sxs-lookup"><span data-stu-id="f2415-154">Service</span></span>|  
  
 <span data-ttu-id="f2415-155">您可以用多种不同的方式来解决此类冲突。</span><span class="sxs-lookup"><span data-stu-id="f2415-155">You can resolve conflicts such as this in different ways.</span></span> <span data-ttu-id="f2415-156">有关详细信息，请参阅 [如何：管理更改冲突](how-to-manage-change-conflicts.md)。</span><span class="sxs-lookup"><span data-stu-id="f2415-156">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="conflict-detection-and-resolution-checklist"></a><span data-ttu-id="f2415-157">冲突检测和解决检查表</span><span class="sxs-lookup"><span data-stu-id="f2415-157">Conflict Detection and Resolution Checklist</span></span>  

 <span data-ttu-id="f2415-158">您可以检测和解决任意详细等级的冲突。</span><span class="sxs-lookup"><span data-stu-id="f2415-158">You can detect and resolve conflicts at any level of detail.</span></span> <span data-ttu-id="f2415-159">一种极端情况是，您可以用三种方式之一（请参见 <xref:System.Data.Linq.RefreshMode>）来解决所有冲突，而不再作其他方面的考虑。</span><span class="sxs-lookup"><span data-stu-id="f2415-159">At one extreme, you can resolve all conflicts in one of three ways (see <xref:System.Data.Linq.RefreshMode>) without additional consideration.</span></span> <span data-ttu-id="f2415-160">另一种极端情况是，您可以为发生冲突的每个成员上的每种冲突指定特定操作。</span><span class="sxs-lookup"><span data-stu-id="f2415-160">At the other extreme, you can designate a specific action for each type of conflict on every member in conflict.</span></span>  
  
- <span data-ttu-id="f2415-161">在您的对象模型中指定或修改 <xref:System.Data.Linq.Mapping.UpdateCheck> 选项。</span><span class="sxs-lookup"><span data-stu-id="f2415-161">Specify or revise <xref:System.Data.Linq.Mapping.UpdateCheck> options in your object model.</span></span>  
  
     <span data-ttu-id="f2415-162">有关详细信息，请参阅 [如何：指定针对并发冲突对哪些成员进行测试](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)。</span><span class="sxs-lookup"><span data-stu-id="f2415-162">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span></span>  
  
- <span data-ttu-id="f2415-163">在对 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 的调用的 try/catch 块中，指定您希望在哪个点引发异常。</span><span class="sxs-lookup"><span data-stu-id="f2415-163">In the try/catch block of your call to <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, specify at what point you want exceptions to be thrown.</span></span>  
  
     <span data-ttu-id="f2415-164">有关详细信息，请参阅 [如何：指定何时引发并发异常](how-to-specify-when-concurrency-exceptions-are-thrown.md)。</span><span class="sxs-lookup"><span data-stu-id="f2415-164">For more information, see [How to: Specify When Concurrency Exceptions are Thrown](how-to-specify-when-concurrency-exceptions-are-thrown.md).</span></span>  
  
- <span data-ttu-id="f2415-165">决定你希望检索的冲突详细信息量，并在 try/catch 块中包括相应的代码。</span><span class="sxs-lookup"><span data-stu-id="f2415-165">Determine how much conflict detail you want to retrieve, and include code in your try/catch block accordingly.</span></span>  
  
     <span data-ttu-id="f2415-166">有关详细信息，请参阅 [如何：检索实体冲突信息](how-to-retrieve-entity-conflict-information.md) 和 [如何：检索成员冲突信息](how-to-retrieve-member-conflict-information.md)。</span><span class="sxs-lookup"><span data-stu-id="f2415-166">For more information, see [How to: Retrieve Entity Conflict Information](how-to-retrieve-entity-conflict-information.md) and [How to: Retrieve Member Conflict Information](how-to-retrieve-member-conflict-information.md).</span></span>  
  
- <span data-ttu-id="f2415-167">在代码中包含 `try` / `catch` 要如何解决你发现的各种冲突。</span><span class="sxs-lookup"><span data-stu-id="f2415-167">Include in your `try`/`catch` code how you want to resolve the various conflicts you discover.</span></span>  
  
     <span data-ttu-id="f2415-168">有关详细信息，请参阅 [如何：通过保留数据库值解决冲突](how-to-resolve-conflicts-by-retaining-database-values.md)、 [如何：通过覆盖数据库值解决冲突](how-to-resolve-conflicts-by-overwriting-database-values.md)和 [如何：通过与数据库值合并解决冲突](how-to-resolve-conflicts-by-merging-with-database-values.md)。</span><span class="sxs-lookup"><span data-stu-id="f2415-168">For more information, see [How to: Resolve Conflicts by Retaining Database Values](how-to-resolve-conflicts-by-retaining-database-values.md), [How to: Resolve Conflicts by Overwriting Database Values](how-to-resolve-conflicts-by-overwriting-database-values.md), and [How to: Resolve Conflicts by Merging with Database Values](how-to-resolve-conflicts-by-merging-with-database-values.md).</span></span>  
  
## <a name="linq-to-sql-types-that-support-conflict-discovery-and-resolution"></a><span data-ttu-id="f2415-169">支持冲突发现和解决的 LINQ to SQL 类型</span><span class="sxs-lookup"><span data-stu-id="f2415-169">LINQ to SQL Types That Support Conflict Discovery and Resolution</span></span>  

 <span data-ttu-id="f2415-170">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中支持解决开放式并发冲突的类和功能包括：</span><span class="sxs-lookup"><span data-stu-id="f2415-170">Classes and features to support the resolution of conflicts in optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] include the following:</span></span>  
  
- <xref:System.Data.Linq.ObjectChangeConflict?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.MemberChangeConflict?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.ChangeConflictCollection?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.ChangeConflictException?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.ChangeConflicts%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.Refresh%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.Mapping.UpdateCheck?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.RefreshMode?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="f2415-171">请参阅</span><span class="sxs-lookup"><span data-stu-id="f2415-171">See also</span></span>

- [<span data-ttu-id="f2415-172">如何：管理更改冲突</span><span class="sxs-lookup"><span data-stu-id="f2415-172">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
