---
title: Windows Communication Foundation 事务概述
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
ms.openlocfilehash: a8e3306612e016568ad7cfd5138ab538af771a17
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585826"
---
# <a name="windows-communication-foundation-transactions-overview"></a><span data-ttu-id="1ffed-102">Windows Communication Foundation 事务概述</span><span class="sxs-lookup"><span data-stu-id="1ffed-102">Windows Communication Foundation Transactions Overview</span></span>
<span data-ttu-id="1ffed-103">事务可提供一种分组方法，将一组操作分为单个不可分的执行单元。</span><span class="sxs-lookup"><span data-stu-id="1ffed-103">Transactions provide a way to group a set of actions or operations into a single indivisible unit of execution.</span></span> <span data-ttu-id="1ffed-104">事务是指具有下列属性的操作集合：</span><span class="sxs-lookup"><span data-stu-id="1ffed-104">A transaction is a collection of operations with the following properties:</span></span>  
  
- <span data-ttu-id="1ffed-105">原子性。</span><span class="sxs-lookup"><span data-stu-id="1ffed-105">Atomicity.</span></span> <span data-ttu-id="1ffed-106">此属性可确保特定事务下完成的所有更新都已提交并保持持久，或所有这些更新都已中止并回滚到其先前状态。</span><span class="sxs-lookup"><span data-stu-id="1ffed-106">This ensures that either all of the updates completed under a specific transaction are committed and made durable or they are all aborted and rolled back to their previous state.</span></span>  
  
- <span data-ttu-id="1ffed-107">一致性。</span><span class="sxs-lookup"><span data-stu-id="1ffed-107">Consistency.</span></span> <span data-ttu-id="1ffed-108">此属性可保证某一事务下所做的更改表示从一种一致状态转换到另一种一致状态。</span><span class="sxs-lookup"><span data-stu-id="1ffed-108">This guarantees that the changes made under a transaction represent a transformation from one consistent state to another.</span></span> <span data-ttu-id="1ffed-109">例如，将钱从支票帐户转移到存款帐户的事务并不改变整个银行帐户中的钱的总额。</span><span class="sxs-lookup"><span data-stu-id="1ffed-109">For example, a transaction that transfers money from a checking account to a savings account does not change the amount of money in the overall bank account.</span></span>  
  
- <span data-ttu-id="1ffed-110">隔离。</span><span class="sxs-lookup"><span data-stu-id="1ffed-110">Isolation.</span></span> <span data-ttu-id="1ffed-111">此属性可防止事务遵循属于其他并发事务的未提交的更改。</span><span class="sxs-lookup"><span data-stu-id="1ffed-111">This prevents a transaction from observing uncommitted changes belonging to other concurrent transactions.</span></span> <span data-ttu-id="1ffed-112">隔离在确保一种事务不能对另一事务的执行产生意外的影响的同时，还提供一个抽象的并发。</span><span class="sxs-lookup"><span data-stu-id="1ffed-112">Isolation provides an abstraction of concurrency while ensuring one transaction cannot have an unexpected impact on the execution of another transaction.</span></span>  
  
- <span data-ttu-id="1ffed-113">持续性。</span><span class="sxs-lookup"><span data-stu-id="1ffed-113">Durability.</span></span> <span data-ttu-id="1ffed-114">这意味着一旦提交对托管资源（如数据库记录）的更新，即使出现失败这些更新也会保持持久。</span><span class="sxs-lookup"><span data-stu-id="1ffed-114">This means that once committed, updates to managed resources (such as a database record) will be persistent in the face of failures.</span></span>  
  
 <span data-ttu-id="1ffed-115">Windows Communication Foundation （WCF）提供了一组丰富的功能，使您能够在 Web 服务应用程序中创建分布式事务。</span><span class="sxs-lookup"><span data-stu-id="1ffed-115">Windows Communication Foundation (WCF) provides a rich set of features that enable you to create distributed transactions in your Web service application.</span></span>  
  
 <span data-ttu-id="1ffed-116">WCF 实现对 ws-atomictransaction （WS-AT）协议的支持，该协议使 WCF 应用程序能够将事务流式传输到可互操作的应用程序，如使用第三方技术生成的可互操作的 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="1ffed-116">WCF implements support for the WS-AtomicTransaction (WS-AT) protocol that enables WCF applications to flow transactions to interoperable applications, such as interoperable Web services built using third-party technology.</span></span> <span data-ttu-id="1ffed-117">WCF 还实现对 OLE 事务协议的支持，该协议可用于不需要互操作功能来启用事务流的情况。</span><span class="sxs-lookup"><span data-stu-id="1ffed-117">WCF also implements support for the OLE Transactions protocol, which can be used in scenarios where you do not need interop functionality to enable transaction flow.</span></span>  
  
 <span data-ttu-id="1ffed-118">你可以使用应用程序配置文件来配置绑定以启用或禁用事务流，以及设置有关绑定的所需事务协定。</span><span class="sxs-lookup"><span data-stu-id="1ffed-118">You can use an application configuration file to configure bindings to enable or disable transaction flow, as well as set the desired transaction protocol on a binding.</span></span> <span data-ttu-id="1ffed-119">此外，你可以使用配置文件在服务级别设置事务超时值。</span><span class="sxs-lookup"><span data-stu-id="1ffed-119">In addition, you can set transaction time-outs at the service level using the configuration file.</span></span> <span data-ttu-id="1ffed-120">有关详细信息，请参阅[启用事务流](enabling-transaction-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="1ffed-120">For more information, see [Enabling Transaction Flow](enabling-transaction-flow.md).</span></span>  
  
 <span data-ttu-id="1ffed-121"><xref:System.ServiceModel> 命名空间中的事务属性允许你进行以下操作：</span><span class="sxs-lookup"><span data-stu-id="1ffed-121">Transaction attributes in the <xref:System.ServiceModel> namespace allow you to do the following:</span></span>  
  
- <span data-ttu-id="1ffed-122">使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 属性配置事务超时值以及隔离级别的筛选。</span><span class="sxs-lookup"><span data-stu-id="1ffed-122">Configure transaction time-outs and isolation-level filtering using the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span>  
  
- <span data-ttu-id="1ffed-123">启用事务功能并使用 <xref:System.ServiceModel.OperationBehaviorAttribute> 属性配置事务完成行为。</span><span class="sxs-lookup"><span data-stu-id="1ffed-123">Enable transactions functionality and configure transaction completion behavior using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span>  
  
- <span data-ttu-id="1ffed-124">使用协定方法上的 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.OperationContractAttribute> 属性来要求、允许或拒绝事务流。</span><span class="sxs-lookup"><span data-stu-id="1ffed-124">Use the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes on a contract method to require, allow or deny transaction flow.</span></span>  
  
 <span data-ttu-id="1ffed-125">有关详细信息，请[参阅 "](servicemodel-transaction-attributes.md)"。</span><span class="sxs-lookup"><span data-stu-id="1ffed-125">For more information, see [ServiceModel Transaction Attributes](servicemodel-transaction-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ffed-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1ffed-126">See also</span></span>

- [<span data-ttu-id="1ffed-127">ServiceModel 事务属性</span><span class="sxs-lookup"><span data-stu-id="1ffed-127">ServiceModel Transaction Attributes</span></span>](servicemodel-transaction-attributes.md)
- [<span data-ttu-id="1ffed-128">启用事务流</span><span class="sxs-lookup"><span data-stu-id="1ffed-128">Enabling Transaction Flow</span></span>](enabling-transaction-flow.md)
