---
title: 从 DNX 迁移到 .NET Core CLI
description: 从使用 DNX 工具迁移到 .NET Core CLI 工具。
ms.date: 06/20/2016
ms.openlocfilehash: e5ebbab2551cf750a5b1136e7b1d4b67816c3b03
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071113"
---
# <a name="migrating-from-dnx-to-net-core-cli-projectjson"></a><span data-ttu-id="be3bd-103">从 DNX 迁移到 .NET Core CLI (project.json)</span><span class="sxs-lookup"><span data-stu-id="be3bd-103">Migrating from DNX to .NET Core CLI (project.json)</span></span>

## <a name="overview"></a><span data-ttu-id="be3bd-104">概述</span><span class="sxs-lookup"><span data-stu-id="be3bd-104">Overview</span></span>

<span data-ttu-id="be3bd-105">.NET Core 和 ASP.NET Core 1.0 RC1 版本中推出了 DNX 工具。</span><span class="sxs-lookup"><span data-stu-id="be3bd-105">The RC1 release of .NET Core and ASP.NET Core 1.0 introduced DNX tooling.</span></span> <span data-ttu-id="be3bd-106">.NET Core 和 ASP.NET Core 1.0 RC2 版本从 DNX 移动到了 .NET Core CLI。</span><span class="sxs-lookup"><span data-stu-id="be3bd-106">The RC2 release of .NET Core and ASP.NET Core 1.0 moved from DNX to the .NET Core CLI.</span></span>

<span data-ttu-id="be3bd-107">温故知新，我们简单复习下 DNX 是什么。</span><span class="sxs-lookup"><span data-stu-id="be3bd-107">As a slight refresher, let's recap what DNX was about.</span></span> <span data-ttu-id="be3bd-108">DNX 是用于生成 .NET Core（更具体点，是用于生成 ASP.NET Core 1.0 应用程序）的运行时和工具集。</span><span class="sxs-lookup"><span data-stu-id="be3bd-108">DNX was a runtime and a toolset used to build .NET Core and, more specifically, ASP.NET Core 1.0 applications.</span></span> <span data-ttu-id="be3bd-109">它主要由 3 个部分组成：</span><span class="sxs-lookup"><span data-stu-id="be3bd-109">It consisted of 3 main pieces:</span></span>

1. <span data-ttu-id="be3bd-110">DNVM -- 用于获取 DNX 的安装脚本</span><span class="sxs-lookup"><span data-stu-id="be3bd-110">DNVM - an install script for obtaining DNX</span></span>
2. <span data-ttu-id="be3bd-111">DNX（Dotnet 执行运行时） - 执行代码的运行时</span><span class="sxs-lookup"><span data-stu-id="be3bd-111">DNX (Dotnet Execution Runtime) - the runtime that executes your code</span></span>
3. <span data-ttu-id="be3bd-112">DNU（Dotnet 开发人员实用程序） - 用于管理依赖项、生成和发布应用程序的工具</span><span class="sxs-lookup"><span data-stu-id="be3bd-112">DNU (Dotnet Developer Utility) - tooling for managing dependencies, building and publishing your applications</span></span>

<span data-ttu-id="be3bd-113">引入 CLI 后，上述所有内容现在全部都属于单个工具集。</span><span class="sxs-lookup"><span data-stu-id="be3bd-113">With the introduction of the CLI, all of the above are now part of a single toolset.</span></span> <span data-ttu-id="be3bd-114">但是，由于 DNX 在 RC1 时间范围内还可用，你可能具有某些使用该 DNX 生成的项目并且想要将其移动到新的 CLI 工具。</span><span class="sxs-lookup"><span data-stu-id="be3bd-114">However, since DNX was available in RC1 timeframe, you might have projects that were built using it that you would want to move off to the new CLI tooling.</span></span>

<span data-ttu-id="be3bd-115">本迁移指南就介绍了关于如何将项目从 DNX 迁移到 .NET Core CLI 的基础知识。</span><span class="sxs-lookup"><span data-stu-id="be3bd-115">This migration guide will cover the essentials on how to migrate projects off of DNX and onto .NET Core CLI.</span></span> <span data-ttu-id="be3bd-116">如果你才刚刚开始在 .NET Core 上从头创建项目，可选择跳过此文档。</span><span class="sxs-lookup"><span data-stu-id="be3bd-116">If you are just starting a project on .NET Core from scratch, you can freely skip this document.</span></span>

