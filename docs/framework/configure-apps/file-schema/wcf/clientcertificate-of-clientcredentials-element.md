---
title: <clientCertificate> of <clientCredentials> 元素
ms.date: 03/30/2017
ms.assetid: 3b3fa000-3434-4142-a178-11903bdd2c5d
ms.openlocfilehash: 74209c43dcafb1e27bb1d7943ee7832eaea0ef57
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204939"
---
# <a name="clientcertificate-of-clientcredentials-element"></a><span data-ttu-id="743c1-102">\<clientCertificate> of \<clientCredentials> 元素</span><span class="sxs-lookup"><span data-stu-id="743c1-102">\<clientCertificate> of \<clientCredentials> Element</span></span>

<span data-ttu-id="743c1-103">定义用于针对服务进行客户端身份验证的 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="743c1-103">Defines an X.509 certificate used to authenticate a client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="743c1-104">语法</span><span class="sxs-lookup"><span data-stu-id="743c1-104">Syntax</span></span>  
  
```xml  
<clientCertificate findValue="String"
                   storeLocation="LocalMachine/CurrentUser"
                   storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                   X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="743c1-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="743c1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="743c1-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="743c1-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="743c1-107">特性</span><span class="sxs-lookup"><span data-stu-id="743c1-107">Attributes</span></span>  
  
|<span data-ttu-id="743c1-108">属性</span><span class="sxs-lookup"><span data-stu-id="743c1-108">Attribute</span></span>|<span data-ttu-id="743c1-109">描述</span><span class="sxs-lookup"><span data-stu-id="743c1-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="743c1-110">一个字符串，包含要在 X.509 证书存储中搜索的值。</span><span class="sxs-lookup"><span data-stu-id="743c1-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="743c1-111">此属性中包含的类型必须满足 `X509FindType` 属性值的要求。</span><span class="sxs-lookup"><span data-stu-id="743c1-111">The type contained in the attribute must satisfy the requirements of the `X509FindType` attribute value.</span></span> <span data-ttu-id="743c1-112">默认值为空字符串。</span><span class="sxs-lookup"><span data-stu-id="743c1-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="743c1-113">指定客户端用于向服务验证自身身份的 X.509 证书的位置。</span><span class="sxs-lookup"><span data-stu-id="743c1-113">Specifies the location of the X.509 certificate that the client uses to authenticate itself to the service.</span></span> <span data-ttu-id="743c1-114">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="743c1-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="743c1-115">-LocalMachine：分配给本地计算机的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="743c1-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="743c1-116">-CurrentUser：分配给当前用户的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="743c1-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="743c1-117">默认值为 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="743c1-117">The default is LocalMachine.</span></span> <span data-ttu-id="743c1-118">此属性的类型为 <xref:System.Security.Cryptography.X509Certificates.StoreLocation>。</span><span class="sxs-lookup"><span data-stu-id="743c1-118">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
|`storeName`|<span data-ttu-id="743c1-119">指定要搜索的 X.509 证书存储的名称。</span><span class="sxs-lookup"><span data-stu-id="743c1-119">Specifies the name of the X.509 certificate store to search.</span></span> <span data-ttu-id="743c1-120">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="743c1-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="743c1-121">-通讯簿：其他用户的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="743c1-121">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="743c1-122">-AuthRoot：第三方证书颁发机构的证书存储 (Ca) 。</span><span class="sxs-lookup"><span data-stu-id="743c1-122">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="743c1-123">-CertificateAuthority：用于中间证书颁发机构的证书存储 (Ca) 。</span><span class="sxs-lookup"><span data-stu-id="743c1-123">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="743c1-124">-不允许：吊销的证书的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="743c1-124">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="743c1-125">-My：个人证书的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="743c1-125">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="743c1-126">-Root：受信任的根证书颁发机构的证书存储 (Ca) 。</span><span class="sxs-lookup"><span data-stu-id="743c1-126">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="743c1-127">-TrustedPeople：直接受信任的人和资源的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="743c1-127">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="743c1-128">-TrustedPublisher：直接受信任的发布者的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="743c1-128">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="743c1-129">默认值为 My。</span><span class="sxs-lookup"><span data-stu-id="743c1-129">The default is My.</span></span> <span data-ttu-id="743c1-130">此属性的类型为 <xref:System.Security.Cryptography.X509Certificates.StoreName>。</span><span class="sxs-lookup"><span data-stu-id="743c1-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreName>.</span></span>|  
|<span data-ttu-id="743c1-131">X509FindType</span><span class="sxs-lookup"><span data-stu-id="743c1-131">X509FindType</span></span>|<span data-ttu-id="743c1-132">定义要执行的 X.509 搜索的类型。</span><span class="sxs-lookup"><span data-stu-id="743c1-132">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="743c1-133">`findValue` 属性中包含的类型必须满足此属性的要求。</span><span class="sxs-lookup"><span data-stu-id="743c1-133">The type contained in the `findValue` attribute must satisfy the requirements of this attribute.</span></span> <span data-ttu-id="743c1-134">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="743c1-134">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="743c1-135">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="743c1-135">-   FindByThumbPrint</span></span><br /><span data-ttu-id="743c1-136">-Findbysubjectname) </span><span class="sxs-lookup"><span data-stu-id="743c1-136">-   FindBySubjectName</span></span><br /><span data-ttu-id="743c1-137">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="743c1-137">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="743c1-138">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="743c1-138">-   FindByIssuerName</span></span><br /><span data-ttu-id="743c1-139">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="743c1-139">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="743c1-140">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="743c1-140">-   FindBySerialNumber</span></span><br /><span data-ttu-id="743c1-141">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="743c1-141">-   FindByTimeValid</span></span><br /><span data-ttu-id="743c1-142">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="743c1-142">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="743c1-143">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="743c1-143">-   FindByTemplateName</span></span><br /><span data-ttu-id="743c1-144">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="743c1-144">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="743c1-145">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="743c1-145">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="743c1-146">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="743c1-146">-   FindByExtension</span></span><br /><span data-ttu-id="743c1-147">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="743c1-147">-   FindByKeyUsage</span></span><br /><span data-ttu-id="743c1-148">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="743c1-148">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="743c1-149">默认值为 FindBySubjectDistinguishedName。</span><span class="sxs-lookup"><span data-stu-id="743c1-149">The default value is FindBySubjectDistinguishedName.</span></span> <span data-ttu-id="743c1-150">此属性的类型为 <xref:System.Security.Cryptography.X509Certificates.X509FindType>。</span><span class="sxs-lookup"><span data-stu-id="743c1-150">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509FindType>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="743c1-151">子元素</span><span class="sxs-lookup"><span data-stu-id="743c1-151">Child Elements</span></span>  

 <span data-ttu-id="743c1-152">无。</span><span class="sxs-lookup"><span data-stu-id="743c1-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="743c1-153">父元素</span><span class="sxs-lookup"><span data-stu-id="743c1-153">Parent Elements</span></span>  
  
|<span data-ttu-id="743c1-154">元素</span><span class="sxs-lookup"><span data-stu-id="743c1-154">Element</span></span>|<span data-ttu-id="743c1-155">描述</span><span class="sxs-lookup"><span data-stu-id="743c1-155">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="743c1-156">指定用于向服务验证客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="743c1-156">Specifies the credentials used to authenticate the client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="743c1-157">备注</span><span class="sxs-lookup"><span data-stu-id="743c1-157">Remarks</span></span>  

 <span data-ttu-id="743c1-158">此配置元素指定用于对具有此元素的客户端进行身份验证的证书。</span><span class="sxs-lookup"><span data-stu-id="743c1-158">This configuration element specifies the certificate used to authenticate the client with this element.</span></span> <span data-ttu-id="743c1-159">有关详细信息，请参阅 [如何：指定客户端凭据值](../../../wcf/how-to-specify-client-credential-values.md)。</span><span class="sxs-lookup"><span data-stu-id="743c1-159">For more information, see [How to: Specify Client Credential Values](../../../wcf/how-to-specify-client-credential-values.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="743c1-160">请参阅</span><span class="sxs-lookup"><span data-stu-id="743c1-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [<span data-ttu-id="743c1-161">安全行为</span><span class="sxs-lookup"><span data-stu-id="743c1-161">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="743c1-162">如何：指定客户端凭据值</span><span class="sxs-lookup"><span data-stu-id="743c1-162">How to: Specify Client Credential Values</span></span>](../../../wcf/how-to-specify-client-credential-values.md)
- [<span data-ttu-id="743c1-163">保证客户端的安全</span><span class="sxs-lookup"><span data-stu-id="743c1-163">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="743c1-164">使用证书</span><span class="sxs-lookup"><span data-stu-id="743c1-164">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="743c1-165">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="743c1-165">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
