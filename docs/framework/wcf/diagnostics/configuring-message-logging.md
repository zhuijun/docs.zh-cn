---
title: 配置消息日志记录
description: 了解如何配置消息日志记录，包括如何启用日志记录、日志记录级别、消息筛选器以及如何在 WCF 中配置自定义侦听器。
ms.date: 03/30/2017
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
ms.openlocfilehash: 5203f19a18e5fa6b0ed7f68e1d1de0447da41abd
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247657"
---
# <a name="configuring-message-logging"></a><span data-ttu-id="fc555-103">配置消息日志记录</span><span class="sxs-lookup"><span data-stu-id="fc555-103">Configuring Message Logging</span></span>

<span data-ttu-id="fc555-104">本主题描述如何针对不同的方案配置消息日志记录。</span><span class="sxs-lookup"><span data-stu-id="fc555-104">This topic describes how you can configure message logging for different scenarios.</span></span>

## <a name="enabling-message-logging"></a><span data-ttu-id="fc555-105">启用消息日志记录</span><span class="sxs-lookup"><span data-stu-id="fc555-105">Enabling Message Logging</span></span>

<span data-ttu-id="fc555-106">默认情况下，Windows Communication Foundation （WCF）不记录消息。</span><span class="sxs-lookup"><span data-stu-id="fc555-106">Windows Communication Foundation (WCF) does not log messages by default.</span></span> <span data-ttu-id="fc555-107">若要激活消息日志记录，必须向 `System.ServiceModel.MessageLogging` 跟踪源添加跟踪侦听器，并在配置文件中设置 `<messagelogging>` 元素的特性。</span><span class="sxs-lookup"><span data-stu-id="fc555-107">To activate message logging, you must add a trace listener to the `System.ServiceModel.MessageLogging` trace source and set attributes for the `<messagelogging>` element in the configuration file.</span></span>

<span data-ttu-id="fc555-108">下面的示例演示如何启用日志记录和指定其他选项。</span><span class="sxs-lookup"><span data-stu-id="fc555-108">The following example shows how to enable logging and specify additional options.</span></span>

```xml
<system.diagnostics>
  <sources>
    <source name="System.ServiceModel.MessageLogging">
      <listeners>
         <add name="messages"
              type="System.Diagnostics.XmlWriterTraceListener"
              initializeData="c:\logs\messages.svclog" />
        </listeners>
    </source>
  </sources>
</system.diagnostics>

<system.serviceModel>
  <diagnostics>
    <messageLogging
         logEntireMessage="true"
         logMalformedMessages="false"
         logMessagesAtServiceLevel="true"
         logMessagesAtTransportLevel="false"
         maxMessagesToLog="3000"
         maxSizeOfMessageToLog="2000"/>
  </diagnostics>
</system.serviceModel>
```

