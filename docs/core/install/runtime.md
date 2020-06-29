---
title: 在 Windows、Linux 和 macOS 上安装 .NET Core 运行时 - .NET Core
description: 了解如何在 Windows、Linux 和 macOS 上安装 .NET Core。 发现运行 .NET Core 应用所需的依赖项。
author: adegeo
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 6a0390ff1db900815628e4c7eb69e7a6c5f148a8
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324599"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="7a8bf-104">安装 .NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="7a8bf-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="7a8bf-105">本文介绍如何下载和安装 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="7a8bf-106">.NET Core 运行时用于运行使用 .NET Core 创建的应用。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="7a8bf-107">使用安装程序安装</span><span class="sxs-lookup"><span data-stu-id="7a8bf-107">Install with an installer</span></span>

<span data-ttu-id="7a8bf-108">Windows 具有独立的安装程序，可用于安装 .NET Core 3.1 运行时：</span><span class="sxs-lookup"><span data-stu-id="7a8bf-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="7a8bf-109">x64（64 位）CPU</span><span class="sxs-lookup"><span data-stu-id="7a8bf-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="7a8bf-110">x86（32 位）CPU</span><span class="sxs-lookup"><span data-stu-id="7a8bf-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="7a8bf-111">使用安装程序安装</span><span class="sxs-lookup"><span data-stu-id="7a8bf-111">Install with an installer</span></span>

<span data-ttu-id="7a8bf-112">macOS 具有独立的安装程序，可用于安装 .NET Core 3.1 运行时：</span><span class="sxs-lookup"><span data-stu-id="7a8bf-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="7a8bf-113">x64（64 位）CPU</span><span class="sxs-lookup"><span data-stu-id="7a8bf-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="7a8bf-114">下载并手动安装</span><span class="sxs-lookup"><span data-stu-id="7a8bf-114">Download and manually install</span></span>

<span data-ttu-id="7a8bf-115">除了使用适用于 .NET Core 的 macOS 安装程序，还可以下载并手动安装运行时。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-115">As an alternative to the macOS installers for .NET Core, you can download and manually install the runtime.</span></span>

