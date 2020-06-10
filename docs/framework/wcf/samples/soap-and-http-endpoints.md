---
title: SOAP 和 HTTP 终结点
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: fee1df86026716941f65dccca15d437ae917770b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600940"
---
# <a name="soap-and-http-endpoints"></a><span data-ttu-id="d43bb-102">SOAP 和 HTTP 终结点</span><span class="sxs-lookup"><span data-stu-id="d43bb-102">SOAP and HTTP Endpoints</span></span>
<span data-ttu-id="d43bb-103">此示例演示如何使用 WCF Web 编程模型实现基于 RPC 的服务并以 SOAP 格式和 "纯旧 XML" （POX）格式公开此服务。</span><span class="sxs-lookup"><span data-stu-id="d43bb-103">This sample demonstrates how to implement an RPC-based service and expose it in the SOAP format and the "Plain Old XML" (POX) format using the WCF Web Programming model.</span></span> <span data-ttu-id="d43bb-104">有关服务的 HTTP 绑定的更多详细信息，请参阅[基本 HTTP 服务](basic-http-service.md)示例。</span><span class="sxs-lookup"><span data-stu-id="d43bb-104">See the [Basic HTTP Service](basic-http-service.md) sample for more details about the HTTP binding for the service.</span></span> <span data-ttu-id="d43bb-105">本示例重点介绍有关使用不同绑定通过 SOAP 和 HTTP 公开相同服务的详细信息。</span><span class="sxs-lookup"><span data-stu-id="d43bb-105">This sample focuses on the details that pertain to exposing the same service over SOAP and HTTP using different bindings.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="d43bb-106">演示</span><span class="sxs-lookup"><span data-stu-id="d43bb-106">Demonstrates</span></span>  
 <span data-ttu-id="d43bb-107">使用 WCF 通过 SOAP 和 HTTP 公开 RPC 服务。</span><span class="sxs-lookup"><span data-stu-id="d43bb-107">Exposing an RPC service over SOAP and HTTP using WCF.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="d43bb-108">讨论区</span><span class="sxs-lookup"><span data-stu-id="d43bb-108">Discussion</span></span>  
 <span data-ttu-id="d43bb-109">此示例由两个组件组成：一个 Web 应用程序项目（服务），其中包含一个使用 SOAP 和 HTTP 绑定调用服务操作的 WCF 服务和控制台应用程序（客户端）。</span><span class="sxs-lookup"><span data-stu-id="d43bb-109">This sample consists of two components: a Web Application project (Service) that contains a WCF service and a console application (Client) that invokes service operations using SOAP and HTTP bindings.</span></span>  
  
 <span data-ttu-id="d43bb-110">WCF 服务公开2个操作– `GetData` 并 `PutData` 回显作为输入传递的字符串。</span><span class="sxs-lookup"><span data-stu-id="d43bb-110">The WCF service exposes 2 operations –`GetData` and `PutData` – that echo the string that was passed as input.</span></span> <span data-ttu-id="d43bb-111">这些服务操作使用 <xref:System.ServiceModel.Web.WebGetAttribute> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute> 进行批注。</span><span class="sxs-lookup"><span data-stu-id="d43bb-111">The service operations are annotated with <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="d43bb-112">这些特性控制这些操作的 HTTP 投影。</span><span class="sxs-lookup"><span data-stu-id="d43bb-112">These attributes control the HTTP projection of these operations.</span></span> <span data-ttu-id="d43bb-113">此外，这些操作使用 <xref:System.ServiceModel.OperationContractAttribute> 进行批注，从而使其可以通过 SOAP 绑定进行公开。</span><span class="sxs-lookup"><span data-stu-id="d43bb-113">In addition, they are annotated with <xref:System.ServiceModel.OperationContractAttribute>, which enables them to be exposed over SOAP bindings.</span></span> <span data-ttu-id="d43bb-114">服务的 `PutData` 方法引发 <xref:System.ServiceModel.Web.WebFaultException>，该异常使用 HTTP 状态代码通过 HTTP 发回，通过 SOAP 作为 SOAP 错误发回。</span><span class="sxs-lookup"><span data-stu-id="d43bb-114">The service’s `PutData` method throws a <xref:System.ServiceModel.Web.WebFaultException>, which gets sent back over HTTP using the HTTP status code and gets sent back over SOAP as a SOAP fault.</span></span>  
  
 <span data-ttu-id="d43bb-115">Web.config 文件将 WCF 服务配置为3个终结点：</span><span class="sxs-lookup"><span data-stu-id="d43bb-115">The Web.config file configures the WCF service with 3 endpoints:</span></span>  
  
- <span data-ttu-id="d43bb-116">~/service.svc/mex 终结点，公开服务元数据供基于 SOAP 的客户端访问。</span><span class="sxs-lookup"><span data-stu-id="d43bb-116">The ~/service.svc/mex endpoint that exposes the service metadata for access by SOAP-based clients.</span></span>  
  
- <span data-ttu-id="d43bb-117">~/service.svc/http 终结点，使客户端可以使用 HTTP 绑定访问服务。</span><span class="sxs-lookup"><span data-stu-id="d43bb-117">The ~/service.svc/http endpoint that enables clients to access the service using the HTTP binding.</span></span>  
  
