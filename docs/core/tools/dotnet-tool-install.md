---
title: dotnet tool install 命令
description: dotnet tool install 命令在计算机上安装指定的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: 067f90124833da537370a36934ff212aba7577f3
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702812"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="cfb55-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="cfb55-103">dotnet tool install</span></span>

<span data-ttu-id="cfb55-104">本文适用于： ✔️ .NET Core 2.1 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="cfb55-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="cfb55-105">“属性”</span><span class="sxs-lookup"><span data-stu-id="cfb55-105">Name</span></span>

<span data-ttu-id="cfb55-106">`dotnet tool install` - 在计算机上安装指定的 [.NET Core 工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="cfb55-106">`dotnet tool install` - Installs the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cfb55-107">摘要</span><span class="sxs-lookup"><span data-stu-id="cfb55-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install -h|--help
```

## <a name="description"></a><span data-ttu-id="cfb55-108">描述</span><span class="sxs-lookup"><span data-stu-id="cfb55-108">Description</span></span>

<span data-ttu-id="cfb55-109">`dotnet tool install` 命令为用户提供一种在计算机上安装 .NET Core 工具的方法。</span><span class="sxs-lookup"><span data-stu-id="cfb55-109">The `dotnet tool install` command provides a way for you to install .NET Core tools on your machine.</span></span> <span data-ttu-id="cfb55-110">若要使用命令，请指定以下安装选项之一：</span><span class="sxs-lookup"><span data-stu-id="cfb55-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="cfb55-111">若要在默认位置中安装全局工具，请使用 `--global` 选项。</span><span class="sxs-lookup"><span data-stu-id="cfb55-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="cfb55-112">若要在自定义位置中安装全局工具，请使用 `--tool-path` 选项。</span><span class="sxs-lookup"><span data-stu-id="cfb55-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="cfb55-113">若要安装本地工具，请省略 `--global` 和 `--tool-path` 选项。</span><span class="sxs-lookup"><span data-stu-id="cfb55-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="cfb55-114">**本地工具从 .NET Core SDK 3.0 开始可用。**</span><span class="sxs-lookup"><span data-stu-id="cfb55-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="cfb55-115">指定 `-g` 或 `--global` 选项时，全局工具默认安装在以下目录中：</span><span class="sxs-lookup"><span data-stu-id="cfb55-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="cfb55-116">(OS)</span><span class="sxs-lookup"><span data-stu-id="cfb55-116">OS</span></span>          | <span data-ttu-id="cfb55-117">路径</span><span class="sxs-lookup"><span data-stu-id="cfb55-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="cfb55-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="cfb55-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="cfb55-119">Windows</span><span class="sxs-lookup"><span data-stu-id="cfb55-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="cfb55-120">本地工具将添加到当前目录下 .config 目录中的 dotnet-tools.json 文件中。</span><span class="sxs-lookup"><span data-stu-id="cfb55-120">Local tools are added to a *dotnet-tools.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="cfb55-121">如果清单文件尚不存在，请通过运行以下命令来创建它：</span><span class="sxs-lookup"><span data-stu-id="cfb55-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="cfb55-122">有关详细信息，请参阅[安装本地工具](global-tools.md#install-a-local-tool)。</span><span class="sxs-lookup"><span data-stu-id="cfb55-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="cfb55-123">自变量</span><span class="sxs-lookup"><span data-stu-id="cfb55-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="cfb55-124">包含要安装的 .NET Core 工具的 NuGet 包的名称/ID。</span><span class="sxs-lookup"><span data-stu-id="cfb55-124">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="cfb55-125">选项</span><span class="sxs-lookup"><span data-stu-id="cfb55-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="cfb55-126">添加安装过程中要使用的其他 NuGet 包源。</span><span class="sxs-lookup"><span data-stu-id="cfb55-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="cfb55-127">要使用的 NuGet 配置 (nuget.config) 文件。</span><span class="sxs-lookup"><span data-stu-id="cfb55-127">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="cfb55-128">指定要安装工具的[目标框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="cfb55-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="cfb55-129">默认情况下，.NET Core SDK 尝试选择最合适的目标框架。</span><span class="sxs-lookup"><span data-stu-id="cfb55-129">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="cfb55-130">指定安装是用户范围的。</span><span class="sxs-lookup"><span data-stu-id="cfb55-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="cfb55-131">不能与 `--tool-path` 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="cfb55-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="cfb55-132">省略 `--global` 和 `--tool-path` 指定本地工具安装。</span><span class="sxs-lookup"><span data-stu-id="cfb55-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-h|--help`**

  <span data-ttu-id="cfb55-133">打印出有关命令的简短帮助。</span><span class="sxs-lookup"><span data-stu-id="cfb55-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="cfb55-134">指定全局工具的安装位置。</span><span class="sxs-lookup"><span data-stu-id="cfb55-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="cfb55-135">路径可以是绝对的，也可以是相对的。</span><span class="sxs-lookup"><span data-stu-id="cfb55-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="cfb55-136">如果路径不存在，命令会尝试创建它。</span><span class="sxs-lookup"><span data-stu-id="cfb55-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="cfb55-137">省略 `--global` 和 `--tool-path` 指定本地工具安装。</span><span class="sxs-lookup"><span data-stu-id="cfb55-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="cfb55-138">设置命令的详细级别。</span><span class="sxs-lookup"><span data-stu-id="cfb55-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="cfb55-139">允许使用的值为 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。</span><span class="sxs-lookup"><span data-stu-id="cfb55-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="cfb55-140">要安装的工具版本。</span><span class="sxs-lookup"><span data-stu-id="cfb55-140">The version of the tool to install.</span></span> <span data-ttu-id="cfb55-141">默认情况下，安装最新的稳定包版本。</span><span class="sxs-lookup"><span data-stu-id="cfb55-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="cfb55-142">使用此选项安装工具的预览版或较旧版本。</span><span class="sxs-lookup"><span data-stu-id="cfb55-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="cfb55-143">示例</span><span class="sxs-lookup"><span data-stu-id="cfb55-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="cfb55-144">在默认位置中安装 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 全局工具。</span><span class="sxs-lookup"><span data-stu-id="cfb55-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="cfb55-145">在特定 Windows 目录中安装 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 全局工具。</span><span class="sxs-lookup"><span data-stu-id="cfb55-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="cfb55-146">在特定 Linux/macOS 目录中安装 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 全局工具。</span><span class="sxs-lookup"><span data-stu-id="cfb55-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="cfb55-147">安装 2.0.0 版的 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 全局工具。</span><span class="sxs-lookup"><span data-stu-id="cfb55-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="cfb55-148">在当前目录中安装 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 本地工具。</span><span class="sxs-lookup"><span data-stu-id="cfb55-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfb55-149">请参阅</span><span class="sxs-lookup"><span data-stu-id="cfb55-149">See also</span></span>

- [<span data-ttu-id="cfb55-150">.NET Core 工具</span><span class="sxs-lookup"><span data-stu-id="cfb55-150">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="cfb55-151">教程：使用 .NET Core CLI 安装和使用 .NET Core 全局工具</span><span class="sxs-lookup"><span data-stu-id="cfb55-151">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="cfb55-152">教程：使用 .NET Core CLI 安装和使用 .NET Core 本地工具</span><span class="sxs-lookup"><span data-stu-id="cfb55-152">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
