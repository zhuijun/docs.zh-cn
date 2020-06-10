---
title: Windows Communication Foundation 安全性
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
ms.openlocfilehash: 327fb509a5186a0b3f428efc2ddd7f983bcfa978
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595137"
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="7e8a9-102">Windows Communication Foundation 安全性</span><span class="sxs-lookup"><span data-stu-id="7e8a9-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="7e8a9-103">本节中的主题介绍 Windows Communication Foundation （WCF）安全功能以及如何使用它们来帮助保护消息。</span><span class="sxs-lookup"><span data-stu-id="7e8a9-103">The topics in this section describe Windows Communication Foundation (WCF) security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="7e8a9-104">有关 Windows Server AppFabric 和 security 的详细信息，请参阅[Windows Server Appfabric 安全模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="7e8a9-104">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7e8a9-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="7e8a9-105">In This Section</span></span>  
 [<span data-ttu-id="7e8a9-106">安全性概述</span><span class="sxs-lookup"><span data-stu-id="7e8a9-106">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="7e8a9-107">描述 WCF 中的安全功能。</span><span class="sxs-lookup"><span data-stu-id="7e8a9-107">Describes the security features in WCF.</span></span>  
  
 [<span data-ttu-id="7e8a9-108">安全性概念</span><span class="sxs-lookup"><span data-stu-id="7e8a9-108">Security Concepts</span></span>](security-concepts.md)  
 <span data-ttu-id="7e8a9-109">描述 WCF 安全性中使用的基本术语和概念。</span><span class="sxs-lookup"><span data-stu-id="7e8a9-109">Describes the basic terminology and concepts used in WCF security.</span></span>  
  
 [<span data-ttu-id="7e8a9-110">常用安全方案</span><span class="sxs-lookup"><span data-stu-id="7e8a9-110">Common Security Scenarios</span></span>](common-security-scenarios.md)  
 <span data-ttu-id="7e8a9-111">介绍可以配置 WCF 的方案和拓扑。</span><span class="sxs-lookup"><span data-stu-id="7e8a9-111">Describes scenarios and topologies you can configure with WCF.</span></span>  
  
 [<span data-ttu-id="7e8a9-112">安全行为</span><span class="sxs-lookup"><span data-stu-id="7e8a9-112">Security Behaviors</span></span>](security-behaviors-in-wcf.md)  
 <span data-ttu-id="7e8a9-113">概要介绍会影响安全的 WCF 行为，例如设置凭据。</span><span class="sxs-lookup"><span data-stu-id="7e8a9-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="7e8a9-114">绑定与安全</span><span class="sxs-lookup"><span data-stu-id="7e8a9-114">Bindings and Security</span></span>](bindings-and-security.md)  
 <span data-ttu-id="7e8a9-115">面向安全的绑定视图，包括演示如何创建自定义安全绑定的主题。</span><span class="sxs-lookup"><span data-stu-id="7e8a9-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="7e8a9-116">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="7e8a9-116">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
 <span data-ttu-id="7e8a9-117">介绍如何使用 WCF 安全功能保护消息。</span><span class="sxs-lookup"><span data-stu-id="7e8a9-117">Describes how to secure messages using WCF security features.</span></span>  
  
 [<span data-ttu-id="7e8a9-118">身份验证</span><span class="sxs-lookup"><span data-stu-id="7e8a9-118">Authentication</span></span>](authentication-in-wcf.md)  
 <span data-ttu-id="7e8a9-119">演示常见的身份验证任务。</span><span class="sxs-lookup"><span data-stu-id="7e8a9-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="7e8a9-120">授权</span><span class="sxs-lookup"><span data-stu-id="7e8a9-120">Authorization</span></span>](authorization-in-wcf.md)  
 <span data-ttu-id="7e8a9-121">描述带有安全实现的常见授权方案。</span><span class="sxs-lookup"><span data-stu-id="7e8a9-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="7e8a9-122">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="7e8a9-122">Federation and Issued Tokens</span></span>](federation-and-issued-tokens.md)  
 <span data-ttu-id="7e8a9-123">描述联合身份验证的基本知识以及如何创建与联合服务器进行通信的客户端。</span><span class="sxs-lookup"><span data-stu-id="7e8a9-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="7e8a9-124">部分信任</span><span class="sxs-lookup"><span data-stu-id="7e8a9-124">Partial Trust</span></span>](partial-trust.md)  
 <span data-ttu-id="7e8a9-125">介绍如何运行部分受信任的方案和 WCF 限制（在部分受信任的情况下运行）。</span><span class="sxs-lookup"><span data-stu-id="7e8a9-125">Describes how to run partially-trusted scenarios and WCF limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="7e8a9-126">审核</span><span class="sxs-lookup"><span data-stu-id="7e8a9-126">Auditing</span></span>](auditing-security-events.md)  
 <span data-ttu-id="7e8a9-127">描述如何审核安全事件。</span><span class="sxs-lookup"><span data-stu-id="7e8a9-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="7e8a9-128">安全指导和最佳做法</span><span class="sxs-lookup"><span data-stu-id="7e8a9-128">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)  
 <span data-ttu-id="7e8a9-129">用于创建安全 WCF 应用程序的准则。</span><span class="sxs-lookup"><span data-stu-id="7e8a9-129">Guidelines for creating secure WCF applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7e8a9-130">参考</span><span class="sxs-lookup"><span data-stu-id="7e8a9-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="7e8a9-131">相关章节</span><span class="sxs-lookup"><span data-stu-id="7e8a9-131">Related Sections</span></span>  
 [<span data-ttu-id="7e8a9-132">WCF 功能详细信息</span><span class="sxs-lookup"><span data-stu-id="7e8a9-132">WCF Feature Details</span></span>](index.md)  
  
 [<span data-ttu-id="7e8a9-133">基本 WCF 编程</span><span class="sxs-lookup"><span data-stu-id="7e8a9-133">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
 [<span data-ttu-id="7e8a9-134">入门教程</span><span class="sxs-lookup"><span data-stu-id="7e8a9-134">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)  
  
 [<span data-ttu-id="7e8a9-135">概念性概述</span><span class="sxs-lookup"><span data-stu-id="7e8a9-135">Conceptual Overview</span></span>](../conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="7e8a9-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e8a9-136">See also</span></span>

- [<span data-ttu-id="7e8a9-137">配置应用程序</span><span class="sxs-lookup"><span data-stu-id="7e8a9-137">Configuring Your Application</span></span>](../diagnostics/configuring-your-application.md)