<span data-ttu-id="7a8bf-116">若要安装运行时并使 .NET Core CLI 命令可用于终端，请先[下载](#all-net-core-downloads) .NET Core 二进制版本。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-116">To install the runtime and enable the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="7a8bf-117">然后，打开终端并运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-117">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="7a8bf-118">假定将运行时下载到 `~/Downloads/dotnet-runtime.pkg` 文件中。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-118">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-runtime.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a><span data-ttu-id="7a8bf-119">在 Linux 上安装</span><span class="sxs-lookup"><span data-stu-id="7a8bf-119">Install on Linux</span></span>

<span data-ttu-id="7a8bf-120">本文将很快删除。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-120">This article will be removed soon.</span></span> <span data-ttu-id="7a8bf-121">目前，它已被替换为[在 Linux 上安装 .NET Core](linux.md)。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-121">It is currently replaced by [Install .NET Core on Linux](linux.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="7a8bf-122">使用 PowerShell 自动化安装</span><span class="sxs-lookup"><span data-stu-id="7a8bf-122">Install with PowerShell automation</span></span>

<span data-ttu-id="7a8bf-123">[dotnet-install 脚本](../tools/dotnet-install-script.md)用于运行时的自动化和非管理员安装。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-123">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="7a8bf-124">可从 [dotnet-install 脚本引用页](../tools/dotnet-install-script.md)下载该脚本。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-124">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="7a8bf-125">此脚本默认安装最新的[长期支持 (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，即 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-125">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="7a8bf-126">可通过指定 `Channel` 开关以选择特定版本。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-126">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="7a8bf-127">包括 `Runtime` 开关以安装运行时。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-127">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="7a8bf-128">否则，该脚本安装 [SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-128">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="7a8bf-129">以上命令安装 ASP.NET Core 运行时，用于实现最大的兼容性。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-129">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="7a8bf-130">ASP.NET Core 运行时还包括标准 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-130">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="7a8bf-131">下载并手动安装</span><span class="sxs-lookup"><span data-stu-id="7a8bf-131">Download and manually install</span></span>

<span data-ttu-id="7a8bf-132">若要提取运行时并使 .NET Core CLI 命令可用于终端，请先[下载](#all-net-core-downloads) .NET Core 二进制版本。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-132">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="7a8bf-133">然后，创建要安装到的目录，例如 `%USERPROFILE%\dotnet`。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-133">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="7a8bf-134">最后，将下载的 zip 文件提取到该目录中。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-134">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="7a8bf-135">默认情况下，.NET Core CLI 命令和应用不会使用通过这种方式安装的 .NET Core，且你必须显式选择以使用它。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-135">By default, .NET Core CLI commands and apps won't use .NET Core installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="7a8bf-136">为此，请更改用于启动应用程序的环境变量：</span><span class="sxs-lookup"><span data-stu-id="7a8bf-136">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="7a8bf-137">使用此方法可以将多个版本安装到不同的位置，然后通过使用指向安装位置的环境变量运行应用程序来明确选择应用程序应使用哪个安装位置。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-137">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="7a8bf-138">即使已设置这些环境变量，在选择用于运行应用程序的最佳框架时，.NET Core 仍会考虑默认的全局安装位置。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-138">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="7a8bf-139">默认位置通常为安装程序使用的 `C:\Program Files\dotnet`。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-139">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="7a8bf-140">还可以通过设置此环境变量来指示运行时仅使用自定义安装位置：</span><span class="sxs-lookup"><span data-stu-id="7a8bf-140">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="7a8bf-141">使用 Bash 自动化安装</span><span class="sxs-lookup"><span data-stu-id="7a8bf-141">Install with bash automation</span></span>

<span data-ttu-id="7a8bf-142">[dotnet-install 脚本](../tools/dotnet-install-script.md)用于运行时的自动化和非管理员安装。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-142">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="7a8bf-143">可从 [dotnet-install 脚本引用页](../tools/dotnet-install-script.md)下载该脚本。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-143">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="7a8bf-144">此脚本默认安装最新的[长期支持 (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，即 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-144">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="7a8bf-145">可通过指定 `current` 开关以选择特定版本。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-145">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="7a8bf-146">包括 `runtime` 开关以安装运行时。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-146">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="7a8bf-147">否则，该脚本安装 [SDK](sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-147">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="7a8bf-148">以上命令安装 ASP.NET Core 运行时，用于实现最大的兼容性。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-148">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="7a8bf-149">ASP.NET Core 运行时还包括标准 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-149">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="7a8bf-150">所有 .NET Core 下载项</span><span class="sxs-lookup"><span data-stu-id="7a8bf-150">All .NET Core downloads</span></span>

<span data-ttu-id="7a8bf-151">可直接通过以下链接之一下载和安装 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="7a8bf-151">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="7a8bf-152">.NET Core 3.1 下载</span><span class="sxs-lookup"><span data-stu-id="7a8bf-152">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="7a8bf-153">.NET Core 2.1 下载</span><span class="sxs-lookup"><span data-stu-id="7a8bf-153">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="7a8bf-154">Docker</span><span class="sxs-lookup"><span data-stu-id="7a8bf-154">Docker</span></span>

<span data-ttu-id="7a8bf-155">容器提供了一种将应用程序与主机系统的其余部分隔离的轻量级方法。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-155">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="7a8bf-156">同一计算机上的容器只共享内核，并使用为应用程序提供的资源。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-156">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="7a8bf-157">.NET Core 可在 Docker 容器中运行。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-157">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="7a8bf-158">官方 .NET Core Docker 映像发布到 Microsoft 容器注册表 (MCR)，用户可以在 [Microsoft.NET Core Docker 中心存储库](https://hub.docker.com/_/microsoft-dotnet-core/)中找到这些映像。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-158">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="7a8bf-159">每个存储库包含 .NET（SDK 或运行时）和可以使用的操作系统的不同组合的映像。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-159">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="7a8bf-160">Microsoft 提供适合特定场景的映像。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-160">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="7a8bf-161">例如，[ASP.NET Core 存储库](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/)提供针对在生产环境中运行 ASP.NET Core 应用生成的映像。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-161">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="7a8bf-162">有关在 Docker 容器中使用 .NET Core 的详细信息，请参阅 [.NET 和 Docker 简介](../docker/introduction.md)和[示例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-162">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7a8bf-163">后续步骤</span><span class="sxs-lookup"><span data-stu-id="7a8bf-163">Next steps</span></span>

- <span data-ttu-id="7a8bf-164">[如何检查是否已安装 .NET Core](how-to-detect-installed-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="7a8bf-164">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
