---
title: 在 Debian 上安装 .NET Core - .NET Core
description: 演示在 Debian 上安装 .NET Core SDK 和 .NET Core 运行时的各种方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: ded9d2be72e8ec476d5ace752e44d92eb0ee1028
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324923"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-debian"></a><span data-ttu-id="06994-103">在 Debian 上安装 .NET Core SDK 或 .NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="06994-103">Install .NET Core SDK or .NET Core Runtime on Debian</span></span>

<span data-ttu-id="06994-104">本文介绍如何在 Debian 上安装 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="06994-104">This article describes how to install .NET Core on Debian.</span></span> <span data-ttu-id="06994-105">如果 Debian 版本不受支持，则该版本不再支持 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="06994-105">When a Debian version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="06994-106">不过，这些说明可能会帮助你让 .NET Core 在这些版本上运行，即使它不受支持。</span><span class="sxs-lookup"><span data-stu-id="06994-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="06994-107">支持的分发</span><span class="sxs-lookup"><span data-stu-id="06994-107">Supported distributions</span></span>

<span data-ttu-id="06994-108">下表列出了当前支持的 .NET Core 版本以及支持它们的 Debian 版本。</span><span class="sxs-lookup"><span data-stu-id="06994-108">The following table is a list of currently supported .NET Core releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="06994-109">这些版本在 [.NET Core 版本达到支持终止日期](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或 [Debian 的版本达到生命周期](https://wiki.debian.org/DebianReleases)之前仍受支持。</span><span class="sxs-lookup"><span data-stu-id="06994-109">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="06994-110">✔️ 指示 Debian 或 .NET Core 版本仍受支持。</span><span class="sxs-lookup"><span data-stu-id="06994-110">A ✔️ indicates that the version of Debian or .NET Core is still supported.</span></span>
- <span data-ttu-id="06994-111">❌ 指示 Debian 或 .NET Core 版本在该 Debian 版本上不受支持。</span><span class="sxs-lookup"><span data-stu-id="06994-111">A ❌ indicates that the version of Debian or .NET Core isn't supported on that Debian release.</span></span>
- <span data-ttu-id="06994-112">当 Debian 版本和 .NET Core 版本都有 ✔️ 时，将支持该 OS 和 .NET 组合。</span><span class="sxs-lookup"><span data-stu-id="06994-112">When both a version of Debian and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="06994-113">Debian</span><span class="sxs-lookup"><span data-stu-id="06994-113">Debian</span></span>                   | <span data-ttu-id="06994-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="06994-114">.NET Core 2.1</span></span> | <span data-ttu-id="06994-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="06994-115">.NET Core 3.1</span></span> | <span data-ttu-id="06994-116">.NET 5 预览版（仅限手动安装）</span><span class="sxs-lookup"><span data-stu-id="06994-116">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="06994-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="06994-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="06994-118">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="06994-118">✔️ 2.1</span></span>        | <span data-ttu-id="06994-119">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="06994-119">✔️ 3.1</span></span>        | <span data-ttu-id="06994-120">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="06994-120">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="06994-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="06994-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="06994-122">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="06994-122">✔️ 2.1</span></span>        | <span data-ttu-id="06994-123">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="06994-123">✔️ 3.1</span></span>        | <span data-ttu-id="06994-124">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="06994-124">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="06994-125">❌ [8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="06994-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="06994-126">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="06994-126">✔️ 2.1</span></span>        | <span data-ttu-id="06994-127">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="06994-127">❌ 3.1</span></span>        | <span data-ttu-id="06994-128">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="06994-128">❌ 5.0 Preview</span></span> |

<span data-ttu-id="06994-129">以下 .NET Core 版本不再受支持。</span><span class="sxs-lookup"><span data-stu-id="06994-129">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="06994-130">这些版本的下载仍保持发布状态：</span><span class="sxs-lookup"><span data-stu-id="06994-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="06994-131">3.0</span><span class="sxs-lookup"><span data-stu-id="06994-131">3.0</span></span>
- <span data-ttu-id="06994-132">2.2</span><span class="sxs-lookup"><span data-stu-id="06994-132">2.2</span></span>
- <span data-ttu-id="06994-133">2.0</span><span class="sxs-lookup"><span data-stu-id="06994-133">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="06994-134">如何安装其他版本</span><span class="sxs-lookup"><span data-stu-id="06994-134">How to install other versions</span></span>

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a><span data-ttu-id="06994-135">Debian 10 ✔️</span><span class="sxs-lookup"><span data-stu-id="06994-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="06994-136">Debian 9 ✔️</span><span class="sxs-lookup"><span data-stu-id="06994-136">Debian 9 ✔️</span></span>

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

## <a name="debian-8-"></a><span data-ttu-id="06994-137">Debian 8 ❌</span><span class="sxs-lookup"><span data-stu-id="06994-137">Debian 8 ❌</span></span>

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

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="06994-138">APT 更新 SDK 或运行时</span><span class="sxs-lookup"><span data-stu-id="06994-138">APT update SDK or runtime</span></span>

<span data-ttu-id="06994-139">当新的修补程序版本适用于 .NET Core 时，只需使用以下命令通过 APT 进行升级：</span><span class="sxs-lookup"><span data-stu-id="06994-139">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="06994-140">APT 疑难解答</span><span class="sxs-lookup"><span data-stu-id="06994-140">APT troubleshooting</span></span>

<span data-ttu-id="06994-141">本部分提供有关使用 APT 安装 .NET Core 时可能会遇到的常见错误的信息。</span><span class="sxs-lookup"><span data-stu-id="06994-141">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="06994-142">无法定位</span><span class="sxs-lookup"><span data-stu-id="06994-142">Unable to locate</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="06994-143">未能提取</span><span class="sxs-lookup"><span data-stu-id="06994-143">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="06994-144">Snap</span><span class="sxs-lookup"><span data-stu-id="06994-144">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="06994-145">依赖项</span><span class="sxs-lookup"><span data-stu-id="06994-145">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="06994-146">脚本安装</span><span class="sxs-lookup"><span data-stu-id="06994-146">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="06994-147">手动安装</span><span class="sxs-lookup"><span data-stu-id="06994-147">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="06994-148">后续步骤</span><span class="sxs-lookup"><span data-stu-id="06994-148">Next steps</span></span>

- [<span data-ttu-id="06994-149">教程：使用 Visual Studio Code 通过 .NET Core SDK 创建控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="06994-149">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
