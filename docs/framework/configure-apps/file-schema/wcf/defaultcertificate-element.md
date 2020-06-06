---
title: <defaultCertificate> 元素
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: cce236bf80fa00f01a3b5f4680d975f83fde0c16
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400417"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="8d305-102">\<defaultCertificate> 元素</span><span class="sxs-lookup"><span data-stu-id="8d305-102">\<defaultCertificate> Element</span></span>
<span data-ttu-id="8d305-103">指定在服务或 STS 未通过协商协议提供证书时要使用的 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="8d305-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="8d305-104">语法</span><span class="sxs-lookup"><span data-stu-id="8d305-104">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d305-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="8d305-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8d305-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8d305-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d305-107">特性</span><span class="sxs-lookup"><span data-stu-id="8d305-107">Attributes</span></span>  
  
|<span data-ttu-id="8d305-108">属性</span><span class="sxs-lookup"><span data-stu-id="8d305-108">Attribute</span></span>|<span data-ttu-id="8d305-109">说明</span><span class="sxs-lookup"><span data-stu-id="8d305-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d305-110">findValue</span><span class="sxs-lookup"><span data-stu-id="8d305-110">findValue</span></span>|<span data-ttu-id="8d305-111">字符串。</span><span class="sxs-lookup"><span data-stu-id="8d305-111">String.</span></span> <span data-ttu-id="8d305-112">要搜索的值。</span><span class="sxs-lookup"><span data-stu-id="8d305-112">The value to search for.</span></span>|  
|<span data-ttu-id="8d305-113">x509FindType</span><span class="sxs-lookup"><span data-stu-id="8d305-113">x509FindType</span></span>|<span data-ttu-id="8d305-114">枚举。</span><span class="sxs-lookup"><span data-stu-id="8d305-114">Enumeration.</span></span> <span data-ttu-id="8d305-115">要搜索的证书字段之一。</span><span class="sxs-lookup"><span data-stu-id="8d305-115">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="8d305-116">storeLocation</span><span class="sxs-lookup"><span data-stu-id="8d305-116">storeLocation</span></span>|<span data-ttu-id="8d305-117">枚举。</span><span class="sxs-lookup"><span data-stu-id="8d305-117">Enumeration.</span></span> <span data-ttu-id="8d305-118">要搜索的两个系统存储位置之一。</span><span class="sxs-lookup"><span data-stu-id="8d305-118">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="8d305-119">storeName</span><span class="sxs-lookup"><span data-stu-id="8d305-119">storeName</span></span>|<span data-ttu-id="8d305-120">枚举。</span><span class="sxs-lookup"><span data-stu-id="8d305-120">Enumeration.</span></span> <span data-ttu-id="8d305-121">要搜索的系统存储之一。</span><span class="sxs-lookup"><span data-stu-id="8d305-121">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="8d305-122">findValue 属性</span><span class="sxs-lookup"><span data-stu-id="8d305-122">findValue Attribute</span></span>  
  
