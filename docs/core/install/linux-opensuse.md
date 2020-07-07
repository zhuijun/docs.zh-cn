---
title: 在 openSUSE 上安装 .NET Core - .NET Core
description: 演示在 openSUSE 上安装 .NET Core SDK 和 .NET Core 运行时的各种方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 24f0a5b5278d038c2f941b0984efcacd91dcbe31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619463"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a><span data-ttu-id="64046-103">在 openSUSE 上安装 .NET Core SDK 或 .NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="64046-103">Install .NET Core SDK or .NET Core Runtime on openSUSE</span></span>

<span data-ttu-id="64046-104">openSUSE 支持 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="64046-104">.NET Core is supported on openSUSE.</span></span> <span data-ttu-id="64046-105">本文介绍如何在 openSUSE 上安装 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="64046-105">This article describes how to install .NET Core on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="64046-106">支持的分发</span><span class="sxs-lookup"><span data-stu-id="64046-106">Supported distributions</span></span>

<span data-ttu-id="64046-107">下表列出了 openSUSE 15 上当前受支持的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="64046-107">The following table is a list of currently supported .NET Core releases on openSUSE 15.</span></span> <span data-ttu-id="64046-108">这些版本在 [.NET Core 版本达到支持终止日期](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或 openSUSE 版本不再受支持之前仍受支持。</span><span class="sxs-lookup"><span data-stu-id="64046-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="64046-109">✔️ 指示 openSUSE 或 .NET Core 版本仍受支持。</span><span class="sxs-lookup"><span data-stu-id="64046-109">A ✔️ indicates that the version of openSUSE or .NET Core is still supported.</span></span>
- <span data-ttu-id="64046-110">❌ 指示 openSUSE 或 .NET Core 版本在该 openSUSE 版本上不受支持。</span><span class="sxs-lookup"><span data-stu-id="64046-110">A ❌ indicates that the version of openSUSE or .NET Core isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="64046-111">当 openSUSE 版本和 .NET Core 版本都有 ✔️ 时，将支持该 OS 和 .NET 组合。</span><span class="sxs-lookup"><span data-stu-id="64046-111">When both a version of openSUSE and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="64046-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="64046-112">openSUSE</span></span>                   | <span data-ttu-id="64046-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="64046-113">.NET Core 2.1</span></span> | <span data-ttu-id="64046-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="64046-114">.NET Core 3.1</span></span> | <span data-ttu-id="64046-115">.NET 5 预览版（仅限手动安装）</span><span class="sxs-lookup"><span data-stu-id="64046-115">.NET 5 Preview (manual install only)</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="64046-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="64046-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="64046-117">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="64046-117">✔️ 2.1</span></span>        | <span data-ttu-id="64046-118">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="64046-118">✔️ 3.1</span></span>        | <span data-ttu-id="64046-119">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="64046-119">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="64046-120">以下 .NET Core 版本不再受支持。</span><span class="sxs-lookup"><span data-stu-id="64046-120">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="64046-121">这些版本的下载仍保持发布状态：</span><span class="sxs-lookup"><span data-stu-id="64046-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="64046-122">3.0</span><span class="sxs-lookup"><span data-stu-id="64046-122">3.0</span></span>
- <span data-ttu-id="64046-123">2.2</span><span class="sxs-lookup"><span data-stu-id="64046-123">2.2</span></span>
- <span data-ttu-id="64046-124">2.0</span><span class="sxs-lookup"><span data-stu-id="64046-124">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="64046-125">如何安装其他版本</span><span class="sxs-lookup"><span data-stu-id="64046-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="64046-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="64046-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="64046-127">包管理器疑难解答</span><span class="sxs-lookup"><span data-stu-id="64046-127">Troubleshoot the package manager</span></span>

<span data-ttu-id="64046-128">本部分提供有关使用程序包管理器安装 .NET Core 时可能会遇到的常见错误的信息。</span><span class="sxs-lookup"><span data-stu-id="64046-128">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="64046-129">未能提取</span><span class="sxs-lookup"><span data-stu-id="64046-129">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="64046-130">Snap</span><span class="sxs-lookup"><span data-stu-id="64046-130">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="64046-131">依赖项</span><span class="sxs-lookup"><span data-stu-id="64046-131">Dependencies</span></span>

<span data-ttu-id="64046-132">使用包管理器进行安装时，将为你安装这些库。</span><span class="sxs-lookup"><span data-stu-id="64046-132">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="64046-133">但是，如果手动安装 .NET Core 或发布自包含的应用，则需要确保已安装以下库：</span><span class="sxs-lookup"><span data-stu-id="64046-133">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="64046-134">krb5</span><span class="sxs-lookup"><span data-stu-id="64046-134">krb5</span></span>
- <span data-ttu-id="64046-135">libicu</span><span class="sxs-lookup"><span data-stu-id="64046-135">libicu</span></span>
- <span data-ttu-id="64046-136">libopenssl1_0_0</span><span class="sxs-lookup"><span data-stu-id="64046-136">libopenssl1_0_0</span></span>

<span data-ttu-id="64046-137">如果目标运行时环境的 OpenSSL 版本为1.1 或更高版本，则需要安装 compat-openssl10。</span><span class="sxs-lookup"><span data-stu-id="64046-137">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="64046-138">有关依赖项的详细信息，请参阅[独立式 Linux 应用](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="64046-138">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="64046-139">对于使用 System.Drawing.Common 程序集的 .NET Core 应用，还需要以下依赖项：</span><span class="sxs-lookup"><span data-stu-id="64046-139">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="64046-140">libgdiplus（版本 6.0.1 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="64046-140">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="64046-141">可以通过将 Mono 存储库添加到系统来安装最新版 libgdiplus。</span><span class="sxs-lookup"><span data-stu-id="64046-141">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="64046-142">有关详细信息，请参阅 <https://www.mono-project.com/download/stable/>。</span><span class="sxs-lookup"><span data-stu-id="64046-142">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="64046-143">脚本安装</span><span class="sxs-lookup"><span data-stu-id="64046-143">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="64046-144">手动安装</span><span class="sxs-lookup"><span data-stu-id="64046-144">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="64046-145">后续步骤</span><span class="sxs-lookup"><span data-stu-id="64046-145">Next steps</span></span>

- [<span data-ttu-id="64046-146">教程：使用 Visual Studio Code 通过 .NET Core SDK 创建控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="64046-146">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
