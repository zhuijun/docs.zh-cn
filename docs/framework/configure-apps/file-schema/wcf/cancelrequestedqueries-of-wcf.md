---
title: <cancelRequestedQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 63cfc835ac7ce88bde56fd9243a2cf6652cbce6e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850094"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="b6666-102">\<cancelRequestedQueries>WCF 的</span><span class="sxs-lookup"><span data-stu-id="b6666-102">\<cancelRequestedQueries> of WCF</span></span>
<span data-ttu-id="b6666-103">表示一个查询集合，这些查询用于跟踪父活动取消子活动的请求。</span><span class="sxs-lookup"><span data-stu-id="b6666-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b6666-104">跟踪参与者需要用此查询来订阅取消请求记录对象。</span><span class="sxs-lookup"><span data-stu-id="b6666-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="b6666-105">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b6666-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="b6666-106">语法</span><span class="sxs-lookup"><span data-stu-id="b6666-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String" />
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6666-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b6666-107">Attributes and elements</span></span>  

<span data-ttu-id="b6666-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b6666-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6666-109">特性</span><span class="sxs-lookup"><span data-stu-id="b6666-109">Attributes</span></span>

<span data-ttu-id="b6666-110">无。</span><span class="sxs-lookup"><span data-stu-id="b6666-110">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="b6666-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b6666-111">Child elements</span></span>
  
|<span data-ttu-id="b6666-112">元素</span><span class="sxs-lookup"><span data-stu-id="b6666-112">Element</span></span>|<span data-ttu-id="b6666-113">说明</span><span class="sxs-lookup"><span data-stu-id="b6666-113">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="b6666-114">一个查询，用于跟踪父活动取消子活动的请求</span><span class="sxs-lookup"><span data-stu-id="b6666-114">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b6666-115">父元素</span><span class="sxs-lookup"><span data-stu-id="b6666-115">Parent elements</span></span>  
  
|<span data-ttu-id="b6666-116">元素</span><span class="sxs-lookup"><span data-stu-id="b6666-116">Element</span></span>|<span data-ttu-id="b6666-117">说明</span><span class="sxs-lookup"><span data-stu-id="b6666-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="b6666-118">一个配置元素，包含 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> 属性所标识的特定工作流的所有查询。</span><span class="sxs-lookup"><span data-stu-id="b6666-118">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6666-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6666-119">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="b6666-120">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="b6666-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b6666-121">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="b6666-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
