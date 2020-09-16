---
title: 针对 Windows 的 WCF 服务和事件跟踪
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: 38e26c369d17f4aa9ccb39d2ae649facffe65418
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552961"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="96f33-102">针对 Windows 的 WCF 服务和事件跟踪</span><span class="sxs-lookup"><span data-stu-id="96f33-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="96f33-103">此示例演示如何使用 Windows Communication Foundation (WCF) 中的分析跟踪在 Windows (ETW) 的事件跟踪中发出事件。</span><span class="sxs-lookup"><span data-stu-id="96f33-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="96f33-104">分析跟踪是在 WCF 堆栈中的关键点处发出的事件，可用于在生产环境中对 WCF 服务进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="96f33-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>

 <span data-ttu-id="96f33-105">WCF 服务中的分析跟踪是跟踪，可以在生产环境中打开，对性能的影响最小。</span><span class="sxs-lookup"><span data-stu-id="96f33-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="96f33-106">这些跟踪都以事件的形式向 ETW 会话发出。</span><span class="sxs-lookup"><span data-stu-id="96f33-106">These traces are emitted as events to an ETW session.</span></span>

 <span data-ttu-id="96f33-107">此示例包括一个基本 WCF 服务，在该服务中，事件从服务发出到事件日志，可以使用事件查看器查看。</span><span class="sxs-lookup"><span data-stu-id="96f33-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="96f33-108">还可以启动一个专用的 ETW 会话，用于侦听 WCF 服务中的事件。</span><span class="sxs-lookup"><span data-stu-id="96f33-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="96f33-109">该示例包括一个用于创建专用 ETW 会话的脚本，该会话将事件存储在可以使用事件查看器读取的二进制文件中。</span><span class="sxs-lookup"><span data-stu-id="96f33-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="96f33-110">使用此示例</span><span class="sxs-lookup"><span data-stu-id="96f33-110">To use this sample</span></span>

1. <span data-ttu-id="96f33-111">使用 Visual Studio 2012 打开 EtwAnalyticTraceSample 解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="96f33-111">Using Visual Studio 2012, open the EtwAnalyticTraceSample.sln solution file.</span></span>

2. <span data-ttu-id="96f33-112">要生成解决方案，按 Ctrl+Shift+B。</span><span class="sxs-lookup"><span data-stu-id="96f33-112">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="96f33-113">若要运行解决方案，请按 Ctrl+F5。</span><span class="sxs-lookup"><span data-stu-id="96f33-113">To run the solution, press CTRL+F5.</span></span>

     <span data-ttu-id="96f33-114">在 Web 浏览器中，单击 " **计算器**"。</span><span class="sxs-lookup"><span data-stu-id="96f33-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="96f33-115">服务的 WSDL 文档的 URI 应出现在浏览器中。</span><span class="sxs-lookup"><span data-stu-id="96f33-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="96f33-116">复制该 URI。</span><span class="sxs-lookup"><span data-stu-id="96f33-116">Copy that URI.</span></span>

     <span data-ttu-id="96f33-117">默认情况下，服务开始侦听端口1378上的请求 `http://localhost:1378/Calculator.svc` 。</span><span class="sxs-lookup"><span data-stu-id="96f33-117">By default, the service starts listening for requests on port 1378 `http://localhost:1378/Calculator.svc`.</span></span>

