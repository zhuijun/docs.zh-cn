---
title: <security> 的 <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: 650483099c7d70450cfc56a9a28efac076d64675
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162227"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="8d237-102">\<security> 的 \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="8d237-102">\<security> of \<wsFederationHttpBinding></span></span>

<span data-ttu-id="8d237-103">定义的安全设置 [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="8d237-103">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="8d237-104">语法</span><span class="sxs-lookup"><span data-stu-id="8d237-104">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri" >
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
      </message>
    </security>
  </binding>
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d237-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="8d237-105">Attributes and Elements</span></span>  

 <span data-ttu-id="8d237-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8d237-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d237-107">特性</span><span class="sxs-lookup"><span data-stu-id="8d237-107">Attributes</span></span>  
  
|<span data-ttu-id="8d237-108">属性</span><span class="sxs-lookup"><span data-stu-id="8d237-108">Attribute</span></span>|<span data-ttu-id="8d237-109">说明</span><span class="sxs-lookup"><span data-stu-id="8d237-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d237-110">“模式”</span><span class="sxs-lookup"><span data-stu-id="8d237-110">Mode</span></span>|<span data-ttu-id="8d237-111">可选。</span><span class="sxs-lookup"><span data-stu-id="8d237-111">Optional.</span></span> <span data-ttu-id="8d237-112">指定所应用的安全类型。</span><span class="sxs-lookup"><span data-stu-id="8d237-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="8d237-113">默认值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="8d237-113">The default value is `Message`.</span></span> <span data-ttu-id="8d237-114">此属性的类型为 <xref:System.ServiceModel.WSFederationHttpSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="8d237-114">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="8d237-115">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="8d237-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="8d237-116">值</span><span class="sxs-lookup"><span data-stu-id="8d237-116">Value</span></span>|<span data-ttu-id="8d237-117">描述</span><span class="sxs-lookup"><span data-stu-id="8d237-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8d237-118">无</span><span class="sxs-lookup"><span data-stu-id="8d237-118">None</span></span>|<span data-ttu-id="8d237-119">SOAP 消息在传输过程中并不安全。</span><span class="sxs-lookup"><span data-stu-id="8d237-119">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="8d237-120">消息</span><span class="sxs-lookup"><span data-stu-id="8d237-120">Message</span></span>|<span data-ttu-id="8d237-121">通过使用 SOAP 消息安全，可以提供完整性、保密性、服务器身份验证和客户端身份验证。</span><span class="sxs-lookup"><span data-stu-id="8d237-121">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="8d237-122">默认情况下，将对正文进行加密和签名。</span><span class="sxs-lookup"><span data-stu-id="8d237-122">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="8d237-123">此服务需要使用证书进行配置。</span><span class="sxs-lookup"><span data-stu-id="8d237-123">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="8d237-124">客户端根据由安全令牌服务颁发给客户端的令牌进行身份验证</span><span class="sxs-lookup"><span data-stu-id="8d237-124">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="8d237-125">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="8d237-125">TransportWithMessageCredential</span></span>|<span data-ttu-id="8d237-126">完整性、保密性和服务器身份验证均由 HTTPS 提供。</span><span class="sxs-lookup"><span data-stu-id="8d237-126">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="8d237-127">此服务需要使用证书进行配置。</span><span class="sxs-lookup"><span data-stu-id="8d237-127">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="8d237-128">客户端身份验证采用 SOAP 消息安全方式提供，并根据由安全令牌服务颁发给客户端的令牌进行。</span><span class="sxs-lookup"><span data-stu-id="8d237-128">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d237-129">子元素</span><span class="sxs-lookup"><span data-stu-id="8d237-129">Child Elements</span></span>  
  
|<span data-ttu-id="8d237-130">元素</span><span class="sxs-lookup"><span data-stu-id="8d237-130">Element</span></span>|<span data-ttu-id="8d237-131">描述</span><span class="sxs-lookup"><span data-stu-id="8d237-131">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="8d237-132">定义消息级安全性设置。</span><span class="sxs-lookup"><span data-stu-id="8d237-132">Defines the settings for the message-level security.</span></span> <span data-ttu-id="8d237-133">此元素的类型为 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>。</span><span class="sxs-lookup"><span data-stu-id="8d237-133">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d237-134">父元素</span><span class="sxs-lookup"><span data-stu-id="8d237-134">Parent Elements</span></span>  
  
|<span data-ttu-id="8d237-135">元素</span><span class="sxs-lookup"><span data-stu-id="8d237-135">Element</span></span>|<span data-ttu-id="8d237-136">描述</span><span class="sxs-lookup"><span data-stu-id="8d237-136">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="8d237-137">定义的所有绑定功能 [\<wsDualHttpBinding>](wsdualhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="8d237-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d237-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="8d237-138">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="8d237-139">如何：创建 WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="8d237-139">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="8d237-140">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="8d237-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8d237-141">选择凭据类型</span><span class="sxs-lookup"><span data-stu-id="8d237-141">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="8d237-142">绑定</span><span class="sxs-lookup"><span data-stu-id="8d237-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8d237-143">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="8d237-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8d237-144">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="8d237-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
