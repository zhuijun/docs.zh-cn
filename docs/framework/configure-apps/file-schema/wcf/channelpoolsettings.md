---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 26537980a6be5c0fe12661d93a6ba5fe862ceb4e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398161"
---
# \<channelPoolSettings>
<span data-ttu-id="ef823-101">指定自定义绑定的通道池设置。</span><span class="sxs-lookup"><span data-stu-id="ef823-101">Specifies the channel pool settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oneWay>**](oneway.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="ef823-102">语法</span><span class="sxs-lookup"><span data-stu-id="ef823-102">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef823-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ef823-103">Attributes and Elements</span></span>  
 <span data-ttu-id="ef823-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ef823-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef823-105">特性</span><span class="sxs-lookup"><span data-stu-id="ef823-105">Attributes</span></span>  
  
|<span data-ttu-id="ef823-106">属性</span><span class="sxs-lookup"><span data-stu-id="ef823-106">Attribute</span></span>|<span data-ttu-id="ef823-107">说明</span><span class="sxs-lookup"><span data-stu-id="ef823-107">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="ef823-108">一个值为正的 <xref:System.TimeSpan>，指定池中的通道在断开前可以空闲的最长时间。</span><span class="sxs-lookup"><span data-stu-id="ef823-108">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="ef823-109">默认值为 00:02:00。</span><span class="sxs-lookup"><span data-stu-id="ef823-109">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="ef823-110"><xref:System.TimeSpan>，用于指定从通道返回池到通道关闭之间的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="ef823-110">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="ef823-111">默认值为 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="ef823-111">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="ef823-112">一个正整数，指定对于每个远程端点可以存储在池中的通道的最大数目。</span><span class="sxs-lookup"><span data-stu-id="ef823-112">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="ef823-113">默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="ef823-113">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef823-114">子元素</span><span class="sxs-lookup"><span data-stu-id="ef823-114">Child Elements</span></span>  
 <span data-ttu-id="ef823-115">无。</span><span class="sxs-lookup"><span data-stu-id="ef823-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef823-116">父元素</span><span class="sxs-lookup"><span data-stu-id="ef823-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ef823-117">元素</span><span class="sxs-lookup"><span data-stu-id="ef823-117">Element</span></span>|<span data-ttu-id="ef823-118">描述</span><span class="sxs-lookup"><span data-stu-id="ef823-118">Description</span></span>|  
|-------------|-----------------|  
|[\<oneWay>](oneway.md)|<span data-ttu-id="ef823-119">针对自定义绑定启用数据包路由。</span><span class="sxs-lookup"><span data-stu-id="ef823-119">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef823-120">注解</span><span class="sxs-lookup"><span data-stu-id="ef823-120">Remarks</span></span>  
 <span data-ttu-id="ef823-121">配额用作一种策略机制，防止消耗过多资源。</span><span class="sxs-lookup"><span data-stu-id="ef823-121">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="ef823-122">它们可防止恶意或无意的拒绝服务 (DOS) 攻击。</span><span class="sxs-lookup"><span data-stu-id="ef823-122">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="ef823-123">在设置自定义通道的通道配额时使用此元素。</span><span class="sxs-lookup"><span data-stu-id="ef823-123">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="ef823-124">`ChannelPoolSettings` 指定三项配额：</span><span class="sxs-lookup"><span data-stu-id="ef823-124">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="ef823-125">`idleTimeout` 配额用于减少通过长时间占用资源来对服务器实施的拒绝服务 (DOS) 攻击。</span><span class="sxs-lookup"><span data-stu-id="ef823-125">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="ef823-126">在客户端，设置正确的值可增加与服务连接的可靠性。</span><span class="sxs-lookup"><span data-stu-id="ef823-126">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="ef823-127">默认值基于资源的保守适度分配。</span><span class="sxs-lookup"><span data-stu-id="ef823-127">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="ef823-128">该值适用于开发环境和小型安装方案。</span><span class="sxs-lookup"><span data-stu-id="ef823-128">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="ef823-129">如果某个安装耗尽了资源或是连接受到限制，则无论是否还有其他资源可用，服务管理员都应检查该值。</span><span class="sxs-lookup"><span data-stu-id="ef823-129">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="ef823-130">`leaseTimeout` 配额用于与负载均衡器的集成以及提高可靠性。</span><span class="sxs-lookup"><span data-stu-id="ef823-130">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="ef823-131">默认值基于资源的保守分配。</span><span class="sxs-lookup"><span data-stu-id="ef823-131">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="ef823-132">该值适用于开发环境和小型安装方案。</span><span class="sxs-lookup"><span data-stu-id="ef823-132">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="ef823-133">如果某个安装耗尽了资源或是连接受到限制，则无论是否还有其他资源可用，服务管理员都应检查该值。</span><span class="sxs-lookup"><span data-stu-id="ef823-133">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="ef823-134">`maxOutboundChannelsPerEndpoint` 配额设置服务器与客户端上的缓存限制，用于提高可靠性。</span><span class="sxs-lookup"><span data-stu-id="ef823-134">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="ef823-135">其默认值基于资源的保守适度分配，适用于开发环境和小型安装方案。</span><span class="sxs-lookup"><span data-stu-id="ef823-135">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="ef823-136">如果某个安装耗尽了资源或是连接受到限制，则无论是否还有其他资源可用，服务管理员都应检查该值。</span><span class="sxs-lookup"><span data-stu-id="ef823-136">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef823-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef823-137">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](oneway.md)
- [<span data-ttu-id="ef823-138">绑定</span><span class="sxs-lookup"><span data-stu-id="ef823-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ef823-139">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="ef823-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ef823-140">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="ef823-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
