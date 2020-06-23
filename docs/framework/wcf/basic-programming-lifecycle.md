---
title: 基本编程生命周期
description: 了解用于生成 WCF 应用程序的任务。 WCF 使应用可以在同一台计算机上、通过网络或在不同的应用程序平台上进行通信。
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: c672827fff780fd263f5355520bb6ccf02bb902e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245526"
---
# <a name="basic-programming-lifecycle"></a><span data-ttu-id="d4c4b-104">基本编程生命周期</span><span class="sxs-lookup"><span data-stu-id="d4c4b-104">Basic Programming Lifecycle</span></span>
<span data-ttu-id="d4c4b-105">Windows Communication Foundation （WCF）使应用程序可以在同一台计算机上、在 Internet 上或在不同应用程序平台上通信。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-105">Windows Communication Foundation (WCF) enables applications to communicate whether they are on the same computer, across the Internet, or on different application platforms.</span></span> <span data-ttu-id="d4c4b-106">本主题概述生成 WCF 应用程序所需的任务。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-106">This topic outlines the tasks that are required to build a WCF application.</span></span> <span data-ttu-id="d4c4b-107">有关有效的示例应用程序，请参阅[入门教程](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-107">For a working sample application, see [Getting Started Tutorial](getting-started-tutorial.md).</span></span>  
  
## <a name="the-basic-tasks"></a><span data-ttu-id="d4c4b-108">基本任务</span><span class="sxs-lookup"><span data-stu-id="d4c4b-108">The Basic Tasks</span></span>  
 <span data-ttu-id="d4c4b-109">要执行的基本任务依次为：</span><span class="sxs-lookup"><span data-stu-id="d4c4b-109">The basic tasks to perform are, in order:</span></span>  
  
1. <span data-ttu-id="d4c4b-110">定义服务协定。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-110">Define the service contract.</span></span> <span data-ttu-id="d4c4b-111">服务协定指定服务的签名、服务交换的数据和其他协定要求的数据。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-111">A service contract specifies the signature of a service, the data it exchanges, and other contractually required data.</span></span> <span data-ttu-id="d4c4b-112">有关详细信息，请参阅[设计服务协定](designing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-112">For more information, see [Designing Service Contracts](designing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="d4c4b-113">实现协定。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-113">Implement the contract.</span></span> <span data-ttu-id="d4c4b-114">若要实现服务协定，请创建实现协定的类并指定运行时应具有的自定义行为。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-114">To implement a service contract, create a class that implements the contract and specify custom behaviors that the runtime should have.</span></span> <span data-ttu-id="d4c4b-115">有关详细信息，请参阅[实现服务协定](implementing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-115">For more information, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
3. <span data-ttu-id="d4c4b-116">通过指定终结点和其他行为信息来配置服务。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-116">Configure the service by specifying endpoints and other behavior information.</span></span> <span data-ttu-id="d4c4b-117">有关详细信息，请参阅[配置服务](configuring-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-117">For more information, see [Configuring Services](configuring-services.md).</span></span>  
  
4. <span data-ttu-id="d4c4b-118">承载服务。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-118">Host the service.</span></span> <span data-ttu-id="d4c4b-119">有关详细信息，请参阅[托管服务](hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-119">For more information, see [Hosting Services](hosting-services.md).</span></span>  
  
5. <span data-ttu-id="d4c4b-120">生成客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-120">Build a client application.</span></span> <span data-ttu-id="d4c4b-121">有关详细信息，请参阅[生成客户端](building-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-121">For more information, see [Building Clients](building-clients.md).</span></span>  
  
 <span data-ttu-id="d4c4b-122">尽管本节中的主题遵循此顺序，但是一些方案并不会从头开始。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-122">Although the topics in this section follow this order, some scenarios do not start at the beginning.</span></span> <span data-ttu-id="d4c4b-123">例如，如果想要为预先存在的服务生成客户端，则从步骤 5 开始。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-123">For example, if you want to build a client for a pre-existing service, you start at step 5.</span></span> <span data-ttu-id="d4c4b-124">或者，如果您是在生成其他人要使用的服务，则可以跳过步骤 5。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-124">Or if you are building a service that others will use, you may skip step 5.</span></span>  
  
 <span data-ttu-id="d4c4b-125">熟悉开发服务协定后，还可以阅读[扩展性简介](introduction-to-extensibility.md)。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-125">Once you are familiar with developing service contracts, you can also read [Introduction to Extensibility](introduction-to-extensibility.md).</span></span> <span data-ttu-id="d4c4b-126">如果你的服务出现问题，请查看[WCF 疑难解答快速入门](wcf-troubleshooting-quickstart.md)，查看其他人是否有相同或类似的问题。</span><span class="sxs-lookup"><span data-stu-id="d4c4b-126">If you have problems with your service, check [WCF Troubleshooting Quickstart](wcf-troubleshooting-quickstart.md) to see whether others have the same or similar problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4c4b-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="d4c4b-127">See also</span></span>

- [<span data-ttu-id="d4c4b-128">实现服务协定</span><span class="sxs-lookup"><span data-stu-id="d4c4b-128">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
