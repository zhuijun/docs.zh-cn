---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 6cfddfb9ebfc7c3447af977e14738baabebc8fe9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177843"
---
# \<webSocketSettings>

<span data-ttu-id="0108c-101">用来指定 Web Socket 设置的配置元素。</span><span class="sxs-lookup"><span data-stu-id="0108c-101">A configuration element used to specify Web Socket settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="0108c-102">语法</span><span class="sxs-lookup"><span data-stu-id="0108c-102">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="Boolean"
                       disablePayloadMasking="Boolean"
                       keepAliveInterval="TimeSpan"
                       maxPendingConnections="Integer"
                       receiveBufferSize="Integer"
                       sendBufferSize="Integer"
                       subProtocol="String"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0108c-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0108c-103">Attributes and Elements</span></span>  

 <span data-ttu-id="0108c-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0108c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0108c-105">特性</span><span class="sxs-lookup"><span data-stu-id="0108c-105">Attributes</span></span>  
  
|<span data-ttu-id="0108c-106">属性</span><span class="sxs-lookup"><span data-stu-id="0108c-106">Attribute</span></span>|<span data-ttu-id="0108c-107">描述</span><span class="sxs-lookup"><span data-stu-id="0108c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0108c-108">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="0108c-108">createNotificationOnConnection</span></span>|<span data-ttu-id="0108c-109">指定是否在连接时发送通知。</span><span class="sxs-lookup"><span data-stu-id="0108c-109">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="0108c-110">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="0108c-110">disablePayloadMasking</span></span>|<span data-ttu-id="0108c-111">指定是否禁用 Web Socket 掩码。</span><span class="sxs-lookup"><span data-stu-id="0108c-111">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="0108c-112">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="0108c-112">keepAliveInterval</span></span>|<span data-ttu-id="0108c-113">指定保持活动状态的间隔。</span><span class="sxs-lookup"><span data-stu-id="0108c-113">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="0108c-114">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="0108c-114">maxPendingConnections</span></span>|<span data-ttu-id="0108c-115">指定服务上等待调度的最大连接数。</span><span class="sxs-lookup"><span data-stu-id="0108c-115">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="0108c-116">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="0108c-116">receiveBufferSize</span></span>|<span data-ttu-id="0108c-117">指定接收缓冲区的大小。</span><span class="sxs-lookup"><span data-stu-id="0108c-117">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="0108c-118">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="0108c-118">sendBufferSize</span></span>|<span data-ttu-id="0108c-119">指定发送缓冲区的大小。</span><span class="sxs-lookup"><span data-stu-id="0108c-119">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="0108c-120">subProtocol</span><span class="sxs-lookup"><span data-stu-id="0108c-120">subProtocol</span></span>|<span data-ttu-id="0108c-121">指定 Web Socket 子协议。</span><span class="sxs-lookup"><span data-stu-id="0108c-121">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="0108c-122">transportUsage</span><span class="sxs-lookup"><span data-stu-id="0108c-122">transportUsage</span></span>|<span data-ttu-id="0108c-123">指定何时使用 Web Socket。</span><span class="sxs-lookup"><span data-stu-id="0108c-123">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="0108c-124">transportUsage 特性</span><span class="sxs-lookup"><span data-stu-id="0108c-124">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="0108c-125">值</span><span class="sxs-lookup"><span data-stu-id="0108c-125">Value</span></span>|<span data-ttu-id="0108c-126">描述</span><span class="sxs-lookup"><span data-stu-id="0108c-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0108c-127">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="0108c-127">WhenDuplex</span></span>|<span data-ttu-id="0108c-128">如果为双工协定，则使用 Web Socket 协议。</span><span class="sxs-lookup"><span data-stu-id="0108c-128">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="0108c-129">始终</span><span class="sxs-lookup"><span data-stu-id="0108c-129">Always</span></span>|<span data-ttu-id="0108c-130">始终使用 Web Socket 协议，而不管协定类型。</span><span class="sxs-lookup"><span data-stu-id="0108c-130">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="0108c-131">从不</span><span class="sxs-lookup"><span data-stu-id="0108c-131">Never</span></span>|<span data-ttu-id="0108c-132">永远不使用 Web Socket 协议。</span><span class="sxs-lookup"><span data-stu-id="0108c-132">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0108c-133">子元素</span><span class="sxs-lookup"><span data-stu-id="0108c-133">Child Elements</span></span>  

 <span data-ttu-id="0108c-134">无</span><span class="sxs-lookup"><span data-stu-id="0108c-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0108c-135">父元素</span><span class="sxs-lookup"><span data-stu-id="0108c-135">Parent Elements</span></span>  
  
|<span data-ttu-id="0108c-136">元素</span><span class="sxs-lookup"><span data-stu-id="0108c-136">Element</span></span>|<span data-ttu-id="0108c-137">描述</span><span class="sxs-lookup"><span data-stu-id="0108c-137">Description</span></span>|  
|-------------|-----------------|  
|\<netHttpBinding>|<span data-ttu-id="0108c-138">指定 NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="0108c-138">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0108c-139">示例</span><span class="sxs-lookup"><span data-stu-id="0108c-139">Example</span></span>  

 <span data-ttu-id="0108c-140">下面的示例演示如何使用 \<webSocketSettings> 元素。</span><span class="sxs-lookup"><span data-stu-id="0108c-140">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="true"
                       disablePayloadMasking="false"
                       keepAliveInterval="00:10:00"
                       maxPendingConnections="100"
                       receiveBufferSize="1000"
                       sendBufferSize="1000"
                       subProtocol="Soap"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="0108c-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="0108c-141">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="0108c-142">绑定</span><span class="sxs-lookup"><span data-stu-id="0108c-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0108c-143">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="0108c-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0108c-144">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="0108c-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
