---
title: <message>的元素<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: dde763687dbc62d6fb342a21a4c614208f28d7e8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738998"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="ccc55-102">\<message>的元素\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ccc55-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="ccc55-103">定义元素的消息级安全性设置 [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="ccc55-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="ccc55-104">语法</span><span class="sxs-lookup"><span data-stu-id="ccc55-104">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri">
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
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
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
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ccc55-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ccc55-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ccc55-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ccc55-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ccc55-107">特性</span><span class="sxs-lookup"><span data-stu-id="ccc55-107">Attributes</span></span>  
  
|<span data-ttu-id="ccc55-108">属性</span><span class="sxs-lookup"><span data-stu-id="ccc55-108">Attribute</span></span>|<span data-ttu-id="ccc55-109">说明</span><span class="sxs-lookup"><span data-stu-id="ccc55-109">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="ccc55-110">可选。</span><span class="sxs-lookup"><span data-stu-id="ccc55-110">Optional.</span></span> <span data-ttu-id="ccc55-111">设置消息加密、签名和密钥包装算法。</span><span class="sxs-lookup"><span data-stu-id="ccc55-111">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="ccc55-112">算法和密钥大小由 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 类确定。</span><span class="sxs-lookup"><span data-stu-id="ccc55-112">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="ccc55-113">这些算法与“安全策略语言”(WS-SecurityPolicy) 规范中指定的算法一致。</span><span class="sxs-lookup"><span data-stu-id="ccc55-113">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="ccc55-114">有关可能的值，请参见下表。</span><span class="sxs-lookup"><span data-stu-id="ccc55-114">See the following table for possible values.</span></span> <span data-ttu-id="ccc55-115">默认值为 Basic256。</span><span class="sxs-lookup"><span data-stu-id="ccc55-115">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="ccc55-116">指定要颁发的密钥类型。</span><span class="sxs-lookup"><span data-stu-id="ccc55-116">Specifies the type of key to be issued.</span></span> <span data-ttu-id="ccc55-117">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="ccc55-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ccc55-118">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="ccc55-118">-   SymmetricKey</span></span><br /><span data-ttu-id="ccc55-119">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="ccc55-119">-   PublicKey</span></span><br /><span data-ttu-id="ccc55-120">-为 bearerkey 并且</span><span class="sxs-lookup"><span data-stu-id="ccc55-120">-   BearerKey</span></span><br /><br /> <span data-ttu-id="ccc55-121">默认值为 SymmetricKey。</span><span class="sxs-lookup"><span data-stu-id="ccc55-121">The default is SymmetricKey.</span></span> <span data-ttu-id="ccc55-122">此属性的类型为 <xref:System.IdentityModel.Tokens.SecurityKeyType>。</span><span class="sxs-lookup"><span data-stu-id="ccc55-122">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="ccc55-123">一个 URI，指定要颁发的令牌的类型。</span><span class="sxs-lookup"><span data-stu-id="ccc55-123">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="ccc55-124">默认为 `null`。</span><span class="sxs-lookup"><span data-stu-id="ccc55-124">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="ccc55-125">一个值，指定是否应在协商过程中交换服务凭据，或者是否可在带外使用服务凭据。</span><span class="sxs-lookup"><span data-stu-id="ccc55-125">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="ccc55-126">默认值为 `true`，这意味着对服务凭据进行协商。</span><span class="sxs-lookup"><span data-stu-id="ccc55-126">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="ccc55-127">algorithmSuite 属性</span><span class="sxs-lookup"><span data-stu-id="ccc55-127">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="ccc55-128">值</span><span class="sxs-lookup"><span data-stu-id="ccc55-128">Value</span></span>|<span data-ttu-id="ccc55-129">说明</span><span class="sxs-lookup"><span data-stu-id="ccc55-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ccc55-130">Basic128</span><span class="sxs-lookup"><span data-stu-id="ccc55-130">Basic128</span></span>|<span data-ttu-id="ccc55-131">使用 Aes128 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="ccc55-131">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ccc55-132">Basic192</span><span class="sxs-lookup"><span data-stu-id="ccc55-132">Basic192</span></span>|<span data-ttu-id="ccc55-133">使用 Aes192 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="ccc55-133">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ccc55-134">Basic256</span><span class="sxs-lookup"><span data-stu-id="ccc55-134">Basic256</span></span>|<span data-ttu-id="ccc55-135">使用 Aes256 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="ccc55-135">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ccc55-136">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ccc55-136">Basic256Rsa15</span></span>|<span data-ttu-id="ccc55-137">对消息加密使用 Aes256，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="ccc55-137">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ccc55-138">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="ccc55-138">Basic192Rsa15</span></span>|<span data-ttu-id="ccc55-139">对消息加密使用 Aes192，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="ccc55-139">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ccc55-140">TripleDes</span><span class="sxs-lookup"><span data-stu-id="ccc55-140">TripleDes</span></span>|<span data-ttu-id="ccc55-141">使用 TripleDes 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="ccc55-141">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ccc55-142">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="ccc55-142">Basic128Rsa15</span></span>|<span data-ttu-id="ccc55-143">对消息加密使用 Aes128，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="ccc55-143">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ccc55-144">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="ccc55-144">TripleDesRsa15</span></span>|<span data-ttu-id="ccc55-145">使用 TripleDes 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="ccc55-145">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ccc55-146">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="ccc55-146">Basic128Sha256</span></span>|<span data-ttu-id="ccc55-147">对消息加密使用 Aes256，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="ccc55-147">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ccc55-148">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="ccc55-148">Basic192Sha256</span></span>|<span data-ttu-id="ccc55-149">对消息加密使用 Aes192，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="ccc55-149">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ccc55-150">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="ccc55-150">Basic256Sha256</span></span>|<span data-ttu-id="ccc55-151">对消息加密使用 Aes256，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="ccc55-151">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ccc55-152">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="ccc55-152">TripleDesSha256</span></span>|<span data-ttu-id="ccc55-153">对消息加密使用 TripleDes，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="ccc55-153">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ccc55-154">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ccc55-154">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="ccc55-155">对消息加密使用 Aes128，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="ccc55-155">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ccc55-156">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ccc55-156">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="ccc55-157">对消息加密使用 Aes192，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="ccc55-157">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ccc55-158">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ccc55-158">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="ccc55-159">对消息加密使用 Aes256，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="ccc55-159">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ccc55-160">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ccc55-160">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="ccc55-161">对消息加密使用 TripleDes，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="ccc55-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ccc55-162">子元素</span><span class="sxs-lookup"><span data-stu-id="ccc55-162">Child Elements</span></span>  
  
