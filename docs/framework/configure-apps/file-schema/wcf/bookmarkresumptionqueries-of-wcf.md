---
title: <bookmarkResumptionQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 94ff9f44f295b45c03e1bd8f52a85d6b7b0c6e3b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850138"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="e11ed-102">\<bookmarkResumptionQueries>WCF 的</span><span class="sxs-lookup"><span data-stu-id="e11ed-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="e11ed-103">表示一个查询集合，这些查询用于跟踪工作流实例中的书签恢复。</span><span class="sxs-lookup"><span data-stu-id="e11ed-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="e11ed-104">跟踪参与者需要用此查询来订阅书签恢复记录。</span><span class="sxs-lookup"><span data-stu-id="e11ed-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="e11ed-105">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="e11ed-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="e11ed-106">语法</span><span class="sxs-lookup"><span data-stu-id="e11ed-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e11ed-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e11ed-107">Attributes and elements</span></span>  
  
<span data-ttu-id="e11ed-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e11ed-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e11ed-109">特性</span><span class="sxs-lookup"><span data-stu-id="e11ed-109">Attributes</span></span>  
  
<span data-ttu-id="e11ed-110">无。</span><span class="sxs-lookup"><span data-stu-id="e11ed-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e11ed-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e11ed-111">Child elements</span></span>  
  
|<span data-ttu-id="e11ed-112">元素</span><span class="sxs-lookup"><span data-stu-id="e11ed-112">Element</span></span>|<span data-ttu-id="e11ed-113">说明</span><span class="sxs-lookup"><span data-stu-id="e11ed-113">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="e11ed-114">一个查询，用于跟踪工作流实例中的书签恢复。</span><span class="sxs-lookup"><span data-stu-id="e11ed-114">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="e11ed-115">跟踪参与者需要用此查询来订阅书签恢复记录。</span><span class="sxs-lookup"><span data-stu-id="e11ed-115">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e11ed-116">父元素</span><span class="sxs-lookup"><span data-stu-id="e11ed-116">Parent elements</span></span>  
  
|<span data-ttu-id="e11ed-117">元素</span><span class="sxs-lookup"><span data-stu-id="e11ed-117">Element</span></span>|<span data-ttu-id="e11ed-118">说明</span><span class="sxs-lookup"><span data-stu-id="e11ed-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="e11ed-119">一个配置元素，包含 `activityDefinitionId` 属性所标识的特定工作流的所有查询。</span><span class="sxs-lookup"><span data-stu-id="e11ed-119">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e11ed-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e11ed-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e11ed-121">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="e11ed-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e11ed-122">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="e11ed-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
