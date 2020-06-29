---
title: 删除 .NET Core 运行时和 SDK
description: 本文介绍如何确定当前安装的 .NET Core 运行时和 SDK 的版本，以及如何在 Windows、Mac 和 Linux 上删除它们。
author: adegeo
ms.author: adegeo
ms.date: 04/28/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 1e4a846cf5e3d0209f5ade873520ef64abc12e7c
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324648"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="6ee39-103">如何删除 .NET Core 运行时和 SDK</span><span class="sxs-lookup"><span data-stu-id="6ee39-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="6ee39-104">经过一段时间后，在安装 .NET Core 运行时和 SDK 的更新版本时，用户可能需要从计算机中删除过时的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="6ee39-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="6ee39-105">如有关 [.NET Core 版本选择](../versions/selection.md)的文章中详述，删除旧版运行时可能会更改为运行共享框架应用程序所选择的运行时。</span><span class="sxs-lookup"><span data-stu-id="6ee39-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](../versions/selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="6ee39-106">是否应删除某个版本？</span><span class="sxs-lookup"><span data-stu-id="6ee39-106">Should I remove a version?</span></span>

<span data-ttu-id="6ee39-107">借助 [.NET Core 版本选择](../versions/selection.md)行为和 .NET Core 各个更新之间的运行时兼容性，可安全地删除以前的版本。</span><span class="sxs-lookup"><span data-stu-id="6ee39-107">The [.NET Core version selection](../versions/selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="6ee39-108">.NET Core 运行时更新在主版本“区段”（如 1.x 和 2.x）中兼容。</span><span class="sxs-lookup"><span data-stu-id="6ee39-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="6ee39-109">此外，较新版本的 .NET Core SDK 通常能够以兼容的方式生成以运行时的早期版本为目标的应用程序。</span><span class="sxs-lookup"><span data-stu-id="6ee39-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="6ee39-110">通常，只需要应用程序所需的最新 SDK 和运行时的最新补丁版本。</span><span class="sxs-lookup"><span data-stu-id="6ee39-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="6ee39-111">需要保留旧版 SDK 或运行时版本的实例包括维护基于 project.json 的应用程序  。</span><span class="sxs-lookup"><span data-stu-id="6ee39-111">Instances where you might want to keep older SDK or runtime versions include maintaining *project.json*-based applications.</span></span> <span data-ttu-id="6ee39-112">除非应用程序有需保留早期 SDK 或运行时的特定原因，否则可以安全地删除旧版本。</span><span class="sxs-lookup"><span data-stu-id="6ee39-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="6ee39-113">确定安装内容</span><span class="sxs-lookup"><span data-stu-id="6ee39-113">Determine what is installed</span></span>

<span data-ttu-id="6ee39-114">从 .NET Core 2.1 开始，.NET CLI 提供一些可用于列出计算机上安装的 SDK 和运行时版本的选项。</span><span class="sxs-lookup"><span data-stu-id="6ee39-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="6ee39-115">使用 [`dotnet --list-sdks`](../tools/dotnet.md#options) 查看计算机上安装的 SDK 列表。</span><span class="sxs-lookup"><span data-stu-id="6ee39-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="6ee39-116">使用 [`dotnet --list-runtimes`](../tools/dotnet.md#options) 查看计算机上安装的运行时列表。</span><span class="sxs-lookup"><span data-stu-id="6ee39-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="6ee39-117">有关详细信息，请参阅[如何检查是否已安装 .NET Core](how-to-detect-installed-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="6ee39-117">For more information, see [How to check that .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>

## <a name="uninstall-net-core"></a><span data-ttu-id="6ee39-118">卸载 .NET Core</span><span class="sxs-lookup"><span data-stu-id="6ee39-118">Uninstall .NET Core</span></span>

::: zone pivot="os-windows"

<span data-ttu-id="6ee39-119">.NET Core 使用 Windows“应用和功能”对话框来删除 .NET Core 运行时和 SDK 的版本  。</span><span class="sxs-lookup"><span data-stu-id="6ee39-119">.NET Core uses the Windows **Apps & features** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="6ee39-120">下图显示了“应用和功能”对话框  。</span><span class="sxs-lookup"><span data-stu-id="6ee39-120">The following figure shows the **Apps & features** dialog.</span></span> <span data-ttu-id="6ee39-121">可以搜索“core sdk”来筛选和显示安装的 .NET Core 版本  。</span><span class="sxs-lookup"><span data-stu-id="6ee39-121">You can search for **core sdk** to filter and show installed versions of .NET Core.</span></span>

![用来删除 .NET Core 的“添加/删除程序”](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="6ee39-123">选择要从计算机中删除的任何版本，然后单击“卸载”  。</span><span class="sxs-lookup"><span data-stu-id="6ee39-123">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

::: zone-end

::: zone pivot="os-linux"

<span data-ttu-id="6ee39-124">Linux 还提供其他可用来卸载 .NET Core（SDK 或运行时）的选项。</span><span class="sxs-lookup"><span data-stu-id="6ee39-124">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="6ee39-125">卸载 .NET Core 的最佳方法是镜像用来安装 .NET Core 的操作。</span><span class="sxs-lookup"><span data-stu-id="6ee39-125">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="6ee39-126">具体取决于所选择的分发和安装方法。</span><span class="sxs-lookup"><span data-stu-id="6ee39-126">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6ee39-127">有关 Red Hat 安装，请参阅 [Red Hat 入门指南](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel)，了解有关安装和卸载 .NET Core 的信息。</span><span class="sxs-lookup"><span data-stu-id="6ee39-127">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="6ee39-128">从 .NET Core 2.1 开始，使用包管理器升级时无需卸载 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="6ee39-128">Starting with .NET Core 2.1, there's no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="6ee39-129">包管理器 `update` 或 `refresh` 命令将在成功安装较新版本后自动删除旧版本。</span><span class="sxs-lookup"><span data-stu-id="6ee39-129">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="6ee39-130">如果使用包管理器安装了 .NET Core，则使用同一包管理器卸载 .NET SDK 或运行时。</span><span class="sxs-lookup"><span data-stu-id="6ee39-130">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="6ee39-131">.NET Core 安装支持最常用的包管理器。</span><span class="sxs-lookup"><span data-stu-id="6ee39-131">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="6ee39-132">有关环境中的精确语法，请查阅分发的包管理器文档：</span><span class="sxs-lookup"><span data-stu-id="6ee39-132">Consult the documentation for your distribution's package manager for the precise syntax in your environment:</span></span>

- <span data-ttu-id="6ee39-133">[apt-get(8)](https://linux.die.net/man/8/apt-get) 由基于 Debian 的系统（包括 Ubuntu）使用。</span><span class="sxs-lookup"><span data-stu-id="6ee39-133">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="6ee39-134">[yum(8)](https://linux.die.net/man/8/yum) 用于 Fedora、CentOS 和 Oracle Linux。</span><span class="sxs-lookup"><span data-stu-id="6ee39-134">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="6ee39-135">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) 用于 openSUSE 和 SUSE Linux Enterprise System (SLES)。</span><span class="sxs-lookup"><span data-stu-id="6ee39-135">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="6ee39-136">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) 用于 Fedora。</span><span class="sxs-lookup"><span data-stu-id="6ee39-136">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="6ee39-137">几乎在所有情况下，删除包的命令都是 `remove`。</span><span class="sxs-lookup"><span data-stu-id="6ee39-137">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="6ee39-138">大多数包管理器的 .NET Core SDK 安装包名称为 `dotnet-sdk`，后跟版本号。</span><span class="sxs-lookup"><span data-stu-id="6ee39-138">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="6ee39-139">从 .NET Core SDK 2.1.300 版和运行时的 `2.1` 版开始，只需要主版本号和次版本号：例如，可将 .NET Core SDK 2.1.300 版引用为包 `dotnet-sdk-2.1`。</span><span class="sxs-lookup"><span data-stu-id="6ee39-139">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="6ee39-140">以前的版本则需要整个版本字符串：例如，.NET Core SDK 2.1.200 版需要 `dotnet-sdk-2.1.200`。</span><span class="sxs-lookup"><span data-stu-id="6ee39-140">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="6ee39-141">对于仅安装了运行时而未安装 SDK 的计算机，.NET Core 运行时的包名称为 `dotnet-runtime-<version>`，整个运行时堆栈的包名称为 `aspnetcore-runtime-<version>`。</span><span class="sxs-lookup"><span data-stu-id="6ee39-141">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="6ee39-142">使用包管理器卸载 SDK 时，2.0 之前的 .NET Core 安装不会卸载主机应用程序。</span><span class="sxs-lookup"><span data-stu-id="6ee39-142">.NET Core installations earlier than 2.0 didn't uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="6ee39-143">使用 `apt-get`，该命令为：</span><span class="sxs-lookup"><span data-stu-id="6ee39-143">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="6ee39-144">请注意，没有版本附加到 `dotnet-host`。</span><span class="sxs-lookup"><span data-stu-id="6ee39-144">Note that there's no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="6ee39-145">如果使用 tarball 安装，则必须使用手动方法删除 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="6ee39-145">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="6ee39-146">在 Linux 上，必须通过删除进行版本控制的目录，分别删除 SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="6ee39-146">On Linux, you must remove the SDKs and runtimes separately, by removing the versioned directories.</span></span> <span data-ttu-id="6ee39-147">删除它们会从磁盘中删除 SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="6ee39-147">Removing them deletes the SDK and runtime from disk.</span></span> <span data-ttu-id="6ee39-148">例如，要删除 1.0.1 SDK 和运行时，可使用以下 bash 命令：</span><span class="sxs-lookup"><span data-stu-id="6ee39-148">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

<span data-ttu-id="6ee39-149">SDK 和运行时的父目录列在 `dotnet --list-sdks` 和 `dotnet --list-runtimes` 命令的输出中，如上表所示。</span><span class="sxs-lookup"><span data-stu-id="6ee39-149">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="6ee39-150">在 Mac 上，必须通过删除进行版本控制的目录，分别删除 SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="6ee39-150">On Mac, you must remove the SDKs and runtimes separately, by removing the versioned directories.</span></span> <span data-ttu-id="6ee39-151">删除它们会从磁盘中删除 SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="6ee39-151">Removing them deletes the SDK and runtime from disk.</span></span> <span data-ttu-id="6ee39-152">例如，要删除 1.0.1 SDK 和运行时，可使用以下 bash 命令：</span><span class="sxs-lookup"><span data-stu-id="6ee39-152">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

<span data-ttu-id="6ee39-153">SDK 和运行时的父目录列在 `dotnet --list-sdks` 和 `dotnet --list-runtimes` 命令的输出中，如上表所示。</span><span class="sxs-lookup"><span data-stu-id="6ee39-153">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

::: zone-end

## <a name="net-core-uninstall-tool"></a><span data-ttu-id="6ee39-154">.NET Core 卸载工具</span><span class="sxs-lookup"><span data-stu-id="6ee39-154">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="6ee39-155">[.NET Core 卸载工具](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) 使你可以从系统中删除 .NET Core SDK 和运行时。</span><span class="sxs-lookup"><span data-stu-id="6ee39-155">The [.NET Core Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and runtimes from a system.</span></span> <span data-ttu-id="6ee39-156">可使用选项集合来指定应卸载的版本。</span><span class="sxs-lookup"><span data-stu-id="6ee39-156">A collection of options is available to specify which versions should be uninstalled.</span></span>

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a><span data-ttu-id="6ee39-157">.NET Core SDK 版本的 Visual Studio 依赖项</span><span class="sxs-lookup"><span data-stu-id="6ee39-157">Visual Studio dependency on .NET Core SDK versions</span></span>

<span data-ttu-id="6ee39-158">在 Visual Studio 2019 版本 16.3 之前，Visual Studio 安装程序称为独立的 .NET Core SDK 安装程序。</span><span class="sxs-lookup"><span data-stu-id="6ee39-158">Before Visual Studio 2019 version 16.3, Visual Studio installers called the standalone .NET Core SDK installer.</span></span> <span data-ttu-id="6ee39-159">因此，SDK 版本显示在 Windows“应用和功能”对话框中  。</span><span class="sxs-lookup"><span data-stu-id="6ee39-159">As a result, the SDK versions appear in the Windows **Apps & features** dialog.</span></span> <span data-ttu-id="6ee39-160">使用独立安装程序删除 Visual Studio 安装的 .NET Core SDK 可能会破坏 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="6ee39-160">Removing .NET Core SDKs that were installed by Visual Studio using the standalone installer may break Visual Studio.</span></span> <span data-ttu-id="6ee39-161">如果 Visual Studio 在卸载 SDK 之后出现问题，请在该特定版本的 Visual Studio 上运行修复。</span><span class="sxs-lookup"><span data-stu-id="6ee39-161">If Visual Studio has problems after you uninstall SDKs, run Repair on that specific version of Visual Studio.</span></span> <span data-ttu-id="6ee39-162">下表显示了 .NET Core SDK 版本的一些 Visual Studio 依赖项：</span><span class="sxs-lookup"><span data-stu-id="6ee39-162">The following table shows some of the Visual Studio dependencies on .NET Core SDK versions:</span></span>

| <span data-ttu-id="6ee39-163">Visual Studio 版本</span><span class="sxs-lookup"><span data-stu-id="6ee39-163">Visual Studio version</span></span>           | <span data-ttu-id="6ee39-164">.NET Core SDK 版本</span><span class="sxs-lookup"><span data-stu-id="6ee39-164">.NET Core SDK version</span></span>          |
|---------------------------------|--------------------------------|
| <span data-ttu-id="6ee39-165">Visual Studio 2019 版本 16.2</span><span class="sxs-lookup"><span data-stu-id="6ee39-165">Visual Studio 2019 version 16.2</span></span> | <span data-ttu-id="6ee39-166">.NET Core SDK 2.2.4xx、2.1.8xx</span><span class="sxs-lookup"><span data-stu-id="6ee39-166">.NET Core SDK 2.2.4xx, 2.1.8xx</span></span> |
| <span data-ttu-id="6ee39-167">Visual Studio 2019 版本 16.1</span><span class="sxs-lookup"><span data-stu-id="6ee39-167">Visual Studio 2019 version 16.1</span></span> | <span data-ttu-id="6ee39-168">.NET Core SDK 2.2.3xx、2.1.7xx</span><span class="sxs-lookup"><span data-stu-id="6ee39-168">.NET Core SDK 2.2.3xx, 2.1.7xx</span></span> |
| <span data-ttu-id="6ee39-169">Visual Studio 2019 版本 16.0</span><span class="sxs-lookup"><span data-stu-id="6ee39-169">Visual Studio 2019 version 16.0</span></span> | <span data-ttu-id="6ee39-170">.NET Core SDK 2.2.2xx、2.1.6xx</span><span class="sxs-lookup"><span data-stu-id="6ee39-170">.NET Core SDK 2.2.2xx, 2.1.6xx</span></span> |
| <span data-ttu-id="6ee39-171">Visual Studio 2017 版本 15.9</span><span class="sxs-lookup"><span data-stu-id="6ee39-171">Visual Studio 2017 version 15.9</span></span> | <span data-ttu-id="6ee39-172">.NET Core SDK 2.2.1xx、2.1.5xx</span><span class="sxs-lookup"><span data-stu-id="6ee39-172">.NET Core SDK 2.2.1xx, 2.1.5xx</span></span> |
| <span data-ttu-id="6ee39-173">Visual Studio 2017 版本 15.8</span><span class="sxs-lookup"><span data-stu-id="6ee39-173">Visual Studio 2017 version 15.8</span></span> | <span data-ttu-id="6ee39-174">.NET Core SDK 2.1.4xx</span><span class="sxs-lookup"><span data-stu-id="6ee39-174">.NET Core SDK 2.1.4xx</span></span>          |

<span data-ttu-id="6ee39-175">从 Visual Studio 2019 版本 16.3 开始，Visual Studio 负责其自己的 .NET Core SDK 副本。</span><span class="sxs-lookup"><span data-stu-id="6ee39-175">Starting with Visual Studio 2019 version 16.3, Visual Studio is in charge of its own copy of the .NET Core SDK.</span></span> <span data-ttu-id="6ee39-176">因此，“应用和功能”对话框中将不再显示这些 SDK 版本  。</span><span class="sxs-lookup"><span data-stu-id="6ee39-176">For that reason, you no longer see those SDK versions in the **Apps & features** dialog.</span></span>

## <a name="remove-the-nuget-fallback-folder"></a><span data-ttu-id="6ee39-177">删除 NuGet 回退文件夹</span><span class="sxs-lookup"><span data-stu-id="6ee39-177">Remove the NuGet fallback folder</span></span>

<span data-ttu-id="6ee39-178">在 .NET Core 3.0 SDK 之前，.NET Core SDK 安装程序使用名为 NuGetFallbackFolder 的文件夹存储 NuGet 包的缓存  。</span><span class="sxs-lookup"><span data-stu-id="6ee39-178">Before .NET Core 3.0 SDK, the .NET Core SDK installers used a folder named *NuGetFallbackFolder* to store a cache of NuGet packages.</span></span> <span data-ttu-id="6ee39-179">此缓存在操作期间（如 `dotnet restore` 或 `dotnet build /t:Restore`）使用。</span><span class="sxs-lookup"><span data-stu-id="6ee39-179">This cache was used during operations such as `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="6ee39-180">NuGetFallbackFolder 在 Windows 上位于 C:\Program Files\dotnet\sdk，在 macOS 上位于 /usr/local/share/dotnet/sdk    。</span><span class="sxs-lookup"><span data-stu-id="6ee39-180">The *NuGetFallbackFolder* is located at *C:\Program Files\dotnet\sdk* on Windows and at */usr/local/share/dotnet/sdk* on macOS.</span></span>

<span data-ttu-id="6ee39-181">如果是以下情况，则可能需要删除此文件夹：</span><span class="sxs-lookup"><span data-stu-id="6ee39-181">You may want to remove this folder, if:</span></span>

- <span data-ttu-id="6ee39-182">仅使用 .NET Core 3.0 SDK 或更高版本进行开发。</span><span class="sxs-lookup"><span data-stu-id="6ee39-182">You're only developing using .NET Core 3.0 SDK or later versions.</span></span>
- <span data-ttu-id="6ee39-183">你使用早于 3.0 的 .NET Core SDK 版本进行开发，但可以联机工作。</span><span class="sxs-lookup"><span data-stu-id="6ee39-183">You're developing using .NET Core SDK versions earlier than 3.0, but you can work online.</span></span>

<span data-ttu-id="6ee39-184">如果要删除 NuGet 回退文件夹，可以将其删除，但需要管理员权限才能执行此操作。</span><span class="sxs-lookup"><span data-stu-id="6ee39-184">If you want to remove the NuGet fallback folder, you can delete it, but you'll need admin privileges to do so.</span></span>

<span data-ttu-id="6ee39-185">建议不要删除 dotnet  文件夹。</span><span class="sxs-lookup"><span data-stu-id="6ee39-185">It's not recommended to delete the *dotnet* folder.</span></span> <span data-ttu-id="6ee39-186">这样做会删除以前安装的所有全局工具。</span><span class="sxs-lookup"><span data-stu-id="6ee39-186">Doing so would remove any global tools you've previously installed.</span></span> <span data-ttu-id="6ee39-187">此外，在 Windows 上：</span><span class="sxs-lookup"><span data-stu-id="6ee39-187">Also, on Windows:</span></span>

- <span data-ttu-id="6ee39-188">你将中断 Visual Studio 2019 版本 16.3 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="6ee39-188">You'll break Visual Studio 2019 version 16.3 and later versions.</span></span> <span data-ttu-id="6ee39-189">可以运行“修复”  来恢复。</span><span class="sxs-lookup"><span data-stu-id="6ee39-189">You can run **Repair** to recover.</span></span>
- <span data-ttu-id="6ee39-190">如果“应用和功能”对话框中存在 .NET Core SDK 条目，它们将是孤立的  。</span><span class="sxs-lookup"><span data-stu-id="6ee39-190">If there are .NET Core SDK entries in the **Apps & features** dialog, they'll be orphaned.</span></span>
