---
title: SAML 令牌和声明
description: 了解 WFC 如何使用 SAML 令牌来携带语句，这些语句是一组与其他实体相关的声明。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
- issued tokens
- SAML token
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
ms.openlocfilehash: c054e594af69def96879852a5145675b3123614a
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244941"
---
# <a name="saml-tokens-and-claims"></a><span data-ttu-id="4f72b-103">SAML 令牌和声明</span><span class="sxs-lookup"><span data-stu-id="4f72b-103">SAML Tokens and Claims</span></span>
<span data-ttu-id="4f72b-104">安全断言标记语言（SAML）*令牌*是声明的 XML 表示形式。</span><span class="sxs-lookup"><span data-stu-id="4f72b-104">Security Assertions Markup Language (SAML) *tokens* are XML representations of claims.</span></span> <span data-ttu-id="4f72b-105">默认情况下，联合安全方案中 Windows Communication Foundation （WCF）使用的 SAML 令牌是*颁发的令牌*。</span><span class="sxs-lookup"><span data-stu-id="4f72b-105">By default, SAML tokens Windows Communication Foundation (WCF) uses in federated security scenarios are *issued tokens*.</span></span>  
  
 <span data-ttu-id="4f72b-106">SAML 令牌包含由一个实体所生成的关于另一实体的多组声明的语句。</span><span class="sxs-lookup"><span data-stu-id="4f72b-106">SAML tokens carry statements that are sets of claims made by one entity about another entity.</span></span> <span data-ttu-id="4f72b-107">例如，在联合安全方案中，语句是由安全令牌服务针对系统中的某一用户所生成的。</span><span class="sxs-lookup"><span data-stu-id="4f72b-107">For example, in federated security scenarios, the statements are made by a security token service about a user in the system.</span></span> <span data-ttu-id="4f72b-108">安全令牌服务将对 SAML 令牌进行签名，以指示令牌中所包含语句的真实性。</span><span class="sxs-lookup"><span data-stu-id="4f72b-108">The security token service signs the SAML token to indicate the veracity of the statements contained in the token.</span></span> <span data-ttu-id="4f72b-109">此外，SAML 令牌与 SAML 令牌用户确实了解的加密密钥材料关联。</span><span class="sxs-lookup"><span data-stu-id="4f72b-109">In addition, the SAML token is associated with cryptographic key material that the user of the SAML token proves knowledge of.</span></span> <span data-ttu-id="4f72b-110">这就向依赖方证明了 SAML 令牌实际上是颁发给该用户的。</span><span class="sxs-lookup"><span data-stu-id="4f72b-110">This proof satisfies the relying party that the SAML token was, in fact, issued to that user.</span></span> <span data-ttu-id="4f72b-111">例如，在典型的方案中：</span><span class="sxs-lookup"><span data-stu-id="4f72b-111">For example, in a typical scenario:</span></span>  
  
1. <span data-ttu-id="4f72b-112">客户端向安全令牌服务请求 SAML 令牌，并通过使用 Windows 证书对该安全令牌服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="4f72b-112">A client requests a SAML token from a security token service, authenticating to that security token service by using Windows credentials.</span></span>  
  
2. <span data-ttu-id="4f72b-113">安全令牌服务向客户端颁发 SAML 令牌。</span><span class="sxs-lookup"><span data-stu-id="4f72b-113">The security token service issues a SAML token to the client.</span></span> <span data-ttu-id="4f72b-114">SAML 令牌使用与安全令牌服务关联的证书进行签名，并包含针对目标服务所加密的校验密钥。</span><span class="sxs-lookup"><span data-stu-id="4f72b-114">The SAML token is signed with a certificate associated with the security token service and contains a proof key encrypted for the target service.</span></span>  
  
3. <span data-ttu-id="4f72b-115">客户端还收到*证明密钥*的副本。</span><span class="sxs-lookup"><span data-stu-id="4f72b-115">The client also receives a copy of the *proof key*.</span></span> <span data-ttu-id="4f72b-116">然后，客户端向应用程序服务（*信赖方*）呈现 SAML 令牌，并通过该校验密钥对消息进行签名。</span><span class="sxs-lookup"><span data-stu-id="4f72b-116">The client then presents the SAML token to the application service (the *relying party*) and signs the message with that proof key.</span></span>  
  
4. <span data-ttu-id="4f72b-117">依赖方可通过 SAML 令牌上的签名了解到，该令牌是由安全令牌服务颁发的；</span><span class="sxs-lookup"><span data-stu-id="4f72b-117">The signature over the SAML token tells the relying party that the security token service issued the token.</span></span> <span data-ttu-id="4f72b-118">依赖方还可通过使用校验密钥创建的消息签名了解到，该令牌是颁发给客户端的。</span><span class="sxs-lookup"><span data-stu-id="4f72b-118">The message signature created with the proof key tells the relying party that the token was issued to the client.</span></span>  
  
