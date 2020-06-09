---
title: 跟踪和消息日志记录
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 9af50f138a2788fc7af0ce5d07e95df49d6675cb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602643"
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="c7e6a-102">跟踪和消息日志记录</span><span class="sxs-lookup"><span data-stu-id="c7e6a-102">Tracing and Message Logging</span></span>
<span data-ttu-id="c7e6a-103">本示例演示如何启用跟踪和消息日志记录。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-103">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="c7e6a-104">使用[服务跟踪查看器工具（svctraceviewer.exe）](../service-trace-viewer-tool-svctraceviewer-exe.md)查看生成的跟踪和消息日志。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-104">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="c7e6a-105">此示例基于[入门](getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7e6a-106">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="c7e6a-107">跟踪</span><span class="sxs-lookup"><span data-stu-id="c7e6a-107">Tracing</span></span>  
 <span data-ttu-id="c7e6a-108">Windows Communication Foundation （WCF）使用在命名空间中定义的跟踪机制 <xref:System.Diagnostics> 。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-108">Windows Communication Foundation (WCF) uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="c7e6a-109">在此跟踪模型中，由应用程序实现的跟踪源生成跟踪数据。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-109">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="c7e6a-110">每个源均由名称进行标识。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-110">Each source is identified by a name.</span></span> <span data-ttu-id="c7e6a-111">跟踪使用程序会创建针对要为其检索信息的跟踪源的侦听器。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-111">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="c7e6a-112">若要接收跟踪数据，您必须创建针对该跟踪源的侦听器。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-112">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="c7e6a-113">在 WCF 中，可以通过设置服务模型跟踪源，通过将以下代码添加到服务或客户端的配置文件来完成此 `switchValue` 操作：</span><span class="sxs-lookup"><span data-stu-id="c7e6a-113">In WCF, this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 <span data-ttu-id="c7e6a-114">有关跟踪源的详细信息，请参阅[配置跟踪](../diagnostics/tracing/configuring-tracing.md)主题中的跟踪源部分。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-114">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="c7e6a-115">活动跟踪和传播</span><span class="sxs-lookup"><span data-stu-id="c7e6a-115">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="c7e6a-116">如果 `ActivityTracing` `propagateActivity` `true` 在客户端和服务的跟踪源中启用并设置为，则在 `system.ServiceModel` 处理逻辑单元（活动）内、终结点内的活动（通过活动传输）以及跨多个终结点（通过活动 ID 传播）的活动之间提供跟踪关联。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-116">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="c7e6a-117">这三种机制（活动、传输和传播）可帮助您使用服务跟踪查看器工具更快地找到错误的根本原因。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-117">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="c7e6a-118">有关详细信息，请参阅[使用服务跟踪查看器查看相关跟踪和故障排除](../diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-118">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="c7e6a-119">通过创建用户定义的活动跟踪可以扩展 ServiceModel 提供的跟踪。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-119">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="c7e6a-120">用户定义的活动跟踪允许用户创建跟踪活动，以便执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="c7e6a-120">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
- <span data-ttu-id="c7e6a-121">将跟踪分组到逻辑工作单元。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-121">Group traces into logical units of work.</span></span>  
  
- <span data-ttu-id="c7e6a-122">通过传输和传播关联活动。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-122">Correlate activities through transfers and propagation.</span></span>  
  
- <span data-ttu-id="c7e6a-123">降低 WCF 跟踪的性能成本（例如，日志文件的磁盘空间成本）。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-123">Lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="c7e6a-124">有关用户定义的活动跟踪的详细信息，请参阅[扩展跟踪](extending-tracing.md)示例。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-124">For more information about user-defined activity trace, please see the [Extending Tracing](extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="c7e6a-125">消息日志记录</span><span class="sxs-lookup"><span data-stu-id="c7e6a-125">Message Logging</span></span>  
 <span data-ttu-id="c7e6a-126">可以在任何 WCF 应用程序的客户端和服务上启用消息日志记录。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-126">Message logging can be enabled both on the client and service of any WCF application.</span></span> <span data-ttu-id="c7e6a-127">若要启动消息日志记录，必须将下面的代码添加到客户端或服务：</span><span class="sxs-lookup"><span data-stu-id="c7e6a-127">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels -->  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="c7e6a-128">记录消息时，跟踪类型取决于是在客户端还是在服务器上进行跟踪。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-128">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="c7e6a-129">例如，发送到客户端的“Add”消息将在客户端的“TransportWrite”类别下跟踪，而同一消息将在服务的“TransportRead”类别下跟踪。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-129">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="c7e6a-130">通过将下面的代码添加到客户端的 App.config 文件或服务的 Web.config 文件的 <xref:System.Diagnostics> 节，可以配置跟踪侦听器：</span><span class="sxs-lookup"><span data-stu-id="c7e6a-130">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 <span data-ttu-id="c7e6a-131">消息将以 XML 格式记录在配置文件中指定的目标目录中。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-131">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7e6a-132">如果开始时未创建日志目录，则不会创建跟踪文件。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-132">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="c7e6a-133">请确保 C:\logs\ 目录存在，或在侦听器配置中指定一个替换日志记录目录。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-133">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="c7e6a-134">有关更多信息，请参见本文档最后的初始安装说明。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-134">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="c7e6a-135">有关消息日志记录的详细信息，请参阅[配置消息日志记录](../diagnostics/configuring-message-logging.md)主题。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-135">For more information about message logging, see the [Configuring Message Logging](../diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c7e6a-136">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="c7e6a-136">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c7e6a-137">确保已对[Windows Communication Foundation 示例执行了一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c7e6a-138">运行“跟踪和消息日志记录”示例之前，创建 C:\logs\ 目录以便服务向其中写入 .svclog 文件。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-138">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="c7e6a-139">此目录的名称在配置文件中定义为要记录的跟踪和消息的路径，并可以进行更改。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-139">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="c7e6a-140">向用户授予对日志目录的网络服务写权限。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-140">Give the user Network Service write access to the logs directory.</span></span>  
  
3. <span data-ttu-id="c7e6a-141">若要生成 c #、c + + 或 Visual Basic .NET 版本的解决方案，请按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-141">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="c7e6a-142">若要以单机配置或跨计算机配置来运行示例，请按照[运行 Windows Communication Foundation 示例](running-the-samples.md)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c7e6a-143">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-143">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c7e6a-144">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="c7e6a-144">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c7e6a-145">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c7e6a-146">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="c7e6a-146">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="c7e6a-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7e6a-147">See also</span></span>

- [<span data-ttu-id="c7e6a-148">跟踪</span><span class="sxs-lookup"><span data-stu-id="c7e6a-148">Tracing</span></span>](../diagnostics/tracing/index.md)
- <span data-ttu-id="c7e6a-149">[AppFabric 监视示例](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c7e6a-149">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
