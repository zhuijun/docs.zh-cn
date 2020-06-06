---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: a02d71811709b2c285ab7081b89ee3082ec5b43d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152204"
---
# \<customTrackingQuery>
<span data-ttu-id="dbec5-101">表示一个查询集合，这些查询用于跟踪你在代码活动中定义的事件。</span><span class="sxs-lookup"><span data-stu-id="dbec5-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="dbec5-102">跟踪参与者需要用此查询来订阅自定义跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="dbec5-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="dbec5-103">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="dbec5-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="dbec5-104">语法</span><span class="sxs-lookup"><span data-stu-id="dbec5-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbec5-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="dbec5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="dbec5-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dbec5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbec5-107">特性</span><span class="sxs-lookup"><span data-stu-id="dbec5-107">Attributes</span></span>  
  
|<span data-ttu-id="dbec5-108">属性</span><span class="sxs-lookup"><span data-stu-id="dbec5-108">Attribute</span></span>|<span data-ttu-id="dbec5-109">说明</span><span class="sxs-lookup"><span data-stu-id="dbec5-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dbec5-110">activityName</span><span class="sxs-lookup"><span data-stu-id="dbec5-110">activityName</span></span>|<span data-ttu-id="dbec5-111">一个字符串，指定生成跟踪记录的活动的名称。</span><span class="sxs-lookup"><span data-stu-id="dbec5-111">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="dbec5-112">NAME</span><span class="sxs-lookup"><span data-stu-id="dbec5-112">name</span></span>|<span data-ttu-id="dbec5-113">一个字符串，指定发出的自定义跟踪记录的名称。</span><span class="sxs-lookup"><span data-stu-id="dbec5-113">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dbec5-114">子元素</span><span class="sxs-lookup"><span data-stu-id="dbec5-114">Child Elements</span></span>  
 <span data-ttu-id="dbec5-115">无。</span><span class="sxs-lookup"><span data-stu-id="dbec5-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dbec5-116">父元素</span><span class="sxs-lookup"><span data-stu-id="dbec5-116">Parent Elements</span></span>  
  
|<span data-ttu-id="dbec5-117">元素</span><span class="sxs-lookup"><span data-stu-id="dbec5-117">Element</span></span>|<span data-ttu-id="dbec5-118">描述</span><span class="sxs-lookup"><span data-stu-id="dbec5-118">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="dbec5-119">一个查询，用于跟踪你在代码活动中定义的事件。</span><span class="sxs-lookup"><span data-stu-id="dbec5-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dbec5-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dbec5-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="dbec5-121">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="dbec5-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dbec5-122">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="dbec5-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
