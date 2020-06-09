---
title: 如何：创建安全令牌服务
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 98e82101-4cff-4bb8-a220-f7abed3556e5
ms.openlocfilehash: 1cfcca524e5dd2b0c1560eb7600795766e2db1d6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598952"
---
# <a name="how-to-create-a-security-token-service"></a><span data-ttu-id="61c67-102">如何：创建安全令牌服务</span><span class="sxs-lookup"><span data-stu-id="61c67-102">How to: Create a Security Token Service</span></span>
<span data-ttu-id="61c67-103">安全令牌服务实现在 WS-Trust 规范中定义的协议。</span><span class="sxs-lookup"><span data-stu-id="61c67-103">A security token service implements the protocol defined in the WS-Trust specification.</span></span> <span data-ttu-id="61c67-104">此协议为颁发、续订、取消和验证安全令牌定义消息格式和消息交换模式。</span><span class="sxs-lookup"><span data-stu-id="61c67-104">This protocol defines message formats and message exchange patterns for issuing, renewing, canceling, and validating security tokens.</span></span> <span data-ttu-id="61c67-105">给定的安全令牌服务提供这些功能中的一个或多个功能。</span><span class="sxs-lookup"><span data-stu-id="61c67-105">A given security token service provides one or more of these capabilities.</span></span> <span data-ttu-id="61c67-106">本主题考虑最常见的情况：实现令牌颁发。</span><span class="sxs-lookup"><span data-stu-id="61c67-106">This topic looks at the most common scenario: implementing token issuance.</span></span>  
  
## <a name="issuing-tokens"></a><span data-ttu-id="61c67-107">颁发令牌</span><span class="sxs-lookup"><span data-stu-id="61c67-107">Issuing Tokens</span></span>  
 <span data-ttu-id="61c67-108">WS-Trust 基于 `RequestSecurityToken` XML 架构定义语言 (XSD) 架构元素和用于执行令牌颁发的 `RequestSecurityTokenResponse` XSD 架构元素来定义消息格式。</span><span class="sxs-lookup"><span data-stu-id="61c67-108">WS-Trust defines message formats, based on the `RequestSecurityToken` XML Schema definition language (XSD) schema element, and `RequestSecurityTokenResponse` XSD schema element for performing token issuance.</span></span> <span data-ttu-id="61c67-109">此外，它还定义关联的操作统一资源标识符 (URI)。</span><span class="sxs-lookup"><span data-stu-id="61c67-109">In addition, it defines the associated Action Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="61c67-110">与消息关联的操作 URI `RequestSecurityToken` 是 `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue` 。</span><span class="sxs-lookup"><span data-stu-id="61c67-110">The action URI associated with the `RequestSecurityToken` message is `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`.</span></span> <span data-ttu-id="61c67-111">与消息关联的操作 URI `RequestSecurityTokenResponse` 是 `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue` 。</span><span class="sxs-lookup"><span data-stu-id="61c67-111">The action URI associated with the `RequestSecurityTokenResponse` message is   `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`.</span></span>  
  
### <a name="request-message-structure"></a><span data-ttu-id="61c67-112">请求消息结构</span><span class="sxs-lookup"><span data-stu-id="61c67-112">Request Message Structure</span></span>  
 <span data-ttu-id="61c67-113">颁发请求消息结构通常包括以下项：</span><span class="sxs-lookup"><span data-stu-id="61c67-113">The issue request message structure typically consists of the following items:</span></span>  
  
- <span data-ttu-id="61c67-114">一个请求类型 URI，其值为 `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue` 。</span><span class="sxs-lookup"><span data-stu-id="61c67-114">A request type URI with a value of `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue`.</span></span>
  
