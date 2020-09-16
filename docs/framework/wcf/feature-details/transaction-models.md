---
title: 事务模型
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 2d3d0631c47506e7bd99d90ed49a1fdc76cc7a59
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556819"
---
# <a name="transaction-models"></a><span data-ttu-id="687f6-102">事务模型</span><span class="sxs-lookup"><span data-stu-id="687f6-102">Transaction Models</span></span>
<span data-ttu-id="687f6-103">本主题描述 Microsoft 提供的事务编程模型和基础结构组件之间的关系。</span><span class="sxs-lookup"><span data-stu-id="687f6-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="687f6-104">使用 (WCF) Windows Communication Foundation 中的事务时，务必要了解不要在不同的事务模型之间进行选择，而是在集成且一致的模型的不同层上操作。</span><span class="sxs-lookup"><span data-stu-id="687f6-104">When using transactions in Windows Communication Foundation (WCF), it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="687f6-105">以下各部分描述了三个主要事务组件。</span><span class="sxs-lookup"><span data-stu-id="687f6-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="687f6-106">Windows Communication Foundation 事务</span><span class="sxs-lookup"><span data-stu-id="687f6-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="687f6-107">WCF 中的事务支持可让你编写事务性服务。</span><span class="sxs-lookup"><span data-stu-id="687f6-107">The transaction support in WCF allows you write transactional services.</span></span> <span data-ttu-id="687f6-108">此外，在支持 ws-atomictransaction (WS-AT) 协议的情况下，应用程序可以将事务流式传输到使用 WCF 或第三方技术生成的 Web 服务。</span><span class="sxs-lookup"><span data-stu-id="687f6-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either WCF or third-party technology.</span></span>  
  
 <span data-ttu-id="687f6-109">在 WCF 服务或应用程序中，WCF 事务功能提供了属性和配置，用于以声明方式指定基础结构创建、流动和同步事务的方式和时间。</span><span class="sxs-lookup"><span data-stu-id="687f6-109">In a WCF service or application, WCF transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="687f6-110">System.Transactions 事务</span><span class="sxs-lookup"><span data-stu-id="687f6-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="687f6-111"><xref:System.Transactions> 命名空间同时提供了一个基于 <xref:System.Transactions.Transaction> 类的显式编程模型和一个使用 <xref:System.Transactions.TransactionScope> 类的隐式编程模型（在此模型中，基础结构自动管理事务）。</span><span class="sxs-lookup"><span data-stu-id="687f6-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="687f6-112">有关如何使用这两种模型创建事务应用程序的详细信息，请参阅 [编写事务应用程序](https://go.microsoft.com/fwlink/?LinkId=94947)。</span><span class="sxs-lookup"><span data-stu-id="687f6-112">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](https://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="687f6-113">在 WCF 服务或应用程序中， <xref:System.Transactions> 提供用于在客户端应用程序中创建事务的编程模型，并在需要时，在服务中显式与事务进行交互。</span><span class="sxs-lookup"><span data-stu-id="687f6-113">In a WCF service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="687f6-114">MSDTC 事务</span><span class="sxs-lookup"><span data-stu-id="687f6-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="687f6-115">Microsoft Distributed Transaction Coordinator (MSDTC) 是一个事务管理器，它为分布式事务提供支持。</span><span class="sxs-lookup"><span data-stu-id="687f6-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="687f6-116">有关详细信息，请参阅 [DTC 程序员参考](/previous-versions/windows/desktop/ms686108(v=vs.85))。</span><span class="sxs-lookup"><span data-stu-id="687f6-116">For more information, see the [DTC Programmer's Reference](/previous-versions/windows/desktop/ms686108(v=vs.85)).</span></span>  
  
 <span data-ttu-id="687f6-117">在 WCF 服务或应用程序中，MSDTC 提供基础结构，用于协调客户端或服务中创建的事务。</span><span class="sxs-lookup"><span data-stu-id="687f6-117">In a WCF service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
