---
title: .NET Core 和开放源代码
description: 阅读有关 .NET Core 的概述，它是 .NET Standard 的常规用途、模块化、跨平台和开放源代码实现。
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
ms.openlocfilehash: 08d30d047c25b3b6d681d72b46b81a0cb21f8e0a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622752"
---
# <a name="net-core-and-open-source"></a><span data-ttu-id="fcd4e-103">.NET Core 和开放源代码</span><span class="sxs-lookup"><span data-stu-id="fcd4e-103">.NET Core and open source</span></span>

<span data-ttu-id="fcd4e-104">本文提供有关 .NET Core 概念的简要概述并展示如何查找更多信息。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-104">This article provides a brief overview of what .NET Core is and shows how you can find more information.</span></span> <span data-ttu-id="fcd4e-105">若要查找有关 .NET Core 的完整文档列表，请访问 [.NET Core 指南](../../core/index.yml)。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-105">To find the complete list of documentation for .NET Core, visit the [.NET Core guide](../../core/index.yml).</span></span>

## <a name="what-is-net-core"></a><span data-ttu-id="fcd4e-106">.NET Core 是什么？</span><span class="sxs-lookup"><span data-stu-id="fcd4e-106">What is .NET Core?</span></span>  

<span data-ttu-id="fcd4e-107">.NET Core 是 .NET Standard 的常规用途、模块化、跨平台和开放源代码实现。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-107">.NET Core is a general purpose, modular, cross-platform, and open-source implementation of the .NET Standard.</span></span> <span data-ttu-id="fcd4e-108">它包含 .NET Framework 这样的许多相同 API（但 .NET Core 是较小的集）并包括支持不同操作系统和芯片目标的运行时、框架、编译器和工具组件。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-108">It contains many of the same APIs as the .NET Framework (but .NET Core is a smaller set) and includes runtime, framework, compiler, and tools components that support a variety of operating systems and chip targets.</span></span> <span data-ttu-id="fcd4e-109">.NET Core 实现主要由 ASP.NET Core 工作负载驱动，但同时也由拥有一个更现代的实现这一需求和愿望驱动。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-109">The .NET Core implementation was primarily driven by the ASP.NET Core workloads but also by the need and desire to have a more modern implementation.</span></span> <span data-ttu-id="fcd4e-110">它可以用于设备、云和嵌入式/IoT 方案。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-110">It can be used in device, cloud, and embedded/IoT scenarios.</span></span>  
  
