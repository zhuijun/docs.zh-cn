---
title: 在 Internet 信息服务中承载
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: 7bfdf2b057c791da7e15619d69c0314557944093
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555830"
---
# <a name="host-in-internet-information-services"></a><span data-ttu-id="fbc46-102">Internet Information Services 中的主机</span><span class="sxs-lookup"><span data-stu-id="fbc46-102">Host in Internet Information Services</span></span>

<span data-ttu-id="fbc46-103">承载 Windows Communication Foundation (WCF) 服务的一种方法是 Internet Information Services (IIS) 应用程序。</span><span class="sxs-lookup"><span data-stu-id="fbc46-103">One option for hosting Windows Communication Foundation (WCF) services is inside of an Internet Information Services (IIS) application.</span></span> <span data-ttu-id="fbc46-104">此托管模型与 ASP.NET 和 ASP.NET Web 服务 (.ASMX) Web 服务使用的模型类似。</span><span class="sxs-lookup"><span data-stu-id="fbc46-104">This hosting model is similar to the model used by ASP.NET and ASP.NET Web services (ASMX) Web Services.</span></span>

## <a name="versions-of-iis"></a><span data-ttu-id="fbc46-105">IIS 的版本</span><span class="sxs-lookup"><span data-stu-id="fbc46-105">Versions of IIS</span></span>

<span data-ttu-id="fbc46-106">可以在以下操作系统上的 IIS 版本上承载 WCF：</span><span class="sxs-lookup"><span data-stu-id="fbc46-106">WCF can be hosted on the following versions of IIS on the following operating systems:</span></span>

- <span data-ttu-id="fbc46-107">Windows XP SP2 上的 IIS 5.1。</span><span class="sxs-lookup"><span data-stu-id="fbc46-107">IIS 5.1 on Windows XP SP2.</span></span> <span data-ttu-id="fbc46-108">此环境可用于设计和开发 IIS 托管的应用程序，这些应用程序稍后部署在服务器操作系统（如 Windows Server 2003）中。</span><span class="sxs-lookup"><span data-stu-id="fbc46-108">This environment is useful for the design and development of IIS-hosted applications that are later deployed on a server operating system such as Windows Server 2003.</span></span>

- <span data-ttu-id="fbc46-109">IIS 6.0（在 Windows Server 2003 上）。</span><span class="sxs-lookup"><span data-stu-id="fbc46-109">IIS 6.0 on Windows Server 2003.</span></span> <span data-ttu-id="fbc46-110">IIS 6.0 提供了一个高级的进程模型，该模型提供经过改进的可伸缩性、可靠性和应用程序隔离。</span><span class="sxs-lookup"><span data-stu-id="fbc46-110">IIS 6.0 provides an advanced process model that offers improved scalability, reliability, and application isolation.</span></span> <span data-ttu-id="fbc46-111">此环境适用于仅使用 HTTP 通信的 WCF 服务的生产部署。</span><span class="sxs-lookup"><span data-stu-id="fbc46-111">This environment is suitable for production deployment of WCF services that use HTTP communication exclusively.</span></span>

