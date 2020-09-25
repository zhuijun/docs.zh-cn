---
title: <add> 的 <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 453593918de15613edb801cca8a16c9dbf71aa90
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176079"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="9ed46-102">\<add> 的 \<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="9ed46-102">\<add> of \<knownCertificates></span></span>

<span data-ttu-id="9ed46-103">向已知证书集合添加 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="9ed46-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="9ed46-104">语法</span><span class="sxs-lookup"><span data-stu-id="9ed46-104">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ed46-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="9ed46-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9ed46-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9ed46-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ed46-107">特性</span><span class="sxs-lookup"><span data-stu-id="9ed46-107">Attributes</span></span>  
  
|<span data-ttu-id="9ed46-108">属性</span><span class="sxs-lookup"><span data-stu-id="9ed46-108">Attribute</span></span>|<span data-ttu-id="9ed46-109">描述</span><span class="sxs-lookup"><span data-stu-id="9ed46-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9ed46-110">findValue</span><span class="sxs-lookup"><span data-stu-id="9ed46-110">findValue</span></span>|<span data-ttu-id="9ed46-111">字符串。</span><span class="sxs-lookup"><span data-stu-id="9ed46-111">String.</span></span> <span data-ttu-id="9ed46-112">要搜索的值。</span><span class="sxs-lookup"><span data-stu-id="9ed46-112">The value to search for.</span></span>|  
|<span data-ttu-id="9ed46-113">storeLocation</span><span class="sxs-lookup"><span data-stu-id="9ed46-113">storeLocation</span></span>|<span data-ttu-id="9ed46-114">枚举。</span><span class="sxs-lookup"><span data-stu-id="9ed46-114">Enumeration.</span></span> <span data-ttu-id="9ed46-115">要搜索的两个存储位置之一。</span><span class="sxs-lookup"><span data-stu-id="9ed46-115">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="9ed46-116">storeName</span><span class="sxs-lookup"><span data-stu-id="9ed46-116">storeName</span></span>|<span data-ttu-id="9ed46-117">枚举。</span><span class="sxs-lookup"><span data-stu-id="9ed46-117">Enumeration.</span></span> <span data-ttu-id="9ed46-118">要搜索的系统存储之一。</span><span class="sxs-lookup"><span data-stu-id="9ed46-118">One of the system stores to search.</span></span>|  
|<span data-ttu-id="9ed46-119">x509FindType</span><span class="sxs-lookup"><span data-stu-id="9ed46-119">x509FindType</span></span>|<span data-ttu-id="9ed46-120">枚举。</span><span class="sxs-lookup"><span data-stu-id="9ed46-120">Enumeration.</span></span> <span data-ttu-id="9ed46-121">要搜索的证书字段之一。</span><span class="sxs-lookup"><span data-stu-id="9ed46-121">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="9ed46-122">findValue 属性</span><span class="sxs-lookup"><span data-stu-id="9ed46-122">findValue Attribute</span></span>  
  
|<span data-ttu-id="9ed46-123">值</span><span class="sxs-lookup"><span data-stu-id="9ed46-123">Value</span></span>|<span data-ttu-id="9ed46-124">说明</span><span class="sxs-lookup"><span data-stu-id="9ed46-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9ed46-125">字符串</span><span class="sxs-lookup"><span data-stu-id="9ed46-125">String</span></span>|<span data-ttu-id="9ed46-126">值取决于搜索的字段（由 X509FindType 属性指定）。</span><span class="sxs-lookup"><span data-stu-id="9ed46-126">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="9ed46-127">例如，如果搜索指纹，则此值必须为十六进制数字字符串。</span><span class="sxs-lookup"><span data-stu-id="9ed46-127">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="9ed46-128">x509FindType 属性</span><span class="sxs-lookup"><span data-stu-id="9ed46-128">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="9ed46-129">值</span><span class="sxs-lookup"><span data-stu-id="9ed46-129">Value</span></span>|<span data-ttu-id="9ed46-130">描述</span><span class="sxs-lookup"><span data-stu-id="9ed46-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9ed46-131">枚举</span><span class="sxs-lookup"><span data-stu-id="9ed46-131">Enumeration</span></span>|<span data-ttu-id="9ed46-132">值包括：FindByThumbprint、FindBySubjectName、FindBySubjectDistinguishedName、FindByIssuerName、FindByIssuerDistinguishedName、FindBySerialNumber、FindByTimeValid、FindByTimeNotYetValid、FindBySerialNumber、FindByTimeExpired、FindByTemplateName、FindByApplicationPolicy、FindByCertificatePolicy、FindByExtension、FindByKeyUsage 和 FindBySubjectKeyIdentifier。</span><span class="sxs-lookup"><span data-stu-id="9ed46-132">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="9ed46-133">storeLocation 属性</span><span class="sxs-lookup"><span data-stu-id="9ed46-133">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="9ed46-134">值</span><span class="sxs-lookup"><span data-stu-id="9ed46-134">Value</span></span>|<span data-ttu-id="9ed46-135">描述</span><span class="sxs-lookup"><span data-stu-id="9ed46-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9ed46-136">枚举</span><span class="sxs-lookup"><span data-stu-id="9ed46-136">Enumeration</span></span>|<span data-ttu-id="9ed46-137">CurrentUser 或 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="9ed46-137">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="9ed46-138">storeName 属性</span><span class="sxs-lookup"><span data-stu-id="9ed46-138">storeName Attribute</span></span>  
  
