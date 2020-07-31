---
title: 在 Ubuntu 上安装 .NET Core - .NET Core
description: 演示在 Ubuntu 上安装 .NET Core SDK 和 .NET Core 运行时的各种方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: c590bd89b718a5cd31dae9f83049eac910cb4049
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863886"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-ubuntu"></a><span data-ttu-id="f2c82-103">在 Ubuntu 上安装 .NET Core SDK 或 .NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="f2c82-103">Install .NET Core SDK or .NET Core Runtime on Ubuntu</span></span>

<span data-ttu-id="f2c82-104">Ubuntu 支持 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="f2c82-104">.NET Core is supported on Ubuntu.</span></span> <span data-ttu-id="f2c82-105">本文介绍如何在 Ubuntu 上安装 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="f2c82-105">This article describes how to install .NET Core on Ubuntu.</span></span> <span data-ttu-id="f2c82-106">如果 Ubuntu 版本不受支持，则该版本不再支持 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="f2c82-106">When an Ubuntu version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="f2c82-107">不过，这些说明可能会帮助你让 .NET Core 在这些版本上运行，即使它不受支持。</span><span class="sxs-lookup"><span data-stu-id="f2c82-107">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="f2c82-108">支持的分发</span><span class="sxs-lookup"><span data-stu-id="f2c82-108">Supported distributions</span></span>

