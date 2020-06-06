---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: f295fe48e194611c80b78c0c23ab3e66ea1c0b64
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400502"
---
# \<clientCredentials>
<span data-ttu-id="b3180-101">指定用于向服务验证客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="b3180-101">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="b3180-102">语法</span><span class="sxs-lookup"><span data-stu-id="b3180-102">Syntax</span></span>  
  
```xml  
<clientCredentials type="String"
                   supportInteractive="Boolean" >
  <clientCertificate>
  </clientCertificate>
  <digest>
  </digest>
  <isuedToken>
  </isuedToken>
  <peer>
  </peer>
  <serviceCertificate>
  </serviceCertificate>
  <windowsAuthentication>
  </windowsAuthentication>
</clientCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3180-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b3180-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b3180-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b3180-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3180-105">特性</span><span class="sxs-lookup"><span data-stu-id="b3180-105">Attributes</span></span>  
  
|<span data-ttu-id="b3180-106">属性</span><span class="sxs-lookup"><span data-stu-id="b3180-106">Attribute</span></span>|<span data-ttu-id="b3180-107">说明</span><span class="sxs-lookup"><span data-stu-id="b3180-107">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="b3180-108">一个布尔值，指定在运行时选择客户端凭据的过程中是否可以涉及交互式用户。</span><span class="sxs-lookup"><span data-stu-id="b3180-108">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="b3180-109">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="b3180-109">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="b3180-110">一个指定此配置元素的类型的字符串。</span><span class="sxs-lookup"><span data-stu-id="b3180-110">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3180-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b3180-111">Child Elements</span></span>  
  
|<span data-ttu-id="b3180-112">元素</span><span class="sxs-lookup"><span data-stu-id="b3180-112">Element</span></span>|<span data-ttu-id="b3180-113">描述</span><span class="sxs-lookup"><span data-stu-id="b3180-113">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="b3180-114">指定用于向服务验证客户端身份的证书。</span><span class="sxs-lookup"><span data-stu-id="b3180-114">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="b3180-115">此元素的类型为 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>。</span><span class="sxs-lookup"><span data-stu-id="b3180-115">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[\<httpDigest>](httpdigest-element.md)|<span data-ttu-id="b3180-116">指定用于向服务验证客户端身份的摘要。</span><span class="sxs-lookup"><span data-stu-id="b3180-116">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="b3180-117">此元素的类型为 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>。</span><span class="sxs-lookup"><span data-stu-id="b3180-117">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="b3180-118">指定用于向安全令牌服务 (STS) 验证客户端身份的自定义令牌类型。</span><span class="sxs-lookup"><span data-stu-id="b3180-118">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="b3180-119">此元素的类型为 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>。</span><span class="sxs-lookup"><span data-stu-id="b3180-119">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="b3180-120">指定一个当前对等凭据。</span><span class="sxs-lookup"><span data-stu-id="b3180-120">Specifies a current peer credential.</span></span> <span data-ttu-id="b3180-121">此元素的类型为 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。</span><span class="sxs-lookup"><span data-stu-id="b3180-121">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="b3180-122">指定用于向客户端验证服务身份的证书，并提供一个用于设置证书选项的结构。</span><span class="sxs-lookup"><span data-stu-id="b3180-122">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="b3180-123">必须从服务以带外方式向客户端提供此证书。</span><span class="sxs-lookup"><span data-stu-id="b3180-123">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="b3180-124">此元素的类型为 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>。</span><span class="sxs-lookup"><span data-stu-id="b3180-124">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[\<windows>](windows-of-clientcredentials-element.md)|<span data-ttu-id="b3180-125">指定 Windows 凭据。</span><span class="sxs-lookup"><span data-stu-id="b3180-125">Specifies a Windows credential.</span></span> <span data-ttu-id="b3180-126">默认值是当前线程的凭据。</span><span class="sxs-lookup"><span data-stu-id="b3180-126">The default is the credential of the current thread.</span></span> <span data-ttu-id="b3180-127">此元素的类型为 <xref:System.ServiceModel.Configuration.WindowsClientElement>。</span><span class="sxs-lookup"><span data-stu-id="b3180-127">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b3180-128">父元素</span><span class="sxs-lookup"><span data-stu-id="b3180-128">Parent Elements</span></span>  
  
|<span data-ttu-id="b3180-129">元素</span><span class="sxs-lookup"><span data-stu-id="b3180-129">Element</span></span>|<span data-ttu-id="b3180-130">描述</span><span class="sxs-lookup"><span data-stu-id="b3180-130">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b3180-131">指定终结点行为。</span><span class="sxs-lookup"><span data-stu-id="b3180-131">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3180-132">注解</span><span class="sxs-lookup"><span data-stu-id="b3180-132">Remarks</span></span>  
 <span data-ttu-id="b3180-133">在要求相互进行身份验证的情况下，需要使用客户端凭据使客户端通过服务的身份验证。</span><span class="sxs-lookup"><span data-stu-id="b3180-133">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="b3180-134">当客户端必须使用服务的证书来保护发送到服务的消息时，还可以使用该配置节来指定服务证书。</span><span class="sxs-lookup"><span data-stu-id="b3180-134">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3180-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3180-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="b3180-136">安全行为</span><span class="sxs-lookup"><span data-stu-id="b3180-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="b3180-137">保证客户端的安全</span><span class="sxs-lookup"><span data-stu-id="b3180-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