|<span data-ttu-id="ccc55-163">元素</span><span class="sxs-lookup"><span data-stu-id="ccc55-163">Element</span></span>|<span data-ttu-id="ccc55-164">描述</span><span class="sxs-lookup"><span data-stu-id="ccc55-164">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="ccc55-165">指定此绑定的声明类型集合。</span><span class="sxs-lookup"><span data-stu-id="ccc55-165">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="ccc55-166">每个元素的类型都为 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="ccc55-166">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[\<issuer>](issuer.md)|<span data-ttu-id="ccc55-167">指定颁发安全令牌的终结点。</span><span class="sxs-lookup"><span data-stu-id="ccc55-167">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="ccc55-168">此元素的类型为 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>。</span><span class="sxs-lookup"><span data-stu-id="ccc55-168">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[\<issuerMetadata>](issuermetadata.md)|<span data-ttu-id="ccc55-169">指定颁发者的终结点地址。</span><span class="sxs-lookup"><span data-stu-id="ccc55-169">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="ccc55-170">令牌请求参数的集合。</span><span class="sxs-lookup"><span data-stu-id="ccc55-170">A collection of token request parameters.</span></span> <span data-ttu-id="ccc55-171">每个参数都是一个 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="ccc55-171">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ccc55-172">父元素</span><span class="sxs-lookup"><span data-stu-id="ccc55-172">Parent Elements</span></span>  
  
|<span data-ttu-id="ccc55-173">元素</span><span class="sxs-lookup"><span data-stu-id="ccc55-173">Element</span></span>|<span data-ttu-id="ccc55-174">描述</span><span class="sxs-lookup"><span data-stu-id="ccc55-174">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="ccc55-175">定义绑定的安全设置。</span><span class="sxs-lookup"><span data-stu-id="ccc55-175">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ccc55-176">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ccc55-176">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="ccc55-177">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="ccc55-177">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ccc55-178">绑定</span><span class="sxs-lookup"><span data-stu-id="ccc55-178">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ccc55-179">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="ccc55-179">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ccc55-180">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="ccc55-180">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