<span data-ttu-id="f2c82-109">下表列出了当前支持的 .NET Core 版本以及支持它们的 Ubuntu 版本。</span><span class="sxs-lookup"><span data-stu-id="f2c82-109">The following table is a list of currently supported .NET Core releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="f2c82-110">这些版本在 [.NET Core 版本达到支持终止日期](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或 [Ubuntu 的版本达到生命周期](https://wiki.ubuntu.com/Releases)之前仍受支持。</span><span class="sxs-lookup"><span data-stu-id="f2c82-110">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="f2c82-111">✔️ 指示 Ubuntu 或 .NET Core 版本仍受支持。</span><span class="sxs-lookup"><span data-stu-id="f2c82-111">A ✔️ indicates that the version of Ubuntu or .NET Core is still supported.</span></span>
- <span data-ttu-id="f2c82-112">❌ 指示 Ubuntu 或 .NET Core 版本在该 Ubuntu 版本上不受支持。</span><span class="sxs-lookup"><span data-stu-id="f2c82-112">A ❌ indicates that the version of Ubuntu or .NET Core isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="f2c82-113">当 Ubuntu 版本和 .NET Core 版本都有 ✔️ 时，将支持该 OS 和 .NET 组合。</span><span class="sxs-lookup"><span data-stu-id="f2c82-113">When both a version of Ubuntu and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="f2c82-114">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="f2c82-114">Ubuntu</span></span>                   | <span data-ttu-id="f2c82-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-115">.NET Core 2.1</span></span> | <span data-ttu-id="f2c82-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-116">.NET Core 3.1</span></span> | <span data-ttu-id="f2c82-117">.NET 5 预览版（仅限手动安装）</span><span class="sxs-lookup"><span data-stu-id="f2c82-117">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="f2c82-118">✔️ [20.04 (LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="f2c82-118">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="f2c82-119">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-119">✔️ 2.1</span></span>        | <span data-ttu-id="f2c82-120">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-120">✔️ 3.1</span></span>        | <span data-ttu-id="f2c82-121">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="f2c82-121">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="f2c82-122">❌ [19.10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="f2c82-122">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="f2c82-123">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-123">✔️ 2.1</span></span>        | <span data-ttu-id="f2c82-124">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-124">✔️ 3.1</span></span>        | <span data-ttu-id="f2c82-125">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="f2c82-125">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="f2c82-126">❌ [19.04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="f2c82-126">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="f2c82-127">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-127">✔️ 2.1</span></span>        | <span data-ttu-id="f2c82-128">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-128">✔️ 3.1</span></span>        | <span data-ttu-id="f2c82-129">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="f2c82-129">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="f2c82-130">❌ [18.10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="f2c82-130">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="f2c82-131">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-131">✔️ 2.1</span></span>        | <span data-ttu-id="f2c82-132">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-132">❌ 3.1</span></span>        | <span data-ttu-id="f2c82-133">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="f2c82-133">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="f2c82-134">✔️ [18.04 (LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="f2c82-134">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="f2c82-135">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-135">✔️ 2.1</span></span>        | <span data-ttu-id="f2c82-136">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-136">✔️ 3.1</span></span>        | <span data-ttu-id="f2c82-137">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="f2c82-137">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="f2c82-138">❌ [17.10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="f2c82-138">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="f2c82-139">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-139">✔️ 2.1</span></span>        | <span data-ttu-id="f2c82-140">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-140">❌ 3.1</span></span>        | <span data-ttu-id="f2c82-141">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="f2c82-141">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="f2c82-142">❌ [17.04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="f2c82-142">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="f2c82-143">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-143">✔️ 2.1</span></span>        | <span data-ttu-id="f2c82-144">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-144">❌ 3.1</span></span>        | <span data-ttu-id="f2c82-145">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="f2c82-145">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="f2c82-146">❌ [16.10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="f2c82-146">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="f2c82-147">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-147">❌ 2.1</span></span>        | <span data-ttu-id="f2c82-148">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-148">❌ 3.1</span></span>        | <span data-ttu-id="f2c82-149">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="f2c82-149">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="f2c82-150">✔️ [16.04 (LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="f2c82-150">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="f2c82-151">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-151">✔️ 2.1</span></span>        | <span data-ttu-id="f2c82-152">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="f2c82-152">✔️ 3.1</span></span>        | <span data-ttu-id="f2c82-153">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="f2c82-153">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="f2c82-154">以下 .NET Core 版本不再受支持。</span><span class="sxs-lookup"><span data-stu-id="f2c82-154">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="f2c82-155">这些版本的下载仍保持发布状态：</span><span class="sxs-lookup"><span data-stu-id="f2c82-155">The downloads for these still remain published:</span></span>

- <span data-ttu-id="f2c82-156">3.0</span><span class="sxs-lookup"><span data-stu-id="f2c82-156">3.0</span></span>
- <span data-ttu-id="f2c82-157">2.2</span><span class="sxs-lookup"><span data-stu-id="f2c82-157">2.2</span></span>
- <span data-ttu-id="f2c82-158">2.0</span><span class="sxs-lookup"><span data-stu-id="f2c82-158">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="f2c82-159">如何安装其他版本</span><span class="sxs-lookup"><span data-stu-id="f2c82-159">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2004-"></a><span data-ttu-id="f2c82-160">20.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="f2c82-160">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1910-"></a><span data-ttu-id="f2c82-161">19.10 ❌</span><span class="sxs-lookup"><span data-stu-id="f2c82-161">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="f2c82-162">19.04 ❌</span><span class="sxs-lookup"><span data-stu-id="f2c82-162">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="f2c82-163">18.10 ❌</span><span class="sxs-lookup"><span data-stu-id="f2c82-163">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="f2c82-164">18.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="f2c82-164">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1710-"></a><span data-ttu-id="f2c82-165">17.10 ❌</span><span class="sxs-lookup"><span data-stu-id="f2c82-165">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="f2c82-166">17.04 ❌</span><span class="sxs-lookup"><span data-stu-id="f2c82-166">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="f2c82-167">16.10 ❌</span><span class="sxs-lookup"><span data-stu-id="f2c82-167">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="f2c82-168">16.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="f2c82-168">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="f2c82-169">APT 更新 SDK 或运行时</span><span class="sxs-lookup"><span data-stu-id="f2c82-169">APT update SDK or runtime</span></span>

<span data-ttu-id="f2c82-170">当新的修补程序版本适用于 .NET Core 时，只需使用以下命令通过 APT 进行升级：</span><span class="sxs-lookup"><span data-stu-id="f2c82-170">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="f2c82-171">APT 疑难解答</span><span class="sxs-lookup"><span data-stu-id="f2c82-171">APT troubleshooting</span></span>

<span data-ttu-id="f2c82-172">本部分提供有关使用 APT 安装 .NET Core 时可能会遇到的常见错误的信息。</span><span class="sxs-lookup"><span data-stu-id="f2c82-172">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="f2c82-173">无法定位</span><span class="sxs-lookup"><span data-stu-id="f2c82-173">Unable to locate</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="f2c82-174">未能提取</span><span class="sxs-lookup"><span data-stu-id="f2c82-174">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="f2c82-175">Snap</span><span class="sxs-lookup"><span data-stu-id="f2c82-175">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="f2c82-176">依赖项</span><span class="sxs-lookup"><span data-stu-id="f2c82-176">Dependencies</span></span>

<span data-ttu-id="f2c82-177">使用包管理器进行安装时，将为你安装这些库。</span><span class="sxs-lookup"><span data-stu-id="f2c82-177">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="f2c82-178">但是，如果手动安装 .NET Core 或发布自包含的应用，则需要确保已安装以下库：</span><span class="sxs-lookup"><span data-stu-id="f2c82-178">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="f2c82-179">libc6</span><span class="sxs-lookup"><span data-stu-id="f2c82-179">libc6</span></span>
- <span data-ttu-id="f2c82-180">libgcc1</span><span class="sxs-lookup"><span data-stu-id="f2c82-180">libgcc1</span></span>
- <span data-ttu-id="f2c82-181">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="f2c82-181">libgssapi-krb5-2</span></span>
- <span data-ttu-id="f2c82-182">libicu52（针对 14.x）</span><span class="sxs-lookup"><span data-stu-id="f2c82-182">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="f2c82-183">libicu55（针对 16.x）</span><span class="sxs-lookup"><span data-stu-id="f2c82-183">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="f2c82-184">libicu60（针对 18.x）</span><span class="sxs-lookup"><span data-stu-id="f2c82-184">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="f2c82-185">libicu66（适用于 20. x）</span><span class="sxs-lookup"><span data-stu-id="f2c82-185">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="f2c82-186">libssl1.0.0（适用于 14.x、16.x）</span><span class="sxs-lookup"><span data-stu-id="f2c82-186">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="f2c82-187">libssl1.1（适用于18.x、20.x）</span><span class="sxs-lookup"><span data-stu-id="f2c82-187">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="f2c82-188">libstdc++6</span><span class="sxs-lookup"><span data-stu-id="f2c82-188">libstdc++6</span></span>
- <span data-ttu-id="f2c82-189">zlib1g</span><span class="sxs-lookup"><span data-stu-id="f2c82-189">zlib1g</span></span>

<span data-ttu-id="f2c82-190">对于使用 System.Drawing.Common 程序集的 .NET Core 应用，还需要以下依赖项：</span><span class="sxs-lookup"><span data-stu-id="f2c82-190">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="f2c82-191">libgdiplus（版本 6.0.1 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="f2c82-191">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="f2c82-192">可以通过将 Mono 存储库添加到系统来安装最新版 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="f2c82-192">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="f2c82-193">有关详细信息，请参阅 <https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="f2c82-193">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="f2c82-194">脚本安装</span><span class="sxs-lookup"><span data-stu-id="f2c82-194">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="f2c82-195">手动安装</span><span class="sxs-lookup"><span data-stu-id="f2c82-195">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="f2c82-196">后续步骤</span><span class="sxs-lookup"><span data-stu-id="f2c82-196">Next steps</span></span>

- [<span data-ttu-id="f2c82-197">教程：使用 Visual Studio Code 通过 .NET Core SDK 创建控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="f2c82-197">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
