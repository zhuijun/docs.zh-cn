---
title: 在 Windows 上安装 .NET Core
description: 了解可在其上安装 .NET Core 的 Windows 版本。
author: adegeo
ms.author: adegeo
ms.date: 06/22/2020
ms.openlocfilehash: 12cffb78de803845a4b18adc70289993e67f64f1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538284"
---
# <a name="install-net-core-on-windows"></a><span data-ttu-id="accd6-103">在 Windows 上安装 .NET Core</span><span class="sxs-lookup"><span data-stu-id="accd6-103">Install .NET Core on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [在 Windows 上安装](windows.md)
> - [在 macOS 上安装](macos.md)
> - [在 Linux 上安装](linux.md)

<span data-ttu-id="accd6-107">在本文中，你将了解如何在 Windows 上安装 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="accd6-107">In this article, you'll learn how to install .NET Core on Windows.</span></span> <span data-ttu-id="accd6-108">.NET Core 由运行时和 SDK 组成。</span><span class="sxs-lookup"><span data-stu-id="accd6-108">.NET Core is made up of the runtime and the SDK.</span></span> <span data-ttu-id="accd6-109">运行时用于运行 .NET Core 应用，应用可能包含也可能不包含它。</span><span class="sxs-lookup"><span data-stu-id="accd6-109">The runtime is used to run a .NET Core app and may or may not be included with the app.</span></span> <span data-ttu-id="accd6-110">SDK 用于创建 .NET Core 应用和库。</span><span class="sxs-lookup"><span data-stu-id="accd6-110">The SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="accd6-111">.NET Core 运行时始终随 SDK 一起安装。</span><span class="sxs-lookup"><span data-stu-id="accd6-111">The .NET Core runtime is always installed with the SDK.</span></span>

<span data-ttu-id="accd6-112">最新版本的 .NET Core 是 3.1。</span><span class="sxs-lookup"><span data-stu-id="accd6-112">The latest version of .NET Core is 3.1.</span></span>

