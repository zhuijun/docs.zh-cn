---
title: 编写事务应用程序
description: 编写 .NET 中的事务处理应用程序。 分别将显式或隐式编程模型与 Transaction 类或 TransactionScope 类一起使用。
ms.date: 03/30/2017
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
ms.openlocfilehash: 0235bb507d974e0bd3a7046ea213d8b78d870d59
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415766"
---
# <a name="writing-a-transactional-application"></a><span data-ttu-id="4cb6d-104">编写事务应用程序</span><span class="sxs-lookup"><span data-stu-id="4cb6d-104">Writing a Transactional Application</span></span>
<span data-ttu-id="4cb6d-105">作为事务应用程序程序员，您可以利用 <xref:System.Transactions> 命名空间所提供的两种编程模型来创建事务。</span><span class="sxs-lookup"><span data-stu-id="4cb6d-105">As a transactional application programmer, you can take advantage of the two programming models provided by the <xref:System.Transactions> namespace to create a transaction.</span></span> <span data-ttu-id="4cb6d-106">通过使用类，可以使用显式编程模型 <xref:System.Transactions.Transaction> ，或者通过使用类，通过基础结构自动管理事务 <xref:System.Transactions.TransactionScope> 。</span><span class="sxs-lookup"><span data-stu-id="4cb6d-106">You can utilize the explicit programming model by using the <xref:System.Transactions.Transaction> class, or the implicit programming model in which transactions are automatically managed by the infrastructure, by using the <xref:System.Transactions.TransactionScope> class.</span></span> <span data-ttu-id="4cb6d-107">建议使用隐式事务模型进行开发。</span><span class="sxs-lookup"><span data-stu-id="4cb6d-107">We recommend that you use the implicit transaction model for development.</span></span> <span data-ttu-id="4cb6d-108">可以在[使用事务范围实现隐式事务](implementing-an-implicit-transaction-using-transaction-scope.md)主题中找到有关如何使用事务范围的详细信息。</span><span class="sxs-lookup"><span data-stu-id="4cb6d-108">You can find more information on how to use a transaction scope in the [Implementing an Implicit Transaction using Transaction Scope](implementing-an-implicit-transaction-using-transaction-scope.md) topic.</span></span>  
  
 <span data-ttu-id="4cb6d-109">这两种模型都支持在程序达到一致状态时提交事务。</span><span class="sxs-lookup"><span data-stu-id="4cb6d-109">Both models support committing a transaction when the program reaches a consistent state.</span></span> <span data-ttu-id="4cb6d-110">如果提交成功，就会永久提交事务。</span><span class="sxs-lookup"><span data-stu-id="4cb6d-110">If the commit succeeds, the transaction is durably committed.</span></span> <span data-ttu-id="4cb6d-111">如果提交失败，事务就会中止。</span><span class="sxs-lookup"><span data-stu-id="4cb6d-111">If the commit fails, the transaction aborts.</span></span> <span data-ttu-id="4cb6d-112">如果应用程序无法成功完成事务，则会尝试中止并撤消事务的效果。</span><span class="sxs-lookup"><span data-stu-id="4cb6d-112">If the application program cannot successfully complete the transaction, it attempts to abort and undo the transaction's effects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4cb6d-113">本节内容</span><span class="sxs-lookup"><span data-stu-id="4cb6d-113">In This Section</span></span>  
  
