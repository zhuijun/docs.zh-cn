---
title: 在 RHEL 上安装 .NET Core - .NET Core
description: 演示在 RHEL 上安装 .NET Core SDK 和 .NET Core 运行时的各种方法。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 9e4d0ab86355329b898a82f135b9eeb839eab1cb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619438"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-rhel"></a><span data-ttu-id="50bcb-103">在 RHEL 上安装 .NET Core SDK 或 .NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="50bcb-103">Install .NET Core SDK or .NET Core Runtime on RHEL</span></span>

<span data-ttu-id="50bcb-104">.NET Core 在 RHEL 上受支持。</span><span class="sxs-lookup"><span data-stu-id="50bcb-104">.NET Core is supported on RHEL.</span></span> <span data-ttu-id="50bcb-105">本文介绍如何在 RHEL 上安装 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="50bcb-105">This article describes how to install .NET Core on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="50bcb-106">注册 Red Hat 订阅</span><span class="sxs-lookup"><span data-stu-id="50bcb-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="50bcb-107">若要在 RHEL 上从 Red Hat 安装 .NET Core，首先需要使用 Red Hat 订阅管理器进行注册。</span><span class="sxs-lookup"><span data-stu-id="50bcb-107">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="50bcb-108">如果未在系统上完成此操作，或者不确定是否完成了此操作，请参阅[适用于 .NET Core 的 Red Hat 产品文档](https://access.redhat.com/documentation/net_core/)。</span><span class="sxs-lookup"><span data-stu-id="50bcb-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="50bcb-109">支持的发行版</span><span class="sxs-lookup"><span data-stu-id="50bcb-109">Supported distributions</span></span>

