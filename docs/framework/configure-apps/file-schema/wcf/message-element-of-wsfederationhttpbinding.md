---
title: <message>的元素<wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 8e0903dd1313e68e2de65730e129079199ebe2f2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738982"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="d58ee-102">\<message>的元素\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d58ee-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="d58ee-103">定义的消息级安全性设置 [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="d58ee-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="d58ee-104">语法</span><span class="sxs-lookup"><span data-stu-id="d58ee-104">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
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
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d58ee-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="d58ee-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d58ee-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d58ee-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d58ee-107">特性</span><span class="sxs-lookup"><span data-stu-id="d58ee-107">Attributes</span></span>  
  
|<span data-ttu-id="d58ee-108">属性</span><span class="sxs-lookup"><span data-stu-id="d58ee-108">Attribute</span></span>|<span data-ttu-id="d58ee-109">说明</span><span class="sxs-lookup"><span data-stu-id="d58ee-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d58ee-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="d58ee-110">algorithmSuite</span></span>|<span data-ttu-id="d58ee-111">设置消息加密和密钥包装算法。</span><span class="sxs-lookup"><span data-stu-id="d58ee-111">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="d58ee-112">有关此属性的有效值，请参见“algorithmSuite 属性”表。</span><span class="sxs-lookup"><span data-stu-id="d58ee-112">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="d58ee-113">默认值为 `Basic256`。</span><span class="sxs-lookup"><span data-stu-id="d58ee-113">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="d58ee-114">此属性的类型为 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>。</span><span class="sxs-lookup"><span data-stu-id="d58ee-114">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="d58ee-115">这些算法与“安全策略语言”(WS-SecurityPolicy) 规范中指定的算法一致。</span><span class="sxs-lookup"><span data-stu-id="d58ee-115">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="d58ee-116">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="d58ee-116">issuedKeyType</span></span>|<span data-ttu-id="d58ee-117">指定要颁发的密钥类型。</span><span class="sxs-lookup"><span data-stu-id="d58ee-117">Specifies the type of key to be issued.</span></span> <span data-ttu-id="d58ee-118">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="d58ee-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d58ee-119">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="d58ee-119">-   SymmetricKey</span></span><br /><span data-ttu-id="d58ee-120">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="d58ee-120">-   PublicKey</span></span><br /><br /> <span data-ttu-id="d58ee-121">默认为 `SymmetricKey`。</span><span class="sxs-lookup"><span data-stu-id="d58ee-121">The default is `SymmetricKey`.</span></span> <span data-ttu-id="d58ee-122">此属性的类型为 <xref:System.IdentityModel.Tokens.SecurityKeyType>。</span><span class="sxs-lookup"><span data-stu-id="d58ee-122">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="d58ee-123">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="d58ee-123">issuedTokenType</span></span>|<span data-ttu-id="d58ee-124">一个字符串，它所包含的 URI 指定要颁发的令牌的类型。</span><span class="sxs-lookup"><span data-stu-id="d58ee-124">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="d58ee-125">默认为 `null`。</span><span class="sxs-lookup"><span data-stu-id="d58ee-125">The default is `null`.</span></span>|  
|<span data-ttu-id="d58ee-126">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="d58ee-126">negotiateServiceCredential</span></span>|<span data-ttu-id="d58ee-127">一个布尔值，指定是否应在协商过程中交换服务凭据，或者是否可在带外使用服务凭据。</span><span class="sxs-lookup"><span data-stu-id="d58ee-127">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="d58ee-128">默认值为 `true`，这意味着对服务凭据进行协商。</span><span class="sxs-lookup"><span data-stu-id="d58ee-128">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="d58ee-129">algorithmSuite 属性</span><span class="sxs-lookup"><span data-stu-id="d58ee-129">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="d58ee-130">值</span><span class="sxs-lookup"><span data-stu-id="d58ee-130">Value</span></span>|<span data-ttu-id="d58ee-131">说明</span><span class="sxs-lookup"><span data-stu-id="d58ee-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d58ee-132">Basic128</span><span class="sxs-lookup"><span data-stu-id="d58ee-132">Basic128</span></span>|<span data-ttu-id="d58ee-133">使用 Basic128 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="d58ee-133">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d58ee-134">Basic192</span><span class="sxs-lookup"><span data-stu-id="d58ee-134">Basic192</span></span>|<span data-ttu-id="d58ee-135">使用 Basic192 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="d58ee-135">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d58ee-136">Basic256</span><span class="sxs-lookup"><span data-stu-id="d58ee-136">Basic256</span></span>|<span data-ttu-id="d58ee-137">使用 Basic256 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="d58ee-137">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d58ee-138">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d58ee-138">Basic256Rsa15</span></span>|<span data-ttu-id="d58ee-139">对消息加密使用 Basic256，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="d58ee-139">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d58ee-140">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="d58ee-140">Basic192Rsa15</span></span>|<span data-ttu-id="d58ee-141">对消息加密使用 Basic192，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="d58ee-141">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d58ee-142">TripleDes</span><span class="sxs-lookup"><span data-stu-id="d58ee-142">TripleDes</span></span>|<span data-ttu-id="d58ee-143">使用 TripleDes 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="d58ee-143">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d58ee-144">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="d58ee-144">Basic128Rsa15</span></span>|<span data-ttu-id="d58ee-145">对消息加密使用 Basic128，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="d58ee-145">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d58ee-146">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="d58ee-146">TripleDesRsa15</span></span>|<span data-ttu-id="d58ee-147">使用 TripleDes 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="d58ee-147">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d58ee-148">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="d58ee-148">Basic128Sha256</span></span>|<span data-ttu-id="d58ee-149">对消息加密使用 Basic128，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="d58ee-149">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d58ee-150">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="d58ee-150">Basic192Sha256</span></span>|<span data-ttu-id="d58ee-151">对消息加密使用 Basic192，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="d58ee-151">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d58ee-152">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="d58ee-152">Basic256Sha256</span></span>|<span data-ttu-id="d58ee-153">对消息加密使用 Basic256，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="d58ee-153">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d58ee-154">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="d58ee-154">TripleDesSha256</span></span>|<span data-ttu-id="d58ee-155">对消息加密使用 TripleDes，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="d58ee-155">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="d58ee-156">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d58ee-156">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="d58ee-157">对消息加密使用 Basic128，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="d58ee-157">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d58ee-158">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d58ee-158">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="d58ee-159">对消息加密使用 Aes192，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="d58ee-159">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d58ee-160">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d58ee-160">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="d58ee-161">对消息加密使用 Basic256，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="d58ee-161">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="d58ee-162">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="d58ee-162">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="d58ee-163">对消息加密使用 TripleDes，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="d58ee-163">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d58ee-164">子元素</span><span class="sxs-lookup"><span data-stu-id="d58ee-164">Child Elements</span></span>  
  
