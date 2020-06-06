---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 23fe19258e09e9e8a5e05a94ccef0e40ee1cb5fd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400336"
---
# \<knownCertificates>
<span data-ttu-id="2260c-101">表示所提供的 X.509 证书的集合，这些证书用于对安全令牌服务 (STS) 颁发的安全凭据进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="2260c-101">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownCertificates>**  
  
## <a name="syntax"></a><span data-ttu-id="2260c-102">语法</span><span class="sxs-lookup"><span data-stu-id="2260c-102">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2260c-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="2260c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="2260c-104">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2260c-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2260c-105">特性</span><span class="sxs-lookup"><span data-stu-id="2260c-105">Attributes</span></span>  
 <span data-ttu-id="2260c-106">无。</span><span class="sxs-lookup"><span data-stu-id="2260c-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2260c-107">子元素</span><span class="sxs-lookup"><span data-stu-id="2260c-107">Child Elements</span></span>  
  
|<span data-ttu-id="2260c-108">元素</span><span class="sxs-lookup"><span data-stu-id="2260c-108">Element</span></span>|<span data-ttu-id="2260c-109">说明</span><span class="sxs-lookup"><span data-stu-id="2260c-109">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-knowncertificates.md)|<span data-ttu-id="2260c-110">将一个 X.509 证书添加到集合中。</span><span class="sxs-lookup"><span data-stu-id="2260c-110">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2260c-111">父元素</span><span class="sxs-lookup"><span data-stu-id="2260c-111">Parent Elements</span></span>  
  
|<span data-ttu-id="2260c-112">元素</span><span class="sxs-lookup"><span data-stu-id="2260c-112">Element</span></span>|<span data-ttu-id="2260c-113">说明</span><span class="sxs-lookup"><span data-stu-id="2260c-113">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="2260c-114">将颁发的令牌指定为服务凭据。</span><span class="sxs-lookup"><span data-stu-id="2260c-114">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2260c-115">注解</span><span class="sxs-lookup"><span data-stu-id="2260c-115">Remarks</span></span>  
 <span data-ttu-id="2260c-116">颁发的令牌方案包含三个阶段。</span><span class="sxs-lookup"><span data-stu-id="2260c-116">The issued token scenario has three stages.</span></span> <span data-ttu-id="2260c-117">在第一阶段中，尝试访问服务的客户端被称为 "*安全令牌服务*"。</span><span class="sxs-lookup"><span data-stu-id="2260c-117">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="2260c-118">然后，安全令牌服务对该客户端进行身份验证，随后向该客户端颁发一个令牌（通常是一个安全断言标记语言 (SAML) 令牌）。</span><span class="sxs-lookup"><span data-stu-id="2260c-118">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="2260c-119">接下来，客户端携带此令牌返回服务。</span><span class="sxs-lookup"><span data-stu-id="2260c-119">The client then returns to the service with the token.</span></span> <span data-ttu-id="2260c-120">服务检查该令牌，以获取使其可以对该令牌并进而对该客户端进行身份验证的数据。</span><span class="sxs-lookup"><span data-stu-id="2260c-120">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="2260c-121">若要对令牌进行身份验证，安全令牌服务所使用的证书必须为该服务所知。</span><span class="sxs-lookup"><span data-stu-id="2260c-121">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="2260c-122">[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)元素是任何此类安全令牌服务证书的储存库。</span><span class="sxs-lookup"><span data-stu-id="2260c-122">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="2260c-123">若要添加证书，请使用[ \<knownCertificates> 元素](knowncertificates.md)。</span><span class="sxs-lookup"><span data-stu-id="2260c-123">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="2260c-124">为 [\<add>](add-of-knowncertificates.md) 每个证书插入一个，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="2260c-124">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="2260c-125">默认情况下，必须从安全令牌服务那里获取证书。</span><span class="sxs-lookup"><span data-stu-id="2260c-125">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="2260c-126">这些“已知的”证书可以确保只有合法的客户端才能访问服务。</span><span class="sxs-lookup"><span data-stu-id="2260c-126">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="2260c-127">若要查看客户端通过联合服务进行身份验证所需的条件，以及有关使用此配置元素的详细信息，请参阅[如何：在联合身份验证服务上配置凭据](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="2260c-127">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="2260c-128">有关联合方案的详细信息，请参阅[联合和颁发的令牌](../../../wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="2260c-128">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="2260c-129">有关演示如何在配置中填充集合的示例，请参见 [\<add>](add-of-knowncertificates.md) 。</span><span class="sxs-lookup"><span data-stu-id="2260c-129">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2260c-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2260c-130">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<add>](add-of-knowncertificates.md)
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="2260c-131">安全行为</span><span class="sxs-lookup"><span data-stu-id="2260c-131">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="2260c-132">如何：在联合身份验证服务上配置凭据</span><span class="sxs-lookup"><span data-stu-id="2260c-132">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="2260c-133">使用证书</span><span class="sxs-lookup"><span data-stu-id="2260c-133">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="2260c-134">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="2260c-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](add-of-knowncertificates.md)
- [<span data-ttu-id="2260c-135">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="2260c-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
