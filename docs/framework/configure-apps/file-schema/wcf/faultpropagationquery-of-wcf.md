---
title: <faultPropagationQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: a6ef4e198caec4a1f21cedf2ff46d390aeaa2d3b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855327"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="f229a-102">\<faultPropagationQuery>WCF 的</span><span class="sxs-lookup"><span data-stu-id="f229a-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="f229a-103">表示一个用于跟踪在活动中发生的错误的处理的查询。</span><span class="sxs-lookup"><span data-stu-id="f229a-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f229a-104">每次 FaultHandler 处理错误时，都会发生此事件。</span><span class="sxs-lookup"><span data-stu-id="f229a-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="f229a-105">应使用此类查询来跟踪对在活动中出现的错误进行的处理。</span><span class="sxs-lookup"><span data-stu-id="f229a-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="f229a-106">跟踪参与者需要用此查询来订阅错误传播记录。</span><span class="sxs-lookup"><span data-stu-id="f229a-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="f229a-107">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="f229a-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**  

## <a name="syntax"></a><span data-ttu-id="f229a-108">语法</span><span class="sxs-lookup"><span data-stu-id="f229a-108">Syntax</span></span>

```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String" />
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f229a-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f229a-109">Attributes and elements</span></span>

<span data-ttu-id="f229a-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f229a-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f229a-111">特性</span><span class="sxs-lookup"><span data-stu-id="f229a-111">Attributes</span></span>

|<span data-ttu-id="f229a-112">属性</span><span class="sxs-lookup"><span data-stu-id="f229a-112">Attribute</span></span>|<span data-ttu-id="f229a-113">说明</span><span class="sxs-lookup"><span data-stu-id="f229a-113">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="f229a-114">一个字符串，指定传播错误的错误处理程序活动的名称。</span><span class="sxs-lookup"><span data-stu-id="f229a-114">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="f229a-115">默认值为 \* ，指示为所有活动返回错误传播记录。</span><span class="sxs-lookup"><span data-stu-id="f229a-115">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="f229a-116">一个字符串，指定导致错误的活动的名称。</span><span class="sxs-lookup"><span data-stu-id="f229a-116">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="f229a-117">子元素</span><span class="sxs-lookup"><span data-stu-id="f229a-117">Child elements</span></span>

<span data-ttu-id="f229a-118">无。</span><span class="sxs-lookup"><span data-stu-id="f229a-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f229a-119">父元素</span><span class="sxs-lookup"><span data-stu-id="f229a-119">Parent elements</span></span>

|<span data-ttu-id="f229a-120">元素</span><span class="sxs-lookup"><span data-stu-id="f229a-120">Element</span></span>|<span data-ttu-id="f229a-121">描述</span><span class="sxs-lookup"><span data-stu-id="f229a-121">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="f229a-122">表示一个配置元素列表，这些元素用于跟踪某个活动中发生的错误的处理。</span><span class="sxs-lookup"><span data-stu-id="f229a-122">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f229a-123">每次 FaultHandler 处理错误时，都会发生此事件。</span><span class="sxs-lookup"><span data-stu-id="f229a-123">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="f229a-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f229a-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f229a-125">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="f229a-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f229a-126">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="f229a-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