4. <span data-ttu-id="96f33-118"> ( # A0) 运行 WCF 测试客户端。</span><span class="sxs-lookup"><span data-stu-id="96f33-118">Run the WCF test client (WcfTestClient.exe).</span></span>

     <span data-ttu-id="96f33-119"> ( # A0) 的 WCF 测试客户端位于上 `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe` 。</span><span class="sxs-lookup"><span data-stu-id="96f33-119">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span>  <span data-ttu-id="96f33-120">默认 Visual Studio 2012 安装目录为 `C:\Program Files\Microsoft Visual Studio 10.0` 。</span><span class="sxs-lookup"><span data-stu-id="96f33-120">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>

5. <span data-ttu-id="96f33-121">在 WCF 测试客户端中，通过依次选择 " **文件**" 和 " **添加服务**" 来添加服务。</span><span class="sxs-lookup"><span data-stu-id="96f33-121">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>

     <span data-ttu-id="96f33-122">在输入框中添加终结点地址。</span><span class="sxs-lookup"><span data-stu-id="96f33-122">Add the endpoint address in the input box.</span></span> <span data-ttu-id="96f33-123">默认值为 `http://localhost:1378/Calculator.svc`。</span><span class="sxs-lookup"><span data-stu-id="96f33-123">The default is `http://localhost:1378/Calculator.svc`.</span></span>

6. <span data-ttu-id="96f33-124">打开事件查看器应用程序。</span><span class="sxs-lookup"><span data-stu-id="96f33-124">Open the Event Viewer application.</span></span>

     <span data-ttu-id="96f33-125">在调用服务之前，请启动事件查看器并确保事件日志正在侦听从 WCF 服务发出的跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="96f33-125">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>

7. <span data-ttu-id="96f33-126">从 " **开始** " 菜单中选择 " **管理工具**"，然后 **事件查看器**"。</span><span class="sxs-lookup"><span data-stu-id="96f33-126">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="96f33-127">启用 **分析** 日志和 **调试** 日志。</span><span class="sxs-lookup"><span data-stu-id="96f33-127">Enable the **Analytic** and **Debug** logs.</span></span>

8. <span data-ttu-id="96f33-128">在事件查看器的树视图中，导航到 " **事件查看器**"、" **应用程序和服务日志**"、" **Microsoft**"、" **Windows**" 和 " **应用程序服务器应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="96f33-128">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="96f33-129">右键单击 " **应用程序服务器-应用程序**"，选择 " **查看**"，然后 **显示 "分析日志和调试日志**"。</span><span class="sxs-lookup"><span data-stu-id="96f33-129">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>

     <span data-ttu-id="96f33-130">确保选中 " **显示分析和调试日志** " 选项。</span><span class="sxs-lookup"><span data-stu-id="96f33-130">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

9. <span data-ttu-id="96f33-131">启用 **分析** 日志。</span><span class="sxs-lookup"><span data-stu-id="96f33-131">Enable the **Analytic** log.</span></span>

     <span data-ttu-id="96f33-132">在事件查看器的树视图中，导航到 " **事件查看器**"、" **应用程序和服务日志**"、" **Microsoft**"、" **Windows**" 和 " **应用程序服务器应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="96f33-132">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="96f33-133">右键单击 " **分析** "，然后选择 " **启用日志**"。</span><span class="sxs-lookup"><span data-stu-id="96f33-133">Right-click **Analytic** and select **Enable Log**.</span></span>

#### <a name="to-test-the-service"></a><span data-ttu-id="96f33-134">测试服务</span><span class="sxs-lookup"><span data-stu-id="96f33-134">To test the service</span></span>

1. <span data-ttu-id="96f33-135">切换回 "WCF 测试客户端"，然后双击 `Divide` 并保留默认值，该值指定分母为0。</span><span class="sxs-lookup"><span data-stu-id="96f33-135">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>

     <span data-ttu-id="96f33-136">如果分母为 0，则服务引发错误。</span><span class="sxs-lookup"><span data-stu-id="96f33-136">If the denominator is 0, then the service throws a fault.</span></span>

2. <span data-ttu-id="96f33-137">观察从服务发出的事件。</span><span class="sxs-lookup"><span data-stu-id="96f33-137">Observe the events emitted from the service.</span></span>

     <span data-ttu-id="96f33-138">切换回事件查看器，导航到 **事件查看器**、 **应用程序和服务日志**、 **Microsoft**、 **Windows**，然后 **应用程序服务器应用程序**。</span><span class="sxs-lookup"><span data-stu-id="96f33-138">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="96f33-139">右键单击 " **分析** "，然后选择 " **刷新**"。</span><span class="sxs-lookup"><span data-stu-id="96f33-139">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="96f33-140">WCF 分析跟踪事件显示在事件查看器中。</span><span class="sxs-lookup"><span data-stu-id="96f33-140">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="96f33-141">请注意，因为服务引发了错误，所以事件查看器中会显示错误跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="96f33-141">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>

3. <span data-ttu-id="96f33-142">重复步骤 1 和 2，但是使用有效的输入。</span><span class="sxs-lookup"><span data-stu-id="96f33-142">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="96f33-143">`N2` 参数的值可以为 0 之外的任何数。</span><span class="sxs-lookup"><span data-stu-id="96f33-143">The value of the `N2` parameter can be any number other than 0.</span></span>

     <span data-ttu-id="96f33-144">刷新分析通道以查看 WCF 事件，可以看到不包含任何错误事件。</span><span class="sxs-lookup"><span data-stu-id="96f33-144">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>

 <span data-ttu-id="96f33-145">该示例演示从 WCF 服务发出的分析跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="96f33-145">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="96f33-146">清理（可选）</span><span class="sxs-lookup"><span data-stu-id="96f33-146">To cleanup (Optional)</span></span>

1. <span data-ttu-id="96f33-147">打开事件查看器。</span><span class="sxs-lookup"><span data-stu-id="96f33-147">Open Event Viewer.</span></span>

2. <span data-ttu-id="96f33-148">导航到 **事件查看器**、 **应用程序和服务日志**、 **Microsoft**、 **Windows**，然后 **应用程序服务器应用程序**。</span><span class="sxs-lookup"><span data-stu-id="96f33-148">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="96f33-149">右键单击 " **分析** "，然后选择 " **禁用日志**"。</span><span class="sxs-lookup"><span data-stu-id="96f33-149">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="96f33-150">导航到 **事件查看器**、 **应用程序和服务日志**、 **Microsoft**、 **Windows**，然后 **应用程序服务器应用程序**。</span><span class="sxs-lookup"><span data-stu-id="96f33-150">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="96f33-151">右键单击 " **分析** "，然后选择 " **清除日志**"。</span><span class="sxs-lookup"><span data-stu-id="96f33-151">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="96f33-152">选择 " **清除** " 选项可清除事件。</span><span class="sxs-lookup"><span data-stu-id="96f33-152">Choose the **Clear** option to clear the events.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96f33-153">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="96f33-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="96f33-154">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="96f33-154">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="96f33-155">如果此目录不存在，请参阅[Windows Communication Foundation (wcf) ，并 Windows Workflow Foundation (的 WF](https://www.microsoft.com/download/details.aspx?id=21459)) .NET Framework Windows Communication Foundation ([!INCLUDE[wf1](../../../../includes/wf1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96f33-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="96f33-156">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="96f33-156">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="96f33-157">请参阅</span><span class="sxs-lookup"><span data-stu-id="96f33-157">See also</span></span>

- <span data-ttu-id="96f33-158">[AppFabric 监视示例](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="96f33-158">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
