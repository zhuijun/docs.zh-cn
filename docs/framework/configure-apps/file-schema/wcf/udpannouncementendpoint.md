---
title: <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: 8dabf8845126705d082d080b643688ed62883f39
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854914"
---
# \<udpAnnouncementEndpoint>
<span data-ttu-id="c1929-101">此配置元素定义服务通过 UDP 绑定发送公告消息所使用的标准终结点。</span><span class="sxs-lookup"><span data-stu-id="c1929-101">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="c1929-102">它具有固定协定并支持两个发现版本。</span><span class="sxs-lookup"><span data-stu-id="c1929-102">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="c1929-103">此外，根据 WS-Discovery 规范（WS-Discovery 2005 年 4 月版或 WS-Discovery 1.1 版）中的规定，它还具有固定 UDP 绑定和默认地址值。</span><span class="sxs-lookup"><span data-stu-id="c1929-103">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="c1929-104">您可以指定用于发送和接收公告消息的多播地址。</span><span class="sxs-lookup"><span data-stu-id="c1929-104">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpAnnouncementEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="c1929-105">语法</span><span class="sxs-lookup"><span data-stu-id="c1929-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1929-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c1929-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c1929-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c1929-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1929-108">特性</span><span class="sxs-lookup"><span data-stu-id="c1929-108">Attributes</span></span>  
  
|<span data-ttu-id="c1929-109">属性</span><span class="sxs-lookup"><span data-stu-id="c1929-109">Attribute</span></span>|<span data-ttu-id="c1929-110">说明</span><span class="sxs-lookup"><span data-stu-id="c1929-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c1929-111">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="c1929-111">discoveryVersion</span></span>|<span data-ttu-id="c1929-112">一个字符串，指定两个 WS-Discovery 协议版本中的其中一个版本。</span><span class="sxs-lookup"><span data-stu-id="c1929-112">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="c1929-113">有效值为 WSDiscovery11 和 WSDiscoveryApril2005。</span><span class="sxs-lookup"><span data-stu-id="c1929-113">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="c1929-114">此值的类型为 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>。</span><span class="sxs-lookup"><span data-stu-id="c1929-114">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="c1929-115">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="c1929-115">maxAnnouncementDelay</span></span>|<span data-ttu-id="c1929-116">一个 Timespan 值，指定 Discovery 协议在发送 Hello 消息之前等待的最大延迟值。</span><span class="sxs-lookup"><span data-stu-id="c1929-116">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="c1929-117">消息在发送之前将等待一个随机时间值（介于 0 到此特性值之间）。</span><span class="sxs-lookup"><span data-stu-id="c1929-117">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="c1929-118">此特性用于设置随机的短时间延迟，以防止在网络出现故障后所有服务同时重新联机所造成的网络风暴。</span><span class="sxs-lookup"><span data-stu-id="c1929-118">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="c1929-119">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="c1929-119">multicastAddress</span></span>|<span data-ttu-id="c1929-120">一个 URI，指定用于发送和接收发现消息的多播地址。</span><span class="sxs-lookup"><span data-stu-id="c1929-120">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="c1929-121">默认值是符合协议规范的多播地址。</span><span class="sxs-lookup"><span data-stu-id="c1929-121">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="c1929-122">NAME</span><span class="sxs-lookup"><span data-stu-id="c1929-122">name</span></span>|<span data-ttu-id="c1929-123">一个字符串，指定标准终结点的配置的名称。</span><span class="sxs-lookup"><span data-stu-id="c1929-123">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="c1929-124">此名称在服务终结点的 `endpointConfiguration` 特性中用于将标准终结点链接到其配置。</span><span class="sxs-lookup"><span data-stu-id="c1929-124">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1929-125">子元素</span><span class="sxs-lookup"><span data-stu-id="c1929-125">Child Elements</span></span>  
  
|<span data-ttu-id="c1929-126">元素</span><span class="sxs-lookup"><span data-stu-id="c1929-126">Element</span></span>|<span data-ttu-id="c1929-127">描述</span><span class="sxs-lookup"><span data-stu-id="c1929-127">Description</span></span>|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|<span data-ttu-id="c1929-128">一个设置集合，用于为 UDP 终结点配置 UDP 传输。</span><span class="sxs-lookup"><span data-stu-id="c1929-128">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c1929-129">父元素</span><span class="sxs-lookup"><span data-stu-id="c1929-129">Parent Elements</span></span>  
  
|<span data-ttu-id="c1929-130">元素</span><span class="sxs-lookup"><span data-stu-id="c1929-130">Element</span></span>|<span data-ttu-id="c1929-131">描述</span><span class="sxs-lookup"><span data-stu-id="c1929-131">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="c1929-132">具有一个或多个固定属性（地址、绑定和协定）的预定义终结点的标准终结点集合。</span><span class="sxs-lookup"><span data-stu-id="c1929-132">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c1929-133">示例</span><span class="sxs-lookup"><span data-stu-id="c1929-133">Example</span></span>  
 <span data-ttu-id="c1929-134">下面的示例演示一个客户端，该客户端分别通过采用默认多播地址和所指定多播地址的 UDP 多播传输侦听公告。</span><span class="sxs-lookup"><span data-stu-id="c1929-134">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="udpAnnouncementEndpointStandard"
              kind="udpAnnouncementEndpoint"
              bindingConfiguration="..." />
    <endpoint name="udpAnnouncementEndpoint2"
              kind="udpAnnouncementEndpoint"
              endpointConfiguration="AnnouncementConfiguration3702"
              bindingConfiguration="..." />
    ...
  </service>
</services>
<standardEndpoints>
  <udpAnnouncementEndpoint>
    <standardEndpoint name="AnnouncementConfiguration2"
                      version="WSDiscoveryApril2005"
                      multicastAddress="soap.udp://239.255.255.250:3703"/>
  </udpAnnouncementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="c1929-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c1929-135">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
