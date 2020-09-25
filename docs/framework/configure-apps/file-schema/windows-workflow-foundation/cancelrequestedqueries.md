---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 4db30f3fed12b585b73339120fa5bc6602150e7d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189534"
---
# \<cancelRequestedQueries>

<span data-ttu-id="5ff43-101">表示一个查询集合，这些查询用于跟踪父活动取消子活动的请求。</span><span class="sxs-lookup"><span data-stu-id="5ff43-101">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="5ff43-102">跟踪参与者需要用此查询来订阅取消请求记录对象。</span><span class="sxs-lookup"><span data-stu-id="5ff43-102">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="5ff43-103">有关跟踪配置文件查询的详细信息，请参阅 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="5ff43-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="5ff43-104">语法</span><span class="sxs-lookup"><span data-stu-id="5ff43-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String"
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ff43-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="5ff43-105">Attributes and Elements</span></span>  

 <span data-ttu-id="5ff43-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5ff43-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ff43-107">特性</span><span class="sxs-lookup"><span data-stu-id="5ff43-107">Attributes</span></span>  

 <span data-ttu-id="5ff43-108">无。</span><span class="sxs-lookup"><span data-stu-id="5ff43-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5ff43-109">子元素</span><span class="sxs-lookup"><span data-stu-id="5ff43-109">Child Elements</span></span>  
  
|<span data-ttu-id="5ff43-110">元素</span><span class="sxs-lookup"><span data-stu-id="5ff43-110">Element</span></span>|<span data-ttu-id="5ff43-111">描述</span><span class="sxs-lookup"><span data-stu-id="5ff43-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery.md)|<span data-ttu-id="5ff43-112">一个查询，用于跟踪父活动取消子活动的请求</span><span class="sxs-lookup"><span data-stu-id="5ff43-112">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ff43-113">父元素</span><span class="sxs-lookup"><span data-stu-id="5ff43-113">Parent Elements</span></span>  
  
|<span data-ttu-id="5ff43-114">元素</span><span class="sxs-lookup"><span data-stu-id="5ff43-114">Element</span></span>|<span data-ttu-id="5ff43-115">描述</span><span class="sxs-lookup"><span data-stu-id="5ff43-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="5ff43-116">一个配置元素，该元素包含由 **activityDefinitionId** 属性标识的特定工作流的所有查询。</span><span class="sxs-lookup"><span data-stu-id="5ff43-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ff43-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="5ff43-117">See also</span></span>

- [<span data-ttu-id="5ff43-118">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="5ff43-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5ff43-119">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="5ff43-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
