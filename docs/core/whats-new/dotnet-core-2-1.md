---
title: .NET Core 2.1 的新增功能
description: 了解 .NET Core 2.1 的新增功能。
dev_langs:
- csharp
- vb
ms.date: 10/10/2018
ms.openlocfilehash: 94f3db14046ad5d63975d0ca44425abed5d52062
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281532"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="7bbf7-103">.NET Core 2.1 的新增功能</span><span class="sxs-lookup"><span data-stu-id="7bbf7-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="7bbf7-104">.NET Core 2.1 提供以下几个方面的增强功能和新功能：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="7bbf7-105">工具</span><span class="sxs-lookup"><span data-stu-id="7bbf7-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="7bbf7-106">前滚</span><span class="sxs-lookup"><span data-stu-id="7bbf7-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="7bbf7-107">部署</span><span class="sxs-lookup"><span data-stu-id="7bbf7-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="7bbf7-108">Windows 兼容包</span><span class="sxs-lookup"><span data-stu-id="7bbf7-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="7bbf7-109">JIT 编译改进</span><span class="sxs-lookup"><span data-stu-id="7bbf7-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="7bbf7-110">API 更改</span><span class="sxs-lookup"><span data-stu-id="7bbf7-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="7bbf7-111">工具</span><span class="sxs-lookup"><span data-stu-id="7bbf7-111">Tooling</span></span>

<span data-ttu-id="7bbf7-112">.NET Core 2.1 SDK (v 2.1.300)，该工具与 .NET Core 2.1 一起提供，包括以下更改和增强功能：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="7bbf7-113">生成性能改进</span><span class="sxs-lookup"><span data-stu-id="7bbf7-113">Build performance improvements</span></span>

<span data-ttu-id="7bbf7-114">.NET Core 2.1 的主要关注点是改进生成时性能，特别是增量生成。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="7bbf7-115">这些性能改进适用于使用 `dotnet build` 的两个命令行生成和 Visual Studio 中的生成。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="7bbf7-116">一些个别的改进领域包括：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="7bbf7-117">对于包资产解决方法，只解决由生成使用的资产而不是所有资产。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="7bbf7-118">程序集引用缓存。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-118">Caching of assembly references.</span></span>

- <span data-ttu-id="7bbf7-119">使用长时间运行的 SDK 生成服务器，这些是跨各个 `dotnet build` 调用的过程。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="7bbf7-120">每次 `dotnet build` 运行时不再需要 JIT 编译大量代码块。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="7bbf7-121">生成服务器进程可以使用以下命令自动终止：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="7bbf7-122">新的 CLI 命令</span><span class="sxs-lookup"><span data-stu-id="7bbf7-122">New CLI commands</span></span>

<span data-ttu-id="7bbf7-123">许多使用 `DotnetCliToolReference` 的仅在每个项目的基础上可用的工具现作为 .NET Core SDK 的一部分提供。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-123">A number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="7bbf7-124">这些工具包括：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-124">These tools include:</span></span>

- <span data-ttu-id="7bbf7-125">`dotnet watch` 提供文件系统观察程序，该程序在执行指定的命令集之前会首先等待文件更改。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="7bbf7-126">例如，下面的命令将自动重新生成当前项目，并在其中的文件发生更改时生成详细输出：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   <span data-ttu-id="7bbf7-127">请注意 `--verbose` 选项前面的 `--` 选项。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="7bbf7-128">它分隔从传递给子 `dotnet` 进程的参数直接传递到 `dotnet watch` 命令的选项。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="7bbf7-129">如果没有该选项，`--verbose` 选项将适用于 `dotnet watch` 命令，而非 `dotnet build` 命令。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="7bbf7-130">有关详细信息，请参阅[使用 dotnet watch 开发 ASP.NET Core 应用](/aspnet/core/tutorials/dotnet-watch)。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch).</span></span>

- <span data-ttu-id="7bbf7-131">`dotnet dev-certs` 生成和管理在 ASP.NET Core 应用程序开发期间使用的证书。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="7bbf7-132">`dotnet user-secrets` 管理 ASP.NET Core 应用程序中用户机密库的机密。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="7bbf7-133">`dotnet sql-cache` 在 Microsoft SQL Server 数据库中创建表和索引以用于分布式缓存。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="7bbf7-134">`dotnet ef` 是用于管理 Entity Framework Core 应用程序中数据库、<xref:Microsoft.EntityFrameworkCore.DbContext> 对象和迁移的工具。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="7bbf7-135">有关详细信息，请参阅 [EF Core .NET 命令行工具](/ef/core/miscellaneous/cli/dotnet)。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="7bbf7-136">全局工具</span><span class="sxs-lookup"><span data-stu-id="7bbf7-136">Global Tools</span></span>

