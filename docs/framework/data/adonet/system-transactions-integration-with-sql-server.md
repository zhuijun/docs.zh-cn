---
title: System.Transactions 与 SQL Server 的集成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 5adf40f96854e08736cdef77300d69e452de5eea
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191679"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="283c7-102">System.Transactions 与 SQL Server 的集成</span><span class="sxs-lookup"><span data-stu-id="283c7-102">System.Transactions Integration with SQL Server</span></span>

<span data-ttu-id="283c7-103">.NET Framework 版本2.0 引入了一个可通过命名空间访问的事务框架 <xref:System.Transactions> 。</span><span class="sxs-lookup"><span data-stu-id="283c7-103">The .NET Framework version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="283c7-104">此框架以完全集成在 .NET Framework 中的方式公开事务，包括 ADO.NET。</span><span class="sxs-lookup"><span data-stu-id="283c7-104">This framework exposes transactions in a way that is fully integrated in the .NET Framework, including ADO.NET.</span></span>  
  
 <span data-ttu-id="283c7-105">除可编程性增强功能外， <xref:System.Transactions> ADO.NET 还可协同工作，在处理事务时协调优化。</span><span class="sxs-lookup"><span data-stu-id="283c7-105">In addition to the programmability enhancements, <xref:System.Transactions> and ADO.NET can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="283c7-106">可提升事务是可以根据需要自动提升为完全分布式事务的轻型（本地）事务。</span><span class="sxs-lookup"><span data-stu-id="283c7-106">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="283c7-107">从 ADO.NET 2.0 开始， <xref:System.Data.SqlClient> 当你使用 SQL Server 时，支持可提升事务。</span><span class="sxs-lookup"><span data-stu-id="283c7-107">Starting with ADO.NET 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="283c7-108">可提升的事务不会调用分布式事务增加的系统开销，除非需要增加的系统开销。</span><span class="sxs-lookup"><span data-stu-id="283c7-108">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="283c7-109">可提升事务是自动的，无需开发人员介入。</span><span class="sxs-lookup"><span data-stu-id="283c7-109">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="283c7-110">仅当使用 .NET Framework 数据提供程序进行 SQL Server () 使用 SQL Server 时，才可以使用可提升事务 `SqlClient` 。</span><span class="sxs-lookup"><span data-stu-id="283c7-110">Promotable transactions are only available when you use the .NET Framework Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="283c7-111">创建可提升事务</span><span class="sxs-lookup"><span data-stu-id="283c7-111">Creating Promotable Transactions</span></span>  

 <span data-ttu-id="283c7-112">SQL Server 的 .NET Framework 提供程序支持可提升事务，这些事务是通过 .NET Framework 命名空间中的类处理的 <xref:System.Transactions> 。</span><span class="sxs-lookup"><span data-stu-id="283c7-112">The .NET Framework Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the .NET Framework <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="283c7-113">可提升事务通过将分布式事务推迟到需要时再创建，对分布式事务进行优化。</span><span class="sxs-lookup"><span data-stu-id="283c7-113">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="283c7-114">如果只需要一个资源管理器，则不会发生任何分布式事务。</span><span class="sxs-lookup"><span data-stu-id="283c7-114">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="283c7-115">在部分信任方案中，将事务提升为分布式事务时，需要 <xref:System.Transactions.DistributedTransactionPermission> 。</span><span class="sxs-lookup"><span data-stu-id="283c7-115">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="283c7-116">可提升事务方案</span><span class="sxs-lookup"><span data-stu-id="283c7-116">Promotable Transaction Scenarios</span></span>  

 <span data-ttu-id="283c7-117">分布式事务由 Microsoft 分布式事务处理协调器 (MS DTC) 管理，该协调程序集成了事务中访问的所有资源管理器，通常会占用大量的系统资源。</span><span class="sxs-lookup"><span data-stu-id="283c7-117">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="283c7-118">可提升事务是事务的一种特殊形式 <xref:System.Transactions> ，有效地将工作委托给简单的 SQL Server 事务。</span><span class="sxs-lookup"><span data-stu-id="283c7-118">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="283c7-119"><xref:System.Transactions>、 <xref:System.Data.SqlClient> 和 SQL Server 协调处理事务时涉及到的工作，根据需要将其提升为完整的分布式事务。</span><span class="sxs-lookup"><span data-stu-id="283c7-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="283c7-120">使用可提升事务的优点是在使用活动 <xref:System.Transactions.TransactionScope> 事务打开某个连接但不打开任何其他连接时，事务作为轻型事务提交，而不引发完全分布式事务的其他系统开销。</span><span class="sxs-lookup"><span data-stu-id="283c7-120">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="283c7-121">连接字符串关键字</span><span class="sxs-lookup"><span data-stu-id="283c7-121">Connection String Keywords</span></span>  

 <span data-ttu-id="283c7-122"><xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 属性支持关键字 `Enlist`，该关键字指示 <xref:System.Data.SqlClient> 是否将检测事务上下文并自动在分布式事务中登记连接。</span><span class="sxs-lookup"><span data-stu-id="283c7-122">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="283c7-123">如果 `Enlist=true`，连接将自动在打开的线程的当前事务上下文中登记。</span><span class="sxs-lookup"><span data-stu-id="283c7-123">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="283c7-124">如果 `Enlist=false`， `SqlClient` 连接不会与分布式事务进行交互。</span><span class="sxs-lookup"><span data-stu-id="283c7-124">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="283c7-125">`Enlist` 的默认值为 true。</span><span class="sxs-lookup"><span data-stu-id="283c7-125">The default value for `Enlist` is true.</span></span> <span data-ttu-id="283c7-126">如果连接字符串中未指定 `Enlist` ，而在连接打开时检测到一个连接，连接将自动在分布式事务中登记。</span><span class="sxs-lookup"><span data-stu-id="283c7-126">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="283c7-127">`Transaction Binding` 连接字符串中的 <xref:System.Data.SqlClient.SqlConnection> 关键字控制连接与已登记的 `System.Transactions` 事务的关联。</span><span class="sxs-lookup"><span data-stu-id="283c7-127">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="283c7-128">还可以通过 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> 的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder>属性使用。</span><span class="sxs-lookup"><span data-stu-id="283c7-128">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="283c7-129">下表说明可用的值。</span><span class="sxs-lookup"><span data-stu-id="283c7-129">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="283c7-130">关键字</span><span class="sxs-lookup"><span data-stu-id="283c7-130">Keyword</span></span>|<span data-ttu-id="283c7-131">说明</span><span class="sxs-lookup"><span data-stu-id="283c7-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="283c7-132">Implicit Unbind</span><span class="sxs-lookup"><span data-stu-id="283c7-132">Implicit Unbind</span></span>|<span data-ttu-id="283c7-133">默认值。</span><span class="sxs-lookup"><span data-stu-id="283c7-133">The default.</span></span> <span data-ttu-id="283c7-134">事务结束时，连接与事务分离，切换回自动提交模式。</span><span class="sxs-lookup"><span data-stu-id="283c7-134">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="283c7-135">Explicit Unbind</span><span class="sxs-lookup"><span data-stu-id="283c7-135">Explicit Unbind</span></span>|<span data-ttu-id="283c7-136">事务关闭之前，连接保持附加到事务。</span><span class="sxs-lookup"><span data-stu-id="283c7-136">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="283c7-137">如果关联的事务未处于活动状态或不匹配 <xref:System.Transactions.Transaction.Current%2A>，则连接将失败。</span><span class="sxs-lookup"><span data-stu-id="283c7-137">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="283c7-138">使用 TransactionScope</span><span class="sxs-lookup"><span data-stu-id="283c7-138">Using TransactionScope</span></span>  

 <span data-ttu-id="283c7-139"><xref:System.Transactions.TransactionScope> 类通过在分布式事务中隐式登记连接，使代码块成为事务代码。</span><span class="sxs-lookup"><span data-stu-id="283c7-139">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="283c7-140">必须在 <xref:System.Transactions.TransactionScope.Complete%2A> 块的结尾调用 <xref:System.Transactions.TransactionScope> 方法，然后再离开该代码块。</span><span class="sxs-lookup"><span data-stu-id="283c7-140">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="283c7-141">离开代码块将调用 <xref:System.Transactions.TransactionScope.Dispose%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="283c7-141">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="283c7-142">如果引发的异常造成代码离开范围，将认为事务已中止。</span><span class="sxs-lookup"><span data-stu-id="283c7-142">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="283c7-143">我们建议您使用 `using` 块，以确保在退出 using 代码块时，在 <xref:System.Transactions.TransactionScope.Dispose%2A> 对象上调用 <xref:System.Transactions.TransactionScope> 。</span><span class="sxs-lookup"><span data-stu-id="283c7-143">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="283c7-144">如果无法提交或回滚挂起的事务，可能会对性能造成严重影响，因为 <xref:System.Transactions.TransactionScope> 的默认超时为一分钟。</span><span class="sxs-lookup"><span data-stu-id="283c7-144">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="283c7-145">如果未使用 `using` 语句，必须在 `Try` 块中执行所有工作，并在 <xref:System.Transactions.TransactionScope.Dispose%2A> 块中显式调用 `Finally` 方法。</span><span class="sxs-lookup"><span data-stu-id="283c7-145">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="283c7-146">如果在 <xref:System.Transactions.TransactionScope>中发生异常，事务将标记为不一致并被弃用。</span><span class="sxs-lookup"><span data-stu-id="283c7-146">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="283c7-147">在 <xref:System.Transactions.TransactionScope> 断开后，事务将回滚。</span><span class="sxs-lookup"><span data-stu-id="283c7-147">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="283c7-148">如果未发生异常，则提交参与的事务。</span><span class="sxs-lookup"><span data-stu-id="283c7-148">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="283c7-149">默认情况下，`TransactionScope` 类创建 <xref:System.Transactions.Transaction.IsolationLevel%2A> 为 `Serializable` 的事务。</span><span class="sxs-lookup"><span data-stu-id="283c7-149">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="283c7-150">根据您的应用程序，您可能希望考虑降低隔离级别，以避免在应用程序中发生争用激烈的情况。</span><span class="sxs-lookup"><span data-stu-id="283c7-150">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="283c7-151">我们建议您只在分布式事务中执行更新、插入和删除，因为这些操作会占用大量的数据库资源。</span><span class="sxs-lookup"><span data-stu-id="283c7-151">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="283c7-152">选择语句可能会对数据库资源进行不必要的锁定，在某些方案中，可能需要使用事务进行选择。</span><span class="sxs-lookup"><span data-stu-id="283c7-152">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="283c7-153">任何非数据库工作应在事务范围之外完成，除非工作涉及其他事务化的资源管理器。</span><span class="sxs-lookup"><span data-stu-id="283c7-153">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="283c7-154">尽管事务范围内的异常会使事务无法提交，但是， <xref:System.Transactions.TransactionScope> 类没有规定回滚您的代码在事务本身范围之外所作的任何更改。</span><span class="sxs-lookup"><span data-stu-id="283c7-154">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="283c7-155">如果在事务回滚时需要采取某项措施，必须自己编写 <xref:System.Transactions.IEnlistmentNotification> 接口的实现并显式在事务中登记。</span><span class="sxs-lookup"><span data-stu-id="283c7-155">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="283c7-156">示例</span><span class="sxs-lookup"><span data-stu-id="283c7-156">Example</span></span>  

 <span data-ttu-id="283c7-157">使用 <xref:System.Transactions> 要求具有 System.Transactions.dll 的引用。</span><span class="sxs-lookup"><span data-stu-id="283c7-157">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="283c7-158">下面的函数演示如何针对包装在 <xref:System.Data.SqlClient.SqlConnection> 块中的两个不同 SQL Server 实例（由两个不同的 <xref:System.Transactions.TransactionScope> 对象表示）创建可提升事务。</span><span class="sxs-lookup"><span data-stu-id="283c7-158">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="283c7-159">该代码使用 <xref:System.Transactions.TransactionScope> 语句创建 `using` 代码块并打开第一个连接，该连接自动在 <xref:System.Transactions.TransactionScope>中登记。</span><span class="sxs-lookup"><span data-stu-id="283c7-159">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="283c7-160">该事务最初作为轻型事务登记，而不是完全分布式事务。</span><span class="sxs-lookup"><span data-stu-id="283c7-160">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="283c7-161">仅当第一个连接中的命令没有引发异常时，才会在 <xref:System.Transactions.TransactionScope> 中登记第二个连接。</span><span class="sxs-lookup"><span data-stu-id="283c7-161">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="283c7-162">打开第二个连接后，事务将自动提升为完全分布式事务。</span><span class="sxs-lookup"><span data-stu-id="283c7-162">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="283c7-163">将会调用 <xref:System.Transactions.TransactionScope.Complete%2A> 方法，仅当未引发异常时，该方法才会提交事务。</span><span class="sxs-lookup"><span data-stu-id="283c7-163">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="283c7-164">如果在 <xref:System.Transactions.TransactionScope> 代码块中的任意位置引发了异常，将不会调用 `Complete` ，当在 <xref:System.Transactions.TransactionScope> 的 `using` 代码块结尾处执行 dispose 后，将回滚分布式事务。</span><span class="sxs-lookup"><span data-stu-id="283c7-164">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
