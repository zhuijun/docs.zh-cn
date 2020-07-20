---
title: 在持续集成 (CI) 中使用 .NET Core SDK 和工具
description: 了解如何在具有持续集成的生成服务器上使用 .NET Core SDK 及其工具。
ms.date: 05/18/2017
ms.openlocfilehash: ddccb477bc112157a155e2217e04c329e7ab51c5
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2020
ms.locfileid: "86415989"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="aefeb-103">在持续集成 (CI) 中使用 .NET Core SDK 和工具</span><span class="sxs-lookup"><span data-stu-id="aefeb-103">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

<span data-ttu-id="aefeb-104">本文档概述了如何在生成服务器上使用 .NET Core SDK 及其工具。</span><span class="sxs-lookup"><span data-stu-id="aefeb-104">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="aefeb-105">.NET Core 工具集既可以交互方式运行（当开发者在命令提示符处键入命令时），也可以自动运行（当持续集成 (CI) 服务器运行生成脚本时）。</span><span class="sxs-lookup"><span data-stu-id="aefeb-105">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="aefeb-106">命令、选项、输入和输出都相同，可通过提供的唯一内容来获取用于生成应用的工具和系统。</span><span class="sxs-lookup"><span data-stu-id="aefeb-106">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="aefeb-107">本文档重点介绍了 CI 工具获取方案，并提供了有关如何设计和构建生成脚本的建议。</span><span class="sxs-lookup"><span data-stu-id="aefeb-107">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="aefeb-108">CI 生成服务器的安装选项</span><span class="sxs-lookup"><span data-stu-id="aefeb-108">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="aefeb-109">使用本机安装程序</span><span class="sxs-lookup"><span data-stu-id="aefeb-109">Using the native installers</span></span>

