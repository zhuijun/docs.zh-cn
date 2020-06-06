---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 0dc667f392595d895bd4f2773ab69777d7369446
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738738"
---
# \<resolver>
<span data-ttu-id="afea2-101">指定对等解析程序，对等解析程序用于将对等网格 ID 解析为一组对等节点地址，这些地址表示参与网格的若干节点。</span><span class="sxs-lookup"><span data-stu-id="afea2-101">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**  
  
## <a name="syntax"></a><span data-ttu-id="afea2-102">语法</span><span class="sxs-lookup"><span data-stu-id="afea2-102">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afea2-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="afea2-103">Attributes and Elements</span></span>  
 <span data-ttu-id="afea2-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="afea2-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afea2-105">特性</span><span class="sxs-lookup"><span data-stu-id="afea2-105">Attributes</span></span>  
  
|<span data-ttu-id="afea2-106">属性</span><span class="sxs-lookup"><span data-stu-id="afea2-106">Attribute</span></span>|<span data-ttu-id="afea2-107">说明</span><span class="sxs-lookup"><span data-stu-id="afea2-107">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="afea2-108">一个字符串，指定与此服务关联的对等解析程序实例是特定于 PNRP，还是为自定义解析程序，或者是自动确定的。</span><span class="sxs-lookup"><span data-stu-id="afea2-108">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="afea2-109">此属性的类型为 <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>。</span><span class="sxs-lookup"><span data-stu-id="afea2-109">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="afea2-110">一个字符串，指定在对等端间共享引用的方式。</span><span class="sxs-lookup"><span data-stu-id="afea2-110">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="afea2-111">此属性的类型为 <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>。</span><span class="sxs-lookup"><span data-stu-id="afea2-111">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="afea2-112">子元素</span><span class="sxs-lookup"><span data-stu-id="afea2-112">Child Elements</span></span>  
  
|<span data-ttu-id="afea2-113">元素</span><span class="sxs-lookup"><span data-stu-id="afea2-113">Element</span></span>|<span data-ttu-id="afea2-114">描述</span><span class="sxs-lookup"><span data-stu-id="afea2-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="afea2-115">指定自定义对等解析程序服务的设置。</span><span class="sxs-lookup"><span data-stu-id="afea2-115">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="afea2-116">父元素</span><span class="sxs-lookup"><span data-stu-id="afea2-116">Parent Elements</span></span>  
  
|<span data-ttu-id="afea2-117">元素</span><span class="sxs-lookup"><span data-stu-id="afea2-117">Element</span></span>|<span data-ttu-id="afea2-118">描述</span><span class="sxs-lookup"><span data-stu-id="afea2-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="afea2-119">定义的所有绑定功能 [\<netPeerTcpBinding>](netpeertcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="afea2-119">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afea2-120">注解</span><span class="sxs-lookup"><span data-stu-id="afea2-120">Remarks</span></span>  
 <span data-ttu-id="afea2-121">对等名解析程序是对等通道用于查找参与对等网格的对等节点的发现服务。</span><span class="sxs-lookup"><span data-stu-id="afea2-121">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="afea2-122">它还可以用于在对等网格中“注册”节点，即对等节点在对等网格中变为已知和可用的机制。</span><span class="sxs-lookup"><span data-stu-id="afea2-122">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="afea2-123">有关对等解析程序的详细信息，请参阅[对等解析](../../../wcf/feature-details/peer-resolvers.md)程序。</span><span class="sxs-lookup"><span data-stu-id="afea2-123">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afea2-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="afea2-124">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="afea2-125">对等解析程序</span><span class="sxs-lookup"><span data-stu-id="afea2-125">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="afea2-126">[向对等通道应用程序添加自定义解析程序](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="afea2-126">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
