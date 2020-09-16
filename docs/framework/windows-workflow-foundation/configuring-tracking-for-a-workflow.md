---
title: 为工作流配置跟踪
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: 098b295be00b1b8283e26e79ea14e78634fdb504
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557549"
---
# <a name="configuring-tracking-for-a-workflow"></a><span data-ttu-id="32bb0-102">为工作流配置跟踪</span><span class="sxs-lookup"><span data-stu-id="32bb0-102">Configuring Tracking for a Workflow</span></span>

<span data-ttu-id="32bb0-103">工作流可以按以下三种方法执行：</span><span class="sxs-lookup"><span data-stu-id="32bb0-103">A workflow can execute in three ways:</span></span>

- <span data-ttu-id="32bb0-104">在 <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="32bb0-104">Hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>

- <span data-ttu-id="32bb0-105">作为 <xref:System.Activities.WorkflowApplication> 执行</span><span class="sxs-lookup"><span data-stu-id="32bb0-105">Executed as a <xref:System.Activities.WorkflowApplication></span></span>

- <span data-ttu-id="32bb0-106">使用 <xref:System.Activities.WorkflowInvoker> 直接执行</span><span class="sxs-lookup"><span data-stu-id="32bb0-106">Executed directly using <xref:System.Activities.WorkflowInvoker></span></span>

<span data-ttu-id="32bb0-107">根据工作流承载选项的不同，可以通过代码或配置文件添加跟踪参与者。</span><span class="sxs-lookup"><span data-stu-id="32bb0-107">Depending on the workflow hosting option, a tracking participant can be added either through code or through a configuration file.</span></span> <span data-ttu-id="32bb0-108">本主题介绍如何通过向 <xref:System.Activities.WorkflowApplication> 和 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 添加跟踪参与者来配置跟踪，并介绍在使用 <xref:System.Activities.WorkflowInvoker> 时如何启用跟踪。</span><span class="sxs-lookup"><span data-stu-id="32bb0-108">This topic describes how tracking is configured by adding a tracking participant to a <xref:System.Activities.WorkflowApplication> and to a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, and how to enable tracking when using <xref:System.Activities.WorkflowInvoker>.</span></span>

## <a name="configuring-workflow-application-tracking"></a><span data-ttu-id="32bb0-109">配置工作流应用程序跟踪</span><span class="sxs-lookup"><span data-stu-id="32bb0-109">Configuring Workflow Application Tracking</span></span>

<span data-ttu-id="32bb0-110">工作流可以使用 <xref:System.Activities.WorkflowApplication> 类运行。</span><span class="sxs-lookup"><span data-stu-id="32bb0-110">A workflow can run using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="32bb0-111">本主题演示如何通过向 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 工作流宿主添加跟踪参与者为 <xref:System.Activities.WorkflowApplication>工作流应用程序配置跟踪。</span><span class="sxs-lookup"><span data-stu-id="32bb0-111">This topic demonstrates how tracking is configured for a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] workflow application by adding a tracking participant to the <xref:System.Activities.WorkflowApplication> workflow host.</span></span> <span data-ttu-id="32bb0-112">在这种情况下，工作流作为工作流应用程序运行。</span><span class="sxs-lookup"><span data-stu-id="32bb0-112">In this case, the workflow runs as a workflow application.</span></span> <span data-ttu-id="32bb0-113">通过代码（而不是通过配置文件）配置一个工作流应用程序，该工作流应用程序是一个使用 <xref:System.Activities.WorkflowApplication> 类的自承载的 .exe 文件。</span><span class="sxs-lookup"><span data-stu-id="32bb0-113">You configure a workflow application through code (rather than by using a configuration file), which is a self-hosted .exe file using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="32bb0-114">跟踪参与者将作为 <xref:System.Activities.WorkflowApplication> 实例的扩展添加。</span><span class="sxs-lookup"><span data-stu-id="32bb0-114">The tracking participant is added as an extension to the <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="32bb0-115">这是通过向 WorkflowApplication 实例的扩展集合添加 <xref:System.Activities.Tracking.TrackingParticipant> 来完成的。</span><span class="sxs-lookup"><span data-stu-id="32bb0-115">This is done by adding the <xref:System.Activities.Tracking.TrackingParticipant> to the extensions collection for the WorkflowApplication instance.</span></span>

