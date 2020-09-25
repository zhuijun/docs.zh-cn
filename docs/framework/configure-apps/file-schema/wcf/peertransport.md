---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 68832c3a5bd4cc423642a6272e70cbecab86d6a8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181539"
---
# \<peerTransport>

<span data-ttu-id="cd59b-101">定义自定义绑定的对等传输。</span><span class="sxs-lookup"><span data-stu-id="cd59b-101">Defines a peer transport for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="cd59b-102">语法</span><span class="sxs-lookup"><span data-stu-id="cd59b-102">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd59b-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="cd59b-103">Attributes and Elements</span></span>  

 <span data-ttu-id="cd59b-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cd59b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd59b-105">特性</span><span class="sxs-lookup"><span data-stu-id="cd59b-105">Attributes</span></span>  
  
|<span data-ttu-id="cd59b-106">属性</span><span class="sxs-lookup"><span data-stu-id="cd59b-106">Attribute</span></span>|<span data-ttu-id="cd59b-107">描述</span><span class="sxs-lookup"><span data-stu-id="cd59b-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cd59b-108">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="cd59b-108">listenIpAddress</span></span>|<span data-ttu-id="cd59b-109">一个字符串，指定对等节点将在其上侦听 TCP 消息的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="cd59b-109">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="cd59b-110">默认为 `null`。</span><span class="sxs-lookup"><span data-stu-id="cd59b-110">The default is `null`.</span></span>|  
|<span data-ttu-id="cd59b-111">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="cd59b-111">maxBufferPoolSize</span></span>|<span data-ttu-id="cd59b-112">一个正整数，指定缓冲池的最大大小。</span><span class="sxs-lookup"><span data-stu-id="cd59b-112">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="cd59b-113">默认值为 524288。</span><span class="sxs-lookup"><span data-stu-id="cd59b-113">The default is 524288.</span></span><br /><br /> <span data-ttu-id="cd59b-114">WCF 的许多组件使用缓冲区。</span><span class="sxs-lookup"><span data-stu-id="cd59b-114">Many parts of WCF use buffers.</span></span> <span data-ttu-id="cd59b-115">每次使用缓冲区时，创建和销毁它们都将占用大量资源，而缓冲区的垃圾回收过程也是如此。</span><span class="sxs-lookup"><span data-stu-id="cd59b-115">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="cd59b-116">利用缓冲池，可以从缓冲池中获得缓冲区，使用缓冲区，然后在完成工作后将其返回给缓冲池。</span><span class="sxs-lookup"><span data-stu-id="cd59b-116">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="cd59b-117">这样就避免了创建和销毁缓冲区的系统开销。</span><span class="sxs-lookup"><span data-stu-id="cd59b-117">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="cd59b-118">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="cd59b-118">maxReceivedMessageSize</span></span>|<span data-ttu-id="cd59b-119">一个正整数，定义包括标头在内的最大消息大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="cd59b-119">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="cd59b-120">如果消息对于接收方而言太大，则消息发送方将收到 SOAP 错误。</span><span class="sxs-lookup"><span data-stu-id="cd59b-120">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="cd59b-121">接收方将删除该消息，并在跟踪日志中创建事件项。</span><span class="sxs-lookup"><span data-stu-id="cd59b-121">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="cd59b-122">默认值为 65536。</span><span class="sxs-lookup"><span data-stu-id="cd59b-122">The default is 65536.</span></span>|  
|<span data-ttu-id="cd59b-123">port</span><span class="sxs-lookup"><span data-stu-id="cd59b-123">port</span></span>|<span data-ttu-id="cd59b-124">一个整数，指定此绑定将用于处理对等通道 TCP 消息的网络接口端口。</span><span class="sxs-lookup"><span data-stu-id="cd59b-124">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="cd59b-125">该值必须介于 <xref:System.Net.IPEndPoint.MinPort> 和 <xref:System.Net.IPEndPoint.MaxPort> 之间。</span><span class="sxs-lookup"><span data-stu-id="cd59b-125">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="cd59b-126">默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="cd59b-126">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd59b-127">子元素</span><span class="sxs-lookup"><span data-stu-id="cd59b-127">Child Elements</span></span>  
  
|<span data-ttu-id="cd59b-128">元素</span><span class="sxs-lookup"><span data-stu-id="cd59b-128">Element</span></span>|<span data-ttu-id="cd59b-129">描述</span><span class="sxs-lookup"><span data-stu-id="cd59b-129">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="cd59b-130">定义此传输的安全设置。</span><span class="sxs-lookup"><span data-stu-id="cd59b-130">Defines the security settings for this transport.</span></span> <span data-ttu-id="cd59b-131">此元素的类型为 <xref:System.ServiceModel.Configuration.PeerSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="cd59b-131">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cd59b-132">父元素</span><span class="sxs-lookup"><span data-stu-id="cd59b-132">Parent Elements</span></span>  
  
|<span data-ttu-id="cd59b-133">元素</span><span class="sxs-lookup"><span data-stu-id="cd59b-133">Element</span></span>|<span data-ttu-id="cd59b-134">描述</span><span class="sxs-lookup"><span data-stu-id="cd59b-134">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="cd59b-135">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="cd59b-135">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd59b-136">备注</span><span class="sxs-lookup"><span data-stu-id="cd59b-136">Remarks</span></span>  

 <span data-ttu-id="cd59b-137">此传输不可用于包含请求/答复操作的协定。</span><span class="sxs-lookup"><span data-stu-id="cd59b-137">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd59b-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="cd59b-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="cd59b-139">传输</span><span class="sxs-lookup"><span data-stu-id="cd59b-139">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="cd59b-140">选择传输方式</span><span class="sxs-lookup"><span data-stu-id="cd59b-140">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="cd59b-141">绑定</span><span class="sxs-lookup"><span data-stu-id="cd59b-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cd59b-142">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="cd59b-142">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="cd59b-143">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="cd59b-143">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
