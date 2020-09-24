---
title: <add> 的 <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 156d8b8d9d0eb05efbf306434ab4555a98bc317e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149044"
---
# <a name="add-of-entries"></a><span data-ttu-id="7244a-102">\<add> 的 \<entries></span><span class="sxs-lookup"><span data-stu-id="7244a-102">\<add> of \<entries></span></span>

<span data-ttu-id="7244a-103">表示将筛选器映射到以前定义的客户端终结点的路由项。</span><span class="sxs-lookup"><span data-stu-id="7244a-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="7244a-104">与此筛选器匹配的消息将发送到此目标。</span><span class="sxs-lookup"><span data-stu-id="7244a-104">Messages matching this filter will be sent to this destination.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<entries>**](entries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="7244a-105">语法</span><span class="sxs-lookup"><span data-stu-id="7244a-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7244a-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="7244a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7244a-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7244a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7244a-108">特性</span><span class="sxs-lookup"><span data-stu-id="7244a-108">Attributes</span></span>  
  
|<span data-ttu-id="7244a-109">属性</span><span class="sxs-lookup"><span data-stu-id="7244a-109">Attribute</span></span>|<span data-ttu-id="7244a-110">描述</span><span class="sxs-lookup"><span data-stu-id="7244a-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7244a-111">backupList</span><span class="sxs-lookup"><span data-stu-id="7244a-111">backupList</span></span>|<span data-ttu-id="7244a-112">一个字符串，指定对终结点备份列表的引用。</span><span class="sxs-lookup"><span data-stu-id="7244a-112">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="7244a-113">endpoint</span><span class="sxs-lookup"><span data-stu-id="7244a-113">endpoint</span></span>|<span data-ttu-id="7244a-114">一个字符串，指定对客户端终结点的引用，该终结点将接收与 `filterName` 特性所指定的筛选器匹配的消息。</span><span class="sxs-lookup"><span data-stu-id="7244a-114">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="7244a-115">filterName</span><span class="sxs-lookup"><span data-stu-id="7244a-115">filterName</span></span>|<span data-ttu-id="7244a-116">一个字符串，指定对筛选器元素的引用。</span><span class="sxs-lookup"><span data-stu-id="7244a-116">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="7244a-117">priority</span><span class="sxs-lookup"><span data-stu-id="7244a-117">priority</span></span>|<span data-ttu-id="7244a-118">一个整数，指定此项的优先级。</span><span class="sxs-lookup"><span data-stu-id="7244a-118">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="7244a-119">将根据优先级计算路由表中的项，0 表示优先级最低。</span><span class="sxs-lookup"><span data-stu-id="7244a-119">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="7244a-120">将同时计算某个特定优先级的所有项，如果未找到当前优先级的匹配项，将计算下一个优先级。</span><span class="sxs-lookup"><span data-stu-id="7244a-120">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="7244a-121">此值是可选的。</span><span class="sxs-lookup"><span data-stu-id="7244a-121">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7244a-122">子元素</span><span class="sxs-lookup"><span data-stu-id="7244a-122">Child Elements</span></span>  

 <span data-ttu-id="7244a-123">无。</span><span class="sxs-lookup"><span data-stu-id="7244a-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7244a-124">父元素</span><span class="sxs-lookup"><span data-stu-id="7244a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7244a-125">元素</span><span class="sxs-lookup"><span data-stu-id="7244a-125">Element</span></span>|<span data-ttu-id="7244a-126">描述</span><span class="sxs-lookup"><span data-stu-id="7244a-126">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="7244a-127">一个包含路由映射项的配置节。</span><span class="sxs-lookup"><span data-stu-id="7244a-127">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7244a-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="7244a-128">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