### <a name="creating-a-transaction"></a><span data-ttu-id="4cb6d-114">创建事务</span><span class="sxs-lookup"><span data-stu-id="4cb6d-114">Creating a Transaction</span></span>  
 <span data-ttu-id="4cb6d-115"><xref:System.Transactions> 命名空间提供了两种用于创建事务的模型。</span><span class="sxs-lookup"><span data-stu-id="4cb6d-115">The <xref:System.Transactions> namespace provides two models for creating a transaction.</span></span> <span data-ttu-id="4cb6d-116">下列主题对这两种模型进行了介绍。</span><span class="sxs-lookup"><span data-stu-id="4cb6d-116">These models are covered in the following topics.</span></span>  
  
 [<span data-ttu-id="4cb6d-117">使用事务范围实现隐式事务</span><span class="sxs-lookup"><span data-stu-id="4cb6d-117">Implementing an Implicit Transaction using Transaction Scope</span></span>](implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 <span data-ttu-id="4cb6d-118">描述 <xref:System.Transactions> 命名空间如何支持使用 <xref:System.Transactions.TransactionScope> 类创建隐式事务。</span><span class="sxs-lookup"><span data-stu-id="4cb6d-118">Describes how the <xref:System.Transactions> namespace supports creating implicit transactions using the <xref:System.Transactions.TransactionScope> class.</span></span>  
  
 [<span data-ttu-id="4cb6d-119">使用 CommittableTransaction 执行显式事务</span><span class="sxs-lookup"><span data-stu-id="4cb6d-119">Implementing an Explicit Transaction using CommittableTransaction</span></span>](implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 <span data-ttu-id="4cb6d-120">描述 <xref:System.Transactions> 命名空间如何支持使用 <xref:System.Transactions.CommittableTransaction> 类创建显式事务。</span><span class="sxs-lookup"><span data-stu-id="4cb6d-120">Describes how the <xref:System.Transactions> namespace supports creating explicit transactions using the <xref:System.Transactions.CommittableTransaction> class.</span></span>  
  
### <a name="escalating-transaction-management"></a><span data-ttu-id="4cb6d-121">升级事务管理</span><span class="sxs-lookup"><span data-stu-id="4cb6d-121">Escalating Transaction Management</span></span>  
 <span data-ttu-id="4cb6d-122">当事务需要访问其他应用程序域中的资源时，或者要登记到其他持久资源管理器时，事务会自动升级为由 MSDTC 管理。</span><span class="sxs-lookup"><span data-stu-id="4cb6d-122">When a transaction needs to access a resource in another application domain, or if you want to enlist in another durable resource manager, the transaction is automatically escalated to be managed by the MSDTC.</span></span> <span data-ttu-id="4cb6d-123">事务升级在[事务管理升级](transaction-management-escalation.md)主题中介绍。</span><span class="sxs-lookup"><span data-stu-id="4cb6d-123">Transaction escalation is covered in the [Transaction Management Escalation](transaction-management-escalation.md) topic.</span></span>  
  
### <a name="concurrency"></a><span data-ttu-id="4cb6d-124">并发</span><span class="sxs-lookup"><span data-stu-id="4cb6d-124">Concurrency</span></span>  
 <span data-ttu-id="4cb6d-125">使用[DependentTransaction 管理并发](managing-concurrency-with-dependenttransaction.md)的主题演示了如何使用类在异步任务之间实现并发 <xref:System.Transactions.DependentTransaction> 。</span><span class="sxs-lookup"><span data-stu-id="4cb6d-125">The topic [Managing Concurrency with DependentTransaction](managing-concurrency-with-dependenttransaction.md) demonstrates how concurrency can be achieved between asynchronous tasks by using the <xref:System.Transactions.DependentTransaction> class.</span></span>  
  
### <a name="com-interop"></a><span data-ttu-id="4cb6d-126">COM+ 互操作</span><span class="sxs-lookup"><span data-stu-id="4cb6d-126">COM+ Interop</span></span>  
 <span data-ttu-id="4cb6d-127">主题[与企业服务和 COM + 事务的互操作性](interoperability-with-enterprise-services-and-com-transactions.md)说明了如何使分布式事务与 com + 事务交互。</span><span class="sxs-lookup"><span data-stu-id="4cb6d-127">The topic [Interoperability with Enterprise Services and COM+ Transactions](interoperability-with-enterprise-services-and-com-transactions.md) illustrates how you can make your distributed transactions interact with COM+ transactions.</span></span>  
  
### <a name="diagnostics"></a><span data-ttu-id="4cb6d-128">诊断</span><span class="sxs-lookup"><span data-stu-id="4cb6d-128">Diagnostics</span></span>  
 <span data-ttu-id="4cb6d-129">[诊断跟踪](diagnostic-traces.md)介绍了如何使用基础结构所生成的跟踪代码 <xref:System.Transactions> 对应用程序中的错误进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="4cb6d-129">[Diagnostic Traces](diagnostic-traces.md) describes how you can use the trace codes that are generated by the <xref:System.Transactions> infrastructure to troubleshoot errors in your applications.</span></span>  
  
### <a name="working-within-aspnet"></a><span data-ttu-id="4cb6d-130">使用 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4cb6d-130">Working within ASP.NET</span></span>  
 <span data-ttu-id="4cb6d-131">[ASP.NET 主题中的 Using system.object](using-system-transactions-in-aspnet.md)介绍了如何在 <xref:System.Transactions> ASP.NET 应用程序中成功使用。</span><span class="sxs-lookup"><span data-stu-id="4cb6d-131">The [Using System.Transactions in ASP.NET](using-system-transactions-in-aspnet.md) topic describes how you can successfully use <xref:System.Transactions> inside an ASP.NET application.</span></span>
