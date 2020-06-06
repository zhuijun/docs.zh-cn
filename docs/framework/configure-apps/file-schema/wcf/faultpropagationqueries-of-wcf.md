---
title: <faultPropagationQueries>WCF 的
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 709c2c6907b4d0d28118f9de12edb047aa16d741
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855266"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="5927a-102">\<faultPropagationQueries>WCF 的</span><span class="sxs-lookup"><span data-stu-id="5927a-102">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="5927a-103">表示一个查询集合，这些查询用于跟踪在某个活动中发生的错误的处理。</span><span class="sxs-lookup"><span data-stu-id="5927a-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="5927a-104">每次 FaultHandler 处理错误时，都会发生此事件。</span><span class="sxs-lookup"><span data-stu-id="5927a-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="5927a-105">应使用此类查询来跟踪对在活动中出现的错误进行的处理。</span><span class="sxs-lookup"><span data-stu-id="5927a-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="5927a-106">跟踪参与者需要用此查询来订阅错误传播记录。</span><span class="sxs-lookup"><span data-stu-id="5927a-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="5927a-107">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="5927a-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="5927a-108">语法</span><span class="sxs-lookup"><span data-stu-id="5927a-108">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5927a-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="5927a-109">Attributes and elements</span></span>

<span data-ttu-id="5927a-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5927a-110">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="5927a-111">特性</span><span class="sxs-lookup"><span data-stu-id="5927a-111">Attributes</span></span>

<span data-ttu-id="5927a-112">无。</span><span class="sxs-lookup"><span data-stu-id="5927a-112">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="5927a-113">子元素</span><span class="sxs-lookup"><span data-stu-id="5927a-113">Child elements</span></span>

|<span data-ttu-id="5927a-114">元素</span><span class="sxs-lookup"><span data-stu-id="5927a-114">Element</span></span>|<span data-ttu-id="5927a-115">说明</span><span class="sxs-lookup"><span data-stu-id="5927a-115">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="5927a-116">一个查询，用于跟踪在活动中发生的错误的处理。</span><span class="sxs-lookup"><span data-stu-id="5927a-116">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="5927a-117">每次 FaultHandler 处理错误时，都会发生此事件。</span><span class="sxs-lookup"><span data-stu-id="5927a-117">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5927a-118">父元素</span><span class="sxs-lookup"><span data-stu-id="5927a-118">Parent elements</span></span>  
  
|<span data-ttu-id="5927a-119">元素</span><span class="sxs-lookup"><span data-stu-id="5927a-119">Element</span></span>|<span data-ttu-id="5927a-120">说明</span><span class="sxs-lookup"><span data-stu-id="5927a-120">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="5927a-121">一个配置元素，包含 `activityDefinitionId` 属性所标识的特定工作流的所有查询。</span><span class="sxs-lookup"><span data-stu-id="5927a-121">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5927a-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5927a-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5927a-123">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="5927a-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5927a-124">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="5927a-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
