---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: c68479737cefe542a10a404a8b31a4820a430ffb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855197"
---
# \<filterTables>
<span data-ttu-id="14446-101">表示一个用于定义路由表的配置节，这些路由表包含路由筛选器与在筛选器匹配时消息要发送到的目标终结点之间的映射。</span><span class="sxs-lookup"><span data-stu-id="14446-101">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTables>**  
  
## <a name="syntax"></a><span data-ttu-id="14446-102">语法</span><span class="sxs-lookup"><span data-stu-id="14446-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14446-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="14446-103">Attributes and Elements</span></span>  
 <span data-ttu-id="14446-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="14446-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14446-105">特性</span><span class="sxs-lookup"><span data-stu-id="14446-105">Attributes</span></span>  
 <span data-ttu-id="14446-106">无。</span><span class="sxs-lookup"><span data-stu-id="14446-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="14446-107">子元素</span><span class="sxs-lookup"><span data-stu-id="14446-107">Child Elements</span></span>  
  
|<span data-ttu-id="14446-108">元素</span><span class="sxs-lookup"><span data-stu-id="14446-108">Element</span></span>|<span data-ttu-id="14446-109">说明</span><span class="sxs-lookup"><span data-stu-id="14446-109">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="14446-110">一个路由表，包含路由筛选器与在筛选器匹配时消息要发送到的目标终结点之间的映射。</span><span class="sxs-lookup"><span data-stu-id="14446-110">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="14446-111">父元素</span><span class="sxs-lookup"><span data-stu-id="14446-111">Parent Elements</span></span>  
  
|<span data-ttu-id="14446-112">元素</span><span class="sxs-lookup"><span data-stu-id="14446-112">Element</span></span>|<span data-ttu-id="14446-113">说明</span><span class="sxs-lookup"><span data-stu-id="14446-113">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="14446-114">一个包含路由筛选器和路由表的配置节。</span><span class="sxs-lookup"><span data-stu-id="14446-114">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14446-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="14446-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