- <span data-ttu-id="61c67-115">令牌类型 URI。</span><span class="sxs-lookup"><span data-stu-id="61c67-115">A token type URI.</span></span> <span data-ttu-id="61c67-116">对于安全断言标记语言（SAML）1.1 令牌，此 URI 的值为 `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` 。</span><span class="sxs-lookup"><span data-stu-id="61c67-116">For Security Assertions Markup Language (SAML) 1.1 tokens, the value of this URI is `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.</span></span>  
  
- <span data-ttu-id="61c67-117">密钥大小值，指示与颁发的令牌关联的密钥中的位数。</span><span class="sxs-lookup"><span data-stu-id="61c67-117">A key size value that indicates the number of bits in the key to be associated with the issued token.</span></span>  
  
- <span data-ttu-id="61c67-118">密钥类型 URI。</span><span class="sxs-lookup"><span data-stu-id="61c67-118">A key type URI.</span></span> <span data-ttu-id="61c67-119">对于对称密钥，此 URI 的值为 `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey` 。</span><span class="sxs-lookup"><span data-stu-id="61c67-119">For symmetric keys, the value of this URI is `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey`.</span></span>  
  
 <span data-ttu-id="61c67-120">此外，可能会显示几个其他项：</span><span class="sxs-lookup"><span data-stu-id="61c67-120">In addition, a couple of other items might be present:</span></span>  
  
- <span data-ttu-id="61c67-121">由客户端提供的密钥材料。</span><span class="sxs-lookup"><span data-stu-id="61c67-121">Key material provided by the client.</span></span>  
  
- <span data-ttu-id="61c67-122">用来指示颁发的令牌将用于的目标服务的范围信息。</span><span class="sxs-lookup"><span data-stu-id="61c67-122">Scope information that indicates the target service that the issued token will be used with.</span></span>  
  
 <span data-ttu-id="61c67-123">安全令牌服务在构造颁发响应消息时使用颁发请求消息中的信息。</span><span class="sxs-lookup"><span data-stu-id="61c67-123">The security token service uses the information in the issue request message when it constructs the Issue Response message.</span></span>  
  
## <a name="response-message-structure"></a><span data-ttu-id="61c67-124">响应消息结构</span><span class="sxs-lookup"><span data-stu-id="61c67-124">Response Message Structure</span></span>  
 <span data-ttu-id="61c67-125">颁发响应消息结构通常包括以下项；</span><span class="sxs-lookup"><span data-stu-id="61c67-125">The issue response message structure typically consists of the following items;</span></span>  
  
- <span data-ttu-id="61c67-126">颁发的安全令牌，例如，一个 SAML 1.1 断言。</span><span class="sxs-lookup"><span data-stu-id="61c67-126">The issued security token, for example, a SAML 1.1 assertion.</span></span>  
  
- <span data-ttu-id="61c67-127">与安全令牌相关联的证明令牌。</span><span class="sxs-lookup"><span data-stu-id="61c67-127">A proof token associated with the security token.</span></span> <span data-ttu-id="61c67-128">对于对称密钥，这通常是密钥材料的加密形式。</span><span class="sxs-lookup"><span data-stu-id="61c67-128">For symmetric keys, this is often an encrypted form of the key material.</span></span>  
  
- <span data-ttu-id="61c67-129">对颁发的安全令牌的引用。</span><span class="sxs-lookup"><span data-stu-id="61c67-129">References to the issued security token.</span></span> <span data-ttu-id="61c67-130">通常，安全令牌服务返回两个引用：一个可以在颁发的令牌显示在随后由客户端发送的消息中时使用，另一个可以在颁发的令牌没有显示在随后的消息中时使用。</span><span class="sxs-lookup"><span data-stu-id="61c67-130">Typically, the security token service returns a reference that can be used when the issued token appears in a subsequent message sent by the client and another that can be used when the token is not present in subsequent messages.</span></span>  
  
 <span data-ttu-id="61c67-131">此外，可能会显示几个其他项：</span><span class="sxs-lookup"><span data-stu-id="61c67-131">In addition, a couple of other items might be present:</span></span>  
  
- <span data-ttu-id="61c67-132">由安全令牌服务提供的密钥材料。</span><span class="sxs-lookup"><span data-stu-id="61c67-132">Key material provided by the security token service.</span></span>  
  
- <span data-ttu-id="61c67-133">计算共享密钥所需的算法。</span><span class="sxs-lookup"><span data-stu-id="61c67-133">The algorithm needed to compute the shared key.</span></span>  
  
- <span data-ttu-id="61c67-134">颁发的令牌的生存期信息。</span><span class="sxs-lookup"><span data-stu-id="61c67-134">Lifetime information for the issued token.</span></span>  
  
## <a name="processing-request-messages"></a><span data-ttu-id="61c67-135">处理请求消息</span><span class="sxs-lookup"><span data-stu-id="61c67-135">Processing Request Messages</span></span>  
 <span data-ttu-id="61c67-136">安全令牌服务通过检查各个请求消息并确保它可以颁发满足此请求的令牌来处理颁发请求。</span><span class="sxs-lookup"><span data-stu-id="61c67-136">The security token service processes the issue request by examining the various pieces of the request message and ensuring that it can issue a token that satisfies the request.</span></span> <span data-ttu-id="61c67-137">安全令牌服务必须先确定以下各项，然后才能构造要颁发的令牌：</span><span class="sxs-lookup"><span data-stu-id="61c67-137">The security token service must determine the following before it constructs the token to be issued:</span></span>  
  
- <span data-ttu-id="61c67-138">该请求实际上是一个对要颁发的令牌的请求。</span><span class="sxs-lookup"><span data-stu-id="61c67-138">The request really is a request for a token to be issued.</span></span>  
  
- <span data-ttu-id="61c67-139">安全令牌服务支持请求的令牌类型。</span><span class="sxs-lookup"><span data-stu-id="61c67-139">The security token service supports the requested token type.</span></span>  
  
- <span data-ttu-id="61c67-140">已授权请求方创建请求。</span><span class="sxs-lookup"><span data-stu-id="61c67-140">The requester is authorized to make the request.</span></span>  
  
- <span data-ttu-id="61c67-141">安全令牌服务可以满足请求方对密钥材料的预期。</span><span class="sxs-lookup"><span data-stu-id="61c67-141">The security token service can meet the requester's expectations with respect to key material.</span></span>  
  
 <span data-ttu-id="61c67-142">构造令牌的两个重要部分是确定对该令牌进行签名时使用的密钥和对共享密钥加密时使用的密钥。</span><span class="sxs-lookup"><span data-stu-id="61c67-142">Two vital parts of constructing a token are determining what key to sign the token with and what key to encrypt the shared key with.</span></span> <span data-ttu-id="61c67-143">需要对该令牌进行签名，以便当客户端将该令牌显示在目标服务中时，该服务可以确定由它信任的安全令牌服务来颁发该令牌。</span><span class="sxs-lookup"><span data-stu-id="61c67-143">The token needs to be signed so that when the client presents the token to the target service, that service can determine that the token was issued by a security token service that it trusts.</span></span> <span data-ttu-id="61c67-144">需要以目标服务对密钥材料解密的方式来对密钥材料加密。</span><span class="sxs-lookup"><span data-stu-id="61c67-144">The key material needs to be encrypted in such a way that the target service can decrypt that key material.</span></span>  
  
 <span data-ttu-id="61c67-145">对一个涉及创建 <xref:System.IdentityModel.Tokens.SigningCredentials> 实例的 SAML 断言进行签名。</span><span class="sxs-lookup"><span data-stu-id="61c67-145">Signing a SAML assertion involves creating a <xref:System.IdentityModel.Tokens.SigningCredentials> instance.</span></span> <span data-ttu-id="61c67-146">此类的构造函数具有以下各项：</span><span class="sxs-lookup"><span data-stu-id="61c67-146">The constructor for this class takes the following:</span></span>  
  
- <span data-ttu-id="61c67-147">密钥的 <xref:System.IdentityModel.Tokens.SecurityKey>，用于对 SAML 断言进行签名。</span><span class="sxs-lookup"><span data-stu-id="61c67-147">A <xref:System.IdentityModel.Tokens.SecurityKey> for the key to use to sign the SAML assertion.</span></span>  
  
- <span data-ttu-id="61c67-148">用于标识要使用的签名算法的字符串。</span><span class="sxs-lookup"><span data-stu-id="61c67-148">A string identifying the signature algorithm to use.</span></span>  
  
- <span data-ttu-id="61c67-149">用于标识要使用的摘要算法的字符串。</span><span class="sxs-lookup"><span data-stu-id="61c67-149">A string identifying the digest algorithm to use.</span></span>  
  
- <span data-ttu-id="61c67-150">或者，用于标识要用来对断言进行签名的密钥的 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>。</span><span class="sxs-lookup"><span data-stu-id="61c67-150">Optionally, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> that identifies the key to use to sign the assertion.</span></span>  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 <span data-ttu-id="61c67-151">对共享密钥加密涉及两个操作：首先获得该密钥材料，然后使用目标服务用来对该共享密钥解密的密钥对该共享密钥进行加密。</span><span class="sxs-lookup"><span data-stu-id="61c67-151">Encrypting the shared key involves taking the key material and encrypting it with a key that the target service can use to decrypt the shared key.</span></span> <span data-ttu-id="61c67-152">通常使用该目标服务的公钥。</span><span class="sxs-lookup"><span data-stu-id="61c67-152">Typically, the public key of the target service is used.</span></span>  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 <span data-ttu-id="61c67-153">此外，需要加密密钥的 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>。</span><span class="sxs-lookup"><span data-stu-id="61c67-153">In addition, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> for the encrypted key is needed.</span></span>  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 <span data-ttu-id="61c67-154">然后此 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> 用于创建一个作为 `SamlSubject` 一部分的 `SamlToken`。</span><span class="sxs-lookup"><span data-stu-id="61c67-154">This <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> is then used to create a `SamlSubject` as part of the `SamlToken`.</span></span>  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 <span data-ttu-id="61c67-155">有关详细信息，请参阅[联合示例](../samples/federation-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="61c67-155">For more information, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
## <a name="creating-response-messages"></a><span data-ttu-id="61c67-156">创建响应消息</span><span class="sxs-lookup"><span data-stu-id="61c67-156">Creating Response Messages</span></span>  
 <span data-ttu-id="61c67-157">一旦安全令牌服务处理颁发请求并构造要随校验密钥一起颁发的令牌，就需要构造响应消息，其中至少包括请求的令牌、证明令牌和颁发的令牌引用。</span><span class="sxs-lookup"><span data-stu-id="61c67-157">Once the security token service processes the issue request and constructs the token to be issued along with the proof key, the response message needs to be constructed, including at least the requested token, the proof token, and the issued token references.</span></span> <span data-ttu-id="61c67-158">此颁发的令牌通常是从 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 中创建的 <xref:System.IdentityModel.Tokens.SamlAssertion>，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="61c67-158">The issued token is typically a <xref:System.IdentityModel.Tokens.SamlSecurityToken> created from the <xref:System.IdentityModel.Tokens.SamlAssertion>, as shown in the following example.</span></span>  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 <span data-ttu-id="61c67-159">如果安全令牌服务提供共享密钥材料，则通过创建一个 <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken> 来构造证明令牌。</span><span class="sxs-lookup"><span data-stu-id="61c67-159">In the case where the security token service provides the shared key material, the proof token is constructed by creating a <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span></span>  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 <span data-ttu-id="61c67-160">有关当客户端和 security token service 都为共享密钥提供密钥材料时如何构造证明令牌的详细信息，请参阅[联合示例](../samples/federation-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="61c67-160">For more information about how to construct the proof token when the client and the security token service both provide key material for the shared key, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
 <span data-ttu-id="61c67-161">通过创建 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> 类的实例来构造颁发的令牌的引用。</span><span class="sxs-lookup"><span data-stu-id="61c67-161">The issued token references are constructed by creating instances of the <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> class.</span></span>  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 <span data-ttu-id="61c67-162">然后这些不同的值序列化到返回客户端的响应消息中。</span><span class="sxs-lookup"><span data-stu-id="61c67-162">These various values are then serialized into the response message returned to the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61c67-163">示例</span><span class="sxs-lookup"><span data-stu-id="61c67-163">Example</span></span>  
 <span data-ttu-id="61c67-164">有关 security token service 的完整代码，请参阅[联合示例](../samples/federation-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="61c67-164">For full code for a security token service, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61c67-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="61c67-165">See also</span></span>

- <xref:System.IdentityModel.Tokens.SigningCredentials>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>
- <xref:System.IdentityModel.Tokens.SamlSecurityToken>
- <xref:System.IdentityModel.Tokens.SamlAssertion>
- <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>
- [<span data-ttu-id="61c67-166">联合示例</span><span class="sxs-lookup"><span data-stu-id="61c67-166">Federation Sample</span></span>](../samples/federation-sample.md)
