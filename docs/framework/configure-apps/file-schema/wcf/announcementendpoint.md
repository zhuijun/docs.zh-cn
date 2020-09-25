---
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: f68972cdf0e55f92fd4856aff912f00db7c62be4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201611"
---
# \<announcementEndpoint>

<span data-ttu-id="e43dc-101">此配置元素定义具有固定公告协定的标准终结点。</span><span class="sxs-lookup"><span data-stu-id="e43dc-101">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="e43dc-102">当分别打开或关闭服务时，服务可以选择通过发送一条联机和脱机公告消息来公告其可用性。</span><span class="sxs-lookup"><span data-stu-id="e43dc-102">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="e43dc-103">Windows Communication Foundation (WCF) 服务指定元素中的公告终结点 [\<serviceDiscovery>](servicediscovery.md) ，并使用 AnnouncementClient 来执行公告。</span><span class="sxs-lookup"><span data-stu-id="e43dc-103">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="e43dc-104">希望侦听来自其他服务的公告的客户端实际充当 WCF 服务;因此，您必须在部分中配置该客户端的公告终结点 [\<services>](services.md) 。</span><span class="sxs-lookup"><span data-stu-id="e43dc-104">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](services.md) section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<announcementEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="e43dc-105">语法</span><span class="sxs-lookup"><span data-stu-id="e43dc-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e43dc-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e43dc-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e43dc-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e43dc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e43dc-108">特性</span><span class="sxs-lookup"><span data-stu-id="e43dc-108">Attributes</span></span>  
  
|<span data-ttu-id="e43dc-109">属性</span><span class="sxs-lookup"><span data-stu-id="e43dc-109">Attribute</span></span>|<span data-ttu-id="e43dc-110">描述</span><span class="sxs-lookup"><span data-stu-id="e43dc-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e43dc-111">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="e43dc-111">discoveryVersion</span></span>|<span data-ttu-id="e43dc-112">一个字符串，指定两个 WS-Discovery 协议版本中的其中一个版本。</span><span class="sxs-lookup"><span data-stu-id="e43dc-112">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="e43dc-113">有效值为 WSDiscovery11 和 WSDiscoveryApril2005。</span><span class="sxs-lookup"><span data-stu-id="e43dc-113">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="e43dc-114">此值的类型为 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>。</span><span class="sxs-lookup"><span data-stu-id="e43dc-114">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="e43dc-115">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="e43dc-115">maxAnnouncementDelay</span></span>|<span data-ttu-id="e43dc-116">一个 Timespan 值，指定 Discovery 协议在发送 Hello 消息之前等待的最大延迟值。</span><span class="sxs-lookup"><span data-stu-id="e43dc-116">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="e43dc-117">消息在发送之前将等待一个随机时间值（介于 0 到此特性值之间）。</span><span class="sxs-lookup"><span data-stu-id="e43dc-117">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="e43dc-118">此特性用于设置随机的短时间延迟，以防止在网络出现故障后所有服务同时重新联机所造成的网络风暴。</span><span class="sxs-lookup"><span data-stu-id="e43dc-118">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="e43dc-119">name</span><span class="sxs-lookup"><span data-stu-id="e43dc-119">name</span></span>|<span data-ttu-id="e43dc-120">一个字符串，指定标准终结点的配置的名称。</span><span class="sxs-lookup"><span data-stu-id="e43dc-120">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="e43dc-121">此名称在服务终结点的 `endpointConfiguration` 特性中用于将标准终结点链接到其配置。</span><span class="sxs-lookup"><span data-stu-id="e43dc-121">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e43dc-122">子元素</span><span class="sxs-lookup"><span data-stu-id="e43dc-122">Child Elements</span></span>  

 <span data-ttu-id="e43dc-123">无。</span><span class="sxs-lookup"><span data-stu-id="e43dc-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e43dc-124">父元素</span><span class="sxs-lookup"><span data-stu-id="e43dc-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e43dc-125">元素</span><span class="sxs-lookup"><span data-stu-id="e43dc-125">Element</span></span>|<span data-ttu-id="e43dc-126">描述</span><span class="sxs-lookup"><span data-stu-id="e43dc-126">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="e43dc-127">具有一个或多个固定属性（地址、绑定和协定）的预定义终结点的标准终结点集合。</span><span class="sxs-lookup"><span data-stu-id="e43dc-127">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e43dc-128">示例</span><span class="sxs-lookup"><span data-stu-id="e43dc-128">Example</span></span>  

 <span data-ttu-id="e43dc-129">下面的示例演示通过 http 和对等网络侦听公告消息的客户端。</span><span class="sxs-lookup"><span data-stu-id="e43dc-129">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="httpAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="basicHttpBinding"
              address="announcements" />
    <endpoint name="peerNetAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  ...
  </service>
</services>

<standardEndpoints>
  <announcementEndpoint>
    <standardEndpoint name="httpAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
    <standardEndpoint name="peerNetAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
  </announcementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="e43dc-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="e43dc-130">See also</span></span>

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