<span data-ttu-id="7bbf7-137">.NET Core 2.1 支持全局工具，即，可通过命令行在全局范围内使用的自定义工具。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="7bbf7-138">以前版本的 .NET Core 中的扩展性模型只能通过使用 `DotnetCliToolReference` 在每个项目的基础上提供自定义工具。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using `DotnetCliToolReference`.</span></span>

<span data-ttu-id="7bbf7-139">若要安装全局工具，请使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-139">To install a Global Tool, you use the [dotnet tool install](../tools/dotnet-tool-install.md) command.</span></span> <span data-ttu-id="7bbf7-140">例如：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-140">For example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="7bbf7-141">完成安装后，可以通过指定工具名称从命令行运行该工具。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="7bbf7-142">有关详细信息，请参阅 [.NET Core 工具概述](../tools/global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="7bbf7-143">使用 `dotnet tool` 命令管理工具</span><span class="sxs-lookup"><span data-stu-id="7bbf7-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="7bbf7-144">在 .NET Core 2.1 SDK 中，所有工具操作都使用 `dotnet tool` 命令。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-144">In .NET Core 2.1 SDK, all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="7bbf7-145">可用选项如下：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-145">The following options are available:</span></span>

- <span data-ttu-id="7bbf7-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) 安装工具。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="7bbf7-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) 卸载并重新安装工具，它将高效地对其进行更新。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="7bbf7-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) 列出当前安装的工具。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="7bbf7-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) 卸载当前安装的工具。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="7bbf7-150">前滚</span><span class="sxs-lookup"><span data-stu-id="7bbf7-150">Roll forward</span></span>

<span data-ttu-id="7bbf7-151">从 .NET Core 2.0 开始，所有 .NET Core 应用程序都将自动前滚到系统上安装的最新次要版本。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-151">All .NET Core applications starting with .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span>

<span data-ttu-id="7bbf7-152">从 .NET Core 2.0 开始，如果在其中构建应用程序的 .NET Core 版本在运行时不存在，应用程序将针对最新安装的次要版本的 .NET Core 自动运行。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at run time, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="7bbf7-153">换而言之，如果应用程序在 .NET Core 2.0 中生成，而主机系统未安装 .NET Core 2.0 但安装了 .NET Core 2.1，则应用程序将通过 .NET Core 2.1 运行。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7bbf7-154">此前滚行为不适用于预览版本。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="7bbf7-155">默认情况下，它也不适用于主要版本，但可以通过以下设置进行更改。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-155">By default, it also doesn't apply to major releases, but this can be changed with the settings below.</span></span>

<span data-ttu-id="7bbf7-156">可以通过在没有候选共享框架的情况下更改前滚设置来修改此行为。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-156">You can modify this behavior by changing the setting for the roll-forward on no candidate shared framework.</span></span> <span data-ttu-id="7bbf7-157">可用设置如下：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-157">The available settings are:</span></span>

- <span data-ttu-id="7bbf7-158">`0` - 禁用次要版本前滚行为。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-158">`0` - disable minor version roll-forward behavior.</span></span> <span data-ttu-id="7bbf7-159">使用此设置，为 .NET Core 2.0.0 构建的应用程序将前滚到 .NET Core 2.0.1，但不会前滚到 .NET Core 2.2.0 或 .NET Core 3.0.0。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-159">With this setting, an application built for .NET Core 2.0.0 will roll forward to .NET Core 2.0.1, but not to .NET Core 2.2.0 or .NET Core 3.0.0.</span></span>
- <span data-ttu-id="7bbf7-160">`1` - 启用次要版本前滚行为。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-160">`1` - enable minor version roll-forward behavior.</span></span> <span data-ttu-id="7bbf7-161">这是设置的默认值。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-161">This is the default value for the setting.</span></span> <span data-ttu-id="7bbf7-162">使用此设置，为 .NET Core 2.0.0 构建的应用程序将前滚到 .NET Core 2.0.1 或 .NET Core 2.2.0，具体取决于安装的版本，但它不会前滚到 .NET Core3.0.0。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-162">With this setting, an application built for .NET Core 2.0.0 will roll forward to either .NET Core 2.0.1 or .NET Core 2.2.0, depending on which one is installed, but it will not roll forward to .NET Core 3.0.0.</span></span>
- <span data-ttu-id="7bbf7-163">`2` - 启用次要和主要版本前滚行为。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-163">`2` - enable minor and major version roll-forward behavior.</span></span> <span data-ttu-id="7bbf7-164">即使考虑不同的主要版本，如果这样设置，为 .NET Core 2.0.0 构建的应用程序将前滚到 .NET Core 3.0.0。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-164">If set, even different major versions are considered, so an application built for .NET Core 2.0.0 will roll forward to .NET Core 3.0.0.</span></span>

