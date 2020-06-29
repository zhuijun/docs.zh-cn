---
title: 使用 .NET Core CLI 发布应用
description: 了解如何使用 .NET Core CLI 命令发布 .NET Core 应用。
author: adegeo
ms.author: adegeo
ms.date: 12/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: a592b397d1ffee5b224638a8d17ce6fa9e44eea2
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325030"
---
# <a name="publish-net-core-apps-with-the-net-core-cli"></a><span data-ttu-id="aa613-103">使用 .NET Core CLI 发布 .NET Core 应用</span><span class="sxs-lookup"><span data-stu-id="aa613-103">Publish .NET Core apps with the .NET Core CLI</span></span>

<span data-ttu-id="aa613-104">本文演示了如何使用命令行发布 .NET Core 应用程序。</span><span class="sxs-lookup"><span data-stu-id="aa613-104">This article demonstrates how you can publish your .NET Core application from the command line.</span></span> <span data-ttu-id="aa613-105">.NET Core 提供了三种发布应用程序的方式。</span><span class="sxs-lookup"><span data-stu-id="aa613-105">.NET Core provides three ways to publish your applications.</span></span> <span data-ttu-id="aa613-106">依赖于框架的部署生成一个跨平台 .dll 文件，该文件使用本地安装的 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="aa613-106">Framework-dependent deployment produces a cross-platform .dll file that uses the locally installed .NET Core runtime.</span></span> <span data-ttu-id="aa613-107">依赖于框架的可执行文件生成特定于平台的可执行文件，后者使用本地安装的 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="aa613-107">Framework-dependent executable produces a platform-specific executable that uses the locally installed .NET Core runtime.</span></span> <span data-ttu-id="aa613-108">独立可执行文件生成特定于平台的可执行文件，并包含 .NET Core 运行时的本地副本。</span><span class="sxs-lookup"><span data-stu-id="aa613-108">Self-contained executable produces a platform-specific executable and includes a local copy of the .NET Core runtime.</span></span>

