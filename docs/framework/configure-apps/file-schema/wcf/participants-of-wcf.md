---
title: <participants> WCF 的
ms.date: 03/30/2017
ms.assetid: d99dbddc-0057-4e18-8e42-f91411d39970
ms.openlocfilehash: 4ee70d3a9b5d75adc639f1e3922cfde6737e9e01
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170150"
---
# <a name="participants-of-wcf"></a><span data-ttu-id="3dcc6-102">\<participants> WCF 的</span><span class="sxs-lookup"><span data-stu-id="3dcc6-102">\<participants> of WCF</span></span>

<span data-ttu-id="3dcc6-103">配置一列跟踪参与者，它们侦听直接从运行时发出的跟踪记录，并按照它们的任何方式处理这些记录。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-103">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="3dcc6-104">这包括写入特定输出（例如，文件、控制台、ETW）、处理/聚合记录或可能需要的任何其他组合。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
<span data-ttu-id="3dcc6-105">有关工作流跟踪和跟踪参与者的详细信息，请参阅 [工作流跟踪和](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) 跟踪和 [跟踪参与者](../../../windows-workflow-foundation/tracking-participants.md)。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<participants>**  
  
## <a name="syntax"></a><span data-ttu-id="3dcc6-106">语法</span><span class="sxs-lookup"><span data-stu-id="3dcc6-106">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3dcc6-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="3dcc6-107">Attributes and Elements</span></span>  

 <span data-ttu-id="3dcc6-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3dcc6-109">特性</span><span class="sxs-lookup"><span data-stu-id="3dcc6-109">Attributes</span></span>  

 <span data-ttu-id="3dcc6-110">无。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3dcc6-111">子元素</span><span class="sxs-lookup"><span data-stu-id="3dcc6-111">Child Elements</span></span>  
  
|<span data-ttu-id="3dcc6-112">元素</span><span class="sxs-lookup"><span data-stu-id="3dcc6-112">Element</span></span>|<span data-ttu-id="3dcc6-113">描述</span><span class="sxs-lookup"><span data-stu-id="3dcc6-113">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](../windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="3dcc6-114">包含跟踪参与者的设置。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-114">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3dcc6-115">父元素</span><span class="sxs-lookup"><span data-stu-id="3dcc6-115">Parent Elements</span></span>  
  
|<span data-ttu-id="3dcc6-116">元素</span><span class="sxs-lookup"><span data-stu-id="3dcc6-116">Element</span></span>|<span data-ttu-id="3dcc6-117">描述</span><span class="sxs-lookup"><span data-stu-id="3dcc6-117">Description</span></span>|  
|-------------|-----------------|  
|[\<tracking>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="3dcc6-118">表示一个配置节，用于定义工作流服务的跟踪设置。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-118">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3dcc6-119">备注</span><span class="sxs-lookup"><span data-stu-id="3dcc6-119">Remarks</span></span>  

 <span data-ttu-id="3dcc6-120">跟踪参与者用于获取从工作流发出的跟踪数据并将其存储在不同的媒体中。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-120">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="3dcc6-121">同样，也可以在跟踪参与者中执行对跟踪记录的任何后续处理。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-121">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="3dcc6-122">多个跟踪参与者可同时使用跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-122">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="3dcc6-123">每个跟踪参与者都可与不同的跟踪配置文件关联。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-123">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="3dcc6-124">提供了将跟踪记录写入 ETW 会话的标准跟踪参与者。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-124">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="3dcc6-125">通过在配置文件中添加特定于跟踪的行为，可以对工作流服务配置参与者。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-125">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="3dcc6-126">通过启用 ETW 跟踪参与者，可以在事件查看器中查看跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-126">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="3dcc6-127">如果这不能满足您的需求，您还可以编写自定义跟踪参与者。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-127">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dcc6-128">示例</span><span class="sxs-lookup"><span data-stu-id="3dcc6-128">Example</span></span>  

 <span data-ttu-id="3dcc6-129">下面的配置示例演示在 Web.config 文件中配置的标准 ETW 跟踪参与者。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="3dcc6-130">ETW 跟踪参与者用于将跟踪记录写入 ETW 的提供程序 ID 在 `<diagnostics>` 节中定义。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="3dcc6-131">跟踪参与者具有一个与其关联的配置文件，用来指定跟踪参与者已订阅的跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="3dcc6-132">它由 `profileName` 元素的 `<add>` 特性进行定义。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-132">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="3dcc6-133">定义这些内容后，跟踪参与者将被添加到 `<etwTracking>` 服务行为中。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-133">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="3dcc6-134">这会将所选跟踪参与者添加到工作流实例的扩展中，以便它们开始接收跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="3dcc6-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0" />
  </system.web>
  <system.serviceModel>
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />
    <tracking>
      <participants>
        <add name="EtwTrackingParticipant"
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
             profileName="HealthMonitoring_Tracking_Profile"/>
      </participants>
    </tracking>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile"/>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="3dcc6-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="3dcc6-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- [<span data-ttu-id="3dcc6-136">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="3dcc6-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3dcc6-137">跟踪参与者</span><span class="sxs-lookup"><span data-stu-id="3dcc6-137">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
