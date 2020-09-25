---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 047d13bc8477214fa1e3c9ffdbed6785b29da637
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189573"
---
# \<bookmarkResumptionQueries>

<span data-ttu-id="d4b9b-101">表示一个查询集合，这些查询用于跟踪工作流实例中的书签恢复。</span><span class="sxs-lookup"><span data-stu-id="d4b9b-101">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="d4b9b-102">跟踪参与者需要用此查询来订阅书签恢复记录。</span><span class="sxs-lookup"><span data-stu-id="d4b9b-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="d4b9b-103">有关跟踪配置文件查询的详细信息，请参阅 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d4b9b-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="d4b9b-104">语法</span><span class="sxs-lookup"><span data-stu-id="d4b9b-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4b9b-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="d4b9b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d4b9b-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d4b9b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4b9b-107">特性</span><span class="sxs-lookup"><span data-stu-id="d4b9b-107">Attributes</span></span>  

 <span data-ttu-id="d4b9b-108">无。</span><span class="sxs-lookup"><span data-stu-id="d4b9b-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d4b9b-109">子元素</span><span class="sxs-lookup"><span data-stu-id="d4b9b-109">Child Elements</span></span>  
  
|<span data-ttu-id="d4b9b-110">元素</span><span class="sxs-lookup"><span data-stu-id="d4b9b-110">Element</span></span>|<span data-ttu-id="d4b9b-111">描述</span><span class="sxs-lookup"><span data-stu-id="d4b9b-111">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery.md)|<span data-ttu-id="d4b9b-112">一个查询，用于跟踪工作流实例中的书签恢复。</span><span class="sxs-lookup"><span data-stu-id="d4b9b-112">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="d4b9b-113">跟踪参与者需要用此查询来订阅书签恢复记录。</span><span class="sxs-lookup"><span data-stu-id="d4b9b-113">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d4b9b-114">父元素</span><span class="sxs-lookup"><span data-stu-id="d4b9b-114">Parent Elements</span></span>  
  
|<span data-ttu-id="d4b9b-115">元素</span><span class="sxs-lookup"><span data-stu-id="d4b9b-115">Element</span></span>|<span data-ttu-id="d4b9b-116">描述</span><span class="sxs-lookup"><span data-stu-id="d4b9b-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="d4b9b-117">一个配置元素，该元素包含由 **activityDefinitionId** 属性标识的特定工作流的所有查询。</span><span class="sxs-lookup"><span data-stu-id="d4b9b-117">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4b9b-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="d4b9b-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d4b9b-119">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="d4b9b-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d4b9b-120">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="d4b9b-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
