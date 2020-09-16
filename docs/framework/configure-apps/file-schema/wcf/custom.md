---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 4077aacab1c1c4594db76cc6663bfc0245d345d7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555492"
---
# \<custom>
<span data-ttu-id="c31a8-101">指定自定义对等解析程序服务的设置。</span><span class="sxs-lookup"><span data-stu-id="c31a8-101">Specifies settings for a custom peer resolver service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<resolver>**](resolver.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<custom>**  
  
## <a name="syntax"></a><span data-ttu-id="c31a8-102">语法</span><span class="sxs-lookup"><span data-stu-id="c31a8-102">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c31a8-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c31a8-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c31a8-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c31a8-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c31a8-105">特性</span><span class="sxs-lookup"><span data-stu-id="c31a8-105">Attributes</span></span>  
  
|<span data-ttu-id="c31a8-106">特性</span><span class="sxs-lookup"><span data-stu-id="c31a8-106">Attribute</span></span>|<span data-ttu-id="c31a8-107">说明</span><span class="sxs-lookup"><span data-stu-id="c31a8-107">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="c31a8-108">一个 URI，指定承载自定义对等解析程序服务的对等节点的终结点地址。</span><span class="sxs-lookup"><span data-stu-id="c31a8-108">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="c31a8-109">一个字符串值，指定自定义对等解析程序服务的类型。</span><span class="sxs-lookup"><span data-stu-id="c31a8-109">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c31a8-110">子元素</span><span class="sxs-lookup"><span data-stu-id="c31a8-110">Child Elements</span></span>  
  
|<span data-ttu-id="c31a8-111">元素</span><span class="sxs-lookup"><span data-stu-id="c31a8-111">Element</span></span>|<span data-ttu-id="c31a8-112">说明</span><span class="sxs-lookup"><span data-stu-id="c31a8-112">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="c31a8-113">指定配置了此元素的自定义对等解析程序的标识。</span><span class="sxs-lookup"><span data-stu-id="c31a8-113">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="c31a8-114">此元素的类型为 <xref:System.ServiceModel.Configuration.IdentityElement>。</span><span class="sxs-lookup"><span data-stu-id="c31a8-114">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="c31a8-115">一个地址标头集合，可用于由自定义对等解析程序处理的 SOAP 消息。</span><span class="sxs-lookup"><span data-stu-id="c31a8-115">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c31a8-116">父元素</span><span class="sxs-lookup"><span data-stu-id="c31a8-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c31a8-117">元素</span><span class="sxs-lookup"><span data-stu-id="c31a8-117">Element</span></span>|<span data-ttu-id="c31a8-118">说明</span><span class="sxs-lookup"><span data-stu-id="c31a8-118">Description</span></span>|  
|-------------|-----------------|  
|[\<resolver>](resolver.md)|<span data-ttu-id="c31a8-119">一个对等解析程序，可用于将对等网格 ID 解析为一组对等节点地址，这些地址表示参与网格的若干节点。</span><span class="sxs-lookup"><span data-stu-id="c31a8-119">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c31a8-120">备注</span><span class="sxs-lookup"><span data-stu-id="c31a8-120">Remarks</span></span>  
 <span data-ttu-id="c31a8-121">此元素可定义自定义对等解析程序服务的基本设置，其中包括执行服务的对等解析程序的终结点地址和所有特定绑定设置。</span><span class="sxs-lookup"><span data-stu-id="c31a8-121">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="c31a8-122">有关创建自定义冲突解决程序的详细信息，请参阅 [将自定义冲突解决程序添加到 PeerChannel 应用程序](/previous-versions/ms730105(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="c31a8-122">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c31a8-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="c31a8-123">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="c31a8-124">对等解析程序</span><span class="sxs-lookup"><span data-stu-id="c31a8-124">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="c31a8-125">[向对等通道应用程序添加自定义解析程序](/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c31a8-125">[Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90))</span></span>
