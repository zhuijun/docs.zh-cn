---
title: <issuedTokenAuthentication> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 6d468a27ee05fb4dd8cf087d10e5d170783d3454
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400362"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a><span data-ttu-id="fc117-102">\<issuedTokenAuthentication> 的 \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="fc117-102">\<issuedTokenAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="fc117-103">指定作为服务凭据颁发的自定义令牌。</span><span class="sxs-lookup"><span data-stu-id="fc117-103">Specifies a custom token issued as a service credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="fc117-104">语法</span><span class="sxs-lookup"><span data-stu-id="fc117-104">Syntax</span></span>  
  
```xml  
<issuedTokenAuthentication allowUntrustedRsaIssuers="Boolean"
                           audienceUriMode="Always/BearerKeyOnly/Never"
                           customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                           certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                           revocationMode="NoCheck/Online/Offline"
                           samlSerializer="String"
                           trustedStoreLocation="CurrentUser/LocalMachine">
  <allowedAudienceUris>
    <add allowedAudienceUri="String" />
  </allowedAudienceUris>
  <knownCertificates>
    <add findValue="String"
         storeLocation="CurrentUser/LocalMachine"
         storeName=" CurrentUser/LocalMachine"
         x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc117-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="fc117-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fc117-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fc117-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc117-107">特性</span><span class="sxs-lookup"><span data-stu-id="fc117-107">Attributes</span></span>  
  
|<span data-ttu-id="fc117-108">属性</span><span class="sxs-lookup"><span data-stu-id="fc117-108">Attribute</span></span>|<span data-ttu-id="fc117-109">说明</span><span class="sxs-lookup"><span data-stu-id="fc117-109">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="fc117-110">获取 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全令牌的目标 URI 集，只有在使用这些目标 URI 时，<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 实例才会将该令牌视为有效令牌。</span><span class="sxs-lookup"><span data-stu-id="fc117-110">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="fc117-111">有关使用此属性的更多信息，请参见 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>。</span><span class="sxs-lookup"><span data-stu-id="fc117-111">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="fc117-112">一个布尔值，指定是否允许不可信的 RSA 证书颁发者。</span><span class="sxs-lookup"><span data-stu-id="fc117-112">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="fc117-113">证书由证书颁发机构 (CA) 签名，以验证真实性。</span><span class="sxs-lookup"><span data-stu-id="fc117-113">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="fc117-114">不可信的颁发者是指未被指定为可信的证书签名者的 CA。</span><span class="sxs-lookup"><span data-stu-id="fc117-114">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="fc117-115">获取一个值，该值指定是否应验证 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全令牌的 <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition>。</span><span class="sxs-lookup"><span data-stu-id="fc117-115">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="fc117-116">此值的类型为 <xref:System.IdentityModel.Selectors.AudienceUriMode>。</span><span class="sxs-lookup"><span data-stu-id="fc117-116">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="fc117-117">有关使用此属性的更多信息，请参见 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>。</span><span class="sxs-lookup"><span data-stu-id="fc117-117">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="fc117-118">设置证书验证模式。</span><span class="sxs-lookup"><span data-stu-id="fc117-118">Sets the certificate validation mode.</span></span> <span data-ttu-id="fc117-119"><xref:System.ServiceModel.Security.X509CertificateValidationMode> 的有效值之一。</span><span class="sxs-lookup"><span data-stu-id="fc117-119">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="fc117-120">如果设置为 `Custom`，则还必须提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="fc117-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="fc117-121">默认为 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="fc117-121">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="fc117-122">可选的字符串。</span><span class="sxs-lookup"><span data-stu-id="fc117-122">Optional string.</span></span> <span data-ttu-id="fc117-123">一个用于验证自定义类型的类型和程序集。</span><span class="sxs-lookup"><span data-stu-id="fc117-123">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="fc117-124">当 `certificateValidationMode` 设置为 `Custom` 时，必须设置此属性。</span><span class="sxs-lookup"><span data-stu-id="fc117-124">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="fc117-125">设置吊销模式以指定是否进行吊销检查，以及是联机执行还是脱机执行。</span><span class="sxs-lookup"><span data-stu-id="fc117-125">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="fc117-126">此属性的类型为 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>。</span><span class="sxs-lookup"><span data-stu-id="fc117-126">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="fc117-127">一个可选字符串属性，指定用于服务凭据的 SamlSerializer 的类型。</span><span class="sxs-lookup"><span data-stu-id="fc117-127">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="fc117-128">默认值为空字符串。</span><span class="sxs-lookup"><span data-stu-id="fc117-128">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="fc117-129">可选的枚举。</span><span class="sxs-lookup"><span data-stu-id="fc117-129">Optional enumeration.</span></span> <span data-ttu-id="fc117-130">两个系统存储位置之一：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="fc117-130">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc117-131">子元素</span><span class="sxs-lookup"><span data-stu-id="fc117-131">Child Elements</span></span>  
  
|<span data-ttu-id="fc117-132">元素</span><span class="sxs-lookup"><span data-stu-id="fc117-132">Element</span></span>|<span data-ttu-id="fc117-133">描述</span><span class="sxs-lookup"><span data-stu-id="fc117-133">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="fc117-134">指定一个 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> 元素的集合，此集合指定服务凭据的可信颁发者。</span><span class="sxs-lookup"><span data-stu-id="fc117-134">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fc117-135">父元素</span><span class="sxs-lookup"><span data-stu-id="fc117-135">Parent Elements</span></span>  
  
|<span data-ttu-id="fc117-136">元素</span><span class="sxs-lookup"><span data-stu-id="fc117-136">Element</span></span>|<span data-ttu-id="fc117-137">描述</span><span class="sxs-lookup"><span data-stu-id="fc117-137">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="fc117-138">指定要用于对服务进行身份验证的凭据以及与客户端凭据验证相关的设置。</span><span class="sxs-lookup"><span data-stu-id="fc117-138">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc117-139">注解</span><span class="sxs-lookup"><span data-stu-id="fc117-139">Remarks</span></span>  
 <span data-ttu-id="fc117-140">颁发的令牌方案包含三个阶段。</span><span class="sxs-lookup"><span data-stu-id="fc117-140">The issued token scenario has three stages.</span></span> <span data-ttu-id="fc117-141">在第一阶段中，尝试访问服务的客户端被称为 "*安全令牌服务*"。</span><span class="sxs-lookup"><span data-stu-id="fc117-141">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="fc117-142">然后，安全令牌服务对该客户端进行身份验证，随后向该客户端颁发一个令牌（通常是一个安全断言标记语言 (SAML) 令牌）。</span><span class="sxs-lookup"><span data-stu-id="fc117-142">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="fc117-143">接下来，客户端携带此令牌返回服务。</span><span class="sxs-lookup"><span data-stu-id="fc117-143">The client then returns to the service with the token.</span></span> <span data-ttu-id="fc117-144">服务检查该令牌，以获取使其可以对该令牌并进而对该客户端进行身份验证的数据。</span><span class="sxs-lookup"><span data-stu-id="fc117-144">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="fc117-145">若要对令牌进行身份验证，安全令牌服务所使用的证书必须为该服务所知。</span><span class="sxs-lookup"><span data-stu-id="fc117-145">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="fc117-146">此元素是所有此类安全令牌服务证书的储存库。</span><span class="sxs-lookup"><span data-stu-id="fc117-146">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="fc117-147">若要添加证书，请使用 [\<knownCertificates>](knowncertificates.md) 。</span><span class="sxs-lookup"><span data-stu-id="fc117-147">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="fc117-148">为 [\<add>](add-of-knowncertificates.md) 每个证书插入一个，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="fc117-148">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 <span data-ttu-id="fc117-149">默认情况下，必须从安全令牌服务那里获取证书。</span><span class="sxs-lookup"><span data-stu-id="fc117-149">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="fc117-150">这些“已知的”证书可以确保只有合法的客户端才能访问服务。</span><span class="sxs-lookup"><span data-stu-id="fc117-150">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="fc117-151">有关使用此配置元素的详细信息，请参阅[如何：在联合身份验证服务上配置凭据](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="fc117-151">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc117-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fc117-152">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [<span data-ttu-id="fc117-153">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="fc117-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="fc117-154">如何：在联合身份验证服务上配置凭据</span><span class="sxs-lookup"><span data-stu-id="fc117-154">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
