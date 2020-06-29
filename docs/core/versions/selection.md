---
title: 选择要使用的 .NET Core 版本
description: 了解 .NET Core 如何自动查找和选择适用于程序的运行时版本。 此外，本文还将介绍如何强制使用特定版本。
author: adegeo
ms.author: adegeo
ms.date: 03/24/2020
ms.openlocfilehash: 5e855adc72f0e75e6f31643f8a8618e6d91be06e
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324353"
---
# <a name="select-the-net-core-version-to-use"></a><span data-ttu-id="b289c-104">选择要使用的 .NET Core 版本</span><span class="sxs-lookup"><span data-stu-id="b289c-104">Select the .NET Core version to use</span></span>

<span data-ttu-id="b289c-105">本文介绍 .NET Core 工具、SDK 和运行时在选择版本时所使用的策略。</span><span class="sxs-lookup"><span data-stu-id="b289c-105">This article explains the policies used by the .NET Core tools, SDK, and runtime for selecting versions.</span></span> <span data-ttu-id="b289c-106">这些策略可通过使用指定版本，使正在运行的应用程序之间达到平衡，同时实现开发人员和最终用户计算机的轻松升级。</span><span class="sxs-lookup"><span data-stu-id="b289c-106">These policies provide a balance between running applications using the specified versions and enabling ease of upgrading both developer and end-user machines.</span></span> <span data-ttu-id="b289c-107">这些策略执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="b289c-107">These policies perform the following actions:</span></span>

- <span data-ttu-id="b289c-108">实现 .NET Core 的轻松高效部署，包括安全性和可靠性更新。</span><span class="sxs-lookup"><span data-stu-id="b289c-108">Easy and efficient deployment of .NET Core, including security and reliability updates.</span></span>
- <span data-ttu-id="b289c-109">使用独立于目标运行时的最新工具和命令。</span><span class="sxs-lookup"><span data-stu-id="b289c-109">Use the latest tools and commands independent of target runtime.</span></span>

<span data-ttu-id="b289c-110">需要选择版本的情况如下：</span><span class="sxs-lookup"><span data-stu-id="b289c-110">Version selection occurs:</span></span>

