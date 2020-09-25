---
title: <security> 的 <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 32b066fdf4d8edbbd36fdff7b14bdec87ddc970d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170072"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="f99d0-102">\<security> 的 \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="f99d0-102">\<security> of \<netMsmqBinding></span></span>

<span data-ttu-id="f99d0-103">定义 MSMQ 绑定的安全设置。</span><span class="sxs-lookup"><span data-stu-id="f99d0-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="f99d0-104">它指定是否启用传输或 SOAP 安全；如果启用，还指定所使用的身份验证模式和保护级别。</span><span class="sxs-lookup"><span data-stu-id="f99d0-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="f99d0-105">语法</span><span class="sxs-lookup"><span data-stu-id="f99d0-105">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/Both">
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
             clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f99d0-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f99d0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f99d0-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f99d0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f99d0-108">特性</span><span class="sxs-lookup"><span data-stu-id="f99d0-108">Attributes</span></span>  
  
|<span data-ttu-id="f99d0-109">属性</span><span class="sxs-lookup"><span data-stu-id="f99d0-109">Attribute</span></span>|<span data-ttu-id="f99d0-110">描述</span><span class="sxs-lookup"><span data-stu-id="f99d0-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f99d0-111">mode</span><span class="sxs-lookup"><span data-stu-id="f99d0-111">mode</span></span>|<span data-ttu-id="f99d0-112">指定用于控制完整性、保密性和身份验证的安全类型。</span><span class="sxs-lookup"><span data-stu-id="f99d0-112">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="f99d0-113">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="f99d0-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f99d0-114">-None：这将禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="f99d0-114">-   None: This disables security.</span></span><br /><span data-ttu-id="f99d0-115">-Transport：传输提供保护和身份验证。</span><span class="sxs-lookup"><span data-stu-id="f99d0-115">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="f99d0-116">这适用于两个队列管理器之间的消息安全性。</span><span class="sxs-lookup"><span data-stu-id="f99d0-116">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="f99d0-117">未在应用程序和队列管理器之间提供安全性。</span><span class="sxs-lookup"><span data-stu-id="f99d0-117">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="f99d0-118">现有的 Msmq 应用程序与此类型的安全模式功能等效。</span><span class="sxs-lookup"><span data-stu-id="f99d0-118">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="f99d0-119">-Message：指定端应用程序安全性。</span><span class="sxs-lookup"><span data-stu-id="f99d0-119">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="f99d0-120">未在传输层提供安全性。</span><span class="sxs-lookup"><span data-stu-id="f99d0-120">There is no security offered at the transport layer.</span></span> <span data-ttu-id="f99d0-121">这类似于其他标准绑定提供的安全性。</span><span class="sxs-lookup"><span data-stu-id="f99d0-121">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="f99d0-122">-Both：同时在传输和 SOAP 消息传送层上提供安全性。</span><span class="sxs-lookup"><span data-stu-id="f99d0-122">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="f99d0-123">在这两个层上需要相同的凭据。</span><span class="sxs-lookup"><span data-stu-id="f99d0-123">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="f99d0-124">默认值为 Transport。</span><span class="sxs-lookup"><span data-stu-id="f99d0-124">The default value is Transport.</span></span> <span data-ttu-id="f99d0-125">此属性的类型为 <xref:System.ServiceModel.NetMsmqSecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="f99d0-125">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f99d0-126">子元素</span><span class="sxs-lookup"><span data-stu-id="f99d0-126">Child Elements</span></span>  
  
|<span data-ttu-id="f99d0-127">元素</span><span class="sxs-lookup"><span data-stu-id="f99d0-127">Element</span></span>|<span data-ttu-id="f99d0-128">描述</span><span class="sxs-lookup"><span data-stu-id="f99d0-128">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-netmsmqbinding.md)|<span data-ttu-id="f99d0-129">定义 SOAP 消息安全设置。</span><span class="sxs-lookup"><span data-stu-id="f99d0-129">Defines the SOAP message security settings.</span></span> <span data-ttu-id="f99d0-130">此元素的类型为 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>。</span><span class="sxs-lookup"><span data-stu-id="f99d0-130">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[\<transport>](transport-of-netmsmqbinding.md)|<span data-ttu-id="f99d0-131">定义 MSMQ 传输的安全设置。</span><span class="sxs-lookup"><span data-stu-id="f99d0-131">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="f99d0-132">此元素的类型为 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="f99d0-132">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f99d0-133">父元素</span><span class="sxs-lookup"><span data-stu-id="f99d0-133">Parent Elements</span></span>  
  
|<span data-ttu-id="f99d0-134">元素</span><span class="sxs-lookup"><span data-stu-id="f99d0-134">Element</span></span>|<span data-ttu-id="f99d0-135">描述</span><span class="sxs-lookup"><span data-stu-id="f99d0-135">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f99d0-136">binding</span><span class="sxs-lookup"><span data-stu-id="f99d0-136">binding</span></span>|<span data-ttu-id="f99d0-137">的绑定元素 [\<netMsmqBinding>](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="f99d0-137">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f99d0-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="f99d0-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="f99d0-139">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="f99d0-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f99d0-140">绑定</span><span class="sxs-lookup"><span data-stu-id="f99d0-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f99d0-141">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="f99d0-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f99d0-142">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="f99d0-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="f99d0-143">WCF 中的队列</span><span class="sxs-lookup"><span data-stu-id="f99d0-143">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
