---
title: 保护服务和客户端的安全
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: 713737b129771967958fddf44e9ef28583d49422
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554073"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="ba67f-102">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="ba67f-102">Securing Services and Clients</span></span>
<span data-ttu-id="ba67f-103">本部分中的信息重点介绍 Windows Communication Foundation (WCF) 的编程安全性。</span><span class="sxs-lookup"><span data-stu-id="ba67f-103">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="ba67f-104">通常，这包括选择系统提供的相应绑定、设置安全元素的属性，然后设置服务行为的属性（控制检索凭据以供服务或客户端使用的方式）。</span><span class="sxs-lookup"><span data-stu-id="ba67f-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="ba67f-105">这些技术涵盖大多数用户在大多数情况下的安全要求，如 [常见安全方案](common-security-scenarios.md)中所示。</span><span class="sxs-lookup"><span data-stu-id="ba67f-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](common-security-scenarios.md).</span></span> <span data-ttu-id="ba67f-106">如果你的方案需要更多功能，请首先查看 [具有自定义绑定的安全功能](security-capabilities-with-custom-bindings.md);如果解决方案不明显，请参阅 [扩展安全性](../extending/extending-security.md)。</span><span class="sxs-lookup"><span data-stu-id="ba67f-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../extending/extending-security.md).</span></span> <span data-ttu-id="ba67f-107">如果要创建 (或与) 使用丰富声明的系统进行互操作，请参阅 [授权](authorization-in-wcf.md)中的主题。</span><span class="sxs-lookup"><span data-stu-id="ba67f-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba67f-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="ba67f-108">In This Section</span></span>  
 [<span data-ttu-id="ba67f-109">WCF 安全编程</span><span class="sxs-lookup"><span data-stu-id="ba67f-109">Programming WCF Security</span></span>](programming-wcf-security.md)  
 <span data-ttu-id="ba67f-110">用于保护消息安全的编程模型概述。</span><span class="sxs-lookup"><span data-stu-id="ba67f-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="ba67f-111">传输安全概述</span><span class="sxs-lookup"><span data-stu-id="ba67f-111">Transport Security Overview</span></span>](transport-security-overview.md)  
 <span data-ttu-id="ba67f-112">如何通过传输层保护消息安全概述。</span><span class="sxs-lookup"><span data-stu-id="ba67f-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="ba67f-113">消息安全</span><span class="sxs-lookup"><span data-stu-id="ba67f-113">Message Security</span></span>](message-security-in-wcf.md)  
 <span data-ttu-id="ba67f-114">汇总在 Windows Communication Foundation 中使用消息级安全性 (WCF) 的原因。</span><span class="sxs-lookup"><span data-stu-id="ba67f-114">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="ba67f-115">安全会话</span><span class="sxs-lookup"><span data-stu-id="ba67f-115">Secure Sessions</span></span>](secure-sessions.md)  
 <span data-ttu-id="ba67f-116">讨论在保护 WCF 会话时需要注意的事项。</span><span class="sxs-lookup"><span data-stu-id="ba67f-116">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="ba67f-117">使用证书</span><span class="sxs-lookup"><span data-stu-id="ba67f-117">Working with Certificates</span></span>](working-with-certificates.md)  
 <span data-ttu-id="ba67f-118">说明使用 X.509 证书时必须完成的一些常见任务。</span><span class="sxs-lookup"><span data-stu-id="ba67f-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ba67f-119">参考</span><span class="sxs-lookup"><span data-stu-id="ba67f-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="ba67f-120">相关章节</span><span class="sxs-lookup"><span data-stu-id="ba67f-120">Related Sections</span></span>  
 [<span data-ttu-id="ba67f-121">安全概念</span><span class="sxs-lookup"><span data-stu-id="ba67f-121">Security Concepts</span></span>](security-concepts.md)  
  
 [<span data-ttu-id="ba67f-122">扩展安全性</span><span class="sxs-lookup"><span data-stu-id="ba67f-122">Extending Security</span></span>](../extending/extending-security.md)  
  
 [<span data-ttu-id="ba67f-123">常用安全方案</span><span class="sxs-lookup"><span data-stu-id="ba67f-123">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
 [<span data-ttu-id="ba67f-124">绑定与安全</span><span class="sxs-lookup"><span data-stu-id="ba67f-124">Bindings and Security</span></span>](bindings-and-security.md)  
  
 [<span data-ttu-id="ba67f-125">使用自定义绑定的安全功能</span><span class="sxs-lookup"><span data-stu-id="ba67f-125">Security Capabilities with Custom Bindings</span></span>](security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="ba67f-126">扩展安全性</span><span class="sxs-lookup"><span data-stu-id="ba67f-126">Extending Security</span></span>](../extending/extending-security.md)  
  
 [<span data-ttu-id="ba67f-127">授权</span><span class="sxs-lookup"><span data-stu-id="ba67f-127">Authorization</span></span>](authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="ba67f-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="ba67f-128">See also</span></span>

- [<span data-ttu-id="ba67f-129">基本 WCF 编程</span><span class="sxs-lookup"><span data-stu-id="ba67f-129">Basic WCF Programming</span></span>](../basic-wcf-programming.md)
- <span data-ttu-id="ba67f-130">[Windows Server App Fabric 的安全模型](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ba67f-130">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