## <a name="main-changes-in-the-tooling"></a><span data-ttu-id="be3bd-117">工具的主要更改</span><span class="sxs-lookup"><span data-stu-id="be3bd-117">Main changes in the tooling</span></span>

<span data-ttu-id="be3bd-118">首先将概述工具中存在的一般性更改。</span><span class="sxs-lookup"><span data-stu-id="be3bd-118">There are some general changes in the tooling that should be outlined first.</span></span>

### <a name="no-more-dnvm"></a><span data-ttu-id="be3bd-119">不再具有 DNVM</span><span class="sxs-lookup"><span data-stu-id="be3bd-119">No more DNVM</span></span>

<span data-ttu-id="be3bd-120">DNVM（DotNet 版本管理器  的简称），是用于在计算机上安装 DNX 的 bash/PowerShell 脚本。</span><span class="sxs-lookup"><span data-stu-id="be3bd-120">DNVM, short for *DotNet Version Manager* was a bash/PowerShell script used to install a DNX on your machine.</span></span> <span data-ttu-id="be3bd-121">它有助于用户从指定的数据源（或默认数据源）获得需要的 DNX，以及将某个 DNX 标记为“活动”，从而将其置于给定会话的 $PATH 中。</span><span class="sxs-lookup"><span data-stu-id="be3bd-121">It helped users get the DNX they need from the feed they specified (or default ones) as well as mark a certain DNX "active", which would put it on the $PATH for the given session.</span></span> <span data-ttu-id="be3bd-122">这使你能够使用各种工具。</span><span class="sxs-lookup"><span data-stu-id="be3bd-122">This would allow you to use the various tools.</span></span>

<span data-ttu-id="be3bd-123">DNVM 现已停用，因为其功能集可能由于 .NET Core CLI 即将推出的更改变得冗余。</span><span class="sxs-lookup"><span data-stu-id="be3bd-123">DNVM was discontinued because its feature set was made redundant by changes coming in the .NET Core CLI.</span></span>

<span data-ttu-id="be3bd-124">可以通过以下两种主要方式打包 CLI：</span><span class="sxs-lookup"><span data-stu-id="be3bd-124">The CLI comes packaged in two main ways:</span></span>

1. <span data-ttu-id="be3bd-125">给定平台的本机安装程序</span><span class="sxs-lookup"><span data-stu-id="be3bd-125">Native installers for a given platform</span></span>
2. <span data-ttu-id="be3bd-126">用于其他情形（如 CI 服务器）的安装脚本</span><span class="sxs-lookup"><span data-stu-id="be3bd-126">Install script for other situations (like CI servers)</span></span>

<span data-ttu-id="be3bd-127">因此，不再需要 DNVM 安装功能。</span><span class="sxs-lookup"><span data-stu-id="be3bd-127">Given this, the DNVM install features are not needed.</span></span> <span data-ttu-id="be3bd-128">但运行时选择功能又如何呢？</span><span class="sxs-lookup"><span data-stu-id="be3bd-128">But what about the runtime selection features?</span></span>

<span data-ttu-id="be3bd-129">将某个版本的包添加到依赖项，可以引用 `project.json` 中的运行时。</span><span class="sxs-lookup"><span data-stu-id="be3bd-129">You reference a runtime in your `project.json` by adding a package of a certain version to your dependencies.</span></span> <span data-ttu-id="be3bd-130">正因有此更改，应用程序将能够使用新的运行时数据。</span><span class="sxs-lookup"><span data-stu-id="be3bd-130">With this change, your application will be able to use the new runtime bits.</span></span> <span data-ttu-id="be3bd-131">将这些数据引入计算机与安装 CLI 方法一样：通过其支持的本机安装程序之一或通过其安装脚本安装运行时。</span><span class="sxs-lookup"><span data-stu-id="be3bd-131">Getting these bits to your machine is the same as with the CLI: you install the runtime via one of the native installers it supports or via its install script.</span></span>

### <a name="different-commands"></a><span data-ttu-id="be3bd-132">命令不同</span><span class="sxs-lookup"><span data-stu-id="be3bd-132">Different commands</span></span>

