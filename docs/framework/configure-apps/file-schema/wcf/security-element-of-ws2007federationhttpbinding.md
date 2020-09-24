---
title: <security> 的元素 <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 943ccc241aef15b58661699408b085d98cf86c3b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183697"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="08589-102">\<security> 的元素 \<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="08589-102">\<security> element of \<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="08589-103">定义元素的安全设置 [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="08589-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="08589-104">语法</span><span class="sxs-lookup"><span data-stu-id="08589-104">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/  Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               defaultProtectionLevel="none/sign/EncryptAndSign"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08589-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="08589-105">Attributes and Elements</span></span>  

 <span data-ttu-id="08589-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="08589-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08589-107">特性</span><span class="sxs-lookup"><span data-stu-id="08589-107">Attributes</span></span>  
  
|<span data-ttu-id="08589-108">属性</span><span class="sxs-lookup"><span data-stu-id="08589-108">Attribute</span></span>|<span data-ttu-id="08589-109">描述</span><span class="sxs-lookup"><span data-stu-id="08589-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="08589-110">可选。</span><span class="sxs-lookup"><span data-stu-id="08589-110">Optional.</span></span> <span data-ttu-id="08589-111">指定所应用的安全类型。</span><span class="sxs-lookup"><span data-stu-id="08589-111">Specifies the type of security that is applied.</span></span> <span data-ttu-id="08589-112">默认值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="08589-112">The default value is `Message`.</span></span> <span data-ttu-id="08589-113">此属性的类型为 <xref:System.ServiceModel.WSFederationHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="08589-113">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="08589-114">mode 属性</span><span class="sxs-lookup"><span data-stu-id="08589-114">mode Attribute</span></span>  
  
|<span data-ttu-id="08589-115">值</span><span class="sxs-lookup"><span data-stu-id="08589-115">Value</span></span>|<span data-ttu-id="08589-116">描述</span><span class="sxs-lookup"><span data-stu-id="08589-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="08589-117">无</span><span class="sxs-lookup"><span data-stu-id="08589-117">None</span></span>|<span data-ttu-id="08589-118">SOAP 消息在传输过程中并不安全。</span><span class="sxs-lookup"><span data-stu-id="08589-118">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="08589-119">消息</span><span class="sxs-lookup"><span data-stu-id="08589-119">Message</span></span>|<span data-ttu-id="08589-120">通过使用 SOAP 消息安全，可以提供完整性、保密性、服务器身份验证和客户端身份验证。</span><span class="sxs-lookup"><span data-stu-id="08589-120">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="08589-121">默认情况下，将对正文进行加密和签名。</span><span class="sxs-lookup"><span data-stu-id="08589-121">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="08589-122">此服务必须使用证书进行配置。</span><span class="sxs-lookup"><span data-stu-id="08589-122">The service must be configured with a certificate.</span></span> <span data-ttu-id="08589-123">客户端根据由安全令牌服务颁发给客户端的令牌进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="08589-123">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="08589-124">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="08589-124">TransportWithMessageCredential</span></span>|<span data-ttu-id="08589-125">完整性、保密性和服务器身份验证均由 HTTPS 提供。</span><span class="sxs-lookup"><span data-stu-id="08589-125">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="08589-126">此服务必须使用证书进行配置。</span><span class="sxs-lookup"><span data-stu-id="08589-126">The service must be configured with a certificate.</span></span> <span data-ttu-id="08589-127">客户端身份验证采用 SOAP 消息安全方式提供，并根据由安全令牌服务颁发给客户端的令牌进行。</span><span class="sxs-lookup"><span data-stu-id="08589-127">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08589-128">子元素</span><span class="sxs-lookup"><span data-stu-id="08589-128">Child Elements</span></span>  
  
|<span data-ttu-id="08589-129">元素</span><span class="sxs-lookup"><span data-stu-id="08589-129">Element</span></span>|<span data-ttu-id="08589-130">描述</span><span class="sxs-lookup"><span data-stu-id="08589-130">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="08589-131">定义消息级安全性设置。</span><span class="sxs-lookup"><span data-stu-id="08589-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="08589-132">此元素的类型为 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>。</span><span class="sxs-lookup"><span data-stu-id="08589-132">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="08589-133">父元素</span><span class="sxs-lookup"><span data-stu-id="08589-133">Parent Elements</span></span>  
  
|<span data-ttu-id="08589-134">元素</span><span class="sxs-lookup"><span data-stu-id="08589-134">Element</span></span>|<span data-ttu-id="08589-135">描述</span><span class="sxs-lookup"><span data-stu-id="08589-135">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="08589-136">定义的所有绑定功能 [\<wsDualHttpBinding>](wsdualhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="08589-136">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08589-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="08589-137">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="08589-138">如何：创建 WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="08589-138">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="08589-139">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="08589-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="08589-140">选择凭据类型</span><span class="sxs-lookup"><span data-stu-id="08589-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="08589-141">绑定</span><span class="sxs-lookup"><span data-stu-id="08589-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="08589-142">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="08589-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="08589-143">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="08589-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
