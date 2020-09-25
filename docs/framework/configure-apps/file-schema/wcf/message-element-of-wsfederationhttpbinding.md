---
title: <message> 的元素 <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: ea320b1d97e742d4f90ec55502f3bd429803283d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204887"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="62b2c-102">\<message> 的元素 \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="62b2c-102">\<message> element of \<wsFederationHttpBinding></span></span>

<span data-ttu-id="62b2c-103">定义的消息级安全性设置 [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="62b2c-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="62b2c-104">语法</span><span class="sxs-lookup"><span data-stu-id="62b2c-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62b2c-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="62b2c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="62b2c-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="62b2c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62b2c-107">特性</span><span class="sxs-lookup"><span data-stu-id="62b2c-107">Attributes</span></span>  
  
|<span data-ttu-id="62b2c-108">属性</span><span class="sxs-lookup"><span data-stu-id="62b2c-108">Attribute</span></span>|<span data-ttu-id="62b2c-109">描述</span><span class="sxs-lookup"><span data-stu-id="62b2c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62b2c-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="62b2c-110">algorithmSuite</span></span>|<span data-ttu-id="62b2c-111">设置消息加密和密钥包装算法。</span><span class="sxs-lookup"><span data-stu-id="62b2c-111">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="62b2c-112">有关此属性的有效值，请参见“algorithmSuite 属性”表。</span><span class="sxs-lookup"><span data-stu-id="62b2c-112">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="62b2c-113">默认值是 `Basic256`。</span><span class="sxs-lookup"><span data-stu-id="62b2c-113">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="62b2c-114">此属性的类型为 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>。</span><span class="sxs-lookup"><span data-stu-id="62b2c-114">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="62b2c-115">这些算法与“安全策略语言”(WS-SecurityPolicy) 规范中指定的算法一致。</span><span class="sxs-lookup"><span data-stu-id="62b2c-115">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="62b2c-116">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="62b2c-116">issuedKeyType</span></span>|<span data-ttu-id="62b2c-117">指定要颁发的密钥类型。</span><span class="sxs-lookup"><span data-stu-id="62b2c-117">Specifies the type of key to be issued.</span></span> <span data-ttu-id="62b2c-118">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="62b2c-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="62b2c-119">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="62b2c-119">-   SymmetricKey</span></span><br /><span data-ttu-id="62b2c-120">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="62b2c-120">-   PublicKey</span></span><br /><br /> <span data-ttu-id="62b2c-121">默认为 `SymmetricKey`。</span><span class="sxs-lookup"><span data-stu-id="62b2c-121">The default is `SymmetricKey`.</span></span> <span data-ttu-id="62b2c-122">此属性的类型为 <xref:System.IdentityModel.Tokens.SecurityKeyType>。</span><span class="sxs-lookup"><span data-stu-id="62b2c-122">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="62b2c-123">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="62b2c-123">issuedTokenType</span></span>|<span data-ttu-id="62b2c-124">一个字符串，它所包含的 URI 指定要颁发的令牌的类型。</span><span class="sxs-lookup"><span data-stu-id="62b2c-124">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="62b2c-125">默认为 `null`。</span><span class="sxs-lookup"><span data-stu-id="62b2c-125">The default is `null`.</span></span>|  
|<span data-ttu-id="62b2c-126">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="62b2c-126">negotiateServiceCredential</span></span>|<span data-ttu-id="62b2c-127">一个布尔值，指定是否应在协商过程中交换服务凭据，或者是否可在带外使用服务凭据。</span><span class="sxs-lookup"><span data-stu-id="62b2c-127">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="62b2c-128">默认值为 `true`，这意味着对服务凭据进行协商。</span><span class="sxs-lookup"><span data-stu-id="62b2c-128">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="62b2c-129">algorithmSuite 属性</span><span class="sxs-lookup"><span data-stu-id="62b2c-129">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="62b2c-130">值</span><span class="sxs-lookup"><span data-stu-id="62b2c-130">Value</span></span>|<span data-ttu-id="62b2c-131">描述</span><span class="sxs-lookup"><span data-stu-id="62b2c-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="62b2c-132">Basic128</span><span class="sxs-lookup"><span data-stu-id="62b2c-132">Basic128</span></span>|<span data-ttu-id="62b2c-133">使用 Basic128 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="62b2c-133">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="62b2c-134">Basic192</span><span class="sxs-lookup"><span data-stu-id="62b2c-134">Basic192</span></span>|<span data-ttu-id="62b2c-135">使用 Basic192 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="62b2c-135">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="62b2c-136">Basic256</span><span class="sxs-lookup"><span data-stu-id="62b2c-136">Basic256</span></span>|<span data-ttu-id="62b2c-137">使用 Basic256 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="62b2c-137">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="62b2c-138">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="62b2c-138">Basic256Rsa15</span></span>|<span data-ttu-id="62b2c-139">对消息加密使用 Basic256，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="62b2c-139">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="62b2c-140">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="62b2c-140">Basic192Rsa15</span></span>|<span data-ttu-id="62b2c-141">对消息加密使用 Basic192，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="62b2c-141">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="62b2c-142">TripleDes</span><span class="sxs-lookup"><span data-stu-id="62b2c-142">TripleDes</span></span>|<span data-ttu-id="62b2c-143">使用 TripleDes 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="62b2c-143">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="62b2c-144">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="62b2c-144">Basic128Rsa15</span></span>|<span data-ttu-id="62b2c-145">对消息加密使用 Basic128，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="62b2c-145">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="62b2c-146">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="62b2c-146">TripleDesRsa15</span></span>|<span data-ttu-id="62b2c-147">使用 TripleDes 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="62b2c-147">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="62b2c-148">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="62b2c-148">Basic128Sha256</span></span>|<span data-ttu-id="62b2c-149">对消息加密使用 Basic128，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="62b2c-149">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="62b2c-150">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="62b2c-150">Basic192Sha256</span></span>|<span data-ttu-id="62b2c-151">对消息加密使用 Basic192，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="62b2c-151">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="62b2c-152">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="62b2c-152">Basic256Sha256</span></span>|<span data-ttu-id="62b2c-153">对消息加密使用 Basic256，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="62b2c-153">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="62b2c-154">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="62b2c-154">TripleDesSha256</span></span>|<span data-ttu-id="62b2c-155">对消息加密使用 TripleDes，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。</span><span class="sxs-lookup"><span data-stu-id="62b2c-155">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="62b2c-156">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="62b2c-156">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="62b2c-157">对消息加密使用 Basic128，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="62b2c-157">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="62b2c-158">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="62b2c-158">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="62b2c-159">对消息加密使用 Aes192，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="62b2c-159">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="62b2c-160">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="62b2c-160">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="62b2c-161">对消息加密使用 Basic256，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="62b2c-161">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="62b2c-162">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="62b2c-162">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="62b2c-163">对消息加密使用 TripleDes，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。</span><span class="sxs-lookup"><span data-stu-id="62b2c-163">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62b2c-164">子元素</span><span class="sxs-lookup"><span data-stu-id="62b2c-164">Child Elements</span></span>  
  
|<span data-ttu-id="62b2c-165">元素</span><span class="sxs-lookup"><span data-stu-id="62b2c-165">Element</span></span>|<span data-ttu-id="62b2c-166">描述</span><span class="sxs-lookup"><span data-stu-id="62b2c-166">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="62b2c-167">指定此绑定的声明类型集合。</span><span class="sxs-lookup"><span data-stu-id="62b2c-167">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="62b2c-168">每个元素的类型都为 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。</span><span class="sxs-lookup"><span data-stu-id="62b2c-168">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="62b2c-169">颁发者</span><span class="sxs-lookup"><span data-stu-id="62b2c-169">issuer</span></span>|<span data-ttu-id="62b2c-170">指定颁发安全令牌的终结点。</span><span class="sxs-lookup"><span data-stu-id="62b2c-170">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="62b2c-171">此元素的类型为 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>。</span><span class="sxs-lookup"><span data-stu-id="62b2c-171">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="62b2c-172">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="62b2c-172">issuerMetadata</span></span>|<span data-ttu-id="62b2c-173">指定颁发者的终结点地址。</span><span class="sxs-lookup"><span data-stu-id="62b2c-173">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="62b2c-174">令牌请求参数的集合。</span><span class="sxs-lookup"><span data-stu-id="62b2c-174">A collection of token request parameters.</span></span> <span data-ttu-id="62b2c-175">每个参数都是一个 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="62b2c-175">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="62b2c-176">父元素</span><span class="sxs-lookup"><span data-stu-id="62b2c-176">Parent Elements</span></span>  
  
|<span data-ttu-id="62b2c-177">元素</span><span class="sxs-lookup"><span data-stu-id="62b2c-177">Element</span></span>|<span data-ttu-id="62b2c-178">描述</span><span class="sxs-lookup"><span data-stu-id="62b2c-178">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="62b2c-179">定义绑定的安全设置。</span><span class="sxs-lookup"><span data-stu-id="62b2c-179">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62b2c-180">请参阅</span><span class="sxs-lookup"><span data-stu-id="62b2c-180">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="62b2c-181">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="62b2c-181">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="62b2c-182">绑定</span><span class="sxs-lookup"><span data-stu-id="62b2c-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="62b2c-183">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="62b2c-183">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="62b2c-184">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="62b2c-184">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
