---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: 72a2d6f8439e720bb7bf236bd942552224e85501
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189722"
---
# \<argument>

<span data-ttu-id="15841-101">一个配置元素，表示与某一活动状态查询关联的参数。</span><span class="sxs-lookup"><span data-stu-id="15841-101">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="15841-102">有关跟踪配置文件查询的详细信息，请参阅 [跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="15841-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<arguments>**](arguments.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<argument>**  
  
## <a name="syntax"></a><span data-ttu-id="15841-103">语法</span><span class="sxs-lookup"><span data-stu-id="15841-103">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15841-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="15841-104">Attributes and Elements</span></span>  

 <span data-ttu-id="15841-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="15841-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15841-106">特性</span><span class="sxs-lookup"><span data-stu-id="15841-106">Attributes</span></span>  
  
|<span data-ttu-id="15841-107">属性</span><span class="sxs-lookup"><span data-stu-id="15841-107">Attribute</span></span>|<span data-ttu-id="15841-108">说明</span><span class="sxs-lookup"><span data-stu-id="15841-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="15841-109">name</span><span class="sxs-lookup"><span data-stu-id="15841-109">name</span></span>|<span data-ttu-id="15841-110">一个字符串，指定该参数的名称。</span><span class="sxs-lookup"><span data-stu-id="15841-110">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15841-111">子元素</span><span class="sxs-lookup"><span data-stu-id="15841-111">Child Elements</span></span>  

 <span data-ttu-id="15841-112">无。</span><span class="sxs-lookup"><span data-stu-id="15841-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="15841-113">父元素</span><span class="sxs-lookup"><span data-stu-id="15841-113">Parent Elements</span></span>  
  
|<span data-ttu-id="15841-114">元素</span><span class="sxs-lookup"><span data-stu-id="15841-114">Element</span></span>|<span data-ttu-id="15841-115">描述</span><span class="sxs-lookup"><span data-stu-id="15841-115">Description</span></span>|  
|-------------|-----------------|  
|[\<arguments>](arguments.md)|<span data-ttu-id="15841-116">与此活动查询关联的自变量的集合。</span><span class="sxs-lookup"><span data-stu-id="15841-116">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15841-117">备注</span><span class="sxs-lookup"><span data-stu-id="15841-117">Remarks</span></span>  

 <span data-ttu-id="15841-118">ActivityStateQuery 的一项独特功能是能够在跟踪工作流的执行时提取数据。</span><span class="sxs-lookup"><span data-stu-id="15841-118">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="15841-119">这在访问跟踪记录后续执行时可提供其他上下文。</span><span class="sxs-lookup"><span data-stu-id="15841-119">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="15841-120">您可以使用 [\<arguments>](arguments.md) 、 [\<states>](states.md) 和 [\<states>](states.md) 元素从工作流中的任何活动提取任何变量或参数。</span><span class="sxs-lookup"><span data-stu-id="15841-120">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="15841-121">下面的示例演示用于在发出活动的 `Closed` 跟踪记录时提取变量和自变量的活动状态查询。</span><span class="sxs-lookup"><span data-stu-id="15841-121">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="15841-122">变量和参数只能通过 ActivityStateRecord 提取，因此使用在跟踪配置文件内进行订阅 [\<activityStateQuery>](activitystatequery.md) 。</span><span class="sxs-lookup"><span data-stu-id="15841-122">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="15841-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="15841-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="15841-124">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="15841-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="15841-125">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="15841-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
