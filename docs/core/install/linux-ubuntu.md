---
title: 在 Ubuntu 上安装 .NET Core - .NET Core
description: 演示在 Ubuntu 上安装 .NET Core SDK 和 .NET Core 运行时的各种方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 9694dac719024264edee849044f048970b63b7b7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132933"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-ubuntu"></a><span data-ttu-id="d94ca-103">在 Ubuntu 上安装 .NET Core SDK 或 .NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="d94ca-103">Install .NET Core SDK or .NET Core Runtime on Ubuntu</span></span>

<span data-ttu-id="d94ca-104">Ubuntu 支持 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="d94ca-104">.NET Core is supported on Ubuntu.</span></span> <span data-ttu-id="d94ca-105">本文介绍如何在 Ubuntu 上安装 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="d94ca-105">This article describes how to install .NET Core on Ubuntu.</span></span> <span data-ttu-id="d94ca-106">如果 Ubuntu 版本不受支持，则该版本不再支持 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="d94ca-106">When an Ubuntu version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="d94ca-107">不过，这些说明可能会帮助你让 .NET Core 在这些版本上运行，即使它不受支持。</span><span class="sxs-lookup"><span data-stu-id="d94ca-107">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="d94ca-108">支持的分发</span><span class="sxs-lookup"><span data-stu-id="d94ca-108">Supported distributions</span></span>

