---
title: 面向 Azure .NET 开发人员的工具
description: 获取工具以通过 Windows、Linux 和 Mac 环境开始使用 Azure .NET 库。
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: fa645b152f15550b25a3542ba0cdbb43799536b9
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174819"
---
# <a name="azure-tools-for-developing-with-net"></a><span data-ttu-id="5d058-103">用于使用 .NET 进行开发的 Azure 工具</span><span class="sxs-lookup"><span data-stu-id="5d058-103">Azure tools for developing with .NET</span></span>

## <a name="sdk-downloads"></a><span data-ttu-id="5d058-104">SDK 下载</span><span class="sxs-lookup"><span data-stu-id="5d058-104">SDK downloads</span></span>

<span data-ttu-id="5d058-105">用于 .NET 的 Azure 库作为 [NuGet 程序包](https://www.nuget.org/packages?q=windowsazureofficial)实现。</span><span class="sxs-lookup"><span data-stu-id="5d058-105">Azure libraries for .NET are implemented as [NuGet packages](https://www.nuget.org/packages?q=windowsazureofficial).</span></span> <span data-ttu-id="5d058-106">若要查看 Azure 服务整理的参考文档，请参阅 [API 参考](/dotnet/api/overview/azure/?view=azure-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="5d058-106">See the [API Reference](/dotnet/api/overview/azure/?view=azure-dotnet) for reference documentation organized by Azure service.</span></span>

## <a name="development-tools"></a><span data-ttu-id="5d058-107">开发工具</span><span class="sxs-lookup"><span data-stu-id="5d058-107">Development tools</span></span>

<span data-ttu-id="5d058-108">Visual Studio 内置了用于许多 Azure 服务的工具。</span><span class="sxs-lookup"><span data-stu-id="5d058-108">Visual Studio has tooling for many Azure services built-in.</span></span> <span data-ttu-id="5d058-109">一些 Azure 服务有其他可用的工具或模拟器，例如 [Azure 存储资源管理器](https://azure.microsoft.com/features/storage-explorer/)。</span><span class="sxs-lookup"><span data-stu-id="5d058-109">Some Azure services have additional tools or emulators available, such as [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="5d058-110">如有必要，请参阅适用于你的 Azure 服务的文档，以获取其他工具的信息。</span><span class="sxs-lookup"><span data-stu-id="5d058-110">See the documentation for your Azure service for any additional tools, if necessary.</span></span>

<span data-ttu-id="5d058-111">在下面选择你的首选开发环境。</span><span class="sxs-lookup"><span data-stu-id="5d058-111">Select your preferred development environment below.</span></span>

## <a name="visual-studio-on-windows"></a>[<span data-ttu-id="5d058-112">Windows 上的 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5d058-112">Visual Studio on Windows</span></span>](#tab/vs)

<span data-ttu-id="5d058-113">Visual Studio 2017 版及更高版本针对 Azure 开发提供了内置支持。</span><span class="sxs-lookup"><span data-stu-id="5d058-113">Visual Studio version 2017 and later have built-in support for Azure development.</span></span> <span data-ttu-id="5d058-114">下面的步骤介绍了如何在 Visual Studio 中启动 Azure 开发支持。</span><span class="sxs-lookup"><span data-stu-id="5d058-114">The below steps describe enabling Azure development support in Visual Studio.</span></span>

<span data-ttu-id="5d058-115">对于 Visual Studio 2015 及更早版本，<a href="vs2015-install.md">请按照这些说明操作</a>。</span><span class="sxs-lookup"><span data-stu-id="5d058-115">For Visual Studio 2015 and earlier, <a href="vs2015-install.md">follow these instructions</a>.</span></span>

### <a name="step-1-download-visual-studio-2019"></a><span data-ttu-id="5d058-116">步骤 1：下载 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="5d058-116">Step 1: Download Visual Studio 2019</span></span>

<span data-ttu-id="5d058-117">如果已安装 Visual Studio 2019，则可跳过此步骤。</span><span class="sxs-lookup"><span data-stu-id="5d058-117">You can skip this step if you already have Visual Studio 2019 installed.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5d058-118">下载 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="5d058-118">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a><span data-ttu-id="5d058-119">步骤 2：安装两个 Azure 工作负荷</span><span class="sxs-lookup"><span data-stu-id="5d058-119">Step 2: Install the two Azure workloads</span></span>

<span data-ttu-id="5d058-120">在 Visual Studio 安装程序中，安装 Visual Studio（或修改现有安装）。</span><span class="sxs-lookup"><span data-stu-id="5d058-120">In the Visual Studio installer, install Visual Studio (or modify an existing installation).</span></span> <span data-ttu-id="5d058-121">确保已选择“Azure 开发”以及“ASP.NET 和 Web 开发”工作负荷。 </span><span class="sxs-lookup"><span data-stu-id="5d058-121">Make sure the *Azure development* and *ASP.NET and web development* workloads are selected.</span></span>

### <a name="step-3-develop-with-net-on-azure"></a><span data-ttu-id="5d058-122">步骤 3：在 Azure 上使用 .NET 进行开发</span><span class="sxs-lookup"><span data-stu-id="5d058-122">Step 3: Develop with .NET on Azure</span></span>

<span data-ttu-id="5d058-123">首先，[在 Azure 应用服务中部署第一个 ASP.NET Core Web 应用](/azure/app-service-web/app-service-web-get-started-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="5d058-123">Get started by [deploying your first ASP.NET Core web app on Azure App Service](/azure/app-service-web/app-service-web-get-started-dotnet).</span></span>

## <a name="visual-studio-code-cross-platform"></a>[<span data-ttu-id="5d058-124">Visual Studio Code（跨平台）</span><span class="sxs-lookup"><span data-stu-id="5d058-124">Visual Studio Code (cross-platform)</span></span>](#tab/vscode)

<span data-ttu-id="5d058-125">Visual Studio Code 提供了进行跨平台 Azure 开发所需的一切内容。</span><span class="sxs-lookup"><span data-stu-id="5d058-125">Visual Studio Code has everything you need for cross-platform Azure development.</span></span>

### <a name="step-1-download-the-net-core-sdk"></a><span data-ttu-id="5d058-126">步骤 1：下载 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="5d058-126">Step 1: Download the .NET Core SDK</span></span>

<span data-ttu-id="5d058-127">用于 .NET Core 应用的 SDK 和命令行工具。</span><span class="sxs-lookup"><span data-stu-id="5d058-127">The SDK and command-line tools for .NET Core apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5d058-128">下载 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="5d058-128">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a><span data-ttu-id="5d058-129">步骤 2：Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5d058-129">Step 2: Visual Studio Code</span></span>

<span data-ttu-id="5d058-130">在任何操作系统上编辑和调试 .NET Core 应用：Windows、Mac 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="5d058-130">Edit and debug .NET Core apps on any operating system: Windows, Mac, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5d058-131">下载 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5d058-131">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

### <a name="step-3-azure-tools-extension"></a><span data-ttu-id="5d058-132">步骤 3：Azure Tools 扩展</span><span class="sxs-lookup"><span data-stu-id="5d058-132">Step 3: Azure Tools extension</span></span>

<span data-ttu-id="5d058-133">在 Visual Studio Code 中安装 Azure Tools 扩展。</span><span class="sxs-lookup"><span data-stu-id="5d058-133">Install the Azure Tools extension in Visual Studio Code.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5d058-134">安装 Azure Tools 扩展</span><span class="sxs-lookup"><span data-stu-id="5d058-134">Install Azure Tools extension</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)

### <a name="step-4-develop-with-net-on-azure"></a><span data-ttu-id="5d058-135">步骤 4：在 Azure 上使用 .NET 进行开发</span><span class="sxs-lookup"><span data-stu-id="5d058-135">Step 4: Develop with .NET on Azure</span></span>

<span data-ttu-id="5d058-136">首先，[在 Linux 上的 Azure 应用服务中部署你的第一个 ASP.NET Core Web 应用](/azure/app-service/containers/quickstart-dotnetcore)。</span><span class="sxs-lookup"><span data-stu-id="5d058-136">Get started by [deploying your first ASP.NET Core web app on Azure App Service on Linux](/azure/app-service/containers/quickstart-dotnetcore).</span></span>

---
