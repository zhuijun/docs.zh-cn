---
title: <security> 的 <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 270ca844f586be256b6483653c868d1cc4396657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399757"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="9664c-102">\<security> 的 \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="9664c-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="9664c-103">包含与对等通道相关的安全设置，包括使用的身份验证类型和用于消息传输的安全性。</span><span class="sxs-lookup"><span data-stu-id="9664c-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="9664c-104">语法</span><span class="sxs-lookup"><span data-stu-id="9664c-104">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9664c-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="9664c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9664c-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9664c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9664c-107">特性</span><span class="sxs-lookup"><span data-stu-id="9664c-107">Attributes</span></span>  
  
|<span data-ttu-id="9664c-108">属性</span><span class="sxs-lookup"><span data-stu-id="9664c-108">Attribute</span></span>|<span data-ttu-id="9664c-109">说明</span><span class="sxs-lookup"><span data-stu-id="9664c-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="9664c-110">指定要应用的安全类型。</span><span class="sxs-lookup"><span data-stu-id="9664c-110">Specifies the type of security to be applied.</span></span> <span data-ttu-id="9664c-111">默认值为 Message。</span><span class="sxs-lookup"><span data-stu-id="9664c-111">The default value is Message.</span></span> <span data-ttu-id="9664c-112">此属性的类型为 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="9664c-112">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="9664c-113">mode 属性</span><span class="sxs-lookup"><span data-stu-id="9664c-113">mode Attribute</span></span>  
  
|<span data-ttu-id="9664c-114">值</span><span class="sxs-lookup"><span data-stu-id="9664c-114">Value</span></span>|<span data-ttu-id="9664c-115">说明</span><span class="sxs-lookup"><span data-stu-id="9664c-115">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="9664c-116">禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="9664c-116">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="9664c-117">使用 HTTPS 提供安全性。</span><span class="sxs-lookup"><span data-stu-id="9664c-117">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="9664c-118">SOAP 安全提供身份验证、完整性和保密性。</span><span class="sxs-lookup"><span data-stu-id="9664c-118">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="9664c-119">HTTPS 提供身份验证和保密性。</span><span class="sxs-lookup"><span data-stu-id="9664c-119">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="9664c-120">SOAP 消息提供丰富的凭据类型。</span><span class="sxs-lookup"><span data-stu-id="9664c-120">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9664c-121">子元素</span><span class="sxs-lookup"><span data-stu-id="9664c-121">Child Elements</span></span>  
  
|<span data-ttu-id="9664c-122">元素</span><span class="sxs-lookup"><span data-stu-id="9664c-122">Element</span></span>|<span data-ttu-id="9664c-123">描述</span><span class="sxs-lookup"><span data-stu-id="9664c-123">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-peertransport.md)|<span data-ttu-id="9664c-124">定义自定义绑定的对等传输。</span><span class="sxs-lookup"><span data-stu-id="9664c-124">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="9664c-125">此元素具有一个 `clientCredentialType` 属性，可指定与服务进行交互时要使用的凭据。</span><span class="sxs-lookup"><span data-stu-id="9664c-125">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="9664c-126">此属性的类型为 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="9664c-126">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="9664c-127">此元素的类型为 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="9664c-127">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9664c-128">父元素</span><span class="sxs-lookup"><span data-stu-id="9664c-128">Parent Elements</span></span>  
  
|<span data-ttu-id="9664c-129">元素</span><span class="sxs-lookup"><span data-stu-id="9664c-129">Element</span></span>|<span data-ttu-id="9664c-130">描述</span><span class="sxs-lookup"><span data-stu-id="9664c-130">Description</span></span>|  
|-------------|-----------------|  
|[\<peerTransport>](peertransport.md)|<span data-ttu-id="9664c-131">定义自定义绑定的对等传输。</span><span class="sxs-lookup"><span data-stu-id="9664c-131">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9664c-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9664c-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9664c-133">传输安全</span><span class="sxs-lookup"><span data-stu-id="9664c-133">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="9664c-134">传输</span><span class="sxs-lookup"><span data-stu-id="9664c-134">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="9664c-135">选择传输方式</span><span class="sxs-lookup"><span data-stu-id="9664c-135">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="9664c-136">绑定</span><span class="sxs-lookup"><span data-stu-id="9664c-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9664c-137">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="9664c-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9664c-138">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="9664c-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
