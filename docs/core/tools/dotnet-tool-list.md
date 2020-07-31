---
title: dotnet tool list 命令
description: dotnet 工具列表命令列出计算机上安装的 .NET Core 工具。
ms.date: 02/14/2020
ms.openlocfilehash: 4035c5be233232e53c6d7150485f737108c1e18d
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925457"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="2ce52-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="2ce52-103">dotnet tool list</span></span>

<span data-ttu-id="2ce52-104">本文适用于： ✔️ .NET Core 2.1 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="2ce52-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2ce52-105">“属性”</span><span class="sxs-lookup"><span data-stu-id="2ce52-105">Name</span></span>

<span data-ttu-id="2ce52-106">`dotnet tool list` - 列出计算机上当前安装的所有指定类型的 [.NET Core 工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="2ce52-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2ce52-107">摘要</span><span class="sxs-lookup"><span data-stu-id="2ce52-107">Synopsis</span></span>

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a><span data-ttu-id="2ce52-108">描述</span><span class="sxs-lookup"><span data-stu-id="2ce52-108">Description</span></span>

<span data-ttu-id="2ce52-109">`dotnet tool list` 命令为用户提供一种在计算机上安装所有 .NET Core 全局、工具路径或本地工具的方法。</span><span class="sxs-lookup"><span data-stu-id="2ce52-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local tools installed on your machine.</span></span> <span data-ttu-id="2ce52-110">此命令列出包名称、安装的版本以及工具命令。</span><span class="sxs-lookup"><span data-stu-id="2ce52-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="2ce52-111">若要使用命令，请指定以下项之一：</span><span class="sxs-lookup"><span data-stu-id="2ce52-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="2ce52-112">若要列出在默认位置安装的全局工具，请使用 `--global` 选项</span><span class="sxs-lookup"><span data-stu-id="2ce52-112">To list global tools installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="2ce52-113">若要列出在自定义位置安装的全局工具，请使用 `--tool-path` 选项。</span><span class="sxs-lookup"><span data-stu-id="2ce52-113">To list global tools installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="2ce52-114">若要列出本地工具，请使用 `--local` 选项或省略 `--global`、`--tool-path` 和 `--local` 选项。</span><span class="sxs-lookup"><span data-stu-id="2ce52-114">To list local tools, use the `--local` option or omit the `--global`, `--tool-path`, and `--local` options.</span></span>

<span data-ttu-id="2ce52-115">**本地工具从 .NET Core SDK 3.0 开始可用。**</span><span class="sxs-lookup"><span data-stu-id="2ce52-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="2ce52-116">选项</span><span class="sxs-lookup"><span data-stu-id="2ce52-116">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="2ce52-117">列出用户范围的全局工具。</span><span class="sxs-lookup"><span data-stu-id="2ce52-117">Lists user-wide global tools.</span></span> <span data-ttu-id="2ce52-118">不能与 `--tool-path` 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="2ce52-118">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="2ce52-119">省略 `--global` 和 `--tool-path` 将列出本地工具。</span><span class="sxs-lookup"><span data-stu-id="2ce52-119">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="2ce52-120">打印出有关命令的简短帮助。</span><span class="sxs-lookup"><span data-stu-id="2ce52-120">Prints out a short help for the command.</span></span>

- **`--local`**

  <span data-ttu-id="2ce52-121">列出当前目录的本地工具。</span><span class="sxs-lookup"><span data-stu-id="2ce52-121">Lists local tools for the current directory.</span></span> <span data-ttu-id="2ce52-122">不能与 `--global` 或 `--tool-path` 选项组合。</span><span class="sxs-lookup"><span data-stu-id="2ce52-122">Can't be combined with the `--global` or `--tool-path` options.</span></span> <span data-ttu-id="2ce52-123">即使未指定 `--local`，同时省略 `--global` 和 `--tool-path` 也会列出本地工具。</span><span class="sxs-lookup"><span data-stu-id="2ce52-123">Omitting both `--global` and `--tool-path` lists local tools even if `--local` is not specified.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="2ce52-124">指定用于查找全局工具的自定义位置。</span><span class="sxs-lookup"><span data-stu-id="2ce52-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="2ce52-125">路径可以是绝对的，也可以是相对的。</span><span class="sxs-lookup"><span data-stu-id="2ce52-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="2ce52-126">不能与 `--global` 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="2ce52-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="2ce52-127">省略 `--global` 和 `--tool-path` 将列出本地工具。</span><span class="sxs-lookup"><span data-stu-id="2ce52-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="2ce52-128">示例</span><span class="sxs-lookup"><span data-stu-id="2ce52-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="2ce52-129">列出计算机上安装的所有用户范围的全局工具（当前用户配置文件）。</span><span class="sxs-lookup"><span data-stu-id="2ce52-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="2ce52-130">列出特定 Windows 目录中的全局工具。</span><span class="sxs-lookup"><span data-stu-id="2ce52-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="2ce52-131">列出特定 Linux/macOS 目录中的全局工具。</span><span class="sxs-lookup"><span data-stu-id="2ce52-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- <span data-ttu-id="2ce52-132">**`dotnet tool list`** 或 **`dotnet tool list --local`**</span><span class="sxs-lookup"><span data-stu-id="2ce52-132">**`dotnet tool list`** or **`dotnet tool list --local`**</span></span>

  <span data-ttu-id="2ce52-133">列出当前目录中所有可用的本地工具。</span><span class="sxs-lookup"><span data-stu-id="2ce52-133">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ce52-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="2ce52-134">See also</span></span>

- [<span data-ttu-id="2ce52-135">.NET Core 工具</span><span class="sxs-lookup"><span data-stu-id="2ce52-135">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="2ce52-136">教程：使用 .NET Core CLI 安装和使用 .NET Core 全局工具</span><span class="sxs-lookup"><span data-stu-id="2ce52-136">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="2ce52-137">教程：使用 .NET Core CLI 安装和使用 .NET Core 本地工具</span><span class="sxs-lookup"><span data-stu-id="2ce52-137">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
