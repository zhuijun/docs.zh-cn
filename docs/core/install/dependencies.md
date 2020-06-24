---
title: .NET Core SDK 和运行时依赖项 - .NET Core
description: 详细介绍在 Windows、Linux 和 macOS 上安装 .NET Core SDK 和运行时的操作系统和 CPU 体系结构先决条件。
author: leecow
ms.author: leecow
ms.date: 06/01/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 81f6ab436428d71f71d9fd0f560bd2b0512a519b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590755"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="7ddca-103">.NET Core 依赖项和要求</span><span class="sxs-lookup"><span data-stu-id="7ddca-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="7ddca-104">本文详细介绍了 .NET Core 支持的操作系统和 CPU 体系结构。</span><span class="sxs-lookup"><span data-stu-id="7ddca-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="7ddca-105">支持的操作系统</span><span class="sxs-lookup"><span data-stu-id="7ddca-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="7ddca-106">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="7ddca-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="7ddca-107">.NET Core 3.1 支持下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="7ddca-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="7ddca-108">`+` 表示最低版本。</span><span class="sxs-lookup"><span data-stu-id="7ddca-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7ddca-109">(OS)</span><span class="sxs-lookup"><span data-stu-id="7ddca-109">OS</span></span>                            | <span data-ttu-id="7ddca-110">Version</span><span class="sxs-lookup"><span data-stu-id="7ddca-110">Version</span></span>                        | <span data-ttu-id="7ddca-111">体系结构</span><span class="sxs-lookup"><span data-stu-id="7ddca-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="7ddca-112">Windows 客户端</span><span class="sxs-lookup"><span data-stu-id="7ddca-112">Windows Client</span></span>                | <span data-ttu-id="7ddca-113">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="7ddca-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="7ddca-114">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7ddca-114">x64, x86</span></span>        |
| <span data-ttu-id="7ddca-115">Windows 10 客户端</span><span class="sxs-lookup"><span data-stu-id="7ddca-115">Windows 10 Client</span></span>             | <span data-ttu-id="7ddca-116">版本 1607+</span><span class="sxs-lookup"><span data-stu-id="7ddca-116">Version 1607+</span></span>                  | <span data-ttu-id="7ddca-117">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7ddca-117">x64, x86</span></span>        |
| <span data-ttu-id="7ddca-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="7ddca-118">Windows Server</span></span>                | <span data-ttu-id="7ddca-119">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="7ddca-119">2012 R2+</span></span>                       | <span data-ttu-id="7ddca-120">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7ddca-120">x64, x86</span></span>        |
| <span data-ttu-id="7ddca-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="7ddca-121">Nano Server</span></span>                   | <span data-ttu-id="7ddca-122">版本 1803+</span><span class="sxs-lookup"><span data-stu-id="7ddca-122">Version 1803+</span></span>                  | <span data-ttu-id="7ddca-123">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="7ddca-123">x64, ARM32</span></span>      |