- <span data-ttu-id="b289c-111">运行 SDK 命令时，[SDK 使用最新安装的版本](#the-sdk-uses-the-latest-installed-version)。</span><span class="sxs-lookup"><span data-stu-id="b289c-111">When you run an SDK command, [the SDK uses the latest installed version](#the-sdk-uses-the-latest-installed-version).</span></span>
- <span data-ttu-id="b289c-112">生成程序集时，[目标框架名字对象定义生成时 API](#target-framework-monikers-define-build-time-apis)。</span><span class="sxs-lookup"><span data-stu-id="b289c-112">When you build an assembly, [target framework monikers define build time APIs](#target-framework-monikers-define-build-time-apis).</span></span>
- <span data-ttu-id="b289c-113">运行 .NET Core 应用程序时，[依赖于目标框架的应用程序将前滚](#framework-dependent-apps-roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="b289c-113">When you run a .NET Core application, [target framework dependent apps roll forward](#framework-dependent-apps-roll-forward).</span></span>
- <span data-ttu-id="b289c-114">发布独立应用程序时，[独立部署包括所选的运行时](#self-contained-deployments-include-the-selected-runtime)。</span><span class="sxs-lookup"><span data-stu-id="b289c-114">When you publish a self-contained application, [self-contained deployments include the selected runtime](#self-contained-deployments-include-the-selected-runtime).</span></span>

<span data-ttu-id="b289c-115">本文档其余部分将介绍这四种方案。</span><span class="sxs-lookup"><span data-stu-id="b289c-115">The rest of this document examines those four scenarios.</span></span>

## <a name="the-sdk-uses-the-latest-installed-version"></a><span data-ttu-id="b289c-116">SDK 使用最新安装的版本</span><span class="sxs-lookup"><span data-stu-id="b289c-116">The SDK uses the latest installed version</span></span>

<span data-ttu-id="b289c-117">SDK 命令包括 `dotnet new` 和 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="b289c-117">SDK commands include `dotnet new` and `dotnet run`.</span></span> <span data-ttu-id="b289c-118">.NET Core CLI 必须为每个 `dotnet` 命令选择 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="b289c-118">The .NET Core CLI must choose an SDK version for every `dotnet` command.</span></span> <span data-ttu-id="b289c-119">即使在以下情况下，它也会默认使用计算机上安装的最新 SDK：</span><span class="sxs-lookup"><span data-stu-id="b289c-119">It uses the latest SDK installed on the machine by default, even if:</span></span>

- <span data-ttu-id="b289c-120">项目面向早期 .NET Core 运行时版本。</span><span class="sxs-lookup"><span data-stu-id="b289c-120">The project targets an earlier version of the .NET Core runtime.</span></span>
- <span data-ttu-id="b289c-121">.NET Core SDK 的最新版本是预览版本。</span><span class="sxs-lookup"><span data-stu-id="b289c-121">The latest version of the .NET Core SDK is a preview version.</span></span>

<span data-ttu-id="b289c-122">面向较旧的 .NET Core 运行时版本时，可利用最新的 SDK 功能和功能改进。</span><span class="sxs-lookup"><span data-stu-id="b289c-122">You can take advantage of the latest SDK features and improvements while targeting earlier .NET Core runtime versions.</span></span> <span data-ttu-id="b289c-123">可在不同项目上面向 .NET Core 的多个运行时版本，同时对所有项目使用相同的 SDK 工具。</span><span class="sxs-lookup"><span data-stu-id="b289c-123">You can target multiple runtime versions of .NET Core on different projects, using the same SDK tools for all projects.</span></span>

<span data-ttu-id="b289c-124">在少数情况下，可能需要使用版本较旧的 SDK。</span><span class="sxs-lookup"><span data-stu-id="b289c-124">On rare occasions, you may need to use an earlier version of the SDK.</span></span> <span data-ttu-id="b289c-125">在 [global.json 文件](../tools/global-json.md)中指定该版本  。</span><span class="sxs-lookup"><span data-stu-id="b289c-125">You specify that version in a [*global.json* file](../tools/global-json.md).</span></span> <span data-ttu-id="b289c-126">“使用最新”策略表示仅使用 global.json 指定早于最新安装版本的一个 .NET Core SDK 版本  。</span><span class="sxs-lookup"><span data-stu-id="b289c-126">The "use latest" policy means you only use *global.json* to specify a .NET Core SDK version earlier than the latest installed version.</span></span>

<span data-ttu-id="b289c-127">可将 global.json 放置在文件层次结构中的任何位置  。</span><span class="sxs-lookup"><span data-stu-id="b289c-127">*global.json* can be placed anywhere in the file hierarchy.</span></span> <span data-ttu-id="b289c-128">CLI 从项目目录中向上搜索其找到的第一个 global.json  。</span><span class="sxs-lookup"><span data-stu-id="b289c-128">The CLI searches upward from the project directory for the first *global.json* it finds.</span></span> <span data-ttu-id="b289c-129">由用户控制对哪些项目应用给定的 global.json（按其在文件系统中的位置）  。</span><span class="sxs-lookup"><span data-stu-id="b289c-129">You control which projects a given *global.json* applies to by its place in the file system.</span></span> <span data-ttu-id="b289c-130">.NET CLI 从当前工作目录路径向上导航，以迭代方式搜索 global.json 文件  。</span><span class="sxs-lookup"><span data-stu-id="b289c-130">The .NET CLI searches for a *global.json* file iteratively navigating the path upward from the current working directory.</span></span> <span data-ttu-id="b289c-131">找到的第一个 global.json 文件指定要使用的版本  。</span><span class="sxs-lookup"><span data-stu-id="b289c-131">The first *global.json* file found specifies the version used.</span></span> <span data-ttu-id="b289c-132">如果已安装该 SDK 版本，则使用该版本。</span><span class="sxs-lookup"><span data-stu-id="b289c-132">If that SDK version is installed, that version is used.</span></span> <span data-ttu-id="b289c-133">如果找不到 global.json  中指定的 SDK，则 .NET CLI 将使用[匹配规则](../tools/global-json.md#matching-rules)来选择兼容的 SDK，如果找不到，则会失败。</span><span class="sxs-lookup"><span data-stu-id="b289c-133">If the SDK specified in the *global.json* is not found, the .NET CLI uses [matching rules](../tools/global-json.md#matching-rules) to select a compatible SDK, or fails if none is found.</span></span>

<span data-ttu-id="b289c-134">下面的示例演示 global.json 语法  ：</span><span class="sxs-lookup"><span data-stu-id="b289c-134">The following example shows the *global.json* syntax:</span></span>

``` json
{
  "sdk": {
    "version": "3.0.0"
  }
}
```

<span data-ttu-id="b289c-135">选择 SDK 版本的过程如下：</span><span class="sxs-lookup"><span data-stu-id="b289c-135">The process for selecting an SDK version is:</span></span>

1. <span data-ttu-id="b289c-136">`dotnet` 从当前工作目录向下导航路径，以迭代方式搜索 global.json 文件  。</span><span class="sxs-lookup"><span data-stu-id="b289c-136">`dotnet` searches for a *global.json* file iteratively reverse-navigating the path upward from the current working directory.</span></span>
1. <span data-ttu-id="b289c-137">`dotnet` 使用所找到的第一个 global.json 中指定的 SDK  。</span><span class="sxs-lookup"><span data-stu-id="b289c-137">`dotnet` uses the SDK specified in the first *global.json* found.</span></span>
1. <span data-ttu-id="b289c-138">如果未找到 global.json，`dotnet` 使用最新安装的 SDK  。</span><span class="sxs-lookup"><span data-stu-id="b289c-138">`dotnet` uses the latest installed SDK if no *global.json* is found.</span></span>

<span data-ttu-id="b289c-139">有关选择 SDK 版本的详细信息，可参阅 global.json 相关文章的[匹配规则](../tools/global-json.md#matching-rules)部分  。</span><span class="sxs-lookup"><span data-stu-id="b289c-139">You can learn more about selecting an SDK version in the [Matching rules](../tools/global-json.md#matching-rules) section of the article on *global.json*.</span></span>

## <a name="target-framework-monikers-define-build-time-apis"></a><span data-ttu-id="b289c-140">目标框架名字对象用于定义生成时 API</span><span class="sxs-lookup"><span data-stu-id="b289c-140">Target Framework Monikers define build time APIs</span></span>

<span data-ttu-id="b289c-141">针对在“目标框架名字对象”(TFM) 中定义的 API 构建项目  。</span><span class="sxs-lookup"><span data-stu-id="b289c-141">You build your project against APIs defined in a **Target Framework Moniker** (TFM).</span></span> <span data-ttu-id="b289c-142">在项目文件中指定[目标框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="b289c-142">You specify the [target framework](../../standard/frameworks.md) in the project file.</span></span> <span data-ttu-id="b289c-143">按如下示例所示，设置项目文件中的 `TargetFramework` 元素：</span><span class="sxs-lookup"><span data-stu-id="b289c-143">Set the `TargetFramework` element in your project file as shown in the following example:</span></span>

``` xml
<TargetFramework>netcoreapp3.0</TargetFramework>
```

<span data-ttu-id="b289c-144">可能会针对多个 TFM 构建项目。</span><span class="sxs-lookup"><span data-stu-id="b289c-144">You may build your project against multiple TFMs.</span></span> <span data-ttu-id="b289c-145">对库设置多个目标框架更为常见，但也可对应用程序执行此操作。</span><span class="sxs-lookup"><span data-stu-id="b289c-145">Setting multiple target frameworks is more common for libraries but can be done with applications as well.</span></span> <span data-ttu-id="b289c-146">指定 `TargetFrameworks` 属性（`TargetFramework` 的复数形式）。</span><span class="sxs-lookup"><span data-stu-id="b289c-146">You specify a `TargetFrameworks` property (plural of `TargetFramework`).</span></span> <span data-ttu-id="b289c-147">目标框架以分号分隔，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="b289c-147">The target frameworks are semicolon-delimited as shown in the following example:</span></span>

``` xml
<TargetFrameworks>netcoreapp3.0;net47</TargetFrameworks>
```

<span data-ttu-id="b289c-148">给定的 SDK 支持固定的一组框架，其中的上限框架为 SDK 附带的运行时的目标框架。</span><span class="sxs-lookup"><span data-stu-id="b289c-148">A given SDK supports a fixed set of frameworks, capped to the target framework of the runtime it ships with.</span></span> <span data-ttu-id="b289c-149">例如，.NET Core 3.0 SDK 包含 .NET Core 3.0 运行时，该运行时是 `netcoreapp3.0` 目标框架的一个实现。</span><span class="sxs-lookup"><span data-stu-id="b289c-149">For example, the .NET Core 3.0 SDK includes the .NET Core 3.0 runtime, which is an implementation of the `netcoreapp3.0` target framework.</span></span> <span data-ttu-id="b289c-150">.NET Core 3.0 SDK 支持 `netcoreapp2.1`、`netcoreapp2.2` 和 `netcoreapp3.0`，但不支持 `netcoreapp3.1`（或更高版本）。</span><span class="sxs-lookup"><span data-stu-id="b289c-150">The .NET Core 3.0 SDK supports `netcoreapp2.1`, `netcoreapp2.2`, `netcoreapp3.0`, but not `netcoreapp3.1` (or higher).</span></span> <span data-ttu-id="b289c-151">安装 .NET Core 3.1 SDK 以针对 `netcoreapp3.1` 进行构建。</span><span class="sxs-lookup"><span data-stu-id="b289c-151">You install the .NET Core 3.1 SDK to build for `netcoreapp3.1`.</span></span>

<span data-ttu-id="b289c-152">.NET Standard 目标框架中的上限框架同样是 SDK 附带的运行时的目标框架。</span><span class="sxs-lookup"><span data-stu-id="b289c-152">.NET Standard target frameworks are also capped to the target framework of the runtime the SDK ships with.</span></span> <span data-ttu-id="b289c-153">.NET Core 3.1 SDK 的上限为 `netstandard2.1`。</span><span class="sxs-lookup"><span data-stu-id="b289c-153">The .NET Core 3.1 SDK is capped to `netstandard2.1`.</span></span> <span data-ttu-id="b289c-154">有关详细信息，请参阅 [.NET Standard](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="b289c-154">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

## <a name="framework-dependent-apps-roll-forward"></a><span data-ttu-id="b289c-155">依赖于框架的应用会前滚</span><span class="sxs-lookup"><span data-stu-id="b289c-155">Framework-dependent apps roll forward</span></span>

<span data-ttu-id="b289c-156">在使用 [`dotnet run`](../tools/dotnet-run.md) 从源运行应用程序时，在使用 [`dotnet myapp.dll`](../tools/dotnet.md#description) 从[框架相关部署  ](../deploying/index.md#publish-runtime-dependent)运行应用程序时，或使用 `myapp.exe` 从[框架相关可执行文件  ](../deploying/index.md#publish-runtime-dependent)运行应用程序时，`dotnet` 可执行文件是应用程序的主机  。</span><span class="sxs-lookup"><span data-stu-id="b289c-156">When you run an application from source with [`dotnet run`](../tools/dotnet-run.md), from a [**framework-dependent deployment**](../deploying/index.md#publish-runtime-dependent) with [`dotnet myapp.dll`](../tools/dotnet.md#description), or from a [**framework-dependent executable**](../deploying/index.md#publish-runtime-dependent) with `myapp.exe`, the `dotnet` executable is the **host** for the application.</span></span>

<span data-ttu-id="b289c-157">该主机选择计算机上安装的最新修补程序版本。</span><span class="sxs-lookup"><span data-stu-id="b289c-157">The host chooses the latest patch version installed on the machine.</span></span> <span data-ttu-id="b289c-158">例如，如果在项目文件中指定 `netcoreapp3.0`，并且 `3.0.4` 是安装的最新 .NET 运行时，则使用 `3.0.4` 运行时。</span><span class="sxs-lookup"><span data-stu-id="b289c-158">For example, if you specified `netcoreapp3.0` in your project file, and `3.0.4` is the latest .NET runtime installed, the `3.0.4` runtime is used.</span></span>

<span data-ttu-id="b289c-159">如果未找到可接受的 `3.0.*` 版本，则使用新的 `3.*` 版本。</span><span class="sxs-lookup"><span data-stu-id="b289c-159">If no acceptable `3.0.*` version is found, a new `3.*` version is used.</span></span> <span data-ttu-id="b289c-160">例如，如果指定了 `netcoreapp3.0` 并且仅安装了 `3.1.0`，则应用程序在运行时使用 `3.1.0` 运行时。</span><span class="sxs-lookup"><span data-stu-id="b289c-160">For example, if you specified `netcoreapp3.0` and only `3.1.0` is installed, the application runs using the `3.1.0` runtime.</span></span> <span data-ttu-id="b289c-161">此行为称为“次要版本前滚”。</span><span class="sxs-lookup"><span data-stu-id="b289c-161">This behavior is referred to as "minor version roll-forward."</span></span> <span data-ttu-id="b289c-162">此外，不会考虑较低版本。</span><span class="sxs-lookup"><span data-stu-id="b289c-162">Lower versions also won't be considered.</span></span> <span data-ttu-id="b289c-163">如果未安装可接受的运行时，应用程序将不会运行。</span><span class="sxs-lookup"><span data-stu-id="b289c-163">When no acceptable runtime is installed, the application won't run.</span></span>

<span data-ttu-id="b289c-164">如果你面向版本 3.0，则下面几个使用示例展示了此行为：</span><span class="sxs-lookup"><span data-stu-id="b289c-164">A few usage examples demonstrate the behavior, if you target 3.0:</span></span>

- <span data-ttu-id="b289c-165">✔️ 指定 3.0。</span><span class="sxs-lookup"><span data-stu-id="b289c-165">✔️ 3.0 is specified.</span></span> <span data-ttu-id="b289c-166">3.0.5 是安装的最高修补程序版本。</span><span class="sxs-lookup"><span data-stu-id="b289c-166">3.0.5 is the highest patch version installed.</span></span> <span data-ttu-id="b289c-167">使用 3.0.5。</span><span class="sxs-lookup"><span data-stu-id="b289c-167">3.0.5 is used.</span></span>
- <span data-ttu-id="b289c-168">❌ 指定 3.0。</span><span class="sxs-lookup"><span data-stu-id="b289c-168">❌ 3.0 is specified.</span></span> <span data-ttu-id="b289c-169">未安装 3.0.\* 版本。</span><span class="sxs-lookup"><span data-stu-id="b289c-169">No 3.0.\* versions are installed.</span></span> <span data-ttu-id="b289c-170">2.1.1 是安装的最高运行时版本。</span><span class="sxs-lookup"><span data-stu-id="b289c-170">2.1.1 is the highest runtime installed.</span></span> <span data-ttu-id="b289c-171">会显示一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="b289c-171">An error message is displayed.</span></span>
- <span data-ttu-id="b289c-172">✔️ 指定 3.0。</span><span class="sxs-lookup"><span data-stu-id="b289c-172">✔️ 3.0 is specified.</span></span> <span data-ttu-id="b289c-173">未安装 3.0.\* 版本。</span><span class="sxs-lookup"><span data-stu-id="b289c-173">No 3.0.\* versions are installed.</span></span> <span data-ttu-id="b289c-174">3.1.0 是安装的最高运行时版本。</span><span class="sxs-lookup"><span data-stu-id="b289c-174">3.1.0 is the highest runtime version installed.</span></span> <span data-ttu-id="b289c-175">使用 3.1.0。</span><span class="sxs-lookup"><span data-stu-id="b289c-175">3.1.0 is used.</span></span>
- <span data-ttu-id="b289c-176">❌ 指定 2.0。</span><span class="sxs-lookup"><span data-stu-id="b289c-176">❌ 2.0 is specified.</span></span> <span data-ttu-id="b289c-177">未安装 2.x 版本。</span><span class="sxs-lookup"><span data-stu-id="b289c-177">No 2.x versions are installed.</span></span> <span data-ttu-id="b289c-178">3.0.0 是安装的最高运行时版本。</span><span class="sxs-lookup"><span data-stu-id="b289c-178">3.0.0 is the highest runtime installed.</span></span> <span data-ttu-id="b289c-179">会显示一条错误消息。</span><span class="sxs-lookup"><span data-stu-id="b289c-179">An error message is displayed.</span></span>

<span data-ttu-id="b289c-180">次要版本回滚会产生一个可能影响最终用户的副作用。</span><span class="sxs-lookup"><span data-stu-id="b289c-180">Minor version roll-forward has one side-effect that may affect end users.</span></span> <span data-ttu-id="b289c-181">请参考以下方案：</span><span class="sxs-lookup"><span data-stu-id="b289c-181">Consider the following scenario:</span></span>

1. <span data-ttu-id="b289c-182">应用程序指定需要版本 3.0。</span><span class="sxs-lookup"><span data-stu-id="b289c-182">The application specifies that 3.0 is required.</span></span>
2. <span data-ttu-id="b289c-183">运行时，未安装 3.0.\*，安装的是 3.1.0。</span><span class="sxs-lookup"><span data-stu-id="b289c-183">When run, version 3.0.\* is not installed, however, 3.1.0 is.</span></span> <span data-ttu-id="b289c-184">将使用版本 3.1.0。</span><span class="sxs-lookup"><span data-stu-id="b289c-184">Version 3.1.0 will be used.</span></span>
3. <span data-ttu-id="b289c-185">稍后，用户重新安装 3.0.5 和运行应用程序，而现将使用版本 3.0.5。</span><span class="sxs-lookup"><span data-stu-id="b289c-185">Later, the user installs 3.0.5 and runs the application again, 3.0.5 will now be used.</span></span>

<span data-ttu-id="b289c-186">3\.0.5 和 3.1.0 可能具有不同行为，序列化二进制数据等方案中尤其如此。</span><span class="sxs-lookup"><span data-stu-id="b289c-186">It's possible that 3.0.5 and 3.1.0 behave differently, particularly for scenarios like serializing binary data.</span></span>

## <a name="self-contained-deployments-include-the-selected-runtime"></a><span data-ttu-id="b289c-187">独立部署包括所选的运行时</span><span class="sxs-lookup"><span data-stu-id="b289c-187">Self-contained deployments include the selected runtime</span></span>

<span data-ttu-id="b289c-188">可以将应用程序作为[独立分发](../deploying/index.md#publish-self-contained)进行发布  。</span><span class="sxs-lookup"><span data-stu-id="b289c-188">You can publish an application as a [**self-contained distribution**](../deploying/index.md#publish-self-contained).</span></span> <span data-ttu-id="b289c-189">此方法可将 .NET Core 运行时和库与应用程序进行捆绑。</span><span class="sxs-lookup"><span data-stu-id="b289c-189">This approach bundles the .NET Core runtime and libraries with your application.</span></span> <span data-ttu-id="b289c-190">独立部署不具有对运行时环境的依赖关系。</span><span class="sxs-lookup"><span data-stu-id="b289c-190">Self-contained deployments don't have a dependency on runtime environments.</span></span> <span data-ttu-id="b289c-191">在发布时（而不是运行时）选择运行时版本。</span><span class="sxs-lookup"><span data-stu-id="b289c-191">Runtime version selection occurs at publishing time, not run time.</span></span>

<span data-ttu-id="b289c-192">发布进程将选择给定运行时系列中的最新修补程序版本。</span><span class="sxs-lookup"><span data-stu-id="b289c-192">The publishing process selects the latest patch version of the given runtime family.</span></span> <span data-ttu-id="b289c-193">例如，`dotnet publish` 将选择 .NET Core 3.0.4（如果它是 .NET Core 3.0 运行时系列中的最新修补程序版本）。</span><span class="sxs-lookup"><span data-stu-id="b289c-193">For example, `dotnet publish` will select .NET Core 3.0.4 if it is the latest patch version in the .NET Core 3.0 runtime family.</span></span> <span data-ttu-id="b289c-194">目标框架（包括最新安装的安全修补程序）与应用程序捆绑打包。</span><span class="sxs-lookup"><span data-stu-id="b289c-194">The target framework (including the latest installed security patches) is packaged with the application.</span></span>

<span data-ttu-id="b289c-195">如果为应用程序指定的最新版本不满足要求，会出现错误。</span><span class="sxs-lookup"><span data-stu-id="b289c-195">It's an error if the minimum version specified for an application isn't satisfied.</span></span> <span data-ttu-id="b289c-196">`dotnet publish` 绑定到最新的运行时修补程序版本（在给定的主要及次要版本系列内）。</span><span class="sxs-lookup"><span data-stu-id="b289c-196">`dotnet publish` binds to the latest runtime patch version (within a given major.minor version family).</span></span> <span data-ttu-id="b289c-197">`dotnet publish` 不支持 `dotnet run` 的前滚语义。</span><span class="sxs-lookup"><span data-stu-id="b289c-197">`dotnet publish` doesn't support the roll-forward semantics of `dotnet run`.</span></span> <span data-ttu-id="b289c-198">有关修补程序和独立部署的详细信息，请参阅有关 .NET Core 应用程序部署中[运行时修补程序选择](../deploying/runtime-patch-selection.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="b289c-198">For more information about patches and self-contained deployments, see the article on [runtime patch selection](../deploying/runtime-patch-selection.md) in deploying .NET Core applications.</span></span>

<span data-ttu-id="b289c-199">独立部署可能需要特定修补程序版本。</span><span class="sxs-lookup"><span data-stu-id="b289c-199">Self-contained deployments may require a specific patch version.</span></span> <span data-ttu-id="b289c-200">可以重写项目文件中的最低运行时修补程序版本（重写为更高或更低版本），如下例所示：</span><span class="sxs-lookup"><span data-stu-id="b289c-200">You can override the minimum runtime patch version (to higher or lower versions) in the project file, as shown in the following example:</span></span>

``` xml
<RuntimeFrameworkVersion>3.0.4</RuntimeFrameworkVersion>
```

<span data-ttu-id="b289c-201">`RuntimeFrameworkVersion` 元素重写默认版本策略。</span><span class="sxs-lookup"><span data-stu-id="b289c-201">The `RuntimeFrameworkVersion` element  overrides the default version policy.</span></span> <span data-ttu-id="b289c-202">对于独立部署，`RuntimeFrameworkVersion` 指定确切的运行时框架版本  。</span><span class="sxs-lookup"><span data-stu-id="b289c-202">For self-contained deployments, the `RuntimeFrameworkVersion` specifies the *exact* runtime framework version.</span></span> <span data-ttu-id="b289c-203">对于依赖于框架的应用程序，`RuntimeFrameworkVersion` 指定所需的最低运行时框架版本  。</span><span class="sxs-lookup"><span data-stu-id="b289c-203">For framework-dependent applications, the `RuntimeFrameworkVersion` specifies the *minimum* required runtime framework version.</span></span>

## <a name="see-also"></a><span data-ttu-id="b289c-204">请参阅</span><span class="sxs-lookup"><span data-stu-id="b289c-204">See also</span></span>

- <span data-ttu-id="b289c-205">[下载和安装 .NET Core](../install/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b289c-205">[Download and install .NET Core](../install/index.md).</span></span>
- <span data-ttu-id="b289c-206">[如何删除 .NET Core 运行时和 SDK](../install/remove-runtime-sdk-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="b289c-206">[How to remove the .NET Core Runtime and SDK](../install/remove-runtime-sdk-versions.md).</span></span>