<span data-ttu-id="aa613-109">请参阅 [.NET Core 应用程序部署](index.md)了解有关这些发布模式的概述。</span><span class="sxs-lookup"><span data-stu-id="aa613-109">For an overview of these publishing modes, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="aa613-110">正在查找有关 CLI 的快速帮助？</span><span class="sxs-lookup"><span data-stu-id="aa613-110">Looking for some quick help on using the CLI?</span></span> <span data-ttu-id="aa613-111">下表列出了一些关于如何发布应用的示例。</span><span class="sxs-lookup"><span data-stu-id="aa613-111">The following table shows some examples of how to publish your app.</span></span> <span data-ttu-id="aa613-112">可以使用 `-f <TFM>` 参数或通过编辑项目文件来指定目标框架。</span><span class="sxs-lookup"><span data-stu-id="aa613-112">You can specify the target framework with the `-f <TFM>` parameter or by editing the project file.</span></span> <span data-ttu-id="aa613-113">有关详细信息，请参阅[发布基本知识](#publishing-basics)。</span><span class="sxs-lookup"><span data-stu-id="aa613-113">For more information, see [Publishing basics](#publishing-basics).</span></span>

| <span data-ttu-id="aa613-114">发布模式</span><span class="sxs-lookup"><span data-stu-id="aa613-114">Publish Mode</span></span> | <span data-ttu-id="aa613-115">SDK 版本</span><span class="sxs-lookup"><span data-stu-id="aa613-115">SDK Version</span></span> | <span data-ttu-id="aa613-116">命令</span><span class="sxs-lookup"><span data-stu-id="aa613-116">Command</span></span> |
| ------------ | ----------- | ------- |
| <span data-ttu-id="aa613-117">依赖框架的部署</span><span class="sxs-lookup"><span data-stu-id="aa613-117">Framework-dependent deployment</span></span> | <span data-ttu-id="aa613-118">2.x</span><span class="sxs-lookup"><span data-stu-id="aa613-118">2.x</span></span> | `dotnet publish -c Release` |
| <span data-ttu-id="aa613-119">依赖于框架的可执行文件</span><span class="sxs-lookup"><span data-stu-id="aa613-119">Framework-dependent executable</span></span> | <span data-ttu-id="aa613-120">2.2</span><span class="sxs-lookup"><span data-stu-id="aa613-120">2.2</span></span> | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | <span data-ttu-id="aa613-121">3.0</span><span class="sxs-lookup"><span data-stu-id="aa613-121">3.0</span></span> | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | <span data-ttu-id="aa613-122">3.0\*</span><span class="sxs-lookup"><span data-stu-id="aa613-122">3.0\*</span></span> | `dotnet publish -c Release` |
| <span data-ttu-id="aa613-123">独立部署</span><span class="sxs-lookup"><span data-stu-id="aa613-123">Self-contained deployment</span></span>      | <span data-ttu-id="aa613-124">2.1</span><span class="sxs-lookup"><span data-stu-id="aa613-124">2.1</span></span> | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | <span data-ttu-id="aa613-125">2.2</span><span class="sxs-lookup"><span data-stu-id="aa613-125">2.2</span></span> | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | <span data-ttu-id="aa613-126">3.0</span><span class="sxs-lookup"><span data-stu-id="aa613-126">3.0</span></span> | `dotnet publish -c Release -r <RID> --self-contained true` |

<span data-ttu-id="aa613-127">\* 使用 SDK 版本 3.0 时，框架依赖可执行文件是运行基本 `dotnet publish` 命令时的默认发布模式。</span><span class="sxs-lookup"><span data-stu-id="aa613-127">\* When using SDK version 3.0, framework-dependent executable is the default publishing mode when running the basic `dotnet publish` command.</span></span> <span data-ttu-id="aa613-128">仅当项目定目标到 .NET Core 2.1  或 .NET Core 3.0  时，这才适用。</span><span class="sxs-lookup"><span data-stu-id="aa613-128">This only applies when the project targets either **.NET Core 2.1** or **.NET Core 3.0**.</span></span>

## <a name="publishing-basics"></a><span data-ttu-id="aa613-129">发布基本知识</span><span class="sxs-lookup"><span data-stu-id="aa613-129">Publishing basics</span></span>

<span data-ttu-id="aa613-130">发布应用时，项目文件的 `<TargetFramework>` 设置指定默认目标框架。</span><span class="sxs-lookup"><span data-stu-id="aa613-130">The `<TargetFramework>` setting of the project file specifies the default target framework when you publish your app.</span></span> <span data-ttu-id="aa613-131">可以将目标框架更改为任意有效[目标框架名字对象 (TFM)](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="aa613-131">You can change the target framework to any valid [Target Framework Moniker (TFM)](../../standard/frameworks.md).</span></span> <span data-ttu-id="aa613-132">例如，如果项目使用 `<TargetFramework>netcoreapp2.2</TargetFramework>`，则会创建面向 .NET Core 2.2 的二进制文件。</span><span class="sxs-lookup"><span data-stu-id="aa613-132">For example, if your project uses `<TargetFramework>netcoreapp2.2</TargetFramework>`, a binary that targets .NET Core 2.2 is created.</span></span> <span data-ttu-id="aa613-133">此设置中指定的 TFM 是[`dotnet publish`](../tools/dotnet-publish.md) 命令使用的默认目标。</span><span class="sxs-lookup"><span data-stu-id="aa613-133">The TFM specified in this setting is the default target used by the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="aa613-134">如果要以多个框架为目标，可以将 `<TargetFrameworks>` 设置设置为多个以分号分隔的 TFM 值。</span><span class="sxs-lookup"><span data-stu-id="aa613-134">If you want to target more than one framework, you can set the `<TargetFrameworks>` setting to more than one TFM value separated by a semicolon.</span></span> <span data-ttu-id="aa613-135">可以使用 `dotnet publish -f <TFM>` 命令发布其中一个框架。</span><span class="sxs-lookup"><span data-stu-id="aa613-135">You can publish one of the frameworks with the `dotnet publish -f <TFM>` command.</span></span> <span data-ttu-id="aa613-136">例如，如果有 `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` 并运行 `dotnet publish -f netcoreapp2.1`，则会创建面向 .NET Core 2.1 的二进制文件。</span><span class="sxs-lookup"><span data-stu-id="aa613-136">For example, if you have `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` and run `dotnet publish -f netcoreapp2.1`, a binary that targets .NET Core 2.1 is created.</span></span>

<span data-ttu-id="aa613-137">除非另有设置，否则 [`dotnet publish`](../tools/dotnet-publish.md) 命令的输出目录为 `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`。</span><span class="sxs-lookup"><span data-stu-id="aa613-137">Unless otherwise set, the output directory of the [`dotnet publish`](../tools/dotnet-publish.md) command is `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`.</span></span> <span data-ttu-id="aa613-138">除非使用 `-c` 参数进行更改，否则默认的 BUILD-CONFIGURATION 模式为 Debug。</span><span class="sxs-lookup"><span data-stu-id="aa613-138">The default **BUILD-CONFIGURATION** mode is **Debug** unless changed with the `-c` parameter.</span></span> <span data-ttu-id="aa613-139">例如，`dotnet publish -c Release -f netcoreapp2.1` 发布到 `myfolder/bin/Release/netcoreapp2.1/publish/`。</span><span class="sxs-lookup"><span data-stu-id="aa613-139">For example, `dotnet publish -c Release -f netcoreapp2.1` publishes to `myfolder/bin/Release/netcoreapp2.1/publish/`.</span></span>

<span data-ttu-id="aa613-140">如果使用 .NET Core SDK 3.0 或更高版本，则面向 .NET Core 版本 2.1、2.2、3.0 或更高版本的应用的默认发布模式为依赖于框架的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="aa613-140">If you use .NET Core SDK 3.0 or later, the default publish mode for apps that target .NET Core versions 2.1, 2.2, 3.0, or a later version, is framework-dependent executable.</span></span>

<span data-ttu-id="aa613-141">如果使用 .NET Core SDK 2.1，则面向 .NET Core 版本 2.1 和 2.2 的应用的默认发布模式为依赖于框架的部署。</span><span class="sxs-lookup"><span data-stu-id="aa613-141">If you use .NET Core SDK 2.1, the default publish mode for apps that target .NET Core versions 2.1 and 2.2 is framework-dependent deployment.</span></span>

### <a name="native-dependencies"></a><span data-ttu-id="aa613-142">本机依赖项</span><span class="sxs-lookup"><span data-stu-id="aa613-142">Native dependencies</span></span>

<span data-ttu-id="aa613-143">如果应用具有本机依赖项，则只能在相同操作系统上运行。</span><span class="sxs-lookup"><span data-stu-id="aa613-143">If your app has native dependencies, it may not run on a different operating system.</span></span> <span data-ttu-id="aa613-144">例如，如果应用使用本机 Windows API，则不能在 macOS 或 Linux 上运行。</span><span class="sxs-lookup"><span data-stu-id="aa613-144">For example, if your app uses the native Windows API, it won't run on macOS or Linux.</span></span> <span data-ttu-id="aa613-145">需要提供特定于平台的代码并为每个平台编译可执行文件。</span><span class="sxs-lookup"><span data-stu-id="aa613-145">You would need to provide platform-specific code and compile an executable for each platform.</span></span>

<span data-ttu-id="aa613-146">另外，如果引用的库具有本机依赖项，则应用可能无法在每个平台上运行。</span><span class="sxs-lookup"><span data-stu-id="aa613-146">Consider also, if a library you referenced has a native dependency, your app may not run on every platform.</span></span> <span data-ttu-id="aa613-147">但是，引用的 NuGet 包可能包含特定于平台的版本，以便处理所需的本机依赖项。</span><span class="sxs-lookup"><span data-stu-id="aa613-147">However, it's possible a NuGet package you're referencing has included platform-specific versions to handle the required native dependencies for you.</span></span>

<span data-ttu-id="aa613-148">使用本机依赖项分发应用时，可能需要使用 `dotnet publish -r <RID>` 开关来指定想要发布的目标平台。</span><span class="sxs-lookup"><span data-stu-id="aa613-148">When distributing an app with native dependencies, you may need to use the `dotnet publish -r <RID>` switch to specify the target platform you want to publish for.</span></span> <span data-ttu-id="aa613-149">有关运行时标识符的详细信息，请参阅[运行时标识符 (RID) 目录](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="aa613-149">For a list of runtime identifiers, see [Runtime Identifier (RID) catalog](../rid-catalog.md).</span></span>

<span data-ttu-id="aa613-150">有关特定于平台的二进制文件的详细信息，请参阅[依赖于框架的可执行文件](#framework-dependent-executable)和[独立部署](#self-contained-deployment)部分。</span><span class="sxs-lookup"><span data-stu-id="aa613-150">More information about platform-specific binaries is covered in the [Framework-dependent executable](#framework-dependent-executable) and [Self-contained deployment](#self-contained-deployment) sections.</span></span>

## <a name="sample-app"></a><span data-ttu-id="aa613-151">示例应用</span><span class="sxs-lookup"><span data-stu-id="aa613-151">Sample app</span></span>

<span data-ttu-id="aa613-152">可使用以下应用来探索发布命令。</span><span class="sxs-lookup"><span data-stu-id="aa613-152">You can use the following app to explore the publishing commands.</span></span> <span data-ttu-id="aa613-153">通过在终端中运行以下命令来创建应用：</span><span class="sxs-lookup"><span data-stu-id="aa613-153">The app is created by running the following commands in your terminal:</span></span>

```dotnetcli
mkdir apptest1
cd apptest1
dotnet new console
dotnet add package Figgle
```

<span data-ttu-id="aa613-154">控制台模板生成的 `Program.cs` 或 `Program.vb` 文件需要进行以下更改：</span><span class="sxs-lookup"><span data-stu-id="aa613-154">The `Program.cs` or `Program.vb` file that is generated by the console template needs to be changed to the following:</span></span>

```csharp
using System;

namespace apptest1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"));
        }
    }
}
```

```vb
Module Program
    Sub Main(args As String())
        Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"))
    End Sub
End Module
```

<span data-ttu-id="aa613-155">运行应用 ([`dotnet run`](../tools/dotnet-run.md)) 时，将显示以下输出：</span><span class="sxs-lookup"><span data-stu-id="aa613-155">When you run the app ([`dotnet run`](../tools/dotnet-run.md)), the following output is displayed:</span></span>

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a><span data-ttu-id="aa613-156">依赖框架的部署</span><span class="sxs-lookup"><span data-stu-id="aa613-156">Framework-dependent deployment</span></span>

<span data-ttu-id="aa613-157">对于 .NET Core SDK 2.x CLI，依赖于框架的部署 (FDD) 是基本 `dotnet publish` 命令的默认模式。</span><span class="sxs-lookup"><span data-stu-id="aa613-157">For the .NET Core SDK 2.x CLI, framework-dependent deployment (FDD) is the default mode for the basic `dotnet publish` command.</span></span>

<span data-ttu-id="aa613-158">将应用作为 FDD 发布时，会在 `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` 文件夹中创建 `<PROJECT-NAME>.dll` 文件。</span><span class="sxs-lookup"><span data-stu-id="aa613-158">When you publish your app as an FDD, a `<PROJECT-NAME>.dll` file is created in the `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` folder.</span></span> <span data-ttu-id="aa613-159">若要运行应用，请导航到输出文件夹并使用 `dotnet <PROJECT-NAME>.dll` 命令。</span><span class="sxs-lookup"><span data-stu-id="aa613-159">To run your app, navigate to the output folder and use the `dotnet <PROJECT-NAME>.dll` command.</span></span>

<span data-ttu-id="aa613-160">应用配置为面向 .NET Core 的特定版本。</span><span class="sxs-lookup"><span data-stu-id="aa613-160">Your app is configured to target a specific version of .NET Core.</span></span> <span data-ttu-id="aa613-161">目标 .NET Core 运行时需要位于运行应用程序的任何计算机上。</span><span class="sxs-lookup"><span data-stu-id="aa613-161">That targeted .NET Core runtime is required to be on any machine where your app runs.</span></span> <span data-ttu-id="aa613-162">例如，如果应用面向 .NET Core 2.2，则运行应用的任何计算机都必须已安装 .NET Core 2.2 运行时。</span><span class="sxs-lookup"><span data-stu-id="aa613-162">For example, if your app targets .NET Core 2.2, any machine that your app runs on must have the .NET Core 2.2 runtime installed.</span></span> <span data-ttu-id="aa613-163">如[发布基础知识](#publishing-basics)部分中所述，可以编辑项目文件为更改默认目标框架或面向多个框架。</span><span class="sxs-lookup"><span data-stu-id="aa613-163">As stated in the [Publishing basics](#publishing-basics) section, you can edit your project file to change the default target framework or to target more than one framework.</span></span>

<span data-ttu-id="aa613-164">发布 FDD 会创建一个应用，该应用会自动前滚到运行该应用的系统上可用的最新 .NET Core 安全修补程序。</span><span class="sxs-lookup"><span data-stu-id="aa613-164">Publishing an FDD creates an app that automatically rolls-forward to the latest .NET Core security patch available on the system that runs the app.</span></span> <span data-ttu-id="aa613-165">有关编译时的版本绑定的详细信息，请参阅[选择要使用的 .NET Core 版本](../versions/selection.md#framework-dependent-apps-roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="aa613-165">For more information on version binding at compile time, see [Select the .NET Core version to use](../versions/selection.md#framework-dependent-apps-roll-forward).</span></span>

## <a name="framework-dependent-executable"></a><span data-ttu-id="aa613-166">依赖于框架的可执行文件</span><span class="sxs-lookup"><span data-stu-id="aa613-166">Framework-dependent executable</span></span>

<span data-ttu-id="aa613-167">对于 .NET Core SDK 3.x CLI，依赖于框架的可执行文件 (FDE) 是基本 `dotnet publish` 命令的默认模式。</span><span class="sxs-lookup"><span data-stu-id="aa613-167">For the .NET Core SDK 3.x CLI, framework-dependent executable (FDE) is the default mode for the basic `dotnet publish` command.</span></span> <span data-ttu-id="aa613-168">只要想要面向当前操作系统，就不需要指定任何其他参数。</span><span class="sxs-lookup"><span data-stu-id="aa613-168">You don't need to specify any other parameters, as long as you want to target the current operating system.</span></span>

<span data-ttu-id="aa613-169">在此模式下，将创建特定于平台的可执行主机来托管跨平台应用。</span><span class="sxs-lookup"><span data-stu-id="aa613-169">In this mode, a platform-specific executable host is created to host your cross-platform app.</span></span> <span data-ttu-id="aa613-170">此模式类似于 FDD，因为 FDD 需要 `dotnet` 命令形式的主机。</span><span class="sxs-lookup"><span data-stu-id="aa613-170">This mode is similar to FDD, as FDD requires a host in the form of the `dotnet` command.</span></span> <span data-ttu-id="aa613-171">每个平台的主机可执行文件名各不相同，其文件名类似于 `<PROJECT-FILE>.exe`。</span><span class="sxs-lookup"><span data-stu-id="aa613-171">The host executable filename varies per platform and is named something similar to `<PROJECT-FILE>.exe`.</span></span> <span data-ttu-id="aa613-172">可以直接运行此可执行文件，而不是调用 `dotnet <PROJECT-FILE>.dll`，这仍然是运行应用的可接受方式。</span><span class="sxs-lookup"><span data-stu-id="aa613-172">You can run this executable directly instead of calling `dotnet <PROJECT-FILE>.dll`, which is still an acceptable way to run the app.</span></span>

<span data-ttu-id="aa613-173">应用配置为面向 .NET Core 的特定版本。</span><span class="sxs-lookup"><span data-stu-id="aa613-173">Your app is configured to target a specific version of .NET Core.</span></span> <span data-ttu-id="aa613-174">目标 .NET Core 运行时需要位于运行应用程序的任何计算机上。</span><span class="sxs-lookup"><span data-stu-id="aa613-174">That targeted .NET Core runtime is required to be on any machine where your app runs.</span></span> <span data-ttu-id="aa613-175">例如，如果应用面向 .NET Core 2.2，则运行应用的任何计算机都必须已安装 .NET Core 2.2 运行时。</span><span class="sxs-lookup"><span data-stu-id="aa613-175">For example, if your app targets .NET Core 2.2, any machine that your app runs on must have the .NET Core 2.2 runtime installed.</span></span> <span data-ttu-id="aa613-176">如[发布基础知识](#publishing-basics)部分中所述，可以编辑项目文件为更改默认目标框架或面向多个框架。</span><span class="sxs-lookup"><span data-stu-id="aa613-176">As stated in the [Publishing basics](#publishing-basics) section, you can edit your project file to change the default target framework or to target more than one framework.</span></span>

<span data-ttu-id="aa613-177">发布 FDE 会创建一个应用，该应用会自动前滚到运行该应用的系统上可用的最新 .NET Core 安全修补程序。</span><span class="sxs-lookup"><span data-stu-id="aa613-177">Publishing an FDE creates an app that automatically rolls-forward to the latest .NET Core security patch available on the system that runs the app.</span></span> <span data-ttu-id="aa613-178">有关编译时的版本绑定的详细信息，请参阅[选择要使用的 .NET Core 版本](../versions/selection.md#framework-dependent-apps-roll-forward)。</span><span class="sxs-lookup"><span data-stu-id="aa613-178">For more information on version binding at compile time, see [Select the .NET Core version to use](../versions/selection.md#framework-dependent-apps-roll-forward).</span></span>

<span data-ttu-id="aa613-179">对于 .NET Core 2.2 及早期版本，必须使用以下开关通过 `dotnet publish` 命令来发布 FDE：</span><span class="sxs-lookup"><span data-stu-id="aa613-179">For .NET Core 2.2 and earlier, you must use the following switches with the `dotnet publish` command to publish an FDE:</span></span>

- <span data-ttu-id="aa613-180">`-r <RID>` 此开关使用标识符 (RID) 来指定目标平台。</span><span class="sxs-lookup"><span data-stu-id="aa613-180">`-r <RID>` This switch uses an identifier (RID) to specify the target platform.</span></span> <span data-ttu-id="aa613-181">有关运行时标识符的详细信息，请参阅[运行时标识符 (RID) 目录](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="aa613-181">For a list of runtime identifiers, see [Runtime Identifier (RID) catalog](../rid-catalog.md).</span></span>

- <span data-ttu-id="aa613-182">`--self-contained false` 此开关告知 .NET Core SDK 创建可执行文件作为 FDE。</span><span class="sxs-lookup"><span data-stu-id="aa613-182">`--self-contained false` This switch tells the .NET Core SDK to create an executable as an FDE.</span></span>

<span data-ttu-id="aa613-183">每次使用 `-r` 开关时，输出文件路都将更改为：`./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`</span><span class="sxs-lookup"><span data-stu-id="aa613-183">Whenever you use the `-r` switch, the output folder path changes to: `./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`</span></span>

<span data-ttu-id="aa613-184">如果使用[示例应用](#sample-app)，请运行 `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false`。</span><span class="sxs-lookup"><span data-stu-id="aa613-184">If you use the [example app](#sample-app), run `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false`.</span></span> <span data-ttu-id="aa613-185">此命令将创建以下可执行文件：`./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`</span><span class="sxs-lookup"><span data-stu-id="aa613-185">This command creates the following executable: `./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="aa613-186">可以通过启用全局固定模式来降低部署的总大小  。</span><span class="sxs-lookup"><span data-stu-id="aa613-186">You can reduce the total size of your deployment by enabling **globalization invariant mode**.</span></span> <span data-ttu-id="aa613-187">此模式适用于不具有全局意识且可以使用[固定区域性](xref:System.Globalization.CultureInfo.InvariantCulture)的格式约定、大小写约定以及字符串比较和排序顺序的应用程序。</span><span class="sxs-lookup"><span data-stu-id="aa613-187">This mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span> <span data-ttu-id="aa613-188">有关全局固定模式及其启用方式的详细信息，请参阅 [.NET Core 全局固定模式](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="aa613-188">For more information about **globalization invariant mode** and how to enable it, see [.NET Core Globalization Invariant Mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

## <a name="self-contained-deployment"></a><span data-ttu-id="aa613-189">独立部署</span><span class="sxs-lookup"><span data-stu-id="aa613-189">Self-contained deployment</span></span>

<span data-ttu-id="aa613-190">发布独立部署 (SCD) 时，.NET Core SDK 创建特定于平台的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="aa613-190">When you publish a self-contained deployment (SCD), the .NET Core SDK creates a platform-specific executable.</span></span> <span data-ttu-id="aa613-191">发布 SCD 时会包括运行应用所需的所有 .NET Core 文件，但不包含 [.NET Core 的本机依赖项](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)。</span><span class="sxs-lookup"><span data-stu-id="aa613-191">Publishing an SCD includes all required .NET Core files to run your app but it doesn't include the [native dependencies of .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span> <span data-ttu-id="aa613-192">这些依赖项必须在应用运行前存在于系统中。</span><span class="sxs-lookup"><span data-stu-id="aa613-192">These dependencies must be present on the system before the app runs.</span></span>

<span data-ttu-id="aa613-193">发布 SCD 会创建一个不会前滚到最新可用 .NET Core 安全修补程序的应用。</span><span class="sxs-lookup"><span data-stu-id="aa613-193">Publishing an SCD creates an app that doesn't roll forward to the latest available .NET Core security patch.</span></span> <span data-ttu-id="aa613-194">有关编译时的版本绑定的详细信息，请参阅[选择要使用的 .NET Core 版本](../versions/selection.md#self-contained-deployments-include-the-selected-runtime)。</span><span class="sxs-lookup"><span data-stu-id="aa613-194">For more information on version binding at compile time, see [Select the .NET Core version to use](../versions/selection.md#self-contained-deployments-include-the-selected-runtime).</span></span>

<span data-ttu-id="aa613-195">必须通过 `dotnet publish` 命令使用以下开关来发布 SCD：</span><span class="sxs-lookup"><span data-stu-id="aa613-195">You must use the following switches with the `dotnet publish` command to publish an SCD:</span></span>

- <span data-ttu-id="aa613-196">`-r <RID>` 此开关使用标识符 (RID) 来指定目标平台。</span><span class="sxs-lookup"><span data-stu-id="aa613-196">`-r <RID>` This switch uses an identifier (RID) to specify the target platform.</span></span> <span data-ttu-id="aa613-197">有关运行时标识符的详细信息，请参阅[运行时标识符 (RID) 目录](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="aa613-197">For a list of runtime identifiers, see [Runtime Identifier (RID) catalog](../rid-catalog.md).</span></span>

- <span data-ttu-id="aa613-198">`--self-contained true` 此开关告知 .NET Core SDK 创建可执行文件作为 SCD。</span><span class="sxs-lookup"><span data-stu-id="aa613-198">`--self-contained true` This switch tells the .NET Core SDK to create an executable as an SCD.</span></span>

> [!NOTE]
> <span data-ttu-id="aa613-199">可以通过启用全局固定模式来降低部署的总大小  。</span><span class="sxs-lookup"><span data-stu-id="aa613-199">You can reduce the total size of your deployment by enabling **globalization invariant mode**.</span></span> <span data-ttu-id="aa613-200">此模式适用于不具有全局意识且可以使用[固定区域性](xref:System.Globalization.CultureInfo.InvariantCulture)的格式约定、大小写约定以及字符串比较和排序顺序的应用程序。</span><span class="sxs-lookup"><span data-stu-id="aa613-200">This mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span> <span data-ttu-id="aa613-201">有关全局固定模式及其启用方式的详细信息，请参阅 [.NET Core 全局固定模式](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="aa613-201">For more information about **globalization invariant mode** and how to enable it, see [.NET Core Globalization Invariant Mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aa613-202">请参阅</span><span class="sxs-lookup"><span data-stu-id="aa613-202">See also</span></span>

- [<span data-ttu-id="aa613-203">.NET Core 应用程序部署概述</span><span class="sxs-lookup"><span data-stu-id="aa613-203">.NET Core Application Deployment Overview</span></span>](index.md)
- [<span data-ttu-id="aa613-204">.NET Core 运行时标识符 (RID) 目录</span><span class="sxs-lookup"><span data-stu-id="aa613-204">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
