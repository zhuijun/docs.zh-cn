---
title: .NET Core 项目 SDK 概述
titleSuffix: ''
description: 了解 .NET Core 项目 SDK。
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 67dede3caabd2967adca22e7563376c761829655
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144234"
---
# <a name="net-core-project-sdks"></a><span data-ttu-id="a0ab0-103">.NET Core 项目 SDK</span><span class="sxs-lookup"><span data-stu-id="a0ab0-103">.NET Core project SDKs</span></span>

<span data-ttu-id="a0ab0-104">.NET Core 项目与软件开发工具包 (SDK) 关联。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-104">.NET Core projects are associated with a software development kit (SDK).</span></span> <span data-ttu-id="a0ab0-105">每个项目 SDK 都是一组 MSBuild [目标](/visualstudio/msbuild/msbuild-targets)和相关的[任务](/visualstudio/msbuild/msbuild-tasks)，它们负责编译、打包和发布代码。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-105">Each *project SDK* is a set of MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and associated [tasks](/visualstudio/msbuild/msbuild-tasks) that are responsible for compiling, packing, and publishing code.</span></span> <span data-ttu-id="a0ab0-106">引用项目 SDK 的项目有时称为“SDK 样式的项目”。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-106">A project that references a project SDK is sometimes referred to as an *SDK-style project*.</span></span>

## <a name="available-sdks"></a><span data-ttu-id="a0ab0-107">可用的 SDK</span><span class="sxs-lookup"><span data-stu-id="a0ab0-107">Available SDKs</span></span>

<span data-ttu-id="a0ab0-108">.NET Core 可使用以下 SDK：</span><span class="sxs-lookup"><span data-stu-id="a0ab0-108">The following SDKs are available for .NET Core:</span></span>

| <span data-ttu-id="a0ab0-109">Id</span><span class="sxs-lookup"><span data-stu-id="a0ab0-109">ID</span></span> | <span data-ttu-id="a0ab0-110">描述</span><span class="sxs-lookup"><span data-stu-id="a0ab0-110">Description</span></span> | <span data-ttu-id="a0ab0-111">存储库</span><span class="sxs-lookup"><span data-stu-id="a0ab0-111">Repo</span></span>|
| - | - | - |
| `Microsoft.NET.Sdk` | <span data-ttu-id="a0ab0-112">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="a0ab0-112">The .NET Core SDK</span></span> | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | <span data-ttu-id="a0ab0-113">.NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span><span class="sxs-lookup"><span data-stu-id="a0ab0-113">The .NET Core [Web SDK](/aspnet/core/razor-pages/web-sdk)</span></span> | <https://github.com/aspnet/websdk> |
| `Microsoft.NET.Sdk.Razor` | <span data-ttu-id="a0ab0-114">.NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span><span class="sxs-lookup"><span data-stu-id="a0ab0-114">The .NET Core [Razor SDK](/aspnet/core/razor-pages/sdk)</span></span> |
| `Microsoft.NET.Sdk.Worker` | <span data-ttu-id="a0ab0-115">.NET Core 辅助角色服务 SDK</span><span class="sxs-lookup"><span data-stu-id="a0ab0-115">The .NET Core Worker Service SDK</span></span> |
| `Microsoft.NET.Sdk.WindowsDesktop` | <span data-ttu-id="a0ab0-116">.NET Core WinForms 和 WPF SDK</span><span class="sxs-lookup"><span data-stu-id="a0ab0-116">The .NET Core WinForms and WPF SDK</span></span> |

<span data-ttu-id="a0ab0-117">.NET Core SDK 是 .NET Core 的基本 SDK。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-117">The .NET Core SDK is the base SDK for .NET Core.</span></span> <span data-ttu-id="a0ab0-118">其他 SDK 引用 .NET Core SDK，与其他 SDK 关联的项目具有所有可用的 .NET Core SDK 属性。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-118">The other SDKs reference the .NET Core SDK, and projects that are associated with the other SDKs have all the .NET Core SDK properties available to them.</span></span> <span data-ttu-id="a0ab0-119">例如，Web SDK 依赖于 .NET Core SDK 和 Razor SDK。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-119">The Web SDK, for example, depends on both the .NET Core SDK and the Razor SDK.</span></span>

