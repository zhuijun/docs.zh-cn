---
title: 在 Debian 上安装 .NET Core - .NET Core
description: 演示在 Debian 上安装 .NET Core SDK 和 .NET Core 运行时的各种方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: d4a54a8a5354a1430141d2c06d4aa90dbafc3edf
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134934"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-debian"></a><span data-ttu-id="786b6-103">在 Debian 上安装 .NET Core SDK 或 .NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="786b6-103">Install .NET Core SDK or .NET Core Runtime on Debian</span></span>

<span data-ttu-id="786b6-104">本文介绍如何在 Debian 上安装 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="786b6-104">This article describes how to install .NET Core on Debian.</span></span> <span data-ttu-id="786b6-105">如果 Debian 版本不受支持，则该版本不再支持 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="786b6-105">When a Debian version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="786b6-106">不过，这些说明可能会帮助你让 .NET Core 在这些版本上运行，即使它不受支持。</span><span class="sxs-lookup"><span data-stu-id="786b6-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="786b6-107">支持的分发</span><span class="sxs-lookup"><span data-stu-id="786b6-107">Supported distributions</span></span>

<span data-ttu-id="786b6-108">下表列出了当前支持的 .NET Core 版本以及支持它们的 Debian 版本。</span><span class="sxs-lookup"><span data-stu-id="786b6-108">The following table is a list of currently supported .NET Core releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="786b6-109">这些版本在 [.NET Core 版本达到支持终止日期](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或 [Debian 的版本达到生命周期](https://wiki.debian.org/DebianReleases)之前仍受支持。</span><span class="sxs-lookup"><span data-stu-id="786b6-109">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="786b6-110">✔️ 指示 Debian 或 .NET Core 版本仍受支持。</span><span class="sxs-lookup"><span data-stu-id="786b6-110">A ✔️ indicates that the version of Debian or .NET Core is still supported.</span></span>
- <span data-ttu-id="786b6-111">❌ 指示 Debian 或 .NET Core 版本在该 Debian 版本上不受支持。</span><span class="sxs-lookup"><span data-stu-id="786b6-111">A ❌ indicates that the version of Debian or .NET Core isn't supported on that Debian release.</span></span>
- <span data-ttu-id="786b6-112">当 Debian 版本和 .NET Core 版本都有 ✔️ 时，将支持该 OS 和 .NET 组合。</span><span class="sxs-lookup"><span data-stu-id="786b6-112">When both a version of Debian and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="786b6-113">Debian</span><span class="sxs-lookup"><span data-stu-id="786b6-113">Debian</span></span>                   | <span data-ttu-id="786b6-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="786b6-114">.NET Core 2.1</span></span> | <span data-ttu-id="786b6-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="786b6-115">.NET Core 3.1</span></span> | <span data-ttu-id="786b6-116">.NET 5 预览版（仅限手动安装）</span><span class="sxs-lookup"><span data-stu-id="786b6-116">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="786b6-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="786b6-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="786b6-118">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="786b6-118">✔️ 2.1</span></span>        | <span data-ttu-id="786b6-119">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="786b6-119">✔️ 3.1</span></span>        | <span data-ttu-id="786b6-120">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="786b6-120">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="786b6-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="786b6-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="786b6-122">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="786b6-122">✔️ 2.1</span></span>        | <span data-ttu-id="786b6-123">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="786b6-123">✔️ 3.1</span></span>        | <span data-ttu-id="786b6-124">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="786b6-124">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="786b6-125">❌ [8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="786b6-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="786b6-126">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="786b6-126">✔️ 2.1</span></span>        | <span data-ttu-id="786b6-127">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="786b6-127">❌ 3.1</span></span>        | <span data-ttu-id="786b6-128">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="786b6-128">❌ 5.0 Preview</span></span> |

<span data-ttu-id="786b6-129">以下版本的 .NET Core 不再受到支持。</span><span class="sxs-lookup"><span data-stu-id="786b6-129">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="786b6-130">这些版本的下载仍保持发布状态：</span><span class="sxs-lookup"><span data-stu-id="786b6-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="786b6-131">3.0</span><span class="sxs-lookup"><span data-stu-id="786b6-131">3.0</span></span>
- <span data-ttu-id="786b6-132">2.2</span><span class="sxs-lookup"><span data-stu-id="786b6-132">2.2</span></span>
- <span data-ttu-id="786b6-133">2.0</span><span class="sxs-lookup"><span data-stu-id="786b6-133">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="786b6-134">如何安装其他版本</span><span class="sxs-lookup"><span data-stu-id="786b6-134">How to install other versions</span></span>

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a><span data-ttu-id="786b6-135">Debian 10 ✔️</span><span class="sxs-lookup"><span data-stu-id="786b6-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="786b6-136">Debian 9 ✔️</span><span class="sxs-lookup"><span data-stu-id="786b6-136">Debian 9 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-8-"></a><span data-ttu-id="786b6-137">Debian 8 ❌</span><span class="sxs-lookup"><span data-stu-id="786b6-137">Debian 8 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-debian.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/8/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="786b6-138">APT 更新 SDK 或运行时</span><span class="sxs-lookup"><span data-stu-id="786b6-138">APT update SDK or runtime</span></span>

<span data-ttu-id="786b6-139">当新的修补程序版本适用于 .NET Core 时，只需使用以下命令通过 APT 进行升级：</span><span class="sxs-lookup"><span data-stu-id="786b6-139">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="786b6-140">APT 疑难解答</span><span class="sxs-lookup"><span data-stu-id="786b6-140">APT troubleshooting</span></span>

<span data-ttu-id="786b6-141">本部分提供有关使用 APT 安装 .NET Core 时可能会遇到的常见错误的信息。</span><span class="sxs-lookup"><span data-stu-id="786b6-141">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="786b6-142">找不到 \\ 无法安装某些包</span><span class="sxs-lookup"><span data-stu-id="786b6-142">Unable to locate \\ Some packages could not be installed</span></span>

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="786b6-143">未能提取</span><span class="sxs-lookup"><span data-stu-id="786b6-143">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="786b6-144">Snap</span><span class="sxs-lookup"><span data-stu-id="786b6-144">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="786b6-145">依赖项</span><span class="sxs-lookup"><span data-stu-id="786b6-145">Dependencies</span></span>

<span data-ttu-id="786b6-146">使用包管理器进行安装时，将为你安装这些库。</span><span class="sxs-lookup"><span data-stu-id="786b6-146">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="786b6-147">但是，如果手动安装 .NET Core 或发布自包含的应用，则需要确保已安装以下库：</span><span class="sxs-lookup"><span data-stu-id="786b6-147">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="786b6-148">libc6</span><span class="sxs-lookup"><span data-stu-id="786b6-148">libc6</span></span>
- <span data-ttu-id="786b6-149">libgcc1</span><span class="sxs-lookup"><span data-stu-id="786b6-149">libgcc1</span></span>
- <span data-ttu-id="786b6-150">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="786b6-150">libgssapi-krb5-2</span></span>
- <span data-ttu-id="786b6-151">libicu52（适用于 8.x）</span><span class="sxs-lookup"><span data-stu-id="786b6-151">libicu52 (for 8.x)</span></span>
- <span data-ttu-id="786b6-152">libicu57（适用于9.x）</span><span class="sxs-lookup"><span data-stu-id="786b6-152">libicu57 (for 9.x)</span></span>
- <span data-ttu-id="786b6-153">libicu63（适用于10.x）</span><span class="sxs-lookup"><span data-stu-id="786b6-153">libicu63 (for 10.x)</span></span>
- <span data-ttu-id="786b6-154">libicu67（适用于11.x）</span><span class="sxs-lookup"><span data-stu-id="786b6-154">libicu67 (for 11.x)</span></span>
- <span data-ttu-id="786b6-155">libssl1.0.0（适用于8.x）</span><span class="sxs-lookup"><span data-stu-id="786b6-155">libssl1.0.0 (for 8.x)</span></span>
- <span data-ttu-id="786b6-156">libssl1.1（适用于9.x-11.x）</span><span class="sxs-lookup"><span data-stu-id="786b6-156">libssl1.1 (for 9.x-11.x)</span></span>
- <span data-ttu-id="786b6-157">libstdc++6</span><span class="sxs-lookup"><span data-stu-id="786b6-157">libstdc++6</span></span>
- <span data-ttu-id="786b6-158">zlib1g</span><span class="sxs-lookup"><span data-stu-id="786b6-158">zlib1g</span></span>

<span data-ttu-id="786b6-159">对于使用 System.Drawing.Common 程序集的 .NET Core 应用，还需要以下依赖项：</span><span class="sxs-lookup"><span data-stu-id="786b6-159">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="786b6-160">libgdiplus（版本 6.0.1 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="786b6-160">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="786b6-161">可以通过将 Mono 存储库添加到系统来安装最新版 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="786b6-161">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="786b6-162">有关详细信息，请参阅 <https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="786b6-162">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="786b6-163">脚本安装</span><span class="sxs-lookup"><span data-stu-id="786b6-163">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="786b6-164">手动安装</span><span class="sxs-lookup"><span data-stu-id="786b6-164">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="786b6-165">后续步骤</span><span class="sxs-lookup"><span data-stu-id="786b6-165">Next steps</span></span>

- [<span data-ttu-id="786b6-166">教程：使用 Visual Studio Code 通过 .NET Core SDK 创建控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="786b6-166">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