<span data-ttu-id="32bb0-116">对于工作流应用程序，您可以添加 <xref:System.Activities.Tracking.EtwTrackingParticipant> 行为扩展，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="32bb0-116">For a workflow application, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension as shown in the following code.</span></span>

```csharp
LogActivity activity = new LogActivity();

WorkflowApplication instance = new WorkflowApplication(activity);
EtwTrackingParticipant trackingParticipant =
    new EtwTrackingParticipant
{

        TrackingProfile = new TrackingProfile
           {
               Name = "SampleTrackingProfile",
               ActivityDefinitionId = "ProcessOrder",
               Queries = new WorkflowInstanceQuery
               {
                  States = { "*" }
              }
          }
       };
instance.Extensions.Add(trackingParticipant);
```

### <a name="configuring-workflow-service-tracking"></a><span data-ttu-id="32bb0-117">配置工作流服务跟踪</span><span class="sxs-lookup"><span data-stu-id="32bb0-117">Configuring Workflow Service Tracking</span></span>

<span data-ttu-id="32bb0-118">在服务主机中承载工作流时，该工作流可以作为 WCF 服务公开 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 。</span><span class="sxs-lookup"><span data-stu-id="32bb0-118">A workflow can be exposed as a WCF service when hosted in the <xref:System.ServiceModel.Activities.WorkflowServiceHost> service host.</span></span> <span data-ttu-id="32bb0-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> 是基于工作流的服务的指定 .NET ServiceHost 实现。</span><span class="sxs-lookup"><span data-stu-id="32bb0-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> is a specialized .NET ServiceHost implementation for a workflow-based service.</span></span> <span data-ttu-id="32bb0-120">本节介绍如何为在 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 中运行的 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 工作流服务配置跟踪。</span><span class="sxs-lookup"><span data-stu-id="32bb0-120">This section explains how to configure tracking for a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow service running in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="32bb0-121">通过在 Web.config 文件（对于 Web 承载的服务）或 App.config 文件（对于在独立的应用程序中承载的服务，例如在控制台应用程序中承载的服务）中指定服务行为，或通过使用代码向服务宿主的 <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> 集合中添加与跟踪相关的行为，可以完成上述配置。</span><span class="sxs-lookup"><span data-stu-id="32bb0-121">It is configured through a Web.config file (for a Web-hosted service) or an App.config file (for a service hosted in a stand-alone application, such as a console application) by specifying a service behavior or through code by adding a tracking-specific behavior to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection for the service host.</span></span>

<span data-ttu-id="32bb0-122">对于中承载的工作流服务 <xref:System.ServiceModel.WorkflowServiceHost> ，可以 <xref:System.Activities.Tracking.EtwTrackingParticipant> 使用 `behavior` 配置文件中的 <> 元素添加，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="32bb0-122">For a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="32bb0-123">此外，对于 <xref:System.ServiceModel.WorkflowServiceHost> 中承载的工作流服务，你可以通过代码添加 <xref:System.Activities.Tracking.EtwTrackingParticipant> 行为扩展。</span><span class="sxs-lookup"><span data-stu-id="32bb0-123">Alternatively, for a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension through code.</span></span> <span data-ttu-id="32bb0-124">若要添加自定义跟踪参与者，请创建一个新的行为扩展并将其添加到 <xref:System.ServiceModel.ServiceHost> 中，如以下代码示例中所示。</span><span class="sxs-lookup"><span data-stu-id="32bb0-124">To add a custom tracking participant, create a new behavior extension and add it to the <xref:System.ServiceModel.ServiceHost> as shown in the following example code.</span></span>