> [!div class="button"]
> [<span data-ttu-id="accd6-113">下载 .NET Core</span><span class="sxs-lookup"><span data-stu-id="accd6-113">Download .NET Core</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="accd6-114">支持的版本</span><span class="sxs-lookup"><span data-stu-id="accd6-114">Supported releases</span></span>

<span data-ttu-id="accd6-115">下表列出了当前支持的 .NET Core 版本以及支持它们的 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="accd6-115">The following table is a list of currently supported .NET Core releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="accd6-116">这些版本在 [.NET Core 版本达到支持终止日期](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或 [Windows 版本达到生命周期](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)之前仍受支持。</span><span class="sxs-lookup"><span data-stu-id="accd6-116">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="accd6-117">Windows 10 版本终止服务日期按版本分段。</span><span class="sxs-lookup"><span data-stu-id="accd6-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="accd6-118">下表中仅考虑家庭版、专业版、专业教育版和专业工作站版。   </span><span class="sxs-lookup"><span data-stu-id="accd6-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="accd6-119">查看 [Windows 生命周期事实表单](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)，了解具体的详细信息。</span><span class="sxs-lookup"><span data-stu-id="accd6-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

- <span data-ttu-id="accd6-120">✔️ 指示 Windows 或 .NET Core 版本仍受支持。</span><span class="sxs-lookup"><span data-stu-id="accd6-120">A ✔️ indicates that the version of Windows or .NET Core is still supported.</span></span>
- <span data-ttu-id="accd6-121">❌ 指示 Windows 或 .NET Core 版本在该 Windows 版本上不受支持。</span><span class="sxs-lookup"><span data-stu-id="accd6-121">A ❌ indicates that the version of Windows or .NET Core isn't supported on that Windows release.</span></span>
- <span data-ttu-id="accd6-122">当 Windows 版本和 .NET Core 版本都有 ✔️ 时，支持该 OS 和 .NET 组合。</span><span class="sxs-lookup"><span data-stu-id="accd6-122">When both a version of Windows and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="accd6-123">操作系统</span><span class="sxs-lookup"><span data-stu-id="accd6-123">Operating System</span></span>                      | <span data-ttu-id="accd6-124">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="accd6-124">.NET Core 2.1</span></span> | <span data-ttu-id="accd6-125">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="accd6-125">.NET Core 3.1</span></span> | <span data-ttu-id="accd6-126">.NET 5 预览版</span><span class="sxs-lookup"><span data-stu-id="accd6-126">.NET 5 Preview</span></span> |
|-----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="accd6-127">✔️ Windows 10 版本 2004</span><span class="sxs-lookup"><span data-stu-id="accd6-127">✔️ Windows 10, Version 2004</span></span> | <span data-ttu-id="accd6-128">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="accd6-128">✔️ 2.1</span></span>        | <span data-ttu-id="accd6-129">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="accd6-129">✔️ 3.1</span></span>        | <span data-ttu-id="accd6-130">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="accd6-130">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="accd6-131">✔️ Windows 10 版本 1909</span><span class="sxs-lookup"><span data-stu-id="accd6-131">✔️ Windows 10, Version 1909</span></span> | <span data-ttu-id="accd6-132">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="accd6-132">✔️ 2.1</span></span>        | <span data-ttu-id="accd6-133">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="accd6-133">✔️ 3.1</span></span>        | <span data-ttu-id="accd6-134">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="accd6-134">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="accd6-135">✔️ Windows 10 版本 1903</span><span class="sxs-lookup"><span data-stu-id="accd6-135">✔️ Windows 10, Version 1903</span></span> | <span data-ttu-id="accd6-136">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="accd6-136">✔️ 2.1</span></span>        | <span data-ttu-id="accd6-137">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="accd6-137">✔️ 3.1</span></span>        | <span data-ttu-id="accd6-138">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="accd6-138">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="accd6-139">✔️ Windows 10 版本 1809</span><span class="sxs-lookup"><span data-stu-id="accd6-139">✔️ Windows 10, Version 1809</span></span> | <span data-ttu-id="accd6-140">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="accd6-140">✔️ 2.1</span></span>        | <span data-ttu-id="accd6-141">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="accd6-141">✔️ 3.1</span></span>        | <span data-ttu-id="accd6-142">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="accd6-142">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="accd6-143">❌ Windows 10 版本 1803</span><span class="sxs-lookup"><span data-stu-id="accd6-143">❌ Windows 10, Version 1803</span></span> | <span data-ttu-id="accd6-144">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="accd6-144">✔️ 2.1</span></span>        | <span data-ttu-id="accd6-145">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="accd6-145">❌ 3.1</span></span>        | <span data-ttu-id="accd6-146">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="accd6-146">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="accd6-147">❌ Windows 10 版本 1709</span><span class="sxs-lookup"><span data-stu-id="accd6-147">❌ Windows 10, Version 1709</span></span> | <span data-ttu-id="accd6-148">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="accd6-148">❌ 2.1</span></span>        | <span data-ttu-id="accd6-149">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="accd6-149">❌ 3.1</span></span>        | <span data-ttu-id="accd6-150">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="accd6-150">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="accd6-151">❌ Windows 10 版本 1703</span><span class="sxs-lookup"><span data-stu-id="accd6-151">❌ Windows 10, Version 1703</span></span> | <span data-ttu-id="accd6-152">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="accd6-152">❌ 2.1</span></span>        | <span data-ttu-id="accd6-153">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="accd6-153">❌ 3.1</span></span>        | <span data-ttu-id="accd6-154">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="accd6-154">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="accd6-155">❌ Windows 10 版本 1607</span><span class="sxs-lookup"><span data-stu-id="accd6-155">❌ Windows 10, Version 1607</span></span> | <span data-ttu-id="accd6-156">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="accd6-156">❌ 2.1</span></span>        | <span data-ttu-id="accd6-157">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="accd6-157">❌ 3.1</span></span>        | <span data-ttu-id="accd6-158">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="accd6-158">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="accd6-159">❌ Windows 10 版本 1511</span><span class="sxs-lookup"><span data-stu-id="accd6-159">❌ Windows 10, Version 1511</span></span> | <span data-ttu-id="accd6-160">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="accd6-160">❌ 2.1</span></span>        | <span data-ttu-id="accd6-161">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="accd6-161">❌ 3.1</span></span>        | <span data-ttu-id="accd6-162">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="accd6-162">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="accd6-163">❌ Windows 10 版本 1507</span><span class="sxs-lookup"><span data-stu-id="accd6-163">❌ Windows 10, Version 1507</span></span> | <span data-ttu-id="accd6-164">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="accd6-164">❌ 2.1</span></span>        | <span data-ttu-id="accd6-165">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="accd6-165">❌ 3.1</span></span>        | <span data-ttu-id="accd6-166">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="accd6-166">❌ 5.0 Preview</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="accd6-167">不支持的版本</span><span class="sxs-lookup"><span data-stu-id="accd6-167">Unsupported releases</span></span>

<span data-ttu-id="accd6-168">以下 .NET Core 版本 ❌ 不再受支持。</span><span class="sxs-lookup"><span data-stu-id="accd6-168">The following versions of .NET Core are ❌ no longer supported.</span></span> <span data-ttu-id="accd6-169">这些版本的下载仍保持发布状态：</span><span class="sxs-lookup"><span data-stu-id="accd6-169">The downloads for these still remain published:</span></span>

- <span data-ttu-id="accd6-170">3.0</span><span class="sxs-lookup"><span data-stu-id="accd6-170">3.0</span></span>
- <span data-ttu-id="accd6-171">2.2</span><span class="sxs-lookup"><span data-stu-id="accd6-171">2.2</span></span>
- <span data-ttu-id="accd6-172">2.0</span><span class="sxs-lookup"><span data-stu-id="accd6-172">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="accd6-173">运行时信息</span><span class="sxs-lookup"><span data-stu-id="accd6-173">Runtime information</span></span>

<span data-ttu-id="accd6-174">运行时用于运行使用 .NET Core 创建的应用。</span><span class="sxs-lookup"><span data-stu-id="accd6-174">The runtime is used to run apps created with .NET Core.</span></span> <span data-ttu-id="accd6-175">应用作者发布应用时，可以在其应用中包含运行时。</span><span class="sxs-lookup"><span data-stu-id="accd6-175">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="accd6-176">如果作者未包含运行时，则由用户安装运行时。</span><span class="sxs-lookup"><span data-stu-id="accd6-176">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="accd6-177">可以在 Windows 上安装三个不同的运行时：</span><span class="sxs-lookup"><span data-stu-id="accd6-177">There are three different runtimes you can install on Windows:</span></span>

<span data-ttu-id="accd6-178">*ASP.NET Core 运行时*</span><span class="sxs-lookup"><span data-stu-id="accd6-178">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="accd6-179">运行 ASP.NET Core 应用。</span><span class="sxs-lookup"><span data-stu-id="accd6-179">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="accd6-180">包括 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="accd6-180">Includes the .NET Core runtime.</span></span>

<span data-ttu-id="accd6-181">*桌面运行时*</span><span class="sxs-lookup"><span data-stu-id="accd6-181">*Desktop runtime*</span></span>\
<span data-ttu-id="accd6-182">运行适用于 Windows 的 .NET Core WPF 和 .NET Core Windows 窗体桌面应用。</span><span class="sxs-lookup"><span data-stu-id="accd6-182">Runs .NET Core WPF and .NET Core Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="accd6-183">包括 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="accd6-183">Includes the .NET Core runtime.</span></span>

<span data-ttu-id="accd6-184">*.NET Core 运行时*</span><span class="sxs-lookup"><span data-stu-id="accd6-184">*.NET Core runtime*</span></span>\
<span data-ttu-id="accd6-185">此运行时是最简单的运行时，不包括任何其他运行时。</span><span class="sxs-lookup"><span data-stu-id="accd6-185">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="accd6-186">强烈建议同时安装 ASP.NET Core 运行时和桌面运行时，以最大限度地提升与 .NET Core 应用的兼容性。 </span><span class="sxs-lookup"><span data-stu-id="accd6-186">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET Core apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="accd6-187">下载 .NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="accd6-187">Download .NET Core Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="accd6-188">SDK 信息</span><span class="sxs-lookup"><span data-stu-id="accd6-188">SDK information</span></span>

<span data-ttu-id="accd6-189">SDK 用于生成和发布 .NET Core 应用和库。</span><span class="sxs-lookup"><span data-stu-id="accd6-189">The SDK is used to build and publish .NET Core apps and libraries.</span></span> <span data-ttu-id="accd6-190">安装 SDK 会包含三个[运行时](#runtime-information)：ASP.NET Core、桌面和 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="accd6-190">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET Core.</span></span>

> [!div class="button"]
> [<span data-ttu-id="accd6-191">下载 .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="accd6-191">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a><span data-ttu-id="accd6-192">依赖项</span><span class="sxs-lookup"><span data-stu-id="accd6-192">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="accd6-193">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="accd6-193">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="accd6-194">.NET Core 3.1 支持下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="accd6-194">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="accd6-195">`+` 表示最低版本。</span><span class="sxs-lookup"><span data-stu-id="accd6-195">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="accd6-196">(OS)</span><span class="sxs-lookup"><span data-stu-id="accd6-196">OS</span></span>                            | <span data-ttu-id="accd6-197">Version</span><span class="sxs-lookup"><span data-stu-id="accd6-197">Version</span></span>                        | <span data-ttu-id="accd6-198">体系结构</span><span class="sxs-lookup"><span data-stu-id="accd6-198">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="accd6-199">Windows 客户端</span><span class="sxs-lookup"><span data-stu-id="accd6-199">Windows Client</span></span>                | <span data-ttu-id="accd6-200">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="accd6-200">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="accd6-201">x64、x86</span><span class="sxs-lookup"><span data-stu-id="accd6-201">x64, x86</span></span>        |
| <span data-ttu-id="accd6-202">Windows 10 客户端</span><span class="sxs-lookup"><span data-stu-id="accd6-202">Windows 10 Client</span></span>             | <span data-ttu-id="accd6-203">版本 1609+</span><span class="sxs-lookup"><span data-stu-id="accd6-203">Version 1609+</span></span>                  | <span data-ttu-id="accd6-204">x64、x86</span><span class="sxs-lookup"><span data-stu-id="accd6-204">x64, x86</span></span>        |
| <span data-ttu-id="accd6-205">Windows Server</span><span class="sxs-lookup"><span data-stu-id="accd6-205">Windows Server</span></span>                | <span data-ttu-id="accd6-206">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="accd6-206">2012 R2+</span></span>                       | <span data-ttu-id="accd6-207">x64、x86</span><span class="sxs-lookup"><span data-stu-id="accd6-207">x64, x86</span></span>        |
| <span data-ttu-id="accd6-208">Nano Server</span><span class="sxs-lookup"><span data-stu-id="accd6-208">Nano Server</span></span>                   | <span data-ttu-id="accd6-209">版本 1803+</span><span class="sxs-lookup"><span data-stu-id="accd6-209">Version 1803+</span></span>                  | <span data-ttu-id="accd6-210">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="accd6-210">x64, ARM32</span></span>      |

<span data-ttu-id="accd6-211">有关 .NET Core 3.1 支持的操作系统、发行版和生命周期策略的详细信息，请参阅 [.NET Core 3.1 支持的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="accd6-211">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="accd6-212">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="accd6-212">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="accd6-213">目前不支持 .NET Core 3.0。有关详细信息，请参阅 [.NET Core 支持策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="accd6-213">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="accd6-214">.NET Core 3.0 支持下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="accd6-214">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="accd6-215">`+` 表示最低版本。</span><span class="sxs-lookup"><span data-stu-id="accd6-215">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="accd6-216">(OS)</span><span class="sxs-lookup"><span data-stu-id="accd6-216">OS</span></span>                            | <span data-ttu-id="accd6-217">Version</span><span class="sxs-lookup"><span data-stu-id="accd6-217">Version</span></span>                        | <span data-ttu-id="accd6-218">体系结构</span><span class="sxs-lookup"><span data-stu-id="accd6-218">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="accd6-219">Windows 客户端</span><span class="sxs-lookup"><span data-stu-id="accd6-219">Windows Client</span></span>                | <span data-ttu-id="accd6-220">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="accd6-220">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="accd6-221">x64、x86</span><span class="sxs-lookup"><span data-stu-id="accd6-221">x64, x86</span></span>        |
| <span data-ttu-id="accd6-222">Windows 10 客户端</span><span class="sxs-lookup"><span data-stu-id="accd6-222">Windows 10 Client</span></span>             | <span data-ttu-id="accd6-223">版本 1607+</span><span class="sxs-lookup"><span data-stu-id="accd6-223">Version 1607+</span></span>                  | <span data-ttu-id="accd6-224">x64、x86</span><span class="sxs-lookup"><span data-stu-id="accd6-224">x64, x86</span></span>        |
| <span data-ttu-id="accd6-225">Windows Server</span><span class="sxs-lookup"><span data-stu-id="accd6-225">Windows Server</span></span>                | <span data-ttu-id="accd6-226">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="accd6-226">2012 R2+</span></span>                       | <span data-ttu-id="accd6-227">x64、x86</span><span class="sxs-lookup"><span data-stu-id="accd6-227">x64, x86</span></span>        |
| <span data-ttu-id="accd6-228">Nano Server</span><span class="sxs-lookup"><span data-stu-id="accd6-228">Nano Server</span></span>                   | <span data-ttu-id="accd6-229">版本 1803+</span><span class="sxs-lookup"><span data-stu-id="accd6-229">Version 1803+</span></span>                  | <span data-ttu-id="accd6-230">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="accd6-230">x64, ARM32</span></span>      |

<span data-ttu-id="accd6-231">有关 .NET Core 3.0 支持的操作系统、发行版和生命周期策略的详细信息，请参阅 [.NET Core 3.0 支持的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="accd6-231">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="accd6-232">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="accd6-232">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="accd6-233">目前不支持 .NET Core 2.2。有关详细信息，请参阅 [.NET Core 支持策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="accd6-233">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="accd6-234">.NET Core 2.2 支持下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="accd6-234">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="accd6-235">`+` 表示最低版本。</span><span class="sxs-lookup"><span data-stu-id="accd6-235">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="accd6-236">(OS)</span><span class="sxs-lookup"><span data-stu-id="accd6-236">OS</span></span>                            | <span data-ttu-id="accd6-237">Version</span><span class="sxs-lookup"><span data-stu-id="accd6-237">Version</span></span>                        | <span data-ttu-id="accd6-238">体系结构</span><span class="sxs-lookup"><span data-stu-id="accd6-238">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="accd6-239">Windows 客户端</span><span class="sxs-lookup"><span data-stu-id="accd6-239">Windows Client</span></span>                | <span data-ttu-id="accd6-240">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="accd6-240">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="accd6-241">x64、x86</span><span class="sxs-lookup"><span data-stu-id="accd6-241">x64, x86</span></span>        |
| <span data-ttu-id="accd6-242">Windows 10 客户端</span><span class="sxs-lookup"><span data-stu-id="accd6-242">Windows 10 Client</span></span>             | <span data-ttu-id="accd6-243">版本 1607+</span><span class="sxs-lookup"><span data-stu-id="accd6-243">Version 1607+</span></span>                  | <span data-ttu-id="accd6-244">x64、x86</span><span class="sxs-lookup"><span data-stu-id="accd6-244">x64, x86</span></span>        |
| <span data-ttu-id="accd6-245">Windows Server</span><span class="sxs-lookup"><span data-stu-id="accd6-245">Windows Server</span></span>                | <span data-ttu-id="accd6-246">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="accd6-246">2008 R2 SP1+</span></span>                   | <span data-ttu-id="accd6-247">x64、x86</span><span class="sxs-lookup"><span data-stu-id="accd6-247">x64, x86</span></span>        |
| <span data-ttu-id="accd6-248">Nano Server</span><span class="sxs-lookup"><span data-stu-id="accd6-248">Nano Server</span></span>                   | <span data-ttu-id="accd6-249">版本 1803+</span><span class="sxs-lookup"><span data-stu-id="accd6-249">Version 1803+</span></span>                   | <span data-ttu-id="accd6-250">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="accd6-250">x64, ARM32</span></span>      |

<span data-ttu-id="accd6-251">有关 .NET Core 2.2 支持的操作系统、发行版和生命周期策略的详细信息，请参阅 [.NET Core 2.2 支持的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="accd6-251">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="accd6-252">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="accd6-252">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="accd6-253">.NET Core 2.1 支持下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="accd6-253">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="accd6-254">`+` 表示最低版本。</span><span class="sxs-lookup"><span data-stu-id="accd6-254">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="accd6-255">(OS)</span><span class="sxs-lookup"><span data-stu-id="accd6-255">OS</span></span>                            | <span data-ttu-id="accd6-256">Version</span><span class="sxs-lookup"><span data-stu-id="accd6-256">Version</span></span>                        | <span data-ttu-id="accd6-257">体系结构</span><span class="sxs-lookup"><span data-stu-id="accd6-257">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="accd6-258">Windows 客户端</span><span class="sxs-lookup"><span data-stu-id="accd6-258">Windows Client</span></span>                | <span data-ttu-id="accd6-259">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="accd6-259">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="accd6-260">x64、x86</span><span class="sxs-lookup"><span data-stu-id="accd6-260">x64, x86</span></span>        |
| <span data-ttu-id="accd6-261">Windows 10 客户端</span><span class="sxs-lookup"><span data-stu-id="accd6-261">Windows 10 Client</span></span>             | <span data-ttu-id="accd6-262">版本 1607+</span><span class="sxs-lookup"><span data-stu-id="accd6-262">Version 1607+</span></span>                  | <span data-ttu-id="accd6-263">x64、x86</span><span class="sxs-lookup"><span data-stu-id="accd6-263">x64, x86</span></span>        |
| <span data-ttu-id="accd6-264">Windows Server</span><span class="sxs-lookup"><span data-stu-id="accd6-264">Windows Server</span></span>                | <span data-ttu-id="accd6-265">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="accd6-265">2008 R2 SP1+</span></span>                   | <span data-ttu-id="accd6-266">x64、x86</span><span class="sxs-lookup"><span data-stu-id="accd6-266">x64, x86</span></span>        |
| <span data-ttu-id="accd6-267">Nano Server</span><span class="sxs-lookup"><span data-stu-id="accd6-267">Nano Server</span></span>                   | <span data-ttu-id="accd6-268">版本 1803+</span><span class="sxs-lookup"><span data-stu-id="accd6-268">Version 1803+</span></span>                  | <span data-ttu-id="accd6-269">x64</span><span class="sxs-lookup"><span data-stu-id="accd6-269">x64,</span></span>            |

<span data-ttu-id="accd6-270">有关 .NET Core 2.1 支持的操作系统、发行版和生命周期策略的详细信息，请参阅 [.NET Core 2.1 支持的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="accd6-270">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> <span data-ttu-id="accd6-271">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="accd6-271">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="accd6-272">如果要在以下 Windows 版本上安装 .NET SDK 或运行时，则需要其他依赖项：</span><span class="sxs-lookup"><span data-stu-id="accd6-272">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="accd6-273">❌ Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="accd6-273">❌ Windows 7 SP1</span></span>
- <span data-ttu-id="accd6-274">❌ Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="accd6-274">❌ Windows Vista SP 2</span></span>
- <span data-ttu-id="accd6-275">✔️ Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="accd6-275">✔️ Windows 8.1</span></span>
- <span data-ttu-id="accd6-276">✔️ Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="accd6-276">✔️ Windows Server 2008 R2</span></span>
- <span data-ttu-id="accd6-277">✔️ Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="accd6-277">✔️ Windows Server 2012 R2</span></span>

<span data-ttu-id="accd6-278">安装以下组件：</span><span class="sxs-lookup"><span data-stu-id="accd6-278">Install the following:</span></span>

- <span data-ttu-id="accd6-279">[Microsoft Visual C++ 2015 Redistributable 更新 3](https://www.microsoft.com/download/details.aspx?id=52685)。</span><span class="sxs-lookup"><span data-stu-id="accd6-279">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="accd6-280">KB2533623</span><span class="sxs-lookup"><span data-stu-id="accd6-280">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="accd6-281">如果遇到一个以下错误，也需要满足上述要求：</span><span class="sxs-lookup"><span data-stu-id="accd6-281">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="accd6-282">此程序无法启动，因为计算机上缺少 api-ms-win-crt-runtime-l1-1-0.dll。</span><span class="sxs-lookup"><span data-stu-id="accd6-282">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="accd6-283">尝试重新安装该程序以解决此问题。</span><span class="sxs-lookup"><span data-stu-id="accd6-283">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="accd6-284">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="accd6-284">\- or -</span></span>
>
> <span data-ttu-id="accd6-285">此程序无法启动，因为计算机上缺少 api-ms-win-cor-timezone-l1-1-0.dll。</span><span class="sxs-lookup"><span data-stu-id="accd6-285">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="accd6-286">尝试重新安装该程序以解决此问题。</span><span class="sxs-lookup"><span data-stu-id="accd6-286">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="accd6-287">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="accd6-287">\- or -</span></span>
>
> <span data-ttu-id="accd6-288">已找到库 hostfxr.dll，但未能将其从 C:\\\<path_to_app>\\hostfxr.dll 中加载。</span><span class="sxs-lookup"><span data-stu-id="accd6-288">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="accd6-289">使用 PowerShell 自动化安装</span><span class="sxs-lookup"><span data-stu-id="accd6-289">Install with PowerShell automation</span></span>

<span data-ttu-id="accd6-290">[dotnet-install 脚本](../tools/dotnet-install-script.md)用于运行时的 CI 自动化和非管理员安装。</span><span class="sxs-lookup"><span data-stu-id="accd6-290">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="accd6-291">可从 [dotnet-install 脚本引用页](../tools/dotnet-install-script.md)下载该脚本。</span><span class="sxs-lookup"><span data-stu-id="accd6-291">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="accd6-292">此脚本默认安装最新的[长期支持 (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，即 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="accd6-292">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="accd6-293">可通过指定 `Channel` 开关以选择特定版本。</span><span class="sxs-lookup"><span data-stu-id="accd6-293">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="accd6-294">包括 `Runtime` 开关以安装运行时。</span><span class="sxs-lookup"><span data-stu-id="accd6-294">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="accd6-295">否则，该脚本安装 SDK。</span><span class="sxs-lookup"><span data-stu-id="accd6-295">Otherwise, the script installs the SDK.</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

<span data-ttu-id="accd6-296">通过省略 `-Runtime` 开关来安装 SDK。</span><span class="sxs-lookup"><span data-stu-id="accd6-296">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="accd6-297">在此示例中将 `-Channel` 开关设置为 `Current`，这将安装受支持的最新版本。</span><span class="sxs-lookup"><span data-stu-id="accd6-297">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="accd6-298">使用 Visual Studio 安装</span><span class="sxs-lookup"><span data-stu-id="accd6-298">Install with Visual Studio</span></span>

<span data-ttu-id="accd6-299">如果你要使用 Visual Studio 开发 .NET Core 应用，请参阅下表，了解不同目标 .NET Core SDK 版本所需的 Visual Studio 最低版本。</span><span class="sxs-lookup"><span data-stu-id="accd6-299">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="accd6-300">.NET Core SDK 版本</span><span class="sxs-lookup"><span data-stu-id="accd6-300">.NET Core SDK version</span></span> | <span data-ttu-id="accd6-301">Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="accd6-301">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="accd6-302">3.1</span><span class="sxs-lookup"><span data-stu-id="accd6-302">3.1</span></span>                   | <span data-ttu-id="accd6-303">Visual Studio 2019 版本 16.4 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="accd6-303">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="accd6-304">3.0</span><span class="sxs-lookup"><span data-stu-id="accd6-304">3.0</span></span>                   | <span data-ttu-id="accd6-305">Visual Studio 2019 版本 16.3 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="accd6-305">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="accd6-306">2.2</span><span class="sxs-lookup"><span data-stu-id="accd6-306">2.2</span></span>                   | <span data-ttu-id="accd6-307">Visual Studio 2017 版本 15.9 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="accd6-307">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="accd6-308">2.1</span><span class="sxs-lookup"><span data-stu-id="accd6-308">2.1</span></span>                   | <span data-ttu-id="accd6-309">Visual Studio 2017 版本 15.7 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="accd6-309">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="accd6-310">如果你已安装 Visual Studio，则可以使用以下步骤检查你的版本。</span><span class="sxs-lookup"><span data-stu-id="accd6-310">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="accd6-311">打开 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="accd6-311">Open Visual Studio.</span></span>
01. <span data-ttu-id="accd6-312">选择“帮助” > “Microsoft Visual Studio”。</span><span class="sxs-lookup"><span data-stu-id="accd6-312">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="accd6-313">从“关于”对话框中读取版本号。</span><span class="sxs-lookup"><span data-stu-id="accd6-313">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="accd6-314">Visual Studio 可安装最新的 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="accd6-314">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

> [!div class="button"]
> <span data-ttu-id="accd6-315">[下载 Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="accd6-315">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="accd6-316">选择工作负载</span><span class="sxs-lookup"><span data-stu-id="accd6-316">Select a workload</span></span>

<span data-ttu-id="accd6-317">安装或修改 Visual Studio 时，根据要生成的应用程序的类型，选择以下一个或多个工作负载：</span><span class="sxs-lookup"><span data-stu-id="accd6-317">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="accd6-318">“其他工具集”部分中的“.NET Core 跨平台开发”工作负荷 。</span><span class="sxs-lookup"><span data-stu-id="accd6-318">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="accd6-319">“Web 和云”部分中的“ASP.NET 和 Web 开发”工作负荷 。</span><span class="sxs-lookup"><span data-stu-id="accd6-319">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="accd6-320">“Web 和云”部分中的“Azure 开发”工作负载 。</span><span class="sxs-lookup"><span data-stu-id="accd6-320">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="accd6-321">“桌面和移动”部分中的“NET 桌面开发”工作负载 。</span><span class="sxs-lookup"><span data-stu-id="accd6-321">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="accd6-322">[![具有 .NET Core 工作负载的 Windows Visual Studio 2019](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="accd6-322">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="accd6-323">随 Visual Studio Code 一起安装</span><span class="sxs-lookup"><span data-stu-id="accd6-323">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="accd6-324">Visual Studio Code 是一个功能强大的轻量级源代码编辑器，可在桌面上运行。</span><span class="sxs-lookup"><span data-stu-id="accd6-324">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="accd6-325">Visual Studio Code 适用于 Windows、macOS 和 Linux。</span><span class="sxs-lookup"><span data-stu-id="accd6-325">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="accd6-326">虽然 Visual Studio Code 不像 Visual Studio 一样附带自动的 .NET Core 安装程序，但添加 .NET Core 支持非常简单。</span><span class="sxs-lookup"><span data-stu-id="accd6-326">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="accd6-327">[下载并安装 Visual Studio Code](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="accd6-327">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="accd6-328">[下载并安装 .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="accd6-328">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="accd6-329">[从 Visual Studio Code 市场安装 C# 扩展](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)。</span><span class="sxs-lookup"><span data-stu-id="accd6-329">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="accd6-330">下载并手动安装</span><span class="sxs-lookup"><span data-stu-id="accd6-330">Download and manually install</span></span>

<span data-ttu-id="accd6-331">除了使用适用于 .NET Core 的 Windows 安装程序，还可以下载并手动安装 SDK 或运行时。</span><span class="sxs-lookup"><span data-stu-id="accd6-331">As an alternative to the Windows installers for .NET Core, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="accd6-332">手动安装通常作为持续集成测试的一部分执行。</span><span class="sxs-lookup"><span data-stu-id="accd6-332">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="accd6-333">对于开发人员或用户，一般使用[安装程序](https://dotnet.microsoft.com/download/dotnet-core)会更好。</span><span class="sxs-lookup"><span data-stu-id="accd6-333">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="accd6-334">在下载 .NET Core SDK 和 .NET Core 运行时后，可以手动安装它们。</span><span class="sxs-lookup"><span data-stu-id="accd6-334">Both .NET Core SDK and .NET Core Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="accd6-335">如果安装 .NET Core SDK，则无需安装相应的运行时。</span><span class="sxs-lookup"><span data-stu-id="accd6-335">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="accd6-336">首先，从以下站点之一下载 SDK 或运行时的二进制版本：</span><span class="sxs-lookup"><span data-stu-id="accd6-336">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="accd6-337">✔️ [.NET 5.0 预览版下载](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="accd6-337">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="accd6-338">✔️ [.NET Core 3.1 下载](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="accd6-338">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="accd6-339">✔️ [.NET Core 2.1 下载](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="accd6-339">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="accd6-340">所有 .NET Core 下载项</span><span class="sxs-lookup"><span data-stu-id="accd6-340">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="accd6-341">创建要将 .NET 提取到的目录，例如 `%USERPROFILE%\dotnet`。</span><span class="sxs-lookup"><span data-stu-id="accd6-341">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="accd6-342">然后，将下载的 zip 文件提取到该目录中。</span><span class="sxs-lookup"><span data-stu-id="accd6-342">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="accd6-343">默认情况下，.NET Core CLI 命令和应用不会使用通过这种方式安装的 .NET Core，且你必须显式选择以使用它。</span><span class="sxs-lookup"><span data-stu-id="accd6-343">By default, .NET Core CLI commands and apps won't use .NET Core installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="accd6-344">为此，请更改用于启动应用程序的环境变量：</span><span class="sxs-lookup"><span data-stu-id="accd6-344">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="accd6-345">使用此方法可以将多个版本安装到不同的位置，然后通过使用指向安装位置的环境变量运行应用程序来明确选择应用程序应使用哪个安装位置。</span><span class="sxs-lookup"><span data-stu-id="accd6-345">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="accd6-346">将 `DOTNET_MULTILEVEL_LOOKUP` 设置为 `0` 时，.NET Core 将忽略任何全局安装的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="accd6-346">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET Core ignores any globally installed .NET Core version.</span></span> <span data-ttu-id="accd6-347">删除环境设置，让 .NET Core 在选择用于运行应用程序的最佳框架时考虑默认的全局安装位置。</span><span class="sxs-lookup"><span data-stu-id="accd6-347">Remove that environment setting to let .NET Core consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="accd6-348">默认值通常为 `C:\Program Files\dotnet`，这是安装 .NET Core 的安装程序所在的位置。</span><span class="sxs-lookup"><span data-stu-id="accd6-348">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET Core.</span></span>

## <a name="docker"></a><span data-ttu-id="accd6-349">Docker</span><span class="sxs-lookup"><span data-stu-id="accd6-349">Docker</span></span>

<span data-ttu-id="accd6-350">容器提供了一种将应用程序与主机系统的其余部分隔离的轻量级方法。</span><span class="sxs-lookup"><span data-stu-id="accd6-350">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="accd6-351">同一计算机上的容器只共享内核，并使用为应用程序提供的资源。</span><span class="sxs-lookup"><span data-stu-id="accd6-351">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="accd6-352">.NET Core 可在 Docker 容器中运行。</span><span class="sxs-lookup"><span data-stu-id="accd6-352">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="accd6-353">官方 .NET Core Docker 映像发布到 Microsoft 容器注册表 (MCR)，用户可以在 [Microsoft.NET Core Docker 中心存储库](https://hub.docker.com/_/microsoft-dotnet-core/)中找到这些映像。</span><span class="sxs-lookup"><span data-stu-id="accd6-353">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="accd6-354">每个存储库包含 .NET（SDK 或运行时）和可以使用的操作系统的不同组合的映像。</span><span class="sxs-lookup"><span data-stu-id="accd6-354">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="accd6-355">Microsoft 提供适合特定场景的映像。</span><span class="sxs-lookup"><span data-stu-id="accd6-355">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="accd6-356">例如，[ASP.NET Core 存储库](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/)提供针对在生产环境中运行 ASP.NET Core 应用生成的映像。</span><span class="sxs-lookup"><span data-stu-id="accd6-356">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="accd6-357">有关在 Docker 容器中使用 .NET Core 的详细信息，请参阅 [.NET 和 Docker 简介](../docker/introduction.md)和[示例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。</span><span class="sxs-lookup"><span data-stu-id="accd6-357">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="accd6-358">后续步骤</span><span class="sxs-lookup"><span data-stu-id="accd6-358">Next steps</span></span>

- <span data-ttu-id="accd6-359">[如何检查是否已安装 .NET Core](how-to-detect-installed-versions.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="accd6-359">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="accd6-360">[教程：Hello World 教程](../tutorials/with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="accd6-360">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="accd6-361">[教程：使用 Visual Studio Code 创建一个新应用](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="accd6-361">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="accd6-362">[教程：使 .NET Core 应用容器化](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="accd6-362">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>
