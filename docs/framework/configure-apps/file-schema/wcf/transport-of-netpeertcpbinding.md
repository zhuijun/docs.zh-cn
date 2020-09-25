---
title: <transport> 的 <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 5df47b1bfc149b524fc9b90eacffa832817f653c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172861"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="8dc18-102">\<transport> 的 \<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="8dc18-102">\<transport> of \<netPeerTcpBinding></span></span>

<span data-ttu-id="8dc18-103">指定使用时的传输级安全性设置 [\<netPeerTcpBinding>](netpeertcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="8dc18-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="8dc18-104">语法</span><span class="sxs-lookup"><span data-stu-id="8dc18-104">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8dc18-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="8dc18-105">Attributes and Elements</span></span>  

 <span data-ttu-id="8dc18-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8dc18-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8dc18-107">特性</span><span class="sxs-lookup"><span data-stu-id="8dc18-107">Attributes</span></span>  
  
|<span data-ttu-id="8dc18-108">属性</span><span class="sxs-lookup"><span data-stu-id="8dc18-108">Attribute</span></span>|<span data-ttu-id="8dc18-109">描述</span><span class="sxs-lookup"><span data-stu-id="8dc18-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8dc18-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="8dc18-110">credentialType</span></span>|<span data-ttu-id="8dc18-111">可选。</span><span class="sxs-lookup"><span data-stu-id="8dc18-111">Optional.</span></span> <span data-ttu-id="8dc18-112">指定用于验证通过对等传输发送的消息的凭据的类型。</span><span class="sxs-lookup"><span data-stu-id="8dc18-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="8dc18-113">此属性的类型为 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="8dc18-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="8dc18-114">credentialType 属性</span><span class="sxs-lookup"><span data-stu-id="8dc18-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="8dc18-115">值</span><span class="sxs-lookup"><span data-stu-id="8dc18-115">Value</span></span>|<span data-ttu-id="8dc18-116">描述</span><span class="sxs-lookup"><span data-stu-id="8dc18-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8dc18-117">证书</span><span class="sxs-lookup"><span data-stu-id="8dc18-117">Certificate</span></span>|<span data-ttu-id="8dc18-118">对等通道传输的身份验证需要 X509 证书。</span><span class="sxs-lookup"><span data-stu-id="8dc18-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="8dc18-119">密码</span><span class="sxs-lookup"><span data-stu-id="8dc18-119">Password</span></span>|<span data-ttu-id="8dc18-120">对等通道传输的身份验证需要正确的密码。</span><span class="sxs-lookup"><span data-stu-id="8dc18-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8dc18-121">子元素</span><span class="sxs-lookup"><span data-stu-id="8dc18-121">Child Elements</span></span>  

 <span data-ttu-id="8dc18-122">无</span><span class="sxs-lookup"><span data-stu-id="8dc18-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8dc18-123">父元素</span><span class="sxs-lookup"><span data-stu-id="8dc18-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8dc18-124">元素</span><span class="sxs-lookup"><span data-stu-id="8dc18-124">Element</span></span>|<span data-ttu-id="8dc18-125">描述</span><span class="sxs-lookup"><span data-stu-id="8dc18-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="8dc18-126">定义的安全设置 [\<netPeerTcpBinding>](netpeertcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="8dc18-126">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8dc18-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="8dc18-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="8dc18-128">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="8dc18-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8dc18-129">绑定</span><span class="sxs-lookup"><span data-stu-id="8dc18-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8dc18-130">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="8dc18-130">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8dc18-131">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="8dc18-131">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
