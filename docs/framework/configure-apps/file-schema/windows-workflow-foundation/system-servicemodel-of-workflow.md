---
title: <System.servicemodel> 工作流
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: c18cc4886d3e7a19b750a005b27d00a841b9fc5d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194851"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="3c840-102">\<system.serviceModel> 的工作流</span><span class="sxs-lookup"><span data-stu-id="3c840-102">\<system.serviceModel> of workflow</span></span>

<span data-ttu-id="3c840-103">此配置节包含所有工作流配置元素。</span><span class="sxs-lookup"><span data-stu-id="3c840-103">This configuration section contains all the workflow configuration elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.ServiceModel>**  
  
## <a name="syntax"></a><span data-ttu-id="3c840-104">语法</span><span class="sxs-lookup"><span data-stu-id="3c840-104">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
    <behavior name="String">  
      <bufferReceive maxPendingMessagesPerChannel="Integer" />  
      <etwTracking profileName="String" />  
     <sendMessageChannelCache allowUnsafeCaching="Boolean" >
        <channelSettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
        <factorySettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
     </sendMessageChannelCache>  
      <sqlWorkflowInstanceStore
          connectionStringName="String"
          hostLockRenewalPeriod="TimeSpan"  
          instanceCompletionAction="DeleteNothing/DeleteAll"  
          instanceEncodingAction="None/GZip"  
          instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"  
          runnableInstancesDetectionPeriod="TimeSpan" />  
      <workflowIdle timeToPersist="TimeSpan"  
          timeToUnload="TimeSpan" />  
      <workflowUnhandledExceptionAction="Abandon/AbandonAndSuspend/Cancel/Terminate" />  
    </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <tracking>
     <participants>
      <add name="String"
           profileName="String"  
           type="String" />
     </participants>
    <trackingProfile name="String">  
      <workflow activityDefinitionId="String">  
          <activityScheduledQueries>  
             <activityScheduledQuery activityName="String"  
                 childActivityName="String"/>  
          </activityScheduledQueries>  
             <activityStateQuery activityName="String" />  
                <arguments>  
                   <argument name="String"/>  
                </arguments>  
                <states>  
                   <state name="String"/>  
                </states>  
                <variables>  
                   <variable name="String"/>  
                </variables>  
          </activityStateQueries>  
          <bookmarkResumptionQueries>  
             <bookmarkResumptionQuery name="String" />  
          </bookmarkResumptionQueries>  
          <cancelRequestQueries>  
             <cancelRequestQuery activityName="String"  
                 childActivityName="String"/>  
          </cancelRequestQueries>  
          <customTrackingQueries>  
             <customTrackingQuery activityName="String"  
                 name="String"/>  
          </customTrackingQueries>  
          <faultPropagationQueries>  
             <faultPropagationQuery activityName="String"  
                 faultHandlerActivityName="String"/>  
          </faultPropagationQueries>  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
              <states>  
                 <state name="String"/>  
              </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>
   </profiles>  
  </tracking>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c840-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="3c840-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3c840-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3c840-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c840-107">特性</span><span class="sxs-lookup"><span data-stu-id="3c840-107">Attributes</span></span>  

 <span data-ttu-id="3c840-108">无</span><span class="sxs-lookup"><span data-stu-id="3c840-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3c840-109">子元素</span><span class="sxs-lookup"><span data-stu-id="3c840-109">Child Elements</span></span>  
  
|<span data-ttu-id="3c840-110">元素</span><span class="sxs-lookup"><span data-stu-id="3c840-110">Element</span></span>|<span data-ttu-id="3c840-111">描述</span><span class="sxs-lookup"><span data-stu-id="3c840-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviors>](behaviors-of-workflow.md)|<span data-ttu-id="3c840-112">本节定义 **serviceBehaviors** 集合。</span><span class="sxs-lookup"><span data-stu-id="3c840-112">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="3c840-113">集合中的每个元素定义服务所使用的行为元素。</span><span class="sxs-lookup"><span data-stu-id="3c840-113">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="3c840-114">每个行为元素都由其唯一 **名称** 属性标识。</span><span class="sxs-lookup"><span data-stu-id="3c840-114">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[\<tracking>](tracking.md)|<span data-ttu-id="3c840-115">表示一个配置节，用于定义工作流服务的跟踪设置。</span><span class="sxs-lookup"><span data-stu-id="3c840-115">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="3c840-116">有关工作流跟踪及其配置的详细信息，请参阅工作流 [跟踪和跟踪](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) 和 [配置工作流跟踪](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="3c840-116">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3c840-117">父元素</span><span class="sxs-lookup"><span data-stu-id="3c840-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3c840-118">元素</span><span class="sxs-lookup"><span data-stu-id="3c840-118">Element</span></span>|<span data-ttu-id="3c840-119">描述</span><span class="sxs-lookup"><span data-stu-id="3c840-119">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="3c840-120">.NET 配置文件中的所有配置元素的根元素。</span><span class="sxs-lookup"><span data-stu-id="3c840-120">The root element for all configuration elements in a .NET configuration file.</span></span>|
