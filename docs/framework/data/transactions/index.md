---
title: 事务处理
description: 查看 .NET 中的事务处理。 事务确保了面向数据的资源不会永久更新，除非所有操作都成功完成。
ms.date: 03/30/2017
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
ms.openlocfilehash: 30d69c55d968865cc80b8633bdbc2442f6d216de
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141909"
---
# <a name="transaction-processing"></a><span data-ttu-id="446ab-104">事务处理</span><span class="sxs-lookup"><span data-stu-id="446ab-104">Transaction Processing</span></span>
<span data-ttu-id="446ab-105">当您从网上书店购买书籍时，会用钱（以信贷方式）来交换书籍。</span><span class="sxs-lookup"><span data-stu-id="446ab-105">When you purchase a book from an online bookstore, you exchange money (in the form of credit) for a book.</span></span> <span data-ttu-id="446ab-106">如果您的信用良好，则一系列相关操作可确保您和书店可以相应地获得书籍和钱。</span><span class="sxs-lookup"><span data-stu-id="446ab-106">If your credit is good, a series of related operations ensures that you get the book and the bookstore gets your money.</span></span> <span data-ttu-id="446ab-107">但如果在交换期间该系列操作中的单个操作发生故障，则整个交换就会失败。</span><span class="sxs-lookup"><span data-stu-id="446ab-107">However, if a single operation in the series fails during the exchange, the entire exchange fails.</span></span> <span data-ttu-id="446ab-108">结果，您就得不到书籍，而书店也得不到钱。</span><span class="sxs-lookup"><span data-stu-id="446ab-108">You do not get the book and the bookstore does not get your money.</span></span>  
  
 <span data-ttu-id="446ab-109">负责使该交换取得平衡且可预测的技术称为事务处理。</span><span class="sxs-lookup"><span data-stu-id="446ab-109">The technology responsible for making the exchange balanced and predictable is called transaction processing.</span></span> <span data-ttu-id="446ab-110">事务可确保仅当事务单位中的所有操作都已成功完成时，才会永久更新面向数据的资源。</span><span class="sxs-lookup"><span data-stu-id="446ab-110">Transactions ensure that data-oriented resources are not permanently updated unless all operations within the transactional unit complete successfully.</span></span> <span data-ttu-id="446ab-111">通过将一组相关操作合并到不是完全成功就是完全失败的单位中，可以简化错误恢复并使应用程序更加可靠。</span><span class="sxs-lookup"><span data-stu-id="446ab-111">By combining a set of related operations into a unit that either completely succeeds or completely fails, you can simplify error recovery and make your application more reliable.</span></span>  
  
 <span data-ttu-id="446ab-112">事务处理系统包括承载一个面向事务的应用程序的计算机软硬件，该应用程序执行开展业务所需的例行事务。</span><span class="sxs-lookup"><span data-stu-id="446ab-112">Transaction processing systems consist of computer hardware and software hosting a transaction-oriented application that performs the routine transactions necessary to conduct business.</span></span> <span data-ttu-id="446ab-113">例如，管理销售订单录入、机票预订、工资单、员工记录、生产和装运的系统。</span><span class="sxs-lookup"><span data-stu-id="446ab-113">Examples include systems that manage sales order entry, airline reservations, payroll, employee records, manufacturing, and shipping.</span></span>  
  
 <span data-ttu-id="446ab-114">本节提供有关事务处理的常见信息，以及有关如何使用 Microsoft .NET Framework 编写事务应用程序和资源管理器的特定信息。</span><span class="sxs-lookup"><span data-stu-id="446ab-114">This section provides both general information on transaction processing, and specific information on how to write transactional applications and resource managers using the Microsoft .NET Framework.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="446ab-115">本节内容</span><span class="sxs-lookup"><span data-stu-id="446ab-115">In This Section</span></span>  
 [<span data-ttu-id="446ab-116">事务基础知识</span><span class="sxs-lookup"><span data-stu-id="446ab-116">Transaction Fundamentals</span></span>](transaction-fundamentals.md)  
 <span data-ttu-id="446ab-117">引入了基本的事务处理术语和概念。</span><span class="sxs-lookup"><span data-stu-id="446ab-117">Introduces basic transaction processing terms and concepts.</span></span>  
  
 [<span data-ttu-id="446ab-118">由 System.Transactions 提供的功能</span><span class="sxs-lookup"><span data-stu-id="446ab-118">Features Provided by System.Transactions</span></span>](features-provided-by-system-transactions.md)  
 <span data-ttu-id="446ab-119">讨论如何使用 System.Transactions 中的功能编写您自己的事务应用程序。</span><span class="sxs-lookup"><span data-stu-id="446ab-119">Discusses how you can use features in System.Transactions to write your own transactional application.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="446ab-120">引用</span><span class="sxs-lookup"><span data-stu-id="446ab-120">Reference</span></span>  
 <xref:System.Transactions>  
 <span data-ttu-id="446ab-121">提供用于使您的代码参与事务的类。</span><span class="sxs-lookup"><span data-stu-id="446ab-121">Provides classes that allow your code to participate in transactions.</span></span> <span data-ttu-id="446ab-122">这些类支持的事务可使用多个分布式参与者、多阶段通知和持久登记。</span><span class="sxs-lookup"><span data-stu-id="446ab-122">The classes support transactions with multiple distributed participants, multiple phase notifications, and durable enlistments.</span></span>
