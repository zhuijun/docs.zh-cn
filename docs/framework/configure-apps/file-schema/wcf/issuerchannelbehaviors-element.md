---
title: <issuerChannelBehaviors> 元素
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
no-loc:
- <system.serviceModel>
- <behaviors>
- <endpointBehaviors>
- <behavior>
- <clientCredentials>
- <issuedToken>
- <issuerChannelBehaviors>
- <dataContractSerializer>
ms.openlocfilehash: cbbfb9d3b5af47a360aa82cf837cd6749f61b641
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70893156"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="78945-102">\<issuerChannelBehaviors> 元素</span><span class="sxs-lookup"><span data-stu-id="78945-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="78945-103">包含与指定的服务令牌服务通信时要使用的 Windows Communication Foundation （WCF）客户端终结点行为（在配置中定义）的集合。</span><span class="sxs-lookup"><span data-stu-id="78945-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="78945-104">定义的行为不能包含任何 [\<clientCredentials>](clientcredentials.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="78945-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<system.serviceModel>](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<behaviors>](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors>](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<behavior>](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials>](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken>](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors>

## <a name="syntax"></a><span data-ttu-id="78945-105">语法</span><span class="sxs-lookup"><span data-stu-id="78945-105">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="78945-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="78945-106">Attributes and elements</span></span>

<span data-ttu-id="78945-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="78945-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="78945-108">特性</span><span class="sxs-lookup"><span data-stu-id="78945-108">Attributes</span></span>

<span data-ttu-id="78945-109">无。</span><span class="sxs-lookup"><span data-stu-id="78945-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="78945-110">子元素</span><span class="sxs-lookup"><span data-stu-id="78945-110">Child elements</span></span>

|<span data-ttu-id="78945-111">元素</span><span class="sxs-lookup"><span data-stu-id="78945-111">Element</span></span>|<span data-ttu-id="78945-112">说明</span><span class="sxs-lookup"><span data-stu-id="78945-112">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="78945-113">向集合中添加行为。</span><span class="sxs-lookup"><span data-stu-id="78945-113">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="78945-114">父元素</span><span class="sxs-lookup"><span data-stu-id="78945-114">Parent elements</span></span>

|<span data-ttu-id="78945-115">元素</span><span class="sxs-lookup"><span data-stu-id="78945-115">Element</span></span>|<span data-ttu-id="78945-116">说明</span><span class="sxs-lookup"><span data-stu-id="78945-116">Description</span></span>|
|-------------|-----------------|
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="78945-117">指定用于向服务验证客户端身份的自定义令牌。</span><span class="sxs-lookup"><span data-stu-id="78945-117">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="78945-118">注解</span><span class="sxs-lookup"><span data-stu-id="78945-118">Remarks</span></span>

<span data-ttu-id="78945-119">当必须使用任何行为（包含 `<clientCredentials>` 元素的行为除外）与某个服务进行通信时，应使用此元素。</span><span class="sxs-lookup"><span data-stu-id="78945-119">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="78945-120">例如，如果 [\<dataContractSerializer>](datacontractserializer-element.md) 必须包括一个行为元素。</span><span class="sxs-lookup"><span data-stu-id="78945-120">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="78945-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="78945-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="78945-122">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="78945-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="78945-123">安全行为</span><span class="sxs-lookup"><span data-stu-id="78945-123">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="78945-124">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="78945-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="78945-125">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="78945-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="78945-126">保证客户端的安全</span><span class="sxs-lookup"><span data-stu-id="78945-126">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="78945-127">如何：创建联合客户端</span><span class="sxs-lookup"><span data-stu-id="78945-127">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="78945-128">如何：配置本地颁发者</span><span class="sxs-lookup"><span data-stu-id="78945-128">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="78945-129">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="78945-129">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
