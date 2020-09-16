---
title: WCF 中的身份验证
description: 了解 WCF 中几个提供身份验证的机制，例如 Windows 身份验证、x.509 证书、用户名和密码。
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: 414353b360992abea69d47de9efb22c3c77f4bf6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558272"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="154bf-103">WCF 中的身份验证</span><span class="sxs-lookup"><span data-stu-id="154bf-103">Authentication in WCF</span></span>
<span data-ttu-id="154bf-104">以下主题介绍了 Windows Communication Foundation (WCF) 提供身份验证的多种不同机制，这些机制提供身份验证，例如 Windows 身份验证、x.509 证书以及用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="154bf-104">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="154bf-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="154bf-105">In This Section</span></span>  
 [<span data-ttu-id="154bf-106">如何：使用 ASP.NET 成员资格提供程序</span><span class="sxs-lookup"><span data-stu-id="154bf-106">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="154bf-107">ASP.NET 功能包括成员资格和角色提供程序、用于存储用户名/密码对以供进行身份验证的数据库，以及用于身份验证的用户角色。</span><span class="sxs-lookup"><span data-stu-id="154bf-107">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="154bf-108">本主题说明 WCF 服务如何使用同一个数据库对用户进行身份验证和授权。</span><span class="sxs-lookup"><span data-stu-id="154bf-108">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="154bf-109">如何：使用自定义用户名和密码验证程序</span><span class="sxs-lookup"><span data-stu-id="154bf-109">How to: Use a Custom User Name and Password Validator</span></span>](how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="154bf-110">演示如何集成自定义用户名/密码验证程序。</span><span class="sxs-lookup"><span data-stu-id="154bf-110">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="154bf-111">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="154bf-111">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)  
 <span data-ttu-id="154bf-112">作为额外的安全措施，客户端可以通过指定服务的预期 *标识* 来对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="154bf-112">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="154bf-113">如果期望的标识与服务返回的标识不匹配，则身份验证失败。</span><span class="sxs-lookup"><span data-stu-id="154bf-113">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="154bf-114">安全协商和超时</span><span class="sxs-lookup"><span data-stu-id="154bf-114">Security Negotiation and Timeouts</span></span>](security-negotiation-and-timeouts.md)  
 <span data-ttu-id="154bf-115">说明如何使用 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> 类的 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> 属性。</span><span class="sxs-lookup"><span data-stu-id="154bf-115">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="154bf-116">调试 Windows 身份验证错误</span><span class="sxs-lookup"><span data-stu-id="154bf-116">Debugging Windows Authentication Errors</span></span>](debugging-windows-authentication-errors.md)  
 <span data-ttu-id="154bf-117">重点说明使用 Windows 身份验证时所遇到的常见问题。</span><span class="sxs-lookup"><span data-stu-id="154bf-117">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="154bf-118">参考</span><span class="sxs-lookup"><span data-stu-id="154bf-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="154bf-119">相关章节</span><span class="sxs-lookup"><span data-stu-id="154bf-119">Related Sections</span></span>  
 [<span data-ttu-id="154bf-120">常用安全方案</span><span class="sxs-lookup"><span data-stu-id="154bf-120">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="154bf-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="154bf-121">See also</span></span>

- [<span data-ttu-id="154bf-122">安全性概述</span><span class="sxs-lookup"><span data-stu-id="154bf-122">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="154bf-123">[Windows Server App Fabric 的安全模型](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="154bf-123">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
