---
title: <transport> 的 <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 49b31a889d192d190125214e89ba09305114eb7f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735975"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="2f063-102">\<transport> 的 \<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="2f063-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="2f063-103">指定使用时的传输级安全性设置 [\<netPeerTcpBinding>](netpeertcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="2f063-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="2f063-104">语法</span><span class="sxs-lookup"><span data-stu-id="2f063-104">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f063-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="2f063-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2f063-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2f063-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f063-107">特性</span><span class="sxs-lookup"><span data-stu-id="2f063-107">Attributes</span></span>  
  
|<span data-ttu-id="2f063-108">属性</span><span class="sxs-lookup"><span data-stu-id="2f063-108">Attribute</span></span>|<span data-ttu-id="2f063-109">说明</span><span class="sxs-lookup"><span data-stu-id="2f063-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2f063-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="2f063-110">credentialType</span></span>|<span data-ttu-id="2f063-111">可选。</span><span class="sxs-lookup"><span data-stu-id="2f063-111">Optional.</span></span> <span data-ttu-id="2f063-112">指定用于验证通过对等传输发送的消息的凭据的类型。</span><span class="sxs-lookup"><span data-stu-id="2f063-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="2f063-113">此属性的类型为 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="2f063-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="2f063-114">credentialType 属性</span><span class="sxs-lookup"><span data-stu-id="2f063-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="2f063-115">值</span><span class="sxs-lookup"><span data-stu-id="2f063-115">Value</span></span>|<span data-ttu-id="2f063-116">说明</span><span class="sxs-lookup"><span data-stu-id="2f063-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2f063-117">证书</span><span class="sxs-lookup"><span data-stu-id="2f063-117">Certificate</span></span>|<span data-ttu-id="2f063-118">对等通道传输的身份验证需要 X509 证书。</span><span class="sxs-lookup"><span data-stu-id="2f063-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="2f063-119">Password</span><span class="sxs-lookup"><span data-stu-id="2f063-119">Password</span></span>|<span data-ttu-id="2f063-120">对等通道传输的身份验证需要正确的密码。</span><span class="sxs-lookup"><span data-stu-id="2f063-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f063-121">子元素</span><span class="sxs-lookup"><span data-stu-id="2f063-121">Child Elements</span></span>  
 <span data-ttu-id="2f063-122">无</span><span class="sxs-lookup"><span data-stu-id="2f063-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2f063-123">父元素</span><span class="sxs-lookup"><span data-stu-id="2f063-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2f063-124">元素</span><span class="sxs-lookup"><span data-stu-id="2f063-124">Element</span></span>|<span data-ttu-id="2f063-125">描述</span><span class="sxs-lookup"><span data-stu-id="2f063-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="2f063-126">定义的安全设置 [\<netPeerTcpBinding>](netpeertcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="2f063-126">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2f063-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2f063-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="2f063-128">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="2f063-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2f063-129">绑定</span><span class="sxs-lookup"><span data-stu-id="2f063-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2f063-130">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="2f063-130">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2f063-131">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="2f063-131">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
