---
title: <peer> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: ca97be7b1ab562382895fea4f1d1fc716151b70b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397644"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="bbae8-102">\<peer> 的 \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="bbae8-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="bbae8-103">指定对等节点的当前凭据。</span><span class="sxs-lookup"><span data-stu-id="bbae8-103">Specifies the current credentials for a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="bbae8-104">语法</span><span class="sxs-lookup"><span data-stu-id="bbae8-104">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbae8-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="bbae8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bbae8-106">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bbae8-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbae8-107">特性</span><span class="sxs-lookup"><span data-stu-id="bbae8-107">Attributes</span></span>  
 <span data-ttu-id="bbae8-108">无。</span><span class="sxs-lookup"><span data-stu-id="bbae8-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bbae8-109">子元素</span><span class="sxs-lookup"><span data-stu-id="bbae8-109">Child Elements</span></span>  
  
|<span data-ttu-id="bbae8-110">元素</span><span class="sxs-lookup"><span data-stu-id="bbae8-110">Element</span></span>|<span data-ttu-id="bbae8-111">说明</span><span class="sxs-lookup"><span data-stu-id="bbae8-111">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-of-peer.md)|<span data-ttu-id="bbae8-112">指定要用于为对等服务的消息进行签名和加密的 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="bbae8-112">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="bbae8-113">.</span><span class="sxs-lookup"><span data-stu-id="bbae8-113">.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication.md)|<span data-ttu-id="bbae8-114">指定用于消息发送方的身份验证选项。</span><span class="sxs-lookup"><span data-stu-id="bbae8-114">Specifies authentication options for message senders.</span></span>|  
|[\<peerAuthentication>](peerauthentication.md)|<span data-ttu-id="bbae8-115">指定用于对等服务的身份验证选项。</span><span class="sxs-lookup"><span data-stu-id="bbae8-115">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bbae8-116">父元素</span><span class="sxs-lookup"><span data-stu-id="bbae8-116">Parent Elements</span></span>  
  
|<span data-ttu-id="bbae8-117">元素</span><span class="sxs-lookup"><span data-stu-id="bbae8-117">Element</span></span>|<span data-ttu-id="bbae8-118">说明</span><span class="sxs-lookup"><span data-stu-id="bbae8-118">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="bbae8-119">指定要用于对服务进行身份验证的凭据以及与客户端凭据验证相关的设置。</span><span class="sxs-lookup"><span data-stu-id="bbae8-119">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bbae8-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bbae8-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="bbae8-121">对等网络</span><span class="sxs-lookup"><span data-stu-id="bbae8-121">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="bbae8-122">[对等通道消息身份验证](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="bbae8-122">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="bbae8-123">[对等通道自定义身份验证](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="bbae8-123">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="bbae8-124">保护对等通道应用程序</span><span class="sxs-lookup"><span data-stu-id="bbae8-124">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="bbae8-125">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="bbae8-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
