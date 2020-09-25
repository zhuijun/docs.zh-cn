---
title: <connectionPoolSettings> 的 <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 53523fd550ecad931bfb2af5eb9beb71c60d44f8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176001"
---
# <a name="connectionpoolsettings-of-tcptransport"></a><span data-ttu-id="4a77c-102">\<connectionPoolSettings> 的 \<tcpTransport></span><span class="sxs-lookup"><span data-stu-id="4a77c-102">\<connectionPoolSettings> of \<tcpTransport></span></span>

<span data-ttu-id="4a77c-103">指定 TCP 传输的其他连接池设置。</span><span class="sxs-lookup"><span data-stu-id="4a77c-103">Specifies additional connection pool settings for a TCP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tcpTransport>**](tcptransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="4a77c-104">语法</span><span class="sxs-lookup"><span data-stu-id="4a77c-104">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a77c-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="4a77c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="4a77c-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4a77c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a77c-107">特性</span><span class="sxs-lookup"><span data-stu-id="4a77c-107">Attributes</span></span>  
  
|<span data-ttu-id="4a77c-108">属性</span><span class="sxs-lookup"><span data-stu-id="4a77c-108">Attribute</span></span>|<span data-ttu-id="4a77c-109">描述</span><span class="sxs-lookup"><span data-stu-id="4a77c-109">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="4a77c-110">一个字符串，定义用于传出通道的连接池的名称。</span><span class="sxs-lookup"><span data-stu-id="4a77c-110">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="4a77c-111">在流处理模式中，不共享连接，这意味着禁用连接池。</span><span class="sxs-lookup"><span data-stu-id="4a77c-111">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="4a77c-112">默认值为字符串 "default"。</span><span class="sxs-lookup"><span data-stu-id="4a77c-112">The default is a "default" string.</span></span> <span data-ttu-id="4a77c-113">可以修改此值，以便将特定客户端的连接隔离到不同的组中。</span><span class="sxs-lookup"><span data-stu-id="4a77c-113">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="4a77c-114">一个值为正的 <xref:System.TimeSpan>，指定连接在断开前可以空闲的最长时间。</span><span class="sxs-lookup"><span data-stu-id="4a77c-114">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="4a77c-115">默认值为 00:02:00。</span><span class="sxs-lookup"><span data-stu-id="4a77c-115">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="4a77c-116">一个 <xref:System.TimeSpan>，指定在关闭活动连接之前所要经过的时间。</span><span class="sxs-lookup"><span data-stu-id="4a77c-116">A <xref:System.TimeSpan> that specifies the time after which an active connection is closed.</span></span> <span data-ttu-id="4a77c-117">默认值为 00:05:00。</span><span class="sxs-lookup"><span data-stu-id="4a77c-117">The default is 00:05:00.</span></span><br /><br /> <span data-ttu-id="4a77c-118">连接在返回到连接缓存之后关闭，而不是在活动传输期间关闭。</span><span class="sxs-lookup"><span data-stu-id="4a77c-118">A connection is closed after it has been returned to the connection cache and not during active transmission.</span></span> <span data-ttu-id="4a77c-119">TCP 传输使用的连接缓存将根据需要为每一个终结点创建新连接，直至达到 `maxOutboundConnectionsPerEndpoint.` 所设置的缓存限制。</span><span class="sxs-lookup"><span data-stu-id="4a77c-119">The connection cache used by the TCP transport creates new connections as required for each endpoint, up to the cache limit that is set by `maxOutboundConnectionsPerEndpoint.`</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="4a77c-120">一个正整数，指定由服务启动的与远程终结点的最大连接数。</span><span class="sxs-lookup"><span data-stu-id="4a77c-120">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="4a77c-121">超出此限制的连接需要排队，直到连接数低于限制值。</span><span class="sxs-lookup"><span data-stu-id="4a77c-121">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="4a77c-122">`idleTimeout` 限制连接在引发异常前保持排队状态的持续时间。</span><span class="sxs-lookup"><span data-stu-id="4a77c-122">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="4a77c-123">默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="4a77c-123">The default is 10.</span></span><br /><br /> <span data-ttu-id="4a77c-124">此属性限制从客户端到特定服务终结点的同时活动的连接数。</span><span class="sxs-lookup"><span data-stu-id="4a77c-124">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="4a77c-125">如果由于具有更多的活动客户端连接而超出此值，则服务可能表现为对客户端无响应。</span><span class="sxs-lookup"><span data-stu-id="4a77c-125">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="4a77c-126">在此情况下，应调整此值使之超过与特定终结点的同时活动的最大预期客户端连接数。</span><span class="sxs-lookup"><span data-stu-id="4a77c-126">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a77c-127">子元素</span><span class="sxs-lookup"><span data-stu-id="4a77c-127">Child Elements</span></span>  

 <span data-ttu-id="4a77c-128">无。</span><span class="sxs-lookup"><span data-stu-id="4a77c-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4a77c-129">父元素</span><span class="sxs-lookup"><span data-stu-id="4a77c-129">Parent Elements</span></span>  
  
|<span data-ttu-id="4a77c-130">元素</span><span class="sxs-lookup"><span data-stu-id="4a77c-130">Element</span></span>|<span data-ttu-id="4a77c-131">描述</span><span class="sxs-lookup"><span data-stu-id="4a77c-131">Description</span></span>|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|<span data-ttu-id="4a77c-132">定义传输，该传输使通道使用命名管道传输消息。</span><span class="sxs-lookup"><span data-stu-id="4a77c-132">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a77c-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="4a77c-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4a77c-134">传输</span><span class="sxs-lookup"><span data-stu-id="4a77c-134">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="4a77c-135">选择传输方式</span><span class="sxs-lookup"><span data-stu-id="4a77c-135">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="4a77c-136">绑定</span><span class="sxs-lookup"><span data-stu-id="4a77c-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4a77c-137">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="4a77c-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4a77c-138">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="4a77c-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
