---
title: 有关跟踪的安全注意事项和有用提示
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 91a1b4bab3ac47f41821ad69228310c3993cf037
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555037"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a><span data-ttu-id="ab73d-102">有关跟踪的安全注意事项和有用提示</span><span class="sxs-lookup"><span data-stu-id="ab73d-102">Security Concerns and Useful Tips for Tracing</span></span>
<span data-ttu-id="ab73d-103">本主题说明防止敏感信息公开的方法以及使用 WebHost 时的有用提示。</span><span class="sxs-lookup"><span data-stu-id="ab73d-103">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a><span data-ttu-id="ab73d-104">将自定义跟踪侦听器与 WebHost 一起使用</span><span class="sxs-lookup"><span data-stu-id="ab73d-104">Using a Custom Trace Listener with WebHost</span></span>  
 <span data-ttu-id="ab73d-105">如果您正在编写自己的跟踪侦听器，则应当注意在 Web 承载的服务中，跟踪可能会丢失。</span><span class="sxs-lookup"><span data-stu-id="ab73d-105">If you are writing your own trace listener, you should be aware of the possibility that traces might be lost in the case of a Web-hosted service.</span></span> <span data-ttu-id="ab73d-106">当 WebHost 回收时，它会关闭活动进程，由一个副本进程来接替该进程。</span><span class="sxs-lookup"><span data-stu-id="ab73d-106">When WebHost recycles, it shuts down the live process while a duplicate takes over.</span></span> <span data-ttu-id="ab73d-107">但是，在一段时间内，这两个进程必须仍具有对同一资源的访问权，具体取决于侦听器类型。</span><span class="sxs-lookup"><span data-stu-id="ab73d-107">However, the two processes must still have access to the same resource for some time, which is dependent on the listener type.</span></span> <span data-ttu-id="ab73d-108">在这种情况下，`XmlWriterTraceListener` 会为第二个进程创建一个新的跟踪文件，Windows 事件跟踪会对同一会话中的多个进程进行管理并给予同一文件的访问权。</span><span class="sxs-lookup"><span data-stu-id="ab73d-108">In this case, , `XmlWriterTraceListener` creates a new trace file for the second process; while Windows event tracing manages multiple processes within the same session and gives access to the same file.</span></span> <span data-ttu-id="ab73d-109">如果您自己的侦听器无法提供类似功能，则当该文件被这两个进程锁定时，跟踪可能会丢失。</span><span class="sxs-lookup"><span data-stu-id="ab73d-109">If your own listener does not provide similar functionalities, traces can be lost when the file is locked up by the two processes.</span></span>  
  
 <span data-ttu-id="ab73d-110">您还应当注意，自定义跟踪侦听器可以在网络上发送跟踪和消息，例如发送到远程数据库。</span><span class="sxs-lookup"><span data-stu-id="ab73d-110">You should also be aware that a custom trace listener can send traces and messages on the wire, for example, to a remote database.</span></span> <span data-ttu-id="ab73d-111">作为应用程序部署人员，您应当使用适当的访问控制来配置自定义侦听器。</span><span class="sxs-lookup"><span data-stu-id="ab73d-111">As an application deployer, you should configure custom listeners with appropriate access control.</span></span> <span data-ttu-id="ab73d-112">您还应当对可以在远程位置上公开的任何个人信息应用安全控制。</span><span class="sxs-lookup"><span data-stu-id="ab73d-112">You should also apply security control on any personal information that can be exposed at the remote location.</span></span>  
  
## <a name="logging-sensitive-information"></a><span data-ttu-id="ab73d-113">记录敏感信息</span><span class="sxs-lookup"><span data-stu-id="ab73d-113">Logging Sensitive Information</span></span>  
 <span data-ttu-id="ab73d-114">当消息在范围内时，跟踪包含消息头。</span><span class="sxs-lookup"><span data-stu-id="ab73d-114">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="ab73d-115">启用跟踪后，特定于应用程序的标头中的个人信息（例如查询字符串）以及正文信息（例如信用卡号）会在日志中变为可见。</span><span class="sxs-lookup"><span data-stu-id="ab73d-115">When tracing is enabled, personal information in application-specific headers, such as, a query string; and body information, such as, a credit card number, can become visible in the logs.</span></span> <span data-ttu-id="ab73d-116">应用程序部署人员负责实施对配置和跟踪文件的访问控制。</span><span class="sxs-lookup"><span data-stu-id="ab73d-116">The application deployer is responsible for enforcing access control on the configuration and trace files.</span></span> <span data-ttu-id="ab73d-117">如果您不希望此类信息可见，应当禁用跟踪，或者如果您希望共享跟踪日志，则筛选出其中的部分数据。</span><span class="sxs-lookup"><span data-stu-id="ab73d-117">If you do not want this kind of information to be visible, you should disable tracing, or filter out part of the data if you want to share the trace logs.</span></span>  
  
 <span data-ttu-id="ab73d-118">下面的提示可帮助您避免意外公开跟踪文件的内容：</span><span class="sxs-lookup"><span data-stu-id="ab73d-118">The following tips can help you to prevent the content of a trace file from being exposed unintentionally:</span></span>  
  
