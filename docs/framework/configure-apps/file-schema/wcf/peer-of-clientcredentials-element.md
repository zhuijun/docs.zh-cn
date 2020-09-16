---
title: <peer> of <clientCredentials> 元素
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: a8144ca7bad5654bf8f77259ea1717442665fc81
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555453"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="374e7-102">\<peer> of \<clientCredentials> 元素</span><span class="sxs-lookup"><span data-stu-id="374e7-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="374e7-103">指定在向对等客户端进行身份验证时使用的凭据。</span><span class="sxs-lookup"><span data-stu-id="374e7-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="374e7-104">语法</span><span class="sxs-lookup"><span data-stu-id="374e7-104">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="374e7-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="374e7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="374e7-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="374e7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="374e7-107">特性</span><span class="sxs-lookup"><span data-stu-id="374e7-107">Attributes</span></span>  
 <span data-ttu-id="374e7-108">无。</span><span class="sxs-lookup"><span data-stu-id="374e7-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="374e7-109">子元素</span><span class="sxs-lookup"><span data-stu-id="374e7-109">Child Elements</span></span>  
  
|<span data-ttu-id="374e7-110">元素</span><span class="sxs-lookup"><span data-stu-id="374e7-110">Element</span></span>|<span data-ttu-id="374e7-111">说明</span><span class="sxs-lookup"><span data-stu-id="374e7-111">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-element.md)|<span data-ttu-id="374e7-112">指定要用于为对等客户端的消息进行签名和加密的 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="374e7-112">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="374e7-113">.</span><span class="sxs-lookup"><span data-stu-id="374e7-113">.</span></span>|  
|[\<peerAuthentication>](peerauthentication-element.md)|<span data-ttu-id="374e7-114">指定用于对等客户端的身份验证选项。</span><span class="sxs-lookup"><span data-stu-id="374e7-114">Specifies authentication options for peer clients.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication-element.md)|<span data-ttu-id="374e7-115">指定用于消息发送方的身份验证选项。</span><span class="sxs-lookup"><span data-stu-id="374e7-115">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="374e7-116">父元素</span><span class="sxs-lookup"><span data-stu-id="374e7-116">Parent Elements</span></span>  
  
|<span data-ttu-id="374e7-117">元素</span><span class="sxs-lookup"><span data-stu-id="374e7-117">Element</span></span>|<span data-ttu-id="374e7-118">说明</span><span class="sxs-lookup"><span data-stu-id="374e7-118">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="374e7-119">指定用于向服务验证客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="374e7-119">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="374e7-120">备注</span><span class="sxs-lookup"><span data-stu-id="374e7-120">Remarks</span></span>  
 <span data-ttu-id="374e7-121">此配置元素指定对等节点用于向网格中的其他节点证明它自己的身份的凭据，以及对等节点用于验证其他对等节点的身份的身份验证设置。</span><span class="sxs-lookup"><span data-stu-id="374e7-121">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="374e7-122">有关详细信息，请参阅 [对等通道消息身份验证](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) 和 [保护对等通道应用程序](../../../wcf/feature-details/securing-peer-channel-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="374e7-122">For more information, see [Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="374e7-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="374e7-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="374e7-124">对等网络</span><span class="sxs-lookup"><span data-stu-id="374e7-124">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="374e7-125">保证客户端的安全</span><span class="sxs-lookup"><span data-stu-id="374e7-125">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="374e7-126">[对等通道消息身份验证](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="374e7-126">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="374e7-127">[对等通道自定义身份验证](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="374e7-127">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="374e7-128">保护对等通道应用程序</span><span class="sxs-lookup"><span data-stu-id="374e7-128">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="374e7-129">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="374e7-129">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
