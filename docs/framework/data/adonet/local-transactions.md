---
title: 本地事务
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ae3712f-ef5e-41a1-9ea9-b3d0399439f1
ms.openlocfilehash: a0b713ab0b81cb2f0661212dae22db34b7f9f3ae
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175390"
---
# <a name="local-transactions"></a><span data-ttu-id="e97c1-102">本地事务</span><span class="sxs-lookup"><span data-stu-id="e97c1-102">Local Transactions</span></span>

<span data-ttu-id="e97c1-103">如果要将多个任务绑定在一起，以便将它们作为单个工作单元执行，则可以使用 ADO.NET 中的事务。</span><span class="sxs-lookup"><span data-stu-id="e97c1-103">Transactions in ADO.NET are used when you want to bind multiple tasks together so that they execute as a single unit of work.</span></span> <span data-ttu-id="e97c1-104">例如，假设应用程序执行两个任务。</span><span class="sxs-lookup"><span data-stu-id="e97c1-104">For example, imagine that an application performs two tasks.</span></span> <span data-ttu-id="e97c1-105">首先使用订单信息更新表。</span><span class="sxs-lookup"><span data-stu-id="e97c1-105">First, it updates a table with order information.</span></span> <span data-ttu-id="e97c1-106">然后更新包含库存信息的表，将已订购的商品记入借方。</span><span class="sxs-lookup"><span data-stu-id="e97c1-106">Second, it updates a table that contains inventory information, debiting the items ordered.</span></span> <span data-ttu-id="e97c1-107">如果有一个任务失败，则回滚两个更新。</span><span class="sxs-lookup"><span data-stu-id="e97c1-107">If either task fails, then both updates are rolled back.</span></span>  
  
## <a name="determining-the-transaction-type"></a><span data-ttu-id="e97c1-108">确定事务类型</span><span class="sxs-lookup"><span data-stu-id="e97c1-108">Determining the Transaction Type</span></span>  

 <span data-ttu-id="e97c1-109">如果事务是单阶段事务，则该事务被视为本地事务，并且由数据库直接处理。</span><span class="sxs-lookup"><span data-stu-id="e97c1-109">A transaction is considered to be a local transaction when it is a single-phase transaction and is handled by the database directly.</span></span> <span data-ttu-id="e97c1-110">当事务由事务监视器协调并使用防故障机制 (例如两阶段提交) 进行事务解析时，该事务被视为分布式事务。</span><span class="sxs-lookup"><span data-stu-id="e97c1-110">A transaction is considered to be a distributed transaction when it is coordinated by a transaction monitor and uses fail-safe mechanisms (such as two-phase commit) for transaction resolution.</span></span>  
  
 <span data-ttu-id="e97c1-111">每个 .NET Framework 数据提供程序都有自己 `Transaction` 的用于执行本地事务的对象。</span><span class="sxs-lookup"><span data-stu-id="e97c1-111">Each of the .NET Framework data providers has its own `Transaction` object for performing local transactions.</span></span> <span data-ttu-id="e97c1-112">如果要求事务在 SQL Server 数据库中执行，则选择 <xref:System.Data.SqlClient> 事务。</span><span class="sxs-lookup"><span data-stu-id="e97c1-112">If you require a transaction to be performed in a SQL Server database, select a <xref:System.Data.SqlClient> transaction.</span></span> <span data-ttu-id="e97c1-113">对于 Oracle 事务，使用 <xref:System.Data.OracleClient> 提供程序。</span><span class="sxs-lookup"><span data-stu-id="e97c1-113">For an Oracle transaction, use the <xref:System.Data.OracleClient> provider.</span></span> <span data-ttu-id="e97c1-114">此外，还提供了一个 <xref:System.Data.Common.DbTransaction> 类，该类可用于编写与提供程序无关的代码，该代码需要事务。</span><span class="sxs-lookup"><span data-stu-id="e97c1-114">In addition, there is a <xref:System.Data.Common.DbTransaction> class that is available for writing provider-independent code that requires transactions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e97c1-115">当事务在服务器上执行时，它们是最有效的。</span><span class="sxs-lookup"><span data-stu-id="e97c1-115">Transactions are most efficient when they are performed on the server.</span></span> <span data-ttu-id="e97c1-116">如果使用的 SQL Server 数据库广泛使用显式事务，应考虑使用 Transact-SQL BEGIN TRANSACTION 语句以存储过程的形式编写这些事务。</span><span class="sxs-lookup"><span data-stu-id="e97c1-116">If you are working with a SQL Server database that makes extensive use of explicit transactions, consider writing them as stored procedures using the Transact-SQL BEGIN TRANSACTION statement.</span></span>
  
