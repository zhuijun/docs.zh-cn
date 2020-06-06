---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 90a34a4a52b4c7a2e67d733fecba132818cac4fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399656"
---
# \<serviceCredentials>
<span data-ttu-id="e5572-101">指定要用于对服务进行身份验证的凭据以及与客户端凭据验证相关的设置。</span><span class="sxs-lookup"><span data-stu-id="e5572-101">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="e5572-102">语法</span><span class="sxs-lookup"><span data-stu-id="e5572-102">Syntax</span></span>  
  
```xml  
<serviceCredentials type="String">
  <clientCertificate>
  </clientCertificate>
  <issuedTokenAuthentication>
  </issuedTokenAuthentication>
  <peer>
  </peer>
  <secureConversationAuthentication>
  </secureConversationAuthentication>
  <serviceCertificate>
  </serviceCertificate>
  <userNameAuthentication>
  </userNameAuthentication>
  <windowsAuthentication>
  </windowsAuthentication>
</serviceCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5572-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e5572-103">Attributes and Elements</span></span>  
 <span data-ttu-id="e5572-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e5572-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5572-105">特性</span><span class="sxs-lookup"><span data-stu-id="e5572-105">Attributes</span></span>  
  
|<span data-ttu-id="e5572-106">属性</span><span class="sxs-lookup"><span data-stu-id="e5572-106">Attribute</span></span>|<span data-ttu-id="e5572-107">说明</span><span class="sxs-lookup"><span data-stu-id="e5572-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="e5572-108">一个指定此配置元素的类型的字符串。</span><span class="sxs-lookup"><span data-stu-id="e5572-108">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5572-109">子元素</span><span class="sxs-lookup"><span data-stu-id="e5572-109">Child Elements</span></span>  
  
|<span data-ttu-id="e5572-110">元素</span><span class="sxs-lookup"><span data-stu-id="e5572-110">Element</span></span>|<span data-ttu-id="e5572-111">描述</span><span class="sxs-lookup"><span data-stu-id="e5572-111">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="e5572-112">指定证书，当可在带外使用客户端证书时，将使用该证书。</span><span class="sxs-lookup"><span data-stu-id="e5572-112">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="e5572-113">此元素还指定客户端证书验证设置。</span><span class="sxs-lookup"><span data-stu-id="e5572-113">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="e5572-114">此元素的类型为 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="e5572-114">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="e5572-115">指定此服务的当前颁发令牌。</span><span class="sxs-lookup"><span data-stu-id="e5572-115">Specifies the current issued token for this service.</span></span> <span data-ttu-id="e5572-116">此元素的类型为 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="e5572-116">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="e5572-117">指定对等节点的当前凭据。</span><span class="sxs-lookup"><span data-stu-id="e5572-117">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="e5572-118">此元素的类型为 <xref:System.ServiceModel.Configuration.PeerCredentialElement>。</span><span class="sxs-lookup"><span data-stu-id="e5572-118">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<secureConversationAuthentication>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="e5572-119">指定安全对话的当前凭据。</span><span class="sxs-lookup"><span data-stu-id="e5572-119">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="e5572-120">此元素的类型为 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="e5572-120">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="e5572-121">指定服务用于标识自身的证书。</span><span class="sxs-lookup"><span data-stu-id="e5572-121">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="e5572-122">此元素的类型为 <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="e5572-122">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[\<userNameAuthentication>](usernameauthentication.md)|<span data-ttu-id="e5572-123">指定用户名密码验证的设置。</span><span class="sxs-lookup"><span data-stu-id="e5572-123">Specifies the settings for username password validation.</span></span> <span data-ttu-id="e5572-124">此元素的类型为 <xref:System.ServiceModel.Configuration.UserNameServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="e5572-124">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[\<windowsAuthentication>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="e5572-125">指定 Windows 凭据验证的设置。</span><span class="sxs-lookup"><span data-stu-id="e5572-125">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="e5572-126">此元素的类型为 <xref:System.ServiceModel.Configuration.WindowsServiceElement>。</span><span class="sxs-lookup"><span data-stu-id="e5572-126">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e5572-127">父元素</span><span class="sxs-lookup"><span data-stu-id="e5572-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e5572-128">元素</span><span class="sxs-lookup"><span data-stu-id="e5572-128">Element</span></span>|<span data-ttu-id="e5572-129">描述</span><span class="sxs-lookup"><span data-stu-id="e5572-129">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="e5572-130">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="e5572-130">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5572-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e5572-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="e5572-132">安全行为</span><span class="sxs-lookup"><span data-stu-id="e5572-132">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
