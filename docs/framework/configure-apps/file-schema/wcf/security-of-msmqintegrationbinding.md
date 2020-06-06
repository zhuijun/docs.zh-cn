---
title: <security> 的 <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 2268bf48a2b86c3b3b25db006e6f8f55ea33af73
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738691"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="19d34-102">\<security> 的 \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="19d34-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="19d34-103">定义消息队列 (MSMQ) 集成通道的传输安全设置。</span><span class="sxs-lookup"><span data-stu-id="19d34-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="19d34-104">语法</span><span class="sxs-lookup"><span data-stu-id="19d34-104">Syntax</span></span>  
  
```xml  
<msmqIntegrationBinding>
  <binding>
    <security mode="None/Transport">
      <transport msmqAuthenticationMode="None/Windows/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
      <message algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               defaultProtectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</msmqIntegrationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19d34-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="19d34-105">Attributes and Elements</span></span>  
 <span data-ttu-id="19d34-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="19d34-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19d34-107">特性</span><span class="sxs-lookup"><span data-stu-id="19d34-107">Attributes</span></span>  
  
|<span data-ttu-id="19d34-108">属性</span><span class="sxs-lookup"><span data-stu-id="19d34-108">Attribute</span></span>|<span data-ttu-id="19d34-109">说明</span><span class="sxs-lookup"><span data-stu-id="19d34-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19d34-110">模式</span><span class="sxs-lookup"><span data-stu-id="19d34-110">mode</span></span>|<span data-ttu-id="19d34-111">指定使用消息队列集成通道控制完整性、保密性和身份验证的安全类型。</span><span class="sxs-lookup"><span data-stu-id="19d34-111">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="19d34-112">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="19d34-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="19d34-113">-None：这将禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="19d34-113">-   None: This disables security.</span></span><br /><span data-ttu-id="19d34-114">-Transport：传输提供保护和身份验证。</span><span class="sxs-lookup"><span data-stu-id="19d34-114">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="19d34-115">这适用于两个队列管理器之间的消息安全性。</span><span class="sxs-lookup"><span data-stu-id="19d34-115">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="19d34-116">未在应用程序和队列管理器之间提供安全性。</span><span class="sxs-lookup"><span data-stu-id="19d34-116">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="19d34-117">现有的 Msmq 应用程序与此类型的安全模式功能等效。</span><span class="sxs-lookup"><span data-stu-id="19d34-117">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="19d34-118">默认值为 `Transport`。</span><span class="sxs-lookup"><span data-stu-id="19d34-118">The default value is `Transport`.</span></span> <span data-ttu-id="19d34-119">此属性的类型为 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="19d34-119">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19d34-120">子元素</span><span class="sxs-lookup"><span data-stu-id="19d34-120">Child Elements</span></span>  
  
|<span data-ttu-id="19d34-121">元素</span><span class="sxs-lookup"><span data-stu-id="19d34-121">Element</span></span>|<span data-ttu-id="19d34-122">描述</span><span class="sxs-lookup"><span data-stu-id="19d34-122">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="19d34-123">定义消息队列集成传输的安全设置。</span><span class="sxs-lookup"><span data-stu-id="19d34-123">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="19d34-124">此元素的类型为 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="19d34-124">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="19d34-125">父元素</span><span class="sxs-lookup"><span data-stu-id="19d34-125">Parent Elements</span></span>  
  
|<span data-ttu-id="19d34-126">元素</span><span class="sxs-lookup"><span data-stu-id="19d34-126">Element</span></span>|<span data-ttu-id="19d34-127">描述</span><span class="sxs-lookup"><span data-stu-id="19d34-127">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="19d34-128">的绑定元素 [\<msmqIntegrationBinding>](msmqintegrationbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="19d34-128">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19d34-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19d34-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="19d34-130">WCF 中的队列</span><span class="sxs-lookup"><span data-stu-id="19d34-130">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="19d34-131">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="19d34-131">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="19d34-132">绑定</span><span class="sxs-lookup"><span data-stu-id="19d34-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="19d34-133">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="19d34-133">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="19d34-134">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="19d34-134">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [\<msmqIntegrationBinding>](msmqintegrationbinding.md)
