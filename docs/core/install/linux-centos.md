---
title: 在 CentOS 上安装 .NET Core - .NET Core
description: 演示在 CentOS 上安装 .NET Core SDK 和 .NET Core 运行时的各种方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 6b1bad3a6c967483bb683866de84c9e5077a336f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619502"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-centos"></a><span data-ttu-id="38000-103">在 CentOS 上安装 .NET Core SDK 或 .NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="38000-103">Install .NET Core SDK or .NET Core Runtime on CentOS</span></span>

<span data-ttu-id="38000-104">CentOS 支持 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="38000-104">.NET Core is supported on CentOS.</span></span> <span data-ttu-id="38000-105">本文介绍如何在 CentOS 上安装 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="38000-105">This article describes how to install .NET Core on CentOS.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="38000-106">支持的分发</span><span class="sxs-lookup"><span data-stu-id="38000-106">Supported distributions</span></span>

<span data-ttu-id="38000-107">下表列出了 CentOS 7 和 CentOS 8 上当前受支持的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="38000-107">The following table is a list of currently supported .NET Core releases on both CentOS 7 and CentOS 8.</span></span> <span data-ttu-id="38000-108">这些版本在 [.NET Core 版本达到支持终止日期](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或 CentOS 版本不再受支持之前仍受支持。</span><span class="sxs-lookup"><span data-stu-id="38000-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of CentOS is no longer supported.</span></span>

- <span data-ttu-id="38000-109">✔️ 指示 CentOS 或 .NET Core 版本仍受支持。</span><span class="sxs-lookup"><span data-stu-id="38000-109">A ✔️ indicates that the version of CentOS or .NET Core is still supported.</span></span>
- <span data-ttu-id="38000-110">❌ 指示 CentOS 或 .NET Core 版本在该 CentOS 版本上不受支持。</span><span class="sxs-lookup"><span data-stu-id="38000-110">A ❌ indicates that the version of CentOS or .NET Core isn't supported on that CentOS release.</span></span>
- <span data-ttu-id="38000-111">当 CentOS 版本和 .NET Core 版本都有 ✔️ 时，将支持该 OS 和 .NET 组合。</span><span class="sxs-lookup"><span data-stu-id="38000-111">When both a version of CentOS and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="38000-112">CentOS</span><span class="sxs-lookup"><span data-stu-id="38000-112">CentOS</span></span>                   | <span data-ttu-id="38000-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="38000-113">.NET Core 2.1</span></span> | <span data-ttu-id="38000-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="38000-114">.NET Core 3.1</span></span> | <span data-ttu-id="38000-115">.NET 5 预览版（仅限手动安装）</span><span class="sxs-lookup"><span data-stu-id="38000-115">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="38000-116">✔️ [8](#centos-8-)</span><span class="sxs-lookup"><span data-stu-id="38000-116">✔️ [8](#centos-8-)</span></span> | <span data-ttu-id="38000-117">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="38000-117">✔️ 2.1</span></span>        | <span data-ttu-id="38000-118">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="38000-118">✔️ 3.1</span></span>        | <span data-ttu-id="38000-119">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="38000-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="38000-120">✔️ [7](#centos-7-)</span><span class="sxs-lookup"><span data-stu-id="38000-120">✔️ [7](#centos-7-)</span></span> | <span data-ttu-id="38000-121">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="38000-121">✔️ 2.1</span></span>        | <span data-ttu-id="38000-122">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="38000-122">✔️ 3.1</span></span>        | <span data-ttu-id="38000-123">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="38000-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="38000-124">以下 .NET Core 版本不再受支持。</span><span class="sxs-lookup"><span data-stu-id="38000-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="38000-125">这些版本的下载仍保持发布状态：</span><span class="sxs-lookup"><span data-stu-id="38000-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="38000-126">3.0</span><span class="sxs-lookup"><span data-stu-id="38000-126">3.0</span></span>
- <span data-ttu-id="38000-127">2.2</span><span class="sxs-lookup"><span data-stu-id="38000-127">2.2</span></span>
- <span data-ttu-id="38000-128">2.0</span><span class="sxs-lookup"><span data-stu-id="38000-128">2.0</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="38000-129">如何安装其他版本</span><span class="sxs-lookup"><span data-stu-id="38000-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="centos-8-"></a><span data-ttu-id="38000-130">CentOS 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="38000-130">CentOS 8 ✔️</span></span>

<span data-ttu-id="38000-131">.NET Core 3.1 在 CentOS 8 的默认包存储库中提供。</span><span class="sxs-lookup"><span data-stu-id="38000-131">.NET Core 3.1 is available in the default package repositories for CentOS 8.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="centos-7-"></a><span data-ttu-id="38000-132">CentOS 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="38000-132">CentOS 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-yum-install-31](includes/linux-install-31-yum.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="38000-133">包管理器疑难解答</span><span class="sxs-lookup"><span data-stu-id="38000-133">Troubleshoot the package manager</span></span>

<span data-ttu-id="38000-134">本部分提供有关使用程序包管理器安装 .NET Core 时可能会遇到的常见错误的信息。</span><span class="sxs-lookup"><span data-stu-id="38000-134">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="38000-135">未能提取</span><span class="sxs-lookup"><span data-stu-id="38000-135">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="38000-136">Snap</span><span class="sxs-lookup"><span data-stu-id="38000-136">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="38000-137">依赖项</span><span class="sxs-lookup"><span data-stu-id="38000-137">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="38000-138">脚本安装</span><span class="sxs-lookup"><span data-stu-id="38000-138">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="38000-139">手动安装</span><span class="sxs-lookup"><span data-stu-id="38000-139">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="38000-140">后续步骤</span><span class="sxs-lookup"><span data-stu-id="38000-140">Next steps</span></span>

- [<span data-ttu-id="38000-141">教程：使用 Visual Studio Code 通过 .NET Core SDK 创建控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="38000-141">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
