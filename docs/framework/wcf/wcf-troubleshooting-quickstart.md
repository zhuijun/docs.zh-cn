---
title: WCF 疑难解答快速入门
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], troubleshooting
- Windows Communication Foundation [WCF], troubleshooting
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
ms.openlocfilehash: 42cbcf4bcc7ad5c9725b657d5fdadb2cdbd9aacb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545038"
---
# <a name="wcf-troubleshooting-quickstart"></a><span data-ttu-id="258c0-102">WCF 疑难解答快速入门</span><span class="sxs-lookup"><span data-stu-id="258c0-102">WCF Troubleshooting Quickstart</span></span>
<span data-ttu-id="258c0-103">本主题列出了一些客户开发 WCF 客户端和服务时所遇到的已知问题。</span><span class="sxs-lookup"><span data-stu-id="258c0-103">This topic lists a number of known issues customers have run into while developing WCF clients and services.</span></span> <span data-ttu-id="258c0-104">如果您遇到的问题不在此列表中，我们建议您为您的服务配置跟踪。</span><span class="sxs-lookup"><span data-stu-id="258c0-104">If the issue you are running into is not in this list, we recommend you configure tracing for your service.</span></span> <span data-ttu-id="258c0-105">这将生成一个跟踪文件，您可以使用跟踪文件查看器查看它并获取有关服务中可能发生的异常的详细信息。</span><span class="sxs-lookup"><span data-stu-id="258c0-105">This will generate a trace file that you can view with the trace file viewer and get detailed information about exceptions that may be occurring within the service.</span></span> <span data-ttu-id="258c0-106">有关配置跟踪的详细信息，请参阅： [Configuring Tracing](./diagnostics/tracing/configuring-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="258c0-106">For more information on configuring tracing, see: [Configuring Tracing](./diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="258c0-107">有关跟踪文件查看器的详细信息，请参阅： [Service Trace Viewer Tool (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="258c0-107">For more information on the trace file viewer, see: [Service Trace Viewer Tool (SvcTraceViewer.exe)](service-trace-viewer-tool-svctraceviewer-exe.md).</span></span>  
  
1. [<span data-ttu-id="258c0-108">在安装 Windows 7 和 IIS 后，当我尝试浏览到 WCF 服务时，收到以下错误消息：HTTP 错误 404.3 – 找不到</span><span class="sxs-lookup"><span data-stu-id="258c0-108">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>](#bkmk_0)  
  
     <span data-ttu-id="258c0-109">HTTP 错误 404.3 – 找不到：由于扩展配置，无法提供您请求的页面。</span><span class="sxs-lookup"><span data-stu-id="258c0-109">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="258c0-110">如果此页是脚本，请添加处理程序。</span><span class="sxs-lookup"><span data-stu-id="258c0-110">If the page is a script, add a handler.</span></span> <span data-ttu-id="258c0-111">如果应下载文件，请添加 MIME 映射。</span><span class="sxs-lookup"><span data-stu-id="258c0-111">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="258c0-112">详细错误 InformationModule StaticFileModule。</span><span class="sxs-lookup"><span data-stu-id="258c0-112">Detailed Error InformationModule StaticFileModule.</span></span>  
  
2. [<span data-ttu-id="258c0-113">如果客户端在第一次请求之后空闲一段时间，则在第二次请求时，会收到 MessageSecurityException。发生了什么事情？</span><span class="sxs-lookup"><span data-stu-id="258c0-113">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request. What is happening?</span></span>](#BKMK_q1)  
  
3. [<span data-ttu-id="258c0-114">在大约10个客户端与客户端交互后，我的服务开始拒绝新的客户端。发生了什么事情？</span><span class="sxs-lookup"><span data-stu-id="258c0-114">My service starts to reject new clients after about 10 clients are interacting with it. What is happening?</span></span>](#BKMK_q2)  
  
4. [<span data-ttu-id="258c0-115">我是否可以从 WCF 应用程序的配置文件以外的某处加载我的服务配置？</span><span class="sxs-lookup"><span data-stu-id="258c0-115">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>](#BKMK_q3)  
  
5. [<span data-ttu-id="258c0-116">我的服务和客户端工作得很好，但当客户端在另一台计算机上时，我无法使其正常工作？发生了什么事情？</span><span class="sxs-lookup"><span data-stu-id="258c0-116">My service and client work great, but I can’t get them to work when the client is on another computer? What’s happening?</span></span>](#BKMK_q4)  
  
6. [<span data-ttu-id="258c0-117">当我引发 \<Exception> 类型为异常的 FaultException 时，始终会在客户端上收到常规 FaultException 类型，而不是泛型类型。发生了什么事情？</span><span class="sxs-lookup"><span data-stu-id="258c0-117">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type. What’s happening?</span></span>](#BKMK_q5)  
  
7. [<span data-ttu-id="258c0-118">当回复不包含任何数据时，与单向和请求-答复操作的返回速度几乎相同。发生了什么事情？</span><span class="sxs-lookup"><span data-stu-id="258c0-118">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data. What's happening?</span></span>](#BKMK_q6)  
  
8. [<span data-ttu-id="258c0-119">我将 x.509 证书与我的服务一起使用，并获得 System.security.cryptography.cryptographicexception。发生了什么事情？</span><span class="sxs-lookup"><span data-stu-id="258c0-119">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException. What’s happening?</span></span>](#BKMK_q77)  
  
9. [<span data-ttu-id="258c0-120">我将操作的第一个参数从大写改为小写;现在我的客户端引发异常。发生了什么事情？</span><span class="sxs-lookup"><span data-stu-id="258c0-120">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception. What's happening?</span></span>](#BKMK_q88)  
  
10. [<span data-ttu-id="258c0-121">我使用的是我的跟踪工具之一，并获得 System.servicemodel.endpointnotfoundexception。发生了什么事情？</span><span class="sxs-lookup"><span data-stu-id="258c0-121">I’m using one of my tracing tools and I get an EndpointNotFoundException. What’s happening?</span></span>](#BKMK_q99)  
  
11. [<span data-ttu-id="258c0-122">从 WCF SOAP 应用程序调用 WCF Web HTTP 应用程序时，服务返回以下错误：405 不允许的方法</span><span class="sxs-lookup"><span data-stu-id="258c0-122">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>](#BK_MK99)  
  
 [<span data-ttu-id="258c0-123">什么是基址？它如何与终结点地址相关联？</span><span class="sxs-lookup"><span data-stu-id="258c0-123">What is the base address? How does it relate to an endpoint address?</span></span>](#BKMK_q10)  
  
<a name="bkmk_0"></a>
## <a name="after-installing-windows-7-and-iis-when-i-attempt-to-browse-to-a-wcf-service-i-get-the-following-error-message-http-error-4043--not-found"></a><span data-ttu-id="258c0-124">在安装 Windows 7 和 IIS 后，当我尝试浏览到 WCF 服务时，收到以下错误消息：HTTP 错误 404.3 – 找不到</span><span class="sxs-lookup"><span data-stu-id="258c0-124">After installing Windows 7 and IIS, when I attempt to browse to a WCF service I get the following error message: HTTP Error 404.3 – Not Found</span></span>  
 <span data-ttu-id="258c0-125">完整错误消息为：</span><span class="sxs-lookup"><span data-stu-id="258c0-125">The full error message is:</span></span>  
  
 <span data-ttu-id="258c0-126">HTTP 错误 404.3 – 找不到：由于扩展配置，无法提供您请求的页面。</span><span class="sxs-lookup"><span data-stu-id="258c0-126">HTTP Error 404.3 – Not FoundThe page you are requesting cannot be served because of the extension configuration.</span></span> <span data-ttu-id="258c0-127">如果此页是脚本，请添加处理程序。</span><span class="sxs-lookup"><span data-stu-id="258c0-127">If the page is a script, add a handler.</span></span> <span data-ttu-id="258c0-128">如果应下载文件，请添加 MIME 映射。</span><span class="sxs-lookup"><span data-stu-id="258c0-128">If the file should be downloaded, add a MIME map.</span></span> <span data-ttu-id="258c0-129">详细错误 InformationModule StaticFileModule。</span><span class="sxs-lookup"><span data-stu-id="258c0-129">Detailed Error InformationModule StaticFileModule.</span></span>  
  
 <span data-ttu-id="258c0-130">当未在控制面板中显式设置 "Windows Communication Foundation HTTP 激活" 时，会出现此错误消息。</span><span class="sxs-lookup"><span data-stu-id="258c0-130">This error message occurs when "Windows Communication Foundation HTTP Activation" is not explicitly set in the Control Panel.</span></span> <span data-ttu-id="258c0-131">若要设置此项，请在窗口的左下角单击 "程序"。</span><span class="sxs-lookup"><span data-stu-id="258c0-131">To set this go to the Control Panel, click Programs in the lower left-hand corner of the window.</span></span> <span data-ttu-id="258c0-132">单击“打开或关闭 Windows 功能”。</span><span class="sxs-lookup"><span data-stu-id="258c0-132">Click Turn Windows features on or off.</span></span> <span data-ttu-id="258c0-133">展开 Microsoft .NET Framework 3.5.1，选中“Windows Communication Foundation HTTP 激活”。</span><span class="sxs-lookup"><span data-stu-id="258c0-133">Expand Microsoft .NET Framework 3.5.1 and select Windows Communication Foundation HTTP Activation.</span></span>  
  
<a name="BKMK_q1"></a>
## <a name="sometimes-i-receive-a-messagesecurityexception-on-the-second-request-if-my-client-is-idle-for-a-while-after-the-first-request-what-is-happening"></a><span data-ttu-id="258c0-134">如果我的客户端在第一次请求后暂时处于空闲，有时我会在第二次请求时收到 MessageSecurityException。</span><span class="sxs-lookup"><span data-stu-id="258c0-134">Sometimes I receive a MessageSecurityException on the second request if my client is idle for a while after the first request.</span></span> <span data-ttu-id="258c0-135">发生了什么？</span><span class="sxs-lookup"><span data-stu-id="258c0-135">What is happening?</span></span>  
 <span data-ttu-id="258c0-136">第二次请求失败主要有两个原因：(1) 会话已超时或 (2) 承载服务的 Web 服务器被回收。</span><span class="sxs-lookup"><span data-stu-id="258c0-136">The second request can fail primarily for two reasons: (1) the session has timed out or (2) the Web server that is hosting the service is recycled.</span></span> <span data-ttu-id="258c0-137">在第一种情况下，会话始终有效，直到服务超时。如果服务在服务的绑定 () 中指定的时间段内未收到来自客户端的请求 <xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A> ，则该服务将终止安全会话。</span><span class="sxs-lookup"><span data-stu-id="258c0-137">In the first case, the session is valid until the service times out. When the service does not receive a request from the client within the period of time specified in the service's binding (<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>), the service terminates the security session.</span></span> <span data-ttu-id="258c0-138">后续客户端消息会导致 <xref:System.ServiceModel.Security.MessageSecurityException>。</span><span class="sxs-lookup"><span data-stu-id="258c0-138">Subsequent client messages result in the <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="258c0-139">客户端必须重新建立与服务的安全会话，才能发送以后的消息或使用有状态安全上下文令牌。</span><span class="sxs-lookup"><span data-stu-id="258c0-139">The client must re-establish a secure session with the service to send future messages or use a stateful security context token.</span></span> <span data-ttu-id="258c0-140">有状态的安全上下文令牌还允许安全会话在回收 Web 服务器后存在。</span><span class="sxs-lookup"><span data-stu-id="258c0-140">Stateful security context tokens also allow a secure session to survive a Web server being recycled.</span></span> <span data-ttu-id="258c0-141">有关在安全会话中使用有状态安全上下文令牌的详细信息，请参阅 [如何：为安全会话创建安全上下文令牌](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)。</span><span class="sxs-lookup"><span data-stu-id="258c0-141">For more information about using stateful secure context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span> <span data-ttu-id="258c0-142">或者，也可禁用安全会话。</span><span class="sxs-lookup"><span data-stu-id="258c0-142">Alternatively, you can disable secure sessions.</span></span> <span data-ttu-id="258c0-143">使用 [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) 绑定时，可以将 `establishSecurityContext` 属性设置为 `false` 以禁用安全会话。</span><span class="sxs-lookup"><span data-stu-id="258c0-143">When you use the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) binding, you can set the `establishSecurityContext` property to `false` to disable secure sessions.</span></span> <span data-ttu-id="258c0-144">若要为其他绑定禁用安全会话，必须创建自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="258c0-144">To disable secure sessions for other bindings, you must create a custom binding.</span></span> <span data-ttu-id="258c0-145">有关创建自定义绑定的详细信息，请参阅 [How to: Create a Custom Binding Using the SecurityBindingElement](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)。</span><span class="sxs-lookup"><span data-stu-id="258c0-145">For details about creating a custom binding, see [How to: Create a Custom Binding Using the SecurityBindingElement](./feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="258c0-146">在应用任何这些选择前，您必须先了解应用程序的安全要求。</span><span class="sxs-lookup"><span data-stu-id="258c0-146">Before you apply any of these options, you must understand your application's security requirements.</span></span>  
  
<a name="BKMK_q2"></a>
## <a name="my-service-starts-to-reject-new-clients-after-about-10-clients-are-interacting-with-it-what-is-happening"></a><span data-ttu-id="258c0-147">大约有 10 个客户端与我的服务交互后，我的服务开始拒绝新的客户端。</span><span class="sxs-lookup"><span data-stu-id="258c0-147">My service starts to reject new clients after about 10 clients are interacting with it.</span></span> <span data-ttu-id="258c0-148">发生了什么？</span><span class="sxs-lookup"><span data-stu-id="258c0-148">What is happening?</span></span>  
 <span data-ttu-id="258c0-149">默认情况下，服务最多只能有 10 个并发会话。</span><span class="sxs-lookup"><span data-stu-id="258c0-149">By default, services can have only 10 concurrent sessions.</span></span> <span data-ttu-id="258c0-150">因此，如果服务绑定使用会话，则服务将接受新的客户端连接，直到到达该数目；之后，它将拒绝新的客户端连接，直到当前会话之一结束。</span><span class="sxs-lookup"><span data-stu-id="258c0-150">Therefore, if the service bindings use sessions, the service accepts new client connections until it reaches that number, after which it refuses new client connections until one of the current sessions ends.</span></span> <span data-ttu-id="258c0-151">可以通过多种方式支持更多的客户端。</span><span class="sxs-lookup"><span data-stu-id="258c0-151">You can support more clients in a number of ways.</span></span> <span data-ttu-id="258c0-152">如果你的服务不要求会话，则不要使用会话绑定。</span><span class="sxs-lookup"><span data-stu-id="258c0-152">If your service does not require sessions, do not use a sessionful binding.</span></span> <span data-ttu-id="258c0-153"> (有关详细信息，请参阅 [使用会话](using-sessions.md)。 ) 另一个选项是通过将属性的值更改 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> 为适合你的情况的数字来增加会话限制。</span><span class="sxs-lookup"><span data-stu-id="258c0-153">(For more information, see [Using Sessions](using-sessions.md).) Another option is to increase the session limit by changing the value of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> property to the number appropriate to your circumstance.</span></span>  
  
<a name="BKMK_q3"></a>
## <a name="can-i-load-my-service-configuration-from-somewhere-other-than-the-wcf-applications-configuration-file"></a><span data-ttu-id="258c0-154">我是否可以从 WCF 应用程序的配置文件以外的某处加载我的服务配置？</span><span class="sxs-lookup"><span data-stu-id="258c0-154">Can I load my service configuration from somewhere other than the WCF application’s configuration file?</span></span>  
 <span data-ttu-id="258c0-155">是。不过，您必须创建自定义 <xref:System.ServiceModel.ServiceHost> 类，并重写 <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="258c0-155">Yes, however, you have to create a custom <xref:System.ServiceModel.ServiceHost> class that overrides the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method.</span></span> <span data-ttu-id="258c0-156">在此方法内，您可以调用 base 先加载配置（如果您还要加载标准配置信息），但是也可以整个替换配置加载系统。</span><span class="sxs-lookup"><span data-stu-id="258c0-156">Inside that method, you can call the base to load configuration first (if you want to load the standard configuration information as well) but you can also entirely replace the configuration loading system.</span></span> <span data-ttu-id="258c0-157">如果要从不同于应用程序配置文件的配置文件中加载配置，则必须自行分析配置文件，然后加载配置。</span><span class="sxs-lookup"><span data-stu-id="258c0-157">If you want to load configuration from a configuration file that is different from the application configuration file, you must parse the configuration file yourself and load the configuration.</span></span>  
  
 <span data-ttu-id="258c0-158">下面的代码示例演示如何重写 <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> 方法以及直接配置终结点。</span><span class="sxs-lookup"><span data-stu-id="258c0-158">The following code example shows how to override the <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> method and directly configure an endpoint.</span></span>  
  
```csharp
public class MyServiceHost : ServiceHost  
{  
    public MyServiceHost(Type serviceType, params Uri[] baseAddresses)
      : base(serviceType, baseAddresses)  
    {
        Console.WriteLine("MyServiceHost Constructor");
    }  
  
    protected override void ApplyConfiguration()  
    {  
        string straddress = GetAddress();  
        Uri address = new Uri(straddress);  
        Binding binding = GetBinding();  
        base.AddServiceEndpoint(typeof(IData), binding, address);  
    }  
  
    string GetAddress()  
    {
        return "http://MyMachine:7777/MyEndpointAddress/";
    }  
  
    Binding GetBinding()  
    {  
        WSHttpBinding binding = new WSHttpBinding();  
        binding.Security.Mode = SecurityMode.None;  
        return binding;  
    }  
}  
```  
  
<a name="BKMK_q4"></a>
## <a name="my-service-and-client-work-great-but-i-cant-get-them-to-work-when-the-client-is-on-another-computer-whats-happening"></a><span data-ttu-id="258c0-159">我的服务和客户端工作得很好，但是当客户端位于另一台计算机上时，为何就无法正常工作？</span><span class="sxs-lookup"><span data-stu-id="258c0-159">My service and client work great, but I can’t get them to work when the client is on another computer?</span></span> <span data-ttu-id="258c0-160">发生了什么情况？</span><span class="sxs-lookup"><span data-stu-id="258c0-160">What’s happening?</span></span>  
 <span data-ttu-id="258c0-161">根据异常的不同，可能会有多个问题：</span><span class="sxs-lookup"><span data-stu-id="258c0-161">Depending upon the exception, there may be several issues:</span></span>  
  
- <span data-ttu-id="258c0-162">可能需要将客户端终结点的地址更改为主机名，而不是“localhost”。</span><span class="sxs-lookup"><span data-stu-id="258c0-162">You might need to change the client endpoint addresses to the host name and not "localhost".</span></span>  
  
- <span data-ttu-id="258c0-163">可能需要打开应用程序的端口。</span><span class="sxs-lookup"><span data-stu-id="258c0-163">You might need to open the port to the application.</span></span> <span data-ttu-id="258c0-164">有关详细信息，请参阅 SDK 示例中的 [Firewall Instructions](./samples/firewall-instructions.md) 。</span><span class="sxs-lookup"><span data-stu-id="258c0-164">For details, see [Firewall Instructions](./samples/firewall-instructions.md) from the SDK samples.</span></span>  
  
- <span data-ttu-id="258c0-165">有关其他可能的问题，请参阅示例主题 [运行 Windows Communication Foundation 示例](./samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="258c0-165">For other possible issues, see the samples topic [Running the Windows Communication Foundation Samples](./samples/running-the-samples.md).</span></span>  
  
- <span data-ttu-id="258c0-166">如果客户端使用的是 Windows 凭据并且异常为 <xref:System.ServiceModel.Security.SecurityNegotiationException>，则按如下方式配置 Kerberos。</span><span class="sxs-lookup"><span data-stu-id="258c0-166">If your client is using Windows credentials and the exception is a <xref:System.ServiceModel.Security.SecurityNegotiationException>, configure Kerberos as follows.</span></span>  
  
    1. <span data-ttu-id="258c0-167">将标识凭据添加到客户端的 App.config 文件中的终结点元素：</span><span class="sxs-lookup"><span data-stu-id="258c0-167">Add the identity credentials to the endpoint element in the client’s App.config file:</span></span>  
  
        ```xml
        <endpoint
          address="http://MyServer:8000/MyService/"
          binding="wsHttpBinding"
          bindingConfiguration="WSHttpBinding_IServiceExample"
          contract="IServiceExample"
          behaviorConfiguration="ClientCredBehavior"
          name="WSHttpBinding_IServiceExample">  
          <identity>  
            <userPrincipalName value="name@corp.contoso.com"/>  
          </identity>  
        </endpoint>  
        ```  
  
    2. <span data-ttu-id="258c0-168">在 System 或 NetworkService 帐户下运行自承载服务。</span><span class="sxs-lookup"><span data-stu-id="258c0-168">Run the self-hosted service under the System or NetworkService account.</span></span> <span data-ttu-id="258c0-169">可以运行此命令在 System 帐户下创建命令窗口：</span><span class="sxs-lookup"><span data-stu-id="258c0-169">You can run this command to create a command window under the System account:</span></span>  
  
        ```console
        at 12:36 /interactive "cmd.exe"  
        ```  
  
    3. <span data-ttu-id="258c0-170">在 Internet 信息服务 (IIS) 下承载服务，默认情况下，IIS 使用服务主体名称 (SPN) 帐户。</span><span class="sxs-lookup"><span data-stu-id="258c0-170">Host the service under Internet Information Services (IIS), which, by default, uses the service principal name (SPN) account.</span></span>  
  
    4. <span data-ttu-id="258c0-171">使用 SetSPN 在域中注册一个新的 SPN。</span><span class="sxs-lookup"><span data-stu-id="258c0-171">Register a new SPN with the domain using SetSPN.</span></span> <span data-ttu-id="258c0-172">你需要是域管理员才能执行此操作。</span><span class="sxs-lookup"><span data-stu-id="258c0-172">You need to be a domain administrator in order to do this.</span></span>  
  
 <span data-ttu-id="258c0-173">有关 Kerberos 协议的详细信息，请参阅 [WCF 中使用的安全概念](./feature-details/security-concepts-used-in-wcf.md) 和：</span><span class="sxs-lookup"><span data-stu-id="258c0-173">For more information about the Kerberos protocol, see [Security Concepts Used in WCF](./feature-details/security-concepts-used-in-wcf.md) and:</span></span>  
  
- [<span data-ttu-id="258c0-174">调试 Windows 身份验证错误</span><span class="sxs-lookup"><span data-stu-id="258c0-174">Debugging Windows Authentication Errors</span></span>](./feature-details/debugging-windows-authentication-errors.md)  
  
- <span data-ttu-id="258c0-175">[Registering Kerberos Service Principal Names by Using Http.sys（使用 Http.sys 注册 Kerberos 服务主体名称）](/previous-versions/sql/sql-server-2008-r2/ms178119(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="258c0-175">[Registering Kerberos Service Principal Names by Using Http.sys](/previous-versions/sql/sql-server-2008-r2/ms178119(v=sql.105))</span></span>  
  
- <span data-ttu-id="258c0-176">[Kerberos Explained（Kerberos 说明）](/previous-versions/windows/it-pro/windows-2000-server/bb742516(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="258c0-176">[Kerberos Explained](/previous-versions/windows/it-pro/windows-2000-server/bb742516(v=technet.10))</span></span>  
  
<a name="BKMK_q5"></a>
## <a name="when-i-throw-a-faultexceptionexception-where-the-type-is-an-exception-i-always-receive-a-general-faultexception-type-on-the-client-and-not-the-generic-type-whats-happening"></a><span data-ttu-id="258c0-177">当我引发 \<Exception> 类型为异常的 FaultException 时，始终会在客户端上收到常规 FaultException 类型，而不是泛型类型。</span><span class="sxs-lookup"><span data-stu-id="258c0-177">When I throw a FaultException\<Exception> where the type is an exception, I always receive a general FaultException type on the client and not the generic type.</span></span> <span data-ttu-id="258c0-178">发生了什么情况？</span><span class="sxs-lookup"><span data-stu-id="258c0-178">What’s happening?</span></span>  
 <span data-ttu-id="258c0-179">强烈建议您创建自己的自定义错误数据类型，并在您的错误协定中将其声明为详细信息类型。</span><span class="sxs-lookup"><span data-stu-id="258c0-179">It is highly recommended that you create your own custom error data type and declare that as the detail type in your fault contract.</span></span> <span data-ttu-id="258c0-180">原因是使用系统提供的异常类型：</span><span class="sxs-lookup"><span data-stu-id="258c0-180">The reason is that using system-provided exception types:</span></span>  
  
- <span data-ttu-id="258c0-181">创建一个类型依赖，它将移除面向服务的应用程序中功能最强大的应用程序之一。</span><span class="sxs-lookup"><span data-stu-id="258c0-181">Creates a type dependency that removes one of the biggest strengths of service-oriented applications.</span></span>  
  
- <span data-ttu-id="258c0-182">不能依赖以标准方式进行序列化的异常。</span><span class="sxs-lookup"><span data-stu-id="258c0-182">Cannot depend upon exceptions serializing in a standard way.</span></span> <span data-ttu-id="258c0-183">某些异常（如 <xref:System.Security.SecurityException>）可能根本无法序列化。</span><span class="sxs-lookup"><span data-stu-id="258c0-183">Some—like <xref:System.Security.SecurityException>—may not be serializable at all.</span></span>  
  
- <span data-ttu-id="258c0-184">向客户端公开内部实现的详细信息。</span><span class="sxs-lookup"><span data-stu-id="258c0-184">Exposes internal implementation details to clients.</span></span> <span data-ttu-id="258c0-185">有关详细信息，请参阅 [在协定和服务中指定和处理错误](specifying-and-handling-faults-in-contracts-and-services.md)。</span><span class="sxs-lookup"><span data-stu-id="258c0-185">For more information, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
 <span data-ttu-id="258c0-186">但是，如果您正在调试应用程序，则可以序列化异常信息，并使用 <xref:System.ServiceModel.Description.ServiceDebugBehavior> 类将其返回到客户端。</span><span class="sxs-lookup"><span data-stu-id="258c0-186">If you are debugging an application, however, you can serialize exception information and return it to the client by using the <xref:System.ServiceModel.Description.ServiceDebugBehavior> class.</span></span>  
  
<a name="BKMK_q6"></a>
## <a name="it-seems-like-one-way-and-request-reply-operations-return-at-roughly-the-same-speed-when-the-reply-contains-no-data-whats-happening"></a><span data-ttu-id="258c0-187">当答复未包含任何数据时，单向操作与请求-答复操作的返回速度似乎基本相同。</span><span class="sxs-lookup"><span data-stu-id="258c0-187">It seems like one-way and request-reply operations return at roughly the same speed when the reply contains no data.</span></span> <span data-ttu-id="258c0-188">发生了什么情况？</span><span class="sxs-lookup"><span data-stu-id="258c0-188">What's happening?</span></span>  
 <span data-ttu-id="258c0-189">指定一个操作为单向只表示操作协定接受输入消息，而不返回输出消息。</span><span class="sxs-lookup"><span data-stu-id="258c0-189">Specifying that an operation is one way means only that the operation contract accepts an input message and does not return an output message.</span></span> <span data-ttu-id="258c0-190">在 WCF 中，当出站数据已写入网络或引发异常时，所有客户端调用都将返回。</span><span class="sxs-lookup"><span data-stu-id="258c0-190">In WCF, all client invocations return when the outbound data has been written to the wire or an exception is thrown.</span></span> <span data-ttu-id="258c0-191">单向操作以相同方式工作，如果找不到服务则它们可以引发；或者如果服务没有准备好从网络接受数据则它们可以阻止。</span><span class="sxs-lookup"><span data-stu-id="258c0-191">One-way operations work the same way, and they can throw if the service cannot be located or block if the service is not prepared to accept the data from the network.</span></span> <span data-ttu-id="258c0-192">通常在 WCF 中，这会导致单向调用返回到客户端的速度比请求-答复更快;但减缓网络上的出站数据发送速度的任何情况都会降低单向操作以及请求-答复操作的速度。</span><span class="sxs-lookup"><span data-stu-id="258c0-192">Typically in WCF, this results in one-way calls returning to the client more quickly than request-reply; but any condition that slows the sending of the outbound data over the network slows one-way operations as well as request-reply operations.</span></span> <span data-ttu-id="258c0-193">有关详细信息，请参阅单向 [服务](./feature-details/one-way-services.md) 和 [使用 WCF 客户端访问服务](./feature-details/accessing-services-using-a-client.md)。</span><span class="sxs-lookup"><span data-stu-id="258c0-193">For more information, see [One-Way Services](./feature-details/one-way-services.md) and [Accessing Services Using a WCF Client](./feature-details/accessing-services-using-a-client.md).</span></span>  
  
<a name="BKMK_q77"></a>
## <a name="im-using-an-x509-certificate-with-my-service-and-i-get-a-systemsecuritycryptographycryptographicexception-whats-happening"></a><span data-ttu-id="258c0-194">我对我的服务使用的是 X.509 证书，并且获得一个 System.Security.Cryptography.CryptographicException。</span><span class="sxs-lookup"><span data-stu-id="258c0-194">I’m using an X.509 certificate with my service and I get a System.Security.Cryptography.CryptographicException.</span></span> <span data-ttu-id="258c0-195">发生了什么情况？</span><span class="sxs-lookup"><span data-stu-id="258c0-195">What’s happening?</span></span>  
 <span data-ttu-id="258c0-196">这通常发生在更改了 IIS 辅助进程运行时所使用的用户帐户之后。</span><span class="sxs-lookup"><span data-stu-id="258c0-196">This commonly occurs after changing the user account under which the IIS worker process runs.</span></span> <span data-ttu-id="258c0-197">例如，在 Windows XP 中，如果你将 Aspnet_wp.exe 运行的默认用户帐户更改为自定义用户帐户，你可能会看到此错误。</span><span class="sxs-lookup"><span data-stu-id="258c0-197">For example, in Windows XP, if you change the default user account that the Aspnet_wp.exe runs under from ASPNET to a custom user account, you may see this error.</span></span> <span data-ttu-id="258c0-198">如果使用的是私钥，则使用该私钥的进程需要具有访问存储该私钥的文件的权限。</span><span class="sxs-lookup"><span data-stu-id="258c0-198">If using a private key, the process that uses it will need to have permissions to access the file storing that key.</span></span>  
  
 <span data-ttu-id="258c0-199">如果的确如此，则必须向该进程的帐户授予对包含该私钥的文件的读访问特权。</span><span class="sxs-lookup"><span data-stu-id="258c0-199">If this is the case, you must give read access privileges to the process's account for the file containing the private key.</span></span> <span data-ttu-id="258c0-200">例如，如果 IIS 辅助进程运行在 Bob 帐户下，则您需要向 Bob 授予对包含该私钥的文件的读访问权。</span><span class="sxs-lookup"><span data-stu-id="258c0-200">For example, if the IIS worker process is running under the Bob account, then you will need to give Bob read access to the file containing the private key.</span></span>  
  
 <span data-ttu-id="258c0-201">有关如何向正确的用户帐户授予对包含特定 x.509 证书的私钥的文件的访问权限的详细信息，请参阅 [如何：使 X.509 证书可供 WCF 访问](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="258c0-201">For more information about how to give the correct user account access to the file that contains the private key for a specific X.509 certificate, see [How to: Make X.509 Certificates Accessible to WCF](./feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md).</span></span>  
  
<a name="BKMK_q88"></a>
## <a name="i-changed-the-first-parameter-of-an-operation-from-uppercase-to-lowercase-now-my-client-throws-an-exception-whats-happening"></a><span data-ttu-id="258c0-202">我将操作的第一个参数从大写更改为了小写，现在我的客户端引发一个异常。</span><span class="sxs-lookup"><span data-stu-id="258c0-202">I changed the first parameter of an operation from uppercase to lowercase; now my client throws an exception.</span></span> <span data-ttu-id="258c0-203">发生了什么情况？</span><span class="sxs-lookup"><span data-stu-id="258c0-203">What's happening?</span></span>  
 <span data-ttu-id="258c0-204">操作签名中的参数名称值是协定的一部分，并区分大小写。</span><span class="sxs-lookup"><span data-stu-id="258c0-204">The values of the parameter names in the operation signature are part of the contract and are case-sensitive.</span></span> <span data-ttu-id="258c0-205">当需要区分本地参数名称与描述客户端应用程序操作的元数据时，请使用 <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> 属性。</span><span class="sxs-lookup"><span data-stu-id="258c0-205">Use the <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> attribute when you need to distinguish between the local parameter name and the metadata that describes the operation for client applications.</span></span>  
  
<a name="BKMK_q99"></a>
## <a name="im-using-one-of-my-tracing-tools-and-i-get-an-endpointnotfoundexception-whats-happening"></a><span data-ttu-id="258c0-206">我正在使用我的跟踪工具之一，并且获得一个 EndpointNotFoundException。</span><span class="sxs-lookup"><span data-stu-id="258c0-206">I’m using one of my tracing tools and I get an EndpointNotFoundException.</span></span> <span data-ttu-id="258c0-207">发生了什么情况？</span><span class="sxs-lookup"><span data-stu-id="258c0-207">What’s happening?</span></span>  
 <span data-ttu-id="258c0-208">如果使用的跟踪工具不是系统提供的 WCF 跟踪机制，并且收到一个 <xref:System.ServiceModel.EndpointNotFoundException> 指示存在地址筛选器不匹配的，则需要使用 <xref:System.ServiceModel.Description.ClientViaBehavior> 类将消息定向到跟踪实用工具，并让该实用工具将这些消息重定向到服务地址。</span><span class="sxs-lookup"><span data-stu-id="258c0-208">If you are using a tracing tool that is not the system-provided WCF tracing mechanism and you receive an <xref:System.ServiceModel.EndpointNotFoundException> that indicates that there was an address filter mismatch, you need to use the <xref:System.ServiceModel.Description.ClientViaBehavior> class to direct the messages to the tracing utility and have the utility redirect those messages to the service address.</span></span> <span data-ttu-id="258c0-209"><xref:System.ServiceModel.Description.ClientViaBehavior> 类更改 `Via` 寻址标头，以独立于最终接收方（由 `To` 寻址标头指示）指定下一个网络地址。</span><span class="sxs-lookup"><span data-stu-id="258c0-209">The <xref:System.ServiceModel.Description.ClientViaBehavior> class alters the `Via` addressing header to specify the next network address separately from the ultimate receiver, indicated by the `To` addressing header.</span></span> <span data-ttu-id="258c0-210">但是，执行此操作时请不要更改终结点地址，它用于设立 `To` 值。</span><span class="sxs-lookup"><span data-stu-id="258c0-210">When doing this, however, do not change the endpoint address, which is used to establish the `To` value.</span></span>  
  
 <span data-ttu-id="258c0-211">下面的代码示例演示一个示例客户端配置文件。</span><span class="sxs-lookup"><span data-stu-id="258c0-211">The following code example shows an example client configuration file.</span></span>  
  
```xml
<endpoint
  address="http://localhost:8000/MyServer/"  
  binding="wsHttpBinding"  
  bindingConfiguration="WSHttpBinding_IMyContract"  
  behaviorConfiguration="MyClient"
  contract="IMyContract"
  name="WSHttpBinding_IMyContract">  
</endpoint>  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="MyClient">  
      <clientVia viaUri="http://localhost:8001/MyServer/"/>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
<a name="BKMK_q10"></a>
## <a name="what-is-the-base-address-how-does-it-relate-to-an-endpoint-address"></a><span data-ttu-id="258c0-212">何为基址？</span><span class="sxs-lookup"><span data-stu-id="258c0-212">What is the base address?</span></span> <span data-ttu-id="258c0-213">它如何关联到一个终结点地址？</span><span class="sxs-lookup"><span data-stu-id="258c0-213">How does it relate to an endpoint address?</span></span>  
 <span data-ttu-id="258c0-214">基址是 <xref:System.ServiceModel.ServiceHost> 类的根地址。</span><span class="sxs-lookup"><span data-stu-id="258c0-214">A base address is the root address for a <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="258c0-215">默认情况下，如果将一个 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 类添加到您的服务配置中，主机发布的所有终结点的 Web 服务描述语言 (WSDL) 都将从 HTTP 基址、提供给元数据行为的任何相对地址以及“?wsdl”中检索。</span><span class="sxs-lookup"><span data-stu-id="258c0-215">By default, if you add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class into your service configuration, the Web Services Description Language (WSDL) for all endpoints the host publishes are retrieved from the HTTP base address, plus any relative address provided to the metadata behavior, plus "?wsdl".</span></span> <span data-ttu-id="258c0-216">如果你熟悉 ASP.NET 和 IIS，则基址等效于虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="258c0-216">If you are familiar with ASP.NET and IIS, the base address is equivalent to the virtual directory.</span></span>  
  
## <a name="sharing-a-port-between-a-service-endpoint-and-a-mex-endpoint-using-the-nettcpbinding"></a><span data-ttu-id="258c0-217">使用 NetTcpBinding 共享服务终结点和 MEX 终结点之间的端口</span><span class="sxs-lookup"><span data-stu-id="258c0-217">Sharing a port between a service endpoint and a mex endpoint using the NetTcpBinding</span></span>  
 <span data-ttu-id="258c0-218">如果将服务的基址指定为 net.tcp://MyServer:8080/MyService 并添加以下终结点：</span><span class="sxs-lookup"><span data-stu-id="258c0-218">If you specify the base address for a service as net.tcp://MyServer:8080/MyService and add the following endpoints:</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
 <span data-ttu-id="258c0-219">如果按下面的配置代码段所示修改某个 NetTcpBinding 设置：</span><span class="sxs-lookup"><span data-stu-id="258c0-219">And if you modify one of the NetTcpBinding settings as shown in the following configuration snippet:</span></span>  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding closeTimeout="00:01:00" openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00" transactionFlow="false" transferMode="Buffered" transactionProtocol="OleTransactions" hostNameComparisonMode="StrongWildcard" listenBacklog="10" maxBufferPoolSize="524288" maxBufferSize="65536" maxConnections="11" maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384"/>  
      <reliableSession ordered="true" inactivityTimeout="00:10:00" enabled="false"/>  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign"/>  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="258c0-220">您将看到一条与以下内容类似的错误：未经处理的异常: System.ServiceModel.AddressAlreadyInUseException: IP 终结点 0.0.0.0:9000 上已有侦听器 可使用 MEX 终结点的其他端口指定完全限定的 URL 来解决此错误，如下面的配置代码段中所示：</span><span class="sxs-lookup"><span data-stu-id="258c0-220">You will see an error like the following: Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000 You can work around this error by specifying a fully qualified URL with a different port for the MEX endpoint as shown in the following configuration snippet:</span></span>  
  
```xml
<services>  
  <service name="Microsoft.Samples.NetTcp.CalculatorService">  
    <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
    <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
  </service>  
</services>  
```  
  
<a name="BK_MK99"></a>
## <a name="when-calling-a-wcf-web-http-application-from-a-wcf-soap-application-the-service-returns-the-following-error-405-method-not-allowed"></a><span data-ttu-id="258c0-221">从 WCF SOAP 应用程序调用 WCF Web HTTP 应用程序时，服务返回以下错误：405 不允许的方法</span><span class="sxs-lookup"><span data-stu-id="258c0-221">When calling a WCF Web HTTP application from a WCF SOAP application the service returns the following error: 405 Method Not Allowed</span></span>  
 <span data-ttu-id="258c0-222"> (从 WCF 服务使用和) 的服务调用 WCF Web HTTP 应用程序 <xref:System.ServiceModel.WebHttpBinding> <xref:System.ServiceModel.Description.WebHttpBehavior> 时，可能会生成以下异常： ``Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.`` 发生此异常的原因是 wcf <xref:System.ServiceModel.OperationContext> 使用传入的覆盖传出的 <xref:System.ServiceModel.OperationContext> 。</span><span class="sxs-lookup"><span data-stu-id="258c0-222">Calling a WCF Web HTTP application (a service that uses the <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior>) from a WCF service may generate the following exception: ``Unhandled Exception: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: The remote server returned an unexpected response: (405) Method Not Allowed.`` This exception occurs because WCF overwrites the outgoing <xref:System.ServiceModel.OperationContext> with the incoming <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="258c0-223">若要解决此问题，请 <xref:System.ServiceModel.OperationContextScope> 在 WCF WEB HTTP 服务操作内创建。</span><span class="sxs-lookup"><span data-stu-id="258c0-223">To solve this problem, create an <xref:System.ServiceModel.OperationContextScope> within the WCF Web HTTP service operation.</span></span> <span data-ttu-id="258c0-224">例如：</span><span class="sxs-lookup"><span data-stu-id="258c0-224">For example:</span></span>  
  
```csharp
public string Echo(string input)  
{  
    using (new OperationContextScope(this.InnerChannel))  
    {  
        return base.Channel.Echo(input);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="258c0-225">请参阅</span><span class="sxs-lookup"><span data-stu-id="258c0-225">See also</span></span>

- [<span data-ttu-id="258c0-226">调试 Windows 身份验证错误</span><span class="sxs-lookup"><span data-stu-id="258c0-226">Debugging Windows Authentication Errors</span></span>](./feature-details/debugging-windows-authentication-errors.md)
