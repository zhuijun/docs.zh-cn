---
title: <transport> 的 <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 3b2c7716727f58abb81bf4d58b13189ac170cf7c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399291"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="4f20e-102">\<transport> 的 \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="4f20e-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="4f20e-103">指定采用此绑定配置的对等方所发送的安全消息的传输类型。</span><span class="sxs-lookup"><span data-stu-id="4f20e-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="4f20e-104">语法</span><span class="sxs-lookup"><span data-stu-id="4f20e-104">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f20e-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="4f20e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4f20e-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4f20e-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f20e-107">特性</span><span class="sxs-lookup"><span data-stu-id="4f20e-107">Attributes</span></span>  
  
|<span data-ttu-id="4f20e-108">属性</span><span class="sxs-lookup"><span data-stu-id="4f20e-108">Attribute</span></span>|<span data-ttu-id="4f20e-109">说明</span><span class="sxs-lookup"><span data-stu-id="4f20e-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f20e-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="4f20e-110">credentialType</span></span>|<span data-ttu-id="4f20e-111">可选。</span><span class="sxs-lookup"><span data-stu-id="4f20e-111">Optional.</span></span> <span data-ttu-id="4f20e-112">指定用于验证通过对等传输发送的消息的凭据的类型。</span><span class="sxs-lookup"><span data-stu-id="4f20e-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="4f20e-113">此属性的类型为 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="4f20e-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="4f20e-114">credentialType 属性</span><span class="sxs-lookup"><span data-stu-id="4f20e-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="4f20e-115">值</span><span class="sxs-lookup"><span data-stu-id="4f20e-115">Value</span></span>|<span data-ttu-id="4f20e-116">说明</span><span class="sxs-lookup"><span data-stu-id="4f20e-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4f20e-117">证书</span><span class="sxs-lookup"><span data-stu-id="4f20e-117">Certificate</span></span>|<span data-ttu-id="4f20e-118">对等通道传输的身份验证需要 X509 证书。</span><span class="sxs-lookup"><span data-stu-id="4f20e-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="4f20e-119">Password</span><span class="sxs-lookup"><span data-stu-id="4f20e-119">Password</span></span>|<span data-ttu-id="4f20e-120">对等通道传输的身份验证需要正确的密码。</span><span class="sxs-lookup"><span data-stu-id="4f20e-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f20e-121">子元素</span><span class="sxs-lookup"><span data-stu-id="4f20e-121">Child Elements</span></span>  
 <span data-ttu-id="4f20e-122">无</span><span class="sxs-lookup"><span data-stu-id="4f20e-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f20e-123">父元素</span><span class="sxs-lookup"><span data-stu-id="4f20e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4f20e-124">元素</span><span class="sxs-lookup"><span data-stu-id="4f20e-124">Element</span></span>|<span data-ttu-id="4f20e-125">描述</span><span class="sxs-lookup"><span data-stu-id="4f20e-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="4f20e-126">定义对等传输的安全设置。</span><span class="sxs-lookup"><span data-stu-id="4f20e-126">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f20e-127">注解</span><span class="sxs-lookup"><span data-stu-id="4f20e-127">Remarks</span></span>  
 <span data-ttu-id="4f20e-128">仅当的 mode 属性设置为或时，才设置此元素 [\<security>](security-of-peertransport.md) `Transport` `TransportWithMessageCredential` 。</span><span class="sxs-lookup"><span data-stu-id="4f20e-128">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f20e-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4f20e-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4f20e-130">传输安全</span><span class="sxs-lookup"><span data-stu-id="4f20e-130">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="4f20e-131">传输</span><span class="sxs-lookup"><span data-stu-id="4f20e-131">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="4f20e-132">选择传输方式</span><span class="sxs-lookup"><span data-stu-id="4f20e-132">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="4f20e-133">绑定</span><span class="sxs-lookup"><span data-stu-id="4f20e-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4f20e-134">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="4f20e-134">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4f20e-135">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="4f20e-135">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