<span data-ttu-id="a0ab0-120">你还可以创建自己的 SDK，并通过 NuGet 进行分发。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-120">You can also author your own SDK that can be distributed via NuGet.</span></span>

## <a name="project-files"></a><span data-ttu-id="a0ab0-121">项目文件</span><span class="sxs-lookup"><span data-stu-id="a0ab0-121">Project files</span></span>

<span data-ttu-id="a0ab0-122">.NET Core 项目基于 [MSBuild](/visualstudio/msbuild/msbuild) 格式。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-122">.NET Core projects are based on the [MSBuild](/visualstudio/msbuild/msbuild) format.</span></span> <span data-ttu-id="a0ab0-123">具有扩展名（如用于 C# 项目的 .csproj 和用于 F# 项目的 .fsproj）的项目文件都是 XML 格式的 。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-123">Project files, which have extensions like *.csproj* for C# projects and *.fsproj* for F# projects, are in XML format.</span></span> <span data-ttu-id="a0ab0-124">MSBuild 项目文件的根元素是 [Project](/visualstudio/msbuild/project-element-msbuild) 元素。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-124">The root element of an MSBuild project file is the [Project](/visualstudio/msbuild/project-element-msbuild) element.</span></span> <span data-ttu-id="a0ab0-125">`Project` 元素有一个可选的 `Sdk` 属性，该属性指定要使用的 SDK（和版本）。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-125">The `Project` element has an optional `Sdk` attribute that specifies which SDK (and version) to use.</span></span> <span data-ttu-id="a0ab0-126">若要使用 .NET Core 工具构建你的代码，请将 `Sdk` 属性设置为[可用 SDK](#available-sdks) 表中的其中一个 ID。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-126">To use the .NET Core tools and build your code, set the `Sdk` attribute to one of the IDs in the [Available SDKs](#available-sdks) table.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

<span data-ttu-id="a0ab0-127">若要指定来自 NuGet 的 SDK，请在名称末尾包含版本，或者在 global.json 文件中指定名称和版本。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-127">To specify an SDK that comes from NuGet, include the version at the end of the name, or specify the name and version in the *global.json* file.</span></span>

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

