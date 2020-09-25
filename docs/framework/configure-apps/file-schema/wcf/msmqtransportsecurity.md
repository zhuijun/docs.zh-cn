---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 9d28f3f08e9c3984c055567df03f2839709a1522
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204640"
---
# \<msmqTransportSecurity>

<span data-ttu-id="d28a5-101">指定自定义绑定的 MSMQ 传输的安全设置。</span><span class="sxs-lookup"><span data-stu-id="d28a5-101">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegration>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="d28a5-102">语法</span><span class="sxs-lookup"><span data-stu-id="d28a5-102">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d28a5-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="d28a5-103">Attributes and Elements</span></span>  

 <span data-ttu-id="d28a5-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d28a5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d28a5-105">特性</span><span class="sxs-lookup"><span data-stu-id="d28a5-105">Attributes</span></span>  
  
|<span data-ttu-id="d28a5-106">属性</span><span class="sxs-lookup"><span data-stu-id="d28a5-106">Attribute</span></span>|<span data-ttu-id="d28a5-107">描述</span><span class="sxs-lookup"><span data-stu-id="d28a5-107">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="d28a5-108">指定 MSMQ 传输必须采用什么方式对消息进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="d28a5-108">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="d28a5-109">如果将此属性设置为 `None`，则 `msmqProtectionLevel` 属性的值也必须设置为 `None`。</span><span class="sxs-lookup"><span data-stu-id="d28a5-109">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="d28a5-110">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="d28a5-110">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d28a5-111">-None：无身份验证。</span><span class="sxs-lookup"><span data-stu-id="d28a5-111">-   None: No authentication.</span></span><br /><span data-ttu-id="d28a5-112">-Windows：身份验证机制使用 Active Directory 获取与消息关联的 SID 的 x.509 证书。</span><span class="sxs-lookup"><span data-stu-id="d28a5-112">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="d28a5-113">然后使用它来检查队列的 ACL 以确保用户有权写入队列。</span><span class="sxs-lookup"><span data-stu-id="d28a5-113">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="d28a5-114">-Certificate：通道从证书存储区获取证书。</span><span class="sxs-lookup"><span data-stu-id="d28a5-114">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="d28a5-115">默认值为 Windows。</span><span class="sxs-lookup"><span data-stu-id="d28a5-115">The default value is Windows.</span></span> <span data-ttu-id="d28a5-116">此属性的类型为 <xref:System.ServiceModel.MsmqAuthenticationMode>。</span><span class="sxs-lookup"><span data-stu-id="d28a5-116">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="d28a5-117">指定在消息队列管理器之间传输消息时用于在网络上对消息进行加密的算法。</span><span class="sxs-lookup"><span data-stu-id="d28a5-117">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="d28a5-118">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="d28a5-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d28a5-119">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="d28a5-119">-   RC4Stream</span></span><br /><span data-ttu-id="d28a5-120">-AES</span><span class="sxs-lookup"><span data-stu-id="d28a5-120">-   AES</span></span><br /><br /> <span data-ttu-id="d28a5-121">默认值为 RC4Stream。</span><span class="sxs-lookup"><span data-stu-id="d28a5-121">The default value is RC4Stream.</span></span> <span data-ttu-id="d28a5-122">此属性的类型为 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="d28a5-122">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="d28a5-123">指定在 MSMQ 传输级别采用什么方式来保护消息。</span><span class="sxs-lookup"><span data-stu-id="d28a5-123">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="d28a5-124">加密可确保消息的完整性，同时 EncryptAndSign 可确保消息的完整性和不可否认性;也就是说，消息确实来自发件人，发件人是谁说。</span><span class="sxs-lookup"><span data-stu-id="d28a5-124">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="d28a5-125">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="d28a5-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d28a5-126">-None：无保护。</span><span class="sxs-lookup"><span data-stu-id="d28a5-126">-   None: No protection.</span></span><br /><span data-ttu-id="d28a5-127">-Sign：对消息进行签名。</span><span class="sxs-lookup"><span data-stu-id="d28a5-127">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="d28a5-128">-EncryptAndSign：对消息进行加密和签名。</span><span class="sxs-lookup"><span data-stu-id="d28a5-128">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="d28a5-129">默认值为 Sign。</span><span class="sxs-lookup"><span data-stu-id="d28a5-129">The default value is Sign.</span></span> <span data-ttu-id="d28a5-130">此属性的类型为 <xref:System.Net.Security.ProtectionLevel>。</span><span class="sxs-lookup"><span data-stu-id="d28a5-130">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="d28a5-131">指定用于计算签名中的摘要的算法。</span><span class="sxs-lookup"><span data-stu-id="d28a5-131">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="d28a5-132">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="d28a5-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d28a5-133">-MD5</span><span class="sxs-lookup"><span data-stu-id="d28a5-133">-   MD5</span></span><br /><span data-ttu-id="d28a5-134">-SHA1</span><span class="sxs-lookup"><span data-stu-id="d28a5-134">-   SHA1</span></span><br /><span data-ttu-id="d28a5-135">-SHA256</span><span class="sxs-lookup"><span data-stu-id="d28a5-135">-   SHA256</span></span><br /><span data-ttu-id="d28a5-136">-SHA512</span><span class="sxs-lookup"><span data-stu-id="d28a5-136">-   SHA512</span></span><br /><br /> <span data-ttu-id="d28a5-137">默认值为 SHA1。</span><span class="sxs-lookup"><span data-stu-id="d28a5-137">The default value is SHA1.</span></span> <span data-ttu-id="d28a5-138">此属性的类型为 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="d28a5-138">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="d28a5-139">由于 MD5 和 SHA1 出现冲突，Microsoft 建议 SHA256 或更好。</span><span class="sxs-lookup"><span data-stu-id="d28a5-139">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d28a5-140">子元素</span><span class="sxs-lookup"><span data-stu-id="d28a5-140">Child Elements</span></span>  

 <span data-ttu-id="d28a5-141">无。</span><span class="sxs-lookup"><span data-stu-id="d28a5-141">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d28a5-142">父元素</span><span class="sxs-lookup"><span data-stu-id="d28a5-142">Parent Elements</span></span>  
  
