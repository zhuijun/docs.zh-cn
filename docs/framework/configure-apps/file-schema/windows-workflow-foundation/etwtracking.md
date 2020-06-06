---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: d562bd4e3d46a1bdf41fc4065fee926850a49aa1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152166"
---
# \<etwTracking>
<span data-ttu-id="d9f62-101">一种服务行为，允许服务使用 <xref:System.Activities.Tracking.EtwTrackingParticipant> 来利用 ETW 跟踪。</span><span class="sxs-lookup"><span data-stu-id="d9f62-101">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**  
  
## <a name="syntax"></a><span data-ttu-id="d9f62-102">语法</span><span class="sxs-lookup"><span data-stu-id="d9f62-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9f62-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="d9f62-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d9f62-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d9f62-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9f62-105">特性</span><span class="sxs-lookup"><span data-stu-id="d9f62-105">Attributes</span></span>  
  
|<span data-ttu-id="d9f62-106">属性</span><span class="sxs-lookup"><span data-stu-id="d9f62-106">Attribute</span></span>|<span data-ttu-id="d9f62-107">说明</span><span class="sxs-lookup"><span data-stu-id="d9f62-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d9f62-108">profileName</span><span class="sxs-lookup"><span data-stu-id="d9f62-108">profileName</span></span>|<span data-ttu-id="d9f62-109">一个字符串，指定与此行为关联的跟踪配置文件的名称。</span><span class="sxs-lookup"><span data-stu-id="d9f62-109">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9f62-110">子元素</span><span class="sxs-lookup"><span data-stu-id="d9f62-110">Child Elements</span></span>  
 <span data-ttu-id="d9f62-111">无。</span><span class="sxs-lookup"><span data-stu-id="d9f62-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d9f62-112">父元素</span><span class="sxs-lookup"><span data-stu-id="d9f62-112">Parent Elements</span></span>  
  
|<span data-ttu-id="d9f62-113">元素</span><span class="sxs-lookup"><span data-stu-id="d9f62-113">Element</span></span>|<span data-ttu-id="d9f62-114">描述</span><span class="sxs-lookup"><span data-stu-id="d9f62-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9f62-115">\<behavior>个\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="d9f62-115">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="d9f62-116">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="d9f62-116">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9f62-117">注解</span><span class="sxs-lookup"><span data-stu-id="d9f62-117">Remarks</span></span>  
 <span data-ttu-id="d9f62-118">在添加到服务的行为配置后，此配置元素对工作流服务配置跟踪参与者。</span><span class="sxs-lookup"><span data-stu-id="d9f62-118">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="d9f62-119">跟踪参与者用于获取从工作流发出的跟踪数据并将其存储在不同的媒体中。</span><span class="sxs-lookup"><span data-stu-id="d9f62-119">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="d9f62-120">同样，也可以在跟踪参与者中执行对跟踪记录的任何后续处理。</span><span class="sxs-lookup"><span data-stu-id="d9f62-120">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9f62-121">示例</span><span class="sxs-lookup"><span data-stu-id="d9f62-121">Example</span></span>  
 <span data-ttu-id="d9f62-122">下面的配置示例演示在 Web.config 文件中配置的标准 ETW 跟踪参与者。</span><span class="sxs-lookup"><span data-stu-id="d9f62-122">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="d9f62-123">ETW 跟踪参与者用于将跟踪记录写入 ETW 的提供程序 Id 在部分中定义 **\<diagnostics>** 。</span><span class="sxs-lookup"><span data-stu-id="d9f62-123">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="d9f62-124">跟踪参与者具有一个与其关联的配置文件，用来指定跟踪参与者已订阅的跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="d9f62-124">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="d9f62-125">这由元素的**profileName**属性定义 **\<add>** 。</span><span class="sxs-lookup"><span data-stu-id="d9f62-125">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="d9f62-126">一旦定义了这些操作，就会将跟踪参与者添加到 **\<etwTracking>** 服务行为中。</span><span class="sxs-lookup"><span data-stu-id="d9f62-126">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="d9f62-127">这会将所选跟踪参与者添加到工作流实例的扩展中，以便它们开始接收跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="d9f62-127">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>
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
  
## <a name="see-also"></a><span data-ttu-id="d9f62-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9f62-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="d9f62-129">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="d9f62-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d9f62-130">跟踪参与者</span><span class="sxs-lookup"><span data-stu-id="d9f62-130">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
