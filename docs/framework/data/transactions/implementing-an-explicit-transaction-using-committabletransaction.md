---
title: 使用 CommittableTransaction 执行显式事务
description: 使用 .NET 中的 CommittableTransaction 类实现显式事务。 此类为应用程序提供了使用事务的显式方法。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 29efe5e5-897b-46c2-a35f-e599a273acc8
ms.openlocfilehash: 40001422e665a7dda3fb938c8d57860909525404
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141986"
---
# <a name="implementing-an-explicit-transaction-using-committabletransaction"></a><span data-ttu-id="5d133-104">使用 CommittableTransaction 执行显式事务</span><span class="sxs-lookup"><span data-stu-id="5d133-104">Implementing an Explicit Transaction using CommittableTransaction</span></span>
<span data-ttu-id="5d133-105"><xref:System.Transactions.CommittableTransaction> 类为应用程序使用事务提供了一种显式方法，而不是隐式地使用 <xref:System.Transactions.TransactionScope> 类。</span><span class="sxs-lookup"><span data-stu-id="5d133-105">The <xref:System.Transactions.CommittableTransaction> class provides an explicit way for applications to use a transaction, as opposed to using the <xref:System.Transactions.TransactionScope> class implicitly.</span></span> <span data-ttu-id="5d133-106">对于要跨多个函数调用或多个线程调用使用同一事务的应用程序，前一种类十分有用。</span><span class="sxs-lookup"><span data-stu-id="5d133-106">It is useful for applications that want to use the same transaction across multiple function calls or multiple thread calls.</span></span> <span data-ttu-id="5d133-107">与 <xref:System.Transactions.TransactionScope> 类不同，应用程序编写器需要明确调用 <xref:System.Transactions.CommittableTransaction.Commit%2A> 和 <xref:System.Transactions.Transaction.Rollback%2A> 方法以提交或中止事务。</span><span class="sxs-lookup"><span data-stu-id="5d133-107">Unlike the <xref:System.Transactions.TransactionScope> class, the application writer needs to specifically call the <xref:System.Transactions.CommittableTransaction.Commit%2A> and <xref:System.Transactions.Transaction.Rollback%2A> methods in order to commit or abort the transaction.</span></span>  
  
## <a name="overview-of-the-committabletransaction-class"></a><span data-ttu-id="5d133-108">CommittableTransaction 类概述</span><span class="sxs-lookup"><span data-stu-id="5d133-108">Overview of the CommittableTransaction class</span></span>  
 <span data-ttu-id="5d133-109"><xref:System.Transactions.CommittableTransaction> 类是从 <xref:System.Transactions.Transaction> 类派生的，因此它提供了后者所具有的所有功能。</span><span class="sxs-lookup"><span data-stu-id="5d133-109">The <xref:System.Transactions.CommittableTransaction> class derives from the <xref:System.Transactions.Transaction> class, therefore providing all the functionality of the latter.</span></span> <span data-ttu-id="5d133-110"><xref:System.Transactions.Transaction.Rollback%2A> 类上的 <xref:System.Transactions.Transaction> 方法尤其有用，该方法还可用于回滚 <xref:System.Transactions.CommittableTransaction> 对象。</span><span class="sxs-lookup"><span data-stu-id="5d133-110">Specifically useful is the <xref:System.Transactions.Transaction.Rollback%2A> method on the <xref:System.Transactions.Transaction> class that can also be used to rollback a <xref:System.Transactions.CommittableTransaction> object.</span></span>  
  
 <span data-ttu-id="5d133-111"><xref:System.Transactions.Transaction> 类与 <xref:System.Transactions.CommittableTransaction> 类似，但前者不提供 `Commit` 方法。</span><span class="sxs-lookup"><span data-stu-id="5d133-111">The  <xref:System.Transactions.Transaction> class is similar to the <xref:System.Transactions.CommittableTransaction> class but does not offer a `Commit` method.</span></span> <span data-ttu-id="5d133-112">这使您可以将事务对象（或其克隆）传递给其他方法（可能位于其他线程上），同时仍可控制事务的提交时间。</span><span class="sxs-lookup"><span data-stu-id="5d133-112">This enables you to pass the transaction object (or clones of it) to other methods (potentially on other threads) while still controlling when the transaction is committed.</span></span> <span data-ttu-id="5d133-113">被调用的代码可以在事务中登记并为其投票，但只有 <xref:System.Transactions.CommittableTransaction> 对象的创建者才能提交事务。</span><span class="sxs-lookup"><span data-stu-id="5d133-113">The called code is able to enlist and vote on the transaction, but only the creator of the <xref:System.Transactions.CommittableTransaction> object has the ability to commit the transaction.</span></span>  
  
 <span data-ttu-id="5d133-114">此外，在使用 <xref:System.Transactions.CommittableTransaction> 类时，还应注意以下几点。</span><span class="sxs-lookup"><span data-stu-id="5d133-114">You should note the followings when working with the <xref:System.Transactions.CommittableTransaction> class,</span></span>  
  