- <span data-ttu-id="d43bb-118">~/service.svc/soap 终结点，使客户端可以使用 SOAP over HTTP 绑定访问服务。</span><span class="sxs-lookup"><span data-stu-id="d43bb-118">The ~/service.svc/soap endpoint that allows the clients to access the service using the SOAP over HTTP binding.</span></span>  
  
 <span data-ttu-id="d43bb-119">使用 `webHttp` 设置为的 <> 标准终结点配置 HTTP 终结点 `helpEnabled` `true` 。</span><span class="sxs-lookup"><span data-stu-id="d43bb-119">The HTTP endpoint is configured with a <`webHttp`> standard endpoint which has `helpEnabled` set to `true`.</span></span> <span data-ttu-id="d43bb-120">因此，服务在 ~/service.svc/http/help 上公开基于 XHTML 的页面，基于 HTTP 的客户端可以使用该页面访问服务。</span><span class="sxs-lookup"><span data-stu-id="d43bb-120">As a result, the service exposes an XHTML based help page at ~/service.svc/http/help that HTTP-based clients can use to access the service.</span></span>  
  
 <span data-ttu-id="d43bb-121">该客户端项目演示如何使用 SOAP 代理（通过**添加服务引用**生成）访问服务，并使用访问服务 <xref:System.Net.WebClient> 。</span><span class="sxs-lookup"><span data-stu-id="d43bb-121">The client project demonstrates accessing the service using a SOAP proxy (generated through **Add Service Reference**) and accessing the service using <xref:System.Net.WebClient>.</span></span>  
  
 <span data-ttu-id="d43bb-122">该示例包含一个 Web 承载的服务和一个控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="d43bb-122">The sample consists of a Web-hosted service and a console application.</span></span> <span data-ttu-id="d43bb-123">在控制台应用程序运行时，客户端会对服务进行请求，并将响应中的相关信息写入控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="d43bb-123">As the console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="d43bb-124">运行示例</span><span class="sxs-lookup"><span data-stu-id="d43bb-124">To run the sample</span></span>  
  
1. <span data-ttu-id="d43bb-125">打开 SOAP 和 HTTP 终结点示例的解决方案。</span><span class="sxs-lookup"><span data-stu-id="d43bb-125">Open the solution for the SOAP and HTTP Endpoints Sample.</span></span>  
  
2. <span data-ttu-id="d43bb-126">按 CTRL+SHIFT+B 生成解决方案。</span><span class="sxs-lookup"><span data-stu-id="d43bb-126">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3. <span data-ttu-id="d43bb-127">如果该窗口尚未打开，请按 CTRL + W，S 打开**解决方案资源管理器**窗口。</span><span class="sxs-lookup"><span data-stu-id="d43bb-127">If it is not already open, press CTRL+W, S to open the **Solution Explorer** window.</span></span>  
  
4. <span data-ttu-id="d43bb-128">在 "**解决方案资源管理器**" 窗口中，右键单击**服务**项目，将光标放在 "**调试**" 上下文菜单选项上，以显示 "**启动新实例**" 上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="d43bb-128">From the **Solution Explorer** window, right-click the **Service** project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="d43bb-129">单击 "**启动新实例**"。</span><span class="sxs-lookup"><span data-stu-id="d43bb-129">Click **Start New Instance**.</span></span> <span data-ttu-id="d43bb-130">这将启动承载服务的 ASP.NET 开发服务器。</span><span class="sxs-lookup"><span data-stu-id="d43bb-130">This launches the ASP.NET development server, which hosts the service.</span></span>  
  
5. <span data-ttu-id="d43bb-131">在解决方案资源管理器窗口中，右键单击客户端项目，然后将光标放在 "**调试**" 上下文菜单选项上以显示 "**启动新实例**" 上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="d43bb-131">From the Solution Explorer windows, right-click the Client project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="d43bb-132">单击 "**启动新实例**"。</span><span class="sxs-lookup"><span data-stu-id="d43bb-132">Click **Start New Instance**.</span></span>  
  
6. <span data-ttu-id="d43bb-133">出现客户端控制台窗口，该窗口提供了正在运行的服务的 URI，以及该服务的 HTML 帮助页的 URI。</span><span class="sxs-lookup"><span data-stu-id="d43bb-133">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="d43bb-134">可随时通过在浏览器中键入 HTML 帮助页的 URI 来查看该帮助页。</span><span class="sxs-lookup"><span data-stu-id="d43bb-134">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>  
  
7. <span data-ttu-id="d43bb-135">在示例运行时，客户端将写入当前活动的状态。</span><span class="sxs-lookup"><span data-stu-id="d43bb-135">As the sample runs, the client writes the status of the current activity.</span></span>  
  
8. <span data-ttu-id="d43bb-136">按任意键可终止客户端控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="d43bb-136">Press any key to terminate the client console application.</span></span>  
  
9. <span data-ttu-id="d43bb-137">按 Shift+F5 可停止调试服务。</span><span class="sxs-lookup"><span data-stu-id="d43bb-137">Press SHIFT+F5 to stop debugging the service.</span></span>  
  
10. <span data-ttu-id="d43bb-138">在 Windows 通知区域中，右键单击 ASP.NET 开发服务器图标，然后从上下文菜单中选择 "**停止**"。</span><span class="sxs-lookup"><span data-stu-id="d43bb-138">In the Windows Notification Area, right-click the ASP.NET development server icon and select **Stop** from the context menu.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d43bb-139">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="d43bb-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d43bb-140">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="d43bb-140">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d43bb-141">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="d43bb-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d43bb-142">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="d43bb-142">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
