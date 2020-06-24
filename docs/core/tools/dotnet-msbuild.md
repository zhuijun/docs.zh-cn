---
title: dotnet msbuild 命令
description: dotnet msbuild 命令可提供对 MSBuild 命令行的访问权限。
ms.date: 02/14/2020
ms.openlocfilehash: 9739fe782e17db3955db087ca1781ad4280cd491
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803177"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="988e3-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="988e3-103">dotnet msbuild</span></span>

<span data-ttu-id="988e3-104">**本文适用于：** ✔️ .NET Core 2.x SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="988e3-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="988e3-105">“属性”</span><span class="sxs-lookup"><span data-stu-id="988e3-105">Name</span></span>

<span data-ttu-id="988e3-106">`dotnet msbuild` - 生成项目及其所有依赖项。</span><span class="sxs-lookup"><span data-stu-id="988e3-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span> <span data-ttu-id="988e3-107">注意：如果有多个解决方案或项目文件，可能需要指定一个。</span><span class="sxs-lookup"><span data-stu-id="988e3-107">Note: A solution or project file may need to be specified if there are multiple.</span></span>

## <a name="synopsis"></a><span data-ttu-id="988e3-108">摘要</span><span class="sxs-lookup"><span data-stu-id="988e3-108">Synopsis</span></span>

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a><span data-ttu-id="988e3-109">描述</span><span class="sxs-lookup"><span data-stu-id="988e3-109">Description</span></span>

<span data-ttu-id="988e3-110">`dotnet msbuild` 命令允许访问功能完备的 MSBuild。</span><span class="sxs-lookup"><span data-stu-id="988e3-110">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="988e3-111">该命令与仅适用于 SDK 样式项目的现有 MSBuild 命令行客户端具有完全相同的功能。</span><span class="sxs-lookup"><span data-stu-id="988e3-111">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="988e3-112">选项一致。</span><span class="sxs-lookup"><span data-stu-id="988e3-112">The options are all the same.</span></span> <span data-ttu-id="988e3-113">有关可用选项的详细信息，请参阅 [MSBuild 命令行参考](/visualstudio/msbuild/msbuild-command-line-reference)。</span><span class="sxs-lookup"><span data-stu-id="988e3-113">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="988e3-114">[dotnet build](dotnet-build.md) 命令相当于 `dotnet msbuild -restore`。</span><span class="sxs-lookup"><span data-stu-id="988e3-114">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore`.</span></span> <span data-ttu-id="988e3-115">如果不想生成项目，并且拥有要运行的特定目标，请使用 `dotnet build` 或 `dotnet msbuild` 并指定目标。</span><span class="sxs-lookup"><span data-stu-id="988e3-115">When you don't want to build the project and you have a specific target you want to run, use `dotnet build` or `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="988e3-116">示例</span><span class="sxs-lookup"><span data-stu-id="988e3-116">Examples</span></span>

- <span data-ttu-id="988e3-117">生成项目及其依赖项：</span><span class="sxs-lookup"><span data-stu-id="988e3-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="988e3-118">使用“发布”配置生成项目及其依赖项：</span><span class="sxs-lookup"><span data-stu-id="988e3-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="988e3-119">运行发布目标并发布 `osx.10.11-x64` RID：</span><span class="sxs-lookup"><span data-stu-id="988e3-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="988e3-120">请参阅包含 SDK 添加的所有目标的整个项目：</span><span class="sxs-lookup"><span data-stu-id="988e3-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  dotnet msbuild -preprocess:<fileName>.xml
  ```
