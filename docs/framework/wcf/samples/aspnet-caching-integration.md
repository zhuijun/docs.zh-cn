---
title: ASP.NET 缓存集成
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: c541f3caad8a500b9fdb33d00b58706bac876e37
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594746"
---
# <a name="aspnet-caching-integration"></a><span data-ttu-id="ce96b-102">ASP.NET 缓存集成</span><span class="sxs-lookup"><span data-stu-id="ce96b-102">ASP.NET Caching Integration</span></span>

<span data-ttu-id="ce96b-103">此示例演示如何通过 WCF WEB HTTP 编程模型使用 ASP.NET 输出缓存。</span><span class="sxs-lookup"><span data-stu-id="ce96b-103">This sample demonstrates how to utilize the ASP.NET output cache with the WCF WEB HTTP programming model.</span></span> <span data-ttu-id="ce96b-104">本主题重点介绍 ASP.NET 输出缓存集成功能。</span><span class="sxs-lookup"><span data-stu-id="ce96b-104">This topic focuses on the ASP.NET output cache integration feature.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ce96b-105">演示</span><span class="sxs-lookup"><span data-stu-id="ce96b-105">Demonstrates</span></span>

<span data-ttu-id="ce96b-106">与 ASP.NET 输出缓存的集成</span><span class="sxs-lookup"><span data-stu-id="ce96b-106">Integration with the ASP.NET Output Cache</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ce96b-107">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="ce96b-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ce96b-108">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="ce96b-108">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ce96b-109">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="ce96b-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ce96b-110">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="ce96b-110">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`

## <a name="discussion"></a><span data-ttu-id="ce96b-111">讨论区</span><span class="sxs-lookup"><span data-stu-id="ce96b-111">Discussion</span></span>

<span data-ttu-id="ce96b-112">该示例使用将 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> ASP.NET output 缓存与 Windows Communication Foundation （WCF）服务结合使用。</span><span class="sxs-lookup"><span data-stu-id="ce96b-112">The sample uses the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> to utilize ASP.NET output caching with the Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="ce96b-113"><xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> 应用于服务操作，并在应该应用于给定操作的响应的配置文件中提供缓存配置文件的名称。</span><span class="sxs-lookup"><span data-stu-id="ce96b-113">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is applied to service operations, and provides the name of a cache profile in a configuration file that should be applied to responses from the given operation.</span></span>

<span data-ttu-id="ce96b-114">在示例服务项目的 Service.cs 文件中， `GetCustomer` 和 `GetCustomers` 操作都用来标记 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> ，后者提供缓存配置文件名称 "CacheFor60Seconds"。</span><span class="sxs-lookup"><span data-stu-id="ce96b-114">In the Service.cs file of the sample Service project, both the `GetCustomer` and `GetCustomers` operations are marked with the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, which provides the cache profile name "CacheFor60Seconds".</span></span> <span data-ttu-id="ce96b-115">在服务项目的 web.config 文件中，缓存配置文件 "CacheFor60Seconds" 在 `caching` < > 的 < > 元素下提供 `system.web` 。</span><span class="sxs-lookup"><span data-stu-id="ce96b-115">In the Web.config file of the Service project, the cache profile "CacheFor60Seconds" is provided under the <`caching`> element of <`system.web`>.</span></span> <span data-ttu-id="ce96b-116">对于此缓存配置文件，属性的值 `duration` 为 "60"，因此与此配置文件关联的响应将在 ASP.NET 输出缓存中缓存60秒。</span><span class="sxs-lookup"><span data-stu-id="ce96b-116">For this cache profile, the value of the `duration` attribute is "60", so responses associated with this profile are cached in the ASP.NET output cache for 60 seconds.</span></span> <span data-ttu-id="ce96b-117">此外，对于此缓存配置文件，该 `varmByParam` 属性设置为 "format"，因此具有不同 `format` 查询字符串参数值的请求会分别缓存其响应。</span><span class="sxs-lookup"><span data-stu-id="ce96b-117">Also, for this cache profile, the `varmByParam` attribute is set to "format" so requests with different values for the `format` query string parameter have their responses cached separately.</span></span> <span data-ttu-id="ce96b-118">最后，缓存配置文件的 `varyByHeader` 属性设置为 "接受"，因此具有不同 Accept 标头值的请求会分别缓存其响应。</span><span class="sxs-lookup"><span data-stu-id="ce96b-118">Lastly, the cache profile’s `varyByHeader` attribute is set to "Accept", so requests with different Accept header values have their responses cached separately.</span></span>

<span data-ttu-id="ce96b-119">客户端项目中的 Program.cs 演示如何使用 <xref:System.Net.HttpWebRequest> 编写此类客户端。</span><span class="sxs-lookup"><span data-stu-id="ce96b-119">Program.cs in the Client project demonstrates how such a client can be authored using <xref:System.Net.HttpWebRequest>.</span></span> <span data-ttu-id="ce96b-120">请注意，这只是访问 WCF 服务的一种方式。</span><span class="sxs-lookup"><span data-stu-id="ce96b-120">Note that this is just one way to access a WCF service.</span></span> <span data-ttu-id="ce96b-121">还可以使用其他 .NET Framework 类（例如 WCF 通道工厂和）来访问该服务 <xref:System.Net.WebClient> 。</span><span class="sxs-lookup"><span data-stu-id="ce96b-121">It is also possible to access the service using other .NET Framework classes like the WCF channel factory and <xref:System.Net.WebClient>.</span></span> <span data-ttu-id="ce96b-122">SDK 中的其他示例（如[基本 HTTP 服务](basic-http-service.md)示例）演示如何使用这些类与 WCF 服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="ce96b-122">Other samples in the SDK (such as the [Basic HTTP Service](basic-http-service.md) sample) illustrate how to use these classes to communicate with a WCF service.</span></span>

## <a name="to-run-the-sample"></a><span data-ttu-id="ce96b-123">运行示例</span><span class="sxs-lookup"><span data-stu-id="ce96b-123">To run the sample</span></span>

<span data-ttu-id="ce96b-124">该示例由三个项目组成：</span><span class="sxs-lookup"><span data-stu-id="ce96b-124">The sample consists of three projects:</span></span>

- <span data-ttu-id="ce96b-125">**服务**：一个 Web 应用程序项目，该项目包含 ASP.NET 中承载的 WCF HTTP 服务。</span><span class="sxs-lookup"><span data-stu-id="ce96b-125">**Service**: A Web Application project that includes a WCF HTTP service hosted in ASP.NET.</span></span>

- <span data-ttu-id="ce96b-126">**客户端**：使调用服务的控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="ce96b-126">**Client**: A console application project that makes calls to the service.</span></span>

- <span data-ttu-id="ce96b-127">**常见**：一个共享库，其中包含客户端和服务使用的客户类型。</span><span class="sxs-lookup"><span data-stu-id="ce96b-127">**Common**: A shared library that contains the Customer type used by the client and service.</span></span>

<span data-ttu-id="ce96b-128">在客户端控制台应用程序运行时，客户端会对服务进行请求，并将响应中的相关信息写入控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="ce96b-128">As the Client console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>

#### <a name="to-run-the-sample"></a><span data-ttu-id="ce96b-129">运行示例</span><span class="sxs-lookup"><span data-stu-id="ce96b-129">To run the sample</span></span>

1. <span data-ttu-id="ce96b-130">打开 ASP.NET 缓存集成示例的解决方案。</span><span class="sxs-lookup"><span data-stu-id="ce96b-130">Open the solution for the ASP.NET Caching Integration Sample.</span></span>

2. <span data-ttu-id="ce96b-131">按 CTRL+SHIFT+B 生成解决方案。</span><span class="sxs-lookup"><span data-stu-id="ce96b-131">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="ce96b-132">如果 "**解决方案资源管理器**" 窗口尚未打开，请按 CTRL + W + S。</span><span class="sxs-lookup"><span data-stu-id="ce96b-132">If the **Solution Explorer** window is not already open, press CTRL+W+S.</span></span>

4. <span data-ttu-id="ce96b-133">从 "**解决方案资源管理器**" 窗口中，右键单击**服务**项目，然后选择 "**启动新实例**"。</span><span class="sxs-lookup"><span data-stu-id="ce96b-133">From the **Solution Explorer** window, right click the **Service** project and select **Start New Instance**.</span></span> <span data-ttu-id="ce96b-134">这将启动承载服务的 ASP.NET 开发服务器。</span><span class="sxs-lookup"><span data-stu-id="ce96b-134">This launches the ASP.NET development server, which hosts the service.</span></span>

5. <span data-ttu-id="ce96b-135">从 "**解决方案资源管理器**" 窗口中，右键单击**客户端**项目，然后选择 "**启动新实例**"。</span><span class="sxs-lookup"><span data-stu-id="ce96b-135">From the **Solution Explorer** window, right click the **Client** project and select **Start New Instance**.</span></span>

6. <span data-ttu-id="ce96b-136">出现客户端控制台窗口，该窗口提供了正在运行的服务的 URI，以及该服务的 HTML 帮助页的 URI。</span><span class="sxs-lookup"><span data-stu-id="ce96b-136">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="ce96b-137">可随时通过在浏览器中键入 HTML 帮助页的 URI 来查看该帮助页。</span><span class="sxs-lookup"><span data-stu-id="ce96b-137">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>

7. <span data-ttu-id="ce96b-138">在示例运行时，客户端将写入当前活动的状态。</span><span class="sxs-lookup"><span data-stu-id="ce96b-138">As the sample runs, the client writes the status of the current activity.</span></span>

8. <span data-ttu-id="ce96b-139">按任意键可终止客户端控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="ce96b-139">Press any key to terminate the client console application.</span></span>

9. <span data-ttu-id="ce96b-140">按 Shift+F5 可停止调试服务。</span><span class="sxs-lookup"><span data-stu-id="ce96b-140">Press SHIFT+F5 to stop debugging the service.</span></span>

10. <span data-ttu-id="ce96b-141">在 Windows 通知区域中，右键单击 "ASP.NET 开发服务器" 图标，然后选择 "**停止**"。</span><span class="sxs-lookup"><span data-stu-id="ce96b-141">In the Windows Notification Area, right click the ASP.NET development server icon and select **Stop**.</span></span>
