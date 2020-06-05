---
title: dotnet migrate 命令
description: dotnet migrate 命令可迁移项目及其所有依赖项。
ms.date: 02/14/2020
ms.openlocfilehash: 2e7f9ae5a1d11c54280d914b04df761f0d5aff99
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284087"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="63907-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="63907-103">dotnet migrate</span></span>

<span data-ttu-id="63907-104">本文适用于：✔️ .NET Core 2.x SDK</span><span class="sxs-lookup"><span data-stu-id="63907-104">**This article applies to:** ✔️ .NET Core 2.x SDK</span></span>

## <a name="name"></a><span data-ttu-id="63907-105">“属性”</span><span class="sxs-lookup"><span data-stu-id="63907-105">Name</span></span>

<span data-ttu-id="63907-106">`dotnet migrate` - 将预览版 2 .NET Core 项目迁移到 .NET Core SDK 样式的项目中。</span><span class="sxs-lookup"><span data-stu-id="63907-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="63907-107">摘要</span><span class="sxs-lookup"><span data-stu-id="63907-107">Synopsis</span></span>

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json <REPORT_FILE>]
    [-r|--report-file <REPORT_FILE>] [-s|--skip-project-references [Debug|Release]]
    [--skip-backup] [-t|--template-file <TEMPLATE_FILE>] [-v|--sdk-package-version]
    [-x|--xproj-file]

