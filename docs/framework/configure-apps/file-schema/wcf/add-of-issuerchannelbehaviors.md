---
title: <add> 的 <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: cf7ac2691ad1c641352a8047373ced538b19e983
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398334"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="2222a-102">\<add> 的 \<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="2222a-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="2222a-103">添加在与 STS 进行通信时要使用的终结点行为。</span><span class="sxs-lookup"><span data-stu-id="2222a-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="2222a-104">如果任何终结点行为包含 [\<clientCredentials>](clientcredentials.md) 元素，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="2222a-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerChannelBehaviors>**](issuerchannelbehaviors-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="2222a-105">语法</span><span class="sxs-lookup"><span data-stu-id="2222a-105">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2222a-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="2222a-106">Attributes and Elements</span></span>

<span data-ttu-id="2222a-107">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2222a-107">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="2222a-108">特性</span><span class="sxs-lookup"><span data-stu-id="2222a-108">Attributes</span></span>

|<span data-ttu-id="2222a-109">属性</span><span class="sxs-lookup"><span data-stu-id="2222a-109">Attribute</span></span>|<span data-ttu-id="2222a-110">说明</span><span class="sxs-lookup"><span data-stu-id="2222a-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="2222a-111">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="2222a-111">issuerAddress</span></span>|<span data-ttu-id="2222a-112">要与之通信的安全令牌颁发者的 URI。</span><span class="sxs-lookup"><span data-stu-id="2222a-112">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="2222a-113">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="2222a-113">behaviorConfiguration</span></span>|<span data-ttu-id="2222a-114">在同一个配置文件中定义的终结点行为的名称。</span><span class="sxs-lookup"><span data-stu-id="2222a-114">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2222a-115">子元素</span><span class="sxs-lookup"><span data-stu-id="2222a-115">Child Elements</span></span>

<span data-ttu-id="2222a-116">无。</span><span class="sxs-lookup"><span data-stu-id="2222a-116">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2222a-117">父元素</span><span class="sxs-lookup"><span data-stu-id="2222a-117">Parent Elements</span></span>

|<span data-ttu-id="2222a-118">元素</span><span class="sxs-lookup"><span data-stu-id="2222a-118">Element</span></span>|<span data-ttu-id="2222a-119">描述</span><span class="sxs-lookup"><span data-stu-id="2222a-119">Description</span></span>|
|-------------|-----------------|
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="2222a-120">包含与指定的服务令牌服务通信时要使用的 Windows Communication Foundation （WCF）客户端终结点行为的集合。</span><span class="sxs-lookup"><span data-stu-id="2222a-120">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2222a-121">注解</span><span class="sxs-lookup"><span data-stu-id="2222a-121">Remarks</span></span>

<span data-ttu-id="2222a-122">`issuerAddress` 包含客户端希望与之进行通信的安全令牌服务的 URI。</span><span class="sxs-lookup"><span data-stu-id="2222a-122">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="2222a-123">`behaviorConfiguration`指向应用程序在 Windows Communication Foundation （WCF）创建的通道中使用的终结点行为，以从安全令牌服务获取已颁发的令牌。</span><span class="sxs-lookup"><span data-stu-id="2222a-123">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="2222a-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2222a-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="2222a-125">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="2222a-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="2222a-126">安全行为</span><span class="sxs-lookup"><span data-stu-id="2222a-126">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="2222a-127">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="2222a-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="2222a-128">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="2222a-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2222a-129">保证客户端的安全</span><span class="sxs-lookup"><span data-stu-id="2222a-129">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="2222a-130">如何：创建联合客户端</span><span class="sxs-lookup"><span data-stu-id="2222a-130">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="2222a-131">如何：配置本地颁发者</span><span class="sxs-lookup"><span data-stu-id="2222a-131">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="2222a-132">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="2222a-132">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)