## <a name="from-claims-to-samlattributes"></a><span data-ttu-id="4f72b-119">从 Claim 到 SamlAttribute</span><span class="sxs-lookup"><span data-stu-id="4f72b-119">From Claims to SamlAttributes</span></span>  
 <span data-ttu-id="4f72b-120">在 WCF 中，SAML 令牌中的语句作为对象进行建模，前提是对象 <xref:System.IdentityModel.Tokens.SamlAttribute> <xref:System.IdentityModel.Claims.Claim> <xref:System.IdentityModel.Claims.Claim> 具有 <xref:System.IdentityModel.Claims.Claim.Right%2A> 属性 <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> 且 <xref:System.IdentityModel.Claims.Claim.Resource%2A> 属性的类型为 <xref:System.String> 。</span><span class="sxs-lookup"><span data-stu-id="4f72b-120">In WCF, statements in SAML tokens are modeled as <xref:System.IdentityModel.Tokens.SamlAttribute> objects, which can be populated directly from <xref:System.IdentityModel.Claims.Claim> objects, provided the <xref:System.IdentityModel.Claims.Claim> object has a <xref:System.IdentityModel.Claims.Claim.Right%2A> property of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> and the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property is of type <xref:System.String>.</span></span> <span data-ttu-id="4f72b-121">例如：</span><span class="sxs-lookup"><span data-stu-id="4f72b-121">For example:</span></span>  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
> <span data-ttu-id="4f72b-122">如果 SAML 令牌在消息中序列化，无论是在安全令牌服务颁发这些令牌时，还是在客户端将其作为身份验证的一部分提交到服务中时，最大消息大小配额都必须足够大，以便能够容纳 SAML 令牌和其他消息部分。</span><span class="sxs-lookup"><span data-stu-id="4f72b-122">When SAML tokens are serialized in messages, either when they are issued by a security token service or when they are presented by clients to services as part of authentication, the maximum message size quota must be sufficiently large to accommodate the SAML token and the other message parts.</span></span> <span data-ttu-id="4f72b-123">正常情况下，默认消息大小配额足够使用。</span><span class="sxs-lookup"><span data-stu-id="4f72b-123">In normal cases, the default message size quotas are sufficient.</span></span> <span data-ttu-id="4f72b-124">但是，如果 SAML 令牌由于包含数以百计的声明而过于庞大，您可能需要提高配额，以便容纳序列化的令牌。</span><span class="sxs-lookup"><span data-stu-id="4f72b-124">However, in cases where a SAML token is large because it contains hundreds of claims, you may need to increase the quotas to accommodate the serialized token.</span></span> <span data-ttu-id="4f72b-125">有关详细信息，请参阅[数据的安全注意事项](security-considerations-for-data.md)。</span><span class="sxs-lookup"><span data-stu-id="4f72b-125">For more information, see [Security Considerations for Data](security-considerations-for-data.md).</span></span>  
  
## <a name="from-samlattributes-to-claims"></a><span data-ttu-id="4f72b-126">从 SamlAttribute 到 Claim</span><span class="sxs-lookup"><span data-stu-id="4f72b-126">From SamlAttributes to Claims</span></span>  
 <span data-ttu-id="4f72b-127">在消息中接收到 SAML 令牌时，SAML 令牌中的各种语句将转换为 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 对象，并放置在 <xref:System.IdentityModel.Policy.AuthorizationContext> 中。</span><span class="sxs-lookup"><span data-stu-id="4f72b-127">When SAML tokens are received in messages, the various statements in the SAML token are turned into <xref:System.IdentityModel.Policy.IAuthorizationPolicy> objects that are placed into the <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="4f72b-128">来自每个 SAML 语句的声明将由 <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> 的 <xref:System.IdentityModel.Policy.AuthorizationContext> 属性返回，并可对这些声明进行检查，以确定是否对该用户进行身份验证和授权。</span><span class="sxs-lookup"><span data-stu-id="4f72b-128">The claims from each SAML statement are returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> and can be examined to determine whether to authenticate and authorize the user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f72b-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="4f72b-129">See also</span></span>

- <xref:System.IdentityModel.Policy.AuthorizationContext>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [<span data-ttu-id="4f72b-130">联合</span><span class="sxs-lookup"><span data-stu-id="4f72b-130">Federation</span></span>](federation.md)
- [<span data-ttu-id="4f72b-131">如何：创建联合客户端</span><span class="sxs-lookup"><span data-stu-id="4f72b-131">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)
- [<span data-ttu-id="4f72b-132">如何：在联合身份验证服务上配置凭据</span><span class="sxs-lookup"><span data-stu-id="4f72b-132">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="4f72b-133">使用标识模型管理声明和授权</span><span class="sxs-lookup"><span data-stu-id="4f72b-133">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="4f72b-134">声明和令牌</span><span class="sxs-lookup"><span data-stu-id="4f72b-134">Claims and Tokens</span></span>](claims-and-tokens.md)
- [<span data-ttu-id="4f72b-135">声明创建和资源值</span><span class="sxs-lookup"><span data-stu-id="4f72b-135">Claim Creation and Resource Values</span></span>](claim-creation-and-resource-values.md)
- [<span data-ttu-id="4f72b-136">如何：创建自定义声明</span><span class="sxs-lookup"><span data-stu-id="4f72b-136">How to: Create a Custom Claim</span></span>](../extending/how-to-create-a-custom-claim.md)