> [!NOTE]
> <span data-ttu-id="32bb0-125">若要查看演示如何创建添加自定义跟踪参与者的自定义行为元素的示例代码，请参阅 [跟踪](./samples/tracking.md) 示例。</span><span class="sxs-lookup"><span data-stu-id="32bb0-125">If you want to view sample code that shows how to create a custom behavior element that adds a custom tracking participant, refer to the [Tracking](./samples/tracking.md) samples.</span></span>

```csharp
ServiceHost svcHost = new ServiceHost(typeof(WorkflowService), new
                                 Uri("http://localhost:8001/Sample"));
EtwTrackingBehavior trackingBehavior =
    new EtwTrackingBehavior
    {
        ProfileName = "Sample Tracking Profile"
    };
svcHost.Description.Behaviors.Add(trackingBehavior);
svcHost.Open();
```

<span data-ttu-id="32bb0-126">跟踪参与者将作为行为的扩展添加到工作流服务主机中。</span><span class="sxs-lookup"><span data-stu-id="32bb0-126">The tracking participant is added to the workflow service host as an extension to the behavior.</span></span>

<span data-ttu-id="32bb0-127">下面的这个代码示例演示如何从配置文件读取跟踪配置文件。</span><span class="sxs-lookup"><span data-stu-id="32bb0-127">This sample code below shows how to read a tracking profile from configuration file.</span></span>

```csharp
TrackingProfile GetProfile(string profileName, string displayName)
        {
            TrackingProfile trackingProfile = null;
            TrackingSection trackingSection = (TrackingSection)WebConfigurationManager.GetSection("system.serviceModel/tracking");
            if (trackingSection == null)
            {
                return null;
            }

            profileName ??= "";

            //Find the profile with the specified profile name in the list of profile found in config
            var match = from p in new List<TrackingProfile>(trackingSection.TrackingProfiles)
                        where (p.Name == profileName) && ((p.ActivityDefinitionId == displayName) || (p.ActivityDefinitionId == "*"))
                        select p;

            if (match.Count() == 0)
            {
                //return an empty profile
                trackingProfile = new TrackingProfile()
                {
                    ActivityDefinitionId = displayName
                };

            }
            else
            {
                trackingProfile = match.First();
            }

            return trackingProfile;
```

<span data-ttu-id="32bb0-128">此代码示例演示如何向工作流主机添加跟踪配置文件。</span><span class="sxs-lookup"><span data-stu-id="32bb0-128">This sample code shows how to add a tracking profile to a workflow host.</span></span>

```csharp
WorkflowServiceHost workflowServiceHost = serviceHostBase as WorkflowServiceHost;
if (null != workflowServiceHost)
{
    string workflowDisplayName = workflowServiceHost.Activity.DisplayName;
    TrackingProfile trackingProfile = GetProfile(this.profileName, workflowDisplayName);
    workflowServiceHost.WorkflowExtensions.Add(()  => new EtwTrackingParticipant {
        TrackingProfile = trackingProfile
    });
 }
```

