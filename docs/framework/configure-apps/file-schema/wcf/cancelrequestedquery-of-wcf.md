---
title: <cancelRequestedQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 0ac8b87afc44927ab6653dd6fcdc09cd61436a9b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850051"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="46824-102">\<cancelRequestedQuery>WCF 的</span><span class="sxs-lookup"><span data-stu-id="46824-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="46824-103">表示一个查询，该查询用于跟踪父活动取消子活动的请求。</span><span class="sxs-lookup"><span data-stu-id="46824-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="46824-104">跟踪参与者需要用此查询来订阅取消请求记录对象。</span><span class="sxs-lookup"><span data-stu-id="46824-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="46824-105">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="46824-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  

## <a name="syntax"></a><span data-ttu-id="46824-106">语法</span><span class="sxs-lookup"><span data-stu-id="46824-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46824-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="46824-107">Attributes and elements</span></span>

<span data-ttu-id="46824-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="46824-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="46824-109">特性</span><span class="sxs-lookup"><span data-stu-id="46824-109">Attributes</span></span>  
  
|<span data-ttu-id="46824-110">属性</span><span class="sxs-lookup"><span data-stu-id="46824-110">Attribute</span></span>|<span data-ttu-id="46824-111">说明</span><span class="sxs-lookup"><span data-stu-id="46824-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="46824-112">一个字符串，指定正在请求取消的活动的名称。</span><span class="sxs-lookup"><span data-stu-id="46824-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="46824-113">一个字符串，指定已请求将其取消的子活动的名称。</span><span class="sxs-lookup"><span data-stu-id="46824-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46824-114">子元素</span><span class="sxs-lookup"><span data-stu-id="46824-114">Child elements</span></span>

<span data-ttu-id="46824-115">无。</span><span class="sxs-lookup"><span data-stu-id="46824-115">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="46824-116">父元素</span><span class="sxs-lookup"><span data-stu-id="46824-116">Parent elements</span></span>
  
|<span data-ttu-id="46824-117">元素</span><span class="sxs-lookup"><span data-stu-id="46824-117">Element</span></span>|<span data-ttu-id="46824-118">描述</span><span class="sxs-lookup"><span data-stu-id="46824-118">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQueries>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="46824-119">表示一个查询集合，这些查询用于跟踪父活动取消子活动的请求。</span><span class="sxs-lookup"><span data-stu-id="46824-119">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="46824-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="46824-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="46824-121">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="46824-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="46824-122">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="46824-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
