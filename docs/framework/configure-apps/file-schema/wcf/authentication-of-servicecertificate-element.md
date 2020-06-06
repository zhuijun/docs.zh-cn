---
title: <authentication>of <serviceCertificate> 元素
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 29170f032469b4d55b50f57ca06ce403a5aeaf2c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398231"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="14d48-102">\<authentication>of \<serviceCertificate> 元素</span><span class="sxs-lookup"><span data-stu-id="14d48-102">\<authentication> of \<serviceCertificate> Element</span></span>
<span data-ttu-id="14d48-103">指定客户端代理用于对使用 SSL/TLS 协商获取的服务证书进行身份验证的设置。</span><span class="sxs-lookup"><span data-stu-id="14d48-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a><span data-ttu-id="14d48-104">语法</span><span class="sxs-lookup"><span data-stu-id="14d48-104">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14d48-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="14d48-105">Attributes and Elements</span></span>  
 <span data-ttu-id="14d48-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="14d48-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14d48-107">特性</span><span class="sxs-lookup"><span data-stu-id="14d48-107">Attributes</span></span>  
  
|<span data-ttu-id="14d48-108">属性</span><span class="sxs-lookup"><span data-stu-id="14d48-108">Attribute</span></span>|<span data-ttu-id="14d48-109">说明</span><span class="sxs-lookup"><span data-stu-id="14d48-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="14d48-110">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="14d48-110">customCertificateValidatorType</span></span>|<span data-ttu-id="14d48-111">字符串。</span><span class="sxs-lookup"><span data-stu-id="14d48-111">String.</span></span> <span data-ttu-id="14d48-112">一个用于验证自定义类型的类型和程序集。</span><span class="sxs-lookup"><span data-stu-id="14d48-112">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="14d48-113">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="14d48-113">certificateValidationMode</span></span>|<span data-ttu-id="14d48-114">指定用来验证凭据的三种模式之一。</span><span class="sxs-lookup"><span data-stu-id="14d48-114">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="14d48-115">如果设置为 `Custom`，则还必须提供 customCertificateValidator。</span><span class="sxs-lookup"><span data-stu-id="14d48-115">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="14d48-116">默认为 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="14d48-116">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="14d48-117">revocationMode</span><span class="sxs-lookup"><span data-stu-id="14d48-117">revocationMode</span></span>|<span data-ttu-id="14d48-118">用于检查吊销证书列表 (CRL) 的一种模式。</span><span class="sxs-lookup"><span data-stu-id="14d48-118">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="14d48-119">默认为 `Online`。</span><span class="sxs-lookup"><span data-stu-id="14d48-119">The default is `Online`.</span></span>|  
|<span data-ttu-id="14d48-120">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="14d48-120">trustedStoreLocation</span></span>|<span data-ttu-id="14d48-121">两个系统存储位置之一：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="14d48-121">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="14d48-122">在向客户端协商服务证书时使用此值。</span><span class="sxs-lookup"><span data-stu-id="14d48-122">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="14d48-123">针对指定存储位置中的 "**受信任人**" 存储执行验证。</span><span class="sxs-lookup"><span data-stu-id="14d48-123">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="14d48-124">默认为 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="14d48-124">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="14d48-125">customCertificateValidator 属性</span><span class="sxs-lookup"><span data-stu-id="14d48-125">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="14d48-126">值</span><span class="sxs-lookup"><span data-stu-id="14d48-126">Value</span></span>|<span data-ttu-id="14d48-127">说明</span><span class="sxs-lookup"><span data-stu-id="14d48-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14d48-128">String</span><span class="sxs-lookup"><span data-stu-id="14d48-128">String</span></span>|<span data-ttu-id="14d48-129">指定类型名称和程序集以及用于查找类型的其他数据。</span><span class="sxs-lookup"><span data-stu-id="14d48-129">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="14d48-130">certificateValidationMode 属性</span><span class="sxs-lookup"><span data-stu-id="14d48-130">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="14d48-131">值</span><span class="sxs-lookup"><span data-stu-id="14d48-131">Value</span></span>|<span data-ttu-id="14d48-132">说明</span><span class="sxs-lookup"><span data-stu-id="14d48-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14d48-133">枚举</span><span class="sxs-lookup"><span data-stu-id="14d48-133">Enumeration</span></span>|<span data-ttu-id="14d48-134">下列值之一：None、PeerTrust、ChainTrust、PeerOrChainTrust 和 Custom。</span><span class="sxs-lookup"><span data-stu-id="14d48-134">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="14d48-135">有关详细信息，请参阅使用[证书](../../../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="14d48-135">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="14d48-136">revocationMode 属性</span><span class="sxs-lookup"><span data-stu-id="14d48-136">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="14d48-137">值</span><span class="sxs-lookup"><span data-stu-id="14d48-137">Value</span></span>|<span data-ttu-id="14d48-138">说明</span><span class="sxs-lookup"><span data-stu-id="14d48-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14d48-139">枚举</span><span class="sxs-lookup"><span data-stu-id="14d48-139">Enumeration</span></span>|<span data-ttu-id="14d48-140">下列值之一：NoCheck、Online 和 Offline。</span><span class="sxs-lookup"><span data-stu-id="14d48-140">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="14d48-141">有关详细信息，请参阅使用[证书](../../../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="14d48-141">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="14d48-142">trustedStoreLocation 属性</span><span class="sxs-lookup"><span data-stu-id="14d48-142">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="14d48-143">值</span><span class="sxs-lookup"><span data-stu-id="14d48-143">Value</span></span>|<span data-ttu-id="14d48-144">说明</span><span class="sxs-lookup"><span data-stu-id="14d48-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14d48-145">枚举</span><span class="sxs-lookup"><span data-stu-id="14d48-145">Enumeration</span></span>|<span data-ttu-id="14d48-146">下列值之一：LocalMachine 或 CurrentUser。</span><span class="sxs-lookup"><span data-stu-id="14d48-146">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="14d48-147">默认值为 CurrentUser。</span><span class="sxs-lookup"><span data-stu-id="14d48-147">The default is CurrentUser.</span></span> <span data-ttu-id="14d48-148">如果客户端应用程序在系统帐户下运行，则证书通常位于 LocalMachine 中。</span><span class="sxs-lookup"><span data-stu-id="14d48-148">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="14d48-149">如果客户端应用程序在用户帐户下运行，则证书通常位于 CurrentUser 中。</span><span class="sxs-lookup"><span data-stu-id="14d48-149">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14d48-150">子元素</span><span class="sxs-lookup"><span data-stu-id="14d48-150">Child Elements</span></span>  
 <span data-ttu-id="14d48-151">无。</span><span class="sxs-lookup"><span data-stu-id="14d48-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14d48-152">父元素</span><span class="sxs-lookup"><span data-stu-id="14d48-152">Parent Elements</span></span>  
  
|<span data-ttu-id="14d48-153">元素</span><span class="sxs-lookup"><span data-stu-id="14d48-153">Element</span></span>|<span data-ttu-id="14d48-154">描述</span><span class="sxs-lookup"><span data-stu-id="14d48-154">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="14d48-155">指定客户端对服务进行身份验证时使用的证书。</span><span class="sxs-lookup"><span data-stu-id="14d48-155">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14d48-156">注解</span><span class="sxs-lookup"><span data-stu-id="14d48-156">Remarks</span></span>  
 <span data-ttu-id="14d48-157">此配置元素的 `certificateValidationMode` 属性指定用于对证书进行身份验证的信任级别。</span><span class="sxs-lookup"><span data-stu-id="14d48-157">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="14d48-158">默认情况下，该级别设置为 `ChainTrust`，它指定每个证书都必须存在于某个证书层次结构中，而该层次结构以位于证书链顶端的受信任的证书颁发机构结束。</span><span class="sxs-lookup"><span data-stu-id="14d48-158">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="14d48-159">这是最安全的模式。</span><span class="sxs-lookup"><span data-stu-id="14d48-159">This is the most secure mode.</span></span> <span data-ttu-id="14d48-160">您还可以将此值设置为 `PeerOrChainTrust`，该值指定受信任的链中的证书以及自行颁发的证书（对等信任）都被接受。</span><span class="sxs-lookup"><span data-stu-id="14d48-160">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="14d48-161">因为不需要从受信任的证书颁发机构那里购买自行颁发的证书，所以可以在开发和调试客户端和服务时使用此值。</span><span class="sxs-lookup"><span data-stu-id="14d48-161">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="14d48-162">在部署客户端时，请改用 `ChainTrust` 值。</span><span class="sxs-lookup"><span data-stu-id="14d48-162">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="14d48-163">您也可以将该值设置为 `Custom` 或 `None`。</span><span class="sxs-lookup"><span data-stu-id="14d48-163">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="14d48-164">若要使用 `Custom` 值，还必须将 `customCertificateValidator` 属性设置为程序集和用于验证证书的类型。</span><span class="sxs-lookup"><span data-stu-id="14d48-164">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="14d48-165">若要创建您自己的自定义验证程序，必须从 X509CertificateValidator 抽象类进行继承。</span><span class="sxs-lookup"><span data-stu-id="14d48-165">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="14d48-166">有关详细信息，请参阅[如何：创建使用自定义证书验证程序的服务](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)。</span><span class="sxs-lookup"><span data-stu-id="14d48-166">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="14d48-167">`revocationMode` 属性指定检查证书是否已吊销的方式。</span><span class="sxs-lookup"><span data-stu-id="14d48-167">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="14d48-168">默认值为 `online`，指示将自动检查证书是否已吊销。</span><span class="sxs-lookup"><span data-stu-id="14d48-168">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="14d48-169">有关详细信息，请参阅使用[证书](../../../wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="14d48-169">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="14d48-170">示例</span><span class="sxs-lookup"><span data-stu-id="14d48-170">Example</span></span>  
 <span data-ttu-id="14d48-171">以下示例执行两项任务。</span><span class="sxs-lookup"><span data-stu-id="14d48-171">The following example does two tasks.</span></span> <span data-ttu-id="14d48-172">它首先指定一个服务证书，以便客户端与域名位于 HTTP 协议的终结点进行通信时使用 `www.contoso.com` 。</span><span class="sxs-lookup"><span data-stu-id="14d48-172">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="14d48-173">然后，它指定了在身份验证过程中使用的吊销模式和存储位置。</span><span class="sxs-lookup"><span data-stu-id="14d48-173">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="14d48-174">另请参阅</span><span class="sxs-lookup"><span data-stu-id="14d48-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="14d48-175">安全行为</span><span class="sxs-lookup"><span data-stu-id="14d48-175">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="14d48-176">使用证书</span><span class="sxs-lookup"><span data-stu-id="14d48-176">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="14d48-177">如何：创建使用自定义证书验证程序的服务</span><span class="sxs-lookup"><span data-stu-id="14d48-177">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="14d48-178">保证客户端的安全</span><span class="sxs-lookup"><span data-stu-id="14d48-178">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="14d48-179">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="14d48-179">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
