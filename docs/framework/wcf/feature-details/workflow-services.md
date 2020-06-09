---
title: 工作流服务
ms.date: 03/30/2017
ms.assetid: 7b05c766-f181-425d-9a3d-2a5e150c85f7
ms.openlocfilehash: c7a5c6245702497fcd75341b3ff7ba08dc190fa5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600122"
---
# <a name="workflow-services"></a><span data-ttu-id="46be2-102">工作流服务</span><span class="sxs-lookup"><span data-stu-id="46be2-102">Workflow Services</span></span>
<span data-ttu-id="46be2-103">使用 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]，您可以在 XAML 中以声明方式充分描述基于工作流的服务。</span><span class="sxs-lookup"><span data-stu-id="46be2-103">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] allows you to fully describe a workflow-based service declaratively in XAML.</span></span> <span data-ttu-id="46be2-104">您完全可以在 XAML 中定义实现服务的工作流并描述服务所公开的终结点。</span><span class="sxs-lookup"><span data-stu-id="46be2-104">You can define a workflow that implements your service and describe endpoints the service exposes, all entirely in XAML.</span></span> <span data-ttu-id="46be2-105">本节中的主题详细描述支持以声明方式编写服务的编程模型。</span><span class="sxs-lookup"><span data-stu-id="46be2-105">The topics in this section describe, in detail, the programming model that supports writing services declaratively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="46be2-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="46be2-106">In This Section</span></span>  
 [<span data-ttu-id="46be2-107">工作流服务概述</span><span class="sxs-lookup"><span data-stu-id="46be2-107">Workflow Services Overview</span></span>](workflow-services-overview.md)  
 <span data-ttu-id="46be2-108">描述创建和承载工作流服务所涉及的组件。</span><span class="sxs-lookup"><span data-stu-id="46be2-108">Describes the components involved in creating and hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="46be2-109">消息传递活动</span><span class="sxs-lookup"><span data-stu-id="46be2-109">Messaging Activities</span></span>](messaging-activities.md)  
 <span data-ttu-id="46be2-110">讨论允许工作流发送和接收消息的活动。</span><span class="sxs-lookup"><span data-stu-id="46be2-110">Discusses activities that allow workflows to send and receive messages.</span></span>  
  
 [<span data-ttu-id="46be2-111">如何：使用消息传递活动创建工作流服务</span><span class="sxs-lookup"><span data-stu-id="46be2-111">How to: Create a Workflow Service with Messaging Activities</span></span>](how-to-create-a-workflow-service-with-messaging-activities.md)  
 <span data-ttu-id="46be2-112">说明如何使用消息传递活动创建工作流服务。</span><span class="sxs-lookup"><span data-stu-id="46be2-112">Describes how to use messaging activities to create a workflow service.</span></span>  
  
 [<span data-ttu-id="46be2-113">如何：从工作流应用程序访问服务</span><span class="sxs-lookup"><span data-stu-id="46be2-113">How To: Access a Service From a Workflow Application</span></span>](how-to-access-a-service-from-a-workflow-application.md)  
 <span data-ttu-id="46be2-114">讨论如何从工作流应用程序调用服务。</span><span class="sxs-lookup"><span data-stu-id="46be2-114">Discusses how to call a service from a workflow application.</span></span>  
  
 [<span data-ttu-id="46be2-115">Correlation</span><span class="sxs-lookup"><span data-stu-id="46be2-115">Correlation</span></span>](correlation.md)  
 <span data-ttu-id="46be2-116">讨论相关性对象如何在彼此之间映射消息以及将消息映射到实例。</span><span class="sxs-lookup"><span data-stu-id="46be2-116">Discusses how correlation maps messages to each other and to instances.</span></span>  
  
 [<span data-ttu-id="46be2-117">无序消息处理</span><span class="sxs-lookup"><span data-stu-id="46be2-117">Out-of-Order Message Processing</span></span>](out-of-order-message-processing.md)  
 <span data-ttu-id="46be2-118">说明如何将服务配置为接受无序消息。</span><span class="sxs-lookup"><span data-stu-id="46be2-118">Describes configuring a service to accept out of order messages.</span></span>  
  
 [<span data-ttu-id="46be2-119">协定优先的工作流服务开发</span><span class="sxs-lookup"><span data-stu-id="46be2-119">Contract First Workflow Service Development</span></span>](../../windows-workflow-foundation/contract-first-workflow-service-development.md)  
 <span data-ttu-id="46be2-120">说明如何基于现有服务协定创建工作流服务。</span><span class="sxs-lookup"><span data-stu-id="46be2-120">Describes creating a workflow service based on an existing service contract.</span></span>  
  
 [<span data-ttu-id="46be2-121">如何：创建使用现有服务协定的工作流服务</span><span class="sxs-lookup"><span data-stu-id="46be2-121">How to: Create a workflow service that consumes an existing service contract</span></span>](../../windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)  
 <span data-ttu-id="46be2-122">提供了一个对使用现有服务协定创建工作流服务的分步说明示例。</span><span class="sxs-lookup"><span data-stu-id="46be2-122">Provides a step-by-step example of creating a workflow service using an existing service contract.</span></span>  
  
 [<span data-ttu-id="46be2-123">承载工作流服务概述</span><span class="sxs-lookup"><span data-stu-id="46be2-123">Hosting Workflow Services Overview</span></span>](hosting-workflow-services-overview.md)  
 <span data-ttu-id="46be2-124">描述承载工作流服务的不同方面。</span><span class="sxs-lookup"><span data-stu-id="46be2-124">Describes the different aspects of hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="46be2-125">在工作流中使用协定</span><span class="sxs-lookup"><span data-stu-id="46be2-125">Using Contracts in Workflow</span></span>](using-contracts-in-workflow.md)  
 <span data-ttu-id="46be2-126">描述不同类型的协定和协定接口。</span><span class="sxs-lookup"><span data-stu-id="46be2-126">Describes the different types of contracts and contract inference.</span></span>
