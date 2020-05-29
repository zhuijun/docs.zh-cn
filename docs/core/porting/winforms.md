---
title: 将 Windows 窗体应用移植到 .NET Core
description: 了解如何将 .NET Framework Windows 窗体应用程序移植到 .NET Core for Windows。
author: Thraka
ms.author: adegeo
ms.date: 01/24/2020
ms.openlocfilehash: efa73428c816eddc00c62c2275d3457c92284388
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206137"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="2826b-103">如何将 Windows 窗体桌面应用程序移植到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="2826b-103">How to port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="2826b-104">本文介绍如何将基于 Windows 窗体的桌面应用从 .NET Framework 移植到 .NET Core 3.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="2826b-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0 or later.</span></span> <span data-ttu-id="2826b-105">.NET Core 3.0 SDK 支持 Windows 窗体应用程序。</span><span class="sxs-lookup"><span data-stu-id="2826b-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="2826b-106">Windows 窗体仍是仅适用于 Windows 的框架，并且只能在 Windows 上运行。</span><span class="sxs-lookup"><span data-stu-id="2826b-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="2826b-107">示例使用 .NET Core SDK CLI 创建和管理项目。</span><span class="sxs-lookup"><span data-stu-id="2826b-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="2826b-108">本文中的各种名称用于标识迁移所用的文件类型。</span><span class="sxs-lookup"><span data-stu-id="2826b-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="2826b-109">迁移项目时，你的文件将以不同的名称命名，因此，请自行在心里将它们与下面列出的文件进行匹配：</span><span class="sxs-lookup"><span data-stu-id="2826b-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="2826b-110">文件</span><span class="sxs-lookup"><span data-stu-id="2826b-110">File</span></span> | <span data-ttu-id="2826b-111">描述</span><span class="sxs-lookup"><span data-stu-id="2826b-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="2826b-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="2826b-112">**MyApps.sln**</span></span> | <span data-ttu-id="2826b-113">解决方案文件的名称。</span><span class="sxs-lookup"><span data-stu-id="2826b-113">The name of the solution file.</span></span> |
| <span data-ttu-id="2826b-114">**MyForms.csproj**</span><span class="sxs-lookup"><span data-stu-id="2826b-114">**MyForms.csproj**</span></span> | <span data-ttu-id="2826b-115">要移植的 .NET Framework Windows 窗体项目的名称。</span><span class="sxs-lookup"><span data-stu-id="2826b-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="2826b-116">**MyFormsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="2826b-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="2826b-117">创建的新 .NET Core 项目的名称。</span><span class="sxs-lookup"><span data-stu-id="2826b-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="2826b-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="2826b-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="2826b-119">.NET Core Windows 窗体应用程序的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="2826b-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="2826b-120">先决条件</span><span class="sxs-lookup"><span data-stu-id="2826b-120">Prerequisites</span></span>

