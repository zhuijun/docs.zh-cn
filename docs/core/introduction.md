---
title: .NET Core 简介和概述
description: .NET Core 是一种高性能的模块化 .NET 实现，用于创建 Windows、Linux 和 macOS 应用。 了解 .NET Core 以开始使用。
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 350fd50bee3403a05d1c19c9a692535613b17498
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538271"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="f16a4-104">.NET Core 简介</span><span class="sxs-lookup"><span data-stu-id="f16a4-104">Introduction to .NET Core</span></span>

<span data-ttu-id="f16a4-105">[.NET Core](about.md) 是一个通用的[开放源代码](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)开发平台。</span><span class="sxs-lookup"><span data-stu-id="f16a4-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform.</span></span> <span data-ttu-id="f16a4-106">可以使用多种编程语言针对 x64、x86、ARM32 和 ARM64 处理器创建适用于 Windows、macOS 和 Linux 的 .NET Core 应用。</span><span class="sxs-lookup"><span data-stu-id="f16a4-106">You can create .NET Core apps for Windows, macOS, and Linux for x64, x86, ARM32, and ARM64 processors using multiple programming languages.</span></span> <span data-ttu-id="f16a4-107">为[云](/aspnet/core/)、[IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)、[客户端 UI](../desktop-wpf/overview/index.md) 和[机器学习](../machine-learning/index.yml)提供了框架和 API。</span><span class="sxs-lookup"><span data-stu-id="f16a4-107">Frameworks and APIs are provided for [cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [client UI](../desktop-wpf/overview/index.md), and [machine learning](../machine-learning/index.yml).</span></span>

<span data-ttu-id="f16a4-108">[下载 .NET Core SDK](https://dotnet.microsoft.com/download)，尝试在计算机上使用 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="f16a4-108">[Download the .NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your machine.</span></span> <span data-ttu-id="f16a4-109">最新版是 [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)。</span><span class="sxs-lookup"><span data-stu-id="f16a4-109">The latest version is [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

## <a name="download-net-core"></a><span data-ttu-id="f16a4-110">下载 .NET Core</span><span class="sxs-lookup"><span data-stu-id="f16a4-110">Download .NET Core</span></span>

<span data-ttu-id="f16a4-111">可以按下列方式获取 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="f16a4-111">You can get .NET Core in the following ways:</span></span>

* [<span data-ttu-id="f16a4-112">适用于 Windows 和 macOS 的安装程序</span><span class="sxs-lookup"><span data-stu-id="f16a4-112">Installers for Windows and macOS</span></span>](https://dotnet.microsoft.com/download)
* [<span data-ttu-id="f16a4-113">Linux 包</span><span class="sxs-lookup"><span data-stu-id="f16a4-113">Linux packages</span></span>](./install/linux.md)
* [<span data-ttu-id="f16a4-114">Docker 容器</span><span class="sxs-lookup"><span data-stu-id="f16a4-114">Docker containers</span></span>](https://hub.docker.com/_/microsoft-dotnet-core/)
* [<span data-ttu-id="f16a4-115">Zip 和 tarball</span><span class="sxs-lookup"><span data-stu-id="f16a4-115">Zips and tarballs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [<span data-ttu-id="f16a4-116">安装脚本</span><span class="sxs-lookup"><span data-stu-id="f16a4-116">Install scripts</span></span>](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [<span data-ttu-id="f16a4-117">发行说明</span><span class="sxs-lookup"><span data-stu-id="f16a4-117">Release notes</span></span>](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a><span data-ttu-id="f16a4-118">创建首个应用程序</span><span class="sxs-lookup"><span data-stu-id="f16a4-118">Create your first application</span></span>

<span data-ttu-id="f16a4-119">安装 .NET Core SDK 后，打开命令提示符。</span><span class="sxs-lookup"><span data-stu-id="f16a4-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="f16a4-120">使用以下命令创建并运行应用程序：</span><span class="sxs-lookup"><span data-stu-id="f16a4-120">Use the following commands to create and run an application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="f16a4-121">您应看到以下输出：</span><span class="sxs-lookup"><span data-stu-id="f16a4-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="contribute"></a><span data-ttu-id="f16a4-122">参与</span><span class="sxs-lookup"><span data-stu-id="f16a4-122">Contribute</span></span>

<span data-ttu-id="f16a4-123">.NET Core 是一个开放平台。</span><span class="sxs-lookup"><span data-stu-id="f16a4-123">.NET Core is an open platform.</span></span> <span data-ttu-id="f16a4-124">欢迎所有人参与。</span><span class="sxs-lookup"><span data-stu-id="f16a4-124">Everyone is welcome to participate.</span></span>

* <span data-ttu-id="f16a4-125">[开发人员社区](https://developercommunity.visualstudio.com/spaces/61/index.html)的文件产品问题。</span><span class="sxs-lookup"><span data-stu-id="f16a4-125">File product issues and questions at [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).</span></span>
* <span data-ttu-id="f16a4-126">产品贡献应该在一个项目存储库上进行，例如 [dotnet/runtime](https://github.com/dotnet/runtime)、[dotnet/sdk](https://github.com/dotnet/sdk)、[dotnet/rosyln](https://github.com/dotnet/roslyn) 或 [aspnetcore](https://github.com/dotnet/aspnetcore)。</span><span class="sxs-lookup"><span data-stu-id="f16a4-126">Product contributions should be made on one of the project repositories, such as [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn), or [aspnetcore](https://github.com/dotnet/aspnetcore).</span></span> <span data-ttu-id="f16a4-127">有关详细信息，请参阅 [.NET Core 存储库](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md)。</span><span class="sxs-lookup"><span data-stu-id="f16a4-127">For more information, see [.NET Core repos](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span></span>

## <a name="support"></a><span data-ttu-id="f16a4-128">支持</span><span class="sxs-lookup"><span data-stu-id="f16a4-128">Support</span></span>

<span data-ttu-id="f16a4-129">.NET Core 受 Windows、macOS 和 Linux 上的 Microsoft 和 Red Hat Enterprise Linux 上的 Red Hat 支持。</span><span class="sxs-lookup"><span data-stu-id="f16a4-129">.NET Core is supported by Microsoft on Windows, macOS, and Linux and by Red Hat on Red Hat Enterprise Linux.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f16a4-130">后续步骤</span><span class="sxs-lookup"><span data-stu-id="f16a4-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f16a4-131">.NET Core 教程</span><span class="sxs-lookup"><span data-stu-id="f16a4-131">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="f16a4-132">在浏览器中试用 .NET Core</span><span class="sxs-lookup"><span data-stu-id="f16a4-132">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
