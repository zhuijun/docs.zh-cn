---
title: 跟踪参与者
ms.date: 03/30/2017
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
ms.openlocfilehash: 9455524da4451bf904d8449412e8f625542a1635
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551447"
---
# <a name="tracking-participants"></a><span data-ttu-id="1e9b6-102">跟踪参与者</span><span class="sxs-lookup"><span data-stu-id="1e9b6-102">Tracking Participants</span></span>
<span data-ttu-id="1e9b6-103">跟踪参与者是扩展点，允许工作流开发人员访问 <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> 对象并对其进行处理。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-103">Tracking participants are extensibility points that allow a workflow developer to access <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objects and process them.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="1e9b6-104">包括一个标准跟踪参与者，可将跟踪记录作为 Windows 事件跟踪 (ETW) 事件写入。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-104">includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="1e9b6-105">如果这不能满足您的需求，您还可以编写自定义跟踪参与者。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-105">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="tracking-participants"></a><span data-ttu-id="1e9b6-106">跟踪参与者</span><span class="sxs-lookup"><span data-stu-id="1e9b6-106">Tracking Participants</span></span>  
 <span data-ttu-id="1e9b6-107">跟踪基础结构允许对传出跟踪记录应用筛选器，以便参与者可订阅该记录的子集。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-107">The tracking infrastructure allows the application of a filter on the outgoing tracking records such that a participant can subscribe to a subset of the records.</span></span> <span data-ttu-id="1e9b6-108">应用筛选器的机制是通过跟踪配置文件来实现的。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-108">The mechanism to apply a filter is through a tracking profile.</span></span>  
  
 <span data-ttu-id="1e9b6-109">中 Windows Workflow Foundation (WF) [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 提供了一个跟踪参与者，该参与者将跟踪记录写入 ETW 会话。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-109">Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] provides a tracking participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="1e9b6-110">通过在配置文件中添加特定于跟踪的行为，可以对工作流服务配置参与者。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-110">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="1e9b6-111">通过启用 ETW 跟踪参与者，可以在事件查看器中查看跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-111">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="1e9b6-112">基于 ETW 的跟踪的 SDK 示例是一种很好的方法，可使用基于 ETW 的跟踪参与者来熟悉 WF 跟踪。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-112">The SDK sample for ETW-based tracking is a good way to get familiar with WF tracking using the ETW-based tracking participant.</span></span>  
  
## <a name="etw-tracking-participant"></a><span data-ttu-id="1e9b6-113">ETW 跟踪参与者</span><span class="sxs-lookup"><span data-stu-id="1e9b6-113">ETW Tracking Participant</span></span>  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="1e9b6-114">包括一个 ETW 跟踪参与者，可将跟踪记录写入 ETW 会话。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-114">includes an ETW Tracking Participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="1e9b6-115">它的实现方式非常高效，对应用程序的性能或对服务器的吞吐量影响非常小。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-115">This is done in a very efficient manner with minimal impact to the application’s performance or to the server’s throughput.</span></span> <span data-ttu-id="1e9b6-116">使用标准 ETW 跟踪参与者的一个优点是，它接收的跟踪记录可以在 Windows 事件查看器中与其他应用程序日志及系统日志一起查看。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-116">An advantage of using the standard ETW tracking participant is that the tracking records it receives can be viewed with the other application and system logs in the Windows Event Viewer.</span></span>  
  
 <span data-ttu-id="1e9b6-117">在 Web.config 文件中配置标准 ETW 跟踪参与者，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-117">The standard ETW tracking participant is configured in the Web.config file as shown in the following example.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
   <tracking>  
      <profiles>  
        <trackingProfile name="Sample Tracking Profile">  
        ….  
       </trackingProfile>  
      </profiles>  
    </tracking>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> <span data-ttu-id="1e9b6-118">如果未指定 `trackingProfile` 名称，例如只使用 `<etwTracking/>` 或 `<etwTracking profileName=""/>`，则使用 Machine.config 文件中随 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 安装的默认跟踪配置文件。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-118">If a `trackingProfile` name is not specified, such as just `<etwTracking/>` or `<etwTracking profileName=""/>`, then the default tracking profile installed with the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] in the Machine.config file is used.</span></span>  
  
 <span data-ttu-id="1e9b6-119">在 Machine.config 文件中，默认跟踪配置文件订阅工作流实例记录和错误。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-119">In the Machine.config file, the default tracking profile subscribes to workflow instance records and faults.</span></span>  
  
 <span data-ttu-id="1e9b6-120">在 ETW 中，事件通过提供程序 ID 写入 ETW 会话中。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-120">In ETW, events are written to the ETW session through a provider ID.</span></span> <span data-ttu-id="1e9b6-121">ETW 跟踪参与者用于将跟踪记录写入 ETW 的提供程序 ID 在 Web.config 文件的 diagnostics 节（`<system.serviceModel><diagnostics>` 下）中定义。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-121">The provider ID that the ETW tracking participant uses for writing the tracking records to ETW is defined in the diagnostics section of the Web.config file (under `<system.serviceModel><diagnostics>`).</span></span> <span data-ttu-id="1e9b6-122">默认情况下，未指定提供程序 ID 时，ETW 跟踪参与者使用默认提供程序 ID，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-122">By default, the ETW tracking participant uses a default provider ID when one has not been specified, as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 <span data-ttu-id="1e9b6-123">下图显示了通过 ETW 跟踪参与者的跟踪数据流。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-123">The following illustration shows the flow of tracking data through the ETW tracking participant.</span></span> <span data-ttu-id="1e9b6-124">跟踪数据到达 ETW 会话后，可以采用多种方法进行访问。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-124">Once the tracking data reaches the ETW session, it can be accessed in a number of ways.</span></span> <span data-ttu-id="1e9b6-125">访问这些事件最有用的方法之一是通过事件查看器，这是一个常用的 Windows 工具，用于查看来自应用程序和服务的日志和跟踪。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-125">One of the most useful ways to access these events is through Event Viewer, a common Windows tool used for viewing logs and traces from applications and services.</span></span>  
  
 ![通过 ETW 跟踪提供程序跟踪数据的流。](./media/tracking-participants/tracking-data-event-tracing-windows-provider.gif)  
  
## <a name="tracking-participant-event-data"></a><span data-ttu-id="1e9b6-127">跟踪参与者事件数据</span><span class="sxs-lookup"><span data-stu-id="1e9b6-127">Tracking Participant Event Data</span></span>  
 <span data-ttu-id="1e9b6-128">跟踪参与者将跟踪的事件数据序列化为 ETW 会话，格式为每个跟踪记录一个事件。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-128">A tracking participant serializes tracked event data to an ETW session in the format of one event per tracking record.</span></span>  <span data-ttu-id="1e9b6-129">标识事件所使用的 ID 在从 100 到 199 的范围内。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-129">An event is identified using an ID within the range of 100 through 199.</span></span> <span data-ttu-id="1e9b6-130">有关跟踪参与者发出的跟踪事件记录的定义，请参阅 [跟踪事件参考](tracking-events-reference.md) 主题。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-130">For definitions of the tracking event records emitted by a tracking participant, see the [Tracking Events Reference](tracking-events-reference.md) topic.</span></span>  
  
 <span data-ttu-id="1e9b6-131">ETW 事件的大小受到 ETW 缓冲区大小或 ETW 事件最大负载的限制，以二者中较小的值为限。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-131">The size of an ETW event is limited by the ETW buffer size, or the by the maximum payload for an ETW event, whichever value is smaller.</span></span> <span data-ttu-id="1e9b6-132">如果事件的大小超出其中任何一个 ETW 限制，则事件将被截断，其内容将以任意方式移除。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-132">If the size of the event exceeds either of these ETW limits, the event is truncated and its content removed in an arbitrary manner.</span></span> <span data-ttu-id="1e9b6-133">不可有选择性地移除变量、参数、批注和自定义数据。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-133">Variables, arguments, annotations and custom data are not selectively removed.</span></span> <span data-ttu-id="1e9b6-134">发生截断时，所有这些内容都将被截断，无论导致事件大小超出 ETW 限制的是哪个值。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-134">In the case of truncation, all of these are truncated regardless of the value that caused the event size to exceed the ETW limit.</span></span>  <span data-ttu-id="1e9b6-135">移除的数据用 `<item>..<item>` 代替。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-135">The removed data is replaced with `<item>..<item>`.</span></span>  
  
 <span data-ttu-id="1e9b6-136">变量、参数和自定义数据项中的复杂类型使用类序列化为 ETW 事件记录 <xref:System.Runtime.Serialization.NetDataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-136">Complex types in variables, arguments, and custom data items are serialized to the ETW event record using the <xref:System.Runtime.Serialization.NetDataContractSerializer> class.</span></span> <span data-ttu-id="1e9b6-137">此类在序列化的 XML 流中包括 CLR 类型的信息。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-137">This class includes CLR-type information in the serialized XML steam.</span></span>  
  
 <span data-ttu-id="1e9b6-138">由于 ETW 限制而截断负载数据可导致向同一 ETW 会话发送重复的跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-138">Truncation of payload data due to ETW limits can result in duplicate tracking records being sent to an ETW session.</span></span> <span data-ttu-id="1e9b6-139">如果多个会话在侦听事件，而且这些会话对事件有不同的负载限制，则会发生上述情况。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-139">This can occur if more than one session is listening for the events and the sessions have different payload limits for the events.</span></span>  
  
 <span data-ttu-id="1e9b6-140">对于具有较低限制的会话，可能会截断事件。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-140">For  the session with the lower limit the event may be truncated.</span></span> <span data-ttu-id="1e9b6-141">ETW 跟踪参与者不知道侦听事件的会话的数量；如果某个会话截断了一个事件，则 ETW 参与者会重新尝试发送一次该事件。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-141">The ETW tracking participant does not have any knowledge of the number of sessions listening for the events; if an event is truncated for a session then the ETW participant retries sending the event once.</span></span> <span data-ttu-id="1e9b6-142">在这种情况下，配置为可接受较大负载大小的会话将获取该事件两次（未截断的和已截断的事件）。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-142">In this case the session that is configured to accept a larger payload size will get the event twice (the non-truncated and truncated event).</span></span> <span data-ttu-id="1e9b6-143">通过将所有 ETW 会话配置为具有相同的缓冲区大小限制，即可防止重复的情况。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-143">Duplication can be prevented by configuring all the ETW sessions with same buffer size limits.</span></span>  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a><span data-ttu-id="1e9b6-144">在事件查看器中访问 ETW 跟踪参与者的跟踪数据</span><span class="sxs-lookup"><span data-stu-id="1e9b6-144">Accessing Tracking Data from an ETW Participant in the Event Viewer</span></span>  
 <span data-ttu-id="1e9b6-145">由 ETW 跟踪参与者写入 ETW 会话的事件可通过事件查看器进行访问（用于使用默认提供程序 ID 时）。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-145">Events that are written to an ETW session by the ETW tracking participant can be accessed through the Event Viewer (when using the default provider ID).</span></span> <span data-ttu-id="1e9b6-146">这可以快速查看工作流已发出的跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-146">This allows for rapidly viewing of tracking records that have been emitted by the workflow.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e9b6-147">向 ETW 会话发出的跟踪记录事件使用从 100 到 199 范围内的事件 ID。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-147">Tracking record events emitted to an ETW session use event IDs in the range of 100 through 199.</span></span>  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a><span data-ttu-id="1e9b6-148">启用在事件查看器中查看跟踪记录</span><span class="sxs-lookup"><span data-stu-id="1e9b6-148">To enable viewing the Tracking Records in Event Viewer</span></span>  
  
1. <span data-ttu-id="1e9b6-149">启动事件查看器 (EVENTVWR.EXE)</span><span class="sxs-lookup"><span data-stu-id="1e9b6-149">Start the Event Viewer (EVENTVWR.EXE)</span></span>  
  
2. <span data-ttu-id="1e9b6-150">选择 " **事件查看器、应用程序和服务日志"、"Microsoft"、"Windows"、"应用程序服务器"**。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-150">Select **Event Viewer, Applications and Services Logs, Microsoft, Windows, Application Server-Applications**.</span></span>  
  
3. <span data-ttu-id="1e9b6-151">右键单击并确保选中 **"查看、显示分析和调试日志"** 。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-151">Right-click and ensure that **View, Show Analytic and Debug logs** is selected.</span></span> <span data-ttu-id="1e9b6-152">如果未选中，请选中它以使选中标记显示在它旁边。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-152">If not, select it so the check mark appears next to it.</span></span> <span data-ttu-id="1e9b6-153">这会显示 " **分析**"、" **性能**" 和 " **调试** " 日志。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-153">This displays the **Analytic**, **Perf**, and **Debug** logs.</span></span>  
  
4. <span data-ttu-id="1e9b6-154">右键单击 **分析** 日志，然后选择 " **启用日志**"。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-154">Right-click the **Analytic** log and then select **Enable Log**.</span></span> <span data-ttu-id="1e9b6-155">该日志将存在于 %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl 文件中。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-155">The log will exist in the %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl file.</span></span>  
  
## <a name="custom-tracking-participant"></a><span data-ttu-id="1e9b6-156">自定义跟踪参与者</span><span class="sxs-lookup"><span data-stu-id="1e9b6-156">Custom Tracking Participant</span></span>  
 <span data-ttu-id="1e9b6-157">跟踪参与者 API 允许以用户提供的跟踪参与者扩展跟踪运行时，该用户提供的跟踪参与者可包括用于对工作流运行时发出的跟踪记录进行处理的自定义逻辑。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-157">The tracking participant API allows extension of the tracking runtime with a user-provided tracking participant that can include custom logic to handle tracking records emitted by the workflow runtime.</span></span> <span data-ttu-id="1e9b6-158">若要编写自定义跟踪参与者，开发人员必须对 `Track` 类实现 <xref:System.Activities.Tracking.TrackingParticipant> 方法。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-158">To write a custom tracking participant, the developer must implement the `Track` method on the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="1e9b6-159">此方法在工作流运行时发出跟踪记录时调用。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-159">This method is called when a tracking record is emitted by the workflow runtime.</span></span>  
  
 <span data-ttu-id="1e9b6-160">跟踪参与者从 <xref:System.Activities.Tracking.TrackingParticipant> 类派生。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-160">Tracking participants derive from the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="1e9b6-161">系统提供的 <xref:System.Activities.Tracking.EtwTrackingParticipant> 为每个收到的跟踪记录发出一个 Windows 事件跟踪 (ETW) 事件。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-161">The system-provided <xref:System.Activities.Tracking.EtwTrackingParticipant> emits an Event Tracking for Windows (ETW) event for each tracking record that is received.</span></span> <span data-ttu-id="1e9b6-162">若要创建自定义跟踪参与者，应创建从 <xref:System.Activities.Tracking.TrackingParticipant> 派生的类。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-162">To create a custom tracking participant, a class is created that derives from <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="1e9b6-163">若要提供基本跟踪功能，应重写 <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-163">To provide basic tracking functionality, override <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span></span> <span data-ttu-id="1e9b6-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> 在运行时发出跟踪记录时调用，并可按所需的方式进行处理。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> is called when a tracking record is sent by the runtime and can be processed in the desired manner.</span></span> <span data-ttu-id="1e9b6-165">在以下示例中，定义了自定义跟踪参与者类，该类将所有跟踪记录发到控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-165">In the following example, a custom tracking participant class is defined that emits all tracking records to the console window.</span></span> <span data-ttu-id="1e9b6-166">还可以实现一个 <xref:System.Activities.Tracking.TrackingParticipant> 对象，该对象使用其 `BeginTrack` 和 `EndTrack` 方法异步处理跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-166">You can also implement a <xref:System.Activities.Tracking.TrackingParticipant> object that processes the tracking records asynchronously using its `BeginTrack` and `EndTrack` methods</span></span>  
  
```csharp  
class ConsoleTrackingParticipant : TrackingParticipant  
{  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        if (record != null)  
        {  
            Console.WriteLine("=================================");  
            Console.WriteLine(record);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="1e9b6-167">若要使用特定跟踪参与者，应将其注册到要跟踪的工作流实例，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-167">To use a particular tracking participant, register it with the workflow instance that you want to track, as shown in the following example.</span></span>  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="1e9b6-168">在以下示例中，创建了一个由包含 <xref:System.Activities.Statements.Sequence> 活动的 <xref:System.Activities.Statements.WriteLine> 活动组成的工作流。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-168">In the following example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> activity that contains a <xref:System.Activities.Statements.WriteLine> activity is created.</span></span> <span data-ttu-id="1e9b6-169">向扩展添加 `ConsoleTrackingParticipant` 并调用工作流。</span><span class="sxs-lookup"><span data-stu-id="1e9b6-169">The `ConsoleTrackingParticipant` is added to the extensions and the workflow is invoked.</span></span>  
  
```csharp  
Activity activity= new Sequence()  
{  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "Hello World."  
        }  
    }  
};  
  
WorkflowApplication instance = new WorkflowApplication(activity);  
  
instance.Extensions.Add(new ConsoleTrackingParticipant());  
  instance.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
            {  
                Console.WriteLine("workflow instance completed, Id = " + instance.Id);  
                resetEvent.Set();  
            };  
            instance.Run();  
            Console.ReadLine();  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e9b6-170">请参阅</span><span class="sxs-lookup"><span data-stu-id="1e9b6-170">See also</span></span>

- <span data-ttu-id="1e9b6-171">[Windows Server App Fabric 监视](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1e9b6-171">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="1e9b6-172">[用 App Fabric 监视应用程序](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1e9b6-172">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