<span data-ttu-id="aefeb-110">本机安装程序适用于 macOS、Linux 和 Windows。</span><span class="sxs-lookup"><span data-stu-id="aefeb-110">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="aefeb-111">安装程序需要拥有对生成服务器的管理员 (sudo) 访问权限。</span><span class="sxs-lookup"><span data-stu-id="aefeb-111">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="aefeb-112">使用本机安装程序的优势在于，可以安装运行工具所需的全部本机依赖项。</span><span class="sxs-lookup"><span data-stu-id="aefeb-112">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="aefeb-113">本机安装程序还可以在整个系统内安装 SDK。</span><span class="sxs-lookup"><span data-stu-id="aefeb-113">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="aefeb-114">macOS 用户应使用 PKG 安装程序。</span><span class="sxs-lookup"><span data-stu-id="aefeb-114">macOS users should use the PKG installers.</span></span> <span data-ttu-id="aefeb-115">在 Linux 上，可选择使用基于源的包管理器（如用于 Ubuntu 的 apt-get 或用于 CentOS 的 yum），也可以选择使用包本身（即 DEB 或 RPM）。</span><span class="sxs-lookup"><span data-stu-id="aefeb-115">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="aefeb-116">在 Windows 上，使用 MSI 安装程序。</span><span class="sxs-lookup"><span data-stu-id="aefeb-116">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="aefeb-117">有关最新的稳定二进制文件，请参阅 [.NET 下载](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="aefeb-117">The latest stable binaries are found at [.NET downloads](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="aefeb-118">若要使用最新（但可能不稳定）的预览版工具，请使用 [dotnet/core-sdk GitHub 存储库](https://github.com/dotnet/core-sdk#installers-and-binaries)中提供的链接。</span><span class="sxs-lookup"><span data-stu-id="aefeb-118">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/core-sdk GitHub repository](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span> <span data-ttu-id="aefeb-119">对于 Linux 发行版本，可以使用 `tar.gz` 存档（亦称为 `tarballs`）；使用存档中的安装脚本来安装 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="aefeb-119">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="aefeb-120">使用安装程序脚本</span><span class="sxs-lookup"><span data-stu-id="aefeb-120">Using the installer script</span></span>

<span data-ttu-id="aefeb-121">使用安装程序脚本，可以在生成服务器上执行非管理员安装，并能轻松实现自动化，以便获取工具。</span><span class="sxs-lookup"><span data-stu-id="aefeb-121">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="aefeb-122">安装程序脚本负责下载并将工具提取到默认或指定位置，以供使用。</span><span class="sxs-lookup"><span data-stu-id="aefeb-122">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="aefeb-123">还可以指定要安装的工具版本，以及是要安装整个 SDK，还是仅安装共享运行时。</span><span class="sxs-lookup"><span data-stu-id="aefeb-123">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="aefeb-124">安装程序脚本在开始生成时自动运行，以提取和安装相应版本的 SDK。</span><span class="sxs-lookup"><span data-stu-id="aefeb-124">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="aefeb-125">相应版本  是指生成项目所需的任意 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="aefeb-125">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="aefeb-126">使用安装程序脚本，可以在服务器的本地目录中安装 SDK，并能从安装位置运行工具，还可以在生成后进行清理（或让 CI 服务进行清理）。</span><span class="sxs-lookup"><span data-stu-id="aefeb-126">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="aefeb-127">这样，可以封装和隔离整个生成进程。</span><span class="sxs-lookup"><span data-stu-id="aefeb-127">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="aefeb-128">有关安装脚本参考，请参阅 [dotnet-install](dotnet-install-script.md) 一文。</span><span class="sxs-lookup"><span data-stu-id="aefeb-128">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) article.</span></span>

> [!NOTE]
> <span data-ttu-id="aefeb-129">**Azure DevOps Services**</span><span class="sxs-lookup"><span data-stu-id="aefeb-129">**Azure DevOps Services**</span></span>
>
> <span data-ttu-id="aefeb-130">使用安装程序脚本时，不会自动安装本机依赖项。</span><span class="sxs-lookup"><span data-stu-id="aefeb-130">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="aefeb-131">如果操作系统没有本机依赖项，必须手动安装。</span><span class="sxs-lookup"><span data-stu-id="aefeb-131">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="aefeb-132">有关详细信息，请参阅 [.NET Core 依赖项和要求](../install/windows.md#dependencies)。</span><span class="sxs-lookup"><span data-stu-id="aefeb-132">For more information, see [.NET Core dependencies and requirements](../install/windows.md#dependencies).</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="aefeb-133">CI 安装示例</span><span class="sxs-lookup"><span data-stu-id="aefeb-133">CI setup examples</span></span>

<span data-ttu-id="aefeb-134">此部分介绍了如何使用 PowerShell 或 bash 脚本进行手动安装，同时还介绍了多个服务型软件 (SaaS) CI 解决方案。</span><span class="sxs-lookup"><span data-stu-id="aefeb-134">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="aefeb-135">涵盖的 SaaS CI 解决方案包括 [Travis CI](https://travis-ci.org/)、[AppVeyor](https://www.appveyor.com/) 和 [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index)。</span><span class="sxs-lookup"><span data-stu-id="aefeb-135">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="aefeb-136">手动安装</span><span class="sxs-lookup"><span data-stu-id="aefeb-136">Manual setup</span></span>

<span data-ttu-id="aefeb-137">每个 SaaS 服务都有自己的生成进程创建和配置方法。</span><span class="sxs-lookup"><span data-stu-id="aefeb-137">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="aefeb-138">如果使用与所列不同的 SaaS 解决方案，或需要超越预封装支持范围的自定义设置，至少必须执行一些手动配置。</span><span class="sxs-lookup"><span data-stu-id="aefeb-138">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="aefeb-139">一般来说，手动安装需要获取一个版本的工具（或最新每日版工具），再运行生成脚本。</span><span class="sxs-lookup"><span data-stu-id="aefeb-139">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="aefeb-140">可以使用 PowerShell 或 bash 脚本安排 .NET Core 命令，也可以使用概述生成进程的项目文件。</span><span class="sxs-lookup"><span data-stu-id="aefeb-140">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="aefeb-141">[业务流程部分](#orchestrating-the-build)详细介绍了这些选项。</span><span class="sxs-lookup"><span data-stu-id="aefeb-141">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="aefeb-142">创建执行手动 CI 生成服务器安装的脚本后，在开发计算机上使用它来生成本地代码以供测试。</span><span class="sxs-lookup"><span data-stu-id="aefeb-142">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="aefeb-143">确认此脚本可以在本地正常运行后，将它部署到 CI 生成服务器。</span><span class="sxs-lookup"><span data-stu-id="aefeb-143">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="aefeb-144">下面展示了相对简单的 PowerShell 脚本，以说明如何获取 .NET Core SDK，并将它安装到 Windows 生成服务器上：</span><span class="sxs-lookup"><span data-stu-id="aefeb-144">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

```powershell
$ErrorActionPreference="Stop"
$ProgressPreference="SilentlyContinue"

# $LocalDotnet is the path to the locally-installed SDK to ensure the
#   correct version of the tools are executed.
$LocalDotnet=""
# $InstallDir and $CliVersion variables can come from options to the
#   script.
$InstallDir = "./cli-tools"
$CliVersion = "1.0.1"

# Test the path provided by $InstallDir to confirm it exists. If it
#   does, it's removed. This is not strictly required, but it's a
#   good way to reset the environment.
if (Test-Path $InstallDir)
{
    rm -Recurse $InstallDir
}
New-Item -Type "directory" -Path $InstallDir

Write-Host "Downloading the CLI installer..."

# Use the Invoke-WebRequest PowerShell cmdlet to obtain the
#   installation script and save it into the installation directory.
Invoke-WebRequest `
    -Uri "https://dot.net/v1/dotnet-install.ps1" `
    -OutFile "$InstallDir/dotnet-install.ps1"

Write-Host "Installing the CLI requested version ($CliVersion) ..."

# Install the SDK of the version specified in $CliVersion into the
#   specified location ($InstallDir).
& $InstallDir/dotnet-install.ps1 -Version $CliVersion `
    -InstallDir $InstallDir

Write-Host "Downloading and installation of the SDK is complete."

# $LocalDotnet holds the path to dotnet.exe for future use by the
#   script.
$LocalDotnet = "$InstallDir/dotnet"

# Run the build process now. Implement your build script here.
```

<span data-ttu-id="aefeb-145">在此脚本末尾提供生成进程的实现代码。</span><span class="sxs-lookup"><span data-stu-id="aefeb-145">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="aefeb-146">此脚本先获取工具，再执行生成进程。</span><span class="sxs-lookup"><span data-stu-id="aefeb-146">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="aefeb-147">对于 UNIX 计算机，下面的 bash 脚本以类似方式执行 PowerShell 脚本中所述的操作：</span><span class="sxs-lookup"><span data-stu-id="aefeb-147">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

```bash
#!/bin/bash
INSTALLDIR="cli-tools"
CLI_VERSION=1.0.1
DOWNLOADER=$(which curl)
if [ -d "$INSTALLDIR" ]
then
    rm -rf "$INSTALLDIR"
fi
mkdir -p "$INSTALLDIR"
echo Downloading the CLI installer.
$DOWNLOADER https://dot.net/v1/dotnet-install.sh > "$INSTALLDIR/dotnet-install.sh"
chmod +x "$INSTALLDIR/dotnet-install.sh"
echo Installing the CLI requested version $CLI_VERSION. Please wait, installation may take a few minutes.
"$INSTALLDIR/dotnet-install.sh" --install-dir "$INSTALLDIR" --version $CLI_VERSION
if [ $? -ne 0 ]
then
    echo Download of $CLI_VERSION version of the CLI failed. Exiting now.
    exit 0
fi
echo The CLI has been installed.
LOCALDOTNET="$INSTALLDIR/dotnet"
# Run the build process now. Implement your build script here.
```

### <a name="travis-ci"></a><span data-ttu-id="aefeb-148">Travis CI</span><span class="sxs-lookup"><span data-stu-id="aefeb-148">Travis CI</span></span>

<span data-ttu-id="aefeb-149">可以将 [Travis CI](https://travis-ci.org/) 配置为使用 `csharp` 语言和 `dotnet` 键安装 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="aefeb-149">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="aefeb-150">有关详细信息，请参阅 Travis CI 官方文档[生成 C#、F# 或 Visual Basic 项目](https://docs.travis-ci.com/user/languages/csharp/)。</span><span class="sxs-lookup"><span data-stu-id="aefeb-150">For more information, see the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/).</span></span> <span data-ttu-id="aefeb-151">请注意，访问 Travis CI 信息时，社区维护的 `language: csharp` 语言标识符适用于所有 .NET 语言，包括 F# 和 Mono。</span><span class="sxs-lookup"><span data-stu-id="aefeb-151">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="aefeb-152">Travis CI 可同时在生成矩阵  中运行 macOS 和 Linux 作业。在生成矩阵中，可以指定运行时、环境和排除项/包含项的组合，从而涵盖应用的生成组合。</span><span class="sxs-lookup"><span data-stu-id="aefeb-152">Travis CI runs both macOS and Linux jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="aefeb-153">有关详细信息，请参阅 Travis CI 文档中的[自定义生成](https://docs.travis-ci.com/user/customizing-the-build)一文。</span><span class="sxs-lookup"><span data-stu-id="aefeb-153">For more information, see the [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) article in the Travis CI documentation.</span></span> <span data-ttu-id="aefeb-154">基于 MSBuild 的工具在包中添加 LTS (1.0.x) 和最新 (1.1.x) 运行时；因此，通过安装 SDK，可以收到执行生成所需的一切。</span><span class="sxs-lookup"><span data-stu-id="aefeb-154">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="aefeb-155">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="aefeb-155">AppVeyor</span></span>

<span data-ttu-id="aefeb-156">[AppVeyor](https://www.appveyor.com/) 使用 `Visual Studio 2017` 生成辅助角色映像安装 .NET Core 1.0.1 SDK。</span><span class="sxs-lookup"><span data-stu-id="aefeb-156">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="aefeb-157">提供具有不同版本的 .NET Core SDK 的其他生成映像。</span><span class="sxs-lookup"><span data-stu-id="aefeb-157">Other build images with different versions of the .NET Core SDK are available.</span></span> <span data-ttu-id="aefeb-158">有关详细信息，请参阅 AppVeyor 文档中的 [appveyor.yml 示例](https://github.com/dotnet/docs/blob/master/appveyor.yml)和[生成辅助角色映像](https://www.appveyor.com/docs/build-environment/#build-worker-images)一文。</span><span class="sxs-lookup"><span data-stu-id="aefeb-158">For more information, see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) article in the AppVeyor docs.</span></span>

<span data-ttu-id="aefeb-159">.NET Core SDK 二进制文件通过安装脚本下载并解压缩到子目录，再添加到 `PATH` 环境变量。</span><span class="sxs-lookup"><span data-stu-id="aefeb-159">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="aefeb-160">添加生成矩阵可以运行包含多个版本 .NET Core SDK 的集成测试：</span><span class="sxs-lookup"><span data-stu-id="aefeb-160">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a><span data-ttu-id="aefeb-161">Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="aefeb-161">Azure DevOps Services</span></span>

<span data-ttu-id="aefeb-162">将 Azure DevOps Services 配置为使用以下方法之一生成 .NET Core 项目：</span><span class="sxs-lookup"><span data-stu-id="aefeb-162">Configure Azure DevOps Services to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="aefeb-163">使用命令运行[手动安装步骤](#manual-setup)中的脚本。</span><span class="sxs-lookup"><span data-stu-id="aefeb-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="aefeb-164">创建包含多个 Azure DevOps Services 内置生成任务（这些任务被配置为使用 .NET Core 工具）的生成。</span><span class="sxs-lookup"><span data-stu-id="aefeb-164">Create a build composed of several Azure DevOps Services built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="aefeb-165">这两种均为有效解决方案。</span><span class="sxs-lookup"><span data-stu-id="aefeb-165">Both solutions are valid.</span></span> <span data-ttu-id="aefeb-166">使用手动安装脚本，可以控制收到的工具版本，因为工具是作为生成的一部分进行下载。</span><span class="sxs-lookup"><span data-stu-id="aefeb-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="aefeb-167">此生成是通过必须创建的脚本进行运行。</span><span class="sxs-lookup"><span data-stu-id="aefeb-167">The build is run from a script that you must create.</span></span> <span data-ttu-id="aefeb-168">本文仅涉及手动选项。</span><span class="sxs-lookup"><span data-stu-id="aefeb-168">This article only covers the manual option.</span></span> <span data-ttu-id="aefeb-169">有关使用 Azure DevOps Services 生成任务撰写生成的详细信息，请参阅 [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) 一文。</span><span class="sxs-lookup"><span data-stu-id="aefeb-169">For more information on composing a build with Azure DevOps Services build tasks, see the [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) documentation.</span></span>

<span data-ttu-id="aefeb-170">若要在 Azure DevOps Services 中使用手动安装脚本，请新建生成定义，并指定要对生成步骤运行的脚本。</span><span class="sxs-lookup"><span data-stu-id="aefeb-170">To use a manual setup script in Azure DevOps Services, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="aefeb-171">为此，请使用 Azure DevOps Services 用户界面：</span><span class="sxs-lookup"><span data-stu-id="aefeb-171">This is accomplished using the Azure DevOps Services user interface:</span></span>

1. <span data-ttu-id="aefeb-172">首先，新建生成定义。</span><span class="sxs-lookup"><span data-stu-id="aefeb-172">Start by creating a new build definition.</span></span> <span data-ttu-id="aefeb-173">到达可以定义要创建的生成类型的屏幕后，选择“空”  选项。</span><span class="sxs-lookup"><span data-stu-id="aefeb-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![选择空的生成定义](./media/using-ci-with-cli/select-empty-build-definition.png)

1. <span data-ttu-id="aefeb-175">配置要生成的存储库后，将转到生成定义。</span><span class="sxs-lookup"><span data-stu-id="aefeb-175">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="aefeb-176">选择“添加生成步骤”  ：</span><span class="sxs-lookup"><span data-stu-id="aefeb-176">Select **Add build step**:</span></span>

   ![添加生成步骤](./media/using-ci-with-cli/add-build-step.png)

1. <span data-ttu-id="aefeb-178">此时，系统会显示“任务目录”  。</span><span class="sxs-lookup"><span data-stu-id="aefeb-178">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="aefeb-179">此目录包含在生成中使用的任务。</span><span class="sxs-lookup"><span data-stu-id="aefeb-179">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="aefeb-180">由于已有脚本，因此选择“PowerShell:运行 PowerShell 脚本”旁边的“添加”按钮。</span><span class="sxs-lookup"><span data-stu-id="aefeb-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![添加 PowerShell 脚本步骤](./media/using-ci-with-cli/add-powershell-script.png)

1. <span data-ttu-id="aefeb-182">配置生成步骤。</span><span class="sxs-lookup"><span data-stu-id="aefeb-182">Configure the build step.</span></span> <span data-ttu-id="aefeb-183">从要生成的存储库中添加脚本：</span><span class="sxs-lookup"><span data-stu-id="aefeb-183">Add the script from the repository that you're building:</span></span>

   ![指定要运行的 PowerShell 脚本](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="aefeb-185">安排生成</span><span class="sxs-lookup"><span data-stu-id="aefeb-185">Orchestrating the build</span></span>

<span data-ttu-id="aefeb-186">本文档的大部分内容介绍了如何获取 .NET Core 工具和配置各种 CI 服务，并未介绍如何安排或实际生成  .NET Core 代码。</span><span class="sxs-lookup"><span data-stu-id="aefeb-186">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="aefeb-187">具体如何构建生成进程取决于许多因素，我们无法在本文中笼统概述。</span><span class="sxs-lookup"><span data-stu-id="aefeb-187">The choices on how to structure the build process depend on many factors that can't be covered in a general way here.</span></span> <span data-ttu-id="aefeb-188">有关使用每种技术安排生成的详细信息，请浏览 [Travis CI](https://travis-ci.org/)、[AppVeyor](https://www.appveyor.com/)、和 [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) 文档集中提供的资源和示例。</span><span class="sxs-lookup"><span data-stu-id="aefeb-188">For more information on orchestrating your builds with each technology, explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

<span data-ttu-id="aefeb-189">使用 .NET Core 工具构建 .NET Core 代码生成进程的两种常规方法是，直接使用 MSBuild 或使用 .NET Core 命令行命令。</span><span class="sxs-lookup"><span data-stu-id="aefeb-189">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="aefeb-190">应采用哪种方法取决于对方法的熟悉程度和复杂性取舍。</span><span class="sxs-lookup"><span data-stu-id="aefeb-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="aefeb-191">使用 MSBuild，可以将生成进程表达为任务和目标，但需要学习 MSBuild 项目文件语法，这增加了复杂性。</span><span class="sxs-lookup"><span data-stu-id="aefeb-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="aefeb-192">使用 .NET Core 命令行工具可能更为简单，但需要在 `bash` 或 PowerShell 等脚本语言中编写业务流程逻辑。</span><span class="sxs-lookup"><span data-stu-id="aefeb-192">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="aefeb-193">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aefeb-193">See also</span></span>

- [<span data-ttu-id="aefeb-194">.NET 下载 - Linux</span><span class="sxs-lookup"><span data-stu-id="aefeb-194">.NET downloads - Linux</span></span>](https://dotnet.microsoft.com/download?initial-os=linux)
