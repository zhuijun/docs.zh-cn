---
title: <add> 的 <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 29b067e6ec20992084f9ab3bab087222bdd56da2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400612"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="1e546-102">\<add> 的 \<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="1e546-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="1e546-103">向已知证书集合添加 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="1e546-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="1e546-104">语法</span><span class="sxs-lookup"><span data-stu-id="1e546-104">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e546-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1e546-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1e546-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1e546-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e546-107">特性</span><span class="sxs-lookup"><span data-stu-id="1e546-107">Attributes</span></span>  
  
|<span data-ttu-id="1e546-108">属性</span><span class="sxs-lookup"><span data-stu-id="1e546-108">Attribute</span></span>|<span data-ttu-id="1e546-109">说明</span><span class="sxs-lookup"><span data-stu-id="1e546-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1e546-110">findValue</span><span class="sxs-lookup"><span data-stu-id="1e546-110">findValue</span></span>|<span data-ttu-id="1e546-111">字符串。</span><span class="sxs-lookup"><span data-stu-id="1e546-111">String.</span></span> <span data-ttu-id="1e546-112">要搜索的值。</span><span class="sxs-lookup"><span data-stu-id="1e546-112">The value to search for.</span></span>|  
|<span data-ttu-id="1e546-113">storeLocation</span><span class="sxs-lookup"><span data-stu-id="1e546-113">storeLocation</span></span>|<span data-ttu-id="1e546-114">枚举。</span><span class="sxs-lookup"><span data-stu-id="1e546-114">Enumeration.</span></span> <span data-ttu-id="1e546-115">要搜索的两个存储位置之一。</span><span class="sxs-lookup"><span data-stu-id="1e546-115">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="1e546-116">storeName</span><span class="sxs-lookup"><span data-stu-id="1e546-116">storeName</span></span>|<span data-ttu-id="1e546-117">枚举。</span><span class="sxs-lookup"><span data-stu-id="1e546-117">Enumeration.</span></span> <span data-ttu-id="1e546-118">要搜索的系统存储之一。</span><span class="sxs-lookup"><span data-stu-id="1e546-118">One of the system stores to search.</span></span>|  
|<span data-ttu-id="1e546-119">x509FindType</span><span class="sxs-lookup"><span data-stu-id="1e546-119">x509FindType</span></span>|<span data-ttu-id="1e546-120">枚举。</span><span class="sxs-lookup"><span data-stu-id="1e546-120">Enumeration.</span></span> <span data-ttu-id="1e546-121">要搜索的证书字段之一。</span><span class="sxs-lookup"><span data-stu-id="1e546-121">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="1e546-122">findValue 属性</span><span class="sxs-lookup"><span data-stu-id="1e546-122">findValue Attribute</span></span>  
  
|<span data-ttu-id="1e546-123">值</span><span class="sxs-lookup"><span data-stu-id="1e546-123">Value</span></span>|<span data-ttu-id="1e546-124">说明</span><span class="sxs-lookup"><span data-stu-id="1e546-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1e546-125">String</span><span class="sxs-lookup"><span data-stu-id="1e546-125">String</span></span>|<span data-ttu-id="1e546-126">值取决于搜索的字段（由 X509FindType 属性指定）。</span><span class="sxs-lookup"><span data-stu-id="1e546-126">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="1e546-127">例如，如果搜索指纹，则此值必须为十六进制数字字符串。</span><span class="sxs-lookup"><span data-stu-id="1e546-127">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="1e546-128">x509FindType 属性</span><span class="sxs-lookup"><span data-stu-id="1e546-128">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="1e546-129">值</span><span class="sxs-lookup"><span data-stu-id="1e546-129">Value</span></span>|<span data-ttu-id="1e546-130">说明</span><span class="sxs-lookup"><span data-stu-id="1e546-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1e546-131">枚举</span><span class="sxs-lookup"><span data-stu-id="1e546-131">Enumeration</span></span>|<span data-ttu-id="1e546-132">值包括：FindByThumbprint、FindBySubjectName、FindBySubjectDistinguishedName、FindByIssuerName、FindByIssuerDistinguishedName、FindBySerialNumber、FindByTimeValid、FindByTimeNotYetValid、FindBySerialNumber、FindByTimeExpired、FindByTemplateName、FindByApplicationPolicy、FindByCertificatePolicy、FindByExtension、FindByKeyUsage 和 FindBySubjectKeyIdentifier。</span><span class="sxs-lookup"><span data-stu-id="1e546-132">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="1e546-133">storeLocation 属性</span><span class="sxs-lookup"><span data-stu-id="1e546-133">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="1e546-134">值</span><span class="sxs-lookup"><span data-stu-id="1e546-134">Value</span></span>|<span data-ttu-id="1e546-135">说明</span><span class="sxs-lookup"><span data-stu-id="1e546-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1e546-136">枚举</span><span class="sxs-lookup"><span data-stu-id="1e546-136">Enumeration</span></span>|<span data-ttu-id="1e546-137">CurrentUser 或 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="1e546-137">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="1e546-138">storeName 属性</span><span class="sxs-lookup"><span data-stu-id="1e546-138">storeName Attribute</span></span>  
  
