---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: b38496b77d80fcb66b1b48485a9eef6abfd72299
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198816"
---
# \<serviceDiscovery>

<span data-ttu-id="7f466-101">指定服务终结点的可发现性。</span><span class="sxs-lookup"><span data-stu-id="7f466-101">Specifies the discoverability of service endpoints.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="7f466-102">语法</span><span class="sxs-lookup"><span data-stu-id="7f466-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </announcementEndpoints>
        <discoveryEndpoints>
          <endpoint name="String"
                    kind="Type" />
        </discoveryEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f466-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="7f466-103">Attributes and Elements</span></span>  

 <span data-ttu-id="7f466-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7f466-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f466-105">特性</span><span class="sxs-lookup"><span data-stu-id="7f466-105">Attributes</span></span>  

 <span data-ttu-id="7f466-106">无。</span><span class="sxs-lookup"><span data-stu-id="7f466-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7f466-107">子元素</span><span class="sxs-lookup"><span data-stu-id="7f466-107">Child Elements</span></span>  
  
|<span data-ttu-id="7f466-108">元素</span><span class="sxs-lookup"><span data-stu-id="7f466-108">Element</span></span>|<span data-ttu-id="7f466-109">描述</span><span class="sxs-lookup"><span data-stu-id="7f466-109">Description</span></span>|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|<span data-ttu-id="7f466-110">一个公告终结点集合。</span><span class="sxs-lookup"><span data-stu-id="7f466-110">A collection of announcement endpoints.</span></span> <span data-ttu-id="7f466-111">使用此节可指定用于发送公告消息的终结点。</span><span class="sxs-lookup"><span data-stu-id="7f466-111">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|<span data-ttu-id="7f466-112">一个发现终结点集合。</span><span class="sxs-lookup"><span data-stu-id="7f466-112">A collection of discovery endpoints.</span></span> <span data-ttu-id="7f466-113">使用此节可指定要在其上侦听发现消息的终结点。</span><span class="sxs-lookup"><span data-stu-id="7f466-113">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f466-114">父元素</span><span class="sxs-lookup"><span data-stu-id="7f466-114">Parent Elements</span></span>  
  
|<span data-ttu-id="7f466-115">元素</span><span class="sxs-lookup"><span data-stu-id="7f466-115">Element</span></span>|<span data-ttu-id="7f466-116">描述</span><span class="sxs-lookup"><span data-stu-id="7f466-116">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="7f466-117">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="7f466-117">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f466-118">备注</span><span class="sxs-lookup"><span data-stu-id="7f466-118">Remarks</span></span>  

 <span data-ttu-id="7f466-119">将此配置元素添加到服务的行为配置后，此元素可使系统检测到此服务的所有终结点。</span><span class="sxs-lookup"><span data-stu-id="7f466-119">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="7f466-120">通过使用 [\<discoveryEndpoint>](discoveryendpoint.md) 或子元素，可以进一步配置此类终结点的发现功能 [\<announcementEndpoint>](announcementendpoint.md) 。</span><span class="sxs-lookup"><span data-stu-id="7f466-120">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="7f466-121">使用 [\<announcementEndpoint>](announcementendpoint.md) 部分通过指定要用于将服务公告发送 (online/Hello 和 offline/再见) 来配置公告。</span><span class="sxs-lookup"><span data-stu-id="7f466-121">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="7f466-122">使用 [\<discoveryEndpoint>](discoveryendpoint.md) 部分手动指定要在其上侦听发现消息的终结点。</span><span class="sxs-lookup"><span data-stu-id="7f466-122">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f466-123">示例</span><span class="sxs-lookup"><span data-stu-id="7f466-123">Example</span></span>  

 <span data-ttu-id="7f466-124">下面的配置示例指定 CalculatorService 可供检测，并选择指定要使用的公告终结点。</span><span class="sxs-lookup"><span data-stu-id="7f466-124">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="udpEndpoint"
                    kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="7f466-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="7f466-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