<span data-ttu-id="7bbf7-165">可以通过以下三种方式之一修改此设置：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-165">You can modify this setting in any of three ways:</span></span>

- <span data-ttu-id="7bbf7-166">将 `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` 环境变量设置为所需的值。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-166">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to the desired value.</span></span>

- <span data-ttu-id="7bbf7-167">使用所需的值将下列行添加到 .runtimeconfig.json 文件：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-167">Add the following line with the desired value to the *.runtimeconfig.json* file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="7bbf7-168">使用 [.NET Core CLI](../tools/index.md) 时，请使用所需的值将下列选项添加到 .NET Core 命令，例如 `run`：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-168">When using the [.NET Core CLI](../tools/index.md), add the following option with the desired value to a .NET Core command such as `run`:</span></span>

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

<span data-ttu-id="7bbf7-169">修补程序版本前滚与此设置无关，并且在应用任何潜在的次要或主要版本前滚之后完成。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-169">Patch version roll forward is independent of this setting and is done after any potential minor or major version roll forward is applied.</span></span>

## <a name="deployment"></a><span data-ttu-id="7bbf7-170">部署</span><span class="sxs-lookup"><span data-stu-id="7bbf7-170">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="7bbf7-171">自包含应用程序服务</span><span class="sxs-lookup"><span data-stu-id="7bbf7-171">Self-contained application servicing</span></span>

<span data-ttu-id="7bbf7-172">`dotnet publish` 现发布服务运行时版本的自包含应用程序。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-172">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="7bbf7-173">当你使用 .NET Core 2.1 SDK (v 2.1.300) 发布自包含应用程序时，你的应用程序将包括此 SDK 已知的最新服务运行时版本。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-173">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="7bbf7-174">升级到最新的 SDK 时，你将发布最新的 .NET Core 运行时版本。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-174">When you upgrade to the latest SDK, you'll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="7bbf7-175">这适用于 .NET Core 1.0 运行时以及更高版本。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-175">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="7bbf7-176">自包含发布依赖于 NuGet.org 上的运行时版本。计算机上不需要有服务运行时。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-176">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="7bbf7-177">使用 .NET Core 2.0 SDK，自包含应用程序将通过 .NET Core 2.0.0 运行时发布，除非通过 `RuntimeFrameworkVersion` 属性指定不同版本。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-177">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="7bbf7-178">借助此新行为，你将不再需要设置此属性便可为自包含的应用程序选择更高版本的运行时。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-178">With this new behavior, you'll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="7bbf7-179">最简单的方法是始终通过 .NET Core 2.1 SDK (v 2.1.300) 发布。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-179">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

<span data-ttu-id="7bbf7-180">有关详细信息，请参阅[独立部署运行时前滚](../deploying/runtime-patch-selection.md)。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-180">For more information, see [Self-contained deployment runtime roll forward](../deploying/runtime-patch-selection.md).</span></span>
## <a name="windows-compatibility-pack"></a><span data-ttu-id="7bbf7-181">Windows 兼容包</span><span class="sxs-lookup"><span data-stu-id="7bbf7-181">Windows Compatibility Pack</span></span>

