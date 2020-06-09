---
title: 配置跟踪
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: 2fbe5b48a9405c9236923ffec268683bdf570831
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579002"
---
# <a name="configuring-tracing"></a><span data-ttu-id="303a8-102">配置跟踪</span><span class="sxs-lookup"><span data-stu-id="303a8-102">Configuring Tracing</span></span>
<span data-ttu-id="303a8-103">本主题描述您可以如何启用跟踪，配置要发出跟踪的跟踪源并设置跟踪级别，设置活动跟踪和传播以支持端对端的跟踪关联，以及设置要访问跟踪的跟踪侦听器。</span><span class="sxs-lookup"><span data-stu-id="303a8-103">This topic describes how you can enable tracing, configure trace sources to emit traces and set trace levels, set activity tracing and propagation to support end-to-end trace correlation, and set trace listeners to access traces.</span></span>  
  
 <span data-ttu-id="303a8-104">有关生产或调试环境中的跟踪设置建议，请参阅[建议用于跟踪和消息日志记录的设置](recommended-settings-for-tracing-and-message-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="303a8-104">For tracing settings recommendations in production or debugging environment, refer to [Recommended Settings for Tracing and Message Logging](recommended-settings-for-tracing-and-message-logging.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="303a8-105">在 Windows 8 上，您必须以提升的权限（以管理员身份运行）运行应用程序，应用程序才能生成跟踪日志。</span><span class="sxs-lookup"><span data-stu-id="303a8-105">On Windows 8 you must run your application elevated (Run as Administrator) in order for your application to generate trace logs.</span></span>  
  
## <a name="enabling-tracing"></a><span data-ttu-id="303a8-106">启用跟踪</span><span class="sxs-lookup"><span data-stu-id="303a8-106">Enabling Tracing</span></span>  
 <span data-ttu-id="303a8-107">Windows Communication Foundation （WCF）输出用于诊断跟踪的以下数据：</span><span class="sxs-lookup"><span data-stu-id="303a8-107">Windows Communication Foundation (WCF) outputs the following data for diagnostic tracing:</span></span>  
  
- <span data-ttu-id="303a8-108">跟踪跨应用程序的所有组件的进程里程碑，如操作调用、代码异常、警告和其他重要处理事件。</span><span class="sxs-lookup"><span data-stu-id="303a8-108">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings, and other significant processing events.</span></span>  
  
- <span data-ttu-id="303a8-109">跟踪功能出现故障时发生的 Windows 错误事件。</span><span class="sxs-lookup"><span data-stu-id="303a8-109">Windows error events when the tracing feature malfunctions.</span></span> <span data-ttu-id="303a8-110">请参阅[事件日志记录](../event-logging/index.md)。</span><span class="sxs-lookup"><span data-stu-id="303a8-110">See [Event Logging](../event-logging/index.md).</span></span>  
  
 <span data-ttu-id="303a8-111">WCF 跟踪在上构建 <xref:System.Diagnostics> 。</span><span class="sxs-lookup"><span data-stu-id="303a8-111">WCF tracing is built on top of <xref:System.Diagnostics>.</span></span> <span data-ttu-id="303a8-112">若要使用跟踪，应在配置文件或代码中定义跟踪源。</span><span class="sxs-lookup"><span data-stu-id="303a8-112">To use tracing, you should define trace sources in the configuration file or in code.</span></span> <span data-ttu-id="303a8-113">WCF 为每个 WCF 程序集定义一个跟踪源。</span><span class="sxs-lookup"><span data-stu-id="303a8-113">WCF defines a trace source for each WCF assembly.</span></span> <span data-ttu-id="303a8-114">`System.ServiceModel`跟踪源是最常规的 wcf 跟踪源，用于在 wcf 通信堆栈中记录处理里程碑，从进入/离开传输到输入/离开用户代码。</span><span class="sxs-lookup"><span data-stu-id="303a8-114">The `System.ServiceModel` trace source is the most general WCF trace source, and records processing milestones across the WCF communication stack, from entering/leaving transport to entering/leaving user code.</span></span> <span data-ttu-id="303a8-115">`System.ServiceModel.MessageLogging` 跟踪源记录流过系统的所有消息。</span><span class="sxs-lookup"><span data-stu-id="303a8-115">The `System.ServiceModel.MessageLogging` trace source records all messages that flow through the system.</span></span>  
  
 <span data-ttu-id="303a8-116">默认情况下不启用跟踪。</span><span class="sxs-lookup"><span data-stu-id="303a8-116">Tracing is not enabled by default.</span></span> <span data-ttu-id="303a8-117">若要激活跟踪，必须在配置中创建跟踪侦听器并为所选跟踪源设置除 "Off" 之外的跟踪级别;否则，WCF 不会生成任何跟踪。</span><span class="sxs-lookup"><span data-stu-id="303a8-117">To activate tracing, you must create a trace listener and set a trace level other than "Off" for the selected trace source in configuration; otherwise, WCF does not generate any traces.</span></span> <span data-ttu-id="303a8-118">如果不指定侦听器，则会自动禁用跟踪。</span><span class="sxs-lookup"><span data-stu-id="303a8-118">If you do not specify a listener, tracing is automatically disabled.</span></span> <span data-ttu-id="303a8-119">如果定义侦听器，但不指定级别，则默认情况下级别将设置为“Off”，这意味着不会发出任何跟踪。</span><span class="sxs-lookup"><span data-stu-id="303a8-119">If a listener is defined, but no level is specified, the level is set to "Off" by default, which means that no trace is emitted.</span></span>  
  
 <span data-ttu-id="303a8-120">如果使用 WCF 扩展点（如自定义操作调用程序），则应发出自己的跟踪。</span><span class="sxs-lookup"><span data-stu-id="303a8-120">If you use WCF extensibility points such as custom operation invokers, you should emit your own traces.</span></span> <span data-ttu-id="303a8-121">这是因为，如果实现扩展点，WCF 就不能再在默认路径中发出标准跟踪。</span><span class="sxs-lookup"><span data-stu-id="303a8-121">This is because if you implement an extensibility point, WCF can no longer emit the standard traces in the default path.</span></span> <span data-ttu-id="303a8-122">如果未通过发出跟踪实现手动跟踪支持，则可能看不到预期跟踪。</span><span class="sxs-lookup"><span data-stu-id="303a8-122">If you do not implement manual tracing support by emitting traces, you may not see the traces you expect.</span></span>  
  
 <span data-ttu-id="303a8-123">您可以通过编辑应用程序的配置文件（web 承载的应用程序的 web.config 或自承载应用程序的 Appname .config）来配置跟踪。</span><span class="sxs-lookup"><span data-stu-id="303a8-123">You can configure tracing by editing the application's configuration file—either Web.config for Web-hosted applications, or Appname.exe.config for self-hosted applications.</span></span> <span data-ttu-id="303a8-124">下面的示例演示如何进行这样的编辑。</span><span class="sxs-lookup"><span data-stu-id="303a8-124">The following is an example of such edit.</span></span> <span data-ttu-id="303a8-125">有关这些设置的详细信息，请参阅 "将跟踪侦听器配置为使用跟踪" 部分。</span><span class="sxs-lookup"><span data-stu-id="303a8-125">For more information on these settings, see the "Configuring Trace Listeners to Consume Traces" section.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
         <source name="System.ServiceModel"
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="traceListener"
                   type="System.Diagnostics.XmlWriterTraceListener"
                   initializeData= "c:\log\Traces.svclog" />  
            </listeners>  
         </source>  
      </sources>  
   </system.diagnostics>  
</configuration>  
```  
  
> [!NOTE]
> <span data-ttu-id="303a8-126">若要在 Visual Studio 中编辑 WCF 服务项目的配置文件，请右键单击应用程序的配置文件（对于 Web 承载的应用程序为 web.config），或在**解决方案资源管理器**中为自承载的应用程序配置 Appname。</span><span class="sxs-lookup"><span data-stu-id="303a8-126">To edit the configuration file of a WCF service project in Visual Studio, right click the application's configuration file—either Web.config for Web-hosted applications, or Appname.exe.config for self-hosted application in **Solution Explorer**.</span></span> <span data-ttu-id="303a8-127">然后选择 "**编辑 WCF 配置**" 上下文菜单项。</span><span class="sxs-lookup"><span data-stu-id="303a8-127">Then choose the **Edit WCF Configuration** context menu item.</span></span> <span data-ttu-id="303a8-128">这会启动[配置编辑器工具（svcconfigeditor.exe）](../../configuration-editor-tool-svcconfigeditor-exe.md)，使你能够使用图形用户界面修改 WCF 服务的配置设置。</span><span class="sxs-lookup"><span data-stu-id="303a8-128">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../../configuration-editor-tool-svcconfigeditor-exe.md), which enables you to modify configuration settings for WCF services using a graphical user interface.</span></span>  
  
## <a name="configuring-trace-sources-to-emit-traces"></a><span data-ttu-id="303a8-129">配置要发出跟踪的跟踪源</span><span class="sxs-lookup"><span data-stu-id="303a8-129">Configuring Trace Sources to Emit Traces</span></span>  
 <span data-ttu-id="303a8-130">WCF 为每个程序集定义一个跟踪源。</span><span class="sxs-lookup"><span data-stu-id="303a8-130">WCF defines a trace source for each assembly.</span></span> <span data-ttu-id="303a8-131">在程序集中生成的跟踪由为该跟踪源定义的侦听器访问。</span><span class="sxs-lookup"><span data-stu-id="303a8-131">Traces generated within an assembly are accessed by the listeners defined for that source.</span></span> <span data-ttu-id="303a8-132">定义下列跟踪源：</span><span class="sxs-lookup"><span data-stu-id="303a8-132">The following trace sources are defined:</span></span>  
  
- <span data-ttu-id="303a8-133">System.servicemodel：记录 WCF 处理的所有阶段，只要读取配置，就会在传输中处理消息，安全处理，在用户代码中调度消息，等等。</span><span class="sxs-lookup"><span data-stu-id="303a8-133">System.ServiceModel: Logs all stages of WCF processing, whenever configuration is read, a message is processed in transport, security processing, a message is dispatched in user code, and so on.</span></span>  
  
- <span data-ttu-id="303a8-134">System.ServiceModel.MessageLogging：记录流过系统的所有消息。</span><span class="sxs-lookup"><span data-stu-id="303a8-134">System.ServiceModel.MessageLogging: Logs all messages that flow through the system.</span></span>  
  
- <span data-ttu-id="303a8-135">System.IdentityModel。</span><span class="sxs-lookup"><span data-stu-id="303a8-135">System.IdentityModel.</span></span>  
  
- <span data-ttu-id="303a8-136">System.ServiceModel.Activation。</span><span class="sxs-lookup"><span data-stu-id="303a8-136">System.ServiceModel.Activation.</span></span>  
  
- <span data-ttu-id="303a8-137">System.IO.Log：记录公用日志文件系统 (CLFS) 的 .NET Framework 接口。</span><span class="sxs-lookup"><span data-stu-id="303a8-137">System.IO.Log: Logging for the .NET Framework interface to the Common Log File System (CLFS).</span></span>  
  
- <span data-ttu-id="303a8-138">System.Runtime.Serialization：在读/写对象时进行记录。</span><span class="sxs-lookup"><span data-stu-id="303a8-138">System.Runtime.Serialization: Logs when objects are read or written.</span></span>  
  
- <span data-ttu-id="303a8-139">CardSpace。</span><span class="sxs-lookup"><span data-stu-id="303a8-139">CardSpace.</span></span>  
  
 <span data-ttu-id="303a8-140">可以将每个跟踪源配置为使用相同（共享）的侦听器，如下面的配置示例中所示。</span><span class="sxs-lookup"><span data-stu-id="303a8-140">You can configure each trace source to use the same (shared) listener, as indicated in the following configuration example.</span></span>  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel"
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="CardSpace">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IO.Log">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.Runtime.Serialization">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IdentityModel">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
        </sources>  
  
        <sharedListeners>  
            <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\log\Traces.svclog" />  
        </sharedListeners>  
    </system.diagnostics>  
</configuration>  
```  
  
 <span data-ttu-id="303a8-141">另外，还可以添加用户定义的跟踪源来发出用户代码跟踪，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="303a8-141">In addition, you can add user-defined trace sources, as demonstrated by the following example, to emit user code traces.</span></span>  
  
```xml  
<system.diagnostics>  
   <sources>  
       <source name="UserTraceSource" switchValue="Warning, ActivityTracing" >  
          <listeners>  
              <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="C:\logs\UserTraces.svclog" />  
          </listeners>  
       </source>  
   </sources>  
   <trace autoflush="true" />
</system.diagnostics>  
```  
  
 <span data-ttu-id="303a8-142">有关创建用户定义的跟踪源的详细信息，请参阅[扩展跟踪](../../samples/extending-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="303a8-142">For more information about creating user-defined trace sources, see [Extending Tracing](../../samples/extending-tracing.md).</span></span>  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a><span data-ttu-id="303a8-143">配置要使用跟踪的跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="303a8-143">Configuring Trace Listeners to Consume Traces</span></span>  
 <span data-ttu-id="303a8-144">在运行时，WCF 将跟踪数据到侦听器，这些侦听器用于处理数据。</span><span class="sxs-lookup"><span data-stu-id="303a8-144">At runtime, WCF feeds trace data to the listeners, which process the data.</span></span> <span data-ttu-id="303a8-145">WCF 为提供了多个预定义的侦听器 <xref:System.Diagnostics> ，这些侦听器在输出时使用的格式不同。</span><span class="sxs-lookup"><span data-stu-id="303a8-145">WCF provides several predefined listeners for <xref:System.Diagnostics>, which differ in the format they use for output.</span></span> <span data-ttu-id="303a8-146">您也可以添加自定义侦听器类型。</span><span class="sxs-lookup"><span data-stu-id="303a8-146">You can also add custom listener types.</span></span>  
  
 <span data-ttu-id="303a8-147">可以使用 `add` 指定要使用的跟踪侦听器的名称和类型。</span><span class="sxs-lookup"><span data-stu-id="303a8-147">You can use `add` to specify the name and type of the trace listener you want to use.</span></span> <span data-ttu-id="303a8-148">在示例配置中，将侦听器命名为 `traceListener` 并添加了标准 .NET Framework 跟踪侦听器 (`System.Diagnostics.XmlWriterTraceListener`) 作为要使用的类型。</span><span class="sxs-lookup"><span data-stu-id="303a8-148">In our example configuration, we named the Listener `traceListener` and added the standard .NET Framework trace listener (`System.Diagnostics.XmlWriterTraceListener`) as the type we want to use.</span></span> <span data-ttu-id="303a8-149">可以为每个源添加任意数目的跟踪侦听器。</span><span class="sxs-lookup"><span data-stu-id="303a8-149">You can add any number of trace listeners for each source.</span></span> <span data-ttu-id="303a8-150">如果跟踪侦听器发出对文件的跟踪，则您必须在配置文件中指定输出文件的位置和名称。</span><span class="sxs-lookup"><span data-stu-id="303a8-150">If the trace listener emits the trace to a file, you must specify the output file location and name in the configuration file.</span></span> <span data-ttu-id="303a8-151">通过将 `initializeData` 设置为该侦听器的文件名称来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="303a8-151">This is done by setting `initializeData` to the name of the file for that listener.</span></span> <span data-ttu-id="303a8-152">如果不指定文件名，则会基于所用的侦听器类型生成一个随机文件名。</span><span class="sxs-lookup"><span data-stu-id="303a8-152">If you do not specify a file name, a random file name is generated based on the listener type used.</span></span> <span data-ttu-id="303a8-153">如果使用 <xref:System.Diagnostics.XmlWriterTraceListener>，则会生成不带扩展名的文件名。</span><span class="sxs-lookup"><span data-stu-id="303a8-153">If <xref:System.Diagnostics.XmlWriterTraceListener> is used, a file name with no extension is generated.</span></span> <span data-ttu-id="303a8-154">如果实现自定义侦听器，则也可以使用此属性来接收除文件名以外的初始化数据。</span><span class="sxs-lookup"><span data-stu-id="303a8-154">If you implement a custom listener, you can also use this attribute to receive initialization data other than a filename.</span></span> <span data-ttu-id="303a8-155">例如，可以为此属性指定数据库标识符。</span><span class="sxs-lookup"><span data-stu-id="303a8-155">For example, you can specify a database identifier for this attribute.</span></span>  
  
 <span data-ttu-id="303a8-156">可以将自定义跟踪侦听器配置为在网络上发送跟踪，例如，发送到远程数据库。</span><span class="sxs-lookup"><span data-stu-id="303a8-156">You can configure a custom trace listener to send traces on the wire, for example, to a remote database.</span></span> <span data-ttu-id="303a8-157">作为应用程序部署人员，您应对远程计算机上的跟踪日志施加适当的访问控制。</span><span class="sxs-lookup"><span data-stu-id="303a8-157">As an application deployer, you should enforce proper access control on the trace logs in the remote machine.</span></span>  
  
 <span data-ttu-id="303a8-158">您也可以通过编程方式配置跟踪侦听器。</span><span class="sxs-lookup"><span data-stu-id="303a8-158">You can also configure a trace listener programmatically.</span></span> <span data-ttu-id="303a8-159">有关详细信息，请参阅[如何：创建和初始化跟踪侦听器](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md)以及[创建自定义 TraceListener](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics)。</span><span class="sxs-lookup"><span data-stu-id="303a8-159">For more information, see [How to: Create and Initialize Trace Listeners](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) and [Creating a Custom TraceListener](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="303a8-160">由于 `System.Diagnostics.XmlWriterTraceListener` 不是线程安全的，因此，跟踪源可能会在输出跟踪时以独占方式锁定资源。</span><span class="sxs-lookup"><span data-stu-id="303a8-160">Because `System.Diagnostics.XmlWriterTraceListener` is not thread-safe, the trace source may lock resources exclusively when outputting traces.</span></span> <span data-ttu-id="303a8-161">当多个线程输出对配置为使用此侦听器的跟踪源的跟踪时，可能会出现资源争用，这会致使重大的性能问题。</span><span class="sxs-lookup"><span data-stu-id="303a8-161">When many threads output traces to a trace source configured to use this listener, resource contention may occur, which results in a significant performance issue.</span></span> <span data-ttu-id="303a8-162">若要解决此问题，应实现一个线程安全的自定义侦听器。</span><span class="sxs-lookup"><span data-stu-id="303a8-162">To resolve this problem, you should implement a custom listener that is thread-safe.</span></span>  
  
## <a name="trace-level"></a><span data-ttu-id="303a8-163">跟踪级别</span><span class="sxs-lookup"><span data-stu-id="303a8-163">Trace Level</span></span>  
 <span data-ttu-id="303a8-164">跟踪级别由跟踪源的 `switchValue` 设置控制。</span><span class="sxs-lookup"><span data-stu-id="303a8-164">The tracing level is controlled by the `switchValue` setting of the trace source.</span></span> <span data-ttu-id="303a8-165">下表中描述了可用的跟踪级别。</span><span class="sxs-lookup"><span data-stu-id="303a8-165">The available tracing levels are described in the following table.</span></span>  
  
|<span data-ttu-id="303a8-166">跟踪级别</span><span class="sxs-lookup"><span data-stu-id="303a8-166">Trace Level</span></span>|<span data-ttu-id="303a8-167">被跟踪事件的特性</span><span class="sxs-lookup"><span data-stu-id="303a8-167">Nature of the Tracked Events</span></span>|<span data-ttu-id="303a8-168">被跟踪事件的内容</span><span class="sxs-lookup"><span data-stu-id="303a8-168">Content of the Tracked Events</span></span>|<span data-ttu-id="303a8-169">被跟踪事件</span><span class="sxs-lookup"><span data-stu-id="303a8-169">Tracked Events</span></span>|<span data-ttu-id="303a8-170">用户目标</span><span class="sxs-lookup"><span data-stu-id="303a8-170">User Target</span></span>|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|<span data-ttu-id="303a8-171">关</span><span class="sxs-lookup"><span data-stu-id="303a8-171">Off</span></span>|<span data-ttu-id="303a8-172">空值</span><span class="sxs-lookup"><span data-stu-id="303a8-172">N/A</span></span>|<span data-ttu-id="303a8-173">空值</span><span class="sxs-lookup"><span data-stu-id="303a8-173">N/A</span></span>|<span data-ttu-id="303a8-174">不发出任何跟踪。</span><span class="sxs-lookup"><span data-stu-id="303a8-174">No traces are emitted.</span></span>|<span data-ttu-id="303a8-175">空值</span><span class="sxs-lookup"><span data-stu-id="303a8-175">N/A</span></span>|  
|<span data-ttu-id="303a8-176">严重</span><span class="sxs-lookup"><span data-stu-id="303a8-176">Critical</span></span>|<span data-ttu-id="303a8-177">"负面" 事件：指示意外处理或错误情况的事件。</span><span class="sxs-lookup"><span data-stu-id="303a8-177">"Negative" events: events that indicate an unexpected processing or an error condition.</span></span>||<span data-ttu-id="303a8-178">将记录包括下列各项的未经处理的异常：</span><span class="sxs-lookup"><span data-stu-id="303a8-178">Unhandled exceptions including the following are logged:</span></span><br /><br /> <span data-ttu-id="303a8-179">-OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="303a8-179">-   OutOfMemoryException</span></span><br /><span data-ttu-id="303a8-180">-ThreadAbortException （CLR 调用任何 ThreadAbortExceptionHandler）</span><span class="sxs-lookup"><span data-stu-id="303a8-180">-   ThreadAbortException (the CLR invokes any ThreadAbortExceptionHandler)</span></span><br /><span data-ttu-id="303a8-181">-StackOverflowException （无法捕获）</span><span class="sxs-lookup"><span data-stu-id="303a8-181">-   StackOverflowException (cannot be caught)</span></span><br /><span data-ttu-id="303a8-182">-System.configuration.configurationerrorsexception</span><span class="sxs-lookup"><span data-stu-id="303a8-182">-   ConfigurationErrorsException</span></span><br /><span data-ttu-id="303a8-183">-SEHException</span><span class="sxs-lookup"><span data-stu-id="303a8-183">-   SEHException</span></span><br /><span data-ttu-id="303a8-184">-应用程序启动错误</span><span class="sxs-lookup"><span data-stu-id="303a8-184">-   Application start errors</span></span><br /><span data-ttu-id="303a8-185">-Failfast 事件</span><span class="sxs-lookup"><span data-stu-id="303a8-185">-   Failfast events</span></span><br /><span data-ttu-id="303a8-186">-系统挂起</span><span class="sxs-lookup"><span data-stu-id="303a8-186">-   System hangs</span></span><br /><span data-ttu-id="303a8-187">-有害消息：导致应用程序失败的消息跟踪。</span><span class="sxs-lookup"><span data-stu-id="303a8-187">-   Poison messages: message traces that cause the application to fail.</span></span>|<span data-ttu-id="303a8-188">管理员</span><span class="sxs-lookup"><span data-stu-id="303a8-188">Administrators</span></span><br /><br /> <span data-ttu-id="303a8-189">应用程序开发人员</span><span class="sxs-lookup"><span data-stu-id="303a8-189">Application developers</span></span>|  
|<span data-ttu-id="303a8-190">错误</span><span class="sxs-lookup"><span data-stu-id="303a8-190">Error</span></span>|<span data-ttu-id="303a8-191">"负面" 事件：指示意外处理或错误情况的事件。</span><span class="sxs-lookup"><span data-stu-id="303a8-191">"Negative" events: events that indicate an unexpected processing or an error condition.</span></span>|<span data-ttu-id="303a8-192">已发生意外处理。</span><span class="sxs-lookup"><span data-stu-id="303a8-192">Unexpected processing has happened.</span></span> <span data-ttu-id="303a8-193">应用程序未能执行预期的任务。</span><span class="sxs-lookup"><span data-stu-id="303a8-193">The application was not able to perform a task as expected.</span></span> <span data-ttu-id="303a8-194">然而，应用程序仍处于开启状态并在运行。</span><span class="sxs-lookup"><span data-stu-id="303a8-194">However, the application is still up and running.</span></span>|<span data-ttu-id="303a8-195">记录所有异常。</span><span class="sxs-lookup"><span data-stu-id="303a8-195">All exceptions are logged.</span></span>|<span data-ttu-id="303a8-196">管理员</span><span class="sxs-lookup"><span data-stu-id="303a8-196">Administrators</span></span><br /><br /> <span data-ttu-id="303a8-197">应用程序开发人员</span><span class="sxs-lookup"><span data-stu-id="303a8-197">Application developers</span></span>|  
|<span data-ttu-id="303a8-198">警告</span><span class="sxs-lookup"><span data-stu-id="303a8-198">Warning</span></span>|<span data-ttu-id="303a8-199">"负面" 事件：指示意外处理或错误情况的事件。</span><span class="sxs-lookup"><span data-stu-id="303a8-199">"Negative" events: events that indicate an unexpected processing or an error condition.</span></span>|<span data-ttu-id="303a8-200">可能的问题已经出现或可能出现，但是，应用程序仍在正常工作。</span><span class="sxs-lookup"><span data-stu-id="303a8-200">A possible problem has occurred or may occur, but the application still functions correctly.</span></span> <span data-ttu-id="303a8-201">不过，该应用程序可能不会继续正常工作。</span><span class="sxs-lookup"><span data-stu-id="303a8-201">However, it may not continue to work properly.</span></span>|<span data-ttu-id="303a8-202">-应用程序收到的请求数超过了限制设置允许的数目。</span><span class="sxs-lookup"><span data-stu-id="303a8-202">-   The application is receiving more requests than its throttling settings allow.</span></span><br /><span data-ttu-id="303a8-203">-接收队列接近配置的最大容量。</span><span class="sxs-lookup"><span data-stu-id="303a8-203">-   The receiving queue is near its maximum configured capacity.</span></span><br /><span data-ttu-id="303a8-204">-已超过超时。</span><span class="sxs-lookup"><span data-stu-id="303a8-204">-   Timeout has exceeded.</span></span><br /><span data-ttu-id="303a8-205">-拒绝凭据。</span><span class="sxs-lookup"><span data-stu-id="303a8-205">-   Credentials are rejected.</span></span>|<span data-ttu-id="303a8-206">管理员</span><span class="sxs-lookup"><span data-stu-id="303a8-206">Administrators</span></span><br /><br /> <span data-ttu-id="303a8-207">应用程序开发人员</span><span class="sxs-lookup"><span data-stu-id="303a8-207">Application developers</span></span>|  
|<span data-ttu-id="303a8-208">信息</span><span class="sxs-lookup"><span data-stu-id="303a8-208">Information</span></span>|<span data-ttu-id="303a8-209">"正" 事件：标记成功里程碑的事件</span><span class="sxs-lookup"><span data-stu-id="303a8-209">"Positive" events: events that mark successful milestones</span></span>|<span data-ttu-id="303a8-210">应用程序执行的重要和成功里程碑，而不考虑该应用程序是否工作正常。</span><span class="sxs-lookup"><span data-stu-id="303a8-210">Important and successful milestones of application execution, regardless of whether the application is working properly or not.</span></span>|<span data-ttu-id="303a8-211">通常，生成对监视和诊断系统状态、测量性能或执行分析十分有用的消息。</span><span class="sxs-lookup"><span data-stu-id="303a8-211">In general, messages helpful for monitoring and diagnosing system status, measuring performance or profiling are generated.</span></span> <span data-ttu-id="303a8-212">可以使用此类信息规划容量和管理性能：</span><span class="sxs-lookup"><span data-stu-id="303a8-212">You can use such information for capacity planning and performance management:</span></span><br /><br /> <span data-ttu-id="303a8-213">-创建通道。</span><span class="sxs-lookup"><span data-stu-id="303a8-213">-   Channels are created.</span></span><br /><span data-ttu-id="303a8-214">-已创建终结点侦听器。</span><span class="sxs-lookup"><span data-stu-id="303a8-214">-   Endpoint listeners are created.</span></span><br /><span data-ttu-id="303a8-215">-消息进入/离开传输。</span><span class="sxs-lookup"><span data-stu-id="303a8-215">-   Message enters/leaves transport.</span></span><br /><span data-ttu-id="303a8-216">-已检索到安全令牌。</span><span class="sxs-lookup"><span data-stu-id="303a8-216">-   Security token is retrieved.</span></span><br /><span data-ttu-id="303a8-217">-已读取配置设置。</span><span class="sxs-lookup"><span data-stu-id="303a8-217">-   Configuration setting is read.</span></span>|<span data-ttu-id="303a8-218">管理员</span><span class="sxs-lookup"><span data-stu-id="303a8-218">Administrators</span></span><br /><br /> <span data-ttu-id="303a8-219">应用程序开发人员</span><span class="sxs-lookup"><span data-stu-id="303a8-219">Application developers</span></span><br /><br /> <span data-ttu-id="303a8-220">产品开发人员。</span><span class="sxs-lookup"><span data-stu-id="303a8-220">Product developers.</span></span>|  
|<span data-ttu-id="303a8-221">“详细”</span><span class="sxs-lookup"><span data-stu-id="303a8-221">Verbose</span></span>|<span data-ttu-id="303a8-222">"正" 事件：标记成功里程碑的事件。</span><span class="sxs-lookup"><span data-stu-id="303a8-222">"Positive" events: events that mark successful milestones.</span></span>|<span data-ttu-id="303a8-223">发出用于用户代码和服务的低级别事件。</span><span class="sxs-lookup"><span data-stu-id="303a8-223">Low-level events for both user code and servicing are emitted.</span></span>|<span data-ttu-id="303a8-224">通常，可以使用此级别进行调试或应用程序优化。</span><span class="sxs-lookup"><span data-stu-id="303a8-224">In general, you can use this level for debugging or application optimization.</span></span><br /><br /> <span data-ttu-id="303a8-225">-理解的消息标头。</span><span class="sxs-lookup"><span data-stu-id="303a8-225">-   Understood message header.</span></span>|<span data-ttu-id="303a8-226">管理员</span><span class="sxs-lookup"><span data-stu-id="303a8-226">Administrators</span></span><br /><br /> <span data-ttu-id="303a8-227">应用程序开发人员</span><span class="sxs-lookup"><span data-stu-id="303a8-227">Application developers</span></span><br /><br /> <span data-ttu-id="303a8-228">产品开发人员。</span><span class="sxs-lookup"><span data-stu-id="303a8-228">Product developers.</span></span>|  
|<span data-ttu-id="303a8-229">活动跟踪</span><span class="sxs-lookup"><span data-stu-id="303a8-229">ActivityTracing</span></span>||<span data-ttu-id="303a8-230">处理活动与组件之间的流事件。</span><span class="sxs-lookup"><span data-stu-id="303a8-230">Flow events between processing activities and components.</span></span>|<span data-ttu-id="303a8-231">此级别允许管理员和开发人员关联同一应用程序域中的各应用程序：</span><span class="sxs-lookup"><span data-stu-id="303a8-231">This level allows administrators and developers to correlate applications in the same application domain:</span></span><br /><br /> <span data-ttu-id="303a8-232">-跟踪活动边界，如启动/停止。</span><span class="sxs-lookup"><span data-stu-id="303a8-232">-   Traces for activity boundaries, such as start/stop.</span></span><br /><span data-ttu-id="303a8-233">-传输跟踪。</span><span class="sxs-lookup"><span data-stu-id="303a8-233">-   Traces for transfers.</span></span>|<span data-ttu-id="303a8-234">全部</span><span class="sxs-lookup"><span data-stu-id="303a8-234">All</span></span>|  
|<span data-ttu-id="303a8-235">全部</span><span class="sxs-lookup"><span data-stu-id="303a8-235">All</span></span>||<span data-ttu-id="303a8-236">应用程序可能工作正常。</span><span class="sxs-lookup"><span data-stu-id="303a8-236">Application may function properly.</span></span> <span data-ttu-id="303a8-237">发出所有事件。</span><span class="sxs-lookup"><span data-stu-id="303a8-237">All events are emitted.</span></span>|<span data-ttu-id="303a8-238">先前的所有事件。</span><span class="sxs-lookup"><span data-stu-id="303a8-238">All previous events.</span></span>|<span data-ttu-id="303a8-239">全部</span><span class="sxs-lookup"><span data-stu-id="303a8-239">All</span></span>|  
  
 <span data-ttu-id="303a8-240">从“详细”到“严重”的级别彼此堆叠，即每个跟踪级别都包括其上除“禁用”级别以外的所有级别。</span><span class="sxs-lookup"><span data-stu-id="303a8-240">The levels from Verbose to Critical are stacked on top of each other, that is, each trace level includes all levels above it except the Off level.</span></span> <span data-ttu-id="303a8-241">例如，在“警告”级别进行侦听的侦听器会接收到“严重”、“错误”和“警告”跟踪。</span><span class="sxs-lookup"><span data-stu-id="303a8-241">For example, a listener listening at the Warning level receives Critical, Error, and Warning traces.</span></span> <span data-ttu-id="303a8-242">“全部”级别包括从“详细”到“严重”的事件以及活动跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="303a8-242">The All level includes events from Verbose to Critical and Activity tracing events.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="303a8-243">“信息”、“详细”和“ActivityTracing”级别会生成大量跟踪，这可能会对消息吞吐量产生不利影响（如果计算机上的所有可用资源均已用尽）。</span><span class="sxs-lookup"><span data-stu-id="303a8-243">The Information, Verbose, and ActivityTracing levels generate a lot of traces, which may negatively impact message throughput if you have used up all available resources on the machine.</span></span>  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a><span data-ttu-id="303a8-244">配置用于关联的活动跟踪和传播</span><span class="sxs-lookup"><span data-stu-id="303a8-244">Configuring Activity Tracing and Propagation for Correlation</span></span>  
 <span data-ttu-id="303a8-245">为 `activityTracing` 属性指定的 `switchValue` 值用于启用活动跟踪，这会在终结点内发出活动边界跟踪和传输跟踪。</span><span class="sxs-lookup"><span data-stu-id="303a8-245">The `activityTracing` value specified for the `switchValue` attribute is used to enable activity tracing, which emits traces for activity boundaries and transfers within endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="303a8-246">在 WCF 中使用某些扩展功能时，您可能会收到 <xref:System.NullReferenceException> 活动跟踪启用的时间。</span><span class="sxs-lookup"><span data-stu-id="303a8-246">When you use certain extensibility features in WCF, you might get a <xref:System.NullReferenceException> when activity tracing is enabled.</span></span> <span data-ttu-id="303a8-247">要解决此问题，请检查应用程序配置文件，并确保跟踪源的 `switchValue` 属性未设置为 `activityTracing`。</span><span class="sxs-lookup"><span data-stu-id="303a8-247">To fix this problem, check your application's configuration file and ensure that the `switchValue` attribute for your trace source is not set to `activityTracing`.</span></span>  
  
 <span data-ttu-id="303a8-248">`propagateActivity` 属性指示是否应将活动传播到参与消息交换的其他终结点。</span><span class="sxs-lookup"><span data-stu-id="303a8-248">The `propagateActivity` attribute indicates whether the activity should be propagated to other endpoints that participate in the message exchange.</span></span> <span data-ttu-id="303a8-249">将此值设置为 `true` 后，可以获取由任意两个终结点生成的跟踪文件，然后观察某一终结点上的一组跟踪是如何流向另一终结点上的一组跟踪的。</span><span class="sxs-lookup"><span data-stu-id="303a8-249">By setting this value to `true`, you can take trace files generated by any two endpoints and observe how a set of traces on one endpoint flowed to a set of traces on another endpoint.</span></span>  
  
 <span data-ttu-id="303a8-250">有关活动跟踪和传播的详细信息，请参阅[传播](propagation.md)。</span><span class="sxs-lookup"><span data-stu-id="303a8-250">For more information about activity tracing and propagation, see [Propagation](propagation.md).</span></span>  
  
 <span data-ttu-id="303a8-251">`propagateActivity`和 `ActivityTracing` 布尔值均适用于 system.servicemodel TraceSource。</span><span class="sxs-lookup"><span data-stu-id="303a8-251">Both `propagateActivity` and `ActivityTracing` Boolean values apply to the System.ServiceModel TraceSource.</span></span> <span data-ttu-id="303a8-252">`ActivityTracing`值还适用于任何跟踪源，包括 WCF 或用户定义的跟踪源。</span><span class="sxs-lookup"><span data-stu-id="303a8-252">The `ActivityTracing` value also applies to any trace source, including WCF or user-defined ones.</span></span>  
  
 <span data-ttu-id="303a8-253">不能将 `propagateActivity` 属性与用户定义的跟踪源一起使用。</span><span class="sxs-lookup"><span data-stu-id="303a8-253">You cannot use the `propagateActivity` attribute with user-defined trace sources.</span></span> <span data-ttu-id="303a8-254">对于用户代码活动 ID 传播，请确保未设置 ServiceModel `ActivityTracing`，而同时仍将 ServiceModel `propagateActivity` 属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="303a8-254">For user code activity ID propagation, make sure you do not set ServiceModel `ActivityTracing`, while still having ServiceModel `propagateActivity` attribute set to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="303a8-255">另请参阅</span><span class="sxs-lookup"><span data-stu-id="303a8-255">See also</span></span>

- [<span data-ttu-id="303a8-256">跟踪</span><span class="sxs-lookup"><span data-stu-id="303a8-256">Tracing</span></span>](index.md)
- [<span data-ttu-id="303a8-257">管理和诊断</span><span class="sxs-lookup"><span data-stu-id="303a8-257">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="303a8-258">如何：创建和初始化跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="303a8-258">How to: Create and Initialize Trace Listeners</span></span>](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md)
- [<span data-ttu-id="303a8-259">Creating a Custom TraceListener（创建自定义 TraceListener）</span><span class="sxs-lookup"><span data-stu-id="303a8-259">Creating a Custom TraceListener</span></span>](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics)