<span data-ttu-id="a0ab0-128">另一种指定 SDK 的方法是使用顶层 [Sdk](/visualstudio/msbuild/sdk-element-msbuild) 元素：</span><span class="sxs-lookup"><span data-stu-id="a0ab0-128">Another way to specify the SDK is with the top-level [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:</span></span>

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

<span data-ttu-id="a0ab0-129">以这些方式之一引用 SDK 可以极大地简化 .NET Core 的项目文件。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-129">Referencing an SDK in one of these ways greatly simplifies project files for .NET Core.</span></span> <span data-ttu-id="a0ab0-130">在评估项目时，MSBuild 在项目文件的顶部和底部分别为 `Sdk.props` 和 `Sdk.targets` 添加隐式导入。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-130">While evaluating the project, MSBuild adds implicit imports for `Sdk.props` at the top of the project file and `Sdk.targets` at the bottom.</span></span>

```xml
<Project>
  <!-- Implicit top import -->
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />
  ...
  <!-- Implicit bottom import -->
  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

> [!TIP]
> <span data-ttu-id="a0ab0-131">在 Windows 计算机上，Sdk.props 和 Sdk.targets 文件位于 %ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk 文件夹中  。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-131">On a Windows machine, the *Sdk.props* and *Sdk.targets* files can be found in the *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk* folder.</span></span>

### <a name="preprocess-the-project-file"></a><span data-ttu-id="a0ab0-132">预处理项目文件</span><span class="sxs-lookup"><span data-stu-id="a0ab0-132">Preprocess the project file</span></span>

<span data-ttu-id="a0ab0-133">使用 `dotnet msbuild -preprocess` 命令，可以看到 MSBuild 在包含 SDK 及其目标之后所显示的完全扩展的项目。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-133">You can see the fully expanded project as MSBuild sees it after the SDK and its targets are included by using the `dotnet msbuild -preprocess` command.</span></span> <span data-ttu-id="a0ab0-134">[`dotnet msbuild`](../tools/dotnet-msbuild.md) 命令的[预处理](/visualstudio/msbuild/msbuild-command-line-reference#preprocess)开关显示导入的文件、文件源及其在生成中的参与情况，而无需实际生成项目。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-134">The [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) switch of the [`dotnet msbuild`](../tools/dotnet-msbuild.md) command shows which files are imported, their sources, and their contributions to the build without actually building the project.</span></span>

<span data-ttu-id="a0ab0-135">如果项目有多个目标框架，请将命令的结果指定为 MSBuild 属性，使其仅侧重于框架之一。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-135">If the project has multiple target frameworks, focus the results of the command on only one framework by specifying it as an MSBuild property.</span></span> <span data-ttu-id="a0ab0-136">例如：</span><span class="sxs-lookup"><span data-stu-id="a0ab0-136">For example:</span></span>

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a><span data-ttu-id="a0ab0-137">默认编译包括</span><span class="sxs-lookup"><span data-stu-id="a0ab0-137">Default compilation includes</span></span>

<span data-ttu-id="a0ab0-138">编译项、嵌入资源和 `None` 项默认包含和排除的内容在 SDK 中定义。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-138">The default includes and excludes for compile items, embedded resources, and `None` items are defined in the SDK.</span></span> <span data-ttu-id="a0ab0-139">与非 SDK .NET 框架项目不同，你无需在项目文件中指定这些项，因为默认设置涵盖了最常见的用例。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-139">Unlike non-SDK .NET Framework projects, you don't need to specify these items in your project file, because the defaults cover most common use cases.</span></span> <span data-ttu-id="a0ab0-140">这使得项目文件更小、更易于理解和手动编辑（如需要）。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-140">This makes the project file smaller and easier to understand and edit by hand, if needed.</span></span>

<span data-ttu-id="a0ab0-141">下表显示在 .NET Core SDK 中包含和排除的元素和 [glob](https://en.wikipedia.org/wiki/Glob_(programming))：</span><span class="sxs-lookup"><span data-stu-id="a0ab0-141">The following table shows which elements and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are included and excluded in the .NET Core SDK:</span></span>

| <span data-ttu-id="a0ab0-142">元素</span><span class="sxs-lookup"><span data-stu-id="a0ab0-142">Element</span></span>           | <span data-ttu-id="a0ab0-143">包含 glob</span><span class="sxs-lookup"><span data-stu-id="a0ab0-143">Include glob</span></span>                              | <span data-ttu-id="a0ab0-144">排除 glob</span><span class="sxs-lookup"><span data-stu-id="a0ab0-144">Exclude glob</span></span>                                                  | <span data-ttu-id="a0ab0-145">删除 glob</span><span class="sxs-lookup"><span data-stu-id="a0ab0-145">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| <span data-ttu-id="a0ab0-146">Compile</span><span class="sxs-lookup"><span data-stu-id="a0ab0-146">Compile</span></span>           | <span data-ttu-id="a0ab0-147">\*\*/\*.cs（或其他语言扩展名）</span><span class="sxs-lookup"><span data-stu-id="a0ab0-147">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="a0ab0-148">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="a0ab0-148">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="a0ab0-149">不可用</span><span class="sxs-lookup"><span data-stu-id="a0ab0-149">N/A</span></span>                      |
| <span data-ttu-id="a0ab0-150">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="a0ab0-150">EmbeddedResource</span></span>  | <span data-ttu-id="a0ab0-151">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="a0ab0-151">\*\*/\*.resx</span></span>                              | <span data-ttu-id="a0ab0-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="a0ab0-152">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="a0ab0-153">不可用</span><span class="sxs-lookup"><span data-stu-id="a0ab0-153">N/A</span></span>                      |
| <span data-ttu-id="a0ab0-154">None</span><span class="sxs-lookup"><span data-stu-id="a0ab0-154">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="a0ab0-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="a0ab0-155">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="a0ab0-156">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="a0ab0-156">\*\*/\*.cs; \*\*/\*.resx</span></span> |

> [!NOTE]
> <span data-ttu-id="a0ab0-157">默认情况下，由 `$(BaseOutputPath)` 和 `$(BaseIntermediateOutputPath)` MSBuild 属性表示的 `./bin` 和 `./obj` 文件夹不包含在 glob 中。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-157">The `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, are excluded from the globs by default.</span></span> <span data-ttu-id="a0ab0-158">排除由属性 `$(DefaultItemExcludes)` 表示。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-158">Excludes are represented by the property `$(DefaultItemExcludes)`.</span></span>

#### <a name="build-errors"></a><span data-ttu-id="a0ab0-159">生成错误</span><span class="sxs-lookup"><span data-stu-id="a0ab0-159">Build errors</span></span>

<span data-ttu-id="a0ab0-160">如果在项目文件中显式定义这些项中的任何项，可能会出现类似于以下内容的“NETSDK1022”生成错误：</span><span class="sxs-lookup"><span data-stu-id="a0ab0-160">If you explicitly define any of these items in your project file, you're likely to get a "NETSDK1022" build error similar to the following:</span></span>

  > <span data-ttu-id="a0ab0-161">包含重复的“编译”项。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-161">Duplicate 'Compile' items were included.</span></span> <span data-ttu-id="a0ab0-162">默认情况下，.NET SDK 包括项目目录中的“编译”项。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-162">The .NET SDK includes 'Compile' items from your project directory by default.</span></span> <span data-ttu-id="a0ab0-163">可从项目文件中删除这些项，或如果想要在项目文件中显式包括它们，则将“EnableDefaultCompileItems”属性设为“false”。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-163">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

  > <span data-ttu-id="a0ab0-164">包含重复的“EmbeddedResource”项。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-164">Duplicate 'EmbeddedResource' items were included.</span></span> <span data-ttu-id="a0ab0-165">默认情况下，.NET SDK 包括项目目录中的“EmbeddedResource”项。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-165">The .NET SDK includes 'EmbeddedResource' items from your project directory by default.</span></span> <span data-ttu-id="a0ab0-166">可从项目文件中删除这些项，或如果想要在项目文件中显式包括它们，则将“EnableDefaultEmbeddedResourceItems”属性设为“false”。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-166">You can either remove these items from your project file, or set the 'EnableDefaultEmbeddedResourceItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="a0ab0-167">若要解决此错误，请执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="a0ab0-167">To resolve the errors, do one of the following:</span></span>

- <span data-ttu-id="a0ab0-168">删除与上表中列出的隐式项匹配的显式 `Compile`、`EmbeddedResource` 或 `None` 项。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-168">Remove the explicit `Compile`, `EmbeddedResource`, or `None` items that match the implicit ones listed on the previous table.</span></span>

- <span data-ttu-id="a0ab0-169">若要禁用所有隐式文件包含，请将 `EnableDefaultItems` 属性设置为 `false`：</span><span class="sxs-lookup"><span data-stu-id="a0ab0-169">Set the `EnableDefaultItems` property to `false` to disable all implicit file inclusion:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="a0ab0-170">若要指定某些文件通过应用发布，仍可以使用相应的已知 MSBuild 机制来实现（例如 `Content` 元素）。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-170">If you want to specify files to be published with your app, you can still use the known MSBuild mechanisms for that, for example, the `Content` element.</span></span>

- <span data-ttu-id="a0ab0-171">将 `EnableDefaultCompileItems`、`EnableDefaultEmbeddedResourceItems` 或 `EnableDefaultNoneItems` 属性设置为 `false`，以选择性地仅禁用 `Compile`、`EmbeddedResource` 或 `None` glob：</span><span class="sxs-lookup"><span data-stu-id="a0ab0-171">Selectively disable only `Compile`, `EmbeddedResource`, or `None` globs by setting the `EnableDefaultCompileItems`, `EnableDefaultEmbeddedResourceItems`, or `EnableDefaultNoneItems` property to `false`:</span></span>

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  <span data-ttu-id="a0ab0-172">如果仅禁用 `Compile` glob，则 Visual Studio 中的解决方案资源管理器仍将 \*.cs 项显示为项目的一部分，并作为 `None` 项包含在内。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-172">If you only disable `Compile` globs, Solution Explorer in Visual Studio still shows \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="a0ab0-173">若要禁用隐式 `None` glob，请将 `EnableDefaultNoneItems` 也设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-173">To disable the implicit `None` glob, set `EnableDefaultNoneItems` to `false` too.</span></span>

## <a name="customize-the-build"></a><span data-ttu-id="a0ab0-174">自定义生成</span><span class="sxs-lookup"><span data-stu-id="a0ab0-174">Customize the build</span></span>

<span data-ttu-id="a0ab0-175">可以通过多种方式[自定义生成](/visualstudio/msbuild/customize-your-build)。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-175">There are various ways to [customize a build](/visualstudio/msbuild/customize-your-build).</span></span> <span data-ttu-id="a0ab0-176">建议通过将属性作为参数传递给 [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) 或 [dotnet](../tools/index.md) 命令来重写该属性。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-176">You may want to override a property by passing it as an argument to an [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) or [dotnet](../tools/index.md) command.</span></span> <span data-ttu-id="a0ab0-177">还可以将属性添加到项目文件或 Directory.Build.props 文件中。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-177">You can also add the property to the project file or to a *Directory.Build.props* file.</span></span> <span data-ttu-id="a0ab0-178">有关 .NET Core 项目的有用属性列表，请参见 [.NET Core SDK 项目的 MSBuild 参考](msbuild-props.md)。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-178">For a list of useful properties for .NET Core projects, see [MSBuild reference for .NET Core SDK projects](msbuild-props.md).</span></span>

### <a name="custom-targets"></a><span data-ttu-id="a0ab0-179">自定义目标</span><span class="sxs-lookup"><span data-stu-id="a0ab0-179">Custom targets</span></span>

<span data-ttu-id="a0ab0-180">.NET Core 项目可以打包自定义的 MSBuild 目标和属性，以供使用该包的项目使用。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-180">.NET Core projects can package custom MSBuild targets and properties for use by projects that consume the package.</span></span> <span data-ttu-id="a0ab0-181">如果要执行以下操作，请使用此类型的可扩展性：</span><span class="sxs-lookup"><span data-stu-id="a0ab0-181">Use this type of extensibility when you want to:</span></span>

- <span data-ttu-id="a0ab0-182">扩展生成过程。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-182">Extend the build process.</span></span>
- <span data-ttu-id="a0ab0-183">访问生成过程的工件，如生成的文件。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-183">Access artifacts of the build process, such as generated files.</span></span>
- <span data-ttu-id="a0ab0-184">检查调用生成的配置。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-184">Inspect the configuration under which the build is invoked.</span></span>

<span data-ttu-id="a0ab0-185">通过在项目的生成文件夹中以 `<package_id>.targets` 或 `<package_id>.props`（例如 `Contoso.Utility.UsefulStuff.targets`）的形式放置文件，可以添加自定义生成目标或属性。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-185">You add custom build targets or properties by placing files in the form `<package_id>.targets` or `<package_id>.props` (for example, `Contoso.Utility.UsefulStuff.targets`) in the *build* folder of the project.</span></span>

<span data-ttu-id="a0ab0-186">以下 XML 是 .csproj 文件中的一个片段，该文件指示 [`dotnet pack`](../tools/dotnet-pack.md) 命令打包的内容。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-186">The following XML is a snippet from a *.csproj* file that instructs the [`dotnet pack`](../tools/dotnet-pack.md) command what to package.</span></span> <span data-ttu-id="a0ab0-187">`<ItemGroup Label="dotnet pack instructions">` 元素将目标文件放入包内的生成文件夹中。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-187">The `<ItemGroup Label="dotnet pack instructions">` element places the targets files into the *build* folder inside the package.</span></span> <span data-ttu-id="a0ab0-188">`<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` 元素将程序集和 .json 文件放入生成文件夹 。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-188">The `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` element places the assemblies and *.json* files into the *build* folder.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  ...
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  ...
  
</Project>
```

<span data-ttu-id="a0ab0-189">若要在项目中使用自定义目标，请添加指向包及其版本的 `PackageReference` 元素。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-189">To consume a custom target in your project, add a `PackageReference` element that points to the package and its version.</span></span> <span data-ttu-id="a0ab0-190">与工具不同，自定义目标包包含在消费项目的依赖项闭包中。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-190">Unlike the tools, the custom targets package is included in the consuming project's dependency closure.</span></span>

<span data-ttu-id="a0ab0-191">你可以配置自定义目标的使用方式。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-191">You can configure how to use the custom target.</span></span> <span data-ttu-id="a0ab0-192">由于它是 MSBuild 目标，因此会依赖于给定的目标并在另一个目标后运行，也可使用 `dotnet msbuild -t:<target-name>` 命令手动调用。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-192">Since it's an MSBuild target, it can depend on a given target, run after another target, or be manually invoked by using the `dotnet msbuild -t:<target-name>` command.</span></span> <span data-ttu-id="a0ab0-193">若要提供更好的用户体验，可以合并基于项目的工具和自定义目标。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-193">However, to provide a better user experience, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="a0ab0-194">在此方案中，每个项目工具接受所需的任何参数，并将其转换为执行目标所需的 [`dotnet msbuild`](../tools/dotnet-msbuild.md) 调用。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-194">In this scenario, the per-project tool accepts whatever parameters are needed and translates that into the required [`dotnet msbuild`](../tools/dotnet-msbuild.md) invocation that executes the target.</span></span> <span data-ttu-id="a0ab0-195">有关此类协同作用的示例，请访问 [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) 项目中的 [2016 年编程马拉松 MVP 峰会示例](https://github.com/dotnet/MVPSummitHackathon2016)存储库。</span><span class="sxs-lookup"><span data-stu-id="a0ab0-195">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0ab0-196">请参阅</span><span class="sxs-lookup"><span data-stu-id="a0ab0-196">See also</span></span>

- [<span data-ttu-id="a0ab0-197">安装 .NET Core</span><span class="sxs-lookup"><span data-stu-id="a0ab0-197">Install .NET Core</span></span>](../install/index.md)
- [<span data-ttu-id="a0ab0-198">如何使用 MSBuild 项目 SDK</span><span class="sxs-lookup"><span data-stu-id="a0ab0-198">How to use MSBuild project SDKs</span></span>](/visualstudio/msbuild/how-to-use-project-sdk)
- [<span data-ttu-id="a0ab0-199">使用 NuGet 打包自定义 MSBuild 目标和属性</span><span class="sxs-lookup"><span data-stu-id="a0ab0-199">Package custom MSBuild targets and props with NuGet</span></span>](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