```csharp  
// This function takes arguments for the 2 connection strings and commands in order  
// to create a transaction involving two SQL Servers. It returns a value > 0 if the  
// transaction committed, 0 if the transaction rolled back. To test this code, you can
// connect to two different databases on the same server by altering the connection string,  
// or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
static public int CreateTransactionScope(  
    string connectString1, string connectString2,  
    string commandText1, string commandText2)  
{  
    // Initialize the return value to zero and create a StringWriter to display results.  
    int returnValue = 0;  
    System.IO.StringWriter writer = new System.IO.StringWriter();  
  
    // Create the TransactionScope in which to execute the commands, guaranteeing  
    // that both commands will commit or roll back as a single unit of work.  
    using (TransactionScope scope = new TransactionScope())  
    {  
        using (SqlConnection connection1 = new SqlConnection(connectString1))  
        {  
            try  
            {  
                // Opening the connection automatically enlists it in the
                // TransactionScope as a lightweight transaction.  
                connection1.Open();  
  
                // Create the SqlCommand object and execute the first command.  
                SqlCommand command1 = new SqlCommand(commandText1, connection1);  
                returnValue = command1.ExecuteNonQuery();  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue);  
  
                // if you get here, this means that command1 succeeded. By nesting  
                // the using block for connection2 inside that of connection1, you  
                // conserve server and network resources by opening connection2
                // only when there is a chance that the transaction can commit.
                using (SqlConnection connection2 = new SqlConnection(connectString2))  
                    try  
                    {  
                        // The transaction is promoted to a full distributed  
                        // transaction when connection2 is opened.  
                        connection2.Open();  
  
                        // Execute the second command in the second database.  
                        returnValue = 0;  
                        SqlCommand command2 = new SqlCommand(commandText2, connection2);  
                        returnValue = command2.ExecuteNonQuery();  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue);  
                    }  
                    catch (Exception ex)  
                    {  
                        // Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue);  
                        writer.WriteLine("Exception Message2: {0}", ex.Message);  
                    }  
            }  
            catch (Exception ex)  
            {  
                // Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue);  
                writer.WriteLine("Exception Message1: {0}", ex.Message);  
            }  
        }  
  
        // If an exception has been thrown, Complete will not
        // be called and the transaction is rolled back.  
        scope.Complete();  
    }  
  
    // The returnValue is greater than 0 if the transaction committed.  
    if (returnValue > 0)  
    {  
        writer.WriteLine("Transaction was committed.");  
    }  
    else  
    {  
        // You could write additional business logic here, notify the caller by  
        // throwing a TransactionAbortedException, or log the failure.  
        writer.WriteLine("Transaction rolled back.");  
    }  
  
    // Display messages.  
    Console.WriteLine(writer.ToString());  
  
    return returnValue;  
}  
```  
  