## <a name="performing-a-transaction-using-a-single-connection"></a><span data-ttu-id="e97c1-117">使用单个连接执行事务</span><span class="sxs-lookup"><span data-stu-id="e97c1-117">Performing a Transaction Using a Single Connection</span></span>  

 <span data-ttu-id="e97c1-118">在 ADO.NET 中，可以通过对象控制事务 `Connection` 。</span><span class="sxs-lookup"><span data-stu-id="e97c1-118">In ADO.NET, you control transactions with the `Connection` object.</span></span> <span data-ttu-id="e97c1-119">可以使用 `BeginTransaction` 方法启动本地事务。</span><span class="sxs-lookup"><span data-stu-id="e97c1-119">You can initiate a local transaction with the `BeginTransaction` method.</span></span> <span data-ttu-id="e97c1-120">开始事务后，可以使用 `Transaction` 对象的 `Command` 属性在该事务中登记一个命令。</span><span class="sxs-lookup"><span data-stu-id="e97c1-120">Once you have begun a transaction, you can enlist a command in that transaction with the `Transaction` property of a `Command` object.</span></span> <span data-ttu-id="e97c1-121">然后，可以根据事务组件的成功或失败，提交或回滚在数据源上进行的修改。</span><span class="sxs-lookup"><span data-stu-id="e97c1-121">You can then commit or roll back modifications made at the data source based on the success or failure of the components of the transaction.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e97c1-122">不应对本地事务使用 `EnlistDistributedTransaction` 方法。</span><span class="sxs-lookup"><span data-stu-id="e97c1-122">The `EnlistDistributedTransaction` method should not be used for a local transaction.</span></span>  
  
 <span data-ttu-id="e97c1-123">事务的作用域限于该连接。</span><span class="sxs-lookup"><span data-stu-id="e97c1-123">The scope of the transaction is limited to the connection.</span></span> <span data-ttu-id="e97c1-124">以下示例执行显式事务，该事务由 `try` 块中两个独立的命令组成。</span><span class="sxs-lookup"><span data-stu-id="e97c1-124">The following example performs an explicit transaction that consists of two separate commands in the `try` block.</span></span> <span data-ttu-id="e97c1-125">命令对 AdventureWorks SQL Server 示例数据库中的 ScrapReason 表执行 INSERT 语句，如果没有引发异常，则提交该数据库。</span><span class="sxs-lookup"><span data-stu-id="e97c1-125">The commands execute INSERT statements against the Production.ScrapReason table in the AdventureWorks SQL Server sample database, which are committed if no exceptions are thrown.</span></span> <span data-ttu-id="e97c1-126">如果引发异常，`catch` 块中的代码将回滚此事务。</span><span class="sxs-lookup"><span data-stu-id="e97c1-126">The code in the `catch` block rolls back the transaction if an exception is thrown.</span></span> <span data-ttu-id="e97c1-127">如果在事务完成之前事务中止或连接关闭，事务将自动回滚。</span><span class="sxs-lookup"><span data-stu-id="e97c1-127">If the transaction is aborted or the connection is closed before the transaction has completed, it is automatically rolled back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e97c1-128">示例</span><span class="sxs-lookup"><span data-stu-id="e97c1-128">Example</span></span>  

 <span data-ttu-id="e97c1-129">按照下列步骤执行事务。</span><span class="sxs-lookup"><span data-stu-id="e97c1-129">Follow these steps to perform a transaction.</span></span>  
  