- <span data-ttu-id="2826b-121">适用于要执行的任何设计器工作的 [Visual Studio 2019 16.5 预览版 1](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&ch=pre&rel=16) 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="2826b-121">[Visual Studio 2019 16.5 Preview 1](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&ch=pre&rel=16) or later for any designer work you want to do.</span></span> <span data-ttu-id="2826b-122">建议更新到最新的 [Visual Studio 预览版](https://visualstudio.microsoft.com/vs/preview/)。</span><span class="sxs-lookup"><span data-stu-id="2826b-122">We recommend to update to the latest [Preview version of Visual Studio](https://visualstudio.microsoft.com/vs/preview/).</span></span>

  <span data-ttu-id="2826b-123">安装以下 Visual Studio 工作负载：</span><span class="sxs-lookup"><span data-stu-id="2826b-123">Install the following Visual Studio workloads:</span></span>
  
  - <span data-ttu-id="2826b-124">.NET 桌面开发</span><span class="sxs-lookup"><span data-stu-id="2826b-124">.NET desktop development</span></span>
  - <span data-ttu-id="2826b-125">.NET Core 跨平台开发</span><span class="sxs-lookup"><span data-stu-id="2826b-125">.NET Core cross-platform development</span></span>

- <span data-ttu-id="2826b-126">在解决方案中顺利生成和运行的有效 Windows 窗体项目。</span><span class="sxs-lookup"><span data-stu-id="2826b-126">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="2826b-127">用 C# 编码的项目。</span><span class="sxs-lookup"><span data-stu-id="2826b-127">A project coded in C#.</span></span>

> [!NOTE]
> <span data-ttu-id="2826b-128">仅在 Visual Studio 2019 或更高版本中支持 .NET Core 3.0 项目。</span><span class="sxs-lookup"><span data-stu-id="2826b-128">.NET Core 3.0 projects are only supported in **Visual Studio 2019** or a later version.</span></span> <span data-ttu-id="2826b-129">从 Visual Studio 2019 版本 16.5 预览版 1 开始，还支持 .NET Core Windows 窗体设计器。</span><span class="sxs-lookup"><span data-stu-id="2826b-129">Starting with **Visual Studio 2019 version 16.5 Preview 1**, the .NET Core Windows Forms designer is also supported.</span></span>
>
> <span data-ttu-id="2826b-130">若要启用该设计器，请转到“工具” > “选项” > “环境” > “预览功能”，然后选择“将预览版 Windows 窗体设计器用于 .NET Core 应用”选项。</span><span class="sxs-lookup"><span data-stu-id="2826b-130">To enable the designer, go to **Tools** > **Options** > **Environment** > **Preview Features** and select the **Use the preview Windows Forms designer for .NET Core apps** option.</span></span>

### <a name="consider"></a><span data-ttu-id="2826b-131">考虑</span><span class="sxs-lookup"><span data-stu-id="2826b-131">Consider</span></span>

<span data-ttu-id="2826b-132">移植 .NET Framework Windows 窗体应用程序时，必须考虑以下几个事项。</span><span class="sxs-lookup"><span data-stu-id="2826b-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="2826b-133">检查应用程序是否适合迁移。</span><span class="sxs-lookup"><span data-stu-id="2826b-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="2826b-134">使用 [.NET 可移植性分析器](../../standard/analyzers/portability-analyzer.md)确定项目将会迁移到 .NET Core 3.0。</span><span class="sxs-lookup"><span data-stu-id="2826b-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="2826b-135">如果项目存在 .NET Core 3.0 相关问题，分析器可帮助你识别这些问题。</span><span class="sxs-lookup"><span data-stu-id="2826b-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="2826b-136">使用的是不同版本的 Windows 窗体。</span><span class="sxs-lookup"><span data-stu-id="2826b-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="2826b-137">发布 .NET Core 3.0 预览版 1 时，Windows 窗体在 GitHub 上公布了开放源代码。</span><span class="sxs-lookup"><span data-stu-id="2826b-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open source on GitHub.</span></span> <span data-ttu-id="2826b-138">.NET Core Windows 窗体的代码是 .NET Framework Windows 窗体基本代码的一个分支。</span><span class="sxs-lookup"><span data-stu-id="2826b-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms codebase.</span></span> <span data-ttu-id="2826b-139">可能存在一些差异导致应用程序无法移植。</span><span class="sxs-lookup"><span data-stu-id="2826b-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="2826b-140">使用 [Windows 兼容包][compat-pack]可有助于进行迁移。</span><span class="sxs-lookup"><span data-stu-id="2826b-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="2826b-141">某些 API 可在 .NET Framework 中使用，但不可用于 .NET Core 3.0。</span><span class="sxs-lookup"><span data-stu-id="2826b-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="2826b-142">[Windows 兼容包][compat-pack]增加了很多这些 API，有助于使 Windows 窗体应用与 .NET Core 兼容。</span><span class="sxs-lookup"><span data-stu-id="2826b-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="2826b-143">更新项目使用的 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="2826b-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="2826b-144">在执行任何迁移之前使用最新版 NuGet 包始终是一个不错的做法。</span><span class="sxs-lookup"><span data-stu-id="2826b-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="2826b-145">如果应用程序引用任何 NuGet 包，请将它们更新到最新版本。</span><span class="sxs-lookup"><span data-stu-id="2826b-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="2826b-146">确保成功生成应用程序。</span><span class="sxs-lookup"><span data-stu-id="2826b-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="2826b-147">升级后，如果存在任何包错误，请将包降级到不会破坏代码的最新版本。</span><span class="sxs-lookup"><span data-stu-id="2826b-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="2826b-148">创建新的 SDK 项目</span><span class="sxs-lookup"><span data-stu-id="2826b-148">Create a new SDK project</span></span>

<span data-ttu-id="2826b-149">创建的新 .NET Core 3.0 项目必须位于不同于 .NET Framework 项目的目录中。</span><span class="sxs-lookup"><span data-stu-id="2826b-149">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="2826b-150">如果它们位于同一目录中，可能会与 obj 目录中生成的文件发生冲突。</span><span class="sxs-lookup"><span data-stu-id="2826b-150">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="2826b-151">本例中，我们将在 SolutionFolder 目录中创建一个名为 MyFormsAppCore 的目录 ：</span><span class="sxs-lookup"><span data-stu-id="2826b-151">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="2826b-152">接下来，需要在 MyFormsAppCore 目录中创建 MyFormsCore.csproj 项目 。</span><span class="sxs-lookup"><span data-stu-id="2826b-152">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="2826b-153">可以使用所选的文本编辑器手动创建此文件。</span><span class="sxs-lookup"><span data-stu-id="2826b-153">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="2826b-154">粘贴以下 XML：</span><span class="sxs-lookup"><span data-stu-id="2826b-154">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="2826b-155">如果不想手动创建项目文件，可以使用 Visual Studio 或 .NET Core SDK 生成项目。</span><span class="sxs-lookup"><span data-stu-id="2826b-155">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="2826b-156">但是，必须删除项目模板生成的所有其他文件（项目文件除外）。</span><span class="sxs-lookup"><span data-stu-id="2826b-156">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="2826b-157">若要使用 SDK，请从 SolutionFolder 目录运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="2826b-157">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="2826b-158">创建 MyFormsCore.csproj 后，目录结构应如下所示：</span><span class="sxs-lookup"><span data-stu-id="2826b-158">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="2826b-159">使用 Visual Studio 或 SolutionFolder 目录中的 .NET Core CLI 将 MyFormsCore.csproj 项目添加到 MyApps.sln  ：</span><span class="sxs-lookup"><span data-stu-id="2826b-159">Add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="2826b-160">修复程序集信息生成</span><span class="sxs-lookup"><span data-stu-id="2826b-160">Fix assembly info generation</span></span>

<span data-ttu-id="2826b-161">使用 .NET Framework 创建的 Windows 窗体项目包含一个 `AssemblyInfo.cs` 文件，该文件包含诸如要生成的程序集的版本等程序集特性。</span><span class="sxs-lookup"><span data-stu-id="2826b-161">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="2826b-162">SDK 样式的项目会根据 SDK 项目文件自动生成此信息。</span><span class="sxs-lookup"><span data-stu-id="2826b-162">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="2826b-163">同时具有两种类型的“程序集信息”时，会产生冲突。</span><span class="sxs-lookup"><span data-stu-id="2826b-163">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="2826b-164">通过禁用自动生成可以解决此问题，这会强制项目使用现有的 `AssemblyInfo.cs` 文件。</span><span class="sxs-lookup"><span data-stu-id="2826b-164">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="2826b-165">若要添加到主 `<PropertyGroup>` 节点，有三个设置项。</span><span class="sxs-lookup"><span data-stu-id="2826b-165">There are three settings to add to the main `<PropertyGroup>` node.</span></span>

- <span data-ttu-id="2826b-166">**GenerateAssemblyInfo**</span><span class="sxs-lookup"><span data-stu-id="2826b-166">**GenerateAssemblyInfo**</span></span>\
<span data-ttu-id="2826b-167">将此属性设置为 `false` 时，它不会生成程序集特性。</span><span class="sxs-lookup"><span data-stu-id="2826b-167">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="2826b-168">这可以避免与 .NET Framework 项目中的现有 `AssemblyInfo.cs` 文件冲突。</span><span class="sxs-lookup"><span data-stu-id="2826b-168">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="2826b-169">**AssemblyName**</span><span class="sxs-lookup"><span data-stu-id="2826b-169">**AssemblyName**</span></span>\
<span data-ttu-id="2826b-170">此属性的值是编译时创建的输出二进制。</span><span class="sxs-lookup"><span data-stu-id="2826b-170">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="2826b-171">该名称不需要添加扩展名。</span><span class="sxs-lookup"><span data-stu-id="2826b-171">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="2826b-172">例如，使用 `MyCoreApp` 生成 `MyCoreApp.exe`。</span><span class="sxs-lookup"><span data-stu-id="2826b-172">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="2826b-173">**RootNamespace**</span><span class="sxs-lookup"><span data-stu-id="2826b-173">**RootNamespace**</span></span>\
<span data-ttu-id="2826b-174">项目使用的默认命名空间。</span><span class="sxs-lookup"><span data-stu-id="2826b-174">The default namespace used by your project.</span></span> <span data-ttu-id="2826b-175">它应该与 .NET Framework 项目的默认命名空间匹配。</span><span class="sxs-lookup"><span data-stu-id="2826b-175">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="2826b-176">将这三个元素添加到 `MyFormsCore.csproj` 文件中的 `<PropertyGroup>` 节点：</span><span class="sxs-lookup"><span data-stu-id="2826b-176">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>WindowsFormsApp1</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a><span data-ttu-id="2826b-177">添加源代码</span><span class="sxs-lookup"><span data-stu-id="2826b-177">Add source code</span></span>

<span data-ttu-id="2826b-178">现在，MyFormsCore.csproj 项目不编译任何代码。</span><span class="sxs-lookup"><span data-stu-id="2826b-178">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="2826b-179">默认情况下，.NET Core 项目会自动包含当前目录和所有子目录中的所有源代码。</span><span class="sxs-lookup"><span data-stu-id="2826b-179">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="2826b-180">必须使用相对路径配置项目以包含 .NET Framework 项目中的代码。</span><span class="sxs-lookup"><span data-stu-id="2826b-180">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="2826b-181">如果 .NET Framework 项目使用了 .resx 文件作为窗体的图标和资源，则还需要包含这些文件。</span><span class="sxs-lookup"><span data-stu-id="2826b-181">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span>

<span data-ttu-id="2826b-182">将以下 `<ItemGroup>` 节点添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="2826b-182">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="2826b-183">每个语句都包含一个文件 glob 模式，其中包含子目录。</span><span class="sxs-lookup"><span data-stu-id="2826b-183">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="2826b-184">或者，可以为 .NET Framework 项目中的每个文件创建一个 `<Compile>` 或 `<EmbeddedResource>` 条目。</span><span class="sxs-lookup"><span data-stu-id="2826b-184">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="2826b-185">添加 NuGet 包</span><span class="sxs-lookup"><span data-stu-id="2826b-185">Add NuGet packages</span></span>

<span data-ttu-id="2826b-186">将 .NET Framework 项目引用的每个 NuGet 包添加到 .NET Core 项目。</span><span class="sxs-lookup"><span data-stu-id="2826b-186">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span>

<span data-ttu-id="2826b-187">很可能你的 .NET Framework Windows 窗体应用程序有一个 packages.config 文件，其中包含项目引用的所有 NuGet 包的列表。</span><span class="sxs-lookup"><span data-stu-id="2826b-187">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="2826b-188">可以查看此列表以确定要添加到 .NET Core 项目的 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="2826b-188">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="2826b-189">例如，如果 .NET Framework 项目引用了 `MetroFramework`、`MetroFramework.Design` 和 `MetroFramework.Fonts` NuGet 包，则使用 Visual Studio 或 SolutionFolder 目录中的 .NET Core CLI 将每个包添加到项目中：</span><span class="sxs-lookup"><span data-stu-id="2826b-189">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="2826b-190">之前的命令会将以下 NuGet 引用添加到 MyFormsCore.csproj 项目：</span><span class="sxs-lookup"><span data-stu-id="2826b-190">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="2826b-191">移植控件库</span><span class="sxs-lookup"><span data-stu-id="2826b-191">Port control libraries</span></span>

<span data-ttu-id="2826b-192">如果要移植 Windows 窗体控件库项目，操作说明与移植 .NET Framework Windows 窗体应用程序项目相同，只不过在一些设置上存在差异。</span><span class="sxs-lookup"><span data-stu-id="2826b-192">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="2826b-193">并且此操作中不编译到可执行文件，而是编译到库。</span><span class="sxs-lookup"><span data-stu-id="2826b-193">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="2826b-194">除了包含源代码的文件 glob 的路径之外，可执行项目和库项目之间的区别也很小。</span><span class="sxs-lookup"><span data-stu-id="2826b-194">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="2826b-195">借助上一步的示例，详细介绍正在处理的项目和文件。</span><span class="sxs-lookup"><span data-stu-id="2826b-195">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="2826b-196">文件</span><span class="sxs-lookup"><span data-stu-id="2826b-196">File</span></span> | <span data-ttu-id="2826b-197">描述</span><span class="sxs-lookup"><span data-stu-id="2826b-197">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="2826b-198">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="2826b-198">**MyApps.sln**</span></span> | <span data-ttu-id="2826b-199">解决方案文件的名称。</span><span class="sxs-lookup"><span data-stu-id="2826b-199">The name of the solution file.</span></span> |
| <span data-ttu-id="2826b-200">**MyControls.csproj**</span><span class="sxs-lookup"><span data-stu-id="2826b-200">**MyControls.csproj**</span></span> | <span data-ttu-id="2826b-201">要移植的 .NET Framework Windows 窗体控件项目的名称。</span><span class="sxs-lookup"><span data-stu-id="2826b-201">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="2826b-202">**MyControlsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="2826b-202">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="2826b-203">创建的新 .NET Core 库项目的名称。</span><span class="sxs-lookup"><span data-stu-id="2826b-203">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="2826b-204">**MyCoreControls.dll**</span><span class="sxs-lookup"><span data-stu-id="2826b-204">**MyCoreControls.dll**</span></span> | <span data-ttu-id="2826b-205">.NET Core Windows 窗体控件库。</span><span class="sxs-lookup"><span data-stu-id="2826b-205">The .NET Core Windows Forms Controls library.</span></span> |

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
├───MyFormsAppCore
│   └───MyFormsCore.csproj
│
├───MyFormsControls
│   └───MyControls.csproj
└───MyFormsControlsCore
    └───MyControlsCore.csproj   <--- New project for core controls
```

<span data-ttu-id="2826b-206">请考虑 `MyControlsCore.csproj` 项目与先前创建的 `MyFormsCore.csproj` 项目之间的差异。</span><span class="sxs-lookup"><span data-stu-id="2826b-206">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

```diff
 <Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

   <PropertyGroup>
-    <OutputType>WinExe</OutputType>
     <TargetFramework>netcoreapp3.0</TargetFramework>
     <UseWindowsForms>true</UseWindowsForms>

     <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
-    <AssemblyName>MyCoreApp</AssemblyName>
-    <RootNamespace>WindowsFormsApp1</RootNamespace>
+    <AssemblyName>MyControlsCore</AssemblyName>
+    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
   </PropertyGroup>

   <ItemGroup>
-    <Compile Include="..\MyFormsApp\**\*.cs" />
-    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
+    <Compile Include="..\MyFormsControls\**\*.cs" />
+    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
   </ItemGroup>

 </Project>
```

<span data-ttu-id="2826b-207">以下是 .NET Core Windows 窗体控件库项目文件的示例：</span><span class="sxs-lookup"><span data-stu-id="2826b-207">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>

    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreControls</AssemblyName>
    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
  </PropertyGroup>

  <ItemGroup>
    <Compile Include="..\MyFormsControls\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="2826b-208">如你所见，`<OutputType>` 节点已被删除，默认使编译器生成库而不是可执行文件。</span><span class="sxs-lookup"><span data-stu-id="2826b-208">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="2826b-209">`<AssemblyName>` 和 `<RootNamespace>` 已更改。</span><span class="sxs-lookup"><span data-stu-id="2826b-209">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="2826b-210">具体来说，`<RootNamespace>` 应匹配正在移植的 Windows 窗体控件库的命名空间。</span><span class="sxs-lookup"><span data-stu-id="2826b-210">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="2826b-211">最后，`<Compile>` 和 `<EmbeddedResource>` 节点已调整为指向要移植的 Windows 窗体控件库的文件夹。</span><span class="sxs-lookup"><span data-stu-id="2826b-211">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="2826b-212">接下来，在主要的 .NET Core MyFormsCore.csproj 项目中，添加对新 .NET Core Windows 窗体控件库的引用。</span><span class="sxs-lookup"><span data-stu-id="2826b-212">Next, in the main .NET Core **MyFormsCore.csproj** project, add a reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="2826b-213">使用 Visual Studio 或 .NET Core CLI 从 SolutionFolder 目录添加引用：</span><span class="sxs-lookup"><span data-stu-id="2826b-213">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

<span data-ttu-id="2826b-214">上一个命令将以下内容添加到 MyFormsCore.csproj 项目中：</span><span class="sxs-lookup"><span data-stu-id="2826b-214">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="compilation-problems"></a><span data-ttu-id="2826b-215">编译问题</span><span class="sxs-lookup"><span data-stu-id="2826b-215">Compilation problems</span></span>

<span data-ttu-id="2826b-216">如果在编译项目时遇到问题，可能是由于正在使用的一些仅适用于 Windows 的 API 在 .NET Framework 中可用，但在 .NET Core 中不可用。</span><span class="sxs-lookup"><span data-stu-id="2826b-216">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="2826b-217">可以尝试将 [Windows 兼容包][compat-pack] NuGet 包添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="2826b-217">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="2826b-218">此包仅在 Windows 上运行，为 .NET Core 和 .NET Standard 项目添加了大约 20,000 个 Windows API。</span><span class="sxs-lookup"><span data-stu-id="2826b-218">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="2826b-219">上一个命令将以下内容添加到 MyFormsCore.csproj 项目中：</span><span class="sxs-lookup"><span data-stu-id="2826b-219">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="3.1.0" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="2826b-220">Windows Forms Designer — Windows 窗体设计器</span><span class="sxs-lookup"><span data-stu-id="2826b-220">Windows Forms Designer</span></span>

<span data-ttu-id="2826b-221">如本文所述，Visual Studio 2019 仅支持 .NET Framework 项目中的窗体设计器。</span><span class="sxs-lookup"><span data-stu-id="2826b-221">As detailed in this article, Visual Studio 2019 only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="2826b-222">通过创建并行 .NET Core 项目，可以在使用 .NET Framework 项目设计窗体时通过 .NET Core 测试项目。</span><span class="sxs-lookup"><span data-stu-id="2826b-222">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="2826b-223">解决方案文件包括 .NET Framework 和 .NET Core 项目。</span><span class="sxs-lookup"><span data-stu-id="2826b-223">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="2826b-224">在 .NET Framework 项目中添加和设计窗体和控件，并且根据添加到 .NET Core 项目的文件 glob 模式，任何新的或更改的文件将自动包含在 .NET Core 项目中。</span><span class="sxs-lookup"><span data-stu-id="2826b-224">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="2826b-225">一旦 Visual Studio 2019 支持 Windows 窗体设计器，就可以将 .NET Core 项目文件的内容复制/粘贴到 .NET Framework 项目文件中。</span><span class="sxs-lookup"><span data-stu-id="2826b-225">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="2826b-226">然后删除使用 `<Source>` 和 `<EmbeddedResource>` 项添加的文件 glob 模式。</span><span class="sxs-lookup"><span data-stu-id="2826b-226">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="2826b-227">修复由应用程序使用的任何项目引用的路径。</span><span class="sxs-lookup"><span data-stu-id="2826b-227">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="2826b-228">这可以有效地将 .NET Framework 项目升级到 .NET Core 项目。</span><span class="sxs-lookup"><span data-stu-id="2826b-228">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2826b-229">后续步骤</span><span class="sxs-lookup"><span data-stu-id="2826b-229">Next steps</span></span>

- <span data-ttu-id="2826b-230">了解[从 .NET Framework 到 .NET Core 的中断性变更](../compatibility/fx-core.md)。</span><span class="sxs-lookup"><span data-stu-id="2826b-230">Learn about [breaking changes from .NET Framework to .NET Core](../compatibility/fx-core.md).</span></span>
- <span data-ttu-id="2826b-231">详细了解 [Windows 兼容包][compat-pack]。</span><span class="sxs-lookup"><span data-stu-id="2826b-231">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
- <span data-ttu-id="2826b-232">观看将 .NET Framework Windows 窗体项目移植到 .NET Core 的[视频](https://www.youtube.com/watch?v=upVQEUc_KwU)。</span><span class="sxs-lookup"><span data-stu-id="2826b-232">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