<span data-ttu-id="7bbf7-182">当你将现有代码从 .NET Framework 转移到 .NET Core 时，可以使用 [Windows 兼容包](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-182">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="7bbf7-183">除了 .NET Core 中提供的 API，它使你还能够访问额外的 20,000 多个 API。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-183">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="7bbf7-184">这些 API 包括 <xref:System.Drawing?displayProperty=nameWithType> 命名空间中的类型、<xref:System.Diagnostics.EventLog> 类、WMI、性能计数器、Windows 服务以及 Windows 注册表类型和成员。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-184">These APIs include types in the <xref:System.Drawing?displayProperty=nameWithType> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="7bbf7-185">JIT 编译器改进</span><span class="sxs-lookup"><span data-stu-id="7bbf7-185">JIT compiler improvements</span></span>

<span data-ttu-id="7bbf7-186">.NET Core 包含新的 JIT 编译器技术，称为“分层编译”（也称为“自适应优化”），可以显著提高性能。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-186">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="7bbf7-187">分层编译是一个可选设置。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-187">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="7bbf7-188">由 JIT 编译器执行的重要任务之一是优化代码执行。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-188">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="7bbf7-189">然而，对于很少使用的代码路径，相比运行未优化代码所花费的运行时，编译器可能需要更多的时间来优化代码。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-189">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="7bbf7-190">分层编译介绍了 JIT 编译中的两个阶段：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-190">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="7bbf7-191">第一层，将尽可能快地生成代码。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-191">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="7bbf7-192">第二层，将为那些频繁执行的方法生成优化代码。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-192">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="7bbf7-193">为了增强性能，第二层编译并行执行。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-193">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="7bbf7-194">可以通过这两种方法之一选择加入分层编译。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-194">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="7bbf7-195">若要在所有使用 .NET Core 2.1 SDK 的项目中使用分层编译，请设置以下环境变量：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-195">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="7bbf7-196">若要在每个项目的基础上使用分层编译，将 `<TieredCompilation>` 属性添加到 MSBuild 项目文件的 `<PropertyGroup>` 部分，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-196">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="7bbf7-197">API 更改</span><span class="sxs-lookup"><span data-stu-id="7bbf7-197">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="7bbf7-198">`Span<T>` 和 `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="7bbf7-198">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="7bbf7-199">.NET Core 2.1 包括一些新类型，使得在使用数组和其他类型内存方面要高效得多。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-199">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="7bbf7-200">新类型包括：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-200">The new types include:</span></span>

- <span data-ttu-id="7bbf7-201"><xref:System.Span%601?displayProperty=nameWithType> 和 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-201"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="7bbf7-202"><xref:System.Memory%601?displayProperty=nameWithType> 和 <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-202"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="7bbf7-203">如果没有这些类型，那么在作为数组的一部分或内存缓冲区的一部分传递此类项时，必须在将数据的某些部分传递给方法之前复制该数据部分。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-203">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="7bbf7-204">这些类型提供了该数据的虚拟视图，无需额外的内存分配和复制操作。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-204">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="7bbf7-205">下面的示例使用 <xref:System.Span%601> 和 <xref:System.Memory%601> 实例来提供一个数组 10 个元素的虚拟视图。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-205">The following example uses a <xref:System.Span%601> and <xref:System.Memory%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!code-csharp[Span\<T>](./snippets/dotnet-core-2-1/csharp/program.cs)]

[!code-vb[Memory\<T>](./snippets/dotnet-core-2-1/vb/program.vb)]

### <a name="brotli-compression"></a><span data-ttu-id="7bbf7-206">Brotli 压缩</span><span class="sxs-lookup"><span data-stu-id="7bbf7-206">Brotli compression</span></span>

<span data-ttu-id="7bbf7-207">.NET Core 2.1 添加了对 Brotli 压缩和解压缩的支持。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-207">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="7bbf7-208">Brotli 是在 [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) 中定义的通用无损压缩算法，并且大多数 Web 浏览器和主 Web 服务器都提供支持。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-208">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="7bbf7-209">可以使用基于流的 <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> 类或基于范围的高性能 <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> 和 <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> 类。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-209">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="7bbf7-210">下面的示例用 <xref:System.IO.Compression.BrotliStream> 类演示压缩：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-210">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!code-csharp[Brotli compression](./snippets/dotnet-core-2-1/csharp/brotli.cs#1)]

[!code-vb[Brotli compression](./snippets/dotnet-core-2-1/vb/brotli.vb#1)]

<span data-ttu-id="7bbf7-211"><xref:System.IO.Compression.BrotliStream> 行为等同于 <xref:System.IO.Compression.DeflateStream> 和 <xref:System.IO.Compression.GZipStream>，这样就可以轻松地将调用这些 API 的代码转换为 <xref:System.IO.Compression.BrotliStream>。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-211">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="7bbf7-212">新加密 API 和加密改进</span><span class="sxs-lookup"><span data-stu-id="7bbf7-212">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="7bbf7-213">.NET Core 2.1 包括加密 API 的许多增强功能：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-213">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="7bbf7-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> 在 System.Security.Cryptography.Pkcs 包中提供。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="7bbf7-215">其实现与 .NET Framework 中的 <xref:System.Security.Cryptography.Pkcs.SignedCms> 类相同。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-215">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="7bbf7-216"><xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> 和 <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> 方法的新重载接受一个哈希算法标识符，使调用方能够使用除 SHA-1 以外的算法获得证书指纹值。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-216">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="7bbf7-217">新的基于 <xref:System.Span%601> 的加密 API 可用于哈希、HMAC、加密随机数生成、非对称签名生成、非对称签名处理和 RSA 加密。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-217">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="7bbf7-218">通过使用基于 <xref:System.Span%601> 的实现，<xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> 的性能提高了大约 15%。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-218">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="7bbf7-219">新 <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> 类包括两个新方法：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-219">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="7bbf7-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> 需要固定时间来返回任意两个长度相同的输入，这使得它适用于加密验证，从而避免提供计时旁道信息。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="7bbf7-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> 是不能进行优化的内存清理例程。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="7bbf7-222">静态 <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> 方法用随机值填充 <xref:System.Span%601>。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-222">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="7bbf7-223"><xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> 现在在 Linux 和 macOS 上受支持。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-223">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and macOS.</span></span>

- <span data-ttu-id="7bbf7-224"><xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> 类系列现提供椭圆曲线 Diffie-Hellman (ECDH)。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-224">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="7bbf7-225">外围应用与 .NET Framework 中相同。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-225">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="7bbf7-226"><xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> 返回的实例可以使用 SHA-2 摘要对 OAEP 进行加密或解密，并使用 RSA-PSS 生成或验证签名。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-226">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="7bbf7-227">套接字改进</span><span class="sxs-lookup"><span data-stu-id="7bbf7-227">Sockets improvements</span></span>

<span data-ttu-id="7bbf7-228">.NET Core 包括一个新类型 <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> 和重写的 <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>，两者构成了更高级别网络 API 的基础。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-228">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="7bbf7-229">例如，<xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> 是 <xref:System.Net.Http.HttpClient> 实现的基础。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="7bbf7-230">在以前版本的 .NET Core 中，更高级别的 API 基于本机网络实现。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-230">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="7bbf7-231">.NET Core 2.1 中引入的套接字实现具有很多优点：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-231">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="7bbf7-232">对照以前的实现，可以看到显著的性能改进。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-232">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="7bbf7-233">消除平台依赖项，从而简化部署和维护。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-233">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="7bbf7-234">在所有 .NET Core 平台之间保持行为一致。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-234">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="7bbf7-235"><xref:System.Net.Http.SocketsHttpHandler> 是 .NET Core 2.1 中的默认实现。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-235"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="7bbf7-236">但是，你可以通过调用 <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> 方法配置应用程序以使用较旧的 <xref:System.Net.Http.HttpClientHandler> 类：</span><span class="sxs-lookup"><span data-stu-id="7bbf7-236">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

<span data-ttu-id="7bbf7-237">还可以使用环境变量选择退出使用基于 <xref:System.Net.Http.SocketsHttpHandler> 的套接字实现。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-237">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="7bbf7-238">为此，需要将 `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` 设置为 `false` 或 0。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-238">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="7bbf7-239">在 Windows 上，还可以选择使用 <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>后者依赖于本机实现），或者通过将类实例传递到 <xref:System.Net.Http.HttpClient> 构造函数来使用 <xref:System.Net.Http.SocketsHttpHandler> 类。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-239">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="7bbf7-240">在 Linux 和 macOS 上，可以在每个进程的基础上仅配置 <xref:System.Net.Http.HttpClient>。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-240">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="7bbf7-241">在 Linux 上，如果想要使用旧的 <xref:System.Net.Http.HttpClient> 实现，则需要部署 [libcurl](https://curl.haxx.se/libcurl/)。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-241">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="7bbf7-242">（它随 .NET Core 2.0 一起安装。）</span><span class="sxs-lookup"><span data-stu-id="7bbf7-242">(It is installed with .NET Core 2.0.)</span></span>

### <a name="breaking-changes"></a><span data-ttu-id="7bbf7-243">重大更改</span><span class="sxs-lookup"><span data-stu-id="7bbf7-243">Breaking changes</span></span>

<span data-ttu-id="7bbf7-244">有关中断性变更的信息，请参阅[从版本 2.0 迁移到 2.1 的中断性变更](../compatibility/2.0-2.1.md)。</span><span class="sxs-lookup"><span data-stu-id="7bbf7-244">For information about breaking changes, see [Breaking changes for migration from version 2.0 to 2.1](../compatibility/2.0-2.1.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7bbf7-245">请参阅</span><span class="sxs-lookup"><span data-stu-id="7bbf7-245">See also</span></span>

- [<span data-ttu-id="7bbf7-246">.NET Core 3.1 的新增功能</span><span class="sxs-lookup"><span data-stu-id="7bbf7-246">What's new in .NET Core 3.1</span></span>](dotnet-core-3-1.md)
- [<span data-ttu-id="7bbf7-247">EF Core 2.1 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="7bbf7-247">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)
- [<span data-ttu-id="7bbf7-248">ASP.NET Core 2.1 的新增功能</span><span class="sxs-lookup"><span data-stu-id="7bbf7-248">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