> [!NOTE]
> <span data-ttu-id="32bb0-129">有关跟踪配置文件的详细信息，请参阅 [跟踪配置文件](tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="32bb0-129">For more information on tracking profiles, refer to [Tracking Profiles](tracking-profiles.md).</span></span>

### <a name="configuring-tracking-using-workflowinvoker"></a><span data-ttu-id="32bb0-130">配置使用 WorkflowInvoker 的跟踪</span><span class="sxs-lookup"><span data-stu-id="32bb0-130">Configuring tracking using WorkflowInvoker</span></span>

<span data-ttu-id="32bb0-131">若要对使用 <xref:System.Activities.WorkflowInvoker> 执行的工作流配置跟踪，请添加跟踪提供程序作为 <xref:System.Activities.WorkflowInvoker> 实例的扩展。</span><span class="sxs-lookup"><span data-stu-id="32bb0-131">To configure tracking for a workflow executed using <xref:System.Activities.WorkflowInvoker>, add the tracking provider as an extension to a <xref:System.Activities.WorkflowInvoker> instance.</span></span> <span data-ttu-id="32bb0-132">下面的代码示例来自 [自定义跟踪](./samples/custom-tracking.md) 示例。</span><span class="sxs-lookup"><span data-stu-id="32bb0-132">The following code example is from the [Custom Tracking](./samples/custom-tracking.md) sample.</span></span>

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a><span data-ttu-id="32bb0-133">在事件查看器中查看跟踪记录</span><span class="sxs-lookup"><span data-stu-id="32bb0-133">Viewing tracking records in Event Viewer</span></span>

<span data-ttu-id="32bb0-134">在跟踪 WF 执行时有两种特殊的事件查看器日志可供查看 - 分析日志和调试日志。</span><span class="sxs-lookup"><span data-stu-id="32bb0-134">There are two Event Viewer logs of particular interest to view when tracking WF execution - the Analytic log and the Debug log.</span></span> <span data-ttu-id="32bb0-135">两者都位于 "Microsoft&#124;Windows&#124;应用程序服务器-应用程序" 节点下。</span><span class="sxs-lookup"><span data-stu-id="32bb0-135">Both reside under the Microsoft&#124;Windows&#124;Application Server-Applications node.</span></span> <span data-ttu-id="32bb0-136">此部分内的日志包含来自单一应用程序的事件，而不包含对整个系统范围产生影响的事件。</span><span class="sxs-lookup"><span data-stu-id="32bb0-136">Logs within this section contain events from a single application rather than events that have an impact on the entire system.</span></span>

<span data-ttu-id="32bb0-137">调试跟踪事件将写入调试日志。</span><span class="sxs-lookup"><span data-stu-id="32bb0-137">Debug trace events are written to the Debug Log.</span></span> <span data-ttu-id="32bb0-138">若要收集事件查看器中的 WF 调试跟踪事件，请启用调试日志。</span><span class="sxs-lookup"><span data-stu-id="32bb0-138">To collect WF debug trace events in the Event Viewer, enable the Debug Log.</span></span>

1. <span data-ttu-id="32bb0-139">若要打开事件查看器，请单击 " **开始**"，然后单击 " **运行"。**</span><span class="sxs-lookup"><span data-stu-id="32bb0-139">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="32bb0-140">在 "运行" 对话框中，键入 `eventvwr` 。</span><span class="sxs-lookup"><span data-stu-id="32bb0-140">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="32bb0-141">在 "事件查看器" 对话框中，展开 " **应用程序和服务日志** " 节点。</span><span class="sxs-lookup"><span data-stu-id="32bb0-141">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="32bb0-142">展开 " **Microsoft**"、" **Windows**" 和 " **应用程序服务器** " 节点。</span><span class="sxs-lookup"><span data-stu-id="32bb0-142">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="32bb0-143">右键单击 "**应用程序服务器-应用程序**" 节点下的 "**调试**" 节点，然后选择 "**启用日志**"。</span><span class="sxs-lookup"><span data-stu-id="32bb0-143">Right-click the **Debug** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="32bb0-144">执行启用跟踪的应用程序以生成跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="32bb0-144">Execute your tracing-enabled application to generate tracing events.</span></span>

6. <span data-ttu-id="32bb0-145">右键单击 " **调试** " 节点，然后选择 " **刷新"。**</span><span class="sxs-lookup"><span data-stu-id="32bb0-145">Right-click the **Debug** node and select **Refresh.**</span></span> <span data-ttu-id="32bb0-146">跟踪事件应显示在中心窗格中。</span><span class="sxs-lookup"><span data-stu-id="32bb0-146">Tracing events should be visible in the center pane.</span></span>

<span data-ttu-id="32bb0-147">WF 4 提供跟踪参与者，可将跟踪记录写入 ETW（Windows 事件跟踪）会话。</span><span class="sxs-lookup"><span data-stu-id="32bb0-147">WF 4 provides a tracking participant that writes tracking records to an ETW (Event Tracing for Windows) session.</span></span> <span data-ttu-id="32bb0-148">ETW 跟踪参与者通过跟踪配置文件配置为订阅跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="32bb0-148">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="32bb0-149">当启用跟踪时，向 ETW 发出错误跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="32bb0-149">When tracking is enabled, errors tracking records are emitted to ETW.</span></span> <span data-ttu-id="32bb0-150">与 ETW 跟踪参与者发出的跟踪事件相对应的 ETW 跟踪事件（范围介于 100 到 113 之间）将写入分析日志。 </span><span class="sxs-lookup"><span data-stu-id="32bb0-150">ETW tracking events (between the range of 100-113) corresponding to the tracking events emitted by the ETW tracking participant are written to the Analytic Log.</span></span>

<span data-ttu-id="32bb0-151">若要查看跟踪记录，请按照以下步骤操作。</span><span class="sxs-lookup"><span data-stu-id="32bb0-151">To view tracking records, follow these steps.</span></span>

1. <span data-ttu-id="32bb0-152">若要打开事件查看器，请单击 " **开始**"，然后单击 " **运行"。**</span><span class="sxs-lookup"><span data-stu-id="32bb0-152">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="32bb0-153">在 "运行" 对话框中，键入 `eventvwr` 。</span><span class="sxs-lookup"><span data-stu-id="32bb0-153">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="32bb0-154">在 "事件查看器" 对话框中，展开 " **应用程序和服务日志** " 节点。</span><span class="sxs-lookup"><span data-stu-id="32bb0-154">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="32bb0-155">展开 " **Microsoft**"、" **Windows**" 和 " **应用程序服务器** " 节点。</span><span class="sxs-lookup"><span data-stu-id="32bb0-155">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="32bb0-156">右键单击 "**应用程序服务器-应用程序**" 节点下的 "**分析**" 节点，然后选择 "**启用日志**"。</span><span class="sxs-lookup"><span data-stu-id="32bb0-156">Right-click the **Analytic** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="32bb0-157">执行启用跟踪的应用程序以生成跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="32bb0-157">Execute your tracking-enabled application to generate tracking records.</span></span>

6. <span data-ttu-id="32bb0-158">右键单击 " **分析** " 节点，然后选择 " **刷新"。**</span><span class="sxs-lookup"><span data-stu-id="32bb0-158">Right-click the **Analytic** node and select **Refresh.**</span></span> <span data-ttu-id="32bb0-159">跟踪记录应会显示在中心窗格中。</span><span class="sxs-lookup"><span data-stu-id="32bb0-159">Tracking records should be visible in the center pane.</span></span>

<span data-ttu-id="32bb0-160">下图显示了事件查看器中的跟踪事件：</span><span class="sxs-lookup"><span data-stu-id="32bb0-160">The following image shows tracking events in the event viewer:</span></span>

![显示跟踪记录的事件查看器屏幕截图。](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a><span data-ttu-id="32bb0-162">注册应用程序特定的提供程序 ID</span><span class="sxs-lookup"><span data-stu-id="32bb0-162">Registering an application-specific provider ID</span></span>

<span data-ttu-id="32bb0-163">如果需要将事件写入到特定的应用程序日志中，请按照以下步骤注册新的提供程序清单。</span><span class="sxs-lookup"><span data-stu-id="32bb0-163">If events need to be written to a specific application log, follow these steps to register the new provider manifest.</span></span>

1. <span data-ttu-id="32bb0-164">在应用程序配置文件中声明提供程序 ID。</span><span class="sxs-lookup"><span data-stu-id="32bb0-164">Declare the provider ID in the application configuration file.</span></span>

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. <span data-ttu-id="32bb0-165">将清单文件从%windir%\Microsoft.NET\Framework \\ \<latest version of [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \microsoft.windows.applicationserver.applications.man 复制复制到临时位置，并将其重命名为 ApplicationServer Applications_Provider1。</span><span class="sxs-lookup"><span data-stu-id="32bb0-165">Copy the manifest file from %windir%\Microsoft.NET\Framework\\\<latest version of [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]>\Microsoft.Windows.ApplicationServer.Applications.man to a temporary location, and rename it to Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span></span>

3. <span data-ttu-id="32bb0-166">将清单文件中的 GUID 更改为新的 GUID。</span><span class="sxs-lookup"><span data-stu-id="32bb0-166">Change the GUID in the manifest file to the new GUID.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

4. <span data-ttu-id="32bb0-167">如果您不想卸载默认提供程序，请更改提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="32bb0-167">Change the provider name if you do not want to uninstall the default provider.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

5. <span data-ttu-id="32bb0-168">如果您在第一步中更改了提供程序名称，请将清单文件中的通道名称更改为新的提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="32bb0-168">If you changed the provider name in the previous step, change the channel names in the manifest file to the new provider name.</span></span>

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. <span data-ttu-id="32bb0-169">按照以下这些步骤生成资源 DLL。</span><span class="sxs-lookup"><span data-stu-id="32bb0-169">Generate the resource DLL by following these steps.</span></span>

    1. <span data-ttu-id="32bb0-170">安装 Windows SDK。</span><span class="sxs-lookup"><span data-stu-id="32bb0-170">Install the Windows SDK.</span></span> <span data-ttu-id="32bb0-171">Windows SDK 包括消息编译器 ([mc.exe](/windows/win32/wes/message-compiler--mc-exe-)) 和资源[编译器 (rc.exe) 。](/windows/win32/menurc/using-rc-the-rc-command-line-)</span><span class="sxs-lookup"><span data-stu-id="32bb0-171">The Windows SDK includes the message compiler ([mc.exe](/windows/win32/wes/message-compiler--mc-exe-)) and resource compiler ([rc.exe](/windows/win32/menurc/using-rc-the-rc-command-line-)).</span></span>

    2. <span data-ttu-id="32bb0-172">在 Windows SDK 命令提示中，对新清单文件运行 mc.exe。</span><span class="sxs-lookup"><span data-stu-id="32bb0-172">In a Windows SDK command prompt, run mc.exe on the new manifest file.</span></span>

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. <span data-ttu-id="32bb0-173">对在上一步中生成的资源文件运行 rc.exe。</span><span class="sxs-lookup"><span data-stu-id="32bb0-173">Run rc.exe on the resource file generated in the previous step.</span></span>

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. <span data-ttu-id="32bb0-174">创建一个名为 NewProviderReg.cs 的空 cs 文件。</span><span class="sxs-lookup"><span data-stu-id="32bb0-174">Create an empty cs file called NewProviderReg.cs.</span></span>

    5. <span data-ttu-id="32bb0-175">使用 C# 编译器创建一个资源 DLL。</span><span class="sxs-lookup"><span data-stu-id="32bb0-175">Create a resource DLL using the C# compiler.</span></span>

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. <span data-ttu-id="32bb0-176">将清单文件中的资源和消息 dll 名称从更改 `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` 为新的 dll 名称。</span><span class="sxs-lookup"><span data-stu-id="32bb0-176">Change the resource and message dll name in the manifest file from `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` to the new dll name.</span></span>

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" />
        ```

    7. <span data-ttu-id="32bb0-177">使用 [wevtutil](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) 注册清单。</span><span class="sxs-lookup"><span data-stu-id="32bb0-177">Use [wevtutil](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) to register the manifest.</span></span>

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a><span data-ttu-id="32bb0-178">请参阅</span><span class="sxs-lookup"><span data-stu-id="32bb0-178">See also</span></span>

- <span data-ttu-id="32bb0-179">[Windows Server App Fabric 监视](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="32bb0-179">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="32bb0-180">[用 App Fabric 监视应用程序](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="32bb0-180">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
