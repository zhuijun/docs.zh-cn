---
title: 使用 DependentTransaction 管理并发
description: 使用 .NET 中的 DependentTransaction 类管理事务并发，包括异步任务。
ms.date: 03/30/2017
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
ms.openlocfilehash: 1e99006c127d83892155bd81e683f5995ac517ef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186739"
---
# <a name="managing-concurrency-with-dependenttransaction"></a><span data-ttu-id="dc729-103">使用 DependentTransaction 管理并发</span><span class="sxs-lookup"><span data-stu-id="dc729-103">Managing Concurrency with DependentTransaction</span></span>

<span data-ttu-id="dc729-104"><xref:System.Transactions.Transaction> 对象是使用 <xref:System.Transactions.Transaction.DependentClone%2A> 方法创建的。</span><span class="sxs-lookup"><span data-stu-id="dc729-104">The <xref:System.Transactions.Transaction> object is created using the <xref:System.Transactions.Transaction.DependentClone%2A> method.</span></span> <span data-ttu-id="dc729-105">该对象的唯一目的是保证当某他一些代码段（如辅助线程）还在事务上工作时，不能提交事务。</span><span class="sxs-lookup"><span data-stu-id="dc729-105">Its sole purpose is to guarantee that the transaction cannot commit while some other pieces of code (for example, a worker thread) are still performing work on the transaction.</span></span> <span data-ttu-id="dc729-106">当在克隆的事务中执行的工作最终完成并可以提交时，该对象可以使用 <xref:System.Transactions.DependentTransaction.Complete%2A> 方法通知事务的创建者。</span><span class="sxs-lookup"><span data-stu-id="dc729-106">When the work done within the cloned transaction is complete and ready to be committed, it can notify the creator of the transaction using the <xref:System.Transactions.DependentTransaction.Complete%2A> method.</span></span> <span data-ttu-id="dc729-107">因而您就可以保持数据的一致性和正确性。</span><span class="sxs-lookup"><span data-stu-id="dc729-107">Thus, you can preserve the consistency and correctness of data.</span></span>  
  
 <span data-ttu-id="dc729-108">此外，<xref:System.Transactions.DependentTransaction> 类还可用于管理异步任务之间的并发性。</span><span class="sxs-lookup"><span data-stu-id="dc729-108">The <xref:System.Transactions.DependentTransaction> class can also be used to manage concurrency between asynchronous tasks.</span></span> <span data-ttu-id="dc729-109">在这种情况下，当依赖的克隆执行其自己的任务时，父事务可以继续执行任意代码。</span><span class="sxs-lookup"><span data-stu-id="dc729-109">In this scenario, the parent can continue to execute any code while the dependent clone works on its own tasks.</span></span> <span data-ttu-id="dc729-110">换句话说，直到依赖的克隆完成时，父事务的执行才会被阻止。</span><span class="sxs-lookup"><span data-stu-id="dc729-110">In other words, the parent's execution is not blocked until the dependent completes.</span></span>  
  
## <a name="creating-a-dependent-clone"></a><span data-ttu-id="dc729-111">创建依赖的克隆</span><span class="sxs-lookup"><span data-stu-id="dc729-111">Creating a Dependent Clone</span></span>  

 <span data-ttu-id="dc729-112">若要创建依赖的事务，请调用 <xref:System.Transactions.Transaction.DependentClone%2A> 方法并将 <xref:System.Transactions.DependentCloneOption> 枚举作为参数传递。</span><span class="sxs-lookup"><span data-stu-id="dc729-112">To create a dependent transaction, call the <xref:System.Transactions.Transaction.DependentClone%2A> method and pass the <xref:System.Transactions.DependentCloneOption> enumeration as a parameter.</span></span> <span data-ttu-id="dc729-113">此参数定义在依赖的克隆指示可以提交事务（通过调用 `Commit` 方法）之前，对父事务调用 <xref:System.Transactions.DependentTransaction.Complete%2A> 时的事务行为。</span><span class="sxs-lookup"><span data-stu-id="dc729-113">This parameter defines the behavior of the transaction if `Commit` is called on the parent transaction before the dependent clone indicates that it is ready for the transaction to commit (by calling the <xref:System.Transactions.DependentTransaction.Complete%2A> method).</span></span> <span data-ttu-id="dc729-114">下面列出了此参数的有效值：</span><span class="sxs-lookup"><span data-stu-id="dc729-114">The following values are valid for this parameter:</span></span>  
  