|<span data-ttu-id="9ed46-139">值</span><span class="sxs-lookup"><span data-stu-id="9ed46-139">Value</span></span>|<span data-ttu-id="9ed46-140">描述</span><span class="sxs-lookup"><span data-stu-id="9ed46-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9ed46-141">枚举</span><span class="sxs-lookup"><span data-stu-id="9ed46-141">Enumeration</span></span>|<span data-ttu-id="9ed46-142">值包括：AddressBook、AuthRoot、CertificateAuthority、Disallowed、My、Root、TrustedPeople 和 TrustedPublisher。</span><span class="sxs-lookup"><span data-stu-id="9ed46-142">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ed46-143">子元素</span><span class="sxs-lookup"><span data-stu-id="9ed46-143">Child Elements</span></span>  

 <span data-ttu-id="9ed46-144">无。</span><span class="sxs-lookup"><span data-stu-id="9ed46-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ed46-145">父元素</span><span class="sxs-lookup"><span data-stu-id="9ed46-145">Parent Elements</span></span>  
  
|<span data-ttu-id="9ed46-146">元素</span><span class="sxs-lookup"><span data-stu-id="9ed46-146">Element</span></span>|<span data-ttu-id="9ed46-147">描述</span><span class="sxs-lookup"><span data-stu-id="9ed46-147">Description</span></span>|  
|-------------|-----------------|  
|[\<knownCertificates>](knowncertificates.md)|<span data-ttu-id="9ed46-148">表示一个 X.509 证书集合，这些证书由安全令牌服务 (STS) 提供以用于验证安全令牌。</span><span class="sxs-lookup"><span data-stu-id="9ed46-148">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ed46-149">备注</span><span class="sxs-lookup"><span data-stu-id="9ed46-149">Remarks</span></span>  

 <span data-ttu-id="9ed46-150">颁发的令牌方案包含三个阶段。</span><span class="sxs-lookup"><span data-stu-id="9ed46-150">The issued token scenario has three stages.</span></span> <span data-ttu-id="9ed46-151">在第一阶段中，尝试访问服务的客户端被称为 " *安全令牌服务*"。</span><span class="sxs-lookup"><span data-stu-id="9ed46-151">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="9ed46-152">然后，安全令牌服务对该客户端进行身份验证，随后向该客户端颁发一个令牌（通常是一个安全断言标记语言 (SAML) 令牌）。</span><span class="sxs-lookup"><span data-stu-id="9ed46-152">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="9ed46-153">接下来，客户端携带此令牌返回服务。</span><span class="sxs-lookup"><span data-stu-id="9ed46-153">The client then returns to the service with the token.</span></span> <span data-ttu-id="9ed46-154">服务检查该令牌，以获取使其可以对该令牌并进而对该客户端进行身份验证的数据。</span><span class="sxs-lookup"><span data-stu-id="9ed46-154">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="9ed46-155">若要对令牌进行身份验证，安全令牌服务所使用的证书必须为该服务所知。</span><span class="sxs-lookup"><span data-stu-id="9ed46-155">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="9ed46-156">[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)元素是任何此类安全令牌服务证书的储存库。</span><span class="sxs-lookup"><span data-stu-id="9ed46-156">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="9ed46-157">若要添加证书，请使用 [\<knownCertificates>](knowncertificates.md) 。</span><span class="sxs-lookup"><span data-stu-id="9ed46-157">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="9ed46-158">为每个证书插入一个[ \<add> 元素 \<knownCertificates> 元素](add-of-knowncertificates.md)，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="9ed46-158">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="9ed46-159">默认情况下，必须从安全令牌服务那里获取证书。</span><span class="sxs-lookup"><span data-stu-id="9ed46-159">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="9ed46-160">这些“已知的”证书可以确保只有合法的客户端才能访问服务。</span><span class="sxs-lookup"><span data-stu-id="9ed46-160">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="9ed46-161">若要查看客户端通过联合服务进行身份验证所需的条件，以及有关使用此配置元素的详细信息，请参阅 [如何：在联合身份验证服务上配置凭据](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="9ed46-161">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="9ed46-162">有关联合方案的详细信息，请参阅 [联合和颁发的令牌](../../../wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="9ed46-162">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ed46-163">示例</span><span class="sxs-lookup"><span data-stu-id="9ed46-163">Example</span></span>  

 <span data-ttu-id="9ed46-164">下面的示例将证书添加到任意 STS 证书的存储库。</span><span class="sxs-lookup"><span data-stu-id="9ed46-164">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9ed46-165">请参阅</span><span class="sxs-lookup"><span data-stu-id="9ed46-165">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<knownCertificates>](knowncertificates.md)
- [<span data-ttu-id="9ed46-166">使用证书</span><span class="sxs-lookup"><span data-stu-id="9ed46-166">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="9ed46-167">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="9ed46-167">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9ed46-168">如何：在联合身份验证服务上配置凭据</span><span class="sxs-lookup"><span data-stu-id="9ed46-168">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="9ed46-169">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="9ed46-169">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