|<span data-ttu-id="8d305-123">值</span><span class="sxs-lookup"><span data-stu-id="8d305-123">Value</span></span>|<span data-ttu-id="8d305-124">说明</span><span class="sxs-lookup"><span data-stu-id="8d305-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8d305-125">String</span><span class="sxs-lookup"><span data-stu-id="8d305-125">String</span></span>|<span data-ttu-id="8d305-126">值取决于搜索的字段（由 X509FindType 属性指定）。</span><span class="sxs-lookup"><span data-stu-id="8d305-126">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="8d305-127">例如，如果搜索指纹，则此值必须为十六进制数字字符串。</span><span class="sxs-lookup"><span data-stu-id="8d305-127">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="8d305-128">x509FindType 属性</span><span class="sxs-lookup"><span data-stu-id="8d305-128">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="8d305-129">值</span><span class="sxs-lookup"><span data-stu-id="8d305-129">Value</span></span>|<span data-ttu-id="8d305-130">说明</span><span class="sxs-lookup"><span data-stu-id="8d305-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8d305-131">枚举</span><span class="sxs-lookup"><span data-stu-id="8d305-131">Enumeration</span></span>|<span data-ttu-id="8d305-132">值包括：FindByThumbprint、FindBySubjectName、FindBySubjectDistinguishedName、FindByIssuerName、FindByIssuerDistinguishedName、FindBySerialNumber、FindByTimeValid、FindByTimeNotYetValid、FindBySerialNumber、FindByTimeExpired、FindByTemplateName、FindByApplicationPolicy、FindByCertificatePolicy、FindByExtension、FindByKeyUsage 和 FindBySubjectKeyIdentifier。</span><span class="sxs-lookup"><span data-stu-id="8d305-132">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="8d305-133">storeLocation 属性</span><span class="sxs-lookup"><span data-stu-id="8d305-133">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="8d305-134">值</span><span class="sxs-lookup"><span data-stu-id="8d305-134">Value</span></span>|<span data-ttu-id="8d305-135">说明</span><span class="sxs-lookup"><span data-stu-id="8d305-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8d305-136">枚举</span><span class="sxs-lookup"><span data-stu-id="8d305-136">Enumeration</span></span>|<span data-ttu-id="8d305-137">CurrentUser 或 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="8d305-137">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="8d305-138">storeName 属性</span><span class="sxs-lookup"><span data-stu-id="8d305-138">storeName Attribute</span></span>  
  
|<span data-ttu-id="8d305-139">值</span><span class="sxs-lookup"><span data-stu-id="8d305-139">Value</span></span>|<span data-ttu-id="8d305-140">说明</span><span class="sxs-lookup"><span data-stu-id="8d305-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8d305-141">枚举</span><span class="sxs-lookup"><span data-stu-id="8d305-141">Enumeration</span></span>|<span data-ttu-id="8d305-142">值包括：AddressBook、AuthRoot、CertificateAuthority、Disallowed、My、Root、TrustedPeople 和 TrustedPublisher。</span><span class="sxs-lookup"><span data-stu-id="8d305-142">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d305-143">子元素</span><span class="sxs-lookup"><span data-stu-id="8d305-143">Child Elements</span></span>  
 <span data-ttu-id="8d305-144">无。</span><span class="sxs-lookup"><span data-stu-id="8d305-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d305-145">父元素</span><span class="sxs-lookup"><span data-stu-id="8d305-145">Parent Elements</span></span>  
  
|<span data-ttu-id="8d305-146">元素</span><span class="sxs-lookup"><span data-stu-id="8d305-146">Element</span></span>|<span data-ttu-id="8d305-147">描述</span><span class="sxs-lookup"><span data-stu-id="8d305-147">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="8d305-148">指定客户端对服务进行身份验证时使用的证书。</span><span class="sxs-lookup"><span data-stu-id="8d305-148">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d305-149">注解</span><span class="sxs-lookup"><span data-stu-id="8d305-149">Remarks</span></span>  
 <span data-ttu-id="8d305-150">对于使用基于证书的消息安全的绑定，此配置元素指定的证书用于加密发送给服务的消息，并期望服务用它来对客户端的应答进行签名。</span><span class="sxs-lookup"><span data-stu-id="8d305-150">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="8d305-151">如果服务未指定任何证书，它只存储要使用的一个证书。</span><span class="sxs-lookup"><span data-stu-id="8d305-151">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d305-152">示例</span><span class="sxs-lookup"><span data-stu-id="8d305-152">Example</span></span>  
 <span data-ttu-id="8d305-153">下面的示例指定一个证书，该证书用于其 URI 以开头的终结点 `http://www.contoso.com` ，以及用于所有不执行证书协商的其他终结点的证书。</span><span class="sxs-lookup"><span data-stu-id="8d305-153">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="8d305-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d305-154">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="8d305-155">使用证书</span><span class="sxs-lookup"><span data-stu-id="8d305-155">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="8d305-156">保证客户端的安全</span><span class="sxs-lookup"><span data-stu-id="8d305-156">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="8d305-157">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="8d305-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
