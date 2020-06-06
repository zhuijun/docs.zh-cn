---
title: <certificate>of <clientCertificate> 元素
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: d0c4ef9d3657d2dfa787feb3576beda09d1997a3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400536"
---
# <a name="certificate-of-clientcertificate-element"></a><span data-ttu-id="71cc7-102">\<certificate>of \<clientCertificate> 元素</span><span class="sxs-lookup"><span data-stu-id="71cc7-102">\<certificate> of \<clientCertificate> Element</span></span>
<span data-ttu-id="71cc7-103">指定用于对消息进行签名和加密的 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="71cc7-103">Specifies an X.509 certificate used to sign and encrypt messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="71cc7-104">语法</span><span class="sxs-lookup"><span data-stu-id="71cc7-104">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71cc7-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="71cc7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="71cc7-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="71cc7-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71cc7-107">特性</span><span class="sxs-lookup"><span data-stu-id="71cc7-107">Attributes</span></span>  
  
|<span data-ttu-id="71cc7-108">属性</span><span class="sxs-lookup"><span data-stu-id="71cc7-108">Attribute</span></span>|<span data-ttu-id="71cc7-109">说明</span><span class="sxs-lookup"><span data-stu-id="71cc7-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="71cc7-110">一个字符串，包含要在 X.509 证书存储中搜索的值。</span><span class="sxs-lookup"><span data-stu-id="71cc7-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="71cc7-111">此属性中包含的类型必须满足指定 X509FindType 的需求。</span><span class="sxs-lookup"><span data-stu-id="71cc7-111">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="71cc7-112">默认值为空字符串。</span><span class="sxs-lookup"><span data-stu-id="71cc7-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="71cc7-113">指定客户端可用于验证服务器证书的 X.509 证书存储的位置。</span><span class="sxs-lookup"><span data-stu-id="71cc7-113">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="71cc7-114">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="71cc7-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="71cc7-115">-LocalMachine：分配给本地计算机的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="71cc7-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="71cc7-116">-CurrentUser：分配给当前用户的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="71cc7-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="71cc7-117">默认值为 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="71cc7-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="71cc7-118">指定要打开的 X.509 证书存储区的名称。</span><span class="sxs-lookup"><span data-stu-id="71cc7-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="71cc7-119">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="71cc7-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="71cc7-120">-通讯簿：其他用户的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="71cc7-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="71cc7-121">-AuthRoot：第三方证书颁发机构（Ca）的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="71cc7-121">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="71cc7-122">-证书颁发机构：中间证书颁发机构（Ca）的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="71cc7-122">-   CertificationAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="71cc7-123">-不允许：吊销的证书的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="71cc7-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="71cc7-124">-My：个人证书的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="71cc7-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="71cc7-125">-Root：受信任的根证书颁发机构（Ca）的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="71cc7-125">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="71cc7-126">-TrustedPeople：直接受信任的人和资源的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="71cc7-126">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="71cc7-127">-TrustedPublisher：直接受信任的发布者的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="71cc7-127">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="71cc7-128">默认值为 My。</span><span class="sxs-lookup"><span data-stu-id="71cc7-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="71cc7-129">定义要执行的 X.509 搜索的类型。</span><span class="sxs-lookup"><span data-stu-id="71cc7-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="71cc7-130">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="71cc7-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="71cc7-131">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="71cc7-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="71cc7-132">-Findbysubjectname)</span><span class="sxs-lookup"><span data-stu-id="71cc7-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="71cc7-133">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="71cc7-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="71cc7-134">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="71cc7-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="71cc7-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="71cc7-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="71cc7-136">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="71cc7-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="71cc7-137">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="71cc7-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="71cc7-138">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="71cc7-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="71cc7-139">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="71cc7-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="71cc7-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="71cc7-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="71cc7-141">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="71cc7-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="71cc7-142">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="71cc7-142">-   FindByExtension</span></span><br /><span data-ttu-id="71cc7-143">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="71cc7-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="71cc7-144">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="71cc7-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="71cc7-145">`findValue` 属性中包含的类型必须满足指定 X509FindType 的要求。</span><span class="sxs-lookup"><span data-stu-id="71cc7-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="71cc7-146">默认值为 FindBySubjectDistinguishedName。</span><span class="sxs-lookup"><span data-stu-id="71cc7-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71cc7-147">子元素</span><span class="sxs-lookup"><span data-stu-id="71cc7-147">Child Elements</span></span>  
 <span data-ttu-id="71cc7-148">无。</span><span class="sxs-lookup"><span data-stu-id="71cc7-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71cc7-149">父元素</span><span class="sxs-lookup"><span data-stu-id="71cc7-149">Parent Elements</span></span>  
  
|<span data-ttu-id="71cc7-150">元素</span><span class="sxs-lookup"><span data-stu-id="71cc7-150">Element</span></span>|<span data-ttu-id="71cc7-151">说明</span><span class="sxs-lookup"><span data-stu-id="71cc7-151">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a><span data-ttu-id="71cc7-152">备注</span><span class="sxs-lookup"><span data-stu-id="71cc7-152">Remarks</span></span>  
 <span data-ttu-id="71cc7-153">当服务必须事先拥有客户端的证书才能与该客户端进行安全通信时，可使用 `<certificate>` 元素。</span><span class="sxs-lookup"><span data-stu-id="71cc7-153">The `<certificate>` element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="71cc7-154">使用双工通信模式时，会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="71cc7-154">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="71cc7-155">在更为典型的请求/响应模式中，客户端会将其证书包含在请求中，服务将使用该证书对发送回客户端的响应进行加密和签名。</span><span class="sxs-lookup"><span data-stu-id="71cc7-155">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="71cc7-156">但是，在双工通信模式中，服务没有来自客户端的请求，因此服务需要事先具有客户端的证书以确保发送到客户端的消息的安全。</span><span class="sxs-lookup"><span data-stu-id="71cc7-156">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="71cc7-157">因此，您必须通过带外协商来获取客户端的证书，并使用此元素指定该证书。</span><span class="sxs-lookup"><span data-stu-id="71cc7-157">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="71cc7-158">有关双工服务的详细信息，请参阅[如何：创建双工协定](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="71cc7-158">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="71cc7-159">示例</span><span class="sxs-lookup"><span data-stu-id="71cc7-159">Example</span></span>  
 <span data-ttu-id="71cc7-160">下面的代码指定如何在 `<authentication>` 元素中查找适当的 X.509 证书和自定义验证类型。</span><span class="sxs-lookup"><span data-stu-id="71cc7-160">The following code specifies how to find an appropriate X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="71cc7-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="71cc7-161">See also</span></span>

- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [<span data-ttu-id="71cc7-162">安全行为</span><span class="sxs-lookup"><span data-stu-id="71cc7-162">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="71cc7-163">如何：创建使用自定义证书验证程序的服务</span><span class="sxs-lookup"><span data-stu-id="71cc7-163">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="71cc7-164">使用证书</span><span class="sxs-lookup"><span data-stu-id="71cc7-164">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
