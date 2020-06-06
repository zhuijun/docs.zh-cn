---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: ad87a5876381a7224341babdb076c85edcd1dd87
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399563"
---
# \<serviceThrottling>
<span data-ttu-id="eec12-101">指定 Windows Communication Foundation (WCF) 服务的限制机制。</span><span class="sxs-lookup"><span data-stu-id="eec12-101">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceThrottling>**  
  
## <a name="syntax"></a><span data-ttu-id="eec12-102">语法</span><span class="sxs-lookup"><span data-stu-id="eec12-102">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eec12-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="eec12-103">Attributes and Elements</span></span>  
 <span data-ttu-id="eec12-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="eec12-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eec12-105">特性</span><span class="sxs-lookup"><span data-stu-id="eec12-105">Attributes</span></span>  
  
|<span data-ttu-id="eec12-106">属性</span><span class="sxs-lookup"><span data-stu-id="eec12-106">Attribute</span></span>|<span data-ttu-id="eec12-107">说明</span><span class="sxs-lookup"><span data-stu-id="eec12-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eec12-108">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="eec12-108">maxConcurrentCalls</span></span>|<span data-ttu-id="eec12-109">一个正整数，用于限制当前在整个 <xref:System.ServiceModel.ServiceHost> 中处理的消息数目。</span><span class="sxs-lookup"><span data-stu-id="eec12-109">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="eec12-110">超出此限制的调用将在队列中排队。</span><span class="sxs-lookup"><span data-stu-id="eec12-110">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="eec12-111">将此值设置为 0 与将其设置为 Int32.MaxValue 等效。</span><span class="sxs-lookup"><span data-stu-id="eec12-111">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="eec12-112">默认值是 16 \* 处理器计数。</span><span class="sxs-lookup"><span data-stu-id="eec12-112">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="eec12-113">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="eec12-113">maxConcurrentInstances</span></span>|<span data-ttu-id="eec12-114">一个正整数，用于限制在整个 <xref:System.ServiceModel.InstanceContext> 中一次执行的 <xref:System.ServiceModel.ServiceHost> 对象数。</span><span class="sxs-lookup"><span data-stu-id="eec12-114">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="eec12-115">用于创建其他实例的请求将会排队，并在出现低于该限值的槽时完成。</span><span class="sxs-lookup"><span data-stu-id="eec12-115">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="eec12-116">默认值是 maxConcurrentSessions 和 MaxConcurrentCalls 的和</span><span class="sxs-lookup"><span data-stu-id="eec12-116">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="eec12-117">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="eec12-117">maxConcurrentSessions</span></span>|<span data-ttu-id="eec12-118">一个正整数，用于限制 <xref:System.ServiceModel.ServiceHost> 对象可以接受的会话数。</span><span class="sxs-lookup"><span data-stu-id="eec12-118">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="eec12-119">此服务将接受超出限制的连接，但是，只有处于限制范围之内的通道处于活动状态（会从此通道中读取消息）。</span><span class="sxs-lookup"><span data-stu-id="eec12-119">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="eec12-120">将此值设置为 0 与将其设置为 Int32.MaxValue 等效。</span><span class="sxs-lookup"><span data-stu-id="eec12-120">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="eec12-121">默认值是 100 \* 处理器计数。</span><span class="sxs-lookup"><span data-stu-id="eec12-121">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eec12-122">子元素</span><span class="sxs-lookup"><span data-stu-id="eec12-122">Child Elements</span></span>  
 <span data-ttu-id="eec12-123">无。</span><span class="sxs-lookup"><span data-stu-id="eec12-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eec12-124">父元素</span><span class="sxs-lookup"><span data-stu-id="eec12-124">Parent Elements</span></span>  
  
|<span data-ttu-id="eec12-125">元素</span><span class="sxs-lookup"><span data-stu-id="eec12-125">Element</span></span>|<span data-ttu-id="eec12-126">描述</span><span class="sxs-lookup"><span data-stu-id="eec12-126">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="eec12-127">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="eec12-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eec12-128">注解</span><span class="sxs-lookup"><span data-stu-id="eec12-128">Remarks</span></span>  
 <span data-ttu-id="eec12-129">限制控件会对并发调用、实例或会话的数目施加限制以防止过度使用资源。</span><span class="sxs-lookup"><span data-stu-id="eec12-129">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="eec12-130">每次达到属性值时，就会记录一个跟踪。</span><span class="sxs-lookup"><span data-stu-id="eec12-130">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="eec12-131">第一个跟踪将记录为警告。</span><span class="sxs-lookup"><span data-stu-id="eec12-131">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eec12-132">示例</span><span class="sxs-lookup"><span data-stu-id="eec12-132">Example</span></span>  
 <span data-ttu-id="eec12-133">下面的配置示例指定服务将最大并发调用数限制为 2，并将最大并发实例数限制为 10。</span><span class="sxs-lookup"><span data-stu-id="eec12-133">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="eec12-134">有关运行此示例的详细示例，请参阅[限制](../../../wcf/samples/throttling.md)。</span><span class="sxs-lookup"><span data-stu-id="eec12-134">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDebug includeExceptionDetailInFaults="False" />
      <serviceMetadata httpGetEnabled="True" />
      <!-- Specify throttling behavior -->
      <serviceThrottling maxConcurrentCalls="2"
                         maxConcurrentInstances="10" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="eec12-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eec12-135">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="eec12-136">使用 ServiceThrottlingBehavior 控制 WCF 服务性能</span><span class="sxs-lookup"><span data-stu-id="eec12-136">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
