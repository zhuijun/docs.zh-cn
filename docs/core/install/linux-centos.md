---
title: 在 CentOS 上安装 .NET Core - .NET Core
description: 演示在 CentOS 上安装 .NET Core SDK 和 .NET Core 运行时的各种方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 7937502067e1717fd7f5c973c64ad33ae2a443a0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538613"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-centos"></a><span data-ttu-id="a7e75-103">在 CentOS 上安装 .NET Core SDK 或 .NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="a7e75-103">Install .NET Core SDK or .NET Core Runtime on CentOS</span></span>

<span data-ttu-id="a7e75-104">CentOS 支持 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="a7e75-104">.NET Core is supported on CentOS.</span></span> <span data-ttu-id="a7e75-105">本文介绍如何在 CentOS 上安装 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="a7e75-105">This article describes how to install .NET Core on CentOS.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="a7e75-106">支持的分发</span><span class="sxs-lookup"><span data-stu-id="a7e75-106">Supported distributions</span></span>

<span data-ttu-id="a7e75-107">下表列出了 CentOS 7 和 CentOS 8 上当前受支持的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="a7e75-107">The following table is a list of currently supported .NET Core releases on both CentOS 7 and CentOS 8.</span></span> <span data-ttu-id="a7e75-108">这些版本在 [.NET Core 版本达到支持终止日期](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或 CentOS 版本不再受支持之前仍受支持。</span><span class="sxs-lookup"><span data-stu-id="a7e75-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of CentOS is no longer supported.</span></span>

- <span data-ttu-id="a7e75-109">✔️ 指示 CentOS 或 .NET Core 版本仍受支持。</span><span class="sxs-lookup"><span data-stu-id="a7e75-109">A ✔️ indicates that the version of CentOS or .NET Core is still supported.</span></span>
- <span data-ttu-id="a7e75-110">❌ 指示 CentOS 或 .NET Core 版本在该 CentOS 版本上不受支持。</span><span class="sxs-lookup"><span data-stu-id="a7e75-110">A ❌ indicates that the version of CentOS or .NET Core isn't supported on that CentOS release.</span></span>
- <span data-ttu-id="a7e75-111">当 CentOS 版本和 .NET Core 版本都有 ✔️ 时，将支持该 OS 和 .NET 组合。</span><span class="sxs-lookup"><span data-stu-id="a7e75-111">When both a version of CentOS and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="a7e75-112">CentOS</span><span class="sxs-lookup"><span data-stu-id="a7e75-112">CentOS</span></span>                   | <span data-ttu-id="a7e75-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a7e75-113">.NET Core 2.1</span></span> | <span data-ttu-id="a7e75-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="a7e75-114">.NET Core 3.1</span></span> | <span data-ttu-id="a7e75-115">.NET 5 预览版（仅限手动安装）</span><span class="sxs-lookup"><span data-stu-id="a7e75-115">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="a7e75-116">✔️ [8](#centos-8-)</span><span class="sxs-lookup"><span data-stu-id="a7e75-116">✔️ [8](#centos-8-)</span></span> | <span data-ttu-id="a7e75-117">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="a7e75-117">✔️ 2.1</span></span>        | <span data-ttu-id="a7e75-118">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="a7e75-118">✔️ 3.1</span></span>        | <span data-ttu-id="a7e75-119">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="a7e75-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="a7e75-120">✔️ [7](#centos-7-)</span><span class="sxs-lookup"><span data-stu-id="a7e75-120">✔️ [7](#centos-7-)</span></span> | <span data-ttu-id="a7e75-121">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="a7e75-121">✔️ 2.1</span></span>        | <span data-ttu-id="a7e75-122">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="a7e75-122">✔️ 3.1</span></span>        | <span data-ttu-id="a7e75-123">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="a7e75-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="a7e75-124">以下 .NET Core 版本不再受支持。</span><span class="sxs-lookup"><span data-stu-id="a7e75-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="a7e75-125">这些版本的下载仍保持发布状态：</span><span class="sxs-lookup"><span data-stu-id="a7e75-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="a7e75-126">3.0</span><span class="sxs-lookup"><span data-stu-id="a7e75-126">3.0</span></span>
- <span data-ttu-id="a7e75-127">2.2</span><span class="sxs-lookup"><span data-stu-id="a7e75-127">2.2</span></span>
- <span data-ttu-id="a7e75-128">2.0</span><span class="sxs-lookup"><span data-stu-id="a7e75-128">2.0</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="a7e75-129">如何安装其他版本</span><span class="sxs-lookup"><span data-stu-id="a7e75-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="centos-8-"></a><span data-ttu-id="a7e75-130">CentOS 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="a7e75-130">CentOS 8 ✔️</span></span>

<span data-ttu-id="a7e75-131">.NET Core 3.1 在 CentOS 8 的默认包存储库中提供。</span><span class="sxs-lookup"><span data-stu-id="a7e75-131">.NET Core 3.1 is available in the default package repositories for CentOS 8.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="centos-7-"></a><span data-ttu-id="a7e75-132">CentOS 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="a7e75-132">CentOS 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-yum-install-31](includes/linux-install-31-yum.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="a7e75-133">包管理器疑难解答</span><span class="sxs-lookup"><span data-stu-id="a7e75-133">Troubleshoot the package manager</span></span>

<span data-ttu-id="a7e75-134">本部分提供有关使用程序包管理器安装 .NET Core 时可能会遇到的常见错误的信息。</span><span class="sxs-lookup"><span data-stu-id="a7e75-134">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="a7e75-135">找不到包</span><span class="sxs-lookup"><span data-stu-id="a7e75-135">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="a7e75-136">未能提取</span><span class="sxs-lookup"><span data-stu-id="a7e75-136">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="a7e75-137">Snap</span><span class="sxs-lookup"><span data-stu-id="a7e75-137">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="a7e75-138">依赖项</span><span class="sxs-lookup"><span data-stu-id="a7e75-138">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="a7e75-139">脚本安装</span><span class="sxs-lookup"><span data-stu-id="a7e75-139">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="a7e75-140">手动安装</span><span class="sxs-lookup"><span data-stu-id="a7e75-140">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="a7e75-141">后续步骤</span><span class="sxs-lookup"><span data-stu-id="a7e75-141">Next steps</span></span>

- [<span data-ttu-id="a7e75-142">教程：使用 Visual Studio Code 通过 .NET Core SDK 创建控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="a7e75-142">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