|<span data-ttu-id="d28a5-143">元素</span><span class="sxs-lookup"><span data-stu-id="d28a5-143">Element</span></span>|<span data-ttu-id="d28a5-144">描述</span><span class="sxs-lookup"><span data-stu-id="d28a5-144">Description</span></span>|  
|-------------|-----------------|  
|[\<msmqIntegration>](msmqintegration.md)|<span data-ttu-id="d28a5-145">指定与消息队列 (MSMQ) 发送方或接收方进行交互所需的设置。</span><span class="sxs-lookup"><span data-stu-id="d28a5-145">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[\<msmqTransport>](msmqtransport.md)|<span data-ttu-id="d28a5-146">指定使用本机 MSMQ 协议的 Windows Communication Foundation (WCF) 服务的队列通信属性。</span><span class="sxs-lookup"><span data-stu-id="d28a5-146">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d28a5-147">备注</span><span class="sxs-lookup"><span data-stu-id="d28a5-147">Remarks</span></span>  

 <span data-ttu-id="d28a5-148">有关传输安全的详细信息，请参阅 [传输安全性](../../../wcf/feature-details/transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="d28a5-148">For more information on transport security, see [Transport Security](../../../wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d28a5-149">请参阅</span><span class="sxs-lookup"><span data-stu-id="d28a5-149">See also</span></span>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d28a5-150">WCF 中的队列</span><span class="sxs-lookup"><span data-stu-id="d28a5-150">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="d28a5-151">传输</span><span class="sxs-lookup"><span data-stu-id="d28a5-151">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="d28a5-152">选择传输方式</span><span class="sxs-lookup"><span data-stu-id="d28a5-152">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="d28a5-153">绑定</span><span class="sxs-lookup"><span data-stu-id="d28a5-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d28a5-154">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="d28a5-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d28a5-155">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="d28a5-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="d28a5-156">传输安全</span><span class="sxs-lookup"><span data-stu-id="d28a5-156">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
