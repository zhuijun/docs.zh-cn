---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: d3dae510ac62735138a24b8fb97a8acfffde1a98
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189962"
---
# \<entries>

<span data-ttu-id="e2518-101">一个路由项，包含路由筛选器与在筛选器匹配时消息要发送到的目标终结点之间的映射。</span><span class="sxs-lookup"><span data-stu-id="e2518-101">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<entries>**  
  
## <a name="syntax"></a><span data-ttu-id="e2518-102">语法</span><span class="sxs-lookup"><span data-stu-id="e2518-102">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2518-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e2518-103">Attributes and Elements</span></span>  

 <span data-ttu-id="e2518-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e2518-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2518-105">特性</span><span class="sxs-lookup"><span data-stu-id="e2518-105">Attributes</span></span>  

 <span data-ttu-id="e2518-106">无。</span><span class="sxs-lookup"><span data-stu-id="e2518-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e2518-107">子元素</span><span class="sxs-lookup"><span data-stu-id="e2518-107">Child Elements</span></span>  
  
|<span data-ttu-id="e2518-108">元素</span><span class="sxs-lookup"><span data-stu-id="e2518-108">Element</span></span>|<span data-ttu-id="e2518-109">描述</span><span class="sxs-lookup"><span data-stu-id="e2518-109">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="e2518-110">将筛选器映射到以前定义的客户端终结点。</span><span class="sxs-lookup"><span data-stu-id="e2518-110">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="e2518-111">与此筛选器匹配的消息将发送到此目标。</span><span class="sxs-lookup"><span data-stu-id="e2518-111">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e2518-112">父元素</span><span class="sxs-lookup"><span data-stu-id="e2518-112">Parent Elements</span></span>  
  
|<span data-ttu-id="e2518-113">元素</span><span class="sxs-lookup"><span data-stu-id="e2518-113">Element</span></span>|<span data-ttu-id="e2518-114">描述</span><span class="sxs-lookup"><span data-stu-id="e2518-114">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="e2518-115">一个包含路由表的配置节。</span><span class="sxs-lookup"><span data-stu-id="e2518-115">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e2518-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="e2518-116">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
