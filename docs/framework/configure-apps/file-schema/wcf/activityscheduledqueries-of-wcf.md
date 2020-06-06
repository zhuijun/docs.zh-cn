---
title: <activityScheduledQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: c2281a9027aabfc5255ef7b09176f60d1725b522
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850494"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="17ee9-102">\<activityScheduledQueries>WCF 的</span><span class="sxs-lookup"><span data-stu-id="17ee9-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="17ee9-103">表示一个查询集合，这些查询用于跟踪安排给父活动来执行的活动。</span><span class="sxs-lookup"><span data-stu-id="17ee9-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="17ee9-104">跟踪参与者需要用此查询来订阅活动安排记录。</span><span class="sxs-lookup"><span data-stu-id="17ee9-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="17ee9-105">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="17ee9-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="17ee9-106">语法</span><span class="sxs-lookup"><span data-stu-id="17ee9-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17ee9-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="17ee9-107">Attributes and elements</span></span>  

<span data-ttu-id="17ee9-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="17ee9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17ee9-109">特性</span><span class="sxs-lookup"><span data-stu-id="17ee9-109">Attributes</span></span>  

<span data-ttu-id="17ee9-110">无。</span><span class="sxs-lookup"><span data-stu-id="17ee9-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="17ee9-111">子元素</span><span class="sxs-lookup"><span data-stu-id="17ee9-111">Child elements</span></span>  
  
|<span data-ttu-id="17ee9-112">元素</span><span class="sxs-lookup"><span data-stu-id="17ee9-112">Element</span></span>|<span data-ttu-id="17ee9-113">说明</span><span class="sxs-lookup"><span data-stu-id="17ee9-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="17ee9-114">一个查询，用于跟踪安排给父活动来执行的活动。</span><span class="sxs-lookup"><span data-stu-id="17ee9-114">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="17ee9-115">父元素</span><span class="sxs-lookup"><span data-stu-id="17ee9-115">Parent elements</span></span>  
  
|<span data-ttu-id="17ee9-116">元素</span><span class="sxs-lookup"><span data-stu-id="17ee9-116">Element</span></span>|<span data-ttu-id="17ee9-117">说明</span><span class="sxs-lookup"><span data-stu-id="17ee9-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="17ee9-118">一个配置元素，包含 `activityDefinitionId` 属性所标识的特定工作流的所有查询。</span><span class="sxs-lookup"><span data-stu-id="17ee9-118">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17ee9-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17ee9-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="17ee9-120">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="17ee9-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="17ee9-121">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="17ee9-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
