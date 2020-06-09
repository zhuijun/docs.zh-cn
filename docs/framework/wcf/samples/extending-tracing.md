---
title: 扩展跟踪
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: 59bdfeea41bac812840ffe166895050a6cd1ad2d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600511"
---
# <a name="extend-tracing"></a><span data-ttu-id="f3951-102">扩展跟踪</span><span class="sxs-lookup"><span data-stu-id="f3951-102">Extend tracing</span></span>

<span data-ttu-id="f3951-103">此示例演示如何通过在客户端和服务代码中编写用户定义的活动跟踪来扩展 Windows Communication Foundation （WCF）跟踪功能。</span><span class="sxs-lookup"><span data-stu-id="f3951-103">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="f3951-104">通过编写用户定义的活动跟踪，用户可以创建跟踪活动，并将跟踪分组为逻辑工作单元。</span><span class="sxs-lookup"><span data-stu-id="f3951-104">Writing user-defined activity traces allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="f3951-105">还可以通过传输（在同一个终结点内）和传播（在终结点之间）来关联活动。</span><span class="sxs-lookup"><span data-stu-id="f3951-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="f3951-106">在此示例中，同时为客户端和服务启用了跟踪。</span><span class="sxs-lookup"><span data-stu-id="f3951-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="f3951-107">有关如何在客户端和服务配置文件中启用跟踪的详细信息，请参阅[跟踪和消息日志记录](tracing-and-message-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="f3951-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="f3951-108">此示例基于[入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="f3951-108">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3951-109">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="f3951-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f3951-110">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="f3951-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f3951-111">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="f3951-111">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f3951-112">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="f3951-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f3951-113">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="f3951-113">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="f3951-114">跟踪和活动传播</span><span class="sxs-lookup"><span data-stu-id="f3951-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="f3951-115">用户定义的活动跟踪允许用户创建自己的跟踪活动，以便将跟踪分组为逻辑工作单元，通过传输和传播关联活动，并降低 WCF 跟踪的性能成本（例如，日志文件的磁盘空间成本）。</span><span class="sxs-lookup"><span data-stu-id="f3951-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="add-custom-sources"></a><span data-ttu-id="f3951-116">添加自定义源</span><span class="sxs-lookup"><span data-stu-id="f3951-116">Add custom sources</span></span>  
 <span data-ttu-id="f3951-117">用户定义的跟踪既可以添加到客户端代码中，又可以添加到服务代码中。</span><span class="sxs-lookup"><span data-stu-id="f3951-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="f3951-118">将跟踪源添加到客户端或服务配置文件后，可以记录这些自定义跟踪并将其显示在[服务跟踪查看器工具（svctraceviewer.exe）](../service-trace-viewer-tool-svctraceviewer-exe.md)中。</span><span class="sxs-lookup"><span data-stu-id="f3951-118">Adding trace sources to the client or service configuration files allows for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="f3951-119">下面的代码演示如何在配置文件中添加一个名为 `ServerCalculatorTraceSource` 的用户定义的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="f3951-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>
....
```  
  
### <a name="correlate-activities"></a><span data-ttu-id="f3951-120">关联活动</span><span class="sxs-lookup"><span data-stu-id="f3951-120">Correlate activities</span></span>  
 <span data-ttu-id="f3951-121">若要跨终结点直接关联活动，必须将 `propagateActivity` 跟踪源中的 `true` 属性设置为 `System.ServiceModel`。</span><span class="sxs-lookup"><span data-stu-id="f3951-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="f3951-122">此外，若要传播跟踪而无需执行 WCF 活动，则必须关闭 "一起活动跟踪"。</span><span class="sxs-lookup"><span data-stu-id="f3951-122">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="f3951-123">这可以在以下代码示例中看到。</span><span class="sxs-lookup"><span data-stu-id="f3951-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3951-124">关闭 ServiceModel 活动跟踪与将 `switchValue` 属性表示的跟踪级别设置为 off 并不一样。</span><span class="sxs-lookup"><span data-stu-id="f3951-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessen-performance-cost"></a><span data-ttu-id="f3951-125">降低性能成本</span><span class="sxs-lookup"><span data-stu-id="f3951-125">Lessen performance cost</span></span>  
 <span data-ttu-id="f3951-126">将 `ActivityTracing` 跟踪源中的 `System.ServiceModel` 设置为 off 将生成一个只包含用户定义的活动跟踪的跟踪文件，而不包含任何 ServiceModel 活动跟踪。</span><span class="sxs-lookup"><span data-stu-id="f3951-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="f3951-127">排除一起活动跟踪会导致更小的日志文件。</span><span class="sxs-lookup"><span data-stu-id="f3951-127">Excluding ServiceModel activity traces results in a much smaller log file.</span></span> <span data-ttu-id="f3951-128">但会丢失关联 WCF 处理跟踪的机会。</span><span class="sxs-lookup"><span data-stu-id="f3951-128">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="f3951-129">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="f3951-129">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f3951-130">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="f3951-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f3951-131">若要生成 C# 或 Visual Basic .NET 版本的解决方案，请按照 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="f3951-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f3951-132">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="f3951-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3951-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f3951-133">See also</span></span>

- <span data-ttu-id="f3951-134">[AppFabric 监视示例](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f3951-134">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
