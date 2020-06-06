---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 3d6d03638ec5806448a16cc32b37e630d6198624
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152126"
---
# \<faultPropagationQueries>
<span data-ttu-id="dde2d-101">表示一个查询集合，这些查询用于跟踪在某个活动中发生的错误的处理。</span><span class="sxs-lookup"><span data-stu-id="dde2d-101">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="dde2d-102">每次 FaultHandler 处理错误时，都会发生此事件。</span><span class="sxs-lookup"><span data-stu-id="dde2d-102">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="dde2d-103">应使用此类查询来跟踪对在活动中出现的错误进行的处理。</span><span class="sxs-lookup"><span data-stu-id="dde2d-103">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="dde2d-104">跟踪参与者需要用此查询来订阅错误传播记录。</span><span class="sxs-lookup"><span data-stu-id="dde2d-104">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="dde2d-105">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="dde2d-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**
  
## <a name="syntax"></a><span data-ttu-id="dde2d-106">语法</span><span class="sxs-lookup"><span data-stu-id="dde2d-106">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String"
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dde2d-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="dde2d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="dde2d-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dde2d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dde2d-109">特性</span><span class="sxs-lookup"><span data-stu-id="dde2d-109">Attributes</span></span>  
 <span data-ttu-id="dde2d-110">无。</span><span class="sxs-lookup"><span data-stu-id="dde2d-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dde2d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="dde2d-111">Child Elements</span></span>  
  
|<span data-ttu-id="dde2d-112">元素</span><span class="sxs-lookup"><span data-stu-id="dde2d-112">Element</span></span>|<span data-ttu-id="dde2d-113">说明</span><span class="sxs-lookup"><span data-stu-id="dde2d-113">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="dde2d-114">一个查询，用于跟踪在活动中发生的错误的处理。</span><span class="sxs-lookup"><span data-stu-id="dde2d-114">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="dde2d-115">每次 FaultHandler 处理错误时，都会发生此事件。</span><span class="sxs-lookup"><span data-stu-id="dde2d-115">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dde2d-116">父元素</span><span class="sxs-lookup"><span data-stu-id="dde2d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="dde2d-117">元素</span><span class="sxs-lookup"><span data-stu-id="dde2d-117">Element</span></span>|<span data-ttu-id="dde2d-118">说明</span><span class="sxs-lookup"><span data-stu-id="dde2d-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="dde2d-119">一个配置元素，该元素包含由**activityDefinitionId**属性标识的特定工作流的所有查询。</span><span class="sxs-lookup"><span data-stu-id="dde2d-119">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dde2d-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dde2d-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="dde2d-121">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="dde2d-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dde2d-122">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="dde2d-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