- <span data-ttu-id="ab73d-119">确保在 WebHost 和自承载方案中都使用访问控制列表 (ACL) 对日志文件进行保护。</span><span class="sxs-lookup"><span data-stu-id="ab73d-119">Ensure that the log files are protected by Access Control Lists (ACL) both in WebHost and self-host scenarios.</span></span>  
  
- <span data-ttu-id="ab73d-120">选择无法使用 Web 请求轻松提供的文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="ab73d-120">Choose a file extension that cannot be easily served using a Web request.</span></span> <span data-ttu-id="ab73d-121">例如，.xml 文件扩展名不是一个安全的选择。</span><span class="sxs-lookup"><span data-stu-id="ab73d-121">For example, the .xml file extension is not a safe choice.</span></span> <span data-ttu-id="ab73d-122">可以参考 IIS 管理指南以查看可提供的扩展名的列表。</span><span class="sxs-lookup"><span data-stu-id="ab73d-122">You can check the IIS administration guide to see a list of extensions that can be served.</span></span>  
  
- <span data-ttu-id="ab73d-123">为日志文件位置指定绝对路径，该位置应当在 WebHost vroot 公共目录之外，以防止外部方使用 Web 浏览器来访问它。</span><span class="sxs-lookup"><span data-stu-id="ab73d-123">Specify an absolute path for the log file location, which should be outside of the WebHost vroot public directory to prevent it from being accessed by an external party using a Web browser.</span></span>  
  
 <span data-ttu-id="ab73d-124">默认情况下，不会在跟踪和已记录消息中记录密钥和个人身份信息 (PII)（例如用户名和密码）。</span><span class="sxs-lookup"><span data-stu-id="ab73d-124">By default, keys and personally identifiable information (PII) such as username and password are not logged in traces and logged messages.</span></span> <span data-ttu-id="ab73d-125">但是，计算机管理员可以使用 Machine.config 文件的 `enableLoggingKnownPII` 元素中的 `machineSettings` 属性来允许计算机上运行的应用程序记录已知的个人身份信息 (PII)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ab73d-125">A machine administrator, however, can use the `enableLoggingKnownPII` attribute in the `machineSettings` element of the Machine.config file to permit applications running on the machine to log known personally identifiable information (PII) as follows:</span></span>  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>