<span data-ttu-id="be3bd-133">如果使用的是 DNX，则使用某些来自其三个部件（DNX、DNU 或 DNVM）之一的命令。</span><span class="sxs-lookup"><span data-stu-id="be3bd-133">If you were using DNX, you used some commands from one of its three parts (DNX, DNU or DNVM).</span></span> <span data-ttu-id="be3bd-134">借助 CLI，其中的某些命令发生了改变，有些命令不再适用，有些保持不变，但语义稍有不同。</span><span class="sxs-lookup"><span data-stu-id="be3bd-134">With the CLI, some of these commands change, some are not available and some are the same but have slightly different semantics.</span></span>

<span data-ttu-id="be3bd-135">下表显示了 DNX/DNU 命令及其 CLI 对应项之间的映射。</span><span class="sxs-lookup"><span data-stu-id="be3bd-135">The table below shows the mapping between the DNX/DNU commands and their CLI counterparts.</span></span>

| <span data-ttu-id="be3bd-136">DNX 命令</span><span class="sxs-lookup"><span data-stu-id="be3bd-136">DNX command</span></span>                    | <span data-ttu-id="be3bd-137">CLI 命令</span><span class="sxs-lookup"><span data-stu-id="be3bd-137">CLI command</span></span>    | <span data-ttu-id="be3bd-138">说明</span><span class="sxs-lookup"><span data-stu-id="be3bd-138">Description</span></span>                                                                                                     |
|--------------------------------|----------------|-----------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="be3bd-139">dnx 运行</span><span class="sxs-lookup"><span data-stu-id="be3bd-139">dnx run</span></span>                        | `dotnet run`     | <span data-ttu-id="be3bd-140">从源运行代码。</span><span class="sxs-lookup"><span data-stu-id="be3bd-140">Run code from source.</span></span>                                                                                           |
| <span data-ttu-id="be3bd-141">dnu 生成</span><span class="sxs-lookup"><span data-stu-id="be3bd-141">dnu build</span></span>                      | `dotnet build`   | <span data-ttu-id="be3bd-142">生成代码的 IL 二进制。</span><span class="sxs-lookup"><span data-stu-id="be3bd-142">Build an IL binary of your code.</span></span>                                                                                |
| <span data-ttu-id="be3bd-143">dnu 包</span><span class="sxs-lookup"><span data-stu-id="be3bd-143">dnu pack</span></span>                       | `dotnet pack`    | <span data-ttu-id="be3bd-144">打包代码的 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="be3bd-144">Package up a NuGet package of your code.</span></span>                                                                        |
| <span data-ttu-id="be3bd-145">dnx \[command]（例如，“dnx web”）</span><span class="sxs-lookup"><span data-stu-id="be3bd-145">dnx \[command] (for example, "dnx web")</span></span> | <span data-ttu-id="be3bd-146">不适用\*</span><span class="sxs-lookup"><span data-stu-id="be3bd-146">N/A\*</span></span>          | <span data-ttu-id="be3bd-147">在 DNX 领域中，按照 project.json 中的定义运行命令。</span><span class="sxs-lookup"><span data-stu-id="be3bd-147">In DNX world, run a command as defined in the project.json.</span></span>                                                     |
| <span data-ttu-id="be3bd-148">dnu 安装</span><span class="sxs-lookup"><span data-stu-id="be3bd-148">dnu install</span></span>                    | <span data-ttu-id="be3bd-149">不适用\*</span><span class="sxs-lookup"><span data-stu-id="be3bd-149">N/A\*</span></span>          | <span data-ttu-id="be3bd-150">在 DNX 领域中，将包安装为一个依赖项。</span><span class="sxs-lookup"><span data-stu-id="be3bd-150">In the DNX world, install a package as a dependency.</span></span>                                                            |
| <span data-ttu-id="be3bd-151">dnu 还原</span><span class="sxs-lookup"><span data-stu-id="be3bd-151">dnu restore</span></span>                    | `dotnet restore` | <span data-ttu-id="be3bd-152">还原 project.json 中指定的依赖项。</span><span class="sxs-lookup"><span data-stu-id="be3bd-152">Restore dependencies specified in your project.json.</span></span> <span data-ttu-id="be3bd-153">（[请参阅注释](#dotnet-restore-note)）</span><span class="sxs-lookup"><span data-stu-id="be3bd-153">([see note](#dotnet-restore-note))</span></span>                                                            |
| <span data-ttu-id="be3bd-154">dnu 发布</span><span class="sxs-lookup"><span data-stu-id="be3bd-154">dnu publish</span></span>                    | `dotnet publish` | <span data-ttu-id="be3bd-155">使用三种形式（可移植、本机可移植和独立形式）之一发布应用程序以进行部署。</span><span class="sxs-lookup"><span data-stu-id="be3bd-155">Publish your application for deployment in one of the three forms (portable, portable with native and standalone).</span></span> |
| <span data-ttu-id="be3bd-156">dnu 包装</span><span class="sxs-lookup"><span data-stu-id="be3bd-156">dnu wrap</span></span>                       | <span data-ttu-id="be3bd-157">不适用\*</span><span class="sxs-lookup"><span data-stu-id="be3bd-157">N/A\*</span></span>          | <span data-ttu-id="be3bd-158">在 DNX 领域中，包装 csproj 中的 project.json。</span><span class="sxs-lookup"><span data-stu-id="be3bd-158">In DNX world, wrap a project.json in csproj.</span></span>                                                                    |
| <span data-ttu-id="be3bd-159">dnu 命令</span><span class="sxs-lookup"><span data-stu-id="be3bd-159">dnu commands</span></span>                   | <span data-ttu-id="be3bd-160">不适用\*</span><span class="sxs-lookup"><span data-stu-id="be3bd-160">N/A\*</span></span>          | <span data-ttu-id="be3bd-161">在 DNX 领域中，管理全局安装的命令。</span><span class="sxs-lookup"><span data-stu-id="be3bd-161">In DNX world, manage the globally installed commands.</span></span>                                                           |

<span data-ttu-id="be3bd-162">(\*) - 按照设计，CLI 中不支持这些功能。</span><span class="sxs-lookup"><span data-stu-id="be3bd-162">(\*) - these features are not supported in the CLI by design.</span></span>

## <a name="dnx-features-that-are-not-supported"></a><span data-ttu-id="be3bd-163">不支持 DNX 功能</span><span class="sxs-lookup"><span data-stu-id="be3bd-163">DNX features that are not supported</span></span>

<span data-ttu-id="be3bd-164">如上表所示，CLI 中不支持（至少暂时不支持）来自 DNX 领域的某些功能。</span><span class="sxs-lookup"><span data-stu-id="be3bd-164">As the table above shows, there are features from the DNX world that we decided not to support in the CLI, at least for the time being.</span></span> <span data-ttu-id="be3bd-165">本部分将介绍最重要的这部分内容，并概述不支持它们的根本原因，以及如果确实需要某些功能时相应的解决办法。</span><span class="sxs-lookup"><span data-stu-id="be3bd-165">This section will go through the most important ones and outline the rationale behind not supporting them as well as workarounds if you do need them.</span></span>

### <a name="global-commands"></a><span data-ttu-id="be3bd-166">全局命令</span><span class="sxs-lookup"><span data-stu-id="be3bd-166">Global commands</span></span>

<span data-ttu-id="be3bd-167">DNU 附带称为“全局命令”的概念。</span><span class="sxs-lookup"><span data-stu-id="be3bd-167">DNU came with a concept called "global commands".</span></span> <span data-ttu-id="be3bd-168">从本质上来说，这些都是打包成 NuGet 包的控制台应用程序，其中 shell 脚本可以调用指定用于运行应用程序的 DNX。</span><span class="sxs-lookup"><span data-stu-id="be3bd-168">These were, essentially, console applications packaged up as NuGet packages with a shell script that would invoke the DNX you specified to run the application.</span></span>

<span data-ttu-id="be3bd-169">CLI 不支持此概念。</span><span class="sxs-lookup"><span data-stu-id="be3bd-169">The CLI does not support this concept.</span></span> <span data-ttu-id="be3bd-170">但是，它确实支持添加所有项目命令的这一概念，这些命令可以使用熟悉的 `dotnet <command>` 语法调用。</span><span class="sxs-lookup"><span data-stu-id="be3bd-170">It does, however, support the concept of adding per-project commands that can be invoked using the familiar `dotnet <command>` syntax.</span></span>

### <a name="installing-dependencies"></a><span data-ttu-id="be3bd-171">安装依赖项</span><span class="sxs-lookup"><span data-stu-id="be3bd-171">Installing dependencies</span></span>

<span data-ttu-id="be3bd-172">自 v1 起，.NET Core CLI 就没有用于安装依赖项的 `install` 命令。</span><span class="sxs-lookup"><span data-stu-id="be3bd-172">As of v1, the .NET Core CLI doesn't have an `install` command for installing dependencies.</span></span> <span data-ttu-id="be3bd-173">为了从 NuGet 安装包，需要将其作为依赖项添加到 `project.json` 文件，然后运行 `dotnet restore`（[请参阅注释](#dotnet-restore-note)）。</span><span class="sxs-lookup"><span data-stu-id="be3bd-173">In order to install a package from NuGet, you would need to add it as a dependency to your `project.json` file and then run `dotnet restore` ([see note](#dotnet-restore-note)).</span></span>

### <a name="running-your-code"></a><span data-ttu-id="be3bd-174">运行代码</span><span class="sxs-lookup"><span data-stu-id="be3bd-174">Running your code</span></span>

<span data-ttu-id="be3bd-175">运行代码主要有两种方法。</span><span class="sxs-lookup"><span data-stu-id="be3bd-175">There are two main ways to run your code.</span></span> <span data-ttu-id="be3bd-176">一种是从源中使用 `dotnet run` 运行。</span><span class="sxs-lookup"><span data-stu-id="be3bd-176">One is from source, with `dotnet run`.</span></span> <span data-ttu-id="be3bd-177">与 `dnx run` 不同，这种方法不能执行任何内存中编译。</span><span class="sxs-lookup"><span data-stu-id="be3bd-177">Unlike `dnx run`, this will not do any in-memory compilation.</span></span> <span data-ttu-id="be3bd-178">实际上，它将调用 `dotnet build` 生成代码，然后运行生成的二进制文件。</span><span class="sxs-lookup"><span data-stu-id="be3bd-178">It will actually invoke `dotnet build` to build your code and then run the built binary.</span></span>

<span data-ttu-id="be3bd-179">另一种是使用 `dotnet` 自身运行代码。</span><span class="sxs-lookup"><span data-stu-id="be3bd-179">Another way is using the `dotnet` itself to run your code.</span></span> <span data-ttu-id="be3bd-180">可通过提供程序集路径实现：`dotnet path/to/an/assembly.dll`。</span><span class="sxs-lookup"><span data-stu-id="be3bd-180">This is done by providing a path to your assembly: `dotnet path/to/an/assembly.dll`.</span></span>

## <a name="migrating-your-dnx-project-to-net-core-cli"></a><span data-ttu-id="be3bd-181">将 DNX 项目迁移到 .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="be3bd-181">Migrating your DNX project to .NET Core CLI</span></span>

<span data-ttu-id="be3bd-182">使用代码时，除了使用新的命令，从 DNX 迁移还剩三件主要的事情：</span><span class="sxs-lookup"><span data-stu-id="be3bd-182">In addition to using new commands when working with your code, there are three major things left in migrating from DNX:</span></span>

1. <span data-ttu-id="be3bd-183">若要使其能够使用 CLI，请迁移 `global.json` 文件。</span><span class="sxs-lookup"><span data-stu-id="be3bd-183">Migrate the `global.json` file if you have it to be able to use CLI.</span></span>
2. <span data-ttu-id="be3bd-184">将项目文件 (`project.json`) 本身迁移到 CLI 工具。</span><span class="sxs-lookup"><span data-stu-id="be3bd-184">Migrating the project file (`project.json`) itself to the CLI tooling.</span></span>
3. <span data-ttu-id="be3bd-185">将任何 DNX API 迁移到 BCL 对应项。</span><span class="sxs-lookup"><span data-stu-id="be3bd-185">Migrating off of any DNX APIs to their BCL counterparts.</span></span>

### <a name="changing-the-globaljson-file"></a><span data-ttu-id="be3bd-186">更改 global.json 文件</span><span class="sxs-lookup"><span data-stu-id="be3bd-186">Changing the global.json file</span></span>

<span data-ttu-id="be3bd-187">对于 RC1 和 RC2（或更高版本）项目，`global.json` 文件充当两者的解决方案文件。</span><span class="sxs-lookup"><span data-stu-id="be3bd-187">The `global.json` file acts like a solution file for both the RC1 and RC2 (or later) projects.</span></span> <span data-ttu-id="be3bd-188">为了在 RC1 和更高版本间区分 .NET Core CLI（以及 Visual Studio），可以使用 `"sdk": { "version" }` 属性来区分哪个项目是 RC1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="be3bd-188">In order for the .NET Core CLI (as well as Visual Studio) to differentiate between RC1 and later versions, they use the `"sdk": { "version" }` property to make the distinction which project is RC1 or later.</span></span> <span data-ttu-id="be3bd-189">如果 `global.json` 根本无此节点，则假定为最新版本。</span><span class="sxs-lookup"><span data-stu-id="be3bd-189">If `global.json` doesn't have this node at all, it is assumed to be the latest.</span></span>

<span data-ttu-id="be3bd-190">为了更新 `global.json` 文件，可以删除此属性或将其设置为想要使用的工具的确切版本，在本示例中为 **1.0.0-preview2-003121**：</span><span class="sxs-lookup"><span data-stu-id="be3bd-190">In order to update the `global.json` file, either remove the property or set it to the exact version of the tools that you wish to use, in this case **1.0.0-preview2-003121**:</span></span>

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```

### <a name="migrating-the-project-file"></a><span data-ttu-id="be3bd-191">迁移项目文件</span><span class="sxs-lookup"><span data-stu-id="be3bd-191">Migrating the project file</span></span>

<span data-ttu-id="be3bd-192">CLI 和 DNX 都使用基于 `project.json` 文件的相同基本项目系统。</span><span class="sxs-lookup"><span data-stu-id="be3bd-192">The CLI and DNX both use the same basic project system based on `project.json` file.</span></span> <span data-ttu-id="be3bd-193">项目文件的语法和语义大致相同，但根据应用场景，会略有不同。</span><span class="sxs-lookup"><span data-stu-id="be3bd-193">The syntax and the semantics of the project file are pretty much the same, with small differences based on the scenarios.</span></span> <span data-ttu-id="be3bd-194">此外还对架构进行了一些更改，可在[架构文件](http://json.schemastore.org/project)中查看这些更改。</span><span class="sxs-lookup"><span data-stu-id="be3bd-194">There are also some changes to the schema which you can see in the [schema file](http://json.schemastore.org/project).</span></span>

<span data-ttu-id="be3bd-195">如果要生成控制台应用程序，需要将以下代码段添加到项目文件：</span><span class="sxs-lookup"><span data-stu-id="be3bd-195">If you are building a console application, you need to add the following snippet to your project file:</span></span>

```json
"buildOptions": {
    "emitEntryPoint": true
}
```

<span data-ttu-id="be3bd-196">这会指示 `dotnet build` 发出应用程序入口点，可以有效地使代码具有可运行性。</span><span class="sxs-lookup"><span data-stu-id="be3bd-196">This instructs `dotnet build` to emit an entry point for your application, effectively making your code runnable.</span></span> <span data-ttu-id="be3bd-197">如果要生成类库，则可以直接省略以上内容。</span><span class="sxs-lookup"><span data-stu-id="be3bd-197">If you are building a class library, simply omit the above section.</span></span> <span data-ttu-id="be3bd-198">当然，将上述代码段添加到 `project.json` 文件后，需要添加静态入口点。</span><span class="sxs-lookup"><span data-stu-id="be3bd-198">Of course, once you add the above snippet to your `project.json` file, you need to add a static entry point.</span></span> <span data-ttu-id="be3bd-199">从 DNX 迁移后，它提供的 DI 服务将不再可用，因此需要属于基本 .NET 入口点：`static void Main()`。</span><span class="sxs-lookup"><span data-stu-id="be3bd-199">With the move off DNX, the DI services it provided are no longer available and thus this needs to be a basic .NET entry point: `static void Main()`.</span></span>

<span data-ttu-id="be3bd-200">如果 `project.json` 中有“命令”部分，可将其删除。</span><span class="sxs-lookup"><span data-stu-id="be3bd-200">If you have a "commands" section in your `project.json`, you can remove it.</span></span> <span data-ttu-id="be3bd-201">过去作为 DNU 命令（例如，实体框架 CLI 命令）存在的某些命令，将作为每个项目的扩展移植到 CLI。</span><span class="sxs-lookup"><span data-stu-id="be3bd-201">Some of the commands that used to exist as DNU commands, such as Entity Framework CLI commands, are being ported to be per-project extensions to the CLI.</span></span> <span data-ttu-id="be3bd-202">如果生成了自己正在项目中使用的命令，需要使用 CLI 扩展将其替换。</span><span class="sxs-lookup"><span data-stu-id="be3bd-202">If you built your own commands that you are using in your projects, you need to replace them with CLI extensions.</span></span> <span data-ttu-id="be3bd-203">在这种情况下，`project.json` 中的 `commands` 节点需要替换为 `tools` 节点，并且需要列出工具依赖项。</span><span class="sxs-lookup"><span data-stu-id="be3bd-203">In this case, the `commands` node in `project.json` needs to be replaced by the `tools` node and it needs to list the tools dependencies.</span></span>

<span data-ttu-id="be3bd-204">完成这些操作后，需要决定希望应用使用的可移植性类型。</span><span class="sxs-lookup"><span data-stu-id="be3bd-204">After these things are done, you need to decide which type of portability you wish for you app.</span></span> <span data-ttu-id="be3bd-205">借助 .NET Core，我们在提供一系列可从中进行选择的可移植性选项方面投入了大量工作。</span><span class="sxs-lookup"><span data-stu-id="be3bd-205">With .NET Core, we have invested into providing a spectrum of portability options that you can choose from.</span></span> <span data-ttu-id="be3bd-206">例如，可能想要一个完全可移植  的应用程序或者想要一个独立的  应用程序。</span><span class="sxs-lookup"><span data-stu-id="be3bd-206">For instance, you may want to have a fully *portable* application or you may want to have a *self-contained* application.</span></span> <span data-ttu-id="be3bd-207">可移植应用程序选项工作原理更像 .NET Framework 应用程序的工作原理：它需要共享组件才能在目标计算机 (.NET Core) 上执行。</span><span class="sxs-lookup"><span data-stu-id="be3bd-207">The portable application option is more like .NET Framework applications work: it needs a shared component to execute it on the target machine (.NET Core).</span></span> <span data-ttu-id="be3bd-208">独立应用程序不需要在目标上安装 .NET Core，但需要为每个要支持的 OS 生成一个应用程序。</span><span class="sxs-lookup"><span data-stu-id="be3bd-208">The self-contained application doesn't require .NET Core to be installed on the target, but you have to produce one application for each OS you wish to support.</span></span> <span data-ttu-id="be3bd-209">有关这些可移植性类型等内容，请参阅[应用程序可移植性类型](../deploying/index.md)文档。</span><span class="sxs-lookup"><span data-stu-id="be3bd-209">These portability types and more are discussed in the [application portability type](../deploying/index.md) document.</span></span>

<span data-ttu-id="be3bd-210">调用想要的可移植性类型后，需要更改目标框架。</span><span class="sxs-lookup"><span data-stu-id="be3bd-210">Once you make a call on what type of portability you want, you need to change your targeted framework(s).</span></span> <span data-ttu-id="be3bd-211">如果是为 .NET Core 编写应用程序，很可能要使用 `dnxcore50` 作为目标框架。</span><span class="sxs-lookup"><span data-stu-id="be3bd-211">If you were writing applications for .NET Core, you were most likely using `dnxcore50` as  your targeted framework.</span></span> <span data-ttu-id="be3bd-212">鉴于 CLI 和全新 [.NET Standard](../../standard/net-standard.md) 引入的变化，框架需要为下列之一：</span><span class="sxs-lookup"><span data-stu-id="be3bd-212">With the CLI and the changes that the new [.NET Standard](../../standard/net-standard.md) brought, the framework needs to be one of the following:</span></span>

1. <span data-ttu-id="be3bd-213">`netcoreapp1.0` - 如果要在 .NET Core 上编写应用程序（包括 ASP.NET Core 应用程序）</span><span class="sxs-lookup"><span data-stu-id="be3bd-213">`netcoreapp1.0` - if you are writing applications on .NET Core (including ASP.NET Core applications)</span></span>
2. <span data-ttu-id="be3bd-214">`netstandard1.6` - 如果要为 .NET Core 编写类库</span><span class="sxs-lookup"><span data-stu-id="be3bd-214">`netstandard1.6` - if you are writing class libraries for .NET Core</span></span>

<span data-ttu-id="be3bd-215">如果要使用其他 `dnx` 目标，如 `dnx451`，则还需要更改这些内容。</span><span class="sxs-lookup"><span data-stu-id="be3bd-215">If you are using other `dnx` targets, like `dnx451` you will need to change those as well.</span></span> <span data-ttu-id="be3bd-216">`dnx451` 应更改为 `net451`。</span><span class="sxs-lookup"><span data-stu-id="be3bd-216">`dnx451` should be changed to `net451`.</span></span>
<span data-ttu-id="be3bd-217">有关详细信息，请参阅 [.NET Standard](../../standard/net-standard.md) 主题。</span><span class="sxs-lookup"><span data-stu-id="be3bd-217">Please refer to the [.NET Standard](../../standard/net-standard.md) topic for more information.</span></span>

<span data-ttu-id="be3bd-218">`project.json` 现已差不多准备就绪。</span><span class="sxs-lookup"><span data-stu-id="be3bd-218">Your `project.json` is now mostly ready.</span></span> <span data-ttu-id="be3bd-219">需要浏览依赖项列表并将依赖项更新至最新版本，尤其在使用 ASP.NET Core 依赖项时。</span><span class="sxs-lookup"><span data-stu-id="be3bd-219">You need to go through your dependencies list and update the dependencies to their newer versions, especially if you are using ASP.NET Core dependencies.</span></span> <span data-ttu-id="be3bd-220">如果使用的是 BCL API 的单独包，可使用运行时包，如[应用程序可移植性类型](../deploying/index.md)文档中所述。</span><span class="sxs-lookup"><span data-stu-id="be3bd-220">If you were using separate packages for BCL APIs, you can use the runtime package as explained in the [application portability type](../deploying/index.md) document.</span></span>

<span data-ttu-id="be3bd-221">准备就绪后，就可以尝试使用 `dotnet restore`（[请参阅注释](#dotnet-restore-note)）进行还原。</span><span class="sxs-lookup"><span data-stu-id="be3bd-221">Once you are ready, you can try restoring with `dotnet restore` ([see note](#dotnet-restore-note)).</span></span> <span data-ttu-id="be3bd-222">具体取决于依赖项版本，如果 NuGet 无法解析上述目标框架的依赖项，可能会遇到错误。</span><span class="sxs-lookup"><span data-stu-id="be3bd-222">Depending on the version of your dependencies, you may encounter errors if NuGet cannot resolve the dependencies for one of the targeted frameworks above.</span></span> <span data-ttu-id="be3bd-223">这是一个“时间点”问题；随着时间的推移，支持这些框架的包会越来越多。</span><span class="sxs-lookup"><span data-stu-id="be3bd-223">This is a "point-in-time" problem; as time progresses, more and more packages will include support for these frameworks.</span></span> <span data-ttu-id="be3bd-224">目前，如果遇到此类问题，可以使用 `framework` 节点内的 `imports` 语句指定到 NuGet，还原“imports”语句内面向该框架的包。</span><span class="sxs-lookup"><span data-stu-id="be3bd-224">For now, if you run into this, you can use the `imports` statement within the `framework` node to specify to NuGet that it can restore the packages targeting the framework within the "imports" statement.</span></span>
<span data-ttu-id="be3bd-225">此种情况下遇到的还原错误可提供足够的信息，告知需要导入的框架类型。</span><span class="sxs-lookup"><span data-stu-id="be3bd-225">The restoring errors you get in this case should provide enough information to tell you which frameworks you need to import.</span></span> <span data-ttu-id="be3bd-226">一般而言，如果对此感到迷惑或不熟悉，在 `imports` 语句中指定 `dnxcore50` 和 `portable-net45+win8` 应该有效。</span><span class="sxs-lookup"><span data-stu-id="be3bd-226">If you are slightly lost or new to this, in general, specifying `dnxcore50` and `portable-net45+win8` in the `imports` statement should do the trick.</span></span> <span data-ttu-id="be3bd-227">下面的 JSON 代码段显示了这种情况是怎样的：</span><span class="sxs-lookup"><span data-stu-id="be3bd-227">The JSON snippet below shows how this looks like:</span></span>

```json
    "frameworks": {
        "netcoreapp1.0": {
            "imports": ["dnxcore50", "portable-net45+win8"]
        }
    }
```

<span data-ttu-id="be3bd-228">运行 `dotnet build` 会显示任何最终的生成错误，但应该不会有很多。</span><span class="sxs-lookup"><span data-stu-id="be3bd-228">Running `dotnet build` will show any eventual build errors, though there shouldn't be too many of them.</span></span> <span data-ttu-id="be3bd-229">生成代码并正常运行后，可以使用运行程序测试它。</span><span class="sxs-lookup"><span data-stu-id="be3bd-229">After your code is building and running properly, you can test it out with the runner.</span></span> <span data-ttu-id="be3bd-230">执行 `dotnet <path-to-your-assembly>` 并查看其运行状况。</span><span class="sxs-lookup"><span data-stu-id="be3bd-230">Execute `dotnet <path-to-your-assembly>` and see it run.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
