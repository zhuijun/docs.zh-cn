---
title: 在 macOS 上安装 .NET Core
description: 了解可在其上安装 .NET Core 的 macOS 版本。
author: adegeo
ms.author: adegeo
ms.date: 06/25/2020
ms.openlocfilehash: 2900d98dbd30c51f689cdce37ea273ccc4f598b5
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/14/2020
ms.locfileid: "86308918"
---
# <a name="install-net-core-on-macos"></a><span data-ttu-id="d3d09-103">在 macOS 上安装 .NET Core</span><span class="sxs-lookup"><span data-stu-id="d3d09-103">Install .NET Core on macOS</span></span>

> [!div class="op_single_selector"]
>
> - [在 Windows 上安装](windows.md)
> - [在 macOS 上安装](macos.md)
> - [在 Linux 上安装](linux.md)

<span data-ttu-id="d3d09-107">在本文中，你将了解如何在 macOS 上安装 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="d3d09-107">In this article, you'll learn how to install .NET Core on macOS.</span></span> <span data-ttu-id="d3d09-108">.NET Core 由运行时和 SDK 组成。</span><span class="sxs-lookup"><span data-stu-id="d3d09-108">.NET Core is made up of the runtime and the SDK.</span></span> <span data-ttu-id="d3d09-109">运行时用于运行 .NET Core 应用，应用可能包含也可能不包含它。</span><span class="sxs-lookup"><span data-stu-id="d3d09-109">The runtime is used to run a .NET Core app and may or may not be included with the app.</span></span> <span data-ttu-id="d3d09-110">SDK 用于创建 .NET Core 应用和库。</span><span class="sxs-lookup"><span data-stu-id="d3d09-110">The SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="d3d09-111">.NET Core 运行时始终随 SDK 一起安装。</span><span class="sxs-lookup"><span data-stu-id="d3d09-111">The .NET Core runtime is always installed with the SDK.</span></span>

<span data-ttu-id="d3d09-112">最新版本的 .NET Core 是 3.1。</span><span class="sxs-lookup"><span data-stu-id="d3d09-112">The latest version of .NET Core is 3.1.</span></span>