- <span data-ttu-id="5d133-115">创建 <xref:System.Transactions.CommittableTransaction> 事务并不会设置环境事务。</span><span class="sxs-lookup"><span data-stu-id="5d133-115">Creating a <xref:System.Transactions.CommittableTransaction> transaction does not set the ambient transaction.</span></span> <span data-ttu-id="5d133-116">您需要明确设置和重置环境事务，才能确保资源管理器在需要时在正确的事务上下文中操作。</span><span class="sxs-lookup"><span data-stu-id="5d133-116">You need to specifically set and reset the ambient transaction, to ensure that resource managers operate under the right transaction context when appropriate.</span></span> <span data-ttu-id="5d133-117">设置当前环境事务的方式是在全局 <xref:System.Transactions.Transaction.Current%2A> 对象上设置静态 <xref:System.Transactions.Transaction> 属性。</span><span class="sxs-lookup"><span data-stu-id="5d133-117">The way to set the current ambient transaction is by setting the static <xref:System.Transactions.Transaction.Current%2A> property on the global <xref:System.Transactions.Transaction> object.</span></span>  
  
- <span data-ttu-id="5d133-118"><xref:System.Transactions.CommittableTransaction> 对象不能被重用。</span><span class="sxs-lookup"><span data-stu-id="5d133-118">A <xref:System.Transactions.CommittableTransaction> object cannot be reused.</span></span> <span data-ttu-id="5d133-119"><xref:System.Transactions.CommittableTransaction> 对象一旦提交或回滚后，就不能再在事务中使用。</span><span class="sxs-lookup"><span data-stu-id="5d133-119">Once a <xref:System.Transactions.CommittableTransaction> object has been committed or rolled back, it cannot be used again in a transaction.</span></span> <span data-ttu-id="5d133-120">也就是说，它不能设置为当前环境事务上下文。</span><span class="sxs-lookup"><span data-stu-id="5d133-120">That is, it cannot be set as the current ambient transaction context.</span></span>  
  