<span data-ttu-id="fc555-109">有关消息日志记录设置的详细信息，请参阅[用于跟踪和消息日志记录的推荐设置](./tracing/recommended-settings-for-tracing-and-message-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="fc555-109">For more information about message logging settings, see [Recommended Settings for Tracing and Message Logging](./tracing/recommended-settings-for-tracing-and-message-logging.md).</span></span>

<span data-ttu-id="fc555-110">可以使用 `add` 指定要使用的侦听器的名称和类型。</span><span class="sxs-lookup"><span data-stu-id="fc555-110">You can use `add` to specify the name and type of the listener you want to use.</span></span> <span data-ttu-id="fc555-111">在示例配置中，侦听器命名为“messages”，并添加了标准 .NET Framework 跟踪侦听器(`System.Diagnostics.XmlWriterTraceListener`)，作为要使用的类型。</span><span class="sxs-lookup"><span data-stu-id="fc555-111">In the example configuration, the Listener is named "messages" and adds the standard .NET Framework trace listener (`System.Diagnostics.XmlWriterTraceListener`) as the type to use.</span></span> <span data-ttu-id="fc555-112">如果使用 `System.Diagnostics.XmlWriterTraceListener`，则必须在配置文件中指定输出文件的位置和名称。</span><span class="sxs-lookup"><span data-stu-id="fc555-112">If you use `System.Diagnostics.XmlWriterTraceListener`, you must specify the output file location and name in the configuration file.</span></span> <span data-ttu-id="fc555-113">这是通过将 `initializeData` 设置为该日志文件的名称来完成的。</span><span class="sxs-lookup"><span data-stu-id="fc555-113">This is done by setting `initializeData` to the name of the log file.</span></span> <span data-ttu-id="fc555-114">否则，系统将引发异常。</span><span class="sxs-lookup"><span data-stu-id="fc555-114">Otherwise, the system throws an exception.</span></span> <span data-ttu-id="fc555-115">还可以实现能向默认文件发出日志的自定义侦听器。</span><span class="sxs-lookup"><span data-stu-id="fc555-115">You can also implement a custom listener that emits logs to a default file.</span></span>

> [!NOTE]
> <span data-ttu-id="fc555-116">因为消息日志记录访问磁盘空间，所以应限制为特定服务而写入磁盘的消息数量。</span><span class="sxs-lookup"><span data-stu-id="fc555-116">Because message logging accesses disk space, you should limit the number of messages that are written to disk for a particular service.</span></span> <span data-ttu-id="fc555-117">当达到消息限制时，会生成信息级别的跟踪，并停止所有消息日志记录活动。</span><span class="sxs-lookup"><span data-stu-id="fc555-117">When the message limit is reached, a trace at the Information level is produced and all message logging activities stop.</span></span>

<span data-ttu-id="fc555-118">日志记录的级别以及其他选项在 Logging Level and Options（日志记录的级别和选项）部分中讨论。</span><span class="sxs-lookup"><span data-stu-id="fc555-118">The logging level, as well as the additional options, are discussed in the Logging Level and Options section.</span></span>

<span data-ttu-id="fc555-119">`switchValue` 的 `source` 属性只对跟踪有效。</span><span class="sxs-lookup"><span data-stu-id="fc555-119">The `switchValue` attribute of a `source` is only valid for tracing.</span></span> <span data-ttu-id="fc555-120">如果按下面这样为 `switchValue` 跟踪源指定 `System.ServiceModel.MessageLogging` 属性，则无效。</span><span class="sxs-lookup"><span data-stu-id="fc555-120">If you specify a `switchValue` attribute for the `System.ServiceModel.MessageLogging` trace source as follows, it has no effect.</span></span>

```xml
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">
</source>
```

<span data-ttu-id="fc555-121">如果希望禁用跟踪源，应该使用 `logMessagesAtServiceLevel`, `logMalformedMessages` 以及 `logMessagesAtTransportLevel` 元素的 `messageLogging` 属性。</span><span class="sxs-lookup"><span data-stu-id="fc555-121">If you want to disable the trace source, you should use the `logMessagesAtServiceLevel`, `logMalformedMessages`, and `logMessagesAtTransportLevel` attributes of the `messageLogging` element instead.</span></span> <span data-ttu-id="fc555-122">应将所有这些属性设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="fc555-122">You should set all these attributes to `false`.</span></span> <span data-ttu-id="fc555-123">可以使用前面的代码示例中的配置文件、通过配置编辑器的 UI 接口或使用 WMI 来完成此操作。</span><span class="sxs-lookup"><span data-stu-id="fc555-123">This can be done by using the configuration file in the previous code example, through the Configuration Editor UI interface, or using WMI.</span></span> <span data-ttu-id="fc555-124">有关配置编辑器工具的详细信息，请参阅[配置编辑器工具（SvcConfigEditor.exe）](../configuration-editor-tool-svcconfigeditor-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="fc555-124">For more information about the Configuration Editor tool, see [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="fc555-125">有关 WMI 的详细信息，请参阅[使用 Windows Management Instrumentation 诊断](./wmi/index.md)。</span><span class="sxs-lookup"><span data-stu-id="fc555-125">For more information about WMI, see [Using Windows Management Instrumentation for Diagnostics](./wmi/index.md).</span></span>

## <a name="logging-levels-and-options"></a><span data-ttu-id="fc555-126">日志记录的级别和选项</span><span class="sxs-lookup"><span data-stu-id="fc555-126">Logging Levels and Options</span></span>

<span data-ttu-id="fc555-127">对于传入消息，在消息形成后、在消息到达服务级别中的用户代码之前以及在检测到格式不正确的消息时，都会立即进行日志记录。</span><span class="sxs-lookup"><span data-stu-id="fc555-127">For incoming messages, logging happens immediately after the message is formed, immediately before the message gets to user code in the service level, and when malformed messages are detected.</span></span>

<span data-ttu-id="fc555-128">对于传出消息，在消息离开用户代码之后和消息进入网络之前，都会立即进行日志记录。</span><span class="sxs-lookup"><span data-stu-id="fc555-128">For outgoing messages, logging happens immediately after the message leaves user code and immediately before the message goes on the wire.</span></span>

<span data-ttu-id="fc555-129">WCF 在两个不同的级别、服务和传输中记录消息。</span><span class="sxs-lookup"><span data-stu-id="fc555-129">WCF logs messages at two different levels, service and transport.</span></span> <span data-ttu-id="fc555-130">也记录格式不正确的消息。</span><span class="sxs-lookup"><span data-stu-id="fc555-130">Malformed messages are also logged.</span></span> <span data-ttu-id="fc555-131">这三种类别是互相独立的，可以在配置中单独激活。</span><span class="sxs-lookup"><span data-stu-id="fc555-131">The three categories are independent from each other and can be activated separately in configuration.</span></span>

<span data-ttu-id="fc555-132">可以通过设置 `logMessagesAtServiceLevel` 元素的 `logMalformedMessages`、`logMessagesAtTransportLevel` 和 `messageLogging` 属性来控制日志记录的级别。</span><span class="sxs-lookup"><span data-stu-id="fc555-132">You can control the logging level by setting the `logMessagesAtServiceLevel`, `logMalformedMessages`, and `logMessagesAtTransportLevel` attributes of the `messageLogging` element.</span></span>

### <a name="service-level"></a><span data-ttu-id="fc555-133">服务级别</span><span class="sxs-lookup"><span data-stu-id="fc555-133">Service Level</span></span>

<span data-ttu-id="fc555-134">在这个层上记录的消息是关于进入用户代码（在接收时）或离开用户代码（在发送时）的情况。</span><span class="sxs-lookup"><span data-stu-id="fc555-134">Messages logged at this layer are about to enter (on receiving) or leave (on sending) user code.</span></span> <span data-ttu-id="fc555-135">如果已定义筛选器，则仅记录与筛选器相匹配的消息。</span><span class="sxs-lookup"><span data-stu-id="fc555-135">If filters have been defined, only messages that match the filters are logged.</span></span> <span data-ttu-id="fc555-136">否则将记录服务级别上的所有消息。</span><span class="sxs-lookup"><span data-stu-id="fc555-136">Otherwise, all messages at the service level are logged.</span></span> <span data-ttu-id="fc555-137">基础结构消息（事务、对等通道和安全性）也在此级别上记录，但可靠传递消息除外。</span><span class="sxs-lookup"><span data-stu-id="fc555-137">Infrastructure messages (transactions, peer channel, and security) are also logged at this level, except for Reliable Messaging messages.</span></span> <span data-ttu-id="fc555-138">对于经过流处理的消息，则只记录标头。</span><span class="sxs-lookup"><span data-stu-id="fc555-138">On streamed messages, only the headers are logged.</span></span> <span data-ttu-id="fc555-139">此外，安全消息在此级别上按解密记录。</span><span class="sxs-lookup"><span data-stu-id="fc555-139">In addition, secure messages are logged decrypted at this level.</span></span>

### <a name="transport-level"></a><span data-ttu-id="fc555-140">“传输”级别</span><span class="sxs-lookup"><span data-stu-id="fc555-140">Transport Level</span></span>

<span data-ttu-id="fc555-141">在这个层上记录的消息已准备好进行编码以便在网络上传输，或已准备好在经过网络传输后进行解码。</span><span class="sxs-lookup"><span data-stu-id="fc555-141">Messages logged at this layer are ready to be encoded or decoded for or after transportation on the wire.</span></span> <span data-ttu-id="fc555-142">如果已定义筛选器，则仅记录与筛选器相匹配的消息。</span><span class="sxs-lookup"><span data-stu-id="fc555-142">If filters have been defined, only messages that match the filters are logged.</span></span> <span data-ttu-id="fc555-143">否则将记录传输层上的所有消息。</span><span class="sxs-lookup"><span data-stu-id="fc555-143">Otherwise, all messages at the transport layer are logged.</span></span> <span data-ttu-id="fc555-144">所有基础结构消息都在此层上记录，包括可靠传递消息。</span><span class="sxs-lookup"><span data-stu-id="fc555-144">All infrastructure messages are logged at this layer, including reliable messaging messages.</span></span> <span data-ttu-id="fc555-145">对于经过流处理的消息，则只记录标头。</span><span class="sxs-lookup"><span data-stu-id="fc555-145">On streamed messages, only the headers are logged.</span></span> <span data-ttu-id="fc555-146">此外，安全消息在此级别上按加密记录，但使用诸如 HTTPS 的安全传输时除外。</span><span class="sxs-lookup"><span data-stu-id="fc555-146">In addition, secure messages are logged as encrypted at this level, except if a secure transport such as HTTPS is used.</span></span>

### <a name="malformed-level"></a><span data-ttu-id="fc555-147">“格式不正确”级别</span><span class="sxs-lookup"><span data-stu-id="fc555-147">Malformed Level</span></span>

<span data-ttu-id="fc555-148">格式不正确的消息是指在任何处理阶段由 WCF 堆栈拒绝的消息。</span><span class="sxs-lookup"><span data-stu-id="fc555-148">Malformed messages are messages that are rejected by the WCF stack at any stage of processing.</span></span> <span data-ttu-id="fc555-149">格式错误的消息将被如实记录：已加密（如果是加密的）、带有不适当的 XML 等。</span><span class="sxs-lookup"><span data-stu-id="fc555-149">Malformed messages are logged as-is: encrypted if they are so, with non-proper XML, and so on.</span></span> <span data-ttu-id="fc555-150">`maxSizeOfMessageToLog` 定义了记录为 CDATA 的消息大小。</span><span class="sxs-lookup"><span data-stu-id="fc555-150">`maxSizeOfMessageToLog` defined the size of the message to be logged as CDATA.</span></span> <span data-ttu-id="fc555-151">默认情况下，`maxSizeOfMessageToLog` 等于 256K。</span><span class="sxs-lookup"><span data-stu-id="fc555-151">By default, `maxSizeOfMessageToLog` is equal to 256K.</span></span> <span data-ttu-id="fc555-152">有关此属性的详细信息，请参阅 "其他选项" 部分。</span><span class="sxs-lookup"><span data-stu-id="fc555-152">For more information about this attribute, see the Other Options section.</span></span>

### <a name="other-options"></a><span data-ttu-id="fc555-153">其他选项</span><span class="sxs-lookup"><span data-stu-id="fc555-153">Other Options</span></span>

<span data-ttu-id="fc555-154">除了日志记录的级别外，用户可以指定以下选项：</span><span class="sxs-lookup"><span data-stu-id="fc555-154">In addition to the logging levels, the user can specify the following options:</span></span>

- <span data-ttu-id="fc555-155">记录整个消息（`logEntireMessage` 属性）：该值指定是否记录整个消息（标头和正文）。</span><span class="sxs-lookup"><span data-stu-id="fc555-155">Log Entire Message (`logEntireMessage` attribute): This value specifies whether the entire message (message header and body) is logged.</span></span> <span data-ttu-id="fc555-156">默认值为 `false`，这意味着仅记录标头。</span><span class="sxs-lookup"><span data-stu-id="fc555-156">The default value is `false`, meaning that only the header is logged.</span></span> <span data-ttu-id="fc555-157">此设置会影响服务和传输消息日志记录级别。</span><span class="sxs-lookup"><span data-stu-id="fc555-157">This setting affects service and transport message logging levels..</span></span>

- <span data-ttu-id="fc555-158">要记录的最大消息数（`maxMessagesToLog` 属性）：该值指定要记录的最大消息数。</span><span class="sxs-lookup"><span data-stu-id="fc555-158">Max messages to log (`maxMessagesToLog` attribute): This value specifies the maximum number of messages to log.</span></span> <span data-ttu-id="fc555-159">所有的消息（服务、传输和格式不正确消息）都统计到该配额中。</span><span class="sxs-lookup"><span data-stu-id="fc555-159">All messages (service, transport, and malformed messages) are counted towards this quota.</span></span> <span data-ttu-id="fc555-160">达到配额上限时，会发出一个跟踪，并且不再记录更多的消息。</span><span class="sxs-lookup"><span data-stu-id="fc555-160">When the quota is reached, a trace is emitted and no additional message is logged.</span></span> <span data-ttu-id="fc555-161">默认值为 10000。</span><span class="sxs-lookup"><span data-stu-id="fc555-161">The default value is 10000.</span></span>

- <span data-ttu-id="fc555-162">要记录的消息的最大大小（`maxSizeOfMessageToLog` 属性）：该值指定要记录的消息的最大大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="fc555-162">Max size of message to log (`maxSizeOfMessageToLog` attribute): This value specifies the maximum size of messages to log in bytes.</span></span> <span data-ttu-id="fc555-163">超过该大小限制的消息将不作记录，也不对该消息执行任何其他活动。</span><span class="sxs-lookup"><span data-stu-id="fc555-163">Messages that exceed the size limit are not logged, and no other activity is performed for that message.</span></span> <span data-ttu-id="fc555-164">此设置会影响所有跟踪级别。</span><span class="sxs-lookup"><span data-stu-id="fc555-164">This setting affects all trace levels.</span></span> <span data-ttu-id="fc555-165">如果 ServiceModel 跟踪打开，将在第一个记录点发出警告级别的跟踪（ServiceModelSend\* 或 TransportReceive）以通知用户。</span><span class="sxs-lookup"><span data-stu-id="fc555-165">If ServiceModel tracing is on, a Warning level trace is emitted at the first logging point (ServiceModelSend\* or TransportReceive) to notify the user.</span></span> <span data-ttu-id="fc555-166">服务级别和传输级别的消息的默认值为 256K，而格式不正确消息的默认值为 4K。</span><span class="sxs-lookup"><span data-stu-id="fc555-166">The default value for service level and transport level messages is 256K, while the default value for malformed messages is 4K.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="fc555-167">计算出来与 `maxSizeOfMessageToLog` 进行比较的消息大小是序列化之前内存中的消息大小。</span><span class="sxs-lookup"><span data-stu-id="fc555-167">The message size that is computed to compare against `maxSizeOfMessageToLog` is the message size in memory before serialization.</span></span> <span data-ttu-id="fc555-168">该大小可能与正在记录的消息字符串的实际长度不同，在很多情况下比实际大小更大。</span><span class="sxs-lookup"><span data-stu-id="fc555-168">This size can differ from the actual length of the message string that is being logged, and in many occasions is bigger than the actual size.</span></span> <span data-ttu-id="fc555-169">结果可能无法记录消息。</span><span class="sxs-lookup"><span data-stu-id="fc555-169">As a result, messages may not be logged.</span></span> <span data-ttu-id="fc555-170">可以通过将 `maxSizeOfMessageToLog` 属性指定为比预期的消息大小大 10% 来解决这个问题。</span><span class="sxs-lookup"><span data-stu-id="fc555-170">You can account for this fact by specifying the `maxSizeOfMessageToLog` attribute to be 10% larger than the expected message size.</span></span> <span data-ttu-id="fc555-171">此外，如果记录了格式不正确的消息，消息日志所占用的实际磁盘空间可能达到 `maxSizeOfMessageToLog` 所指定的值的 5 倍。</span><span class="sxs-lookup"><span data-stu-id="fc555-171">In addition, if malformed messages are logged, the actual disk space utilized by the message logs can be up to 5 times the size of the value specified by `maxSizeOfMessageToLog`.</span></span>

<span data-ttu-id="fc555-172">如果在配置文件中没有定义跟踪侦听器，则不论指定什么记录级别，都不会生成记录输出。</span><span class="sxs-lookup"><span data-stu-id="fc555-172">If no trace listener is defined in the configuration file, no logging output is generated regardless of the specified logging level.</span></span>

<span data-ttu-id="fc555-173">对于消息日志记录选项（例如在本部分描述的属性），可以使用 Windows Management Instrumentation (WMI) 在运行时进行更改。</span><span class="sxs-lookup"><span data-stu-id="fc555-173">Message logging options, such as the attributes described in this section, can be changed at runtime using Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="fc555-174">这可以通过访问[AppDomainInfo](./wmi/appdomaininfo.md)实例来完成，此实例将公开以下布尔属性： `LogMessagesAtServiceLevel` 、 `LogMessagesAtTransportLevel` 和 `LogMalformedMessages` 。</span><span class="sxs-lookup"><span data-stu-id="fc555-174">This can be done by accessing the [AppDomainInfo](./wmi/appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, and `LogMalformedMessages`.</span></span> <span data-ttu-id="fc555-175">因此，如果为消息日志记录配置了跟踪侦听器，但是在配置中将这些选项设置为 `false`，那么可以在以后运行应用程序时将它们更改为 `true`。</span><span class="sxs-lookup"><span data-stu-id="fc555-175">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="fc555-176">这会在运行时有效地启用消息日志记录。</span><span class="sxs-lookup"><span data-stu-id="fc555-176">This effectively enables message logging at runtime.</span></span> <span data-ttu-id="fc555-177">同样，如果在配置文件中启用了消息日志记录，可以在运行时使用 WMI 将其禁用。</span><span class="sxs-lookup"><span data-stu-id="fc555-177">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span> <span data-ttu-id="fc555-178">有关详细信息，请参阅[使用诊断 Windows Management Instrumentation](./wmi/index.md)。</span><span class="sxs-lookup"><span data-stu-id="fc555-178">For more information, see [Using Windows Management Instrumentation for Diagnostics](./wmi/index.md).</span></span>

<span data-ttu-id="fc555-179">消息记录中的 `source` 字段指定了在何种上下文中记录消息：在发送/接收请求消息时、在进行请求-答复或单向请求时、在服务模型或传输层上或者在发现格式不正确的消息时。</span><span class="sxs-lookup"><span data-stu-id="fc555-179">The `source` field in a message log specifies in which context the message is logged: when sending/receiving a request message, for a request-reply or 1-way request, at service model or transport layer, or in the case of a malformed message.</span></span>

<span data-ttu-id="fc555-180">对于格式不正确的消息， `source` 等于 `Malformed` 。</span><span class="sxs-lookup"><span data-stu-id="fc555-180">For malformed messages, `source`  is equal to `Malformed`.</span></span> <span data-ttu-id="fc555-181">否则，根据上下文，源具有以下值。</span><span class="sxs-lookup"><span data-stu-id="fc555-181">Otherwise, source has the following values based on the context.</span></span>

<span data-ttu-id="fc555-182">对于请求/答复</span><span class="sxs-lookup"><span data-stu-id="fc555-182">For Request/Reply</span></span>

||<span data-ttu-id="fc555-183">发送请求</span><span class="sxs-lookup"><span data-stu-id="fc555-183">Send Request</span></span>|<span data-ttu-id="fc555-184">接收请求</span><span class="sxs-lookup"><span data-stu-id="fc555-184">Receive Request</span></span>|<span data-ttu-id="fc555-185">发送答复</span><span class="sxs-lookup"><span data-stu-id="fc555-185">Send Reply</span></span>|<span data-ttu-id="fc555-186">接收答复</span><span class="sxs-lookup"><span data-stu-id="fc555-186">Receive Reply</span></span>|
|-|------------------|---------------------|----------------|-------------------|
|<span data-ttu-id="fc555-187">服务模型层</span><span class="sxs-lookup"><span data-stu-id="fc555-187">Service Model layer</span></span>|<span data-ttu-id="fc555-188">服务</span><span class="sxs-lookup"><span data-stu-id="fc555-188">Service</span></span><br /><br /> <span data-ttu-id="fc555-189">Level</span><span class="sxs-lookup"><span data-stu-id="fc555-189">Level</span></span><br /><br /> <span data-ttu-id="fc555-190">Send</span><span class="sxs-lookup"><span data-stu-id="fc555-190">Send</span></span><br /><br /> <span data-ttu-id="fc555-191">请求</span><span class="sxs-lookup"><span data-stu-id="fc555-191">Request</span></span>|<span data-ttu-id="fc555-192">服务</span><span class="sxs-lookup"><span data-stu-id="fc555-192">Service</span></span><br /><br /> <span data-ttu-id="fc555-193">Level</span><span class="sxs-lookup"><span data-stu-id="fc555-193">Level</span></span><br /><br /> <span data-ttu-id="fc555-194">接收</span><span class="sxs-lookup"><span data-stu-id="fc555-194">Receive</span></span><br /><br /> <span data-ttu-id="fc555-195">请求</span><span class="sxs-lookup"><span data-stu-id="fc555-195">Request</span></span>|<span data-ttu-id="fc555-196">服务</span><span class="sxs-lookup"><span data-stu-id="fc555-196">Service</span></span><br /><br /> <span data-ttu-id="fc555-197">Level</span><span class="sxs-lookup"><span data-stu-id="fc555-197">Level</span></span><br /><br /> <span data-ttu-id="fc555-198">Send</span><span class="sxs-lookup"><span data-stu-id="fc555-198">Send</span></span><br /><br /> <span data-ttu-id="fc555-199">回复</span><span class="sxs-lookup"><span data-stu-id="fc555-199">Reply</span></span>|<span data-ttu-id="fc555-200">服务</span><span class="sxs-lookup"><span data-stu-id="fc555-200">Service</span></span><br /><br /> <span data-ttu-id="fc555-201">Level</span><span class="sxs-lookup"><span data-stu-id="fc555-201">Level</span></span><br /><br /> <span data-ttu-id="fc555-202">接收</span><span class="sxs-lookup"><span data-stu-id="fc555-202">Receive</span></span><br /><br /> <span data-ttu-id="fc555-203">回复</span><span class="sxs-lookup"><span data-stu-id="fc555-203">Reply</span></span>|
|<span data-ttu-id="fc555-204">传输层</span><span class="sxs-lookup"><span data-stu-id="fc555-204">Transport layer</span></span>|<span data-ttu-id="fc555-205">传输</span><span class="sxs-lookup"><span data-stu-id="fc555-205">Transport</span></span><br /><br /> <span data-ttu-id="fc555-206">Send</span><span class="sxs-lookup"><span data-stu-id="fc555-206">Send</span></span>|<span data-ttu-id="fc555-207">传输</span><span class="sxs-lookup"><span data-stu-id="fc555-207">Transport</span></span><br /><br /> <span data-ttu-id="fc555-208">接收</span><span class="sxs-lookup"><span data-stu-id="fc555-208">Receive</span></span>|<span data-ttu-id="fc555-209">传输</span><span class="sxs-lookup"><span data-stu-id="fc555-209">Transport</span></span><br /><br /> <span data-ttu-id="fc555-210">Send</span><span class="sxs-lookup"><span data-stu-id="fc555-210">Send</span></span>|<span data-ttu-id="fc555-211">传输</span><span class="sxs-lookup"><span data-stu-id="fc555-211">Transport</span></span><br /><br /> <span data-ttu-id="fc555-212">接收</span><span class="sxs-lookup"><span data-stu-id="fc555-212">Receive</span></span>|

<span data-ttu-id="fc555-213">对于单向请求</span><span class="sxs-lookup"><span data-stu-id="fc555-213">For One-way Request</span></span>

||<span data-ttu-id="fc555-214">发送请求</span><span class="sxs-lookup"><span data-stu-id="fc555-214">Send Request</span></span>|<span data-ttu-id="fc555-215">接收请求</span><span class="sxs-lookup"><span data-stu-id="fc555-215">Receive Request</span></span>|
|-|------------------|---------------------|
|<span data-ttu-id="fc555-216">服务模型层</span><span class="sxs-lookup"><span data-stu-id="fc555-216">Service Model layer</span></span>|<span data-ttu-id="fc555-217">服务</span><span class="sxs-lookup"><span data-stu-id="fc555-217">Service</span></span><br /><br /> <span data-ttu-id="fc555-218">Level</span><span class="sxs-lookup"><span data-stu-id="fc555-218">Level</span></span><br /><br /> <span data-ttu-id="fc555-219">Send</span><span class="sxs-lookup"><span data-stu-id="fc555-219">Send</span></span><br /><br /> <span data-ttu-id="fc555-220">数据报</span><span class="sxs-lookup"><span data-stu-id="fc555-220">Datagram</span></span>|<span data-ttu-id="fc555-221">服务</span><span class="sxs-lookup"><span data-stu-id="fc555-221">Service</span></span><br /><br /> <span data-ttu-id="fc555-222">Level</span><span class="sxs-lookup"><span data-stu-id="fc555-222">Level</span></span><br /><br /> <span data-ttu-id="fc555-223">接收</span><span class="sxs-lookup"><span data-stu-id="fc555-223">Receive</span></span><br /><br /> <span data-ttu-id="fc555-224">数据报</span><span class="sxs-lookup"><span data-stu-id="fc555-224">Datagram</span></span>|
|<span data-ttu-id="fc555-225">传输层</span><span class="sxs-lookup"><span data-stu-id="fc555-225">Transport layer</span></span>|<span data-ttu-id="fc555-226">传输</span><span class="sxs-lookup"><span data-stu-id="fc555-226">Transport</span></span><br /><br /> <span data-ttu-id="fc555-227">Send</span><span class="sxs-lookup"><span data-stu-id="fc555-227">Send</span></span>|<span data-ttu-id="fc555-228">传输</span><span class="sxs-lookup"><span data-stu-id="fc555-228">Transport</span></span><br /><br /> <span data-ttu-id="fc555-229">接收</span><span class="sxs-lookup"><span data-stu-id="fc555-229">Receive</span></span>|

## <a name="message-filters"></a><span data-ttu-id="fc555-230">消息筛选器</span><span class="sxs-lookup"><span data-stu-id="fc555-230">Message Filters</span></span>

<span data-ttu-id="fc555-231">消息筛选器在 `messageLogging` 配置节的 `diagnostics` 配置元素中定义。</span><span class="sxs-lookup"><span data-stu-id="fc555-231">Message filters are defined in the `messageLogging` configuration element of the `diagnostics` configuration section.</span></span> <span data-ttu-id="fc555-232">它们在服务和传输级别上应用。</span><span class="sxs-lookup"><span data-stu-id="fc555-232">They are applied at the service and transport level.</span></span> <span data-ttu-id="fc555-233">如果定义一个或多个筛选器，则仅记录与其中至少一个筛选器相匹配的消息。</span><span class="sxs-lookup"><span data-stu-id="fc555-233">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="fc555-234">如果未定义任何筛选器，则所有消息都可通过。</span><span class="sxs-lookup"><span data-stu-id="fc555-234">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="fc555-235">筛选器支持完整的 XPath 语法，并按照其在配置文件中出现的顺序进行应用。</span><span class="sxs-lookup"><span data-stu-id="fc555-235">Filters support the full XPath syntax and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="fc555-236">存在语法错误的筛选器会导致配置异常。</span><span class="sxs-lookup"><span data-stu-id="fc555-236">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="fc555-237">筛选器还使用 `nodeQuota` 属性提供安全功能，该属性限制 XPath DOM 中可以进行检查以便与筛选器匹配的最大节点数量。</span><span class="sxs-lookup"><span data-stu-id="fc555-237">Filters also provide a safety feature using the `nodeQuota` attribute, which limits the maximum number of nodes in the XPath DOM that can be examined to match the filter.</span></span>

<span data-ttu-id="fc555-238">下面的示例演示如何配置一个筛选器，它仅记录具有 SOAP 标头部分的消息。</span><span class="sxs-lookup"><span data-stu-id="fc555-238">The following example shows how to configure a filter that records only messages that have a SOAP header section.</span></span>

```xml
<messageLogging logEntireMessage="true"
    logMalformedMessages="true"
    logMessagesAtServiceLevel="true"
    logMessagesAtTransportLevel="true"
    maxMessagesToLog="420">
    <filters>
        <add nodeQuota="10" xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
                 /soap:Envelope/soap:Header
        </add>
     </filters>
</messageLogging>
```

<span data-ttu-id="fc555-239">筛选器不能应用于消息正文。</span><span class="sxs-lookup"><span data-stu-id="fc555-239">Filters cannot be applied to the body of a message.</span></span> <span data-ttu-id="fc555-240">尝试对消息正文进行操作的筛选器会从筛选器列表中删除。</span><span class="sxs-lookup"><span data-stu-id="fc555-240">Filters that attempt to manipulate the body of a message are removed from the list of filters.</span></span> <span data-ttu-id="fc555-241">此外还会发出一个指示此事的事件。</span><span class="sxs-lookup"><span data-stu-id="fc555-241">An event is also emitted that indicates this.</span></span> <span data-ttu-id="fc555-242">例如，下面的筛选器会从筛选器表中删除。</span><span class="sxs-lookup"><span data-stu-id="fc555-242">For example, the following filter would be removed from the filter table.</span></span>

```xml
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>
```

## <a name="configuring-a-custom-listener"></a><span data-ttu-id="fc555-243">配置自定义侦听器</span><span class="sxs-lookup"><span data-stu-id="fc555-243">Configuring a Custom Listener</span></span>

<span data-ttu-id="fc555-244">您还可以配置具有其他选项的自定义侦听器。</span><span class="sxs-lookup"><span data-stu-id="fc555-244">You can also configure a custom listener with additional options.</span></span> <span data-ttu-id="fc555-245">若要在记录之前将特定于应用程序的 PII 元素从消息中筛选出来，自定义侦听器可能很有用。</span><span class="sxs-lookup"><span data-stu-id="fc555-245">A custom listener can be useful in filtering application-specific PII elements from messages before logging.</span></span> <span data-ttu-id="fc555-246">下面的示例演示自定义侦听器配置。</span><span class="sxs-lookup"><span data-stu-id="fc555-246">The following example demonstrates a custom listener configuration.</span></span>

```xml
<system.diagnostics>
   <sources>
     <source name="System.ServiceModel.MessageLogging">
           <listeners>
             <add name="MyListener"
                    type="YourCustomListener"
                    initializeData="c:\logs\messages.svclog"
                    maxDiskSpace="1000"/>
           </listeners>
     </source>
   </sources>
</system.diagnostics>
```

<span data-ttu-id="fc555-247">请您注意，`type` 属性应该设置为该类型的限定程序集名称。</span><span class="sxs-lookup"><span data-stu-id="fc555-247">You should be aware that the `type` attribute should be set to a qualified assembly name of the type.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc555-248">请参阅</span><span class="sxs-lookup"><span data-stu-id="fc555-248">See also</span></span>

- [\<messageLogging>](../../configure-apps/file-schema/wcf/messagelogging.md)
- [<span data-ttu-id="fc555-249">消息日志记录</span><span class="sxs-lookup"><span data-stu-id="fc555-249">Message Logging</span></span>](message-logging.md)
- [<span data-ttu-id="fc555-250">跟踪和消息日志记录的推荐设置</span><span class="sxs-lookup"><span data-stu-id="fc555-250">Recommended Settings for Tracing and Message Logging</span></span>](./tracing/recommended-settings-for-tracing-and-message-logging.md)
