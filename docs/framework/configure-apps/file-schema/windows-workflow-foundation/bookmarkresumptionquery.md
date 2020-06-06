---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: b2a81a42a17474bdb0124bec6d3c3eeefa514411
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398849"
---
# \<bookmarkResumptionQuery>
<span data-ttu-id="13698-101">表示一个查询，该查询用于跟踪工作流实例中的书签恢复。</span><span class="sxs-lookup"><span data-stu-id="13698-101">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="13698-102">跟踪参与者需要用此查询来订阅书签恢复记录。</span><span class="sxs-lookup"><span data-stu-id="13698-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="13698-103">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="13698-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="13698-104">语法</span><span class="sxs-lookup"><span data-stu-id="13698-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13698-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="13698-105">Attributes and Elements</span></span>  
 <span data-ttu-id="13698-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="13698-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13698-107">特性</span><span class="sxs-lookup"><span data-stu-id="13698-107">Attributes</span></span>  
  
|<span data-ttu-id="13698-108">属性</span><span class="sxs-lookup"><span data-stu-id="13698-108">Attribute</span></span>|<span data-ttu-id="13698-109">说明</span><span class="sxs-lookup"><span data-stu-id="13698-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="13698-110">name</span><span class="sxs-lookup"><span data-stu-id="13698-110">name</span></span>|<span data-ttu-id="13698-111">一个字符串，指定要订阅的书签记录的名称。</span><span class="sxs-lookup"><span data-stu-id="13698-111">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13698-112">子元素</span><span class="sxs-lookup"><span data-stu-id="13698-112">Child Elements</span></span>  
 <span data-ttu-id="13698-113">无。</span><span class="sxs-lookup"><span data-stu-id="13698-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13698-114">父元素</span><span class="sxs-lookup"><span data-stu-id="13698-114">Parent Elements</span></span>  
  
|<span data-ttu-id="13698-115">元素</span><span class="sxs-lookup"><span data-stu-id="13698-115">Element</span></span>|<span data-ttu-id="13698-116">描述</span><span class="sxs-lookup"><span data-stu-id="13698-116">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|<span data-ttu-id="13698-117">表示一个查询集合，这些查询用于跟踪工作流实例中的书签恢复。</span><span class="sxs-lookup"><span data-stu-id="13698-117">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13698-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13698-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="13698-119">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="13698-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="13698-120">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="13698-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