<span data-ttu-id="fcd4e-111">若要开始使用 .NET Core，请访问 .NET 教程 [Hello World 10 分钟入门](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-111">To get started with .NET Core, visit the .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).</span></span>  
  
<span data-ttu-id="fcd4e-112">下面列出了 .NET Core 的主要特征：</span><span class="sxs-lookup"><span data-stu-id="fcd4e-112">The main characteristics of .NET Core are:</span></span>
  
- <span data-ttu-id="fcd4e-113">**跨平台：** .NET Core 提供了实现所需应用功能的关键功能，并且可以重用代码而不考虑平台目标。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-113">**Cross-platform:** .NET Core provides key functionality to implement the app features you need and reuse this code regardless of your platform target.</span></span> <span data-ttu-id="fcd4e-114">它当前支持三种主要的操作系统 (OS)：Windows、Linux 和 macOS。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-114">It currently supports three main operating systems (OS): Windows, Linux, and macOS.</span></span> <span data-ttu-id="fcd4e-115">可以编写无需修改即可跨受支持操作系统运行的应用和库。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-115">You can write apps and libraries that run unmodified across supported operating systems.</span></span> <span data-ttu-id="fcd4e-116">若要查看受支持操作系统的列表，请访问 [.NET Core 路线图](https://github.com/dotnet/core/blob/master/roadmap.md)。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-116">To see the list of supported operating systems, visit [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md).</span></span>
  
- <span data-ttu-id="fcd4e-117">**开放源代码：** .NET Core 是 [.NET Foundation](https://www.dotnetfoundation.org/) 管理下的很多项目中的一个，并在 [GitHub](https://github.com/) 上提供。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-117">**Open source:** .NET Core is one of the many projects under the stewardship of the [.NET Foundation](https://www.dotnetfoundation.org/) and is available on [GitHub](https://github.com/).</span></span> <span data-ttu-id="fcd4e-118">作为开放源代码项目，.NET Core 促使开发过程更加透明并能提升社区的活跃度及参与度。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-118">As an open-source project, .NET Core promotes a more transparent development process and an active and engaged community.</span></span>  
  
- <span data-ttu-id="fcd4e-119">**灵活部署：** 部署应用有两种主要方法：依赖框架的部署或独立部署。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-119">**Flexible deployment:** there are two main ways to deploy your app: framework-dependent deployment or self-contained deployment.</span></span> <span data-ttu-id="fcd4e-120">使用依赖框架的部署时，仅安装应用和第三方依赖关系，而应用依赖于存在系统范围版本的 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-120">With framework-dependent deployment, only your app and third-party dependencies are installed and your app depends on a system-wide version of .NET Core to be present.</span></span> <span data-ttu-id="fcd4e-121">使用独立部署时，用于构建应用程序的 .NET Core 版本随应用和第三方依赖关系一同部署，并可与其他版本并行运行。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-121">With self-contained deployment, the .NET Core version used to build your application is also deployed along with your app and third-party dependencies and can run side by side with other versions.</span></span> <span data-ttu-id="fcd4e-122">有关详细信息，请参阅 [.NET Core 应用程序部署](../../core/deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-122">For more information, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>

- <span data-ttu-id="fcd4e-123">模块化：.NET Core 为模块化，因为它通过 NuGet 以较小的程序集包发布。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-123">**Modular:** .NET Core is modular because it's released through NuGet in smaller assembly packages.</span></span> <span data-ttu-id="fcd4e-124">与包含了大部分核心功能的大型程序集不同，.NET Core 作为以功能为中心的小型数据包提供。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-124">Rather than one large assembly that contains most of the core functionality, .NET Core is made available as smaller, feature-centric packages.</span></span> <span data-ttu-id="fcd4e-125">这种模块化为我们提供了更加灵活的开发模型，允许优化应用使其仅包含所需的 NuGet 程序包。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-125">This modularity enables a more agile development model for us and allows you to optimize your app to include just the NuGet packages you need.</span></span> <span data-ttu-id="fcd4e-126">较小的应用图面区域的优势包括：提升安全性、减少维护、提高性能并采用按使用情况付费的模式降低成本。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-126">The benefits of a smaller app surface area include tighter security, reduced servicing, improved performance, and decreased costs in a pay-for-what-you-use model.</span></span>  
  
## <a name="the-net-core-platform"></a><span data-ttu-id="fcd4e-127">.NET Core 平台</span><span class="sxs-lookup"><span data-stu-id="fcd4e-127">The .NET Core platform</span></span>
  
<span data-ttu-id="fcd4e-128">.NET Core 平台由一些组件构成，其中包括托管的编译器、运行时、基类库和大量应用程序模型，如 ASP.NET Core。</span><span class="sxs-lookup"><span data-stu-id="fcd4e-128">The .NET Core platform is made up of several components, including the managed compilers, the runtime, the base class libraries, and numerous application models, such as ASP.NET Core.</span></span> <span data-ttu-id="fcd4e-129">可以通过访问以下 [GitHub](https://github.com/) 存储库来了解更多关于不同组件的信息并参与进来：</span><span class="sxs-lookup"><span data-stu-id="fcd4e-129">You can learn more about the different components and get engaged by visiting the following [GitHub](https://github.com/) repos:</span></span>  
  
- [<span data-ttu-id="fcd4e-130">.NET Core 主页</span><span class="sxs-lookup"><span data-stu-id="fcd4e-130">.NET Core home</span></span>](https://github.com/dotnet/core)  
  
- [<span data-ttu-id="fcd4e-131">运行时 - .NET Core 平台和运行时</span><span class="sxs-lookup"><span data-stu-id="fcd4e-131">Runtime - .NET Core platform and runtime</span></span>](https://github.com/dotnet/runtime)  
  
- [<span data-ttu-id="fcd4e-132">CLI - .NET Core command-line tools</span><span class="sxs-lookup"><span data-stu-id="fcd4e-132">CLI - .NET Core command-line tools</span></span>](https://github.com/dotnet/cli)  
  
- [<span data-ttu-id="fcd4e-133">Roslyn - .NET Compiler Platform</span><span class="sxs-lookup"><span data-stu-id="fcd4e-133">Roslyn - .NET Compiler Platform</span></span>](https://github.com/dotnet/roslyn)  
  
- [<span data-ttu-id="fcd4e-134">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fcd4e-134">ASP.NET Core</span></span>](https://github.com/dotnet/aspnetcore)  
  
## <a name="see-also"></a><span data-ttu-id="fcd4e-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="fcd4e-135">See also</span></span>

- [<span data-ttu-id="fcd4e-136">.NET 教程 - Hello World 10 分钟入门</span><span class="sxs-lookup"><span data-stu-id="fcd4e-136">.NET tutorial - Hello World in 10 minutes</span></span>](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [<span data-ttu-id="fcd4e-137">.NET Core 指南</span><span class="sxs-lookup"><span data-stu-id="fcd4e-137">.NET Core guide</span></span>](../../core/index.yml)
- [<span data-ttu-id="fcd4e-138">ASP.NET Core 文档</span><span class="sxs-lookup"><span data-stu-id="fcd4e-138">ASP.NET Core docs</span></span>](/aspnet/core/)
