---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 6901244009956a499458858bf73f8fd83ec52e13
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152256"
---
# \<customTrackingQueries>
<span data-ttu-id="39cb2-101">表示一个查询集合，这些查询用于跟踪你在代码活动中定义的事件。</span><span class="sxs-lookup"><span data-stu-id="39cb2-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="39cb2-102">跟踪参与者需要用此查询来订阅自定义跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="39cb2-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="39cb2-103">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="39cb2-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="39cb2-104">语法</span><span class="sxs-lookup"><span data-stu-id="39cb2-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String"
                             name="String" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39cb2-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="39cb2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="39cb2-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="39cb2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39cb2-107">特性</span><span class="sxs-lookup"><span data-stu-id="39cb2-107">Attributes</span></span>  
 <span data-ttu-id="39cb2-108">无。</span><span class="sxs-lookup"><span data-stu-id="39cb2-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="39cb2-109">子元素</span><span class="sxs-lookup"><span data-stu-id="39cb2-109">Child Elements</span></span>  
  
|<span data-ttu-id="39cb2-110">元素</span><span class="sxs-lookup"><span data-stu-id="39cb2-110">Element</span></span>|<span data-ttu-id="39cb2-111">说明</span><span class="sxs-lookup"><span data-stu-id="39cb2-111">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="39cb2-112">一个查询，用于跟踪你在代码活动中定义的事件。</span><span class="sxs-lookup"><span data-stu-id="39cb2-112">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39cb2-113">父元素</span><span class="sxs-lookup"><span data-stu-id="39cb2-113">Parent Elements</span></span>  
  
|<span data-ttu-id="39cb2-114">元素</span><span class="sxs-lookup"><span data-stu-id="39cb2-114">Element</span></span>|<span data-ttu-id="39cb2-115">说明</span><span class="sxs-lookup"><span data-stu-id="39cb2-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="39cb2-116">一个配置元素，该元素包含由**activityDefinitionId**属性标识的特定工作流的所有查询。</span><span class="sxs-lookup"><span data-stu-id="39cb2-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39cb2-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="39cb2-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="39cb2-118">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="39cb2-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="39cb2-119">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="39cb2-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
