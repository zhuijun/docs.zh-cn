---
title: <bookmarkResumptionQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 8cb254599a9742305ec958fd77174f4c4b8a57c2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "71834009"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="8bfe8-102">\<bookmarkResumptionQuery>WCF 的</span><span class="sxs-lookup"><span data-stu-id="8bfe8-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="8bfe8-103">表示一个查询，该查询用于跟踪工作流实例中的书签恢复。</span><span class="sxs-lookup"><span data-stu-id="8bfe8-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="8bfe8-104">跟踪参与者需要用此查询来订阅书签恢复记录。</span><span class="sxs-lookup"><span data-stu-id="8bfe8-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="8bfe8-105">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="8bfe8-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="8bfe8-106">语法</span><span class="sxs-lookup"><span data-stu-id="8bfe8-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8bfe8-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="8bfe8-107">Attributes and elements</span></span>

<span data-ttu-id="8bfe8-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8bfe8-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8bfe8-109">特性</span><span class="sxs-lookup"><span data-stu-id="8bfe8-109">Attributes</span></span>  
  
|<span data-ttu-id="8bfe8-110">属性</span><span class="sxs-lookup"><span data-stu-id="8bfe8-110">Attribute</span></span>|<span data-ttu-id="8bfe8-111">说明</span><span class="sxs-lookup"><span data-stu-id="8bfe8-111">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="8bfe8-112">一个字符串，指定要订阅的书签记录的名称。</span><span class="sxs-lookup"><span data-stu-id="8bfe8-112">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8bfe8-113">子元素</span><span class="sxs-lookup"><span data-stu-id="8bfe8-113">Child elements</span></span>

<span data-ttu-id="8bfe8-114">无。</span><span class="sxs-lookup"><span data-stu-id="8bfe8-114">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="8bfe8-115">父元素</span><span class="sxs-lookup"><span data-stu-id="8bfe8-115">Parent elements</span></span>  
  
|<span data-ttu-id="8bfe8-116">元素</span><span class="sxs-lookup"><span data-stu-id="8bfe8-116">Element</span></span>|<span data-ttu-id="8bfe8-117">描述</span><span class="sxs-lookup"><span data-stu-id="8bfe8-117">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="8bfe8-118">表示一个查询集合，这些查询用于跟踪工作流实例中的书签恢复。</span><span class="sxs-lookup"><span data-stu-id="8bfe8-118">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8bfe8-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8bfe8-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8bfe8-120">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="8bfe8-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8bfe8-121">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="8bfe8-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
