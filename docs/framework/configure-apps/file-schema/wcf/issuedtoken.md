---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 56439748926ada642018f48a5787634a50d0f180
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "72846861"
---
# \<issuedToken>
<span data-ttu-id="c90a1-101">指定用于向服务验证客户端身份的自定义令牌。</span><span class="sxs-lookup"><span data-stu-id="c90a1-101">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**  
  
## <a name="syntax"></a><span data-ttu-id="c90a1-102">语法</span><span class="sxs-lookup"><span data-stu-id="c90a1-102">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c90a1-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c90a1-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c90a1-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c90a1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c90a1-105">特性</span><span class="sxs-lookup"><span data-stu-id="c90a1-105">Attributes</span></span>  
  
|<span data-ttu-id="c90a1-106">属性</span><span class="sxs-lookup"><span data-stu-id="c90a1-106">Attribute</span></span>|<span data-ttu-id="c90a1-107">说明</span><span class="sxs-lookup"><span data-stu-id="c90a1-107">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="c90a1-108">可选的布尔值属性，指定是否对令牌进行缓存。</span><span class="sxs-lookup"><span data-stu-id="c90a1-108">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="c90a1-109">默认为 `true`。</span><span class="sxs-lookup"><span data-stu-id="c90a1-109">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="c90a1-110">可选的字符串属性，指定用于握手操作的随机值（熵）。</span><span class="sxs-lookup"><span data-stu-id="c90a1-110">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="c90a1-111">这些值包括 `ClientEntropy`、`ServerEntropy` 和 `CombinedEntropy`，默认值为 `CombinedEntropy`。</span><span class="sxs-lookup"><span data-stu-id="c90a1-111">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="c90a1-112">此属性的类型为 <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>。</span><span class="sxs-lookup"><span data-stu-id="c90a1-112">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="c90a1-113">可选的整数属性，指定在续订令牌之前可经过的有效时间段（由令牌颁发者提供）的百分比。</span><span class="sxs-lookup"><span data-stu-id="c90a1-113">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="c90a1-114">值的范围是 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="c90a1-114">Values are from 0 to 100.</span></span> <span data-ttu-id="c90a1-115">默认值为 60，指定尝试续订之前经过了 60% 的时间。</span><span class="sxs-lookup"><span data-stu-id="c90a1-115">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="c90a1-116">可选属性，指定当与颁发者进行通信时所使用的通道行为。</span><span class="sxs-lookup"><span data-stu-id="c90a1-116">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="c90a1-117">可选属性，指定当与本地颁发者进行通信时所使用的通道行为。</span><span class="sxs-lookup"><span data-stu-id="c90a1-117">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="c90a1-118">可选的 Timespan 属性，指定当令牌颁发者 (STS) 未指定时间时，对颁发的令牌进行缓存的持续时间。</span><span class="sxs-lookup"><span data-stu-id="c90a1-118">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="c90a1-119">默认值为 "10675199.02：48： 05.4775807"。</span><span class="sxs-lookup"><span data-stu-id="c90a1-119">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c90a1-120">子元素</span><span class="sxs-lookup"><span data-stu-id="c90a1-120">Child Elements</span></span>  
  
|<span data-ttu-id="c90a1-121">元素</span><span class="sxs-lookup"><span data-stu-id="c90a1-121">Element</span></span>|<span data-ttu-id="c90a1-122">描述</span><span class="sxs-lookup"><span data-stu-id="c90a1-122">Description</span></span>|  
|-------------|-----------------|  
|[\<localIssuer>](localissuer.md)|<span data-ttu-id="c90a1-123">指定令牌的本地颁发者地址以及用于与终结点进行通信的绑定。</span><span class="sxs-lookup"><span data-stu-id="c90a1-123">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="c90a1-124">指定当联系本地颁发者时所使用的终结点行为。</span><span class="sxs-lookup"><span data-stu-id="c90a1-124">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c90a1-125">父元素</span><span class="sxs-lookup"><span data-stu-id="c90a1-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c90a1-126">元素</span><span class="sxs-lookup"><span data-stu-id="c90a1-126">Element</span></span>|<span data-ttu-id="c90a1-127">描述</span><span class="sxs-lookup"><span data-stu-id="c90a1-127">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="c90a1-128">指定用于向服务验证客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="c90a1-128">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c90a1-129">注解</span><span class="sxs-lookup"><span data-stu-id="c90a1-129">Remarks</span></span>  
 <span data-ttu-id="c90a1-130">例如，颁发的令牌是在使用联合方案中的安全令牌服务 (STS) 进行身份验证时所使用的自定义凭据类型。</span><span class="sxs-lookup"><span data-stu-id="c90a1-130">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="c90a1-131">默认情况下，该令牌为 SAML 令牌。</span><span class="sxs-lookup"><span data-stu-id="c90a1-131">By default, the token is a SAML token.</span></span> <span data-ttu-id="c90a1-132">有关详细信息，请参阅[联合和颁发的令牌](../../../wcf/feature-details/federation-and-issued-tokens.md)以及[联合和颁发的令牌](../../../wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="c90a1-132">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md), and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="c90a1-133">本节包含用于配置本地令牌颁发者的元素，或者与安全令牌服务一起使用的行为。</span><span class="sxs-lookup"><span data-stu-id="c90a1-133">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="c90a1-134">有关将客户端配置为使用本地颁发者的说明，请参阅[如何：配置本地颁发者](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)。</span><span class="sxs-lookup"><span data-stu-id="c90a1-134">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c90a1-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c90a1-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="c90a1-136">安全行为</span><span class="sxs-lookup"><span data-stu-id="c90a1-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="c90a1-137">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="c90a1-137">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c90a1-138">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="c90a1-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c90a1-139">保证客户端的安全</span><span class="sxs-lookup"><span data-stu-id="c90a1-139">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="c90a1-140">如何：创建联合客户端</span><span class="sxs-lookup"><span data-stu-id="c90a1-140">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="c90a1-141">如何：配置本地颁发者</span><span class="sxs-lookup"><span data-stu-id="c90a1-141">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="c90a1-142">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="c90a1-142">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