## <a name="creating-a-committabletransaction"></a><span data-ttu-id="5d133-121">创建可提交的事务</span><span class="sxs-lookup"><span data-stu-id="5d133-121">Creating a CommittableTransaction</span></span>  
 <span data-ttu-id="5d133-122">下面的示例创建一个新的 <xref:System.Transactions.CommittableTransaction> 并提交它。</span><span class="sxs-lookup"><span data-stu-id="5d133-122">The following sample creates a new <xref:System.Transactions.CommittableTransaction> and commits it.</span></span>  
  
 [!code-csharp[Tx_CommittableTx#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_committabletx/cs/committabletxwithsql.cs#1)]
 [!code-vb[Tx_CommittableTx#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_committabletx/vb/committabletxwithsql.vb#1)]  
  
 <span data-ttu-id="5d133-123">创建 <xref:System.Transactions.CommittableTransaction> 的实例并不会自动设置环境事务上下文。</span><span class="sxs-lookup"><span data-stu-id="5d133-123">Creating an instance of <xref:System.Transactions.CommittableTransaction> does not automatically set the ambient transaction context.</span></span> <span data-ttu-id="5d133-124">因此，资源管理器上的任何操作都不属于该事务。</span><span class="sxs-lookup"><span data-stu-id="5d133-124">Therefore, any operation on a resource manager is not part of that transaction.</span></span> <span data-ttu-id="5d133-125">全局 <xref:System.Transactions.Transaction.Current%2A> 对象上的静态 <xref:System.Transactions.Transaction> 属性用于设置或检索环境事务，应用程序必须手动设置该属性，才能确保资源管理器可参与事务。</span><span class="sxs-lookup"><span data-stu-id="5d133-125">The static <xref:System.Transactions.Transaction.Current%2A> property on the global <xref:System.Transactions.Transaction> object is used to set or retrieve the ambient transaction and the application must manually set it to ensure that resource managers can participate in the transaction.</span></span> <span data-ttu-id="5d133-126">此外，还有一个很好的做法，就是保存旧环境事务并在完成时使用 <xref:System.Transactions.CommittableTransaction> 对象还原它。</span><span class="sxs-lookup"><span data-stu-id="5d133-126">It is also a good practice to save the old ambient transaction and restore it when you finish using the <xref:System.Transactions.CommittableTransaction> object.</span></span>  
  
 <span data-ttu-id="5d133-127">若要提交事务，需要显式调用 <xref:System.Transactions.CommittableTransaction.Commit%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="5d133-127">To commit the transaction, you need to explicitly call the <xref:System.Transactions.CommittableTransaction.Commit%2A> method.</span></span> <span data-ttu-id="5d133-128">若要回滚事务，应调用 <xref:System.Transactions.Transaction.Rollback%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="5d133-128">For rolling back a transaction, you should call the <xref:System.Transactions.Transaction.Rollback%2A> method.</span></span> <span data-ttu-id="5d133-129">请注意，还有一点很重要，就是在提交或回滚 <xref:System.Transactions.CommittableTransaction> 之前，该事务中所涉及的所有资源仍处于锁定状态。</span><span class="sxs-lookup"><span data-stu-id="5d133-129">It is important to note that until a <xref:System.Transactions.CommittableTransaction> has been committed or rolled back, all the resources involved in that transaction are still locked.</span></span>  
  
 <span data-ttu-id="5d133-130">可跨函数调用和线程使用 <xref:System.Transactions.CommittableTransaction> 对象。</span><span class="sxs-lookup"><span data-stu-id="5d133-130">A <xref:System.Transactions.CommittableTransaction> object can be used across function calls and threads.</span></span> <span data-ttu-id="5d133-131">但是，在发生故障时，应由应用程序开发人员负责处理异常并明确调用 <xref:System.Transactions.Transaction.Rollback%28System.Exception%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="5d133-131">However, it is up to the application developer to handle exceptions and specifically call the <xref:System.Transactions.Transaction.Rollback%28System.Exception%29> method in case of failures.</span></span>  
  
## <a name="asynchronous-commit"></a><span data-ttu-id="5d133-132">异步提交</span><span class="sxs-lookup"><span data-stu-id="5d133-132">Asynchronous Commit</span></span>  
 <span data-ttu-id="5d133-133"><xref:System.Transactions.CommittableTransaction> 类还提供了一种以异步方式提交事务的机制。</span><span class="sxs-lookup"><span data-stu-id="5d133-133">The <xref:System.Transactions.CommittableTransaction> class also provides a mechanism for committing a transaction asynchronously.</span></span> <span data-ttu-id="5d133-134">事务提交可能会耗费大量时间，因为它可能涉及多个数据库访问和可能的网络延迟。</span><span class="sxs-lookup"><span data-stu-id="5d133-134">A transaction commit can take substantial time, as it might involve multiple database access and possible network latency.</span></span> <span data-ttu-id="5d133-135">如果要在高吞吐量应用程序中避免死锁，可以使用异步提交尽快地完成事务工作，并将提交操作作为后台任务运行。</span><span class="sxs-lookup"><span data-stu-id="5d133-135">When you want to avoid deadlocks in high throughput applications, you can use asynchronous commit to finish the transactional work as soon as possible, and run the commit operation as a background task.</span></span> <span data-ttu-id="5d133-136">此操作可以通过 <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> 类的 <xref:System.Transactions.CommittableTransaction.EndCommit%2A> 和 <xref:System.Transactions.CommittableTransaction> 方法执行。</span><span class="sxs-lookup"><span data-stu-id="5d133-136">The <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> and <xref:System.Transactions.CommittableTransaction.EndCommit%2A> methods of the <xref:System.Transactions.CommittableTransaction> class allow you to do so.</span></span>  
  
 <span data-ttu-id="5d133-137">调用 <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> 可将提交延迟调度到线程池中的某一线程。</span><span class="sxs-lookup"><span data-stu-id="5d133-137">You can call <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> to dispatch the commit holdup to a thread from the thread pool.</span></span> <span data-ttu-id="5d133-138">此外，还可以调用 <xref:System.Transactions.CommittableTransaction.EndCommit%2A> 来确定是否确实已提交事务。</span><span class="sxs-lookup"><span data-stu-id="5d133-138">You can also call <xref:System.Transactions.CommittableTransaction.EndCommit%2A> to determine if the transaction has actually been committed.</span></span> <span data-ttu-id="5d133-139">如果无法提交事务（无论出于什么原因），<xref:System.Transactions.CommittableTransaction.EndCommit%2A> 就会引发事务异常。</span><span class="sxs-lookup"><span data-stu-id="5d133-139">If the transaction failed to commit for whatever reason, <xref:System.Transactions.CommittableTransaction.EndCommit%2A> raises a transaction exception.</span></span> <span data-ttu-id="5d133-140">如果在调用 <xref:System.Transactions.CommittableTransaction.EndCommit%2A> 时仍未提交事务，则调用方就会处于锁定状态，直到提交或中止事务为止。</span><span class="sxs-lookup"><span data-stu-id="5d133-140">If the transaction is not yet committed by the time <xref:System.Transactions.CommittableTransaction.EndCommit%2A> is called, the caller is blocked until the transaction is committed or aborted.</span></span>  
  
 <span data-ttu-id="5d133-141">执行异步提交的最简单方法就是提供要在完成提交时调用的回调方法。</span><span class="sxs-lookup"><span data-stu-id="5d133-141">The easiest way to do an asynchronous commit is by providing a callback method, to be called when committing is finished.</span></span> <span data-ttu-id="5d133-142">但是，必须在用于执行该调用的原始 <xref:System.Transactions.CommittableTransaction.EndCommit%2A> 对象上调用 <xref:System.Transactions.CommittableTransaction> 方法。</span><span class="sxs-lookup"><span data-stu-id="5d133-142">However, you must call the <xref:System.Transactions.CommittableTransaction.EndCommit%2A> method on the original <xref:System.Transactions.CommittableTransaction> object used to invoke the call.</span></span> <span data-ttu-id="5d133-143">若要获取该对象，可以向下转换回调方法的*IAsyncResult*参数，因为 <xref:System.Transactions.CommittableTransaction> 类实现 <xref:System.IAsyncResult> 类。</span><span class="sxs-lookup"><span data-stu-id="5d133-143">To obtain that object, you can downcast the *IAsyncResult* parameter of the callback method, since the <xref:System.Transactions.CommittableTransaction> class implements <xref:System.IAsyncResult> class.</span></span>  
  
 <span data-ttu-id="5d133-144">下面的示例演示如何执行异步提交。</span><span class="sxs-lookup"><span data-stu-id="5d133-144">The following example shows how an asynchronous commit can be done.</span></span>  
  
```csharp  
public void DoTransactionalWork()  
{  
     Transaction oldAmbient = Transaction.Current;  
     CommittableTransaction committableTransaction = new CommittableTransaction();  
     Transaction.Current = committableTransaction;  
  
     try  
     {  
          /* Perform transactional work here */  
          // No errors - commit transaction asynchronously  
          committableTransaction.BeginCommit(OnCommitted,null);  
     }  
     finally  
     {  
          //Restore the ambient transaction
          Transaction.Current = oldAmbient;  
     }  
}  
void OnCommitted(IAsyncResult asyncResult)  
{  
     CommittableTransaction committableTransaction;  
     committableTransaction = asyncResult as CommittableTransaction;
     Debug.Assert(committableTransaction != null);  
     try  
     {  
          using(committableTransaction)  
          {  
               committableTransaction.EndCommit(asyncResult);  
          }  
     }  
     catch(TransactionException e)  
     {  
          //Handle the failure to commit  
     }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d133-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5d133-145">See also</span></span>

- [<span data-ttu-id="5d133-146">使用事务范围实现隐式事务</span><span class="sxs-lookup"><span data-stu-id="5d133-146">Implementing an Implicit Transaction using Transaction Scope</span></span>](implementing-an-implicit-transaction-using-transaction-scope.md)
- [<span data-ttu-id="5d133-147">事务处理</span><span class="sxs-lookup"><span data-stu-id="5d133-147">Transaction Processing</span></span>](index.md)