dotnet migrate -h|--help
```

## <a name="description"></a><span data-ttu-id="63907-108">描述</span><span class="sxs-lookup"><span data-stu-id="63907-108">Description</span></span>

<span data-ttu-id="63907-109">此命令已弃用。</span><span class="sxs-lookup"><span data-stu-id="63907-109">This command is deprecated.</span></span> <span data-ttu-id="63907-110">自 .NET Core 3.0 SDK 起，`dotnet migrate` 命令不再可用。</span><span class="sxs-lookup"><span data-stu-id="63907-110">The `dotnet migrate` command is no longer available starting with .NET Core 3.0 SDK.</span></span> <span data-ttu-id="63907-111">它只能将预览版 2 .NET Core 项目迁移到不支持的 1.x .NET Core 项目。</span><span class="sxs-lookup"><span data-stu-id="63907-111">It can only migrate a Preview 2 .NET Core project to a 1.x .NET Core project, which is out of support.</span></span>

<span data-ttu-id="63907-112">默认情况下，命令迁移根项目和根项目包含的任何项目引用。</span><span class="sxs-lookup"><span data-stu-id="63907-112">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="63907-113">在运行时使用 `--skip-project-references` 选项禁用此行为。</span><span class="sxs-lookup"><span data-stu-id="63907-113">This behavior is disabled using the `--skip-project-references` option at run time.</span></span>

<span data-ttu-id="63907-114">可在下列资产上执行迁移：</span><span class="sxs-lookup"><span data-stu-id="63907-114">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="63907-115">通过指定 *project.json* 文件进行迁移的单个项目。</span><span class="sxs-lookup"><span data-stu-id="63907-115">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="63907-116">通过将路径传递到 *global.json* 文件在 *global.json* 文件中指定的所有目录。</span><span class="sxs-lookup"><span data-stu-id="63907-116">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="63907-117">一个 *solution.sln* 文件，它迁移在解决方案中引用的项目。</span><span class="sxs-lookup"><span data-stu-id="63907-117">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="63907-118">以递归方式迁移给定目录的所有子目录。</span><span class="sxs-lookup"><span data-stu-id="63907-118">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="63907-119">`dotnet migrate` 命令将迁移的 *project.json* 文件保存在 `backup` 目录中，如果该目录不存在，将创建一个。</span><span class="sxs-lookup"><span data-stu-id="63907-119">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="63907-120">使用 `--skip-backup` 选项重写此行为。</span><span class="sxs-lookup"><span data-stu-id="63907-120">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="63907-121">默认情况下，迁移操作会将迁移过程的状态输出到标准输出 (STDOUT)。</span><span class="sxs-lookup"><span data-stu-id="63907-121">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="63907-122">如果使用 `--report-file <REPORT_FILE>` 选项，输出将保存到指定的文件中。</span><span class="sxs-lookup"><span data-stu-id="63907-122">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="63907-123">`dotnet migrate` 命令仅支持有效的预览版 2 基于 *project.json* 的项目。</span><span class="sxs-lookup"><span data-stu-id="63907-123">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="63907-124">这意味着，不能使用它将 DNX 或预览版 1 基于 *project.json* 的项目直接迁移到 MSBuild/csproj 项目。</span><span class="sxs-lookup"><span data-stu-id="63907-124">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="63907-125">首先需要将项目手动迁移到预览版 2 基于 *project.json* 的项目，然后使用 `dotnet migrate` 命令迁移该项目。</span><span class="sxs-lookup"><span data-stu-id="63907-125">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="63907-126">自变量</span><span class="sxs-lookup"><span data-stu-id="63907-126">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="63907-127">下列路径之一：</span><span class="sxs-lookup"><span data-stu-id="63907-127">The path to one of the following:</span></span>

* <span data-ttu-id="63907-128">要迁移的 *project.json* 文件。</span><span class="sxs-lookup"><span data-stu-id="63907-128">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="63907-129">global.json 文件：迁移在 global.json 中指定的文件夹 。</span><span class="sxs-lookup"><span data-stu-id="63907-129">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="63907-130">solution.sln 文件：迁移该解决方案中引用的项目。</span><span class="sxs-lookup"><span data-stu-id="63907-130">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="63907-131">要迁移的目录：在指定的目录中以递归方式搜索要迁移的 project.json 文件。</span><span class="sxs-lookup"><span data-stu-id="63907-131">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="63907-132">如未指定，则默认为当前目录。</span><span class="sxs-lookup"><span data-stu-id="63907-132">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="63907-133">选项</span><span class="sxs-lookup"><span data-stu-id="63907-133">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="63907-134">将迁移报告文件（而非用户消息）作为 JSON 输出。</span><span class="sxs-lookup"><span data-stu-id="63907-134">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="63907-135">打印出有关命令的简短帮助。</span><span class="sxs-lookup"><span data-stu-id="63907-135">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="63907-136">除控制台外，还将迁移报告输出到文件。</span><span class="sxs-lookup"><span data-stu-id="63907-136">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="63907-137">跳过迁移项目引用。</span><span class="sxs-lookup"><span data-stu-id="63907-137">Skip migrating project references.</span></span> <span data-ttu-id="63907-138">默认情况下，以递归方式迁移项目引用。</span><span class="sxs-lookup"><span data-stu-id="63907-138">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="63907-139">在成功迁移后，跳过将 *project.json*、*global.json* 和 *\*.xproj* 移动到 `backup` 目录的步骤。</span><span class="sxs-lookup"><span data-stu-id="63907-139">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="63907-140">用于迁移的模板 csproj 文件。</span><span class="sxs-lookup"><span data-stu-id="63907-140">Template csproj file to use for migration.</span></span> <span data-ttu-id="63907-141">默认情况下，使用与被 `dotnet new console` 删除的模板相同的模板。</span><span class="sxs-lookup"><span data-stu-id="63907-141">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="63907-142">在已迁移应用中将被引用的 sdk 包的版本。</span><span class="sxs-lookup"><span data-stu-id="63907-142">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="63907-143">默认为 `dotnet new` 中 SDK 的版本。</span><span class="sxs-lookup"><span data-stu-id="63907-143">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="63907-144">要使用的 xproj 文件的路径。</span><span class="sxs-lookup"><span data-stu-id="63907-144">The path to the xproj file to use.</span></span> <span data-ttu-id="63907-145">当项目目录中有多个 xproj 时需要。</span><span class="sxs-lookup"><span data-stu-id="63907-145">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="63907-146">示例</span><span class="sxs-lookup"><span data-stu-id="63907-146">Examples</span></span>

<span data-ttu-id="63907-147">将当前目录中的项目及其所有项目迁移到项目依赖项：</span><span class="sxs-lookup"><span data-stu-id="63907-147">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="63907-148">迁移 *global.json* 文件所包含的所有项目：</span><span class="sxs-lookup"><span data-stu-id="63907-148">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="63907-149">仅迁移当前项目，不迁移项目到项目 (P2P) 的依赖项。</span><span class="sxs-lookup"><span data-stu-id="63907-149">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="63907-150">此外，使用特定的 SDK 版本：</span><span class="sxs-lookup"><span data-stu-id="63907-150">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
