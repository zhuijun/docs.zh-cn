---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 6b43a570b4d4534adce1ef5ab394849651e3ac0e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398721"
---
# \<faultPropagationQuery>

<span data-ttu-id="60ac7-101">表示一个用于跟踪在活动中发生的错误的处理的查询。</span><span class="sxs-lookup"><span data-stu-id="60ac7-101">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="60ac7-102">每次 FaultHandler 处理错误时，都会发生此事件。</span><span class="sxs-lookup"><span data-stu-id="60ac7-102">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="60ac7-103">应使用此类查询来跟踪对在活动中出现的错误进行的处理。</span><span class="sxs-lookup"><span data-stu-id="60ac7-103">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="60ac7-104">跟踪参与者需要用此查询来订阅错误传播记录。</span><span class="sxs-lookup"><span data-stu-id="60ac7-104">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="60ac7-105">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="60ac7-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**

## <a name="syntax"></a><span data-ttu-id="60ac7-106">语法</span><span class="sxs-lookup"><span data-stu-id="60ac7-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="60ac7-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="60ac7-107">Attributes and Elements</span></span>

<span data-ttu-id="60ac7-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="60ac7-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="60ac7-109">特性</span><span class="sxs-lookup"><span data-stu-id="60ac7-109">Attributes</span></span>

|<span data-ttu-id="60ac7-110">属性</span><span class="sxs-lookup"><span data-stu-id="60ac7-110">Attribute</span></span>|<span data-ttu-id="60ac7-111">说明</span><span class="sxs-lookup"><span data-stu-id="60ac7-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="60ac7-112">activityName</span><span class="sxs-lookup"><span data-stu-id="60ac7-112">activityName</span></span>|<span data-ttu-id="60ac7-113">一个字符串，指定传播错误的错误处理程序活动的名称。</span><span class="sxs-lookup"><span data-stu-id="60ac7-113">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="60ac7-114">默认值为 \*，指示为所有活动返回错误传播记录。</span><span class="sxs-lookup"><span data-stu-id="60ac7-114">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="60ac7-115">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="60ac7-115">faultHandlerActivityName</span></span>|<span data-ttu-id="60ac7-116">一个字符串，指定导致错误的活动的名称。</span><span class="sxs-lookup"><span data-stu-id="60ac7-116">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="60ac7-117">子元素</span><span class="sxs-lookup"><span data-stu-id="60ac7-117">Child Elements</span></span>

<span data-ttu-id="60ac7-118">无。</span><span class="sxs-lookup"><span data-stu-id="60ac7-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="60ac7-119">父元素</span><span class="sxs-lookup"><span data-stu-id="60ac7-119">Parent Elements</span></span>

|<span data-ttu-id="60ac7-120">元素</span><span class="sxs-lookup"><span data-stu-id="60ac7-120">Element</span></span>|<span data-ttu-id="60ac7-121">描述</span><span class="sxs-lookup"><span data-stu-id="60ac7-121">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries.md)|<span data-ttu-id="60ac7-122">表示一个配置元素列表，这些元素用于跟踪某个活动中发生的错误的处理。</span><span class="sxs-lookup"><span data-stu-id="60ac7-122">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="60ac7-123">每次 FaultHandler 处理错误时，都会发生此事件。</span><span class="sxs-lookup"><span data-stu-id="60ac7-123">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="60ac7-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="60ac7-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="60ac7-125">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="60ac7-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="60ac7-126">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="60ac7-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
