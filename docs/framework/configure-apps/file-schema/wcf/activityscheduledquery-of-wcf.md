---
title: <activityScheduledQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: b173964cf5d691f4b9300bca69ca4a1fe1ea7e11
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850474"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="fafdd-102">\<activityScheduledQuery>WCF 的</span><span class="sxs-lookup"><span data-stu-id="fafdd-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="fafdd-103">表示一个查询集合，这些查询用于跟踪安排给父活动来执行的活动。</span><span class="sxs-lookup"><span data-stu-id="fafdd-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="fafdd-104">跟踪参与者需要用此查询来订阅活动安排记录。</span><span class="sxs-lookup"><span data-stu-id="fafdd-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="fafdd-105">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="fafdd-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="fafdd-106">语法</span><span class="sxs-lookup"><span data-stu-id="fafdd-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fafdd-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="fafdd-107">Attributes and elements</span></span>  

<span data-ttu-id="fafdd-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fafdd-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fafdd-109">特性</span><span class="sxs-lookup"><span data-stu-id="fafdd-109">Attributes</span></span>  
  
|<span data-ttu-id="fafdd-110">属性</span><span class="sxs-lookup"><span data-stu-id="fafdd-110">Attribute</span></span>|<span data-ttu-id="fafdd-111">说明</span><span class="sxs-lookup"><span data-stu-id="fafdd-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="fafdd-112">一个字符串，指定正在请求取消的活动的名称。</span><span class="sxs-lookup"><span data-stu-id="fafdd-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="fafdd-113">一个字符串，指定已请求将其取消的子活动的名称。</span><span class="sxs-lookup"><span data-stu-id="fafdd-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fafdd-114">子元素</span><span class="sxs-lookup"><span data-stu-id="fafdd-114">Child elements</span></span>

<span data-ttu-id="fafdd-115">无。</span><span class="sxs-lookup"><span data-stu-id="fafdd-115">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="fafdd-116">父元素</span><span class="sxs-lookup"><span data-stu-id="fafdd-116">Parent elements</span></span>  
  
|<span data-ttu-id="fafdd-117">元素</span><span class="sxs-lookup"><span data-stu-id="fafdd-117">Element</span></span>|<span data-ttu-id="fafdd-118">描述</span><span class="sxs-lookup"><span data-stu-id="fafdd-118">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQueries>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="fafdd-119">查询的集合，这些查询用于跟踪计划的父活动执行的活动。</span><span class="sxs-lookup"><span data-stu-id="fafdd-119">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fafdd-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fafdd-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="fafdd-121">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="fafdd-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fafdd-122">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="fafdd-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
