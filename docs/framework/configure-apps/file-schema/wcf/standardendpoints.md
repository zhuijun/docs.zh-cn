---
title: <standardEndpoints>
ms.date: 03/30/2017
ms.assetid: d62153d7-a6e6-462a-a784-cca61e9c2ba1
ms.openlocfilehash: 5d0607b5c541fc5ae402a50a0f8c464355b6b246
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157195"
---
# \<standardEndpoints>

<span data-ttu-id="67cd7-101">此配置节用于定义一个标准终结点集合，这些终结点是预配置的可重用终结点。</span><span class="sxs-lookup"><span data-stu-id="67cd7-101">This configuration section allows you to define a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="67cd7-102">标准终结点具有一个或多个设置为固定值的地址、绑定和协定特性。</span><span class="sxs-lookup"><span data-stu-id="67cd7-102">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="67cd7-103">例如，发现终结点具有固定的协定。</span><span class="sxs-lookup"><span data-stu-id="67cd7-103">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="67cd7-104">此外，还可以使用标准终结点用新属性扩展服务终结点，这与定义自定义绑定相似。</span><span class="sxs-lookup"><span data-stu-id="67cd7-104">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoints>**  
  
## <a name="syntax"></a><span data-ttu-id="67cd7-105">语法</span><span class="sxs-lookup"><span data-stu-id="67cd7-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67cd7-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="67cd7-106">Attributes and Elements</span></span>  

 <span data-ttu-id="67cd7-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="67cd7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67cd7-108">特性</span><span class="sxs-lookup"><span data-stu-id="67cd7-108">Attributes</span></span>  

 <span data-ttu-id="67cd7-109">无。</span><span class="sxs-lookup"><span data-stu-id="67cd7-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="67cd7-110">子元素</span><span class="sxs-lookup"><span data-stu-id="67cd7-110">Child Elements</span></span>  
  