1. <span data-ttu-id="e97c1-130">调用 <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> 对象的 <xref:System.Data.SqlClient.SqlConnection> 方法，以标记事务的开始。</span><span class="sxs-lookup"><span data-stu-id="e97c1-130">Call the <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to mark the start of the transaction.</span></span> <span data-ttu-id="e97c1-131"><xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> 方法返回对事务的引用。</span><span class="sxs-lookup"><span data-stu-id="e97c1-131">The <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> method returns a reference to the transaction.</span></span> <span data-ttu-id="e97c1-132">此引用分配给在事务中登记的 <xref:System.Data.SqlClient.SqlCommand> 对象。</span><span class="sxs-lookup"><span data-stu-id="e97c1-132">This reference is assigned to the <xref:System.Data.SqlClient.SqlCommand> objects that are enlisted in the transaction.</span></span>  
  
2. <span data-ttu-id="e97c1-133">将 `Transaction` 对象分配给要执行的 <xref:System.Data.SqlClient.SqlCommand.Transaction%2A> 的 <xref:System.Data.SqlClient.SqlCommand> 属性。</span><span class="sxs-lookup"><span data-stu-id="e97c1-133">Assign the `Transaction` object to the <xref:System.Data.SqlClient.SqlCommand.Transaction%2A> property of the <xref:System.Data.SqlClient.SqlCommand> to be executed.</span></span> <span data-ttu-id="e97c1-134">如果在具有活动事务的连接上执行命令，并且尚未将 `Transaction` 对象配给 `Transaction` 对象的 `Command` 属性，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="e97c1-134">If a command is executed on a connection with an active transaction, and the `Transaction` object has not been assigned to the `Transaction` property of the `Command` object, an exception is thrown.</span></span>  
  
3. <span data-ttu-id="e97c1-135">执行所需的命令。</span><span class="sxs-lookup"><span data-stu-id="e97c1-135">Execute the required commands.</span></span>  
  
4. <span data-ttu-id="e97c1-136">调用 <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> 对象的 <xref:System.Data.SqlClient.SqlTransaction> 方法完成事务，或调用 <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> 方法结束事务。</span><span class="sxs-lookup"><span data-stu-id="e97c1-136">Call the <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> method of the <xref:System.Data.SqlClient.SqlTransaction> object to complete the transaction, or call the <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> method to end the transaction.</span></span> <span data-ttu-id="e97c1-137">如果在 <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> 或 <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> 方法执行之前连接关闭或断开，事务将回滚。</span><span class="sxs-lookup"><span data-stu-id="e97c1-137">If the connection is closed or disposed before either the <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> or <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> methods have been executed, the transaction is rolled back.</span></span>  
  
 <span data-ttu-id="e97c1-138">下面的代码示例演示了使用 ADO.NET 与 Microsoft SQL Server 的事务逻辑。</span><span class="sxs-lookup"><span data-stu-id="e97c1-138">The following code example demonstrates transactional logic using ADO.NET with Microsoft SQL Server.</span></span>  
  
 [!code-csharp[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e97c1-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="e97c1-139">See also</span></span>

- [<span data-ttu-id="e97c1-140">事务和并发性</span><span class="sxs-lookup"><span data-stu-id="e97c1-140">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="e97c1-141">分布式事务</span><span class="sxs-lookup"><span data-stu-id="e97c1-141">Distributed Transactions</span></span>](distributed-transactions.md)
- [<span data-ttu-id="e97c1-142">System.Transactions 与 SQL Server 的集成</span><span class="sxs-lookup"><span data-stu-id="e97c1-142">System.Transactions Integration with SQL Server</span></span>](system-transactions-integration-with-sql-server.md)
- [<span data-ttu-id="e97c1-143">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="e97c1-143">ADO.NET Overview</span></span>](ado-net-overview.md)