<span data-ttu-id="50bcb-110">下表列出了 RHEL 7 和 RHEL 8 上当前受支持的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="50bcb-110">The following table is a list of currently supported .NET Core releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="50bcb-111">这些版本在 [.NET Core 达到支持终止日期](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或 RHEL 版本不再受到支持之前仍受支持。</span><span class="sxs-lookup"><span data-stu-id="50bcb-111">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="50bcb-112">✔️ 指示 RHEL 或 .NET Core 版本仍受支持。</span><span class="sxs-lookup"><span data-stu-id="50bcb-112">A ✔️ indicates that the version of RHEL or .NET Core is still supported.</span></span>
- <span data-ttu-id="50bcb-113">❌ 指示 RHEL 或 .NET Core 版本在该 RHEL 版本上不受支持。</span><span class="sxs-lookup"><span data-stu-id="50bcb-113">A ❌ indicates that the version of RHEL or .NET Core isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="50bcb-114">当 RHEL 版本和 .NET Core 版本都有 ✔️ 时，将支持该 OS 和 .NET 组合。</span><span class="sxs-lookup"><span data-stu-id="50bcb-114">When both a version of RHEL and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="50bcb-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="50bcb-115">RHEL</span></span>                   | <span data-ttu-id="50bcb-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="50bcb-116">.NET Core 2.1</span></span> | <span data-ttu-id="50bcb-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="50bcb-117">.NET Core 3.1</span></span> | <span data-ttu-id="50bcb-118">.NET 5 预览版（仅限手动安装）</span><span class="sxs-lookup"><span data-stu-id="50bcb-118">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="50bcb-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="50bcb-119">✔️ [8](#rhel-8-)</span></span> | <span data-ttu-id="50bcb-120">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="50bcb-120">✔️ 2.1</span></span>        | <span data-ttu-id="50bcb-121">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="50bcb-121">✔️ 3.1</span></span>        | <span data-ttu-id="50bcb-122">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="50bcb-122">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="50bcb-123">✔️ [7](#rhel-7-)</span><span class="sxs-lookup"><span data-stu-id="50bcb-123">✔️ [7](#rhel-7-)</span></span> | <span data-ttu-id="50bcb-124">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="50bcb-124">✔️ 2.1</span></span>        | <span data-ttu-id="50bcb-125">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="50bcb-125">✔️ 3.1</span></span>        | <span data-ttu-id="50bcb-126">✔️ 5.0 预览版</span><span class="sxs-lookup"><span data-stu-id="50bcb-126">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="50bcb-127">以下版本的 .NET Core 不再受到支持。</span><span class="sxs-lookup"><span data-stu-id="50bcb-127">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="50bcb-128">这些版本的下载仍保持发布状态：</span><span class="sxs-lookup"><span data-stu-id="50bcb-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="50bcb-129">3.0</span><span class="sxs-lookup"><span data-stu-id="50bcb-129">3.0</span></span>
- <span data-ttu-id="50bcb-130">2.2</span><span class="sxs-lookup"><span data-stu-id="50bcb-130">2.2</span></span>
- <span data-ttu-id="50bcb-131">2.0</span><span class="sxs-lookup"><span data-stu-id="50bcb-131">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="50bcb-132">如何安装其他版本</span><span class="sxs-lookup"><span data-stu-id="50bcb-132">How to install other versions</span></span>

<span data-ttu-id="50bcb-133">有关安装其他版本的 .NET Core 所需的步骤，请参阅 [.NET Core 的 Red Hat 文档](https://access.redhat.com/documentation/net_core/)。</span><span class="sxs-lookup"><span data-stu-id="50bcb-133">Consult the [Red Hat documentation for .NET Core](https://access.redhat.com/documentation/net_core/) on the steps required to install other releases of .NET Core.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="50bcb-134">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="50bcb-134">RHEL 8 ✔️</span></span>

<span data-ttu-id="50bcb-135">.NET Core 包含在 RHEL 8 的应用流存储库中。</span><span class="sxs-lookup"><span data-stu-id="50bcb-135">.NET Core is included in the AppStream repositories for RHEL 8.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="rhel-7-"></a><span data-ttu-id="50bcb-136">RHEL 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="50bcb-136">RHEL 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="50bcb-137">以下命令安装 `scl-utils` 包：</span><span class="sxs-lookup"><span data-stu-id="50bcb-137">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="50bcb-138">安装 SDK</span><span class="sxs-lookup"><span data-stu-id="50bcb-138">Install the SDK</span></span>

<span data-ttu-id="50bcb-139">.NET Core SDK 使你可以通过 .NET Core 开发应用。</span><span class="sxs-lookup"><span data-stu-id="50bcb-139">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="50bcb-140">如果安装 .NET Core SDK，则无需安装相应的运行时。</span><span class="sxs-lookup"><span data-stu-id="50bcb-140">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="50bcb-141">若要安装 .NET Core SDK，请运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="50bcb-141">To install .NET Core SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="50bcb-142">Red Hat 建议不要永久启用 `rh-dotnet31`，因为这可能会影响其他程序。</span><span class="sxs-lookup"><span data-stu-id="50bcb-142">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="50bcb-143">例如，`rh-dotnet31` 包括与基本 RHEL 版本不同的 `libcurl` 版本。</span><span class="sxs-lookup"><span data-stu-id="50bcb-143">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="50bcb-144">这可能会导致不需要不同版本的 `libcurl` 的程序出现问题。</span><span class="sxs-lookup"><span data-stu-id="50bcb-144">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="50bcb-145">如果要永久启用 `rh-dotnet`，请将以下行添加到 ~/.bashrc 文件中。</span><span class="sxs-lookup"><span data-stu-id="50bcb-145">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a><span data-ttu-id="50bcb-146">安装运行时</span><span class="sxs-lookup"><span data-stu-id="50bcb-146">Install the runtime</span></span>

<span data-ttu-id="50bcb-147">.NET Core 运行时允许运行使用不随附运行时的 .NET Core 所开发的应用。</span><span class="sxs-lookup"><span data-stu-id="50bcb-147">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="50bcb-148">以下命令安装 ASP.NET Core 运行时，这是与 .NET Core 最兼容的运行时。</span><span class="sxs-lookup"><span data-stu-id="50bcb-148">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="50bcb-149">在终端中，运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="50bcb-149">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31-aspnetcore-runtime-3.1 bash
```

<span data-ttu-id="50bcb-150">Red Hat 建议不要永久启用 `rh-dotnet31-aspnetcore-runtime-3.1`，因为这可能会影响其他程序。</span><span class="sxs-lookup"><span data-stu-id="50bcb-150">Red Hat does not recommend permanently enabling `rh-dotnet31-aspnetcore-runtime-3.1` because it may affect other programs.</span></span> <span data-ttu-id="50bcb-151">例如，`rh-dotnet31-aspnetcore-runtime-3.1` 包括与基本 RHEL 版本不同的 `libcurl` 版本。</span><span class="sxs-lookup"><span data-stu-id="50bcb-151">For example, `rh-dotnet31-aspnetcore-runtime-3.1` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="50bcb-152">这可能会导致不需要不同版本的 `libcurl` 的程序出现问题。</span><span class="sxs-lookup"><span data-stu-id="50bcb-152">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="50bcb-153">如果要永久启用 `rh-dotnet31-aspnetcore-runtime-3.1`，请将以下行添加到 ~/.bashrc 文件中。</span><span class="sxs-lookup"><span data-stu-id="50bcb-153">If you want to enable `rh-dotnet31-aspnetcore-runtime-3.1` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31-aspnetcore-runtime-3.1
```

<span data-ttu-id="50bcb-154">作为 ASP.NET Core 运行时的一种替代方法，你可以安装不包含 ASP.NET Core 支持的 .NET Core 运行时：将上述命令中的 `rh-dotnet31-aspnetcore-runtime-3.1` 替换为 `rh-dotnet31-dotnet-runtime-3.1`。</span><span class="sxs-lookup"><span data-stu-id="50bcb-154">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet31-aspnetcore-runtime-3.1` in the commands above with `rh-dotnet31-dotnet-runtime-3.1`.</span></span>

## <a name="snap"></a><span data-ttu-id="50bcb-155">Snap</span><span class="sxs-lookup"><span data-stu-id="50bcb-155">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="50bcb-156">依赖项</span><span class="sxs-lookup"><span data-stu-id="50bcb-156">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="50bcb-157">脚本安装</span><span class="sxs-lookup"><span data-stu-id="50bcb-157">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="50bcb-158">手动安装</span><span class="sxs-lookup"><span data-stu-id="50bcb-158">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="50bcb-159">后续步骤</span><span class="sxs-lookup"><span data-stu-id="50bcb-159">Next steps</span></span>

- [<span data-ttu-id="50bcb-160">教程：使用 Visual Studio Code 通过 .NET Core SDK 创建控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="50bcb-160">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
