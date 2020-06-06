---
title: <certificate> 的 <peer>
ms.date: 03/30/2017
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
ms.openlocfilehash: 2044dc6fb4ae688a0a3c7e29b3b7696df0d0d218
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398203"
---
# <a name="certificate-of-peer"></a><span data-ttu-id="070de-102">\<certificate> 的 \<peer></span><span class="sxs-lookup"><span data-stu-id="070de-102">\<certificate> of \<peer></span></span>
<span data-ttu-id="070de-103">指定对等方使用的证书。</span><span class="sxs-lookup"><span data-stu-id="070de-103">Specifies a certificate used by a peer.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="070de-104">语法</span><span class="sxs-lookup"><span data-stu-id="070de-104">Syntax</span></span>  
  
```xml  
<certificate findValue = "String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="070de-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="070de-105">Attributes and Elements</span></span>  
 <span data-ttu-id="070de-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="070de-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="070de-107">特性</span><span class="sxs-lookup"><span data-stu-id="070de-107">Attributes</span></span>  
  
|<span data-ttu-id="070de-108">属性</span><span class="sxs-lookup"><span data-stu-id="070de-108">Attribute</span></span>|<span data-ttu-id="070de-109">说明</span><span class="sxs-lookup"><span data-stu-id="070de-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="070de-110">一个字符串，包含要在 X.509 证书存储中搜索的值。</span><span class="sxs-lookup"><span data-stu-id="070de-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="070de-111">此属性中包含的类型必须满足指定 `x509FindType` 的要求。</span><span class="sxs-lookup"><span data-stu-id="070de-111">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="070de-112">默认值为空字符串。</span><span class="sxs-lookup"><span data-stu-id="070de-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="070de-113">指定客户端可用于验证对等方的证书的 X.509 证书存储的位置。</span><span class="sxs-lookup"><span data-stu-id="070de-113">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="070de-114">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="070de-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="070de-115">-LocalMachine：分配给本地计算机的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="070de-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="070de-116">-CurrentUser：分配给当前用户的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="070de-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="070de-117">默认值为 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="070de-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="070de-118">指定要打开的 X.509 证书存储区的名称。</span><span class="sxs-lookup"><span data-stu-id="070de-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="070de-119">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="070de-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="070de-120">-通讯簿：其他用户的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="070de-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="070de-121">-AuthRoot：第三方证书颁发机构（Ca）的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="070de-121">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="070de-122">-CertificateAuthority：中间证书颁发机构（Ca）的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="070de-122">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="070de-123">-不允许：吊销的证书的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="070de-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="070de-124">-My：个人证书的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="070de-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="070de-125">-Root：受信任的根证书颁发机构（Ca）的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="070de-125">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="070de-126">-TrustedPeople：直接受信任的人和资源的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="070de-126">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="070de-127">-TrustedPublisher：直接受信任的发布者的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="070de-127">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="070de-128">默认值为 My。</span><span class="sxs-lookup"><span data-stu-id="070de-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="070de-129">定义要执行的 X.509 搜索的类型。</span><span class="sxs-lookup"><span data-stu-id="070de-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="070de-130">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="070de-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="070de-131">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="070de-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="070de-132">-Findbysubjectname)</span><span class="sxs-lookup"><span data-stu-id="070de-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="070de-133">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="070de-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="070de-134">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="070de-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="070de-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="070de-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="070de-136">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="070de-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="070de-137">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="070de-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="070de-138">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="070de-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="070de-139">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="070de-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="070de-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="070de-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="070de-141">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="070de-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="070de-142">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="070de-142">-   FindByExtension</span></span><br /><span data-ttu-id="070de-143">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="070de-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="070de-144">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="070de-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="070de-145">`findValue` 属性中包含的类型必须满足指定 `X509FindType` 的要求。</span><span class="sxs-lookup"><span data-stu-id="070de-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="070de-146">默认值为 FindBySubjectDistinguishedName。</span><span class="sxs-lookup"><span data-stu-id="070de-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="070de-147">子元素</span><span class="sxs-lookup"><span data-stu-id="070de-147">Child Elements</span></span>  
 <span data-ttu-id="070de-148">无。</span><span class="sxs-lookup"><span data-stu-id="070de-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="070de-149">父元素</span><span class="sxs-lookup"><span data-stu-id="070de-149">Parent Elements</span></span>  
  
|<span data-ttu-id="070de-150">元素</span><span class="sxs-lookup"><span data-stu-id="070de-150">Element</span></span>|<span data-ttu-id="070de-151">描述</span><span class="sxs-lookup"><span data-stu-id="070de-151">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="070de-152">指定对等节点的当前凭据。</span><span class="sxs-lookup"><span data-stu-id="070de-152">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="070de-153">注解</span><span class="sxs-lookup"><span data-stu-id="070de-153">Remarks</span></span>  
 <span data-ttu-id="070de-154">此配置元素包含对对等网格中的邻居进行身份验证时使用的 `X509Certificate2` 实例。</span><span class="sxs-lookup"><span data-stu-id="070de-154">This configuration element contains an `X509Certificate2` instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="070de-155">有关对等编程的详细信息，请参阅对等[网络](../../../wcf/feature-details/peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="070de-155">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="070de-156">另请参阅</span><span class="sxs-lookup"><span data-stu-id="070de-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="070de-157">使用证书</span><span class="sxs-lookup"><span data-stu-id="070de-157">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="070de-158">对等网络</span><span class="sxs-lookup"><span data-stu-id="070de-158">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="070de-159">[对等通道消息身份验证](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="070de-159">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="070de-160">[对等通道自定义身份验证](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="070de-160">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="070de-161">保护对等通道应用程序</span><span class="sxs-lookup"><span data-stu-id="070de-161">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="070de-162">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="070de-162">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
