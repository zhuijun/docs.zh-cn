---
title: <transport> 的 <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 1cb165fed9266307335482166116c4c1d62efe7e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152952"
---
# <a name="transport-of-msmqintegrationbinding"></a><span data-ttu-id="a42bc-102">\<transport> 的 \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="a42bc-102">\<transport> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="a42bc-103">定义消息队列集成传输的安全设置。</span><span class="sxs-lookup"><span data-stu-id="a42bc-103">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="a42bc-104">语法</span><span class="sxs-lookup"><span data-stu-id="a42bc-104">Syntax</span></span>  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a42bc-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="a42bc-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a42bc-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a42bc-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a42bc-107">特性</span><span class="sxs-lookup"><span data-stu-id="a42bc-107">Attributes</span></span>  
  
|<span data-ttu-id="a42bc-108">属性</span><span class="sxs-lookup"><span data-stu-id="a42bc-108">Attribute</span></span>|<span data-ttu-id="a42bc-109">说明</span><span class="sxs-lookup"><span data-stu-id="a42bc-109">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="a42bc-110">指定 MSMQ 传输必须采用什么方式对消息进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="a42bc-110">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="a42bc-111">如果将此属性设置为 `None`，则 `msmqProtectionLevel` 属性的值也必须设置为 `None`。</span><span class="sxs-lookup"><span data-stu-id="a42bc-111">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="a42bc-112">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="a42bc-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a42bc-113">-None：无身份验证。</span><span class="sxs-lookup"><span data-stu-id="a42bc-113">-   None: No authentication.</span></span><br /><span data-ttu-id="a42bc-114">-WindowsDomain：身份验证机制使用 Active Directory 获取与消息关联的 SID 的 x.509 证书。</span><span class="sxs-lookup"><span data-stu-id="a42bc-114">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="a42bc-115">然后使用它来检查队列的 ACL 以确保用户有权写入队列。</span><span class="sxs-lookup"><span data-stu-id="a42bc-115">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="a42bc-116">-Certificate：通道从证书存储区获取证书。</span><span class="sxs-lookup"><span data-stu-id="a42bc-116">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="a42bc-117">默认值为 WindowsDomain。</span><span class="sxs-lookup"><span data-stu-id="a42bc-117">The default value is WindowsDomain.</span></span> <span data-ttu-id="a42bc-118">此属性的类型为 <xref:System.ServiceModel.MsmqAuthenticationMode>。</span><span class="sxs-lookup"><span data-stu-id="a42bc-118">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="a42bc-119">指定在消息队列管理器之间传输消息时用于在网络上对消息进行加密的算法。</span><span class="sxs-lookup"><span data-stu-id="a42bc-119">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="a42bc-120">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="a42bc-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a42bc-121">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="a42bc-121">-   RC4Stream</span></span><br /><span data-ttu-id="a42bc-122">-AES</span><span class="sxs-lookup"><span data-stu-id="a42bc-122">-   AES</span></span><br /><br /> <span data-ttu-id="a42bc-123">默认值为 RC4Stream。</span><span class="sxs-lookup"><span data-stu-id="a42bc-123">The default value is RC4Stream.</span></span> <span data-ttu-id="a42bc-124">此属性的类型为 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="a42bc-124">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="a42bc-125">指定在 MSMQ 传输级别采用什么方式来保护消息。</span><span class="sxs-lookup"><span data-stu-id="a42bc-125">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="a42bc-126">加密可确保消息的完整性，同时 EncryptAndSign 可确保消息的完整性和不可否认性;也就是说，消息确实来自发件人，发件人是谁说。</span><span class="sxs-lookup"><span data-stu-id="a42bc-126">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span><br /><br /> <span data-ttu-id="a42bc-127">-有效值包括：</span><span class="sxs-lookup"><span data-stu-id="a42bc-127">-   Valid values include the following:</span></span><br /><span data-ttu-id="a42bc-128">-None：无保护。</span><span class="sxs-lookup"><span data-stu-id="a42bc-128">-   None: No protection.</span></span><br /><span data-ttu-id="a42bc-129">-Sign：对消息进行签名。</span><span class="sxs-lookup"><span data-stu-id="a42bc-129">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="a42bc-130">-EncryptAndSign：对消息进行加密和签名。</span><span class="sxs-lookup"><span data-stu-id="a42bc-130">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="a42bc-131">默认值为 Sign。</span><span class="sxs-lookup"><span data-stu-id="a42bc-131">The default value is Sign.</span></span> <span data-ttu-id="a42bc-132">此属性的类型为 ProtectionLevel。</span><span class="sxs-lookup"><span data-stu-id="a42bc-132">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="a42bc-133">-指定要在签名中计算摘要时使用的算法。</span><span class="sxs-lookup"><span data-stu-id="a42bc-133">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="a42bc-134">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="a42bc-134">Valid values include the following:</span></span><br /><span data-ttu-id="a42bc-135">-MD5</span><span class="sxs-lookup"><span data-stu-id="a42bc-135">-   MD5</span></span><br /><span data-ttu-id="a42bc-136">-SHA1</span><span class="sxs-lookup"><span data-stu-id="a42bc-136">-   SHA1</span></span><br /><span data-ttu-id="a42bc-137">-SHA256</span><span class="sxs-lookup"><span data-stu-id="a42bc-137">-   SHA256</span></span><br /><span data-ttu-id="a42bc-138">-SHA512</span><span class="sxs-lookup"><span data-stu-id="a42bc-138">-   SHA512</span></span><br /><br /> <span data-ttu-id="a42bc-139">默认值为 SHA1。</span><span class="sxs-lookup"><span data-stu-id="a42bc-139">The default value is SHA1.</span></span> <span data-ttu-id="a42bc-140">此属性的类型为 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="a42bc-140">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="a42bc-141">由于 MD5 和 SHA1 出现冲突，Microsoft 建议 SHA256 或更好。</span><span class="sxs-lookup"><span data-stu-id="a42bc-141">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a42bc-142">子元素</span><span class="sxs-lookup"><span data-stu-id="a42bc-142">Child Elements</span></span>  
 <span data-ttu-id="a42bc-143">无</span><span class="sxs-lookup"><span data-stu-id="a42bc-143">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a42bc-144">父元素</span><span class="sxs-lookup"><span data-stu-id="a42bc-144">Parent Elements</span></span>  
  
|<span data-ttu-id="a42bc-145">元素</span><span class="sxs-lookup"><span data-stu-id="a42bc-145">Element</span></span>|<span data-ttu-id="a42bc-146">描述</span><span class="sxs-lookup"><span data-stu-id="a42bc-146">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="a42bc-147">定义 MSMQ 绑定的安全设置。</span><span class="sxs-lookup"><span data-stu-id="a42bc-147">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a42bc-148">注解</span><span class="sxs-lookup"><span data-stu-id="a42bc-148">Remarks</span></span>  
 <span data-ttu-id="a42bc-149">此元素包装消息队列集成传输的安全设置。</span><span class="sxs-lookup"><span data-stu-id="a42bc-149">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="a42bc-150">消息队列集成传输和排队传输的设置是相同的。</span><span class="sxs-lookup"><span data-stu-id="a42bc-150">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="a42bc-151">使用此元素可以设置身份验证模式、加密算法、安全哈希算法和保护级别。</span><span class="sxs-lookup"><span data-stu-id="a42bc-151">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a42bc-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a42bc-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="a42bc-153">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="a42bc-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a42bc-154">绑定</span><span class="sxs-lookup"><span data-stu-id="a42bc-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a42bc-155">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="a42bc-155">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a42bc-156">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="a42bc-156">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