|<span data-ttu-id="d58ee-165">元素</span><span class="sxs-lookup"><span data-stu-id="d58ee-165">Element</span></span>|<span data-ttu-id="d58ee-166">描述</span><span class="sxs-lookup"><span data-stu-id="d58ee-166">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="d58ee-167">指定此绑定的声明类型集合。</span><span class="sxs-lookup"><span data-stu-id="d58ee-167">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="d58ee-168">每个元素的类型都为 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="d58ee-168">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="d58ee-169">颁发者</span><span class="sxs-lookup"><span data-stu-id="d58ee-169">issuer</span></span>|<span data-ttu-id="d58ee-170">指定颁发安全令牌的终结点。</span><span class="sxs-lookup"><span data-stu-id="d58ee-170">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="d58ee-171">此元素的类型为 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>。</span><span class="sxs-lookup"><span data-stu-id="d58ee-171">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="d58ee-172">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="d58ee-172">issuerMetadata</span></span>|<span data-ttu-id="d58ee-173">指定颁发者的终结点地址。</span><span class="sxs-lookup"><span data-stu-id="d58ee-173">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="d58ee-174">令牌请求参数的集合。</span><span class="sxs-lookup"><span data-stu-id="d58ee-174">A collection of token request parameters.</span></span> <span data-ttu-id="d58ee-175">每个参数都是一个 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="d58ee-175">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d58ee-176">父元素</span><span class="sxs-lookup"><span data-stu-id="d58ee-176">Parent Elements</span></span>  
  
|<span data-ttu-id="d58ee-177">元素</span><span class="sxs-lookup"><span data-stu-id="d58ee-177">Element</span></span>|<span data-ttu-id="d58ee-178">描述</span><span class="sxs-lookup"><span data-stu-id="d58ee-178">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="d58ee-179">定义绑定的安全设置。</span><span class="sxs-lookup"><span data-stu-id="d58ee-179">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d58ee-180">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d58ee-180">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="d58ee-181">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="d58ee-181">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d58ee-182">绑定</span><span class="sxs-lookup"><span data-stu-id="d58ee-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d58ee-183">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="d58ee-183">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d58ee-184">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="d58ee-184">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
