---
title: dotnet tool update 命令
description: dotnet tool update 命令更新计算机上指定的 .NET Core 工具。
ms.date: 07/08/2020
ms.openlocfilehash: 7c4bde44ac9964828074baeb1a697ba64ed17887
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226616"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="e36b9-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="e36b9-103">dotnet tool update</span></span>

<span data-ttu-id="e36b9-104">本文适用于： ✔️ .NET Core 2.1 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="e36b9-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e36b9-105">“属性”</span><span class="sxs-lookup"><span data-stu-id="e36b9-105">Name</span></span>

<span data-ttu-id="e36b9-106">`dotnet tool update` - 更新计算机上指定的 [.NET Core 工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="e36b9-106">`dotnet tool update` - Updates the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e36b9-107">摘要</span><span class="sxs-lookup"><span data-stu-id="e36b9-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_ID> -g|--global
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [--add-source <SOURCE>] [--disable-parallel]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --tool-path <PATH>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [--add-source <SOURCE>] [--disable-parallel]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --local
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [--add-source <SOURCE>] [--disable-parallel]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [--tool-manifest <PATH>]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update -h|--help
```

## <a name="description"></a><span data-ttu-id="e36b9-108">描述</span><span class="sxs-lookup"><span data-stu-id="e36b9-108">Description</span></span>

<span data-ttu-id="e36b9-109">`dotnet tool update` 命令让你可以将计算机上的 .NET Core 工具更新为包的最新稳定版。</span><span class="sxs-lookup"><span data-stu-id="e36b9-109">The `dotnet tool update` command provides a way for you to update .NET Core tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="e36b9-110">此命令卸载并重新安装工具，有效地对工具进行更新。</span><span class="sxs-lookup"><span data-stu-id="e36b9-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="e36b9-111">若要使用命令，请指定以下选项之一：</span><span class="sxs-lookup"><span data-stu-id="e36b9-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="e36b9-112">若要更新安装在默认位置的全局工具，请使用 `--global` 选项</span><span class="sxs-lookup"><span data-stu-id="e36b9-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="e36b9-113">若要更新安装在自定义位置的全局工具，请使用 `--tool-path` 选项。</span><span class="sxs-lookup"><span data-stu-id="e36b9-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="e36b9-114">若要更新本地工具，请使用 `--local` 选项。</span><span class="sxs-lookup"><span data-stu-id="e36b9-114">To update a local tool, use the `--local` option.</span></span>

<span data-ttu-id="e36b9-115">**本地工具从 .NET Core SDK 3.0 开始可用。**</span><span class="sxs-lookup"><span data-stu-id="e36b9-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="e36b9-116">自变量</span><span class="sxs-lookup"><span data-stu-id="e36b9-116">Arguments</span></span>

- **`PACKAGE_ID`**

  <span data-ttu-id="e36b9-117">包含要更新的 .NET Core 全局工具的 NuGet 包的名称/ID。</span><span class="sxs-lookup"><span data-stu-id="e36b9-117">Name/ID of the NuGet package that contains the .NET Core global tool to update.</span></span> <span data-ttu-id="e36b9-118">你可以使用 [dotnet tool list](dotnet-tool-list.md) 命令查找包名称。</span><span class="sxs-lookup"><span data-stu-id="e36b9-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="e36b9-119">选项</span><span class="sxs-lookup"><span data-stu-id="e36b9-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="e36b9-120">添加安装过程中要使用的其他 NuGet 包源。</span><span class="sxs-lookup"><span data-stu-id="e36b9-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="e36b9-121">要使用的 NuGet 配置 (nuget.config) 文件。</span><span class="sxs-lookup"><span data-stu-id="e36b9-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="e36b9-122">防止并行还原多个项目。</span><span class="sxs-lookup"><span data-stu-id="e36b9-122">Prevent restoring multiple projects in parallel.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="e36b9-123">指定要更新工具的[目标框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="e36b9-123">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="e36b9-124">将包源失败视为警告。</span><span class="sxs-lookup"><span data-stu-id="e36b9-124">Treat package source failures as warnings.</span></span>

- **`--interactive`**

  <span data-ttu-id="e36b9-125">允许命令停止并等待用户输入或操作（例如，完成身份验证）。</span><span class="sxs-lookup"><span data-stu-id="e36b9-125">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`--local`**

  <span data-ttu-id="e36b9-126">更新工具和本地工具清单。</span><span class="sxs-lookup"><span data-stu-id="e36b9-126">Update the tool and the local tool manifest.</span></span> <span data-ttu-id="e36b9-127">不能与 `--global` 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="e36b9-127">Can't be combined with the `--global` option.</span></span>

- **`--no-cache`**

  <span data-ttu-id="e36b9-128">不要缓存包和 HTTP 请求。</span><span class="sxs-lookup"><span data-stu-id="e36b9-128">Do not cache packages and HTTP requests.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="e36b9-129">清单文件的路径。</span><span class="sxs-lookup"><span data-stu-id="e36b9-129">Path to the manifest file.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="e36b9-130">指定全局工具的安装位置。</span><span class="sxs-lookup"><span data-stu-id="e36b9-130">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="e36b9-131">路径可以是绝对的，也可以是相对的。</span><span class="sxs-lookup"><span data-stu-id="e36b9-131">PATH can be absolute or relative.</span></span> <span data-ttu-id="e36b9-132">不能与 `--global` 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="e36b9-132">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="e36b9-133">省略 `--global` 和 `--tool-path` 均指定要更新的工具是本地工具。</span><span class="sxs-lookup"><span data-stu-id="e36b9-133">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`--version <VERSION>`**

  <span data-ttu-id="e36b9-134">要将工具包更新到的版本范围。</span><span class="sxs-lookup"><span data-stu-id="e36b9-134">The version range of the tool package to update to.</span></span> <span data-ttu-id="e36b9-135">这不能用于降级版本，必须首先 `uninstall` 较新的版本。</span><span class="sxs-lookup"><span data-stu-id="e36b9-135">This cannot be used to downgrade versions, you must `uninstall` newer versions first.</span></span>

- **`-g|--global`**

  <span data-ttu-id="e36b9-136">指定此更新用于用户范围的工具。</span><span class="sxs-lookup"><span data-stu-id="e36b9-136">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="e36b9-137">不能与 `--tool-path` 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="e36b9-137">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="e36b9-138">省略 `--global` 和 `--tool-path` 均指定要更新的工具是本地工具。</span><span class="sxs-lookup"><span data-stu-id="e36b9-138">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="e36b9-139">打印出有关命令的简短帮助。</span><span class="sxs-lookup"><span data-stu-id="e36b9-139">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="e36b9-140">设置命令的详细级别。</span><span class="sxs-lookup"><span data-stu-id="e36b9-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e36b9-141">允许使用的值为 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="e36b9-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="e36b9-142">示例</span><span class="sxs-lookup"><span data-stu-id="e36b9-142">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="e36b9-143">更新 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 全局工具。</span><span class="sxs-lookup"><span data-stu-id="e36b9-143">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="e36b9-144">更新位于特定 Windows 目录的 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 全局工具。</span><span class="sxs-lookup"><span data-stu-id="e36b9-144">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="e36b9-145">更新位于特定 Linux/macOS 目录的 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 全局工具。</span><span class="sxs-lookup"><span data-stu-id="e36b9-145">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="e36b9-146">更新为当前目录安装的 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 本地工具。</span><span class="sxs-lookup"><span data-stu-id="e36b9-146">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

- **`dotnet tool update -g dotnetsay --version 2.0.*`**

  <span data-ttu-id="e36b9-147">将 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 全局工具更新到最新的修补程序版本，主版本为 `2`，次要版本为 `0`。</span><span class="sxs-lookup"><span data-stu-id="e36b9-147">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool to the latest patch version, with a major version of `2`, and a minor version of `0`.</span></span>

- **`dotnet tool update -g dotnetsay --version (2.0.*,2.1.4)`**

  <span data-ttu-id="e36b9-148">将 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 全局工具更新到指定范围 `(> 2.0.0 && < 2.1.4)` 内的最低版本，因此将安装版本 `2.1.0`。</span><span class="sxs-lookup"><span data-stu-id="e36b9-148">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool to the lowest version within the specified range `(> 2.0.0 && < 2.1.4)`, version `2.1.0` would be installed.</span></span> <span data-ttu-id="e36b9-149">有关语义化版本控制范围的详细信息，请参阅 [NuGet 打包版本范围](/nuget/concepts/package-versioning#version-ranges)。</span><span class="sxs-lookup"><span data-stu-id="e36b9-149">For more information on semantic versioning ranges, see [NuGet packaging version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span>

## <a name="see-also"></a><span data-ttu-id="e36b9-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="e36b9-150">See also</span></span>

- [<span data-ttu-id="e36b9-151">.NET Core 工具</span><span class="sxs-lookup"><span data-stu-id="e36b9-151">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="e36b9-152">语义化版本控制</span><span class="sxs-lookup"><span data-stu-id="e36b9-152">Semantic versioning</span></span>](https://semver.org)
- [<span data-ttu-id="e36b9-153">教程：使用 .NET Core CLI 安装和使用 .NET Core 全局工具</span><span class="sxs-lookup"><span data-stu-id="e36b9-153">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="e36b9-154">教程：使用 .NET Core CLI 安装和使用 .NET Core 本地工具</span><span class="sxs-lookup"><span data-stu-id="e36b9-154">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
