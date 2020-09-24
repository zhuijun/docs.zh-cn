---
title: <activityScheduledQueries> WCF 的
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 86f196437b2230d6541570aa8994d99e7b340f66
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151189"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="80d3b-102">\<activityScheduledQueries> WCF 的</span><span class="sxs-lookup"><span data-stu-id="80d3b-102">\<activityScheduledQueries> of WCF</span></span>

<span data-ttu-id="80d3b-103">表示一个查询集合，这些查询用于跟踪安排给父活动来执行的活动。</span><span class="sxs-lookup"><span data-stu-id="80d3b-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="80d3b-104">跟踪参与者需要用此查询来订阅活动安排记录。</span><span class="sxs-lookup"><span data-stu-id="80d3b-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="80d3b-105">有关跟踪配置文件查询的详细信息，请参阅 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="80d3b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="80d3b-106">语法</span><span class="sxs-lookup"><span data-stu-id="80d3b-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80d3b-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="80d3b-107">Attributes and elements</span></span>  

<span data-ttu-id="80d3b-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="80d3b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80d3b-109">特性</span><span class="sxs-lookup"><span data-stu-id="80d3b-109">Attributes</span></span>  

<span data-ttu-id="80d3b-110">无。</span><span class="sxs-lookup"><span data-stu-id="80d3b-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="80d3b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="80d3b-111">Child elements</span></span>  
  
|<span data-ttu-id="80d3b-112">元素</span><span class="sxs-lookup"><span data-stu-id="80d3b-112">Element</span></span>|<span data-ttu-id="80d3b-113">描述</span><span class="sxs-lookup"><span data-stu-id="80d3b-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="80d3b-114">一个查询，用于跟踪安排给父活动来执行的活动。</span><span class="sxs-lookup"><span data-stu-id="80d3b-114">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="80d3b-115">父元素</span><span class="sxs-lookup"><span data-stu-id="80d3b-115">Parent elements</span></span>  
  
|<span data-ttu-id="80d3b-116">元素</span><span class="sxs-lookup"><span data-stu-id="80d3b-116">Element</span></span>|<span data-ttu-id="80d3b-117">描述</span><span class="sxs-lookup"><span data-stu-id="80d3b-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="80d3b-118">一个配置元素，包含 `activityDefinitionId` 属性所标识的特定工作流的所有查询。</span><span class="sxs-lookup"><span data-stu-id="80d3b-118">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80d3b-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="80d3b-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="80d3b-120">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="80d3b-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="80d3b-121">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="80d3b-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
