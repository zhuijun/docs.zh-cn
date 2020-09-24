---
title: <transport> 的 <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 7328d67c4649010dce3e1c866238d1e0067e4990
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157065"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="0e873-102">\<transport> 的 \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="0e873-102">\<transport> of \<peerTransport></span></span>

<span data-ttu-id="0e873-103">指定采用此绑定配置的对等方所发送的安全消息的传输类型。</span><span class="sxs-lookup"><span data-stu-id="0e873-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="0e873-104">语法</span><span class="sxs-lookup"><span data-stu-id="0e873-104">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e873-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0e873-105">Attributes and Elements</span></span>  

 <span data-ttu-id="0e873-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0e873-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e873-107">特性</span><span class="sxs-lookup"><span data-stu-id="0e873-107">Attributes</span></span>  
  
|<span data-ttu-id="0e873-108">属性</span><span class="sxs-lookup"><span data-stu-id="0e873-108">Attribute</span></span>|<span data-ttu-id="0e873-109">描述</span><span class="sxs-lookup"><span data-stu-id="0e873-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0e873-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="0e873-110">credentialType</span></span>|<span data-ttu-id="0e873-111">可选。</span><span class="sxs-lookup"><span data-stu-id="0e873-111">Optional.</span></span> <span data-ttu-id="0e873-112">指定用于验证通过对等传输发送的消息的凭据的类型。</span><span class="sxs-lookup"><span data-stu-id="0e873-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="0e873-113">此属性的类型为 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="0e873-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="0e873-114">credentialType 属性</span><span class="sxs-lookup"><span data-stu-id="0e873-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="0e873-115">值</span><span class="sxs-lookup"><span data-stu-id="0e873-115">Value</span></span>|<span data-ttu-id="0e873-116">描述</span><span class="sxs-lookup"><span data-stu-id="0e873-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e873-117">证书</span><span class="sxs-lookup"><span data-stu-id="0e873-117">Certificate</span></span>|<span data-ttu-id="0e873-118">对等通道传输的身份验证需要 X509 证书。</span><span class="sxs-lookup"><span data-stu-id="0e873-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="0e873-119">密码</span><span class="sxs-lookup"><span data-stu-id="0e873-119">Password</span></span>|<span data-ttu-id="0e873-120">对等通道传输的身份验证需要正确的密码。</span><span class="sxs-lookup"><span data-stu-id="0e873-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e873-121">子元素</span><span class="sxs-lookup"><span data-stu-id="0e873-121">Child Elements</span></span>  

 <span data-ttu-id="0e873-122">无</span><span class="sxs-lookup"><span data-stu-id="0e873-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0e873-123">父元素</span><span class="sxs-lookup"><span data-stu-id="0e873-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0e873-124">元素</span><span class="sxs-lookup"><span data-stu-id="0e873-124">Element</span></span>|<span data-ttu-id="0e873-125">描述</span><span class="sxs-lookup"><span data-stu-id="0e873-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="0e873-126">定义对等传输的安全设置。</span><span class="sxs-lookup"><span data-stu-id="0e873-126">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e873-127">备注</span><span class="sxs-lookup"><span data-stu-id="0e873-127">Remarks</span></span>  

 <span data-ttu-id="0e873-128">仅当的 mode 属性设置为或时，才设置此元素 [\<security>](security-of-peertransport.md) `Transport` `TransportWithMessageCredential` 。</span><span class="sxs-lookup"><span data-stu-id="0e873-128">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e873-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="0e873-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="0e873-130">传输安全</span><span class="sxs-lookup"><span data-stu-id="0e873-130">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="0e873-131">传输</span><span class="sxs-lookup"><span data-stu-id="0e873-131">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="0e873-132">选择传输方式</span><span class="sxs-lookup"><span data-stu-id="0e873-132">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="0e873-133">绑定</span><span class="sxs-lookup"><span data-stu-id="0e873-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0e873-134">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="0e873-134">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="0e873-135">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="0e873-135">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
