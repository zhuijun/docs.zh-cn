---
title: Microsoft.NET.Sdk 的 MSBuild 属性
description: .NET Core SDK 可以理解的 MSBuild 属性和项的引用。
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: 39cbd18121d2b8659b2f5270f39624798f4ebbdc
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810516"
---
# <a name="msbuild-reference-for-net-core-sdk-projects"></a><span data-ttu-id="5c739-103">.NET Core SDK 项目的 MSBuild 引用</span><span class="sxs-lookup"><span data-stu-id="5c739-103">MSBuild reference for .NET Core SDK projects</span></span>

<span data-ttu-id="5c739-104">此页是对可用于配置 .NET Core 项目的 MSBuild 属性和项的引用。</span><span class="sxs-lookup"><span data-stu-id="5c739-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="5c739-105">此页面正在运行中，未列出 .NET Core SDK 的所有有用的 MSBuild 属性。</span><span class="sxs-lookup"><span data-stu-id="5c739-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="5c739-106">有关通用 MSBuild 属性的列表，请参阅[通用 MSBuild 属性](/visualstudio/msbuild/common-msbuild-project-properties)。</span><span class="sxs-lookup"><span data-stu-id="5c739-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="5c739-107">框架属性</span><span class="sxs-lookup"><span data-stu-id="5c739-107">Framework properties</span></span>

