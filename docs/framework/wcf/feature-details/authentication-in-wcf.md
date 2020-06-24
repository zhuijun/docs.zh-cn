---
title: WCF 中的身份验证
description: 了解 WCF 中几个提供身份验证的机制，例如 Windows 身份验证、x.509 证书、用户名和密码。
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: 4c3348cfb84b8571dc1f24b774ffcd691aaa5001
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247515"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="db176-103">WCF 中的身份验证</span><span class="sxs-lookup"><span data-stu-id="db176-103">Authentication in WCF</span></span>
<span data-ttu-id="db176-104">以下主题介绍 Windows Communication Foundation （WCF）中的一些不同机制，这些机制提供身份验证，例如 Windows 身份验证、x.509 证书以及用户名和密码。</span><span class="sxs-lookup"><span data-stu-id="db176-104">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db176-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="db176-105">In This Section</span></span>  
 [<span data-ttu-id="db176-106">如何：使用 ASP.NET 成员资格提供程序</span><span class="sxs-lookup"><span data-stu-id="db176-106">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="db176-107">ASP.NET 功能包括成员资格和角色提供程序、用于存储用户名/密码对以供进行身份验证的数据库，以及用于身份验证的用户角色。</span><span class="sxs-lookup"><span data-stu-id="db176-107">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="db176-108">本主题说明 WCF 服务如何使用同一个数据库对用户进行身份验证和授权。</span><span class="sxs-lookup"><span data-stu-id="db176-108">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="db176-109">如何：使用自定义用户名和密码验证程序</span><span class="sxs-lookup"><span data-stu-id="db176-109">How to: Use a Custom User Name and Password Validator</span></span>](how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="db176-110">演示如何集成自定义用户名/密码验证程序。</span><span class="sxs-lookup"><span data-stu-id="db176-110">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="db176-111">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="db176-111">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)  
 <span data-ttu-id="db176-112">作为额外的安全措施，客户端可以通过指定服务的预期*标识*来对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="db176-112">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="db176-113">如果期望的标识与服务返回的标识不匹配，则身份验证失败。</span><span class="sxs-lookup"><span data-stu-id="db176-113">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="db176-114">安全协商和超时</span><span class="sxs-lookup"><span data-stu-id="db176-114">Security Negotiation and Timeouts</span></span>](security-negotiation-and-timeouts.md)  
 <span data-ttu-id="db176-115">说明如何使用 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> 类的 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> 属性。</span><span class="sxs-lookup"><span data-stu-id="db176-115">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="db176-116">调试 Windows 身份验证错误</span><span class="sxs-lookup"><span data-stu-id="db176-116">Debugging Windows Authentication Errors</span></span>](debugging-windows-authentication-errors.md)  
 <span data-ttu-id="db176-117">重点说明使用 Windows 身份验证时所遇到的常见问题。</span><span class="sxs-lookup"><span data-stu-id="db176-117">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="db176-118">参考</span><span class="sxs-lookup"><span data-stu-id="db176-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="db176-119">相关章节</span><span class="sxs-lookup"><span data-stu-id="db176-119">Related Sections</span></span>  
 [<span data-ttu-id="db176-120">常用安全方案</span><span class="sxs-lookup"><span data-stu-id="db176-120">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="db176-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="db176-121">See also</span></span>

- [<span data-ttu-id="db176-122">安全性概述</span><span class="sxs-lookup"><span data-stu-id="db176-122">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="db176-123">[Windows Server App Fabric 的安全模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="db176-123">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