- <span data-ttu-id="dc729-115"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> 创建一个依赖事务，该事务将阻止父事务的提交进程，直到父事务超时，或 <xref:System.Transactions.DependentTransaction.Complete%2A> 在所有表示其完成的依赖项上调用。</span><span class="sxs-lookup"><span data-stu-id="dc729-115"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> creates a dependent transaction that blocks the commit process of the parent transaction until the parent transaction times out, or until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on all dependents indicating their completion.</span></span> <span data-ttu-id="dc729-116">当客户端希望在依赖事务完成后再提交父事务时，这一点十分有用。</span><span class="sxs-lookup"><span data-stu-id="dc729-116">This is useful when the client does not want the parent transaction to commit until the dependent transactions have completed.</span></span> <span data-ttu-id="dc729-117">如果父事务的工作比该依赖事务早完成，并在此时对该依赖事务调用了 <xref:System.Transactions.CommittableTransaction.Commit%2A>，则提交进程会被阻止（在该状态下可在依赖事务上执行其他工作并可创建新登记），直到所有依赖事务都调用 <xref:System.Transactions.DependentTransaction.Complete%2A> 为止。</span><span class="sxs-lookup"><span data-stu-id="dc729-117">If the parent finishes its work earlier than the dependent transaction and calls <xref:System.Transactions.CommittableTransaction.Commit%2A> on the transaction, the commit process is blocked in a state where additional work can be done on the transaction and new enlistments can be created, until all of the dependents call <xref:System.Transactions.DependentTransaction.Complete%2A>.</span></span> <span data-ttu-id="dc729-118">只要所有依赖事务完成了工作并调用了 <xref:System.Transactions.DependentTransaction.Complete%2A>，就会立即启动事务的提交进程。</span><span class="sxs-lookup"><span data-stu-id="dc729-118">As soon as all of them have finished their work and call <xref:System.Transactions.DependentTransaction.Complete%2A>, the commit process for the transaction begins.</span></span>  
  
- <span data-ttu-id="dc729-119">另一方面，在调用 <xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete> 之前对父事务调用 <xref:System.Transactions.CommittableTransaction.Commit%2A> 时，<xref:System.Transactions.DependentTransaction.Complete%2A> 会创建一个自动中止的依赖事务。</span><span class="sxs-lookup"><span data-stu-id="dc729-119"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, on the other hand, creates a dependent transaction that automatically aborts if <xref:System.Transactions.CommittableTransaction.Commit%2A> is called on the parent transaction before <xref:System.Transactions.DependentTransaction.Complete%2A> is called.</span></span> <span data-ttu-id="dc729-120">在这种情况下，在该依赖事务中执行的所有工作在一个事务生存期内都保持不变，并且根本无法只提交其中的一部分。</span><span class="sxs-lookup"><span data-stu-id="dc729-120">In this case, all the work done in the dependent transaction is intact within one transaction lifetime, and no one has a chance to commit just a portion of it.</span></span>  
  
 <span data-ttu-id="dc729-121">当应用程序完成在该依赖事务上的工作时，必须调用一次 <xref:System.Transactions.DependentTransaction.Complete%2A> 方法；否则，会引发 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="dc729-121">The <xref:System.Transactions.DependentTransaction.Complete%2A> method must be called only once when your application finishes its work on the dependent transaction; otherwise, a <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="dc729-122">在执行此调用之后，不能在事务上尝试任何附加工作，否则就会引发异常。</span><span class="sxs-lookup"><span data-stu-id="dc729-122">After this call is invoked, you must not attempt any additional work on the transaction, or an exception is thrown.</span></span>  
  
 <span data-ttu-id="dc729-123">下面的代码示例演示如何创建一个依赖事务来管理两个并发任务，具体为克隆一个依赖的事务并将其传递给辅助线程。</span><span class="sxs-lookup"><span data-stu-id="dc729-123">The following code example shows how to create a dependent transaction to manage two concurrent tasks by cloning a dependent transaction and passing it to a worker thread.</span></span>  
  
