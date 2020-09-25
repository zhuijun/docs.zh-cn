---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: efd1e4e54223ff9f5d60b4087fbe5b6bebf1af2f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189583"
---
# \<bookmarkResumptionQuery>

<span data-ttu-id="66197-101">表示一个查询，该查询用于跟踪工作流实例中的书签恢复。</span><span class="sxs-lookup"><span data-stu-id="66197-101">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="66197-102">跟踪参与者需要用此查询来订阅书签恢复记录。</span><span class="sxs-lookup"><span data-stu-id="66197-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="66197-103">有关跟踪配置文件查询的详细信息，请参阅 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="66197-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="66197-104">语法</span><span class="sxs-lookup"><span data-stu-id="66197-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66197-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="66197-105">Attributes and Elements</span></span>  

 <span data-ttu-id="66197-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="66197-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66197-107">特性</span><span class="sxs-lookup"><span data-stu-id="66197-107">Attributes</span></span>  
  
|<span data-ttu-id="66197-108">属性</span><span class="sxs-lookup"><span data-stu-id="66197-108">Attribute</span></span>|<span data-ttu-id="66197-109">说明</span><span class="sxs-lookup"><span data-stu-id="66197-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="66197-110">name</span><span class="sxs-lookup"><span data-stu-id="66197-110">name</span></span>|<span data-ttu-id="66197-111">一个字符串，指定要订阅的书签记录的名称。</span><span class="sxs-lookup"><span data-stu-id="66197-111">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66197-112">子元素</span><span class="sxs-lookup"><span data-stu-id="66197-112">Child Elements</span></span>  

 <span data-ttu-id="66197-113">无。</span><span class="sxs-lookup"><span data-stu-id="66197-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="66197-114">父元素</span><span class="sxs-lookup"><span data-stu-id="66197-114">Parent Elements</span></span>  
  
|<span data-ttu-id="66197-115">元素</span><span class="sxs-lookup"><span data-stu-id="66197-115">Element</span></span>|<span data-ttu-id="66197-116">描述</span><span class="sxs-lookup"><span data-stu-id="66197-116">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|<span data-ttu-id="66197-117">表示一个查询集合，这些查询用于跟踪工作流实例中的书签恢复。</span><span class="sxs-lookup"><span data-stu-id="66197-117">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66197-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="66197-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="66197-119">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="66197-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="66197-120">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="66197-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