|<span data-ttu-id="1e546-139">值</span><span class="sxs-lookup"><span data-stu-id="1e546-139">Value</span></span>|<span data-ttu-id="1e546-140">说明</span><span class="sxs-lookup"><span data-stu-id="1e546-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1e546-141">枚举</span><span class="sxs-lookup"><span data-stu-id="1e546-141">Enumeration</span></span>|<span data-ttu-id="1e546-142">值包括：AddressBook、AuthRoot、CertificateAuthority、Disallowed、My、Root、TrustedPeople 和 TrustedPublisher。</span><span class="sxs-lookup"><span data-stu-id="1e546-142">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e546-143">子元素</span><span class="sxs-lookup"><span data-stu-id="1e546-143">Child Elements</span></span>  
 <span data-ttu-id="1e546-144">无。</span><span class="sxs-lookup"><span data-stu-id="1e546-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e546-145">父元素</span><span class="sxs-lookup"><span data-stu-id="1e546-145">Parent Elements</span></span>  
  
|<span data-ttu-id="1e546-146">元素</span><span class="sxs-lookup"><span data-stu-id="1e546-146">Element</span></span>|<span data-ttu-id="1e546-147">描述</span><span class="sxs-lookup"><span data-stu-id="1e546-147">Description</span></span>|  
|-------------|-----------------|  
|[\<knownCertificates>](knowncertificates.md)|<span data-ttu-id="1e546-148">表示一个 X.509 证书集合，这些证书由安全令牌服务 (STS) 提供以用于验证安全令牌。</span><span class="sxs-lookup"><span data-stu-id="1e546-148">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e546-149">注解</span><span class="sxs-lookup"><span data-stu-id="1e546-149">Remarks</span></span>  
 <span data-ttu-id="1e546-150">颁发的令牌方案包含三个阶段。</span><span class="sxs-lookup"><span data-stu-id="1e546-150">The issued token scenario has three stages.</span></span> <span data-ttu-id="1e546-151">在第一阶段中，尝试访问服务的客户端被称为 "*安全令牌服务*"。</span><span class="sxs-lookup"><span data-stu-id="1e546-151">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="1e546-152">然后，安全令牌服务对该客户端进行身份验证，随后向该客户端颁发一个令牌（通常是一个安全断言标记语言 (SAML) 令牌）。</span><span class="sxs-lookup"><span data-stu-id="1e546-152">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="1e546-153">接下来，客户端携带此令牌返回服务。</span><span class="sxs-lookup"><span data-stu-id="1e546-153">The client then returns to the service with the token.</span></span> <span data-ttu-id="1e546-154">服务检查该令牌，以获取使其可以对该令牌并进而对该客户端进行身份验证的数据。</span><span class="sxs-lookup"><span data-stu-id="1e546-154">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="1e546-155">若要对令牌进行身份验证，安全令牌服务所使用的证书必须为该服务所知。</span><span class="sxs-lookup"><span data-stu-id="1e546-155">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="1e546-156">[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)元素是任何此类安全令牌服务证书的储存库。</span><span class="sxs-lookup"><span data-stu-id="1e546-156">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="1e546-157">若要添加证书，请使用 [\<knownCertificates>](knowncertificates.md) 。</span><span class="sxs-lookup"><span data-stu-id="1e546-157">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="1e546-158">为每个证书插入一个[ \<add> 元素 \<knownCertificates> 元素](add-of-knowncertificates.md)，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="1e546-158">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="1e546-159">默认情况下，必须从安全令牌服务那里获取证书。</span><span class="sxs-lookup"><span data-stu-id="1e546-159">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="1e546-160">这些“已知的”证书可以确保只有合法的客户端才能访问服务。</span><span class="sxs-lookup"><span data-stu-id="1e546-160">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="1e546-161">若要查看客户端通过联合服务进行身份验证所需的条件，以及有关使用此配置元素的详细信息，请参阅[如何：在联合身份验证服务上配置凭据](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="1e546-161">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="1e546-162">有关联合方案的详细信息，请参阅[联合和颁发的令牌](../../../wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="1e546-162">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e546-163">示例</span><span class="sxs-lookup"><span data-stu-id="1e546-163">Example</span></span>  
 <span data-ttu-id="1e546-164">下面的示例将证书添加到任意 STS 证书的存储库。</span><span class="sxs-lookup"><span data-stu-id="1e546-164">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <serviceCredentials>
      <issuedTokenAuthentication>
        <knownCertificates>
          <add findValue="www.contoso.com"
               storeLocation="LocalMachine"
               storeName="CertificateAuthority"
               x509FindType="FindByIssuerName" />
        </knownCertificates>
      </issuedTokenAuthentication>
    </serviceCredentials>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="1e546-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1e546-165">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<knownCertificates>](knowncertificates.md)
- [<span data-ttu-id="1e546-166">使用证书</span><span class="sxs-lookup"><span data-stu-id="1e546-166">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="1e546-167">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="1e546-167">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="1e546-168">如何：在联合身份验证服务上配置凭据</span><span class="sxs-lookup"><span data-stu-id="1e546-168">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="1e546-169">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="1e546-169">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