- [<span data-ttu-id="5c739-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="5c739-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="5c739-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="5c739-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="5c739-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="5c739-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="5c739-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="5c739-111">TargetFramework</span></span>

<span data-ttu-id="5c739-112">`TargetFramework` 属性指定应用的目标框架版本。</span><span class="sxs-lookup"><span data-stu-id="5c739-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="5c739-113">有关有效的目标框架名字对象的列表，请参阅 [SDK 样式项目中的目标框架](../../standard/frameworks.md#supported-target-framework-versions)。</span><span class="sxs-lookup"><span data-stu-id="5c739-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="5c739-114">有关详细信息，请参阅 [SDK 样式项目中的目标框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="5c739-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="5c739-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="5c739-115">TargetFrameworks</span></span>

<span data-ttu-id="5c739-116">如果希望应用面向多个平台，请使用 `TargetFrameworks` 属性。</span><span class="sxs-lookup"><span data-stu-id="5c739-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="5c739-117">有关有效的目标框架名字对象的列表，请参阅 [SDK 样式项目中的目标框架](../../standard/frameworks.md#supported-target-framework-versions)。</span><span class="sxs-lookup"><span data-stu-id="5c739-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="5c739-118">如果指定了 `TargetFramework`（单数），则忽略此属性。</span><span class="sxs-lookup"><span data-stu-id="5c739-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="5c739-119">有关详细信息，请参阅 [SDK 样式项目中的目标框架](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="5c739-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="5c739-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="5c739-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="5c739-121">此属性仅适用于使用 `netstandard1.x` 的项目。</span><span class="sxs-lookup"><span data-stu-id="5c739-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="5c739-122">它不适用于使用 `netstandard2.x` 的项目。</span><span class="sxs-lookup"><span data-stu-id="5c739-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="5c739-123">如果要指定低于元包版本的框架版本，请使用 `NetStandardImplicitPackageVersion` 属性。</span><span class="sxs-lookup"><span data-stu-id="5c739-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="5c739-124">以下示例中的项目文件以 `netstandard1.3` 为目标，但使用 `NETStandard.Library` 的 1.6.0 版本。</span><span class="sxs-lookup"><span data-stu-id="5c739-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="5c739-125">包属性</span><span class="sxs-lookup"><span data-stu-id="5c739-125">Package properties</span></span>

<span data-ttu-id="5c739-126">可以指定 `PackageId`、`PackageVersion`、`PackageIcon`、`Title` 和 `Description` 等属性来描述通过项目创建的包。</span><span class="sxs-lookup"><span data-stu-id="5c739-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="5c739-127">若要了解这些属性和其他属性，请参阅[包目标](/nuget/reference/msbuild-targets#pack-target)。</span><span class="sxs-lookup"><span data-stu-id="5c739-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a><span data-ttu-id="5c739-128">发布属性和项</span><span class="sxs-lookup"><span data-stu-id="5c739-128">Publish properties and items</span></span>

- [<span data-ttu-id="5c739-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="5c739-129">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="5c739-130">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="5c739-130">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="5c739-131">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="5c739-131">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="5c739-132">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="5c739-132">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="5c739-133">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="5c739-133">RuntimeIdentifier</span></span>

<span data-ttu-id="5c739-134">`RuntimeIdentifier` 属性可用于指定项目的单个[运行时标识符 (RID)](../rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="5c739-134">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="5c739-135">RID 支持发布独立部署。</span><span class="sxs-lookup"><span data-stu-id="5c739-135">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="5c739-136">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="5c739-136">RuntimeIdentifiers</span></span>

<span data-ttu-id="5c739-137">`RuntimeIdentifiers` 属性可用于指定项目的[运行时标识符 (RID)](../rid-catalog.md) 的列表（以分号分隔）。</span><span class="sxs-lookup"><span data-stu-id="5c739-137">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="5c739-138">如果需要为多个运行时发布，请使用此属性。</span><span class="sxs-lookup"><span data-stu-id="5c739-138">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="5c739-139">`RuntimeIdentifiers` 在还原时使用，以确保图中有适当的资产。</span><span class="sxs-lookup"><span data-stu-id="5c739-139">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="5c739-140">`RuntimeIdentifier`（单数）可以在只需要一个运行时时提供更快的生成。</span><span class="sxs-lookup"><span data-stu-id="5c739-140">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="5c739-141">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="5c739-141">TrimmerRootAssembly</span></span>

<span data-ttu-id="5c739-142">`TrimmerRootAssembly` 项允许通过[修整](../deploying/trim-self-contained.md)排除程序集。</span><span class="sxs-lookup"><span data-stu-id="5c739-142">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="5c739-143">修整是从打包的应用程序中删除运行时未使用部分的过程。</span><span class="sxs-lookup"><span data-stu-id="5c739-143">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="5c739-144">在某些情况下，修整可能会错误地删除所需的引用。</span><span class="sxs-lookup"><span data-stu-id="5c739-144">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="5c739-145">以下 XML 通过修整排除 `System.Security` 程序集。</span><span class="sxs-lookup"><span data-stu-id="5c739-145">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="5c739-146">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="5c739-146">UseAppHost</span></span>

<span data-ttu-id="5c739-147">`UseAppHost` 属性是在 .NET Core SDK 的 2.1.400 版本中引入的。</span><span class="sxs-lookup"><span data-stu-id="5c739-147">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="5c739-148">它控制是否为部署创建本机可执行文件。</span><span class="sxs-lookup"><span data-stu-id="5c739-148">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="5c739-149">自包含部署需要本机可执行文件。</span><span class="sxs-lookup"><span data-stu-id="5c739-149">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="5c739-150">在 .NET Core3.0 及更高版本中，默认情况下会创建依赖于框架的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="5c739-150">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="5c739-151">将 `UseAppHost` 属性设置为 `false` 可禁用可执行文件的生成。</span><span class="sxs-lookup"><span data-stu-id="5c739-151">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="5c739-152">有关部署的详细信息，请参阅 [.NET Core 应用程序部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5c739-152">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="5c739-153">编译属性</span><span class="sxs-lookup"><span data-stu-id="5c739-153">Compile properties</span></span>

- [<span data-ttu-id="5c739-154">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="5c739-154">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="5c739-155">LangVersion</span><span class="sxs-lookup"><span data-stu-id="5c739-155">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="5c739-156">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="5c739-156">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="5c739-157">`EmbeddedResourceUseDependentUponConvention` 属性定义了是否从与资源文件并置的源文件中的类型信息生成资源清单文件名。</span><span class="sxs-lookup"><span data-stu-id="5c739-157">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="5c739-158">例如，如果 Form1.resx 与 Form1.cs 位于同一文件夹中，并且 `EmbeddedResourceUseDependentUponConvention` 设置为 `true`，则生成的 .resources 文件将采用 Form1.cs 中定义的第一个类型的名称作为其文件名。</span><span class="sxs-lookup"><span data-stu-id="5c739-158">For example, if *Form1.resx* is in the same folder as *Form1.cs*, and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="5c739-159">例如，如果 Form1.cs 中定义的第一个类型为 `MyNamespace.Form1`，则生成的文件名为 MyNamespace.Form1.resources。</span><span class="sxs-lookup"><span data-stu-id="5c739-159">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="5c739-160">如果为 `EmbeddedResource` 项指定 `LogicalName`、`ManifestResourceName` 或 `DependentUpon` 元数据，则为该资源文件生成的清单文件名将改为基于该元数据。</span><span class="sxs-lookup"><span data-stu-id="5c739-160">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="5c739-161">默认情况下，在新的 .NET Core 项目中，此属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="5c739-161">By default, in a new .NET Core project, this property is set to `true`.</span></span> <span data-ttu-id="5c739-162">如果设置为 `false`，并且没有为项目文件中的 `EmbeddedResource` 项指定 `LogicalName`、`ManifestResourceName` 或 `DependentUpon` 元数据，则资源清单文件名将基于项目的根命名空间和 .resx 文件的相对文件路径。</span><span class="sxs-lookup"><span data-stu-id="5c739-162">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="5c739-163">有关详细信息，请参阅[资源清单文件的命名](../resources/manifest-file-names.md)。</span><span class="sxs-lookup"><span data-stu-id="5c739-163">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="5c739-164">LangVersion</span><span class="sxs-lookup"><span data-stu-id="5c739-164">LangVersion</span></span>

<span data-ttu-id="5c739-165">`LangVersion` 属性可用于指定特定的编程语言版本。</span><span class="sxs-lookup"><span data-stu-id="5c739-165">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="5c739-166">例如，如果要访问 C# 预览功能，请将 `LangVersion` 设置为 `preview`。</span><span class="sxs-lookup"><span data-stu-id="5c739-166">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="5c739-167">有关详细信息，请参阅 [C# 语言版本控制](../../csharp/language-reference/configure-language-version.md#override-a-default)。</span><span class="sxs-lookup"><span data-stu-id="5c739-167">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="code-analysis-properties"></a><span data-ttu-id="5c739-168">代码分析属性</span><span class="sxs-lookup"><span data-stu-id="5c739-168">Code analysis properties</span></span>

### <a name="analysislevel"></a><span data-ttu-id="5c739-169">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="5c739-169">AnalysisLevel</span></span>

<span data-ttu-id="5c739-170">`AnalysisLevel` 属性可指定代码分析级别。</span><span class="sxs-lookup"><span data-stu-id="5c739-170">The `AnalysisLevel` property lets you specify a code analysis level.</span></span> <span data-ttu-id="5c739-171">例如，如果要访问预览代码分析器，请将 `AnalysisLevel` 设置为 `preview`。</span><span class="sxs-lookup"><span data-stu-id="5c739-171">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span> <span data-ttu-id="5c739-172">默认值为 `latest`。</span><span class="sxs-lookup"><span data-stu-id="5c739-172">The default value is `latest`.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="5c739-173">下表显示可用的选项。</span><span class="sxs-lookup"><span data-stu-id="5c739-173">The following table shows the available options.</span></span>

| <span data-ttu-id="5c739-174">值</span><span class="sxs-lookup"><span data-stu-id="5c739-174">Value</span></span> | <span data-ttu-id="5c739-175">含义</span><span class="sxs-lookup"><span data-stu-id="5c739-175">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="5c739-176">使用已发布的最新版代码分析器。</span><span class="sxs-lookup"><span data-stu-id="5c739-176">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="5c739-177">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="5c739-177">This is the default.</span></span> |
| `preview` | <span data-ttu-id="5c739-178">使用最新的代码分析器（即使它们处于预览状态）。</span><span class="sxs-lookup"><span data-stu-id="5c739-178">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="5c739-179">即使有较新的规则可用，也会使用为 .NET 5.0 版本启用的规则集。</span><span class="sxs-lookup"><span data-stu-id="5c739-179">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="5c739-180">即使有较新的规则可用，也会使用为 .NET 5.0 版本启用的规则集。</span><span class="sxs-lookup"><span data-stu-id="5c739-180">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="5c739-181">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="5c739-181">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="5c739-182">`CodeAnalysisTreatWarningsAsErrors` 属性可配置是否应将代码分析警告视为警告并中断生成。</span><span class="sxs-lookup"><span data-stu-id="5c739-182">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code analysis warnings should be treated as warnings and break the build.</span></span> <span data-ttu-id="5c739-183">如果在生成项目时使用 `-warnaserror` 标志，则 [.NET 代码分析](../../fundamentals/productivity/code-analysis.md)警告也会被视为错误。</span><span class="sxs-lookup"><span data-stu-id="5c739-183">If you use the `-warnaserror` flag when you build your projects, [.NET code analysis](../../fundamentals/productivity/code-analysis.md) warnings are also treated as errors.</span></span> <span data-ttu-id="5c739-184">如果只想将编译器警告视为错误，则可在项目文件中将 `CodeAnalysisTreatWarningsAsErrors` MSBuild 属性设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="5c739-184">If you only want compiler warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="5c739-185">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="5c739-185">EnableNETAnalyzers</span></span>

<span data-ttu-id="5c739-186">默认情况下，为面向 .NET 5.0 或更高版本的项目启用 [.NET 代码分析](../../fundamentals/productivity/code-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="5c739-186">[.NET Code analysis](../../fundamentals/productivity/code-analysis.md) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="5c739-187">可通过将 `EnableNETAnalyzers` 属性设置为 true，来为面向 .NET 早期版本的项目启用 .NET 代码分析。</span><span class="sxs-lookup"><span data-stu-id="5c739-187">You can enable .NET code analysis for projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to true.</span></span> <span data-ttu-id="5c739-188">若要禁用任何项目中的代码分析，可将此属性设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="5c739-188">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="5c739-189">有关面向 .NET 5.0 之前的 .NET 版本的项目，启用 .NET 代码分析的另一种方法是将 [AnalysisLevel](#analysislevel) 属性设置为 `latest`。</span><span class="sxs-lookup"><span data-stu-id="5c739-189">Another way to enable .NET code analysis on projects that target .NET versions prior to .NET 5.0 is to set the [AnalysisLevel](#analysislevel) property to `latest`.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="5c739-190">运行时配置属性</span><span class="sxs-lookup"><span data-stu-id="5c739-190">Run-time configuration properties</span></span>

<span data-ttu-id="5c739-191">可以通过在应用的项目文件中指定 MSBuild 属性来配置某些运行时行为。</span><span class="sxs-lookup"><span data-stu-id="5c739-191">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="5c739-192">有关配置运行时行为的其他方法的信息，请参阅 [.NET Core 运行时配置设置](../run-time-config/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5c739-192">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="5c739-193">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="5c739-193">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="5c739-194">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="5c739-194">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="5c739-195">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="5c739-195">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="5c739-196">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="5c739-196">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="5c739-197">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="5c739-197">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="5c739-198">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="5c739-198">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="5c739-199">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="5c739-199">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="5c739-200">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="5c739-200">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="5c739-201">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="5c739-201">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="5c739-202">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="5c739-202">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="5c739-203">`ConcurrentGarbageCollection` 属性配置是否启用 [后台（并发）垃圾回收](../../standard/garbage-collection/background-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="5c739-203">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="5c739-204">将值设置为 `false` 以禁用后台垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="5c739-204">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="5c739-205">有关详细信息，请参阅[后台 GC](../run-time-config/garbage-collector.md#background-gc)。</span><span class="sxs-lookup"><span data-stu-id="5c739-205">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="5c739-206">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="5c739-206">InvariantGlobalization</span></span>

<span data-ttu-id="5c739-207">`InvariantGlobalization` 属性配置应用是否在全球化固定模式下运行，这意味着它无权访问特定于区域性的数据。</span><span class="sxs-lookup"><span data-stu-id="5c739-207">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="5c739-208">将值设置为 `true` 以在全球化固定模式下运行。</span><span class="sxs-lookup"><span data-stu-id="5c739-208">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="5c739-209">有关详细信息，请参阅[固定模式](../run-time-config/globalization.md#invariant-mode)。</span><span class="sxs-lookup"><span data-stu-id="5c739-209">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="5c739-210">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="5c739-210">RetainVMGarbageCollection</span></span>

<span data-ttu-id="5c739-211">`RetainVMGarbageCollection` 属性配置垃圾回收器，以将已删除的内存段放置在备用列表上供将来使用或释放它们。</span><span class="sxs-lookup"><span data-stu-id="5c739-211">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="5c739-212">将值设置为 `true` 会告知垃圾回收器将段放在备用列表上。</span><span class="sxs-lookup"><span data-stu-id="5c739-212">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="5c739-213">有关详细信息，请参阅[保留 VM](../run-time-config/garbage-collector.md#retain-vm)。</span><span class="sxs-lookup"><span data-stu-id="5c739-213">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="5c739-214">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="5c739-214">ServerGarbageCollection</span></span>

<span data-ttu-id="5c739-215">`ServerGarbageCollection` 属性配置应用程序是使用[工作站垃圾回收还是服务器垃圾回收](../../standard/garbage-collection/workstation-server-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="5c739-215">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="5c739-216">将值设置为 `true` 以使用服务器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="5c739-216">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="5c739-217">有关详细信息，请参阅[工作站与服务器](../run-time-config/garbage-collector.md#workstation-vs-server)。</span><span class="sxs-lookup"><span data-stu-id="5c739-217">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="5c739-218">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="5c739-218">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="5c739-219">`ThreadPoolMaxThreads` 属性配置工作线程池的最大线程数。</span><span class="sxs-lookup"><span data-stu-id="5c739-219">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="5c739-220">有关详细信息，请参阅[最大线程数](../run-time-config/threading.md#maximum-threads)。</span><span class="sxs-lookup"><span data-stu-id="5c739-220">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="5c739-221">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="5c739-221">ThreadPoolMinThreads</span></span>

<span data-ttu-id="5c739-222">`ThreadPoolMinThreads` 属性配置工作线程池的最小线程数。</span><span class="sxs-lookup"><span data-stu-id="5c739-222">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="5c739-223">有关详细信息，请参阅[最小线程数](../run-time-config/threading.md#minimum-threads)。</span><span class="sxs-lookup"><span data-stu-id="5c739-223">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="5c739-224">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="5c739-224">TieredCompilation</span></span>

<span data-ttu-id="5c739-225">`TieredCompilation` 属性配置实时 (JIT) 编译器是否使用[分层编译](../whats-new/dotnet-core-3-0.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="5c739-225">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="5c739-226">将值设置为 `false` 以禁用分层编译。</span><span class="sxs-lookup"><span data-stu-id="5c739-226">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="5c739-227">有关详细信息，请参阅[分层编译](../run-time-config/compilation.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="5c739-227">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="5c739-228">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="5c739-228">TieredCompilationQuickJit</span></span>

<span data-ttu-id="5c739-229">`TieredCompilationQuickJit` 属性配置 JIT 编译器是否使用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="5c739-229">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="5c739-230">将值设置为 `false` 以禁用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="5c739-230">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="5c739-231">有关详细信息，请参阅[快速 JIT](../run-time-config/compilation.md#quick-jit)。</span><span class="sxs-lookup"><span data-stu-id="5c739-231">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="5c739-232">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="5c739-232">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="5c739-233">`TieredCompilationQuickJitForLoops` 配置 JIT 编译器是否对包含循环的方法使用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="5c739-233">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="5c739-234">将值设置为 `true` 以对包含循环的方法启用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="5c739-234">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="5c739-235">有关详细信息，请参阅[适用于循环的快速 JIT](../run-time-config/compilation.md#quick-jit-for-loops)。</span><span class="sxs-lookup"><span data-stu-id="5c739-235">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="5c739-236">引用属性和项</span><span class="sxs-lookup"><span data-stu-id="5c739-236">Reference properties and items</span></span>

- [<span data-ttu-id="5c739-237">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="5c739-237">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="5c739-238">PackageReference</span><span class="sxs-lookup"><span data-stu-id="5c739-238">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="5c739-239">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="5c739-239">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="5c739-240">引用</span><span class="sxs-lookup"><span data-stu-id="5c739-240">Reference</span></span>](#reference)
- [<span data-ttu-id="5c739-241">还原属性</span><span class="sxs-lookup"><span data-stu-id="5c739-241">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="5c739-242">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="5c739-242">AssetTargetFallback</span></span>

<span data-ttu-id="5c739-243">使用 `AssetTargetFallback` 属性，可以为项目引用和 NuGet 包指定其他兼容的框架版本。</span><span class="sxs-lookup"><span data-stu-id="5c739-243">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="5c739-244">例如，如果使用 `PackageReference` 指定包依赖项，但该包不包含与项目的 `TargetFramework` 兼容的资源，则可使用 `AssetTargetFallback` 属性。</span><span class="sxs-lookup"><span data-stu-id="5c739-244">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="5c739-245">使用 `AssetTargetFallback` 中指定的每个目标框架重新检查引用包的兼容性。</span><span class="sxs-lookup"><span data-stu-id="5c739-245">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="5c739-246">可以将 `AssetTargetFallback` 属性设置为一个或多个[目标框架版本](../../standard/frameworks.md#supported-target-framework-versions)。</span><span class="sxs-lookup"><span data-stu-id="5c739-246">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="5c739-247">PackageReference</span><span class="sxs-lookup"><span data-stu-id="5c739-247">PackageReference</span></span>

<span data-ttu-id="5c739-248">`PackageReference` 项定义了对 NuGet 包的引用。</span><span class="sxs-lookup"><span data-stu-id="5c739-248">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="5c739-249">`Include` 属性指定包 ID。</span><span class="sxs-lookup"><span data-stu-id="5c739-249">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="5c739-250">`Version` 特性指定版本或版本范围。</span><span class="sxs-lookup"><span data-stu-id="5c739-250">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="5c739-251">若要了解如何指定最低版本、最高版本、范围或完全匹配，请参阅[版本范围](/nuget/concepts/package-versioning#version-ranges)。</span><span class="sxs-lookup"><span data-stu-id="5c739-251">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="5c739-252">还可以将下面的元数据添加到项目引用中：`IncludeAssets`、`ExcludeAssets` 和 `PrivateAssets`。</span><span class="sxs-lookup"><span data-stu-id="5c739-252">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="5c739-253">以下示例中的项目文件片段引用 [System.Runtime](https://www.nuget.org/packages/System.Runtime/) 包。</span><span class="sxs-lookup"><span data-stu-id="5c739-253">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="5c739-254">有关详细信息，请参阅[项目文件中的包引用](/nuget/consume-packages/package-references-in-project-files)。</span><span class="sxs-lookup"><span data-stu-id="5c739-254">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="5c739-255">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="5c739-255">ProjectReference</span></span>

<span data-ttu-id="5c739-256">`ProjectReference` 项定义对另一个项目的引用。</span><span class="sxs-lookup"><span data-stu-id="5c739-256">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="5c739-257">被引用的项目作为 NuGet 包依赖项添加，即它被视为与 `PackageReference` 相同。</span><span class="sxs-lookup"><span data-stu-id="5c739-257">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="5c739-258">`Include` 特性指定项目路径。</span><span class="sxs-lookup"><span data-stu-id="5c739-258">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="5c739-259">还可以将下面的元数据添加到项目引用中：`IncludeAssets`、`ExcludeAssets` 和 `PrivateAssets`。</span><span class="sxs-lookup"><span data-stu-id="5c739-259">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="5c739-260">以下示例中的项目文件片段引用名为 `Project2` 的项目。</span><span class="sxs-lookup"><span data-stu-id="5c739-260">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="5c739-261">参考</span><span class="sxs-lookup"><span data-stu-id="5c739-261">Reference</span></span>

<span data-ttu-id="5c739-262">`Reference` 项定义对程序集文件的引用。</span><span class="sxs-lookup"><span data-stu-id="5c739-262">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="5c739-263">`Include` 特性用于指定文件名，`HintPath` 元数据用于指定程序集路径。</span><span class="sxs-lookup"><span data-stu-id="5c739-263">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="5c739-264">还原属性</span><span class="sxs-lookup"><span data-stu-id="5c739-264">Restore properties</span></span>

<span data-ttu-id="5c739-265">还原被引用的包会安装它的所有直接依赖项，以及这些依赖项的全部依赖项。</span><span class="sxs-lookup"><span data-stu-id="5c739-265">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="5c739-266">可以通过指定 `RestorePackagesPath` 和 `RestoreIgnoreFailedSources` 等属性来自定义包还原。</span><span class="sxs-lookup"><span data-stu-id="5c739-266">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="5c739-267">若要详细了解这些属性和其他属性，请参阅[还原目标](/nuget/reference/msbuild-targets#restore-target)。</span><span class="sxs-lookup"><span data-stu-id="5c739-267">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="5c739-268">请参阅</span><span class="sxs-lookup"><span data-stu-id="5c739-268">See also</span></span>

- [<span data-ttu-id="5c739-269">MSBuild 架构引用</span><span class="sxs-lookup"><span data-stu-id="5c739-269">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="5c739-270">通用 MSBuild 属性</span><span class="sxs-lookup"><span data-stu-id="5c739-270">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="5c739-271">NuGet 包的 MSBuild 属性</span><span class="sxs-lookup"><span data-stu-id="5c739-271">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="5c739-272">NuGet 还原的 MSBuild 属性</span><span class="sxs-lookup"><span data-stu-id="5c739-272">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="5c739-273">自定义生成</span><span class="sxs-lookup"><span data-stu-id="5c739-273">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
