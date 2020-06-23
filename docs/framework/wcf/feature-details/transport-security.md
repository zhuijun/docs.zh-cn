---
title: 传输安全
description: 使用这些参考来了解 WFC 中的传输安全机制、如何实现它们以及它们的选项。
ms.date: 03/30/2017
ms.assetid: 86c94153-e48d-4539-b6cf-cd8060582e7f
ms.openlocfilehash: d39aa49906b79b9e12eecf04629080863719f986
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244746"
---
# <a name="transport-security"></a><span data-ttu-id="018f7-103">传输安全</span><span class="sxs-lookup"><span data-stu-id="018f7-103">Transport Security</span></span>
<span data-ttu-id="018f7-104">Windows Communication Foundation （WCF）中的传输安全取决于所选绑定。</span><span class="sxs-lookup"><span data-stu-id="018f7-104">Transport security in Windows Communication Foundation (WCF) depends on the binding selected.</span></span> <span data-ttu-id="018f7-105">绑定所实现的传输决定实际的安全机制。</span><span class="sxs-lookup"><span data-stu-id="018f7-105">The transport that the binding implements determines the actual security mechanism.</span></span> <span data-ttu-id="018f7-106">本节中的主题说明所实现的机制及其选项。</span><span class="sxs-lookup"><span data-stu-id="018f7-106">The topics in this section explain the mechanisms that are implemented and their options.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="018f7-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="018f7-107">In This Section</span></span>  
 [<span data-ttu-id="018f7-108">传输安全概述</span><span class="sxs-lookup"><span data-stu-id="018f7-108">Transport Security Overview</span></span>](transport-security-overview.md)  
 <span data-ttu-id="018f7-109">说明 WCF 中传输安全性的基础知识。</span><span class="sxs-lookup"><span data-stu-id="018f7-109">Explains the basics of transport security in WCF.</span></span>  
  
 [<span data-ttu-id="018f7-110">HTTP 传输安全</span><span class="sxs-lookup"><span data-stu-id="018f7-110">HTTP Transport Security</span></span>](http-transport-security.md)  
 <span data-ttu-id="018f7-111">说明 WCF 如何实现安全套接字层（SSL 或 HTTPS）。</span><span class="sxs-lookup"><span data-stu-id="018f7-111">Explains how WCF implements Secure Sockets Layer (SSL, or HTTPS).</span></span>  
  
 [<span data-ttu-id="018f7-112">了解 HTTP 身份验证</span><span class="sxs-lookup"><span data-stu-id="018f7-112">Understanding HTTP Authentication</span></span>](understanding-http-authentication.md)  
 <span data-ttu-id="018f7-113">描述 HTTP 身份验证方案，如基本、摘要式、NT LAN Manager (NTLM) 及其他。</span><span class="sxs-lookup"><span data-stu-id="018f7-113">Describes HTTP authentication schemes, such as Basic, Digest, NT LAN Manager (NTLM), and others.</span></span>  
  
 [<span data-ttu-id="018f7-114">将模拟用于传输安全</span><span class="sxs-lookup"><span data-stu-id="018f7-114">Using Impersonation with Transport Security</span></span>](using-impersonation-with-transport-security.md)  
 <span data-ttu-id="018f7-115">说明传输安全模式的五个可能的模拟级别。</span><span class="sxs-lookup"><span data-stu-id="018f7-115">Explains the five levels of impersonation that are possible with transport security mode.</span></span>  
  
 [<span data-ttu-id="018f7-116">如何：使用 SSL 证书配置端口</span><span class="sxs-lookup"><span data-stu-id="018f7-116">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)  
 <span data-ttu-id="018f7-117">浏览有关在具有用于 SSL（传输）安全的 X.509 证书的计算机上配置端口的基本知识。</span><span class="sxs-lookup"><span data-stu-id="018f7-117">Walks through the basics of configuring a port on a machine with an X.509 certificate for SSL (transport) security.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="018f7-118">参考</span><span class="sxs-lookup"><span data-stu-id="018f7-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="018f7-119">相关章节</span><span class="sxs-lookup"><span data-stu-id="018f7-119">Related Sections</span></span>  
 [<span data-ttu-id="018f7-120">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="018f7-120">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="018f7-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="018f7-121">See also</span></span>

- [<span data-ttu-id="018f7-122">WCF 安全编程</span><span class="sxs-lookup"><span data-stu-id="018f7-122">Programming WCF Security</span></span>](programming-wcf-security.md)
