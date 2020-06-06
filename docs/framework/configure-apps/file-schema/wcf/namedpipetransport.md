---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 00631ad88d771ed8f45638f28c84df05917fd3a0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736584"
---
# \<namedPipeTransport>
<span data-ttu-id="a55a5-101">定义传输，使通道在被包括到自定义绑定中时使用命名管道来传输消息。</span><span class="sxs-lookup"><span data-stu-id="a55a5-101">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="a55a5-102">语法</span><span class="sxs-lookup"><span data-stu-id="a55a5-102">Syntax</span></span>  
  
```xml  
<namedPipeTransport channelInitializationTimeout="TimeSpan"
                    connectionBufferSize="Integer"
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                    manualAddressing="Boolean"
                    maxBufferPoolSize="Integer"
                    maxBufferSize="Integer"
                    maxOutputDelay="TimeSpan"
                    maxPendingAccepts="Integer"
                    maxPendingConnections="Integer"
                    maxReceivedMessageSize="Integer"
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a55a5-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="a55a5-103">Attributes and Elements</span></span>  
<span data-ttu-id="a55a5-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a55a5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a55a5-105">特性</span><span class="sxs-lookup"><span data-stu-id="a55a5-105">Attributes</span></span>  
<span data-ttu-id="a55a5-106">无。</span><span class="sxs-lookup"><span data-stu-id="a55a5-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a55a5-107">子元素</span><span class="sxs-lookup"><span data-stu-id="a55a5-107">Child Elements</span></span>  
  
|<span data-ttu-id="a55a5-108">元素</span><span class="sxs-lookup"><span data-stu-id="a55a5-108">Element</span></span>|<span data-ttu-id="a55a5-109">说明</span><span class="sxs-lookup"><span data-stu-id="a55a5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a55a5-110">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="a55a5-110">ChannelInitializationTimeout</span></span>|<span data-ttu-id="a55a5-111">获取或设置确定通道在断开连接前可处于初始化状态的最长时间的 <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="a55a5-111">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="a55a5-112">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="a55a5-112">ConnectionBufferSize</span></span>|<span data-ttu-id="a55a5-113">获取或设置用于从客户端或服务传输网络上的序列化消息块的缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="a55a5-113">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="a55a5-114">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="a55a5-114">hostNameComparisonMode</span></span>|<span data-ttu-id="a55a5-115">获取或设置一个值，该值指示在对 URI 进行匹配时，是否使用主机名来访问服务。</span><span class="sxs-lookup"><span data-stu-id="a55a5-115">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="a55a5-116">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="a55a5-116">manualAddressing</span></span>|<span data-ttu-id="a55a5-117">获取或设置一个值，该值指示是否要求对消息进行手动寻址。</span><span class="sxs-lookup"><span data-stu-id="a55a5-117">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="a55a5-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="a55a5-118">maxBufferPoolSize</span></span>|<span data-ttu-id="a55a5-119">获取或设置传输消息使用的任何缓冲池的最大字节大小。</span><span class="sxs-lookup"><span data-stu-id="a55a5-119">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="a55a5-120">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="a55a5-120">maxBufferSize</span></span>|<span data-ttu-id="a55a5-121">获取或设置要使用的缓冲区的最大大小。</span><span class="sxs-lookup"><span data-stu-id="a55a5-121">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="a55a5-122">对于经过流处理的消息，该值最少应为以缓冲模式读取的消息头的最大可能大小。</span><span class="sxs-lookup"><span data-stu-id="a55a5-122">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="a55a5-123">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="a55a5-123">maxOutputDelay</span></span>|<span data-ttu-id="a55a5-124">获取或设置消息块或完整消息在发出之前可以在内存中保持缓冲的最大时间间隔。</span><span class="sxs-lookup"><span data-stu-id="a55a5-124">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="a55a5-125">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="a55a5-125">maxPendingAccepts</span></span>|<span data-ttu-id="a55a5-126">获取或设置服务可等待许可证处理至服务的传入连接的最大通道数量。</span><span class="sxs-lookup"><span data-stu-id="a55a5-126">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="a55a5-127">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="a55a5-127">maxPendingConnections</span></span>|<span data-ttu-id="a55a5-128">获取或设置在服务上等待调度的最大连接数。</span><span class="sxs-lookup"><span data-stu-id="a55a5-128">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="a55a5-129">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="a55a5-129">maxReceivedMessageSize</span></span>|<span data-ttu-id="a55a5-130">获取和设置允许接收的最大消息大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="a55a5-130">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="a55a5-131">transferMode</span><span class="sxs-lookup"><span data-stu-id="a55a5-131">transferMode</span></span>|<span data-ttu-id="a55a5-132">获取或设置一个值，该值指示通过面向连接的传输对消息进行缓冲还是流处理。</span><span class="sxs-lookup"><span data-stu-id="a55a5-132">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="a55a5-133">\<connectionPoolSettings>个\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="a55a5-133">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="a55a5-134">指定命名管道绑定的其他连接池设置。</span><span class="sxs-lookup"><span data-stu-id="a55a5-134">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a55a5-135">父元素</span><span class="sxs-lookup"><span data-stu-id="a55a5-135">Parent Elements</span></span>  
  
|<span data-ttu-id="a55a5-136">元素</span><span class="sxs-lookup"><span data-stu-id="a55a5-136">Element</span></span>|<span data-ttu-id="a55a5-137">说明</span><span class="sxs-lookup"><span data-stu-id="a55a5-137">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="a55a5-138">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="a55a5-138">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a55a5-139">注解</span><span class="sxs-lookup"><span data-stu-id="a55a5-139">Remarks</span></span>  
<span data-ttu-id="a55a5-140">此传输使用“net.pipe://hostname/path”形式的 URI。</span><span class="sxs-lookup"><span data-stu-id="a55a5-140">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="a55a5-141">其他 URI 组件是可选的。</span><span class="sxs-lookup"><span data-stu-id="a55a5-141">Other URI components are optional.</span></span>  
  
<span data-ttu-id="a55a5-142">`namedPipeTransport` 元素是创建实现命名管道传输协议的自定义绑定的起始点。</span><span class="sxs-lookup"><span data-stu-id="a55a5-142">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="a55a5-143">此传输用于计算机上的 WCF (Windows Communication Foundation) 到 WCF 的通信。</span><span class="sxs-lookup"><span data-stu-id="a55a5-143">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a55a5-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a55a5-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a55a5-145">传输</span><span class="sxs-lookup"><span data-stu-id="a55a5-145">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="a55a5-146">选择传输方式</span><span class="sxs-lookup"><span data-stu-id="a55a5-146">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="a55a5-147">绑定</span><span class="sxs-lookup"><span data-stu-id="a55a5-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a55a5-148">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="a55a5-148">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a55a5-149">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="a55a5-149">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
