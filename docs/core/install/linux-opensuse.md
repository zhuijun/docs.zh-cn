---
title: 在 openSUSE 上安装 .NET Core - .NET Core
description: 演示在 openSUSE 上安装 .NET Core SDK 和 .NET Core 运行时的各种方式。
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: a642cee9ae78f81cd671d8745d5ce241be6a3b69
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602800"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a><span data-ttu-id="dc091-103">在 openSUSE 上安装 .NET Core SDK 或 .NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="dc091-103">Install .NET Core SDK or .NET Core Runtime on openSUSE</span></span>

<span data-ttu-id="dc091-104">openSUSE 支持 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="dc091-104">.NET Core is supported on openSUSE.</span></span> <span data-ttu-id="dc091-105">本文介绍如何在 openSUSE 上安装 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="dc091-105">This article describes how to install .NET Core on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="dc091-106">支持的分发</span><span class="sxs-lookup"><span data-stu-id="dc091-106">Supported distributions</span></span>

<span data-ttu-id="dc091-107">下表列出了 openSUSE 15 上当前受支持的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="dc091-107">The following table is a list of currently supported .NET Core releases on openSUSE 15.</span></span> <span data-ttu-id="dc091-108">这些版本在 [.NET Core 版本达到支持终止日期](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或 openSUSE 版本不再受支持之前仍受支持。</span><span class="sxs-lookup"><span data-stu-id="dc091-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="dc091-109">✔️ 指示 openSUSE 或 .NET Core 版本仍受支持。</span><span class="sxs-lookup"><span data-stu-id="dc091-109">A ✔️ indicates that the version of openSUSE or .NET Core is still supported.</span></span>
- <span data-ttu-id="dc091-110">❌ 指示 openSUSE 或 .NET Core 版本在该 openSUSE 版本上不受支持。</span><span class="sxs-lookup"><span data-stu-id="dc091-110">A ❌ indicates that the version of openSUSE or .NET Core isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="dc091-111">当 openSUSE 版本和 .NET Core 版本都有 ✔️ 时，将支持该 OS 和 .NET 组合。</span><span class="sxs-lookup"><span data-stu-id="dc091-111">When both a version of openSUSE and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="dc091-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="dc091-112">openSUSE</span></span>                   | <span data-ttu-id="dc091-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="dc091-113">.NET Core 2.1</span></span> | <span data-ttu-id="dc091-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="dc091-114">.NET Core 3.1</span></span> | <span data-ttu-id="dc091-115">.NET 5 预览版（仅限手动安装）</span><span class="sxs-lookup"><span data-stu-id="dc091-115">.NET 5 Preview (manual install only)</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="dc091-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="dc091-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="dc091-117">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="dc091-117">✔️ 2.1</span></span>        | <span data-ttu-id="dc091-118">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="dc091-118">✔️ 3.1</span></span>        | <span data-ttu-id="dc091-119">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="dc091-119">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="dc091-120">以下 .NET Core 版本不再受支持。</span><span class="sxs-lookup"><span data-stu-id="dc091-120">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="dc091-121">这些版本的下载仍保持发布状态：</span><span class="sxs-lookup"><span data-stu-id="dc091-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="dc091-122">3.0</span><span class="sxs-lookup"><span data-stu-id="dc091-122">3.0</span></span>
- <span data-ttu-id="dc091-123">2.2</span><span class="sxs-lookup"><span data-stu-id="dc091-123">2.2</span></span>
- <span data-ttu-id="dc091-124">2.0</span><span class="sxs-lookup"><span data-stu-id="dc091-124">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="dc091-125">如何安装其他版本</span><span class="sxs-lookup"><span data-stu-id="dc091-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="dc091-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="dc091-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="dc091-127">包管理器疑难解答</span><span class="sxs-lookup"><span data-stu-id="dc091-127">Troubleshoot the package manager</span></span>

<span data-ttu-id="dc091-128">本部分提供有关使用程序包管理器安装 .NET Core 时可能会遇到的常见错误的信息。</span><span class="sxs-lookup"><span data-stu-id="dc091-128">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="dc091-129">未能提取</span><span class="sxs-lookup"><span data-stu-id="dc091-129">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="dc091-130">Snap</span><span class="sxs-lookup"><span data-stu-id="dc091-130">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="dc091-131">依赖项</span><span class="sxs-lookup"><span data-stu-id="dc091-131">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="dc091-132">脚本安装</span><span class="sxs-lookup"><span data-stu-id="dc091-132">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="dc091-133">手动安装</span><span class="sxs-lookup"><span data-stu-id="dc091-133">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="dc091-134">后续步骤</span><span class="sxs-lookup"><span data-stu-id="dc091-134">Next steps</span></span>

- [<span data-ttu-id="dc091-135">教程：使用 Visual Studio Code 通过 .NET Core SDK 创建控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="dc091-135">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
