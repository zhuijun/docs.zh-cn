---
title: <udpTransportSettings>
ms.date: 03/30/2017
ms.assetid: 842d92e9-6199-4ec5-b2d1-58533054e1f0
ms.openlocfilehash: ed59a139ac21e7cfb4400d17f1fc6a0fa3096641
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183671"
---
# \<udpTransportSettings>

<span data-ttu-id="0f810-101">此配置元素公开的 UDP 传输设置 [\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md) 。</span><span class="sxs-lookup"><span data-stu-id="0f810-101">This configuration element exposes UDP transport settings for [\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<udpDiscoveryEndpoint>**](udpdiscoveryendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<updTransportSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="0f810-102">语法</span><span class="sxs-lookup"><span data-stu-id="0f810-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint>
        <updTransportSettings duplicateMessageHistoryLength="Integer"
                              maxBufferPoolSize="Integer"
                              maxMulticastRetransmitCount="Integer"
                              maxPendingMessageCount="Integer"
                              maxReceivedMessageSize="Integer"
                              maxUnicastRetransmitCount="Integer"
                              multicastInterfaceId="String"
                              socketReceiveBufferSize="Integer"
                              timeToLive="Integer" />
      </standardEndpoint>
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f810-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0f810-103">Attributes and Elements</span></span>  

 <span data-ttu-id="0f810-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0f810-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f810-105">特性</span><span class="sxs-lookup"><span data-stu-id="0f810-105">Attributes</span></span>  
  
|<span data-ttu-id="0f810-106">属性</span><span class="sxs-lookup"><span data-stu-id="0f810-106">Attribute</span></span>|<span data-ttu-id="0f810-107">描述</span><span class="sxs-lookup"><span data-stu-id="0f810-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0f810-108">duplicateMessageHistoryLength</span><span class="sxs-lookup"><span data-stu-id="0f810-108">duplicateMessageHistoryLength</span></span>|<span data-ttu-id="0f810-109">一个整数，指定传输用于标识重复消息的最大消息哈希数。</span><span class="sxs-lookup"><span data-stu-id="0f810-109">An integer that specifies the maximum number of message hashes used by the transport for identifying duplicate messages.</span></span>  <span data-ttu-id="0f810-110">将在 TransportManager 级别进行重复检测。</span><span class="sxs-lookup"><span data-stu-id="0f810-110">Duplicate detection will be done at the TransportManager level.</span></span> <span data-ttu-id="0f810-111">将此属性设置为 0 即可禁用重复检测。</span><span class="sxs-lookup"><span data-stu-id="0f810-111">Setting this property to 0 disables duplicate detection.</span></span><br /><br /> <span data-ttu-id="0f810-112">系统管理员或开发人员可以使用此特性关闭重复消息检测算法。</span><span class="sxs-lookup"><span data-stu-id="0f810-112">This attribute allows system administrators or developers to turn off duplicate message detection algorithms.</span></span> <span data-ttu-id="0f810-113">如果您希望实现自己的重复检测算法，可能需要这一功能。</span><span class="sxs-lookup"><span data-stu-id="0f810-113">This may be desirable if you want to implement your own duplicate detection algorithm.</span></span><br /><br /> <span data-ttu-id="0f810-114">默认值为 4112。</span><span class="sxs-lookup"><span data-stu-id="0f810-114">The default is 4112.</span></span>|  
|<span data-ttu-id="0f810-115">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="0f810-115">maxBufferPoolSize</span></span>|<span data-ttu-id="0f810-116">一个整数，指定传输使用的任何缓冲池的最大大小。</span><span class="sxs-lookup"><span data-stu-id="0f810-116">An integer that specifies the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="0f810-117">maxMulticastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="0f810-117">maxMulticastRetransmitCount</span></span>|<span data-ttu-id="0f810-118">一个整数，指定应重新传输消息的最大次数（包括第一次发送）。</span><span class="sxs-lookup"><span data-stu-id="0f810-118">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span><br /><br /> <span data-ttu-id="0f810-119">默认值为 2。</span><span class="sxs-lookup"><span data-stu-id="0f810-119">The default is 2.</span></span>|  
|<span data-ttu-id="0f810-120">maxPendingMessageCount</span><span class="sxs-lookup"><span data-stu-id="0f810-120">maxPendingMessageCount</span></span>|<span data-ttu-id="0f810-121">一个整数，指定已经接收但尚未从单个通道实例的 InputQueue 中移除的最大消息数。</span><span class="sxs-lookup"><span data-stu-id="0f810-121">An integer that specifies the maximum number of messages that have been received but not yet removed from the InputQueue for an individual channel instance.</span></span>  <span data-ttu-id="0f810-122">如果 InputQueue 已达到挂起消息计数上限，则将丢弃消息。</span><span class="sxs-lookup"><span data-stu-id="0f810-122">If the InputQueue has hit its pending message count limit, the message will be dropped.</span></span><br /><br /> <span data-ttu-id="0f810-123">默认值为 32。</span><span class="sxs-lookup"><span data-stu-id="0f810-123">The default is 32.</span></span>|  
|<span data-ttu-id="0f810-124">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="0f810-124">maxReceivedMessageSize</span></span>|<span data-ttu-id="0f810-125">一个整数，指定绑定可处理的消息的最大大小。</span><span class="sxs-lookup"><span data-stu-id="0f810-125">An integer that specifies the maximum size for a message that can be processed by the binding.</span></span><br /><br /> <span data-ttu-id="0f810-126">默认值为 65507。</span><span class="sxs-lookup"><span data-stu-id="0f810-126">The default value is 65507.</span></span>|  
|<span data-ttu-id="0f810-127">maxUnicastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="0f810-127">maxUnicastRetransmitCount</span></span>|<span data-ttu-id="0f810-128">一个整数，指定应重新传输消息的最大次数（包括第一次发送）。</span><span class="sxs-lookup"><span data-stu-id="0f810-128">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span>  <span data-ttu-id="0f810-129">如果将消息发送到单播地址，并且收到的响应消息中带有相应的 RelatesTo 标头，重新传输可能会提前终止（在达到配置的重新传输次数之前）。</span><span class="sxs-lookup"><span data-stu-id="0f810-129">If the message is sent to a unicast address and a response message is received with a corresponding RelatesTo header, then retransmission may terminate early (before retransmitting the configured number of times).</span></span><br /><br /> <span data-ttu-id="0f810-130">默认值为 1。</span><span class="sxs-lookup"><span data-stu-id="0f810-130">The default value is 1.</span></span>|  
|<span data-ttu-id="0f810-131">multicastInterfaceId</span><span class="sxs-lookup"><span data-stu-id="0f810-131">multicastInterfaceId</span></span>|<span data-ttu-id="0f810-132">一个字符串，唯一标识在多宿主计算机上发送和接收多播流量时应使用的网络适配器。</span><span class="sxs-lookup"><span data-stu-id="0f810-132">A string that uniquely identifies the network adapter that should be used when sending and receiving multicast traffic on multi-homed machines.</span></span> <span data-ttu-id="0f810-133">在运行时，传输将使用此特性值来查找接口索引，然后使用该索引设置 `IP_MULTICAST_IF` 和 `IPV6_MULTICAST_IF` 套接字选项。</span><span class="sxs-lookup"><span data-stu-id="0f810-133">At runtime, the transport will use this attribute value to lookup the interface index, which is then used to set the `IP_MULTICAST_IF` and `IPV6_MULTICAST_IF` socket options.</span></span>  <span data-ttu-id="0f810-134">加入多播组时将使用相同的接口索引（如果适用）。</span><span class="sxs-lookup"><span data-stu-id="0f810-134">The same interface index will be used when joining a multicast group, if applicable.</span></span><br /><br /> <span data-ttu-id="0f810-135">默认值是 `null`。</span><span class="sxs-lookup"><span data-stu-id="0f810-135">The default value is `null`.</span></span>|  
|<span data-ttu-id="0f810-136">socketReceiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="0f810-136">socketReceiveBufferSize</span></span>|<span data-ttu-id="0f810-137">一个整数，指定基础 WinSock 套接字上接收缓冲区的大小。</span><span class="sxs-lookup"><span data-stu-id="0f810-137">An integer that specifies the receive buffer size on the underlying WinSock socket.</span></span><br /><br /> <span data-ttu-id="0f810-138">接收通道的用户可以对绑定使用此特性，以控制系统在接收数据时的行为。</span><span class="sxs-lookup"><span data-stu-id="0f810-138">A user of a receiving channel can use this attribute on the Binding to control how the system behaves when it receives data.</span></span>  <span data-ttu-id="0f810-139">例如，假定应用程序使用入站 WCF 消息时达到了最大阈值，对此特性使用较高的值将允许消息在等待应用程序处理时在 WinSock 缓冲区中堆叠。</span><span class="sxs-lookup"><span data-stu-id="0f810-139">For example, given an application that is consuming inbound WCF messages at the maximum threshold, using a higher value for this attribute would allow messages to stack up in the WinSock buffer while waiting for the application to be able to process them.</span></span>  <span data-ttu-id="0f810-140">在同样的情况下，使用较低的值将导致消息被丢弃。</span><span class="sxs-lookup"><span data-stu-id="0f810-140">Using a lower value in the same situation would result in messages getting dropped.</span></span> <span data-ttu-id="0f810-141">此属性公开基础 WinSock `SO_RCVBUF` 套接字选项。此属性值必须至少为的大小 `maxReceivedMessageSize` 。</span><span class="sxs-lookup"><span data-stu-id="0f810-141">This attribute exposes the underlying WinSock `SO_RCVBUF` socket option.This attribute value must be at least the size of `maxReceivedMessageSize`.</span></span>   <span data-ttu-id="0f810-142">如果将其设置为小于的值，则 `maxReceivedMessageSize` 会导致运行时异常。</span><span class="sxs-lookup"><span data-stu-id="0f810-142">Setting it to a value smaller than the `maxReceivedMessageSize` will result in a runtime exception.</span></span><br /><br /> <span data-ttu-id="0f810-143">默认值为 65536。</span><span class="sxs-lookup"><span data-stu-id="0f810-143">The default value is 65536.</span></span>|  
|<span data-ttu-id="0f810-144">timeToLive</span><span class="sxs-lookup"><span data-stu-id="0f810-144">timeToLive</span></span>|<span data-ttu-id="0f810-145">一个整数，指定多播数据包可以遍历的网络段跃点数。</span><span class="sxs-lookup"><span data-stu-id="0f810-145">An integer that specifies the number of network segment hops that a multicast packet can traverse.</span></span>  <span data-ttu-id="0f810-146">此特性公开与 `IP_MULTICAST_TTL` 和 `IP_TTL` 套接字选项关联的功能。</span><span class="sxs-lookup"><span data-stu-id="0f810-146">This attribute exposes the functionality associated with the `IP_MULTICAST_TTL` and `IP_TTL` socket options.</span></span><br /><br /> <span data-ttu-id="0f810-147">默认值为 1。</span><span class="sxs-lookup"><span data-stu-id="0f810-147">The default value is 1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f810-148">子元素</span><span class="sxs-lookup"><span data-stu-id="0f810-148">Child Elements</span></span>  

 <span data-ttu-id="0f810-149">无。</span><span class="sxs-lookup"><span data-stu-id="0f810-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0f810-150">父元素</span><span class="sxs-lookup"><span data-stu-id="0f810-150">Parent Elements</span></span>  
  
|<span data-ttu-id="0f810-151">元素</span><span class="sxs-lookup"><span data-stu-id="0f810-151">Element</span></span>|<span data-ttu-id="0f810-152">描述</span><span class="sxs-lookup"><span data-stu-id="0f810-152">Description</span></span>|  
|-------------|-----------------|  
|[\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md)|<span data-ttu-id="0f810-153">具有固定发现协定和 UDP 传输绑定的标准终结点。</span><span class="sxs-lookup"><span data-stu-id="0f810-153">A standard endpoint that has fixed discovery contract and UDP transport binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f810-154">请参阅</span><span class="sxs-lookup"><span data-stu-id="0f810-154">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpTransportSettings>