|<span data-ttu-id="67cd7-111">元素</span><span class="sxs-lookup"><span data-stu-id="67cd7-111">Element</span></span>|<span data-ttu-id="67cd7-112">描述</span><span class="sxs-lookup"><span data-stu-id="67cd7-112">Description</span></span>|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|<span data-ttu-id="67cd7-113">定义具有固定公告协定的标准终结点。</span><span class="sxs-lookup"><span data-stu-id="67cd7-113">Defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="67cd7-114">当分别打开或关闭服务时，服务可以选择通过发送一条联机和脱机公告消息来公告其可用性。</span><span class="sxs-lookup"><span data-stu-id="67cd7-114">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="67cd7-115">Windows Communication Foundation (WCF) 服务指定元素中的公告终结点 [\<serviceDiscovery>](servicediscovery.md) ，并使用 AnnouncementClient 来执行公告。</span><span class="sxs-lookup"><span data-stu-id="67cd7-115">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="67cd7-116">希望侦听来自其他服务的公告的客户端实际充当 WCF 服务;因此，您必须在部分中配置该客户端的公告终结点 [\<services>](services.md) 。</span><span class="sxs-lookup"><span data-stu-id="67cd7-116">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](services.md) section.</span></span>|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|<span data-ttu-id="67cd7-117">定义具有固定发现协定的标准终结点。</span><span class="sxs-lookup"><span data-stu-id="67cd7-117">Defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="67cd7-118">将此元素添加到服务配置后，该元素将指定侦听发现消息的位置。</span><span class="sxs-lookup"><span data-stu-id="67cd7-118">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="67cd7-119">将此元素添加到客户端配置后，该元素将指定发送发现查询的位置。</span><span class="sxs-lookup"><span data-stu-id="67cd7-119">When added to the client configuration it specifies where to send the discovery queries.</span></span>|  
|[\<dynamicEndpoint>](dynamicendpoint.md)|<span data-ttu-id="67cd7-120">此配置元素定义一个标准终结点，应用程序通过利用该终结点包含的信息，能够充当可在运行时动态查找终结点地址的客户端程序。</span><span class="sxs-lookup"><span data-stu-id="67cd7-120">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
|[\<mexEndpoint>](mexendpoint.md)|<span data-ttu-id="67cd7-121">定义具有固定 IMetadataExchange 协定的标准终结点。</span><span class="sxs-lookup"><span data-stu-id="67cd7-121">Defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="67cd7-122">由于所有元数据交换终结点都指定 IMetadataExchange 作为其协定，因此可以使用此标准终结点，而不必定义您自己的终结点。</span><span class="sxs-lookup"><span data-stu-id="67cd7-122">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>|  
|[\<udpAnnouncementEndpoint>](udpannouncementendpoint.md)|<span data-ttu-id="67cd7-123">定义由服务用于通过 UDP 绑定发送公告消息的标准终结点。</span><span class="sxs-lookup"><span data-stu-id="67cd7-123">Defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="67cd7-124">它具有固定协定并支持两个发现版本。</span><span class="sxs-lookup"><span data-stu-id="67cd7-124">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="67cd7-125">此外，根据 WS-Discovery 规范（WS-Discovery 2005 年 4 月版或 WS-Discovery 1.1 版）中的规定，它还具有固定 UDP 绑定和默认地址值。</span><span class="sxs-lookup"><span data-stu-id="67cd7-125">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="67cd7-126">您可以指定用于发送和接收公告消息的多播地址。</span><span class="sxs-lookup"><span data-stu-id="67cd7-126">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>|  
|[\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md)|<span data-ttu-id="67cd7-127">定义通过 UDP 多播绑定为发现操作预先配置的标准终结点。</span><span class="sxs-lookup"><span data-stu-id="67cd7-127">Defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="67cd7-128">此终结点具有固定协定并支持两个 WS-Discovery 协议版本。</span><span class="sxs-lookup"><span data-stu-id="67cd7-128">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="67cd7-129">此外，根据 WS-Discovery 规范（WS-Discovery 2005 年 4 月版或 WS-Discovery 1.1 版）中的规定，它还具有固定 UDP 绑定和默认地址。</span><span class="sxs-lookup"><span data-stu-id="67cd7-129">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>|  
|[\<webHttpEndpoint>](webhttpendpoint.md)|<span data-ttu-id="67cd7-130">定义具有 [\<webHttpBinding>](webhttpbinding.md) 自动添加行为的固定绑定的标准终结点 [\<webHttp>](webhttp.md) 。</span><span class="sxs-lookup"><span data-stu-id="67cd7-130">Defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="67cd7-131">在编写 REST 服务时，请使用此终结点。</span><span class="sxs-lookup"><span data-stu-id="67cd7-131">Use this endpoint when writing a REST service.</span></span>|  
|[\<webScriptEndpoint>](webscriptendpoint.md)|<span data-ttu-id="67cd7-132">定义具有 [\<webHttpBinding>](webhttpbinding.md) 自动添加行为的固定绑定的标准终结点 [\<enableWebScript>](enablewebscript.md) 。</span><span class="sxs-lookup"><span data-stu-id="67cd7-132">Defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="67cd7-133">在编写从 ASP.NET AJAX 应用程序中调用的服务时，请使用此终结点。</span><span class="sxs-lookup"><span data-stu-id="67cd7-133">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>|  
|[\<workflowControlEndpoint>](workflowcontrolendpoint.md)|<span data-ttu-id="67cd7-134">定义用于控制工作流实例的执行（创建、运行、挂起、终止等）的标准终结点。</span><span class="sxs-lookup"><span data-stu-id="67cd7-134">Defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="67cd7-135">父元素</span><span class="sxs-lookup"><span data-stu-id="67cd7-135">Parent Elements</span></span>  
  
|<span data-ttu-id="67cd7-136">元素</span><span class="sxs-lookup"><span data-stu-id="67cd7-136">Element</span></span>|<span data-ttu-id="67cd7-137">描述</span><span class="sxs-lookup"><span data-stu-id="67cd7-137">Description</span></span>|  
|-------------|-----------------|  
|\<system.ServiceModel>|<span data-ttu-id="67cd7-138">所有 WCF 配置元素的根元素。</span><span class="sxs-lookup"><span data-stu-id="67cd7-138">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67cd7-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="67cd7-139">See also</span></span>

- [<span data-ttu-id="67cd7-140">标准终结点</span><span class="sxs-lookup"><span data-stu-id="67cd7-140">Standard Endpoints</span></span>](../../../wcf/feature-details/standard-endpoints.md)