```  
  
 <span data-ttu-id="ab73d-126">应用程序部署人员然后可以使用 App.config 或 Web.config 文件中的 `logKnownPii` 属性来启用 PII 日志记录，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ab73d-126">An application deployer can then use the `logKnownPii` attribute in either the App.config or Web.config file to enable PII logging as follows:</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="true">  
        <listeners>  
                 <add name="messages"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="ab73d-127">只有当两个设置都为 `true` 时，才会启用 PII 日志记录。</span><span class="sxs-lookup"><span data-stu-id="ab73d-127">Only when both settings are `true` is PII logging enabled.</span></span> <span data-ttu-id="ab73d-128">两个开关的组合为记录每个应用程序的已知 PII 带来了很大的灵活性。</span><span class="sxs-lookup"><span data-stu-id="ab73d-128">The combination of two switches allows the flexibility to log known PII for each application.</span></span>  
  
 <span data-ttu-id="ab73d-129">您应当注意，如果在一个配置文件中指定了两个或更多自定义源，则只读取第一个源的特性，</span><span class="sxs-lookup"><span data-stu-id="ab73d-129">You should be aware that if you specify two or more custom sources in a configuration file, only the attributes of the first source are read.</span></span> <span data-ttu-id="ab73d-130">而忽略其他源的属性。</span><span class="sxs-lookup"><span data-stu-id="ab73d-130">The others are ignored.</span></span> <span data-ttu-id="ab73d-131">这意味着，对于以下 App.config 文件，即使已为第二个源显式启用了 PII 日志记录，也不会同时为这两个源记录 PII。</span><span class="sxs-lookup"><span data-stu-id="ab73d-131">This means that, for the following App.config, file, PII is not logged for both sources even though PII logging is explicitly enabled for the second source.</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="false">  
        <listeners>  
           <add name="messages"  
                type="System.Diagnostics.XmlWriterTraceListener"  
                initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
      <source name="System.ServiceModel"
         logKnownPii="true">  
         <listeners>  
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="ab73d-132">如果 `<machineSettings enableLoggingKnownPii="Boolean"/>`<xref:System.Configuration.ConfigurationErrorsException> 元素不在 Machine.config 文件中，则系统引发。</span><span class="sxs-lookup"><span data-stu-id="ab73d-132">If the `<machineSettings enableLoggingKnownPii="Boolean"/>` element exists outside the Machine.config file, the system throws a <xref:System.Configuration.ConfigurationErrorsException>.</span></span>  
  
 <span data-ttu-id="ab73d-133">只有当应用程序启动或重新启动之后，更改才有效。</span><span class="sxs-lookup"><span data-stu-id="ab73d-133">The changes are effective only when the application starts or restarts.</span></span> <span data-ttu-id="ab73d-134">在两个属性都设置为 `true` 的情况下，会在启动时记录一个事件。</span><span class="sxs-lookup"><span data-stu-id="ab73d-134">An event is logged at startup when both attributes are set to `true`.</span></span> <span data-ttu-id="ab73d-135">如果 `logKnownPii` 设置为 `true` 但 `enableLoggingKnownPii` 设置为 `false`，也会记录一个事件。</span><span class="sxs-lookup"><span data-stu-id="ab73d-135">An event is also logged if `logKnownPii` is set to `true` but `enableLoggingKnownPii` is `false`.</span></span>  
  
 <span data-ttu-id="ab73d-136">有关 PII 日志记录的详细信息，请参阅 [Pii 安全锁定](../../samples/pii-security-lockdown.md) 示例。</span><span class="sxs-lookup"><span data-stu-id="ab73d-136">For more information on PII logging, see [PII Security Lockdown](../../samples/pii-security-lockdown.md) sample.</span></span>  
  
 <span data-ttu-id="ab73d-137">计算机管理员和应用程序部署人员应谨慎使用这两个开关。</span><span class="sxs-lookup"><span data-stu-id="ab73d-137">The machine administrator and application deployer should exercise extreme caution when using these two switches.</span></span> <span data-ttu-id="ab73d-138">如果启用了 PII 日志记录，则会记录安全密钥和 PII。</span><span class="sxs-lookup"><span data-stu-id="ab73d-138">If PII logging is enabled, security keys and PII are logged.</span></span> <span data-ttu-id="ab73d-139">如果禁用了 PII 日志记录，仍会在消息头和正文中记录敏感数据和特定于应用程序的数据。</span><span class="sxs-lookup"><span data-stu-id="ab73d-139">If it is disabled, sensitive and application-specific data is still logged in message headers and bodies.</span></span> <span data-ttu-id="ab73d-140">若要深入了解隐私并保护 PII，请参阅 [用户隐私](/previous-versions/dotnet/articles/aa480490(v=msdn.10))。</span><span class="sxs-lookup"><span data-stu-id="ab73d-140">For a more thorough discussion on privacy and protecting PII from being exposed, see [User Privacy](/previous-versions/dotnet/articles/aa480490(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="ab73d-141">另外，对于面向连接的传输，每次连接时会记录一次消息发送方的 IP 地址；对于非面向连接的传输，每发送一条消息会记录一次消息发送方的 IP 地址。</span><span class="sxs-lookup"><span data-stu-id="ab73d-141">In addition, the IP address of the message sender is logged once per connection for connection-oriented transports, and once per message sent otherwise.</span></span> <span data-ttu-id="ab73d-142">这是在未经发送方同意的情况下进行的。</span><span class="sxs-lookup"><span data-stu-id="ab73d-142">This is done without the consent of the sender.</span></span> <span data-ttu-id="ab73d-143">不过，只有在“信息”或“详细”跟踪级别才会发生此日志记录，这些级别不是生产中的默认或推荐跟踪级别（现场调试时除外）。</span><span class="sxs-lookup"><span data-stu-id="ab73d-143">However, this logging only occurs at the Information or Verbose tracing levels, which are not the default or recommended tracing levels in production, except for live debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab73d-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="ab73d-144">See also</span></span>

- [<span data-ttu-id="ab73d-145">跟踪</span><span class="sxs-lookup"><span data-stu-id="ab73d-145">Tracing</span></span>](index.md)
