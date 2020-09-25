---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 4663ccedcafb6b151de75568afd3743c83c75224
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189820"
---
# \<activityStateQueries>

<span data-ttu-id="23471-101">表示一个查询集合，这些查询用于跟踪构成工作流实例的活动的生命周期更改。</span><span class="sxs-lookup"><span data-stu-id="23471-101">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="23471-102">例如，你可能想要跟踪每次在工作流实例中完成 "发送电子邮件" 活动的时间。</span><span class="sxs-lookup"><span data-stu-id="23471-102">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="23471-103">跟踪参与者需要用此查询来订阅活动状态记录对象。</span><span class="sxs-lookup"><span data-stu-id="23471-103">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="23471-104">在 ActivityStates 中指定了要订阅的可用状态。</span><span class="sxs-lookup"><span data-stu-id="23471-104">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="23471-105">有关跟踪配置文件查询的详细信息，请参阅 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="23471-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="23471-106">语法</span><span class="sxs-lookup"><span data-stu-id="23471-106">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23471-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="23471-107">Attributes and Elements</span></span>  

 <span data-ttu-id="23471-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="23471-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23471-109">特性</span><span class="sxs-lookup"><span data-stu-id="23471-109">Attributes</span></span>  

 <span data-ttu-id="23471-110">无。</span><span class="sxs-lookup"><span data-stu-id="23471-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="23471-111">子元素</span><span class="sxs-lookup"><span data-stu-id="23471-111">Child Elements</span></span>  
  
|<span data-ttu-id="23471-112">元素</span><span class="sxs-lookup"><span data-stu-id="23471-112">Element</span></span>|<span data-ttu-id="23471-113">描述</span><span class="sxs-lookup"><span data-stu-id="23471-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="23471-114">一个查询，用于跟踪在活动中发生的错误的处理。</span><span class="sxs-lookup"><span data-stu-id="23471-114">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="23471-115">每次 FaultHandler 处理错误时，都会发生此事件。</span><span class="sxs-lookup"><span data-stu-id="23471-115">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="23471-116">父元素</span><span class="sxs-lookup"><span data-stu-id="23471-116">Parent Elements</span></span>  
  
|<span data-ttu-id="23471-117">元素</span><span class="sxs-lookup"><span data-stu-id="23471-117">Element</span></span>|<span data-ttu-id="23471-118">描述</span><span class="sxs-lookup"><span data-stu-id="23471-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="23471-119">一个配置元素，该元素包含由 **activityDefinitionId** 属性标识的特定工作流的所有查询。</span><span class="sxs-lookup"><span data-stu-id="23471-119">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23471-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="23471-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="23471-121">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="23471-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="23471-122">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="23471-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
