---
title: <security> 的 <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 543c57d6b2dba1ff5934b49e0e219cf2e5cad153
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170020"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="5bec1-102">\<security> 的 \<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="5bec1-102">\<security> of \<netPeerBinding></span></span>

<span data-ttu-id="5bec1-103">定义的安全设置 [\<netPeerTcpBinding>](netpeertcpbinding.md) ，包括使用的身份验证类型和用于消息传输的安全性。</span><span class="sxs-lookup"><span data-stu-id="5bec1-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="5bec1-104">语法</span><span class="sxs-lookup"><span data-stu-id="5bec1-104">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bec1-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="5bec1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="5bec1-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5bec1-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bec1-107">特性</span><span class="sxs-lookup"><span data-stu-id="5bec1-107">Attributes</span></span>  
  
|<span data-ttu-id="5bec1-108">属性</span><span class="sxs-lookup"><span data-stu-id="5bec1-108">Attribute</span></span>|<span data-ttu-id="5bec1-109">描述</span><span class="sxs-lookup"><span data-stu-id="5bec1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5bec1-110">mode</span><span class="sxs-lookup"><span data-stu-id="5bec1-110">mode</span></span>|<span data-ttu-id="5bec1-111">可选。</span><span class="sxs-lookup"><span data-stu-id="5bec1-111">Optional.</span></span> <span data-ttu-id="5bec1-112">指定采用此绑定配置的对等端所使用的安全类型。</span><span class="sxs-lookup"><span data-stu-id="5bec1-112">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="5bec1-113">默认值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="5bec1-113">The default value is `Message`.</span></span> <span data-ttu-id="5bec1-114">此属性的类型为 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="5bec1-114">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="5bec1-115">mode 属性</span><span class="sxs-lookup"><span data-stu-id="5bec1-115">mode Attribute</span></span>  
  
|<span data-ttu-id="5bec1-116">值</span><span class="sxs-lookup"><span data-stu-id="5bec1-116">Value</span></span>|<span data-ttu-id="5bec1-117">描述</span><span class="sxs-lookup"><span data-stu-id="5bec1-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5bec1-118">消息</span><span class="sxs-lookup"><span data-stu-id="5bec1-118">Message</span></span>|<span data-ttu-id="5bec1-119">SOAP 安全提供身份验证、完整性和保密性。</span><span class="sxs-lookup"><span data-stu-id="5bec1-119">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="5bec1-120">无</span><span class="sxs-lookup"><span data-stu-id="5bec1-120">None</span></span>|<span data-ttu-id="5bec1-121">禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="5bec1-121">Security is disabled.</span></span>|  
|<span data-ttu-id="5bec1-122">传输</span><span class="sxs-lookup"><span data-stu-id="5bec1-122">Transport</span></span>|<span data-ttu-id="5bec1-123">使用 HTTPS 提供安全性。</span><span class="sxs-lookup"><span data-stu-id="5bec1-123">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="5bec1-124">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="5bec1-124">TransportWithMessageCredential</span></span>|<span data-ttu-id="5bec1-125">HTTPS 提供身份验证和保密性。</span><span class="sxs-lookup"><span data-stu-id="5bec1-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="5bec1-126">SOAP 消息提供丰富的凭据类型。</span><span class="sxs-lookup"><span data-stu-id="5bec1-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5bec1-127">子元素</span><span class="sxs-lookup"><span data-stu-id="5bec1-127">Child Elements</span></span>  
  
|<span data-ttu-id="5bec1-128">元素</span><span class="sxs-lookup"><span data-stu-id="5bec1-128">Element</span></span>|<span data-ttu-id="5bec1-129">描述</span><span class="sxs-lookup"><span data-stu-id="5bec1-129">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="5bec1-130">定义采用此绑定配置的对等端所发送的安全消息的传输类型。</span><span class="sxs-lookup"><span data-stu-id="5bec1-130">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="5bec1-131">此元素的类型为 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="5bec1-131">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5bec1-132">父元素</span><span class="sxs-lookup"><span data-stu-id="5bec1-132">Parent Elements</span></span>  
  
|<span data-ttu-id="5bec1-133">元素</span><span class="sxs-lookup"><span data-stu-id="5bec1-133">Element</span></span>|<span data-ttu-id="5bec1-134">描述</span><span class="sxs-lookup"><span data-stu-id="5bec1-134">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="5bec1-135">定义的所有绑定功能 [\<netPeerTcpBinding>](netpeertcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="5bec1-135">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bec1-136">备注</span><span class="sxs-lookup"><span data-stu-id="5bec1-136">Remarks</span></span>  

 <span data-ttu-id="5bec1-137">安全性可以是特定于消息的，也可以是特定于传输的。</span><span class="sxs-lookup"><span data-stu-id="5bec1-137">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bec1-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="5bec1-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="5bec1-139">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="5bec1-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5bec1-140">选择凭据类型</span><span class="sxs-lookup"><span data-stu-id="5bec1-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="5bec1-141">绑定</span><span class="sxs-lookup"><span data-stu-id="5bec1-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5bec1-142">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="5bec1-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5bec1-143">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="5bec1-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
