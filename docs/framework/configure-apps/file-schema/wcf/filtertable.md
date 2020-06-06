---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 918a365004efea82f4ef4c8868f6821d4bb6da18
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855189"
---
# \<filterTable>
<span data-ttu-id="d6e78-101">表示一个路由表，此表包含计算消息所依据的筛选器的列表，以及当筛选器的计算结果为 true 时消息要路由到的客户端终结点。</span><span class="sxs-lookup"><span data-stu-id="d6e78-101">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**  
  
## <a name="syntax"></a><span data-ttu-id="d6e78-102">语法</span><span class="sxs-lookup"><span data-stu-id="d6e78-102">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
     name="String">
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6e78-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="d6e78-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d6e78-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d6e78-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6e78-105">特性</span><span class="sxs-lookup"><span data-stu-id="d6e78-105">Attributes</span></span>  
  
|<span data-ttu-id="d6e78-106">元素</span><span class="sxs-lookup"><span data-stu-id="d6e78-106">Element</span></span>|<span data-ttu-id="d6e78-107">说明</span><span class="sxs-lookup"><span data-stu-id="d6e78-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6e78-108">name</span><span class="sxs-lookup"><span data-stu-id="d6e78-108">name</span></span>|<span data-ttu-id="d6e78-109">一个字符串，包含此配置元素的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="d6e78-109">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6e78-110">子元素</span><span class="sxs-lookup"><span data-stu-id="d6e78-110">Child Elements</span></span>  
  
|<span data-ttu-id="d6e78-111">元素</span><span class="sxs-lookup"><span data-stu-id="d6e78-111">Element</span></span>|<span data-ttu-id="d6e78-112">说明</span><span class="sxs-lookup"><span data-stu-id="d6e78-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="d6e78-113">路由筛选器与在筛选器匹配时消息要发送到的目标终结点之间的映射。</span><span class="sxs-lookup"><span data-stu-id="d6e78-113">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d6e78-114">父元素</span><span class="sxs-lookup"><span data-stu-id="d6e78-114">Parent Elements</span></span>  
  
|<span data-ttu-id="d6e78-115">元素</span><span class="sxs-lookup"><span data-stu-id="d6e78-115">Element</span></span>|<span data-ttu-id="d6e78-116">说明</span><span class="sxs-lookup"><span data-stu-id="d6e78-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="d6e78-117">一个包含路由表的配置节。</span><span class="sxs-lookup"><span data-stu-id="d6e78-117">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6e78-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d6e78-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
