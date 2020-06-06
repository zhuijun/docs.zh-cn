---
title: <scopedCertificates> 元素
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 3c06159709df0afe2a475de1e186b0114af32bc2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399959"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="9daf5-102">\<scopedCertificates> 元素</span><span class="sxs-lookup"><span data-stu-id="9daf5-102">\<scopedCertificates> Element</span></span>
<span data-ttu-id="9daf5-103">表示特定服务为身份验证提供的 X.509（作用域）证书的集合。</span><span class="sxs-lookup"><span data-stu-id="9daf5-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="9daf5-104">此集合通常用于指定联合方案中安全令牌服务的服务证书。</span><span class="sxs-lookup"><span data-stu-id="9daf5-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopedCertificates>**  
  
## <a name="syntax"></a><span data-ttu-id="9daf5-105">语法</span><span class="sxs-lookup"><span data-stu-id="9daf5-105">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9daf5-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="9daf5-106">Attributes and Elements</span></span>  
 <span data-ttu-id="9daf5-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9daf5-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9daf5-108">特性</span><span class="sxs-lookup"><span data-stu-id="9daf5-108">Attributes</span></span>  
 <span data-ttu-id="9daf5-109">无。</span><span class="sxs-lookup"><span data-stu-id="9daf5-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9daf5-110">子元素</span><span class="sxs-lookup"><span data-stu-id="9daf5-110">Child Elements</span></span>  
  
|<span data-ttu-id="9daf5-111">元素</span><span class="sxs-lookup"><span data-stu-id="9daf5-111">Element</span></span>|<span data-ttu-id="9daf5-112">说明</span><span class="sxs-lookup"><span data-stu-id="9daf5-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-scopedcertificates-element.md)|<span data-ttu-id="9daf5-113">向作用域证书集合添加 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="9daf5-113">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9daf5-114">父元素</span><span class="sxs-lookup"><span data-stu-id="9daf5-114">Parent Elements</span></span>  
  
|<span data-ttu-id="9daf5-115">元素</span><span class="sxs-lookup"><span data-stu-id="9daf5-115">Element</span></span>|<span data-ttu-id="9daf5-116">说明</span><span class="sxs-lookup"><span data-stu-id="9daf5-116">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="9daf5-117">指定客户端对服务进行身份验证时使用的证书。</span><span class="sxs-lookup"><span data-stu-id="9daf5-117">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9daf5-118">注解</span><span class="sxs-lookup"><span data-stu-id="9daf5-118">Remarks</span></span>  
 <span data-ttu-id="9daf5-119">此集合使客户端能够根据与它通信的服务的 URL 来配置要使用的服务证书。</span><span class="sxs-lookup"><span data-stu-id="9daf5-119">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="9daf5-120">这在已颁发令牌的方案中尤其有用，在这些方案中，客户端可与多个服务（终端服务以及中间的安全令牌服务）进行通信。</span><span class="sxs-lookup"><span data-stu-id="9daf5-120">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="9daf5-121">对于使用基于证书的消息安全的绑定，此证书用于加密发送给服务的消息，并期望服务用它来对客户端的应答进行签名。</span><span class="sxs-lookup"><span data-stu-id="9daf5-121">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="9daf5-122">如果绑定需要服务的证书，但在 ScopedCertificates 中未找到服务 URL 的特定证书，则使用默认证书。</span><span class="sxs-lookup"><span data-stu-id="9daf5-122">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="9daf5-123">有关详细信息，请参阅[如何：创建联合客户端](../../../wcf/feature-details/how-to-create-a-federated-client.md)中的 "范围内的证书" 一节。</span><span class="sxs-lookup"><span data-stu-id="9daf5-123">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9daf5-124">示例</span><span class="sxs-lookup"><span data-stu-id="9daf5-124">Example</span></span>  
 <span data-ttu-id="9daf5-125">下面的示例指定一个服务证书，以便客户端与域名位于 HTTP 协议的终结点进行通信时使用 `http://www.contoso.com` 。</span><span class="sxs-lookup"><span data-stu-id="9daf5-125">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
```xml  
<serviceCertificate>
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="9daf5-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9daf5-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="9daf5-127">使用证书</span><span class="sxs-lookup"><span data-stu-id="9daf5-127">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="9daf5-128">如何：创建联合客户端</span><span class="sxs-lookup"><span data-stu-id="9daf5-128">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [\<add>](add-of-scopedcertificates-element.md)
- [<span data-ttu-id="9daf5-129">保证客户端的安全</span><span class="sxs-lookup"><span data-stu-id="9daf5-129">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="9daf5-130">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="9daf5-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