```vb  
' This function takes arguments for the 2 connection strings and commands in order  
' to create a transaction involving two SQL Servers. It returns a value > 0 if the  
' transaction committed, 0 if the transaction rolled back. To test this code, you can
' connect to two different databases on the same server by altering the connection string,  
' or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
Public Function CreateTransactionScope( _  
  ByVal connectString1 As String, ByVal connectString2 As String, _  
  ByVal commandText1 As String, ByVal commandText2 As String) As Integer  
  
    ' Initialize the return value to zero and create a StringWriter to display results.  
    Dim returnValue As Integer = 0  
    Dim writer As System.IO.StringWriter = New System.IO.StringWriter  
  
    ' Create the TransactionScope in which to execute the commands, guaranteeing  
    ' that both commands will commit or roll back as a single unit of work.  
    Using scope As New TransactionScope()  
        Using connection1 As New SqlConnection(connectString1)  
            Try  
                ' Opening the connection automatically enlists it in the
                ' TransactionScope as a lightweight transaction.  
                connection1.Open()  
  
                ' Create the SqlCommand object and execute the first command.  
                Dim command1 As SqlCommand = New SqlCommand(commandText1, connection1)  
                returnValue = command1.ExecuteNonQuery()  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue)  
  
                ' If you get here, this means that command1 succeeded. By nesting  
                ' the Using block for connection2 inside that of connection1, you  
                ' conserve server and network resources by opening connection2
                ' only when there is a chance that the transaction can commit.
                Using connection2 As New SqlConnection(connectString2)  
                    Try  
                        ' The transaction is promoted to a full distributed  
                        ' transaction when connection2 is opened.  
                        connection2.Open()  
  
                        ' Execute the second command in the second database.  
                        returnValue = 0  
                        Dim command2 As SqlCommand = New SqlCommand(commandText2, connection2)  
                        returnValue = command2.ExecuteNonQuery()  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue)  
  
                    Catch ex As Exception  
                        ' Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue)  
                        writer.WriteLine("Exception Message2: {0}", ex.Message)  
                    End Try  
                End Using  
  
            Catch ex As Exception  
                ' Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue)  
                writer.WriteLine("Exception Message1: {0}", ex.Message)  
            End Try  
        End Using  
  
        ' If an exception has been thrown, Complete will
        ' not be called and the transaction is rolled back.  
        scope.Complete()  
    End Using  
  
    ' The returnValue is greater than 0 if the transaction committed.  
    If returnValue > 0 Then  
        writer.WriteLine("Transaction was committed.")  
    Else  
        ' You could write additional business logic here, notify the caller by  
        ' throwing a TransactionAbortedException, or log the failure.  
       writer.WriteLine("Transaction rolled back.")  
     End If  
  
    ' Display messages.  
    Console.WriteLine(writer.ToString())  
  
    Return returnValue  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="283c7-165">请参阅</span><span class="sxs-lookup"><span data-stu-id="283c7-165">See also</span></span>

- [<span data-ttu-id="283c7-166">事务和并发性</span><span class="sxs-lookup"><span data-stu-id="283c7-166">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="283c7-167">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="283c7-167">ADO.NET Overview</span></span>](ado-net-overview.md)
