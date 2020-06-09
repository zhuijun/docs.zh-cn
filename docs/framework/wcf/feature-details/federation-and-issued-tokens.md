---
title: 联合令牌与颁发的令牌
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: aeffc1e2a7b61dfd9406b9f06678064533ea61ec
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595500"
---
# <a name="federation-and-issued-tokens"></a><span data-ttu-id="ed6d8-102">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="ed6d8-102">Federation and Issued Tokens</span></span>
<span data-ttu-id="ed6d8-103">通过 Windows Communication Foundation （WCF），可以创建与实现 WS 联合身份验证和 WS-TRUST 规范的服务安全通信的客户端。</span><span class="sxs-lookup"><span data-stu-id="ed6d8-103">With Windows Communication Foundation (WCF), you can create clients that communicate securely with services that implement the WS-Federation and WS-Trust specifications.</span></span> <span data-ttu-id="ed6d8-104">这些规范使用 XML、SOAP 和 Web 服务描述语言 (WSDL) 来提供用来跨不同的信任领域进行身份验证和授权的机制。</span><span class="sxs-lookup"><span data-stu-id="ed6d8-104">The specifications use XML, SOAP, and Web Services Description Language (WSDL) to provide mechanisms that enable authentication and authorization across different trust realms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ed6d8-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="ed6d8-105">In This Section</span></span>  
 [<span data-ttu-id="ed6d8-106">联合</span><span class="sxs-lookup"><span data-stu-id="ed6d8-106">Federation</span></span>](federation.md)  
 <span data-ttu-id="ed6d8-107">提供对联合的概述。</span><span class="sxs-lookup"><span data-stu-id="ed6d8-107">Provides an overview of federation.</span></span>  
  
 [<span data-ttu-id="ed6d8-108">联合与信任</span><span class="sxs-lookup"><span data-stu-id="ed6d8-108">Federation and Trust</span></span>](federation-and-trust.md)  
 <span data-ttu-id="ed6d8-109">列出在创建联合服务或客户端时应注意的设计问题。</span><span class="sxs-lookup"><span data-stu-id="ed6d8-109">Lists the design issues to be aware of when creating federated services or clients.</span></span>  
  
 [<span data-ttu-id="ed6d8-110">如何：创建联合客户端</span><span class="sxs-lookup"><span data-stu-id="ed6d8-110">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)  
 <span data-ttu-id="ed6d8-111">介绍使用 WCF 创建联合客户端的基础知识。</span><span class="sxs-lookup"><span data-stu-id="ed6d8-111">Describes the basics of creating a federated client with WCF.</span></span>  
  
 [<span data-ttu-id="ed6d8-112">如何：在联合身份验证服务上配置凭据</span><span class="sxs-lookup"><span data-stu-id="ed6d8-112">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)  
 <span data-ttu-id="ed6d8-113">描述创建联合服务的步骤。</span><span class="sxs-lookup"><span data-stu-id="ed6d8-113">Describes the steps of creating a federated service.</span></span>  
  
 [<span data-ttu-id="ed6d8-114">如何：创建 WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="ed6d8-114">How to: Create a WSFederationHttpBinding</span></span>](how-to-create-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="ed6d8-115">描述如何配置使用 `WSFederationHttpBinding` 的客户端和服务。</span><span class="sxs-lookup"><span data-stu-id="ed6d8-115">Describes how to configure clients and services that use the `WSFederationHttpBinding`.</span></span>  
  
 [<span data-ttu-id="ed6d8-116">如何：创建安全令牌服务</span><span class="sxs-lookup"><span data-stu-id="ed6d8-116">How to: Create a Security Token Service</span></span>](how-to-create-a-security-token-service.md)  
 <span data-ttu-id="ed6d8-117">描述创建安全令牌服务的步骤。</span><span class="sxs-lookup"><span data-stu-id="ed6d8-117">Describes the steps of creating a security token service.</span></span>  
  
 [<span data-ttu-id="ed6d8-118">安全断言标记语言 (SAML) 令牌和声明</span><span class="sxs-lookup"><span data-stu-id="ed6d8-118">Security Assertions Markup Language (SAML) Tokens and Claims</span></span>](saml-tokens-and-claims.md)  
 <span data-ttu-id="ed6d8-119">描述可扩展并能够用来创建丰富的声明类型的安全断言标记语言 (SAML) 令牌。</span><span class="sxs-lookup"><span data-stu-id="ed6d8-119">Describes Security Assertions Markup Language (SAML) tokens, which are extensible and enable you to create rich claim types.</span></span>  
  
 [<span data-ttu-id="ed6d8-120">如何：配置本地颁发者</span><span class="sxs-lookup"><span data-stu-id="ed6d8-120">How to: Configure a Local Issuer</span></span>](how-to-configure-a-local-issuer.md)  
 <span data-ttu-id="ed6d8-121">描述如何创建安全令牌的本地颁发机构。</span><span class="sxs-lookup"><span data-stu-id="ed6d8-121">Describes how to create a local issuer of security tokens.</span></span>  
  
 [<span data-ttu-id="ed6d8-122">如何：在 WSFederationHttpBinding 上禁用安全会话</span><span class="sxs-lookup"><span data-stu-id="ed6d8-122">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="ed6d8-123">描述如何在 `WSFederationHttpBinding` 上禁用安全会话。</span><span class="sxs-lookup"><span data-stu-id="ed6d8-123">Describes how to disable secure sessions on a `WSFederationHttpBinding`.</span></span> <span data-ttu-id="ed6d8-124">在创建要求每个客户端都有一个会话的网络场时，有必要禁用安全会话。</span><span class="sxs-lookup"><span data-stu-id="ed6d8-124">Disabling secure sessions is necessary when creating a Web farm that requires a session for each client.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ed6d8-125">参考</span><span class="sxs-lookup"><span data-stu-id="ed6d8-125">Reference</span></span>  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a><span data-ttu-id="ed6d8-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="ed6d8-126">See also</span></span>

- [<span data-ttu-id="ed6d8-127">授权</span><span class="sxs-lookup"><span data-stu-id="ed6d8-127">Authorization</span></span>](authorization-in-wcf.md)
- [<span data-ttu-id="ed6d8-128">自定义令牌</span><span class="sxs-lookup"><span data-stu-id="ed6d8-128">Custom Tokens</span></span>](../extending/custom-tokens.md)
- <span data-ttu-id="ed6d8-129">[Windows Server App Fabric 的安全模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ed6d8-129">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