- <span data-ttu-id="fbc46-112">Windows Vista 和 Windows Server 2008 上的 IIS 7.0。</span><span class="sxs-lookup"><span data-stu-id="fbc46-112">IIS 7.0 on Windows Vista and Windows Server 2008.</span></span> <span data-ttu-id="fbc46-113">IIS 7.0 提供与 IIS 6.0 相同的高级进程模型，但使用 Windows 进程激活服务 () ，以允许通过 HTTP 以外的协议进行激活和网络通信。</span><span class="sxs-lookup"><span data-stu-id="fbc46-113">IIS 7.0 provides the same advanced process model as IIS 6.0, but uses the Windows Process Activation Service (WAS) to allow activation and network communication over protocols other than HTTP.</span></span> <span data-ttu-id="fbc46-114">此环境适用于 WCF 服务的开发，这些服务通过 WCF (支持的任何网络协议进行通信，包括 HTTP、net.tcp、net.pipe 和 net.tcp) 。</span><span class="sxs-lookup"><span data-stu-id="fbc46-114">This environment is suitable for the development of WCF services that communicate over any network protocol supported by WCF (including HTTP, net.tcp, net.pipe, and net.msmq).</span></span> <span data-ttu-id="fbc46-115">有关 WAS 的详细信息，请参阅 [Windows 进程激活服务中的托管](hosting-in-windows-process-activation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="fbc46-115">For more information about WAS, see [Hosting in Windows Process Activation Service](hosting-in-windows-process-activation-service.md).</span></span>

- <span data-ttu-id="fbc46-116">[Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10)) 使用 IIS 7.0 和 Windows 进程激活服务 () 为 NET4 WCF 和 WF 服务提供丰富的应用程序宿主环境。</span><span class="sxs-lookup"><span data-stu-id="fbc46-116">[Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10)) works with IIS 7.0 and Windows Process Activation Service (WAS) to provide a rich application hosting environment for NET4 WCF and WF services.</span></span> <span data-ttu-id="fbc46-117">这些优点包括进程生命周期管理、进程回收、共享承载、快速失败保护、进程孤立、按需激活和运行状况监视。</span><span class="sxs-lookup"><span data-stu-id="fbc46-117">These benefits include process life-cycle management, process recycling, shared hosting, rapid failure protection, process orphaning, on-demand activation, and health monitoring.</span></span> <span data-ttu-id="fbc46-118">有关详细信息，请参阅 [Appfabric 托管功能](/previous-versions/appfabric/ee677189(v=azure.10)) 和 [appfabric 托管概念](/previous-versions/appfabric/ee677371(v=azure.10))。</span><span class="sxs-lookup"><span data-stu-id="fbc46-118">For detailed information, see [AppFabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10)) and [AppFabric Hosting Concepts](/previous-versions/appfabric/ee677371(v=azure.10)).</span></span>

## <a name="benefits-of-iis-hosting"></a><span data-ttu-id="fbc46-119">IIS 托管的优点</span><span class="sxs-lookup"><span data-stu-id="fbc46-119">Benefits of IIS hosting</span></span>

<span data-ttu-id="fbc46-120">在 IIS 中承载 WCF 服务有多个优点：</span><span class="sxs-lookup"><span data-stu-id="fbc46-120">Hosting WCF services in IIS has several benefits:</span></span>

- <span data-ttu-id="fbc46-121">IIS 中承载的 WCF 服务的部署和管理与任何其他类型的 IIS 应用程序（包括 ASP.NET 应用程序和 .ASMX）一样。</span><span class="sxs-lookup"><span data-stu-id="fbc46-121">WCF services hosted in IIS are deployed and managed like any other type of IIS application, including ASP.NET applications and ASMX.</span></span>

- <span data-ttu-id="fbc46-122">IIS 提供进程激活、运行状况管理和回收功能以提高承载的应用程序的可靠性。</span><span class="sxs-lookup"><span data-stu-id="fbc46-122">IIS provides process activation, health management, and recycling capabilities to increase the reliability of hosted applications.</span></span>

- <span data-ttu-id="fbc46-123">与 ASP.NET 一样，ASP.NET 中托管的 WCF 服务可以利用 ASP.NET 共享的托管模型，其中，多个应用程序驻留在常见的工作进程中，以提高服务器的密度和可伸缩性。</span><span class="sxs-lookup"><span data-stu-id="fbc46-123">Like ASP.NET, WCF services hosted in ASP.NET can take advantage of the ASP.NET shared hosting model where multiple applications reside in a common worker process for improved server density and scalability.</span></span>

- <span data-ttu-id="fbc46-124">在 IIS 中托管的 WCF 服务使用与 ASP.NET 2.0 相同的动态编译模型，从而简化了托管服务的开发和部署。</span><span class="sxs-lookup"><span data-stu-id="fbc46-124">WCF services hosted in IIS use the same dynamic compilation model as ASP.NET 2.0, which simplifies development and deployment of hosted services.</span></span>