<span data-ttu-id="d94ca-109">下表列出了当前支持的 .NET Core 版本以及支持它们的 Ubuntu 版本。</span><span class="sxs-lookup"><span data-stu-id="d94ca-109">The following table is a list of currently supported .NET Core releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="d94ca-110">这些版本在 [.NET Core 版本达到支持终止日期](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或 [Ubuntu 的版本达到生命周期](https://wiki.ubuntu.com/Releases)之前仍受支持。</span><span class="sxs-lookup"><span data-stu-id="d94ca-110">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="d94ca-111">✔️ 指示 Ubuntu 或 .NET Core 版本仍受支持。</span><span class="sxs-lookup"><span data-stu-id="d94ca-111">A ✔️ indicates that the version of Ubuntu or .NET Core is still supported.</span></span>
- <span data-ttu-id="d94ca-112">❌ 指示 Ubuntu 或 .NET Core 版本在该 Ubuntu 版本上不受支持。</span><span class="sxs-lookup"><span data-stu-id="d94ca-112">A ❌ indicates that the version of Ubuntu or .NET Core isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="d94ca-113">当 Ubuntu 版本和 .NET Core 版本都有 ✔️ 时，将支持该 OS 和 .NET 组合。</span><span class="sxs-lookup"><span data-stu-id="d94ca-113">When both a version of Ubuntu and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="d94ca-114">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d94ca-114">Ubuntu</span></span>                   | <span data-ttu-id="d94ca-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-115">.NET Core 2.1</span></span> | <span data-ttu-id="d94ca-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-116">.NET Core 3.1</span></span> | <span data-ttu-id="d94ca-117">.NET 5 预览版（仅限手动安装）</span><span class="sxs-lookup"><span data-stu-id="d94ca-117">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="d94ca-118">✔️ [20.04 (LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="d94ca-118">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="d94ca-119">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-119">✔️ 2.1</span></span>        | <span data-ttu-id="d94ca-120">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-120">✔️ 3.1</span></span>        | <span data-ttu-id="d94ca-121">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="d94ca-121">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="d94ca-122">❌ [19.10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="d94ca-122">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="d94ca-123">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-123">✔️ 2.1</span></span>        | <span data-ttu-id="d94ca-124">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-124">✔️ 3.1</span></span>        | <span data-ttu-id="d94ca-125">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="d94ca-125">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="d94ca-126">❌ [19.04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="d94ca-126">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="d94ca-127">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-127">✔️ 2.1</span></span>        | <span data-ttu-id="d94ca-128">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-128">✔️ 3.1</span></span>        | <span data-ttu-id="d94ca-129">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="d94ca-129">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="d94ca-130">❌ [18.10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="d94ca-130">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="d94ca-131">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-131">✔️ 2.1</span></span>        | <span data-ttu-id="d94ca-132">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-132">❌ 3.1</span></span>        | <span data-ttu-id="d94ca-133">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="d94ca-133">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="d94ca-134">✔️ [18.04 (LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="d94ca-134">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="d94ca-135">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-135">✔️ 2.1</span></span>        | <span data-ttu-id="d94ca-136">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-136">✔️ 3.1</span></span>        | <span data-ttu-id="d94ca-137">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="d94ca-137">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="d94ca-138">❌ [17.10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="d94ca-138">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="d94ca-139">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-139">✔️ 2.1</span></span>        | <span data-ttu-id="d94ca-140">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-140">❌ 3.1</span></span>        | <span data-ttu-id="d94ca-141">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="d94ca-141">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="d94ca-142">❌ [17.04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="d94ca-142">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="d94ca-143">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-143">✔️ 2.1</span></span>        | <span data-ttu-id="d94ca-144">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-144">❌ 3.1</span></span>        | <span data-ttu-id="d94ca-145">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="d94ca-145">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="d94ca-146">❌ [16.10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="d94ca-146">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="d94ca-147">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-147">❌ 2.1</span></span>        | <span data-ttu-id="d94ca-148">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-148">❌ 3.1</span></span>        | <span data-ttu-id="d94ca-149">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="d94ca-149">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="d94ca-150">✔️ [16.04 (LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="d94ca-150">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="d94ca-151">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-151">✔️ 2.1</span></span>        | <span data-ttu-id="d94ca-152">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="d94ca-152">✔️ 3.1</span></span>        | <span data-ttu-id="d94ca-153">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="d94ca-153">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="d94ca-154">以下 .NET Core 版本不再受支持。</span><span class="sxs-lookup"><span data-stu-id="d94ca-154">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="d94ca-155">这些版本的下载仍保持发布状态：</span><span class="sxs-lookup"><span data-stu-id="d94ca-155">The downloads for these still remain published:</span></span>

- <span data-ttu-id="d94ca-156">3.0</span><span class="sxs-lookup"><span data-stu-id="d94ca-156">3.0</span></span>
- <span data-ttu-id="d94ca-157">2.2</span><span class="sxs-lookup"><span data-stu-id="d94ca-157">2.2</span></span>
- <span data-ttu-id="d94ca-158">2.0</span><span class="sxs-lookup"><span data-stu-id="d94ca-158">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="d94ca-159">如何安装其他版本</span><span class="sxs-lookup"><span data-stu-id="d94ca-159">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2004-"></a><span data-ttu-id="d94ca-160">20.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="d94ca-160">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1910-"></a><span data-ttu-id="d94ca-161">19.10 ❌</span><span class="sxs-lookup"><span data-stu-id="d94ca-161">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="d94ca-162">19.04 ❌</span><span class="sxs-lookup"><span data-stu-id="d94ca-162">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="d94ca-163">18.10 ❌</span><span class="sxs-lookup"><span data-stu-id="d94ca-163">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="d94ca-164">18.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="d94ca-164">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1710-"></a><span data-ttu-id="d94ca-165">17.10 ❌</span><span class="sxs-lookup"><span data-stu-id="d94ca-165">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="d94ca-166">17.04 ❌</span><span class="sxs-lookup"><span data-stu-id="d94ca-166">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="d94ca-167">16.10 ❌</span><span class="sxs-lookup"><span data-stu-id="d94ca-167">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="d94ca-168">16.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="d94ca-168">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="d94ca-169">APT 更新 SDK 或运行时</span><span class="sxs-lookup"><span data-stu-id="d94ca-169">APT update SDK or runtime</span></span>

<span data-ttu-id="d94ca-170">当新的修补程序版本适用于 .NET Core 时，只需使用以下命令通过 APT 进行升级：</span><span class="sxs-lookup"><span data-stu-id="d94ca-170">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="d94ca-171">APT 疑难解答</span><span class="sxs-lookup"><span data-stu-id="d94ca-171">APT troubleshooting</span></span>

<span data-ttu-id="d94ca-172">本部分提供有关使用 APT 安装 .NET Core 时可能会遇到的常见错误的信息。</span><span class="sxs-lookup"><span data-stu-id="d94ca-172">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="d94ca-173">找不到 \\ 无法安装某些包</span><span class="sxs-lookup"><span data-stu-id="d94ca-173">Unable to locate \\ Some packages could not be installed</span></span>

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="d94ca-174">未能提取</span><span class="sxs-lookup"><span data-stu-id="d94ca-174">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="d94ca-175">Snap</span><span class="sxs-lookup"><span data-stu-id="d94ca-175">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="d94ca-176">依赖项</span><span class="sxs-lookup"><span data-stu-id="d94ca-176">Dependencies</span></span>

<span data-ttu-id="d94ca-177">使用包管理器进行安装时，将为你安装这些库。</span><span class="sxs-lookup"><span data-stu-id="d94ca-177">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="d94ca-178">但是，如果手动安装 .NET Core 或发布自包含的应用，则需要确保已安装以下库：</span><span class="sxs-lookup"><span data-stu-id="d94ca-178">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="d94ca-179">libc6</span><span class="sxs-lookup"><span data-stu-id="d94ca-179">libc6</span></span>
- <span data-ttu-id="d94ca-180">libgcc1</span><span class="sxs-lookup"><span data-stu-id="d94ca-180">libgcc1</span></span>
- <span data-ttu-id="d94ca-181">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="d94ca-181">libgssapi-krb5-2</span></span>
- <span data-ttu-id="d94ca-182">libicu52（针对 14.x）</span><span class="sxs-lookup"><span data-stu-id="d94ca-182">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="d94ca-183">libicu55（针对 16.x）</span><span class="sxs-lookup"><span data-stu-id="d94ca-183">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="d94ca-184">libicu60（针对 18.x）</span><span class="sxs-lookup"><span data-stu-id="d94ca-184">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="d94ca-185">libicu66（适用于 20. x）</span><span class="sxs-lookup"><span data-stu-id="d94ca-185">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="d94ca-186">libssl1.0.0（适用于 14.x、16.x）</span><span class="sxs-lookup"><span data-stu-id="d94ca-186">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="d94ca-187">libssl1.1（适用于18.x、20.x）</span><span class="sxs-lookup"><span data-stu-id="d94ca-187">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="d94ca-188">libstdc++6</span><span class="sxs-lookup"><span data-stu-id="d94ca-188">libstdc++6</span></span>
- <span data-ttu-id="d94ca-189">zlib1g</span><span class="sxs-lookup"><span data-stu-id="d94ca-189">zlib1g</span></span>

<span data-ttu-id="d94ca-190">对于使用 System.Drawing.Common 程序集的 .NET Core 应用，还需要以下依赖项：</span><span class="sxs-lookup"><span data-stu-id="d94ca-190">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="d94ca-191">libgdiplus（版本 6.0.1 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="d94ca-191">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="d94ca-192">可以通过将 Mono 存储库添加到系统来安装最新版 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="d94ca-192">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="d94ca-193">有关详细信息，请参阅 <https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="d94ca-193">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="d94ca-194">脚本安装</span><span class="sxs-lookup"><span data-stu-id="d94ca-194">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="d94ca-195">手动安装</span><span class="sxs-lookup"><span data-stu-id="d94ca-195">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="d94ca-196">后续步骤</span><span class="sxs-lookup"><span data-stu-id="d94ca-196">Next steps</span></span>

- [<span data-ttu-id="d94ca-197">教程：使用 Visual Studio Code 通过 .NET Core SDK 创建控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="d94ca-197">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
