---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: fb36feedc5fb2cbdf3827cbe44242c7ac6ab8a9b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185686"
---
# \<filterTable>

<span data-ttu-id="bbb68-101">表示一个路由表，此表包含计算消息所依据的筛选器的列表，以及当筛选器的计算结果为 true 时消息要路由到的客户端终结点。</span><span class="sxs-lookup"><span data-stu-id="bbb68-101">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**  
  
## <a name="syntax"></a><span data-ttu-id="bbb68-102">语法</span><span class="sxs-lookup"><span data-stu-id="bbb68-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbb68-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="bbb68-103">Attributes and Elements</span></span>  

 <span data-ttu-id="bbb68-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bbb68-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbb68-105">特性</span><span class="sxs-lookup"><span data-stu-id="bbb68-105">Attributes</span></span>  
  
|<span data-ttu-id="bbb68-106">元素</span><span class="sxs-lookup"><span data-stu-id="bbb68-106">Element</span></span>|<span data-ttu-id="bbb68-107">说明</span><span class="sxs-lookup"><span data-stu-id="bbb68-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bbb68-108">name</span><span class="sxs-lookup"><span data-stu-id="bbb68-108">name</span></span>|<span data-ttu-id="bbb68-109">一个字符串，包含此配置元素的唯一名称。</span><span class="sxs-lookup"><span data-stu-id="bbb68-109">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bbb68-110">子元素</span><span class="sxs-lookup"><span data-stu-id="bbb68-110">Child Elements</span></span>  
  
|<span data-ttu-id="bbb68-111">元素</span><span class="sxs-lookup"><span data-stu-id="bbb68-111">Element</span></span>|<span data-ttu-id="bbb68-112">描述</span><span class="sxs-lookup"><span data-stu-id="bbb68-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="bbb68-113">路由筛选器与在筛选器匹配时消息要发送到的目标终结点之间的映射。</span><span class="sxs-lookup"><span data-stu-id="bbb68-113">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bbb68-114">父元素</span><span class="sxs-lookup"><span data-stu-id="bbb68-114">Parent Elements</span></span>  
  
|<span data-ttu-id="bbb68-115">元素</span><span class="sxs-lookup"><span data-stu-id="bbb68-115">Element</span></span>|<span data-ttu-id="bbb68-116">描述</span><span class="sxs-lookup"><span data-stu-id="bbb68-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="bbb68-117">一个包含路由表的配置节。</span><span class="sxs-lookup"><span data-stu-id="bbb68-117">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bbb68-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="bbb68-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