> [!div class="button"]
> [<span data-ttu-id="d3d09-113">下载 .NET Core</span><span class="sxs-lookup"><span data-stu-id="d3d09-113">Download .NET Core</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="d3d09-114">支持的版本</span><span class="sxs-lookup"><span data-stu-id="d3d09-114">Supported releases</span></span>

<span data-ttu-id="d3d09-115">下表列出了当前支持的 .NET Core 版本以及支持它们的 macOS 版本。</span><span class="sxs-lookup"><span data-stu-id="d3d09-115">The following table is a list of currently supported .NET Core releases and the versions of macOS they're supported on.</span></span> <span data-ttu-id="d3d09-116">无论哪个 [.NET Core 版本达到支持终止](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)，仍支持这些版本。</span><span class="sxs-lookup"><span data-stu-id="d3d09-116">These versions remain supported either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

- <span data-ttu-id="d3d09-117">✔️ 指示 .NET Core 版本仍受支持。</span><span class="sxs-lookup"><span data-stu-id="d3d09-117">A ✔️ indicates that the version of .NET Core is still supported.</span></span>
- <span data-ttu-id="d3d09-118">❌ 指示 .NET Core 版本不受支持。</span><span class="sxs-lookup"><span data-stu-id="d3d09-118">A ❌ indicates that the version of .NET Core isn't supported.</span></span>

| <span data-ttu-id="d3d09-119">操作系统</span><span class="sxs-lookup"><span data-stu-id="d3d09-119">Operating System</span></span>          | <span data-ttu-id="d3d09-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d3d09-120">.NET Core 2.1</span></span> | <span data-ttu-id="d3d09-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="d3d09-121">.NET Core 3.1</span></span> | <span data-ttu-id="d3d09-122">.NET 5 预览版</span><span class="sxs-lookup"><span data-stu-id="d3d09-122">.NET 5 Preview</span></span> |
|---------------------------|---------------|---------------|----------------|
| <span data-ttu-id="d3d09-123">macOS 10.15“Catalina”</span><span class="sxs-lookup"><span data-stu-id="d3d09-123">macOS 10.15 "Catalina"</span></span>    | <span data-ttu-id="d3d09-124">✔️ 2.1（[发行说明][release-notes-21]）</span><span class="sxs-lookup"><span data-stu-id="d3d09-124">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="d3d09-125">✔️ 3.1（[发行说明][release-notes-31]）</span><span class="sxs-lookup"><span data-stu-id="d3d09-125">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="d3d09-126">✔️ 5.0 预览版（[发行说明][release-notes-50]）</span><span class="sxs-lookup"><span data-stu-id="d3d09-126">✔️ 5.0 Preview ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="d3d09-127">macOS 10.14“Mojave”</span><span class="sxs-lookup"><span data-stu-id="d3d09-127">macOS 10.14 "Mojave"</span></span>      | <span data-ttu-id="d3d09-128">✔️ 2.1（[发行说明][release-notes-21]）</span><span class="sxs-lookup"><span data-stu-id="d3d09-128">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="d3d09-129">✔️ 3.1（[发行说明][release-notes-31]）</span><span class="sxs-lookup"><span data-stu-id="d3d09-129">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="d3d09-130">✔️ 5.0 预览版（[发行说明][release-notes-50]）</span><span class="sxs-lookup"><span data-stu-id="d3d09-130">✔️ 5.0 Preview ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="d3d09-131">macOS 10.13“High Sierra”</span><span class="sxs-lookup"><span data-stu-id="d3d09-131">macOS 10.13 "High Sierra"</span></span> | <span data-ttu-id="d3d09-132">✔️ 2.1（[发行说明][release-notes-21]）</span><span class="sxs-lookup"><span data-stu-id="d3d09-132">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="d3d09-133">✔️ 3.1（[发行说明][release-notes-31]）</span><span class="sxs-lookup"><span data-stu-id="d3d09-133">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="d3d09-134">✔️ 5.0 预览版（[发行说明][release-notes-50]）</span><span class="sxs-lookup"><span data-stu-id="d3d09-134">✔️ 5.0 Preview ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="d3d09-135">macOS 10.12“Sierra”</span><span class="sxs-lookup"><span data-stu-id="d3d09-135">macOS 10.12 "Sierra"</span></span>      | <span data-ttu-id="d3d09-136">✔️ 2.1（[发行说明][release-notes-21]）</span><span class="sxs-lookup"><span data-stu-id="d3d09-136">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="d3d09-137">❌ 3.1（[发行说明][release-notes-31]）</span><span class="sxs-lookup"><span data-stu-id="d3d09-137">❌ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="d3d09-138">❌ 5.0 预览版（[发行说明][release-notes-50]）</span><span class="sxs-lookup"><span data-stu-id="d3d09-138">❌ 5.0 Preview ([Release notes][release-notes-50])</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="d3d09-139">不支持的版本</span><span class="sxs-lookup"><span data-stu-id="d3d09-139">Unsupported releases</span></span>

<span data-ttu-id="d3d09-140">以下 .NET Core 版本 ❌ 不再受支持。</span><span class="sxs-lookup"><span data-stu-id="d3d09-140">The following versions of .NET Core are ❌ no longer supported.</span></span> <span data-ttu-id="d3d09-141">这些版本的下载仍保持发布状态：</span><span class="sxs-lookup"><span data-stu-id="d3d09-141">The downloads for these still remain published:</span></span>

- <span data-ttu-id="d3d09-142">3.0（[发行说明][release-notes-30]）</span><span class="sxs-lookup"><span data-stu-id="d3d09-142">3.0 ([Release notes][release-notes-30])</span></span>
- <span data-ttu-id="d3d09-143">2.2（[发行说明][release-notes-22]）</span><span class="sxs-lookup"><span data-stu-id="d3d09-143">2.2 ([Release notes][release-notes-22])</span></span>
- <span data-ttu-id="d3d09-144">2.0（[发行说明][release-notes-20]）</span><span class="sxs-lookup"><span data-stu-id="d3d09-144">2.0 ([Release notes][release-notes-20])</span></span>

## <a name="runtime-information"></a><span data-ttu-id="d3d09-145">运行时信息</span><span class="sxs-lookup"><span data-stu-id="d3d09-145">Runtime information</span></span>

<span data-ttu-id="d3d09-146">运行时用于运行使用 .NET Core 创建的应用。</span><span class="sxs-lookup"><span data-stu-id="d3d09-146">The runtime is used to run apps created with .NET Core.</span></span> <span data-ttu-id="d3d09-147">应用作者发布应用时，可以在其应用中包含运行时。</span><span class="sxs-lookup"><span data-stu-id="d3d09-147">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="d3d09-148">如果作者未包含运行时，则由用户安装运行时。</span><span class="sxs-lookup"><span data-stu-id="d3d09-148">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="d3d09-149">可以在 macOS 上安装三个不同的运行时：</span><span class="sxs-lookup"><span data-stu-id="d3d09-149">There are three different runtimes you can install on macOS:</span></span>

<span data-ttu-id="d3d09-150">*ASP.NET Core 运行时*</span><span class="sxs-lookup"><span data-stu-id="d3d09-150">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="d3d09-151">运行 ASP.NET Core 应用。</span><span class="sxs-lookup"><span data-stu-id="d3d09-151">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="d3d09-152">包括 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="d3d09-152">Includes the .NET Core runtime.</span></span>

<span data-ttu-id="d3d09-153">*.NET Core 运行时*</span><span class="sxs-lookup"><span data-stu-id="d3d09-153">*.NET Core runtime*</span></span>\
<span data-ttu-id="d3d09-154">此运行时是最简单的运行时，不包括任何其他运行时。</span><span class="sxs-lookup"><span data-stu-id="d3d09-154">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="d3d09-155">强烈建议安装 ASP.NET Core 运行时，以最大限度地提升与 .NET Core 应用的兼容性。</span><span class="sxs-lookup"><span data-stu-id="d3d09-155">It's highly recommended that you install *ASP.NET Core runtime* for the best compatibility with .NET Core apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="d3d09-156">下载 .NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="d3d09-156">Download .NET Core Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="d3d09-157">SDK 信息</span><span class="sxs-lookup"><span data-stu-id="d3d09-157">SDK information</span></span>

<span data-ttu-id="d3d09-158">SDK 用于生成和发布 .NET Core 应用和库。</span><span class="sxs-lookup"><span data-stu-id="d3d09-158">The SDK is used to build and publish .NET Core apps and libraries.</span></span> <span data-ttu-id="d3d09-159">安装 SDK 会包含两个[运行时](#runtime-information)：ASP.NET Core 和 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="d3d09-159">Installing the SDK includes both [runtimes](#runtime-information): ASP.NET Core and .NET Core.</span></span>

> [!div class="button"]
> [<span data-ttu-id="d3d09-160">下载 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="d3d09-160">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a><span data-ttu-id="d3d09-161">依赖项</span><span class="sxs-lookup"><span data-stu-id="d3d09-161">Dependencies</span></span>

<span data-ttu-id="d3d09-162">以下 macOS 版本支持 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="d3d09-162">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="d3d09-163">`+` 表示最低版本。</span><span class="sxs-lookup"><span data-stu-id="d3d09-163">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="d3d09-164">.NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="d3d09-164">.NET Core Version</span></span> | <span data-ttu-id="d3d09-165">macOS</span><span class="sxs-lookup"><span data-stu-id="d3d09-165">macOS</span></span>                 | <span data-ttu-id="d3d09-166">体系结构</span><span class="sxs-lookup"><span data-stu-id="d3d09-166">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="d3d09-167">3.1</span><span class="sxs-lookup"><span data-stu-id="d3d09-167">3.1</span></span>               | <span data-ttu-id="d3d09-168">High Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="d3d09-168">High Sierra (10.13+)</span></span>  | <span data-ttu-id="d3d09-169">X64</span><span class="sxs-lookup"><span data-stu-id="d3d09-169">x64</span></span> | [<span data-ttu-id="d3d09-170">详细信息</span><span class="sxs-lookup"><span data-stu-id="d3d09-170">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="d3d09-171">3.0</span><span class="sxs-lookup"><span data-stu-id="d3d09-171">3.0</span></span>               | <span data-ttu-id="d3d09-172">High Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="d3d09-172">High Sierra (10.13+)</span></span>  | <span data-ttu-id="d3d09-173">X64</span><span class="sxs-lookup"><span data-stu-id="d3d09-173">x64</span></span> | [<span data-ttu-id="d3d09-174">详细信息</span><span class="sxs-lookup"><span data-stu-id="d3d09-174">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="d3d09-175">2.2</span><span class="sxs-lookup"><span data-stu-id="d3d09-175">2.2</span></span>               | <span data-ttu-id="d3d09-176">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="d3d09-176">Sierra (10.12+)</span></span>       | <span data-ttu-id="d3d09-177">X64</span><span class="sxs-lookup"><span data-stu-id="d3d09-177">x64</span></span> | [<span data-ttu-id="d3d09-178">详细信息</span><span class="sxs-lookup"><span data-stu-id="d3d09-178">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="d3d09-179">2.1</span><span class="sxs-lookup"><span data-stu-id="d3d09-179">2.1</span></span>               | <span data-ttu-id="d3d09-180">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="d3d09-180">Sierra (10.12+)</span></span>       | <span data-ttu-id="d3d09-181">X64</span><span class="sxs-lookup"><span data-stu-id="d3d09-181">x64</span></span> | [<span data-ttu-id="d3d09-182">详细信息</span><span class="sxs-lookup"><span data-stu-id="d3d09-182">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="d3d09-183">自 macOS Catalina（版本10.15）开始，所有在 2019 年 6 月 1 日之后生成并使用开发者 ID 扩散的软件都必须经过公证。</span><span class="sxs-lookup"><span data-stu-id="d3d09-183">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="d3d09-184">此要求应用于 .NET Core 运行时、.NET Core SDK 以及使用 .NET Core 创建的软件。</span><span class="sxs-lookup"><span data-stu-id="d3d09-184">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="d3d09-185">自 2020 年 2 月 18 日起，.NET Core（运行时和 SDK）版本 3.1、3.0 和 2.1 的安装程序都已经过公证。</span><span class="sxs-lookup"><span data-stu-id="d3d09-185">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="d3d09-186">以前发布的版本没有经过公证。</span><span class="sxs-lookup"><span data-stu-id="d3d09-186">Prior released versions aren't notarized.</span></span> <span data-ttu-id="d3d09-187">如果运行未经过公证的应用，将看到类似于下图的错误：</span><span class="sxs-lookup"><span data-stu-id="d3d09-187">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![macOS Catalina 公证警报](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="d3d09-189">若要详细了解强制执行的公证要求对 .NET Core 和 .NET Core 应用的影响，请参阅[处理 macOS Catalina 公证](macos-notarization-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="d3d09-189">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="d3d09-190">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="d3d09-190">libgdiplus</span></span>

<span data-ttu-id="d3d09-191">使用 System.Drawing.Common 程序集的 .NET Core 应用程序要求安装 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="d3d09-191">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="d3d09-192">获取 libgdiplus 的一个简单方法是使用适用于 macOS 的 [Homebrew (“brew”)](https://brew.sh/) 包。</span><span class="sxs-lookup"><span data-stu-id="d3d09-192">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="d3d09-193">在安装 brew 后，通过在终端（命令）提示符处执行以下命令来安装 libgdiplus：</span><span class="sxs-lookup"><span data-stu-id="d3d09-193">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a><span data-ttu-id="d3d09-194">使用安装程序安装</span><span class="sxs-lookup"><span data-stu-id="d3d09-194">Install with an installer</span></span>

<span data-ttu-id="d3d09-195">macOS 具有独立的安装程序，可用于安装 .NET Core 3.1 SDK：</span><span class="sxs-lookup"><span data-stu-id="d3d09-195">macOS has standalone installers that can be used to install the .NET Core 3.1 SDK:</span></span>

- [<span data-ttu-id="d3d09-196">x64（64 位）CPU</span><span class="sxs-lookup"><span data-stu-id="d3d09-196">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="d3d09-197">下载并手动安装</span><span class="sxs-lookup"><span data-stu-id="d3d09-197">Download and manually install</span></span>

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="d3d09-198">除了使用适用于 .NET Core 的 macOS 安装程序，还可以下载并手动安装 SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="d3d09-198">As an alternative to the macOS installers for .NET Core, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="d3d09-199">手动安装通常作为持续集成测试的一部分执行。</span><span class="sxs-lookup"><span data-stu-id="d3d09-199">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="d3d09-200">对于开发人员或用户，一般使用[安装程序](https://dotnet.microsoft.com/download/dotnet-core)会更好。</span><span class="sxs-lookup"><span data-stu-id="d3d09-200">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="d3d09-201">如果安装 .NET Core SDK，则无需安装相应的运行时。</span><span class="sxs-lookup"><span data-stu-id="d3d09-201">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="d3d09-202">首先，从以下站点之一下载 SDK 或运行时的二进制版本：</span><span class="sxs-lookup"><span data-stu-id="d3d09-202">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="d3d09-203">✔️ [.NET 5.0 预览版下载](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="d3d09-203">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="d3d09-204">✔️ [.NET Core 3.1 下载](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="d3d09-204">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="d3d09-205">✔️ [.NET Core 2.1 下载](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="d3d09-205">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="d3d09-206">所有 .NET Core 下载项</span><span class="sxs-lookup"><span data-stu-id="d3d09-206">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="d3d09-207">接下来，提取已下载的文件并使用 `export` 命令设置 .NET Core 使用的变量，然后确保 .NET Core 在 PATH 中。</span><span class="sxs-lookup"><span data-stu-id="d3d09-207">Next, extract the downloaded file and use the `export` command to set variables used by .NET Core and then ensure .NET Core is in PATH.</span></span>

<span data-ttu-id="d3d09-208">若要提取运行时并使 .NET Core CLI 命令可用于终端，请先下载 .NET Core 二进制版本。</span><span class="sxs-lookup"><span data-stu-id="d3d09-208">To extract the runtime and make the .NET Core CLI commands available at the terminal, first download a .NET Core binary release.</span></span> <span data-ttu-id="d3d09-209">然后，打开终端并从保存文件的目录运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="d3d09-209">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="d3d09-210">根据下载内容，存档文件名称可能不同。</span><span class="sxs-lookup"><span data-stu-id="d3d09-210">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="d3d09-211">**使用以下命令来提取运行时**：</span><span class="sxs-lookup"><span data-stu-id="d3d09-211">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.5-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="d3d09-212">**使用以下命令来提取 SDK**：</span><span class="sxs-lookup"><span data-stu-id="d3d09-212">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="d3d09-213">前面的 `export` 命令只会使 .NET Core CLI 命令对运行它的终端会话可用。</span><span class="sxs-lookup"><span data-stu-id="d3d09-213">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="d3d09-214">你可以编辑 shell 配置文件，永久地添加这些命令。</span><span class="sxs-lookup"><span data-stu-id="d3d09-214">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="d3d09-215">Linux 提供了许多不同的 shell，每个都有不同的配置文件。</span><span class="sxs-lookup"><span data-stu-id="d3d09-215">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="d3d09-216">例如：</span><span class="sxs-lookup"><span data-stu-id="d3d09-216">For example:</span></span>
>
> - <span data-ttu-id="d3d09-217">**Bash Shell**：~/.bash_profile、~/.bashrc</span><span class="sxs-lookup"><span data-stu-id="d3d09-217">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="d3d09-218">**Korn Shell**：~/.kshrc 或 .profile</span><span class="sxs-lookup"><span data-stu-id="d3d09-218">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="d3d09-219">**Z Shell**：~/.zshrc 或 .zprofile</span><span class="sxs-lookup"><span data-stu-id="d3d09-219">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="d3d09-220">为 shell 编辑相应的源文件，并将 `:$HOME/dotnet` 添加到现有 `PATH` 语句的末尾。</span><span class="sxs-lookup"><span data-stu-id="d3d09-220">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="d3d09-221">如果不包含 `PATH` 语句，则使用 `export PATH=$PATH:$HOME/dotnet` 添加新行。</span><span class="sxs-lookup"><span data-stu-id="d3d09-221">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="d3d09-222">另外，将 `export DOTNET_ROOT=$HOME/dotnet` 添加至文件的末尾。</span><span class="sxs-lookup"><span data-stu-id="d3d09-222">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="d3d09-223">使用此方法可以将不同的版本安装到不同的位置，并明确选择应用程序要使用的对应版本。</span><span class="sxs-lookup"><span data-stu-id="d3d09-223">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="d3d09-224">使用 Visual Studio for Mac 安装</span><span class="sxs-lookup"><span data-stu-id="d3d09-224">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="d3d09-225">在选定“.NET Core”工作负载时，使用 Visual Studio for Mac 安装 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="d3d09-225">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="d3d09-226">若要开始在 macOS 上进行 .NET Core 开发，请参阅[安装 Visual Studio 2019 for Mac](/visualstudio/mac/installation)。</span><span class="sxs-lookup"><span data-stu-id="d3d09-226">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span> <span data-ttu-id="d3d09-227">对于最新的版本 .NET Core 3.1，则必须使用 Visual Studio for Mac 8.4 预览版。</span><span class="sxs-lookup"><span data-stu-id="d3d09-227">For the latest release, .NET Core 3.1, you must use the Visual Studio for Mac 8.4 Preview.</span></span>

<span data-ttu-id="d3d09-228">[![具有 .NET Core 工作负载功能的 macOS Visual Studio 2019 for Mac](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="d3d09-228">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="d3d09-229">随 Visual Studio Code 一起安装</span><span class="sxs-lookup"><span data-stu-id="d3d09-229">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="d3d09-230">Visual Studio Code 是一个功能强大的轻量级源代码编辑器，可在桌面上运行。</span><span class="sxs-lookup"><span data-stu-id="d3d09-230">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="d3d09-231">Visual Studio Code 适用于 Windows、macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="d3d09-231">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="d3d09-232">虽然 Visual Studio Code 不像 Visual Studio 一样附带自动的 .NET Core 安装程序，但添加 .NET Core 支持非常简单。</span><span class="sxs-lookup"><span data-stu-id="d3d09-232">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="d3d09-233">[下载并安装 Visual Studio Code](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="d3d09-233">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="d3d09-234">[下载并安装 .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="d3d09-234">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="d3d09-235">[从 Visual Studio Code 市场安装 C# 扩展](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)。</span><span class="sxs-lookup"><span data-stu-id="d3d09-235">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="install-with-bash-automation"></a><span data-ttu-id="d3d09-236">使用 Bash 自动化安装</span><span class="sxs-lookup"><span data-stu-id="d3d09-236">Install with bash automation</span></span>

<span data-ttu-id="d3d09-237">[dotnet-install 脚本](../tools/dotnet-install-script.md)用于运行时的自动化和非管理员安装。</span><span class="sxs-lookup"><span data-stu-id="d3d09-237">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="d3d09-238">可从 [dotnet-install 脚本引用页](../tools/dotnet-install-script.md)下载该脚本。</span><span class="sxs-lookup"><span data-stu-id="d3d09-238">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="d3d09-239">此脚本默认安装最新的[长期支持 (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，即 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="d3d09-239">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="d3d09-240">可通过指定 `current` 开关以选择特定版本。</span><span class="sxs-lookup"><span data-stu-id="d3d09-240">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="d3d09-241">包括 `runtime` 开关以安装运行时。</span><span class="sxs-lookup"><span data-stu-id="d3d09-241">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="d3d09-242">否则，该脚本安装 [SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="d3d09-242">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="d3d09-243">以上命令安装 ASP.NET Core 运行时，用于实现最大的兼容性。</span><span class="sxs-lookup"><span data-stu-id="d3d09-243">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="d3d09-244">ASP.NET Core 运行时还包括标准 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="d3d09-244">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="docker"></a><span data-ttu-id="d3d09-245">Docker</span><span class="sxs-lookup"><span data-stu-id="d3d09-245">Docker</span></span>

<span data-ttu-id="d3d09-246">容器提供了一种将应用程序与主机系统的其余部分隔离的轻量级方法。</span><span class="sxs-lookup"><span data-stu-id="d3d09-246">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="d3d09-247">同一计算机上的容器只共享内核，并使用为应用程序提供的资源。</span><span class="sxs-lookup"><span data-stu-id="d3d09-247">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="d3d09-248">.NET Core 可在 Docker 容器中运行。</span><span class="sxs-lookup"><span data-stu-id="d3d09-248">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="d3d09-249">官方 .NET Core Docker 映像发布到 Microsoft 容器注册表 (MCR)，用户可以在 [Microsoft.NET Core Docker 中心存储库](https://hub.docker.com/_/microsoft-dotnet-core/)中找到这些映像。</span><span class="sxs-lookup"><span data-stu-id="d3d09-249">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="d3d09-250">每个存储库包含 .NET（SDK 或运行时）和可以使用的操作系统的不同组合的映像。</span><span class="sxs-lookup"><span data-stu-id="d3d09-250">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="d3d09-251">Microsoft 提供适合特定场景的映像。</span><span class="sxs-lookup"><span data-stu-id="d3d09-251">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="d3d09-252">例如，[ASP.NET Core 存储库](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/)提供针对在生产环境中运行 ASP.NET Core 应用生成的映像。</span><span class="sxs-lookup"><span data-stu-id="d3d09-252">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="d3d09-253">有关在 Docker 容器中使用 .NET Core 的详细信息，请参阅 [.NET 和 Docker 简介](../docker/introduction.md)和[示例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。</span><span class="sxs-lookup"><span data-stu-id="d3d09-253">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d3d09-254">后续步骤</span><span class="sxs-lookup"><span data-stu-id="d3d09-254">Next steps</span></span>

- <span data-ttu-id="d3d09-255">[如何检查是否已安装 .NET Core](how-to-detect-installed-versions.md?pivots=os-macos)。</span><span class="sxs-lookup"><span data-stu-id="d3d09-255">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md?pivots=os-macos).</span></span>
- <span data-ttu-id="d3d09-256">[处理 macOS Catalina 公证](macos-notarization-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="d3d09-256">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="d3d09-257">[教程：开始使用 macOS](../tutorials/using-on-mac-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="d3d09-257">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="d3d09-258">[教程：使用 Visual Studio Code 创建一个新应用](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="d3d09-258">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="d3d09-259">[教程：使 .NET Core 应用容器化](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="d3d09-259">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[release-notes-21]: https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md
