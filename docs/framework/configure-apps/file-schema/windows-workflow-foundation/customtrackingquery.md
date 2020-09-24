---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 59a76ea772dc8d06c390e3bca9d531df5f11e5f0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148719"
---
# \<customTrackingQuery>

<span data-ttu-id="fd788-101">表示一个查询集合，这些查询用于跟踪你在代码活动中定义的事件。</span><span class="sxs-lookup"><span data-stu-id="fd788-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="fd788-102">跟踪参与者需要用此查询来订阅自定义跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="fd788-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="fd788-103">有关跟踪配置文件查询的详细信息，请参阅 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="fd788-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="fd788-104">语法</span><span class="sxs-lookup"><span data-stu-id="fd788-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd788-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="fd788-105">Attributes and Elements</span></span>  

 <span data-ttu-id="fd788-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fd788-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd788-107">特性</span><span class="sxs-lookup"><span data-stu-id="fd788-107">Attributes</span></span>  
  
|<span data-ttu-id="fd788-108">属性</span><span class="sxs-lookup"><span data-stu-id="fd788-108">Attribute</span></span>|<span data-ttu-id="fd788-109">描述</span><span class="sxs-lookup"><span data-stu-id="fd788-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd788-110">activityName</span><span class="sxs-lookup"><span data-stu-id="fd788-110">activityName</span></span>|<span data-ttu-id="fd788-111">一个字符串，指定生成跟踪记录的活动的名称。</span><span class="sxs-lookup"><span data-stu-id="fd788-111">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="fd788-112">name</span><span class="sxs-lookup"><span data-stu-id="fd788-112">name</span></span>|<span data-ttu-id="fd788-113">一个字符串，指定发出的自定义跟踪记录的名称。</span><span class="sxs-lookup"><span data-stu-id="fd788-113">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd788-114">子元素</span><span class="sxs-lookup"><span data-stu-id="fd788-114">Child Elements</span></span>  

 <span data-ttu-id="fd788-115">无。</span><span class="sxs-lookup"><span data-stu-id="fd788-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd788-116">父元素</span><span class="sxs-lookup"><span data-stu-id="fd788-116">Parent Elements</span></span>  
  
|<span data-ttu-id="fd788-117">元素</span><span class="sxs-lookup"><span data-stu-id="fd788-117">Element</span></span>|<span data-ttu-id="fd788-118">描述</span><span class="sxs-lookup"><span data-stu-id="fd788-118">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="fd788-119">一个查询，用于跟踪你在代码活动中定义的事件。</span><span class="sxs-lookup"><span data-stu-id="fd788-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd788-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="fd788-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="fd788-121">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="fd788-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fd788-122">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="fd788-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
