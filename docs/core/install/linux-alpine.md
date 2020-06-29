---
title: 在 Alpine 上安装 .NET Core - .NET Core
description: 演示在 Alpine 上安装 .NET Core SDK 和 .NET Core 运行时的各种方法。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 92753933cbcedae28867b66293d1044f700d7baa
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324832"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-alpine"></a><span data-ttu-id="525f3-103">在 Alpine 上安装 .NET Core SDK 或 .NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="525f3-103">Install .NET Core SDK or .NET Core Runtime on Alpine</span></span>

<span data-ttu-id="525f3-104">本文介绍如何在 Alpine 上安装 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="525f3-104">This article describes how to install .NET Core on Alpine.</span></span> <span data-ttu-id="525f3-105">如果 Alpine 版本不再受到支持，则该版本不再支持 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="525f3-105">When a Alpine version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="525f3-106">不过，这些说明可帮助你在这些版本上运行 .NET Core，即使它不受支持。</span><span class="sxs-lookup"><span data-stu-id="525f3-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

<span data-ttu-id="525f3-107">Alpine 没有安装程序。</span><span class="sxs-lookup"><span data-stu-id="525f3-107">There are no installers for Alpine.</span></span> <span data-ttu-id="525f3-108">必须使用[安装脚本](#scripted-install)或按照[手动安装](#manual-install)说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="525f3-108">You must either use the [install script](#scripted-install) or follow the [manual install](#manual-install) instructions.</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="525f3-109">支持的发行版</span><span class="sxs-lookup"><span data-stu-id="525f3-109">Supported distributions</span></span>

<span data-ttu-id="525f3-110">下表列出了当前支持的 .NET Core 版本以及支持它们的 Alpine 版本。</span><span class="sxs-lookup"><span data-stu-id="525f3-110">The following table is a list of currently supported .NET Core releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="525f3-111">这些版本在 [.NET Core 到达支持终止日期](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或 [Alpine 的版本到达有效期](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)之前仍受支持。</span><span class="sxs-lookup"><span data-stu-id="525f3-111">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="525f3-112">✔️ 指示 Alpine 或 .NET Core 版本仍受支持。</span><span class="sxs-lookup"><span data-stu-id="525f3-112">A ✔️ indicates that the version of Alpine or .NET Core is still supported.</span></span>
- <span data-ttu-id="525f3-113">❌ 指示 Alpine 或 .NET Core 版本在该 Alpine 发行版本上不受支持。</span><span class="sxs-lookup"><span data-stu-id="525f3-113">A ❌ indicates that the version of Alpine or .NET Core isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="525f3-114">当 Alpine 版本和 .NET Core 版本都有 ✔️ 时，则支持该 OS 和 .NET 的组合。</span><span class="sxs-lookup"><span data-stu-id="525f3-114">When both a version of Alpine and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="525f3-115">Alpine</span><span class="sxs-lookup"><span data-stu-id="525f3-115">Alpine</span></span>                   | <span data-ttu-id="525f3-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="525f3-116">.NET Core 2.1</span></span> | <span data-ttu-id="525f3-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="525f3-117">.NET Core 3.1</span></span> | <span data-ttu-id="525f3-118">.NET 5 预览版</span><span class="sxs-lookup"><span data-stu-id="525f3-118">.NET 5 Preview</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="525f3-119">✔️ 3.12</span><span class="sxs-lookup"><span data-stu-id="525f3-119">✔️ 3.12</span></span>  | <span data-ttu-id="525f3-120">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="525f3-120">✔️ 2.1</span></span>        | <span data-ttu-id="525f3-121">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="525f3-121">✔️ 3.1</span></span>        | <span data-ttu-id="525f3-122">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="525f3-122">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="525f3-123">✔️ 3.11</span><span class="sxs-lookup"><span data-stu-id="525f3-123">✔️ 3.11</span></span>  | <span data-ttu-id="525f3-124">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="525f3-124">✔️ 2.1</span></span>        | <span data-ttu-id="525f3-125">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="525f3-125">✔️ 3.1</span></span>        | <span data-ttu-id="525f3-126">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="525f3-126">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="525f3-127">✔️ 3.10</span><span class="sxs-lookup"><span data-stu-id="525f3-127">✔️ 3.10</span></span>  | <span data-ttu-id="525f3-128">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="525f3-128">✔️ 2.1</span></span>        | <span data-ttu-id="525f3-129">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="525f3-129">✔️ 3.1</span></span>        | <span data-ttu-id="525f3-130">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="525f3-130">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="525f3-131">✔️ 3.9</span><span class="sxs-lookup"><span data-stu-id="525f3-131">✔️ 3.9</span></span>   | <span data-ttu-id="525f3-132">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="525f3-132">✔️ 2.1</span></span>        | <span data-ttu-id="525f3-133">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="525f3-133">✔️ 3.1</span></span>        | <span data-ttu-id="525f3-134">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="525f3-134">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="525f3-135">❌ 3.8</span><span class="sxs-lookup"><span data-stu-id="525f3-135">❌ 3.8</span></span>   | <span data-ttu-id="525f3-136">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="525f3-136">✔️ 2.1</span></span>        | <span data-ttu-id="525f3-137">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="525f3-137">❌ 3.1</span></span>        | <span data-ttu-id="525f3-138">❌ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="525f3-138">❌ 5.0 Preview</span></span> |

<span data-ttu-id="525f3-139">以下版本的 .NET Core 不再受到支持。</span><span class="sxs-lookup"><span data-stu-id="525f3-139">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="525f3-140">这些版本的下载仍保持发布状态：</span><span class="sxs-lookup"><span data-stu-id="525f3-140">The downloads for these still remain published:</span></span>

- <span data-ttu-id="525f3-141">3.0</span><span class="sxs-lookup"><span data-stu-id="525f3-141">3.0</span></span>
- <span data-ttu-id="525f3-142">2.2</span><span class="sxs-lookup"><span data-stu-id="525f3-142">2.2</span></span>
- <span data-ttu-id="525f3-143">2.0</span><span class="sxs-lookup"><span data-stu-id="525f3-143">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="525f3-144">依赖项</span><span class="sxs-lookup"><span data-stu-id="525f3-144">Dependencies</span></span>

<span data-ttu-id="525f3-145">Alpine Linux 上的 .NET Core 要求安装以下依赖项：</span><span class="sxs-lookup"><span data-stu-id="525f3-145">.NET Core on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="525f3-146">icu-libs</span><span class="sxs-lookup"><span data-stu-id="525f3-146">icu-libs</span></span>
- <span data-ttu-id="525f3-147">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="525f3-147">krb5-libs</span></span>
- <span data-ttu-id="525f3-148">libintl</span><span class="sxs-lookup"><span data-stu-id="525f3-148">libintl</span></span>
- <span data-ttu-id="525f3-149">libssl1.1（Alpine v3.9 或更高版本）</span><span class="sxs-lookup"><span data-stu-id="525f3-149">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="525f3-150">libssl1.0 (Alpine v3.8)</span><span class="sxs-lookup"><span data-stu-id="525f3-150">libssl1.0 (Alpine v3.8)</span></span>
- <span data-ttu-id="525f3-151">libstdc++</span><span class="sxs-lookup"><span data-stu-id="525f3-151">libstdc++</span></span>
- <span data-ttu-id="525f3-152">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="525f3-152">lttng-ust</span></span>
- <span data-ttu-id="525f3-153">numactl（可选）</span><span class="sxs-lookup"><span data-stu-id="525f3-153">numactl (optional)</span></span>
- <span data-ttu-id="525f3-154">zlib</span><span class="sxs-lookup"><span data-stu-id="525f3-154">zlib</span></span>

## <a name="scripted-install"></a><span data-ttu-id="525f3-155">脚本安装</span><span class="sxs-lookup"><span data-stu-id="525f3-155">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="525f3-156">手动安装</span><span class="sxs-lookup"><span data-stu-id="525f3-156">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="525f3-157">后续步骤</span><span class="sxs-lookup"><span data-stu-id="525f3-157">Next steps</span></span>

- [<span data-ttu-id="525f3-158">教程：使用 Visual Studio Code 通过 .NET Core SDK 创建控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="525f3-158">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
