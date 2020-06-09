---
title: 使用 HTTP POST 的 AJAX 服务
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: 143585b40a493983b7265971a17224165de6f36d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575883"
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="20d29-102">使用 HTTP POST 的 AJAX 服务</span><span class="sxs-lookup"><span data-stu-id="20d29-102">AJAX Service Using HTTP POST</span></span>

<span data-ttu-id="20d29-103">此示例演示如何使用 Windows Communication Foundation （WCF）来创建使用 HTTP POST 的 ASP.NET 异步 JavaScript 和 XML （AJAX）服务。</span><span class="sxs-lookup"><span data-stu-id="20d29-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="20d29-104">AJAX 服务是指可以从 Web 浏览器客户端使用基本 JavaScript 代码访问的服务。</span><span class="sxs-lookup"><span data-stu-id="20d29-104">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="20d29-105">此示例以[基本 AJAX 服务](basic-ajax-service.md)示例为基础。这两个示例的唯一区别在于使用 HTTP POST，而不是 HTTP GET。</span><span class="sxs-lookup"><span data-stu-id="20d29-105">This sample builds on the [Basic AJAX Service](basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>

<span data-ttu-id="20d29-106">Windows Communication Foundation （WCF）中的 AJAX 支持经过优化，可通过控件与 ASP.NET AJAX 一起使用 `ScriptManager` 。</span><span class="sxs-lookup"><span data-stu-id="20d29-106">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="20d29-107">有关将 WCF 与 ASP.NET AJAX 一起使用的示例，请参阅[Ajax 示例](ajax-service-using-http-post.md)。</span><span class="sxs-lookup"><span data-stu-id="20d29-107">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](ajax-service-using-http-post.md).</span></span>

> [!NOTE]
> <span data-ttu-id="20d29-108">本主题的最后介绍了此示例的设置过程和生成说明。</span><span class="sxs-lookup"><span data-stu-id="20d29-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="20d29-109">以下示例中的服务是不包含 AJAX 特定代码的 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="20d29-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span>

<span data-ttu-id="20d29-110">如果对 <xref:System.ServiceModel.Web.WebInvokeAttribute> 操作应用了属性，或 <xref:System.ServiceModel.Web.WebGetAttribute> 未应用该属性，则使用默认的 HTTP 谓词（"POST"）。</span><span class="sxs-lookup"><span data-stu-id="20d29-110">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="20d29-111">POST 请求虽然比 GET 请求更难构造，但它们不会被缓存；当不适宜缓存时，应对所有操作使用 POST 请求。</span><span class="sxs-lookup"><span data-stu-id="20d29-111">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>

```csharp
[ServiceContract(Namespace = "PostAjaxService")]
public interface ICalculator
{
    [WebInvoke]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

<span data-ttu-id="20d29-112">通过使用 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 在服务上创建 AJAX 终结点，就像在基本 AJAX 服务示例中一样。</span><span class="sxs-lookup"><span data-stu-id="20d29-112">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>

<span data-ttu-id="20d29-113">与 GET 请求不同的是，不能从浏览器中调用 POST 服务。</span><span class="sxs-lookup"><span data-stu-id="20d29-113">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="20d29-114">例如，导航到会 `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` 导致错误，因为 POST 服务要求在 `n1` `n2` 消息正文中以 JSON 格式发送和参数，而不是在 URL 中发送和参数。</span><span class="sxs-lookup"><span data-stu-id="20d29-114">For example, navigating to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body in the JSON format, and not in the URL.</span></span>

<span data-ttu-id="20d29-115">客户端网页 PostAjaxClientPage.aspx 包含 ASP.NET 代码以便在用户单击页面上的操作按钮之一时调用服务。</span><span class="sxs-lookup"><span data-stu-id="20d29-115">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="20d29-116">服务的响应方式与在[基本 AJAX 服务](basic-ajax-service.md)示例中一样，通过 GET 请求来实现。</span><span class="sxs-lookup"><span data-stu-id="20d29-116">The service responds in the same way as in the [Basic AJAX Service](basic-ajax-service.md) sample, with the GET request.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="20d29-117">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="20d29-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="20d29-118">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="20d29-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="20d29-119">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="20d29-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="20d29-120">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="20d29-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="20d29-121">设置、生成和运行示例</span><span class="sxs-lookup"><span data-stu-id="20d29-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="20d29-122">确保为 Windows Communication Foundation 示例执行设置说明[一次性安装过程](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="20d29-122">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="20d29-123">按照[生成 Windows Communication Foundation 示例](building-the-samples.md)中所述生成解决方案 postajaxservice.sln。</span><span class="sxs-lookup"><span data-stu-id="20d29-123">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="20d29-124">导航到 `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` （不要在浏览器中从项目目录打开 postajaxclientpage.aspx）。</span><span class="sxs-lookup"><span data-stu-id="20d29-124">Navigate to `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>