<span data-ttu-id="fbc46-125">当决定在 IIS 中承载 WCF 服务时，请记住 IIS 5.1 和 IIS 6.0 仅限于 HTTP 通信，这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="fbc46-125">When deciding to host WCF services in IIS, it is important to remember that IIS 5.1 and IIS 6.0 are limited to HTTP communication only.</span></span> <span data-ttu-id="fbc46-126">有关选择宿主环境的详细信息，请参阅 [托管服务](../hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fbc46-126">For more information about choosing a hosting environment, see [Hosting Services](../hosting-services.md).</span></span>

## <a name="deploy-an-iis-hosted-wcf-service"></a><span data-ttu-id="fbc46-127">部署 IIS 承载的 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="fbc46-127">Deploy an IIS-hosted WCF service</span></span>

<span data-ttu-id="fbc46-128">开发和部署 IIS 承载的 WCF 服务包含以下任务：</span><span class="sxs-lookup"><span data-stu-id="fbc46-128">Developing and deploying an IIS-hosted WCF service consists of the following tasks:</span></span>

- <span data-ttu-id="fbc46-129">确保正确安装并注册了 IIS、ASP.NET、WCF 和 WCF HTTP 激活组件。</span><span class="sxs-lookup"><span data-stu-id="fbc46-129">Ensure that IIS, ASP.NET, WCF, and the WCF HTTP activation component are correctly installed and registered.</span></span>

- <span data-ttu-id="fbc46-130">创建新的 IIS 应用程序，或重复使用现有的 ASP.NET 应用程序。</span><span class="sxs-lookup"><span data-stu-id="fbc46-130">Create a new IIS application, or reuse an existing ASP.NET application.</span></span>

- <span data-ttu-id="fbc46-131">为 WCF 服务创建 .svc 文件。</span><span class="sxs-lookup"><span data-stu-id="fbc46-131">Create a .svc file for the WCF service.</span></span>

- <span data-ttu-id="fbc46-132">将服务实现部署到 IIS 应用程序。</span><span class="sxs-lookup"><span data-stu-id="fbc46-132">Deploy the service implementation to the IIS application.</span></span>

- <span data-ttu-id="fbc46-133">配置 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="fbc46-133">Configure the WCF service.</span></span>

<span data-ttu-id="fbc46-134">有关每项任务的讨论，请参阅 [部署 Internet Information Services 承载的 WCF 服务](deploying-an-internet-information-services-hosted-wcf-service.md)。</span><span class="sxs-lookup"><span data-stu-id="fbc46-134">For a discussion of each of these tasks, see [Deploying an Internet Information Services-Hosted WCF Service](deploying-an-internet-information-services-hosted-wcf-service.md).</span></span>

## <a name="wcf-services-and-aspnet"></a><span data-ttu-id="fbc46-135">WCF 服务和 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fbc46-135">WCF services and ASP.NET</span></span>

<span data-ttu-id="fbc46-136">WCF 服务可与 ASP.NET 或在 ASP.NET 兼容模式下并行托管，在此模式中，服务可充分利用 ASP.NET Web 应用程序平台提供的功能。</span><span class="sxs-lookup"><span data-stu-id="fbc46-136">WCF services can be hosted either side-by-side with ASP.NET or in ASP.NET Compatibility Mode in which services can take full advantage of features provided by the ASP.NET Web application platform.</span></span> <span data-ttu-id="fbc46-137">有关这些功能的讨论，请参阅 [WCF 服务和 ASP.NET](wcf-services-and-aspnet.md)。</span><span class="sxs-lookup"><span data-stu-id="fbc46-137">For a discussion of these features, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fbc46-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="fbc46-138">See also</span></span>

- [<span data-ttu-id="fbc46-139">使用 ServiceHostFactory 扩展宿主</span><span class="sxs-lookup"><span data-stu-id="fbc46-139">Extending Hosting Using ServiceHostFactory</span></span>](../extending/extending-hosting-using-servicehostfactory.md)
- [<span data-ttu-id="fbc46-140">部署承载于 Internet 信息服务中的 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="fbc46-140">Deploying an Internet Information Services-Hosted WCF Service</span></span>](deploying-an-internet-information-services-hosted-wcf-service.md)
- [<span data-ttu-id="fbc46-141">WCF 服务和 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fbc46-141">WCF Services and ASP.NET</span></span>](wcf-services-and-aspnet.md)
- [<span data-ttu-id="fbc46-142">Internet 信息服务承载最佳实践</span><span class="sxs-lookup"><span data-stu-id="fbc46-142">Internet Information Services Hosting Best Practices</span></span>](internet-information-services-hosting-best-practices.md)
- [<span data-ttu-id="fbc46-143">为 Windows Communication Foundation 配置 Internet Information Services 7.0</span><span class="sxs-lookup"><span data-stu-id="fbc46-143">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>](configuring-iis-for-wcf.md)
- <span data-ttu-id="fbc46-144">[Windows Server App Fabric 承载功能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="fbc46-144">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