<span data-ttu-id="7ddca-124">有关 .NET Core 3.1 支持的操作系统、发行版和生命周期策略的详细信息，请参阅 [.NET Core 3.1 支持的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7ddca-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="7ddca-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7ddca-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="7ddca-126">目前不支持 .NET Core 3.0。有关详细信息，请参阅 [.NET Core 支持策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="7ddca-126">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="7ddca-127">.NET Core 3.0 支持下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="7ddca-127">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="7ddca-128">`+` 表示最低版本。</span><span class="sxs-lookup"><span data-stu-id="7ddca-128">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7ddca-129">(OS)</span><span class="sxs-lookup"><span data-stu-id="7ddca-129">OS</span></span>                            | <span data-ttu-id="7ddca-130">Version</span><span class="sxs-lookup"><span data-stu-id="7ddca-130">Version</span></span>                        | <span data-ttu-id="7ddca-131">体系结构</span><span class="sxs-lookup"><span data-stu-id="7ddca-131">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="7ddca-132">Windows 客户端</span><span class="sxs-lookup"><span data-stu-id="7ddca-132">Windows Client</span></span>                | <span data-ttu-id="7ddca-133">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="7ddca-133">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="7ddca-134">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7ddca-134">x64, x86</span></span>        |
| <span data-ttu-id="7ddca-135">Windows 10 客户端</span><span class="sxs-lookup"><span data-stu-id="7ddca-135">Windows 10 Client</span></span>             | <span data-ttu-id="7ddca-136">版本 1607+</span><span class="sxs-lookup"><span data-stu-id="7ddca-136">Version 1607+</span></span>                  | <span data-ttu-id="7ddca-137">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7ddca-137">x64, x86</span></span>        |
| <span data-ttu-id="7ddca-138">Windows Server</span><span class="sxs-lookup"><span data-stu-id="7ddca-138">Windows Server</span></span>                | <span data-ttu-id="7ddca-139">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="7ddca-139">2012 R2+</span></span>                       | <span data-ttu-id="7ddca-140">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7ddca-140">x64, x86</span></span>        |
| <span data-ttu-id="7ddca-141">Nano Server</span><span class="sxs-lookup"><span data-stu-id="7ddca-141">Nano Server</span></span>                   | <span data-ttu-id="7ddca-142">版本 1803+</span><span class="sxs-lookup"><span data-stu-id="7ddca-142">Version 1803+</span></span>                  | <span data-ttu-id="7ddca-143">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="7ddca-143">x64, ARM32</span></span>      |

<span data-ttu-id="7ddca-144">有关 .NET Core 3.0 支持的操作系统、发行版和生命周期策略的详细信息，请参阅 [.NET Core 3.0 支持的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7ddca-144">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="7ddca-145">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="7ddca-145">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="7ddca-146">目前不支持 .NET Core 2.2。有关详细信息，请参阅 [.NET Core 支持策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="7ddca-146">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="7ddca-147">.NET Core 2.2 支持下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="7ddca-147">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="7ddca-148">`+` 表示最低版本。</span><span class="sxs-lookup"><span data-stu-id="7ddca-148">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7ddca-149">(OS)</span><span class="sxs-lookup"><span data-stu-id="7ddca-149">OS</span></span>                            | <span data-ttu-id="7ddca-150">Version</span><span class="sxs-lookup"><span data-stu-id="7ddca-150">Version</span></span>                        | <span data-ttu-id="7ddca-151">体系结构</span><span class="sxs-lookup"><span data-stu-id="7ddca-151">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="7ddca-152">Windows 客户端</span><span class="sxs-lookup"><span data-stu-id="7ddca-152">Windows Client</span></span>                | <span data-ttu-id="7ddca-153">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="7ddca-153">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="7ddca-154">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7ddca-154">x64, x86</span></span>        |
| <span data-ttu-id="7ddca-155">Windows 10 客户端</span><span class="sxs-lookup"><span data-stu-id="7ddca-155">Windows 10 Client</span></span>             | <span data-ttu-id="7ddca-156">版本 1607+</span><span class="sxs-lookup"><span data-stu-id="7ddca-156">Version 1607+</span></span>                  | <span data-ttu-id="7ddca-157">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7ddca-157">x64, x86</span></span>        |
| <span data-ttu-id="7ddca-158">Windows Server</span><span class="sxs-lookup"><span data-stu-id="7ddca-158">Windows Server</span></span>                | <span data-ttu-id="7ddca-159">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="7ddca-159">2008 R2 SP1+</span></span>                   | <span data-ttu-id="7ddca-160">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7ddca-160">x64, x86</span></span>        |
| <span data-ttu-id="7ddca-161">Nano Server</span><span class="sxs-lookup"><span data-stu-id="7ddca-161">Nano Server</span></span>                   | <span data-ttu-id="7ddca-162">版本 1803+</span><span class="sxs-lookup"><span data-stu-id="7ddca-162">Version 1803+</span></span>                   | <span data-ttu-id="7ddca-163">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="7ddca-163">x64, ARM32</span></span>      |

<span data-ttu-id="7ddca-164">有关 .NET Core 2.2 支持的操作系统、发行版和生命周期策略的详细信息，请参阅 [.NET Core 2.2 支持的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7ddca-164">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="7ddca-165">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="7ddca-165">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="7ddca-166">.NET Core 2.1 支持下列 Windows 版本：</span><span class="sxs-lookup"><span data-stu-id="7ddca-166">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="7ddca-167">`+` 表示最低版本。</span><span class="sxs-lookup"><span data-stu-id="7ddca-167">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7ddca-168">(OS)</span><span class="sxs-lookup"><span data-stu-id="7ddca-168">OS</span></span>                            | <span data-ttu-id="7ddca-169">Version</span><span class="sxs-lookup"><span data-stu-id="7ddca-169">Version</span></span>                        | <span data-ttu-id="7ddca-170">体系结构</span><span class="sxs-lookup"><span data-stu-id="7ddca-170">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="7ddca-171">Windows 客户端</span><span class="sxs-lookup"><span data-stu-id="7ddca-171">Windows Client</span></span>                | <span data-ttu-id="7ddca-172">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="7ddca-172">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="7ddca-173">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7ddca-173">x64, x86</span></span>        |
| <span data-ttu-id="7ddca-174">Windows 10 客户端</span><span class="sxs-lookup"><span data-stu-id="7ddca-174">Windows 10 Client</span></span>             | <span data-ttu-id="7ddca-175">版本 1607+</span><span class="sxs-lookup"><span data-stu-id="7ddca-175">Version 1607+</span></span>                  | <span data-ttu-id="7ddca-176">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7ddca-176">x64, x86</span></span>        |
| <span data-ttu-id="7ddca-177">Windows Server</span><span class="sxs-lookup"><span data-stu-id="7ddca-177">Windows Server</span></span>                | <span data-ttu-id="7ddca-178">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="7ddca-178">2008 R2 SP1+</span></span>                   | <span data-ttu-id="7ddca-179">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7ddca-179">x64, x86</span></span>        |
| <span data-ttu-id="7ddca-180">Nano Server</span><span class="sxs-lookup"><span data-stu-id="7ddca-180">Nano Server</span></span>                   | <span data-ttu-id="7ddca-181">版本 1803+</span><span class="sxs-lookup"><span data-stu-id="7ddca-181">Version 1803+</span></span>                  | <span data-ttu-id="7ddca-182">x64</span><span class="sxs-lookup"><span data-stu-id="7ddca-182">x64,</span></span>            |

<span data-ttu-id="7ddca-183">有关 .NET Core 2.1 支持的操作系统、发行版和生命周期策略的详细信息，请参阅 [.NET Core 2.1 支持的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7ddca-183">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> <span data-ttu-id="7ddca-184">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="7ddca-184">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="7ddca-185">如果要在以下 Windows 版本上安装 .NET SDK 或运行时，则需要其他依赖项：</span><span class="sxs-lookup"><span data-stu-id="7ddca-185">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="7ddca-186">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="7ddca-186">Windows 7 SP1</span></span>
- <span data-ttu-id="7ddca-187">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="7ddca-187">Windows Vista SP 2</span></span>
- <span data-ttu-id="7ddca-188">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="7ddca-188">Windows 8.1</span></span>
- <span data-ttu-id="7ddca-189">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="7ddca-189">Windows Server 2008 R2</span></span>
- <span data-ttu-id="7ddca-190">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="7ddca-190">Windows Server 2012 R2</span></span>

<span data-ttu-id="7ddca-191">安装以下组件：</span><span class="sxs-lookup"><span data-stu-id="7ddca-191">Install the following:</span></span>

- <span data-ttu-id="7ddca-192">[Microsoft Visual C++ 2015 Redistributable 更新 3](https://www.microsoft.com/download/details.aspx?id=52685)。</span><span class="sxs-lookup"><span data-stu-id="7ddca-192">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="7ddca-193">KB2533623</span><span class="sxs-lookup"><span data-stu-id="7ddca-193">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="7ddca-194">如果遇到一个以下错误，也需要满足上述要求：</span><span class="sxs-lookup"><span data-stu-id="7ddca-194">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="7ddca-195">此程序无法启动，因为计算机上缺少 api-ms-win-crt-runtime-l1-1-0.dll。</span><span class="sxs-lookup"><span data-stu-id="7ddca-195">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="7ddca-196">尝试重新安装该程序以解决此问题。</span><span class="sxs-lookup"><span data-stu-id="7ddca-196">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="7ddca-197">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="7ddca-197">\- or -</span></span>
>
> <span data-ttu-id="7ddca-198">此程序无法启动，因为计算机上缺少 api-ms-win-cor-timezone-l1-1-0.dll。</span><span class="sxs-lookup"><span data-stu-id="7ddca-198">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="7ddca-199">尝试重新安装该程序以解决此问题。</span><span class="sxs-lookup"><span data-stu-id="7ddca-199">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="7ddca-200">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="7ddca-200">\- or -</span></span>
>
> <span data-ttu-id="7ddca-201">已找到库 hostfxr.dll，但未能将其从 C:\\\<path_to_app>\\hostfxr.dll 中加载。</span><span class="sxs-lookup"><span data-stu-id="7ddca-201">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="7ddca-202">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="7ddca-202">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="7ddca-203">.NET Core 3.1 将 Linux 视为一个操作系统。</span><span class="sxs-lookup"><span data-stu-id="7ddca-203">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="7ddca-204">对于支持的 Linux 发行版，每芯片体系结构都对应有一个 Linux 内部版本。</span><span class="sxs-lookup"><span data-stu-id="7ddca-204">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="7ddca-205">以下 Linux 发行版/版本支持 .NET Core 3.1：</span><span class="sxs-lookup"><span data-stu-id="7ddca-205">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="7ddca-206">`+` 表示最低版本。</span><span class="sxs-lookup"><span data-stu-id="7ddca-206">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7ddca-207">(OS)</span><span class="sxs-lookup"><span data-stu-id="7ddca-207">OS</span></span>                             | <span data-ttu-id="7ddca-208">Version</span><span class="sxs-lookup"><span data-stu-id="7ddca-208">Version</span></span>               | <span data-ttu-id="7ddca-209">体系结构</span><span class="sxs-lookup"><span data-stu-id="7ddca-209">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="7ddca-210">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="7ddca-210">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="7ddca-211">6、7、8</span><span class="sxs-lookup"><span data-stu-id="7ddca-211">6, 7, 8</span></span>               | <span data-ttu-id="7ddca-212">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-212">x64</span></span> |
| <span data-ttu-id="7ddca-213">CentOS</span><span class="sxs-lookup"><span data-stu-id="7ddca-213">CentOS</span></span>                         | <span data-ttu-id="7ddca-214">7+</span><span class="sxs-lookup"><span data-stu-id="7ddca-214">7+</span></span>                    | <span data-ttu-id="7ddca-215">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-215">x64</span></span> |
| <span data-ttu-id="7ddca-216">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="7ddca-216">Oracle Linux</span></span>                   | <span data-ttu-id="7ddca-217">7+</span><span class="sxs-lookup"><span data-stu-id="7ddca-217">7+</span></span>                    | <span data-ttu-id="7ddca-218">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-218">x64</span></span> |
| <span data-ttu-id="7ddca-219">Fedora</span><span class="sxs-lookup"><span data-stu-id="7ddca-219">Fedora</span></span>                         | <span data-ttu-id="7ddca-220">30+</span><span class="sxs-lookup"><span data-stu-id="7ddca-220">30+</span></span>                   | <span data-ttu-id="7ddca-221">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-221">x64</span></span> |
| <span data-ttu-id="7ddca-222">Debian</span><span class="sxs-lookup"><span data-stu-id="7ddca-222">Debian</span></span>                         | <span data-ttu-id="7ddca-223">9+</span><span class="sxs-lookup"><span data-stu-id="7ddca-223">9+</span></span>                    | <span data-ttu-id="7ddca-224">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="7ddca-224">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="7ddca-225">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7ddca-225">Ubuntu</span></span>                         | <span data-ttu-id="7ddca-226">16.04+</span><span class="sxs-lookup"><span data-stu-id="7ddca-226">16.04+</span></span>                | <span data-ttu-id="7ddca-227">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="7ddca-227">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="7ddca-228">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="7ddca-228">Linux Mint</span></span>                     | <span data-ttu-id="7ddca-229">18+</span><span class="sxs-lookup"><span data-stu-id="7ddca-229">18+</span></span>                   | <span data-ttu-id="7ddca-230">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-230">x64</span></span> |
| <span data-ttu-id="7ddca-231">openSUSE</span><span class="sxs-lookup"><span data-stu-id="7ddca-231">openSUSE</span></span>                       | <span data-ttu-id="7ddca-232">15+</span><span class="sxs-lookup"><span data-stu-id="7ddca-232">15+</span></span>                   | <span data-ttu-id="7ddca-233">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-233">x64</span></span> |
| <span data-ttu-id="7ddca-234">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="7ddca-234">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="7ddca-235">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="7ddca-235">12 SP2+</span></span>               | <span data-ttu-id="7ddca-236">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-236">x64</span></span> |
| <span data-ttu-id="7ddca-237">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="7ddca-237">Alpine Linux</span></span>                   | <span data-ttu-id="7ddca-238">3.10+</span><span class="sxs-lookup"><span data-stu-id="7ddca-238">3.10+</span></span>                 | <span data-ttu-id="7ddca-239">x64、ARM64</span><span class="sxs-lookup"><span data-stu-id="7ddca-239">x64, ARM64</span></span> |

<span data-ttu-id="7ddca-240">有关 .NET Core 3.1 支持的操作系统、发行版和生命周期策略的详细信息，请参阅 [.NET Core 3.1 支持的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7ddca-240">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="7ddca-241">有关如何在 ARM64（内核 4.14+）上安装 .NET Core 3.1 的详细信息，请参阅[在 Linux ARM64 上安装 .NET Core 3.0](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213)。</span><span class="sxs-lookup"><span data-stu-id="7ddca-241">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ddca-242">ARM64 支持需要 Linux 内核 4.14 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7ddca-242">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="7ddca-243">某些 linux 发行版满足此要求，而另一些则不满足。</span><span class="sxs-lookup"><span data-stu-id="7ddca-243">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="7ddca-244">例如，支持 Ubuntu 18.04，但不支持 Ubuntu 16.04。</span><span class="sxs-lookup"><span data-stu-id="7ddca-244">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="7ddca-245">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7ddca-245">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="7ddca-246">目前不支持 .NET Core 3.0。有关详细信息，请参阅 [.NET Core 支持策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="7ddca-246">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="7ddca-247">.NET Core 3.0 将 Linux 视为一个操作系统。</span><span class="sxs-lookup"><span data-stu-id="7ddca-247">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="7ddca-248">对于支持的 Linux 发行版，每芯片体系结构都对应有一个 Linux 内部版本。</span><span class="sxs-lookup"><span data-stu-id="7ddca-248">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="7ddca-249">以下 Linux 发行版本/版本支持 .NET Core 3.0：</span><span class="sxs-lookup"><span data-stu-id="7ddca-249">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="7ddca-250">`+` 表示最低版本。</span><span class="sxs-lookup"><span data-stu-id="7ddca-250">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7ddca-251">(OS)</span><span class="sxs-lookup"><span data-stu-id="7ddca-251">OS</span></span>                             | <span data-ttu-id="7ddca-252">Version</span><span class="sxs-lookup"><span data-stu-id="7ddca-252">Version</span></span>               | <span data-ttu-id="7ddca-253">体系结构</span><span class="sxs-lookup"><span data-stu-id="7ddca-253">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="7ddca-254">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="7ddca-254">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="7ddca-255">6、7、8</span><span class="sxs-lookup"><span data-stu-id="7ddca-255">6, 7, 8</span></span>               | <span data-ttu-id="7ddca-256">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-256">x64</span></span> |
| <span data-ttu-id="7ddca-257">CentOS</span><span class="sxs-lookup"><span data-stu-id="7ddca-257">CentOS</span></span>                         | <span data-ttu-id="7ddca-258">7+</span><span class="sxs-lookup"><span data-stu-id="7ddca-258">7+</span></span>                    | <span data-ttu-id="7ddca-259">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-259">x64</span></span> |
| <span data-ttu-id="7ddca-260">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="7ddca-260">Oracle Linux</span></span>                   | <span data-ttu-id="7ddca-261">7+</span><span class="sxs-lookup"><span data-stu-id="7ddca-261">7+</span></span>                    | <span data-ttu-id="7ddca-262">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-262">x64</span></span> |
| <span data-ttu-id="7ddca-263">Fedora</span><span class="sxs-lookup"><span data-stu-id="7ddca-263">Fedora</span></span>                         | <span data-ttu-id="7ddca-264">29+</span><span class="sxs-lookup"><span data-stu-id="7ddca-264">29+</span></span>                   | <span data-ttu-id="7ddca-265">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-265">x64</span></span> |
| <span data-ttu-id="7ddca-266">Debian</span><span class="sxs-lookup"><span data-stu-id="7ddca-266">Debian</span></span>                         | <span data-ttu-id="7ddca-267">9+</span><span class="sxs-lookup"><span data-stu-id="7ddca-267">9+</span></span>                    | <span data-ttu-id="7ddca-268">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="7ddca-268">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="7ddca-269">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7ddca-269">Ubuntu</span></span>                         | <span data-ttu-id="7ddca-270">16.04+</span><span class="sxs-lookup"><span data-stu-id="7ddca-270">16.04+</span></span>                | <span data-ttu-id="7ddca-271">x64、ARM32、ARM64</span><span class="sxs-lookup"><span data-stu-id="7ddca-271">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="7ddca-272">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="7ddca-272">Linux Mint</span></span>                     | <span data-ttu-id="7ddca-273">18+</span><span class="sxs-lookup"><span data-stu-id="7ddca-273">18+</span></span>                   | <span data-ttu-id="7ddca-274">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-274">x64</span></span> |
| <span data-ttu-id="7ddca-275">openSUSE</span><span class="sxs-lookup"><span data-stu-id="7ddca-275">openSUSE</span></span>                       | <span data-ttu-id="7ddca-276">15+</span><span class="sxs-lookup"><span data-stu-id="7ddca-276">15+</span></span>                   | <span data-ttu-id="7ddca-277">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-277">x64</span></span> |
| <span data-ttu-id="7ddca-278">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="7ddca-278">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="7ddca-279">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="7ddca-279">12 SP2+</span></span>               | <span data-ttu-id="7ddca-280">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-280">x64</span></span> |
| <span data-ttu-id="7ddca-281">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="7ddca-281">Alpine Linux</span></span>                   | <span data-ttu-id="7ddca-282">3.8+</span><span class="sxs-lookup"><span data-stu-id="7ddca-282">3.8+</span></span>                  | <span data-ttu-id="7ddca-283">x64、ARM64</span><span class="sxs-lookup"><span data-stu-id="7ddca-283">x64, ARM64</span></span> |

<span data-ttu-id="7ddca-284">有关 .NET Core 3.0 支持的操作系统、发行版和生命周期策略的详细信息，请参阅 [.NET Core 3.0 支持的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7ddca-284">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="7ddca-285">有关如何在 ARM64 上安装 .NET Core 3.0 的详细信息，请参阅[在 Linux ARM64 上安装 .NET Core 3.0](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213)。</span><span class="sxs-lookup"><span data-stu-id="7ddca-285">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="7ddca-286">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="7ddca-286">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="7ddca-287">目前不支持 .NET Core 2.2。有关详细信息，请参阅 [.NET Core 支持策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="7ddca-287">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="7ddca-288">.NET Core 2.2 将 Linux 视为一个操作系统。</span><span class="sxs-lookup"><span data-stu-id="7ddca-288">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="7ddca-289">对于支持的 Linux 发行版，每芯片体系结构都对应有一个 Linux 内部版本。</span><span class="sxs-lookup"><span data-stu-id="7ddca-289">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="7ddca-290">以下 Linux 发行版本/版本支持 .NET Core 2.2：</span><span class="sxs-lookup"><span data-stu-id="7ddca-290">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="7ddca-291">`+` 表示最低版本。</span><span class="sxs-lookup"><span data-stu-id="7ddca-291">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7ddca-292">(OS)</span><span class="sxs-lookup"><span data-stu-id="7ddca-292">OS</span></span>                             |  <span data-ttu-id="7ddca-293">Version</span><span class="sxs-lookup"><span data-stu-id="7ddca-293">Version</span></span>                |  <span data-ttu-id="7ddca-294">体系结构</span><span class="sxs-lookup"><span data-stu-id="7ddca-294">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="7ddca-295">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="7ddca-295">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="7ddca-296">6、7</span><span class="sxs-lookup"><span data-stu-id="7ddca-296">6, 7</span></span>                   | <span data-ttu-id="7ddca-297">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-297">x64</span></span> |
| <span data-ttu-id="7ddca-298">CentOS</span><span class="sxs-lookup"><span data-stu-id="7ddca-298">CentOS</span></span>                         |  <span data-ttu-id="7ddca-299">7</span><span class="sxs-lookup"><span data-stu-id="7ddca-299">7</span></span>                      | <span data-ttu-id="7ddca-300">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-300">x64</span></span> |
| <span data-ttu-id="7ddca-301">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="7ddca-301">Oracle Linux</span></span>                   |  <span data-ttu-id="7ddca-302">7</span><span class="sxs-lookup"><span data-stu-id="7ddca-302">7</span></span>                      | <span data-ttu-id="7ddca-303">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-303">x64</span></span> |
| <span data-ttu-id="7ddca-304">Fedora</span><span class="sxs-lookup"><span data-stu-id="7ddca-304">Fedora</span></span>                         |  <span data-ttu-id="7ddca-305">29、30</span><span class="sxs-lookup"><span data-stu-id="7ddca-305">29, 30</span></span>                 | <span data-ttu-id="7ddca-306">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-306">x64</span></span> |
| <span data-ttu-id="7ddca-307">Debian</span><span class="sxs-lookup"><span data-stu-id="7ddca-307">Debian</span></span>                         |  <span data-ttu-id="7ddca-308">9</span><span class="sxs-lookup"><span data-stu-id="7ddca-308">9</span></span>                      | <span data-ttu-id="7ddca-309">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="7ddca-309">x64, ARM32</span></span> |
| <span data-ttu-id="7ddca-310">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7ddca-310">Ubuntu</span></span>                         |  <span data-ttu-id="7ddca-311">16.04、18.04、18.10</span><span class="sxs-lookup"><span data-stu-id="7ddca-311">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="7ddca-312">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="7ddca-312">x64, ARM32</span></span> |
| <span data-ttu-id="7ddca-313">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="7ddca-313">Linux Mint</span></span>                     |  <span data-ttu-id="7ddca-314">17、18</span><span class="sxs-lookup"><span data-stu-id="7ddca-314">17, 18</span></span>                 | <span data-ttu-id="7ddca-315">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-315">x64</span></span> |
| <span data-ttu-id="7ddca-316">openSUSE</span><span class="sxs-lookup"><span data-stu-id="7ddca-316">openSUSE</span></span>                       |  <span data-ttu-id="7ddca-317">15+</span><span class="sxs-lookup"><span data-stu-id="7ddca-317">15+</span></span>                    | <span data-ttu-id="7ddca-318">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-318">x64</span></span> |
| <span data-ttu-id="7ddca-319">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="7ddca-319">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="7ddca-320">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="7ddca-320">12 SP2+</span></span>                | <span data-ttu-id="7ddca-321">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-321">x64</span></span> |
| <span data-ttu-id="7ddca-322">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="7ddca-322">Alpine Linux</span></span>                   |  <span data-ttu-id="7ddca-323">3.8+</span><span class="sxs-lookup"><span data-stu-id="7ddca-323">3.8+</span></span>                   | <span data-ttu-id="7ddca-324">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-324">x64</span></span> |

<span data-ttu-id="7ddca-325">有关 .NET Core 2.2 支持的操作系统、发行版和生命周期策略的详细信息，请参阅 [.NET Core 2.2 支持的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7ddca-325">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="7ddca-326">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="7ddca-326">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="7ddca-327">.NET Core 2.1 将 Linux 视为一个操作系统。</span><span class="sxs-lookup"><span data-stu-id="7ddca-327">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="7ddca-328">对于支持的 Linux 发行版，每芯片体系结构都对应有一个 Linux 内部版本。</span><span class="sxs-lookup"><span data-stu-id="7ddca-328">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="7ddca-329">以下 Linux 发行版本/版本支持 .NET Core 2.1：</span><span class="sxs-lookup"><span data-stu-id="7ddca-329">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="7ddca-330">`+` 表示最低版本。</span><span class="sxs-lookup"><span data-stu-id="7ddca-330">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7ddca-331">(OS)</span><span class="sxs-lookup"><span data-stu-id="7ddca-331">OS</span></span>                             |  <span data-ttu-id="7ddca-332">Version</span><span class="sxs-lookup"><span data-stu-id="7ddca-332">Version</span></span>                |  <span data-ttu-id="7ddca-333">体系结构</span><span class="sxs-lookup"><span data-stu-id="7ddca-333">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="7ddca-334">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="7ddca-334">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="7ddca-335">6、7、8</span><span class="sxs-lookup"><span data-stu-id="7ddca-335">6, 7, 8</span></span>                | <span data-ttu-id="7ddca-336">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-336">x64</span></span> |
| <span data-ttu-id="7ddca-337">CentOS</span><span class="sxs-lookup"><span data-stu-id="7ddca-337">CentOS</span></span>                         |  <span data-ttu-id="7ddca-338">7+</span><span class="sxs-lookup"><span data-stu-id="7ddca-338">7+</span></span>                     | <span data-ttu-id="7ddca-339">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-339">x64</span></span> |
| <span data-ttu-id="7ddca-340">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="7ddca-340">Oracle Linux</span></span>                   |  <span data-ttu-id="7ddca-341">7+</span><span class="sxs-lookup"><span data-stu-id="7ddca-341">7+</span></span>                     | <span data-ttu-id="7ddca-342">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-342">x64</span></span> |
| <span data-ttu-id="7ddca-343">Fedora</span><span class="sxs-lookup"><span data-stu-id="7ddca-343">Fedora</span></span>                         |  <span data-ttu-id="7ddca-344">30+</span><span class="sxs-lookup"><span data-stu-id="7ddca-344">30+</span></span>                    | <span data-ttu-id="7ddca-345">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-345">x64</span></span> |
| <span data-ttu-id="7ddca-346">Debian</span><span class="sxs-lookup"><span data-stu-id="7ddca-346">Debian</span></span>                         |  <span data-ttu-id="7ddca-347">9</span><span class="sxs-lookup"><span data-stu-id="7ddca-347">9</span></span>                      | <span data-ttu-id="7ddca-348">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="7ddca-348">x64, ARM32</span></span> |
| <span data-ttu-id="7ddca-349">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7ddca-349">Ubuntu</span></span>                         |  <span data-ttu-id="7ddca-350">16.04、18.04、19.04、19.10</span><span class="sxs-lookup"><span data-stu-id="7ddca-350">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="7ddca-351">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="7ddca-351">x64, ARM32</span></span> |
| <span data-ttu-id="7ddca-352">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="7ddca-352">Linux Mint</span></span>                     |  <span data-ttu-id="7ddca-353">17+</span><span class="sxs-lookup"><span data-stu-id="7ddca-353">17+</span></span>                    | <span data-ttu-id="7ddca-354">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-354">x64</span></span> |
| <span data-ttu-id="7ddca-355">openSUSE</span><span class="sxs-lookup"><span data-stu-id="7ddca-355">openSUSE</span></span>                       |  <span data-ttu-id="7ddca-356">15+</span><span class="sxs-lookup"><span data-stu-id="7ddca-356">15+</span></span>                    | <span data-ttu-id="7ddca-357">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-357">x64</span></span> |
| <span data-ttu-id="7ddca-358">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="7ddca-358">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="7ddca-359">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="7ddca-359">12 SP2+</span></span>                | <span data-ttu-id="7ddca-360">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-360">x64</span></span> |
| <span data-ttu-id="7ddca-361">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="7ddca-361">Alpine Linux</span></span>                   |  <span data-ttu-id="7ddca-362">3.8+</span><span class="sxs-lookup"><span data-stu-id="7ddca-362">3.8+</span></span>                   | <span data-ttu-id="7ddca-363">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-363">x64</span></span> |

<span data-ttu-id="7ddca-364">有关 .NET Core 2.1 支持的操作系统、发行版和生命周期策略的详细信息，请参阅 [.NET Core 2.1 支持的 OS 版本](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)。</span><span class="sxs-lookup"><span data-stu-id="7ddca-364">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="7ddca-365">Linux 发行版本依赖项</span><span class="sxs-lookup"><span data-stu-id="7ddca-365">Linux distribution dependencies</span></span>

<span data-ttu-id="7ddca-366">根据 Linux 发行版，你可能需要安装其他依赖项。</span><span class="sxs-lookup"><span data-stu-id="7ddca-366">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ddca-367">确切的版本和名称可能因所选 Linux 发行版本略有不同。</span><span class="sxs-lookup"><span data-stu-id="7ddca-367">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="7ddca-368">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7ddca-368">Ubuntu</span></span>

<span data-ttu-id="7ddca-369">Ubuntu 发行版需要安装以下库：</span><span class="sxs-lookup"><span data-stu-id="7ddca-369">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="7ddca-370">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="7ddca-370">liblttng-ust0</span></span>
- <span data-ttu-id="7ddca-371">libcurl3（针对 14.x 和 16.x）</span><span class="sxs-lookup"><span data-stu-id="7ddca-371">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="7ddca-372">libcurl4（针对 18.x）</span><span class="sxs-lookup"><span data-stu-id="7ddca-372">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="7ddca-373">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="7ddca-373">libssl1.0.0</span></span>
- <span data-ttu-id="7ddca-374">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="7ddca-374">libkrb5-3</span></span>
- <span data-ttu-id="7ddca-375">zlib1g</span><span class="sxs-lookup"><span data-stu-id="7ddca-375">zlib1g</span></span>
- <span data-ttu-id="7ddca-376">libicu52（针对 14.x）</span><span class="sxs-lookup"><span data-stu-id="7ddca-376">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="7ddca-377">libicu55（针对 16.x）</span><span class="sxs-lookup"><span data-stu-id="7ddca-377">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="7ddca-378">libicu57（针对 17.x）</span><span class="sxs-lookup"><span data-stu-id="7ddca-378">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="7ddca-379">libicu60（针对 18.x）</span><span class="sxs-lookup"><span data-stu-id="7ddca-379">libicu60 (for 18.x)</span></span>

<span data-ttu-id="7ddca-380">对于使用 System.Drawing.Common 程序集的 .NET Core 应用，还需要以下依赖项：</span><span class="sxs-lookup"><span data-stu-id="7ddca-380">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="7ddca-381">libgdiplus（版本 6.0.1 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="7ddca-381">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="7ddca-382">大多数 Ubuntu 版本都包含 libgdiplus 的早期版本。</span><span class="sxs-lookup"><span data-stu-id="7ddca-382">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="7ddca-383">可以通过将 Mono 存储库添加到系统来安装最新版 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="7ddca-383">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="7ddca-384">有关详细信息，请参阅 <https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="7ddca-384">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="7ddca-385">CentOS 和 Fedora</span><span class="sxs-lookup"><span data-stu-id="7ddca-385">CentOS and Fedora</span></span>

<span data-ttu-id="7ddca-386">CentOS 发行版本需要安装以下库：</span><span class="sxs-lookup"><span data-stu-id="7ddca-386">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="7ddca-387">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="7ddca-387">lttng-ust</span></span>
- <span data-ttu-id="7ddca-388">libcurl</span><span class="sxs-lookup"><span data-stu-id="7ddca-388">libcurl</span></span>
- <span data-ttu-id="7ddca-389">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="7ddca-389">openssl-libs</span></span>
- <span data-ttu-id="7ddca-390">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="7ddca-390">krb5-libs</span></span>
- <span data-ttu-id="7ddca-391">libicu</span><span class="sxs-lookup"><span data-stu-id="7ddca-391">libicu</span></span>
- <span data-ttu-id="7ddca-392">zlib</span><span class="sxs-lookup"><span data-stu-id="7ddca-392">zlib</span></span>

<span data-ttu-id="7ddca-393">Fedora 用户：如果 OpenSSL 的版本为 1.1 及更高版本，则需要安装 compat-openssl10。</span><span class="sxs-lookup"><span data-stu-id="7ddca-393">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="7ddca-394">对于 .NET Core 2.0，还需要以下依赖项：</span><span class="sxs-lookup"><span data-stu-id="7ddca-394">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="7ddca-395">libunwind</span><span class="sxs-lookup"><span data-stu-id="7ddca-395">libunwind</span></span>
- <span data-ttu-id="7ddca-396">libuuid</span><span class="sxs-lookup"><span data-stu-id="7ddca-396">libuuid</span></span>

<span data-ttu-id="7ddca-397">有关依赖项的详细信息，请参阅[独立式 Linux 应用](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="7ddca-397">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="7ddca-398">对于使用 System.Drawing.Common 程序集的 .NET Core 应用，还需要以下依赖项：</span><span class="sxs-lookup"><span data-stu-id="7ddca-398">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="7ddca-399">libgdiplus（版本 6.0.1 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="7ddca-399">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="7ddca-400">CentOS 和 Fedora 的大多数版本都包含 libgdiplus 的早期版本。</span><span class="sxs-lookup"><span data-stu-id="7ddca-400">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="7ddca-401">可以通过将 Mono 存储库添加到系统来安装最新版 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="7ddca-401">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="7ddca-402">有关详细信息，请参阅 <https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="7ddca-402">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="alpine"></a><span data-ttu-id="7ddca-403">Alpine</span><span class="sxs-lookup"><span data-stu-id="7ddca-403">Alpine</span></span>

<span data-ttu-id="7ddca-404">Alpine 发行版需要安装以下库：</span><span class="sxs-lookup"><span data-stu-id="7ddca-404">Alpine distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="7ddca-405">icu-libs（如果已禁用全球化，则不需要此库）</span><span class="sxs-lookup"><span data-stu-id="7ddca-405">icu-libs (this is not needed if globalization is disabled)</span></span>
- <span data-ttu-id="7ddca-406">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="7ddca-406">krb5-libs</span></span>
- <span data-ttu-id="7ddca-407">libcurl</span><span class="sxs-lookup"><span data-stu-id="7ddca-407">libcurl</span></span>
- <span data-ttu-id="7ddca-408">libintl</span><span class="sxs-lookup"><span data-stu-id="7ddca-408">libintl</span></span>
- <span data-ttu-id="7ddca-409">libssl1.1（适用于 Alpine 3.9 或更高版本）或 libssl1.0（适用于旧版本）</span><span class="sxs-lookup"><span data-stu-id="7ddca-409">libssl1.1 (for Alpine 3.9 or later) or libssl1.0 (for older ones)</span></span>
- <span data-ttu-id="7ddca-410">libstdc++</span><span class="sxs-lookup"><span data-stu-id="7ddca-410">libstdc++</span></span>
- <span data-ttu-id="7ddca-411">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="7ddca-411">lttng-ust</span></span>
- <span data-ttu-id="7ddca-412">numactl（可选，仅适用于启用了 NUMA 的设备）</span><span class="sxs-lookup"><span data-stu-id="7ddca-412">numactl (optional, useful only for devices with NUMA enabled)</span></span>
- <span data-ttu-id="7ddca-413">zlib</span><span class="sxs-lookup"><span data-stu-id="7ddca-413">zlib</span></span>

<span data-ttu-id="7ddca-414">对于使用 System.Drawing.Common 程序集的 .NET Core 应用，还需要以下依赖项：</span><span class="sxs-lookup"><span data-stu-id="7ddca-414">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="7ddca-415">libgdiplus（只能用于边缘/测试存储库）</span><span class="sxs-lookup"><span data-stu-id="7ddca-415">libgdiplus (it is available only in the edge/testing repository)</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="7ddca-416">以下 macOS 版本支持 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="7ddca-416">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="7ddca-417">`+` 表示最低版本。</span><span class="sxs-lookup"><span data-stu-id="7ddca-417">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7ddca-418">.NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="7ddca-418">.NET Core Version</span></span> | <span data-ttu-id="7ddca-419">macOS</span><span class="sxs-lookup"><span data-stu-id="7ddca-419">macOS</span></span>                 | <span data-ttu-id="7ddca-420">体系结构</span><span class="sxs-lookup"><span data-stu-id="7ddca-420">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="7ddca-421">3.1</span><span class="sxs-lookup"><span data-stu-id="7ddca-421">3.1</span></span>               | <span data-ttu-id="7ddca-422">High Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="7ddca-422">High Sierra (10.13+)</span></span>  | <span data-ttu-id="7ddca-423">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-423">x64</span></span> | [<span data-ttu-id="7ddca-424">详细信息</span><span class="sxs-lookup"><span data-stu-id="7ddca-424">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="7ddca-425">3.0</span><span class="sxs-lookup"><span data-stu-id="7ddca-425">3.0</span></span>               | <span data-ttu-id="7ddca-426">High Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="7ddca-426">High Sierra (10.13+)</span></span>  | <span data-ttu-id="7ddca-427">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-427">x64</span></span> | [<span data-ttu-id="7ddca-428">详细信息</span><span class="sxs-lookup"><span data-stu-id="7ddca-428">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="7ddca-429">2.2</span><span class="sxs-lookup"><span data-stu-id="7ddca-429">2.2</span></span>               | <span data-ttu-id="7ddca-430">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="7ddca-430">Sierra (10.12+)</span></span>       | <span data-ttu-id="7ddca-431">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-431">x64</span></span> | [<span data-ttu-id="7ddca-432">详细信息</span><span class="sxs-lookup"><span data-stu-id="7ddca-432">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="7ddca-433">2.1</span><span class="sxs-lookup"><span data-stu-id="7ddca-433">2.1</span></span>               | <span data-ttu-id="7ddca-434">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="7ddca-434">Sierra (10.12+)</span></span>       | <span data-ttu-id="7ddca-435">X64</span><span class="sxs-lookup"><span data-stu-id="7ddca-435">x64</span></span> | [<span data-ttu-id="7ddca-436">详细信息</span><span class="sxs-lookup"><span data-stu-id="7ddca-436">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="7ddca-437">自 macOS Catalina（版本10.15）开始，所有在 2019 年 6 月 1 日之后生成并使用开发者 ID 扩散的软件都必须经过公证。</span><span class="sxs-lookup"><span data-stu-id="7ddca-437">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="7ddca-438">此要求应用于 .NET Core 运行时、.NET Core SDK 以及使用 .NET Core 创建的软件。</span><span class="sxs-lookup"><span data-stu-id="7ddca-438">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="7ddca-439">自 2020 年 2 月 18 日起，.NET Core（运行时和 SDK）版本 3.1、3.0 和 2.1 的安装程序都已经过公证。</span><span class="sxs-lookup"><span data-stu-id="7ddca-439">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="7ddca-440">以前发布的版本没有经过公证。</span><span class="sxs-lookup"><span data-stu-id="7ddca-440">Prior released versions aren't notarized.</span></span> <span data-ttu-id="7ddca-441">如果运行未经过公证的应用，将看到类似于下图的错误：</span><span class="sxs-lookup"><span data-stu-id="7ddca-441">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![macOS Catalina 公证警报](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="7ddca-443">若要详细了解强制执行的公证要求对 .NET Core 和 .NET Core 应用的影响，请参阅[处理 macOS Catalina 公证](macos-notarization-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="7ddca-443">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="7ddca-444">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="7ddca-444">libgdiplus</span></span>

<span data-ttu-id="7ddca-445">使用 System.Drawing.Common 程序集的 .NET Core 应用程序要求安装 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="7ddca-445">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="7ddca-446">获取 libgdiplus 的一个简单方法是使用适用于 macOS 的 [Homebrew (“brew”)](https://brew.sh/) 包。</span><span class="sxs-lookup"><span data-stu-id="7ddca-446">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="7ddca-447">在安装 brew 后，通过在终端（命令）提示符处执行以下命令来安装 libgdiplus：</span><span class="sxs-lookup"><span data-stu-id="7ddca-447">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="7ddca-448">后续步骤</span><span class="sxs-lookup"><span data-stu-id="7ddca-448">Next steps</span></span>

- <span data-ttu-id="7ddca-449">若要开发并运行应用，请安装 [.NET Core SDK](sdk.md)（包括运行时）。</span><span class="sxs-lookup"><span data-stu-id="7ddca-449">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="7ddca-450">若要运行其他人创建的应用，请安装 [.NET Core 运行时](runtime.md)。</span><span class="sxs-lookup"><span data-stu-id="7ddca-450">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
