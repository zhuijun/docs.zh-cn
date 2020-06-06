---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 055b7b49d1f775d49ac20de18c18ca0433716a23
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397863"
---
# \<localIssuer>
<span data-ttu-id="c0945-101">指定要用于颁发安全令牌的本地颁发者的地址和绑定。</span><span class="sxs-lookup"><span data-stu-id="c0945-101">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**  
  
## <a name="syntax"></a><span data-ttu-id="c0945-102">语法</span><span class="sxs-lookup"><span data-stu-id="c0945-102">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0945-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c0945-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c0945-104">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c0945-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0945-105">特性</span><span class="sxs-lookup"><span data-stu-id="c0945-105">Attributes</span></span>  
  
|<span data-ttu-id="c0945-106">属性</span><span class="sxs-lookup"><span data-stu-id="c0945-106">Attribute</span></span>|<span data-ttu-id="c0945-107">说明</span><span class="sxs-lookup"><span data-stu-id="c0945-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0945-108">address</span><span class="sxs-lookup"><span data-stu-id="c0945-108">address</span></span>|<span data-ttu-id="c0945-109">必需的字符串。</span><span class="sxs-lookup"><span data-stu-id="c0945-109">Required string.</span></span> <span data-ttu-id="c0945-110">指定本地颁发者的 URI。</span><span class="sxs-lookup"><span data-stu-id="c0945-110">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="c0945-111">binding</span><span class="sxs-lookup"><span data-stu-id="c0945-111">binding</span></span>|<span data-ttu-id="c0945-112">可选的字符串。</span><span class="sxs-lookup"><span data-stu-id="c0945-112">Optional string.</span></span> <span data-ttu-id="c0945-113">系统提供的一个绑定。</span><span class="sxs-lookup"><span data-stu-id="c0945-113">One of the system-provided bindings.</span></span> <span data-ttu-id="c0945-114">有关列表，请参阅[系统提供的绑定](../../../wcf/system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="c0945-114">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="c0945-115">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="c0945-115">bindingConfiguration</span></span>|<span data-ttu-id="c0945-116">可选的字符串。</span><span class="sxs-lookup"><span data-stu-id="c0945-116">Optional string.</span></span> <span data-ttu-id="c0945-117">指定在配置文件中找到的绑定配置。</span><span class="sxs-lookup"><span data-stu-id="c0945-117">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0945-118">子元素</span><span class="sxs-lookup"><span data-stu-id="c0945-118">Child Elements</span></span>  
  
|<span data-ttu-id="c0945-119">元素</span><span class="sxs-lookup"><span data-stu-id="c0945-119">Element</span></span>|<span data-ttu-id="c0945-120">描述</span><span class="sxs-lookup"><span data-stu-id="c0945-120">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="c0945-121">指定此本地颁发者的标识信息。</span><span class="sxs-lookup"><span data-stu-id="c0945-121">Specifies identity information for the local issuer.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="c0945-122">地址头的集合，要正确书写本地颁发者的地址必须使用这些地址头。</span><span class="sxs-lookup"><span data-stu-id="c0945-122">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="c0945-123">可以使用 `add` 关键字向此集合添加标头。</span><span class="sxs-lookup"><span data-stu-id="c0945-123">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c0945-124">父元素</span><span class="sxs-lookup"><span data-stu-id="c0945-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c0945-125">元素</span><span class="sxs-lookup"><span data-stu-id="c0945-125">Element</span></span>|<span data-ttu-id="c0945-126">描述</span><span class="sxs-lookup"><span data-stu-id="c0945-126">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="c0945-127">指定用于向服务验证客户端身份的自定义令牌。</span><span class="sxs-lookup"><span data-stu-id="c0945-127">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0945-128">注解</span><span class="sxs-lookup"><span data-stu-id="c0945-128">Remarks</span></span>  
 <span data-ttu-id="c0945-129">从安全令牌服务 (STS) 获取已颁发的令牌时，必须使用地址和绑定配置客户端应用程序，以将其用于与 STS 进行通信。</span><span class="sxs-lookup"><span data-stu-id="c0945-129">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="c0945-130">如果没有 <xref:System.ServiceModel.WSFederationHttpBinding> 为 security token service 提供 URL，或者联合绑定的颁发者地址为 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` 或时 `null` ，则客户端的 Windows Communication Foundation （WCF）通道使用由和指定的值 `address` `binding` 来与 STS 通信以获取已颁发的令牌。</span><span class="sxs-lookup"><span data-stu-id="c0945-130">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="c0945-131">有关配置本地颁发者的详细信息，请参阅[如何：配置本地颁发者](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)。</span><span class="sxs-lookup"><span data-stu-id="c0945-131">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0945-132">示例</span><span class="sxs-lookup"><span data-stu-id="c0945-132">Example</span></span>  
 <span data-ttu-id="c0945-133">下面的示例设置 `address` 元素的 `binding`、`bindingConfiguration` 和 `localIssuer` 属性。</span><span class="sxs-lookup"><span data-stu-id="c0945-133">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
```xml  
<system.serviceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="MyEndpointBehavior">
        <clientCredentials>
          <issuedToken cacheIssuedTokens="false"
                       defaultKeyEntropyMode="ClientEntropy">
            <localIssuer address="net.tcp://cohowinery/tokens"
                         binding="netTcpBinding"
                         bindingConfiguration="myTcpBindingConfig" />
          </issuedToken>
        </clientCredentials>
      </behavior>
    </endpointBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="c0945-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0945-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="c0945-135">安全行为</span><span class="sxs-lookup"><span data-stu-id="c0945-135">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="c0945-136">如何：配置本地颁发者</span><span class="sxs-lookup"><span data-stu-id="c0945-136">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="c0945-137">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="c0945-137">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c0945-138">安全行为</span><span class="sxs-lookup"><span data-stu-id="c0945-138">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="c0945-139">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="c0945-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c0945-140">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="c0945-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c0945-141">保证客户端的安全</span><span class="sxs-lookup"><span data-stu-id="c0945-141">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="c0945-142">如何：创建联合客户端</span><span class="sxs-lookup"><span data-stu-id="c0945-142">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="c0945-143">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="c0945-143">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
