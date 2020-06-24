---
title: 在 SLES 上安装 .NET Core - .NET Core
description: 演示在 SLES 上安装 .NET Core SDK 和 .NET Core 运行时的各种方法。
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: b2eab6a0305d492e37e1b33d02be43ca41d42b6f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602788"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-sles"></a><span data-ttu-id="6db41-103">在 SLES 上安装 .NET Core SDK 或 .NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="6db41-103">Install .NET Core SDK or .NET Core Runtime on SLES</span></span>

<span data-ttu-id="6db41-104">SLES 支持 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="6db41-104">.NET Core is supported on SLES.</span></span> <span data-ttu-id="6db41-105">本文介绍如何在 SLES 上安装 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="6db41-105">This article describes how to install .NET Core on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="6db41-106">支持的发行版</span><span class="sxs-lookup"><span data-stu-id="6db41-106">Supported distributions</span></span>

<span data-ttu-id="6db41-107">下表列出了 SLES 12 SP2 和 SLES 15 上当前受支持的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="6db41-107">The following table is a list of currently supported .NET Core releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="6db41-108">这些版本在 [.NET Core 达到支持终止日期](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或 SLES 版本不再受到支持之前仍受支持。</span><span class="sxs-lookup"><span data-stu-id="6db41-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="6db41-109">✔️ 指示 SLES 或 .NET Core 版本仍受支持。</span><span class="sxs-lookup"><span data-stu-id="6db41-109">A ✔️ indicates that the version of SLES or .NET Core is still supported.</span></span>
- <span data-ttu-id="6db41-110">❌ 指示 SLES 或 .NET Core 版本在该 SLES 版本上不受支持。</span><span class="sxs-lookup"><span data-stu-id="6db41-110">A ❌ indicates that the version of SLES or .NET Core isn't supported on that SLES release.</span></span>
- <span data-ttu-id="6db41-111">当 SLES 版本和 .NET Core 版本都有 ✔️ 时，将支持该 OS 和 .NET 组合。</span><span class="sxs-lookup"><span data-stu-id="6db41-111">When both a version of SLES and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="6db41-112">SLES</span><span class="sxs-lookup"><span data-stu-id="6db41-112">SLES</span></span>                   | <span data-ttu-id="6db41-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6db41-113">.NET Core 2.1</span></span> | <span data-ttu-id="6db41-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="6db41-114">.NET Core 3.1</span></span> | <span data-ttu-id="6db41-115">.NET 5 预览版（仅限手动安装）</span><span class="sxs-lookup"><span data-stu-id="6db41-115">.NET 5 Preview (manual install only)</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="6db41-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="6db41-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="6db41-117">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="6db41-117">✔️ 2.1</span></span>        | <span data-ttu-id="6db41-118">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="6db41-118">✔️ 3.1</span></span>        | <span data-ttu-id="6db41-119">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="6db41-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="6db41-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="6db41-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="6db41-121">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="6db41-121">✔️ 2.1</span></span>        | <span data-ttu-id="6db41-122">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="6db41-122">✔️ 3.1</span></span>        | <span data-ttu-id="6db41-123">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="6db41-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="6db41-124">以下 .NET Core 版本不再受支持。</span><span class="sxs-lookup"><span data-stu-id="6db41-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="6db41-125">这些版本的下载仍保持发布状态：</span><span class="sxs-lookup"><span data-stu-id="6db41-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="6db41-126">3.0</span><span class="sxs-lookup"><span data-stu-id="6db41-126">3.0</span></span>
- <span data-ttu-id="6db41-127">2.2</span><span class="sxs-lookup"><span data-stu-id="6db41-127">2.2</span></span>
- <span data-ttu-id="6db41-128">2.0</span><span class="sxs-lookup"><span data-stu-id="6db41-128">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="6db41-129">如何安装其他版本</span><span class="sxs-lookup"><span data-stu-id="6db41-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="6db41-130">SLES 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="6db41-130">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="6db41-131">目前，SLES 15 Microsoft 存储库安装包会将 microsoft-prod.repo 文件安装到错误的目录，从而导致 zypper 找不到 .NET Core 包。</span><span class="sxs-lookup"><span data-stu-id="6db41-131">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="6db41-132">若要解决此问题，请在正确的目录中创建一个符号链接。</span><span class="sxs-lookup"><span data-stu-id="6db41-132">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="6db41-133">SLES 12 ✔️</span><span class="sxs-lookup"><span data-stu-id="6db41-133">SLES 12 ✔️</span></span>

<span data-ttu-id="6db41-134">SLES 12 系列的 .NET Core 需要至少为 SP2。</span><span class="sxs-lookup"><span data-stu-id="6db41-134">.NET Core requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="6db41-135">包管理器疑难解答</span><span class="sxs-lookup"><span data-stu-id="6db41-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="6db41-136">本部分提供有关使用程序包管理器安装 .NET Core 时可能会遇到的常见错误的信息。</span><span class="sxs-lookup"><span data-stu-id="6db41-136">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="6db41-137">未能提取</span><span class="sxs-lookup"><span data-stu-id="6db41-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="6db41-138">Snap</span><span class="sxs-lookup"><span data-stu-id="6db41-138">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="6db41-139">依赖项</span><span class="sxs-lookup"><span data-stu-id="6db41-139">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="6db41-140">脚本安装</span><span class="sxs-lookup"><span data-stu-id="6db41-140">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="6db41-141">手动安装</span><span class="sxs-lookup"><span data-stu-id="6db41-141">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="6db41-142">后续步骤</span><span class="sxs-lookup"><span data-stu-id="6db41-142">Next steps</span></span>

- [<span data-ttu-id="6db41-143">教程：使用 Visual Studio Code 通过 .NET Core SDK 创建控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="6db41-143">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