```csharp  
public class WorkerThread  
{  
    public void DoWork(DependentTransaction dependentTransaction)  
    {  
        Thread thread = new Thread(ThreadMethod);  
        thread.Start(dependentTransaction);
    }  
  
    public void ThreadMethod(object transaction)
    {
        DependentTransaction dependentTransaction = transaction as DependentTransaction;  
        Debug.Assert(dependentTransaction != null);
        try  
        {  
            using(TransactionScope ts = new TransactionScope(dependentTransaction))  
            {  
                /* Perform transactional work here */
                ts.Complete();  
            }  
        }  
        finally  
        {  
            dependentTransaction.Complete();
             dependentTransaction.Dispose();
        }  
    }  
  
//Client code
using(TransactionScope scope = new TransactionScope())  
{  
    Transaction currentTransaction = Transaction.Current;  
    DependentTransaction dependentTransaction;
    dependentTransaction = currentTransaction.DependentClone(DependentCloneOption.BlockCommitUntilComplete);  
    WorkerThread workerThread = new WorkerThread();  
    workerThread.DoWork(dependentTransaction);  
    /* Do some transactional work here, then: */  
    scope.Complete();  
}  
```  
  
 <span data-ttu-id="dc729-124">客户端代码创建了一个还能够设置环境事务的事务范围。</span><span class="sxs-lookup"><span data-stu-id="dc729-124">The client code creates a transactional scope that also sets the ambient transaction.</span></span> <span data-ttu-id="dc729-125">不能直接将环境事务传递给辅助线程。</span><span class="sxs-lookup"><span data-stu-id="dc729-125">You should not pass the ambient transaction to the worker thread.</span></span> <span data-ttu-id="dc729-126">相反，应通过对当前事务调用 <xref:System.Transactions.Transaction.DependentClone%2A> 方法来克隆当前（环境）事务，并将依赖事务传递给辅助线程。</span><span class="sxs-lookup"><span data-stu-id="dc729-126">Instead, you should clone the current (ambient) transaction by calling the <xref:System.Transactions.Transaction.DependentClone%2A> method on the current transaction, and pass the dependent to the worker thread.</span></span>  
  
 <span data-ttu-id="dc729-127">`ThreadMethod` 方法将在新线程上执行。</span><span class="sxs-lookup"><span data-stu-id="dc729-127">The `ThreadMethod` method executes on the new thread.</span></span> <span data-ttu-id="dc729-128">客户端会启动一个新线程，以将该依赖事务作为 `ThreadMethod` 参数传递。</span><span class="sxs-lookup"><span data-stu-id="dc729-128">The client starts a new thread, passing the dependent transaction as the `ThreadMethod` parameter.</span></span>  
  
 <span data-ttu-id="dc729-129">由于依赖事务是用 <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> 创建的，因此应保证第二个线程上的所有事务工作都完成并对该依赖事务调用 <xref:System.Transactions.DependentTransaction.Complete%2A> 后才能提交事务。</span><span class="sxs-lookup"><span data-stu-id="dc729-129">Because the dependent transaction is created with <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, you are guaranteed that the transaction cannot be committed until all of the transactional work done on the second thread is finished and <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent transaction.</span></span> <span data-ttu-id="dc729-130">这意味着，如果客户端的范围 (在该语句尝试释放该语句末尾的 transaction 对象时) ，则在该依赖 `using` 事务上调用之前 <xref:System.Transactions.DependentTransaction.Complete%2A> ，将阻止客户端代码阻止 <xref:System.Transactions.DependentTransaction.Complete%2A> 。</span><span class="sxs-lookup"><span data-stu-id="dc729-130">This means that if the client's scope ends (when it tries to dispose of the transaction object at the end of the `using` statement) before the new thread calls <xref:System.Transactions.DependentTransaction.Complete%2A> on the dependent transaction, the client code blocks until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent.</span></span> <span data-ttu-id="dc729-131">这样，事务就可完成提交或中止。</span><span class="sxs-lookup"><span data-stu-id="dc729-131">Then the transaction can finish committing or aborting.</span></span>  
  
## <a name="concurrency-issues"></a><span data-ttu-id="dc729-132">并发问题</span><span class="sxs-lookup"><span data-stu-id="dc729-132">Concurrency Issues</span></span>  

 <span data-ttu-id="dc729-133">使用 <xref:System.Transactions.DependentTransaction> 类时，存在其他一些需要了解的并发问题。</span><span class="sxs-lookup"><span data-stu-id="dc729-133">There are a few additional concurrency issues that you need to be aware of when using the <xref:System.Transactions.DependentTransaction> class:</span></span>  
  
- <span data-ttu-id="dc729-134">如果辅助线程回滚事务而父事务却尝试提交它，则会引发 <xref:System.Transactions.TransactionAbortedException>。</span><span class="sxs-lookup"><span data-stu-id="dc729-134">If the worker thread rolls back the transaction but the parent tries to commit it, a <xref:System.Transactions.TransactionAbortedException> is thrown.</span></span>  
  
- <span data-ttu-id="dc729-135">您应为事务中的每个辅助线程分别创建一个依赖的克隆。</span><span class="sxs-lookup"><span data-stu-id="dc729-135">You should create a new dependent clone for each worker thread in the transaction.</span></span> <span data-ttu-id="dc729-136">不要将同一依赖克隆传递给多个线程，因为只有一个线程能够对依赖克隆调用 <xref:System.Transactions.DependentTransaction.Complete%2A>。</span><span class="sxs-lookup"><span data-stu-id="dc729-136">Do not pass the same dependent clone to multiple threads, because only one of them can call <xref:System.Transactions.DependentTransaction.Complete%2A> on it.</span></span>  
  
- <span data-ttu-id="dc729-137">如果辅助线程生成新的辅助线程，请确保利用现有的依赖克隆中再创建一个依赖的克隆，然后将后者传递给该新线程。</span><span class="sxs-lookup"><span data-stu-id="dc729-137">If the worker thread spawns a new worker thread, make sure to create a dependent clone from the dependent clone and pass it to the new thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc729-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="dc729-138">See also</span></span>

- <xref:System.Transactions.DependentTransaction>
