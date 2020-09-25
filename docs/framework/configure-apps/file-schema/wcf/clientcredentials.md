---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: 6094006df24ee824c419a783ab29d7604757577c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201455"
---
# \<clientCredentials>

<span data-ttu-id="c77a1-101">指定用于向服务验证客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="c77a1-101">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="c77a1-102">语法</span><span class="sxs-lookup"><span data-stu-id="c77a1-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c77a1-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c77a1-103">Attributes and Elements</span></span>  

 <span data-ttu-id="c77a1-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c77a1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c77a1-105">特性</span><span class="sxs-lookup"><span data-stu-id="c77a1-105">Attributes</span></span>  
  
|<span data-ttu-id="c77a1-106">属性</span><span class="sxs-lookup"><span data-stu-id="c77a1-106">Attribute</span></span>|<span data-ttu-id="c77a1-107">描述</span><span class="sxs-lookup"><span data-stu-id="c77a1-107">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="c77a1-108">一个布尔值，指定在运行时选择客户端凭据的过程中是否可以涉及交互式用户。</span><span class="sxs-lookup"><span data-stu-id="c77a1-108">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="c77a1-109">默认值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="c77a1-109">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="c77a1-110">一个指定此配置元素的类型的字符串。</span><span class="sxs-lookup"><span data-stu-id="c77a1-110">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c77a1-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c77a1-111">Child Elements</span></span>  
  
|<span data-ttu-id="c77a1-112">元素</span><span class="sxs-lookup"><span data-stu-id="c77a1-112">Element</span></span>|<span data-ttu-id="c77a1-113">描述</span><span class="sxs-lookup"><span data-stu-id="c77a1-113">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="c77a1-114">指定用于向服务验证客户端身份的证书。</span><span class="sxs-lookup"><span data-stu-id="c77a1-114">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="c77a1-115">此元素的类型为 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>。</span><span class="sxs-lookup"><span data-stu-id="c77a1-115">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[\<httpDigest>](httpdigest-element.md)|<span data-ttu-id="c77a1-116">指定用于向服务验证客户端身份的摘要。</span><span class="sxs-lookup"><span data-stu-id="c77a1-116">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="c77a1-117">此元素的类型为 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>。</span><span class="sxs-lookup"><span data-stu-id="c77a1-117">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="c77a1-118">指定用于向安全令牌服务 (STS) 验证客户端身份的自定义令牌类型。</span><span class="sxs-lookup"><span data-stu-id="c77a1-118">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="c77a1-119">此元素的类型为 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>。</span><span class="sxs-lookup"><span data-stu-id="c77a1-119">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="c77a1-120">指定一个当前对等凭据。</span><span class="sxs-lookup"><span data-stu-id="c77a1-120">Specifies a current peer credential.</span></span> <span data-ttu-id="c77a1-121">此元素的类型为 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。</span><span class="sxs-lookup"><span data-stu-id="c77a1-121">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="c77a1-122">指定用于向客户端验证服务身份的证书，并提供一个用于设置证书选项的结构。</span><span class="sxs-lookup"><span data-stu-id="c77a1-122">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="c77a1-123">必须从服务以带外方式向客户端提供此证书。</span><span class="sxs-lookup"><span data-stu-id="c77a1-123">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="c77a1-124">此元素的类型为 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>。</span><span class="sxs-lookup"><span data-stu-id="c77a1-124">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[\<windows>](windows-of-clientcredentials-element.md)|<span data-ttu-id="c77a1-125">指定 Windows 凭据。</span><span class="sxs-lookup"><span data-stu-id="c77a1-125">Specifies a Windows credential.</span></span> <span data-ttu-id="c77a1-126">默认值是当前线程的凭据。</span><span class="sxs-lookup"><span data-stu-id="c77a1-126">The default is the credential of the current thread.</span></span> <span data-ttu-id="c77a1-127">此元素的类型为 <xref:System.ServiceModel.Configuration.WindowsClientElement>。</span><span class="sxs-lookup"><span data-stu-id="c77a1-127">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c77a1-128">父元素</span><span class="sxs-lookup"><span data-stu-id="c77a1-128">Parent Elements</span></span>  
  
|<span data-ttu-id="c77a1-129">元素</span><span class="sxs-lookup"><span data-stu-id="c77a1-129">Element</span></span>|<span data-ttu-id="c77a1-130">描述</span><span class="sxs-lookup"><span data-stu-id="c77a1-130">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c77a1-131">指定终结点行为。</span><span class="sxs-lookup"><span data-stu-id="c77a1-131">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c77a1-132">备注</span><span class="sxs-lookup"><span data-stu-id="c77a1-132">Remarks</span></span>  

 <span data-ttu-id="c77a1-133">在要求相互进行身份验证的情况下，需要使用客户端凭据使客户端通过服务的身份验证。</span><span class="sxs-lookup"><span data-stu-id="c77a1-133">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="c77a1-134">当客户端必须使用服务的证书来保护发送到服务的消息时，还可以使用该配置节来指定服务证书。</span><span class="sxs-lookup"><span data-stu-id="c77a1-134">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c77a1-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="c77a1-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="c77a1-136">安全行为</span><span class="sxs-lookup"><span data-stu-id="c77a1-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="c77a1-137">保证客户端的安全</span><span class="sxs-lookup"><span data-stu-id="c77a1-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
