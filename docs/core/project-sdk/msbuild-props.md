---
title: Microsoft.NET.Sdk 的 MSBuild 属性
description: .NET Core SDK 可以理解的 MSBuild 属性和项的引用。
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 7980369b87d606d3876fe043e929a65da1d0d92b
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916251"
---
# <a name="msbuild-reference-for-net-core-sdk-projects"></a>.NET Core SDK 项目的 MSBuild 引用

此页是对可用于配置 .NET Core 项目的 MSBuild 属性和项的引用。

> [!NOTE]
> 此页面正在运行中，未列出 .NET Core SDK 的所有有用的 MSBuild 属性。 有关通用 MSBuild 属性的列表，请参阅[通用 MSBuild 属性](/visualstudio/msbuild/common-msbuild-project-properties)。

## <a name="framework-properties"></a>框架属性

- [TargetFramework](#targetframework)
- [TargetFrameworks](#targetframeworks)
- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>TargetFramework

`TargetFramework` 属性指定应用的目标框架版本。 有关有效的目标框架名字对象的列表，请参阅 [SDK 样式项目中的目标框架](../../standard/frameworks.md#supported-target-framework-versions)。

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

有关详细信息，请参阅 [SDK 样式项目中的目标框架](../../standard/frameworks.md)。

### <a name="targetframeworks"></a>TargetFrameworks

如果希望应用面向多个平台，请使用 `TargetFrameworks` 属性。 有关有效的目标框架名字对象的列表，请参阅 [SDK 样式项目中的目标框架](../../standard/frameworks.md#supported-target-framework-versions)。

> [!NOTE]
> 如果指定了 `TargetFramework`（单数），则忽略此属性。

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

有关详细信息，请参阅 [SDK 样式项目中的目标框架](../../standard/frameworks.md)。

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> 此属性仅适用于使用 `netstandard1.x` 的项目。 它不适用于使用 `netstandard2.x` 的项目。

如果要指定低于元包版本的框架版本，请使用 `NetStandardImplicitPackageVersion` 属性。 以下示例中的项目文件以 `netstandard1.3` 为目标，但使用 `NETStandard.Library` 的 1.6.0 版本。

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a>包属性

可以指定 `PackageId`、`PackageVersion`、`PackageIcon`、`Title` 和 `Description` 等属性来描述通过项目创建的包。 若要了解这些属性和其他属性，请参阅[包目标](/nuget/reference/msbuild-targets#pack-target)。

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a>发布属性和项

- [RuntimeIdentifier](#runtimeidentifier)
- [RuntimeIdentifiers](#runtimeidentifiers)
- [TrimmerRootAssembly](#trimmerrootassembly)
- [UseAppHost](#useapphost)

### <a name="runtimeidentifier"></a>RuntimeIdentifier

`RuntimeIdentifier` 属性可用于指定项目的单个[运行时标识符 (RID)](../rid-catalog.md)。 RID 支持发布独立部署。

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

`RuntimeIdentifiers` 属性可用于指定项目的[运行时标识符 (RID)](../rid-catalog.md) 的列表（以分号分隔）。 如果需要为多个运行时发布，请使用此属性。 `RuntimeIdentifiers` 在还原时使用，以确保图中有适当的资产。

> [!TIP]
> `RuntimeIdentifier`（单数）可以在只需要一个运行时时提供更快的生成。

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a>TrimmerRootAssembly

`TrimmerRootAssembly` 项允许通过[修整](../deploying/trim-self-contained.md)排除程序集。 修整是从打包的应用程序中删除运行时未使用部分的过程。 在某些情况下，修整可能会错误地删除所需的引用。

以下 XML 通过修整排除 `System.Security` 程序集。

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a>UseAppHost

`UseAppHost` 属性是在 .NET Core SDK 的 2.1.400 版本中引入的。 它控制是否为部署创建本机可执行文件。 自包含部署需要本机可执行文件。

在 .NET Core3.0 及更高版本中，默认情况下会创建依赖于框架的可执行文件。 将 `UseAppHost` 属性设置为 `false` 可禁用可执行文件的生成。

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

有关部署的详细信息，请参阅 [.NET Core 应用程序部署](../deploying/index.md)。

## <a name="compile-properties"></a>编译属性

- [EmbeddedResourceUseDependentUponConvention](#embeddedresourceusedependentuponconvention)
- [LangVersion](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a>EmbeddedResourceUseDependentUponConvention

`EmbeddedResourceUseDependentUponConvention` 属性定义了是否从与资源文件并置的源文件中的类型信息生成资源清单文件名。 例如，如果 Form1.resx 与 Form1.cs 位于同一文件夹中，并且 `EmbeddedResourceUseDependentUponConvention` 设置为 `true`，则生成的 .resources 文件将采用 Form1.cs 中定义的第一个类型的名称作为其文件名。 例如，如果 Form1.cs 中定义的第一个类型为 `MyNamespace.Form1`，则生成的文件名为 MyNamespace.Form1.resources。

> [!NOTE]
> 如果为 `EmbeddedResource` 项指定 `LogicalName`、`ManifestResourceName` 或 `DependentUpon` 元数据，则为该资源文件生成的清单文件名将改为基于该元数据。

默认情况下，在新的 .NET Core 项目中，此属性设置为 `true`。 如果设置为 `false`，并且没有为项目文件中的 `EmbeddedResource` 项指定 `LogicalName`、`ManifestResourceName` 或 `DependentUpon` 元数据，则资源清单文件名将基于项目的根命名空间和 .resx 文件的相对文件路径。 有关详细信息，请参阅[资源清单文件的命名](../resources/manifest-file-names.md)。

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a>LangVersion

`LangVersion` 属性可用于指定特定的编程语言版本。 例如，如果要访问 C# 预览功能，请将 `LangVersion` 设置为 `preview`。

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

有关详细信息，请参阅 [C# 语言版本控制](../../csharp/language-reference/configure-language-version.md#override-a-default)。

## <a name="run-time-configuration-properties"></a>运行时配置属性

可以通过在应用的项目文件中指定 MSBuild 属性来配置某些运行时行为。 有关配置运行时行为的其他方法的信息，请参阅 [.NET Core 运行时配置设置](../run-time-config/index.md)。

- [ConcurrentGarbageCollection](#concurrentgarbagecollection)
- [InvariantGlobalization](#invariantglobalization)
- [RetainVMGarbageCollection](#retainvmgarbagecollection)
- [ServerGarbageCollection](#servergarbagecollection)
- [ThreadPoolMaxThreads](#threadpoolmaxthreads)
- [ThreadPoolMinThreads](#threadpoolminthreads)
- [TieredCompilation](#tieredcompilation)
- [TieredCompilationQuickJit](#tieredcompilationquickjit)
- [TieredCompilationQuickJitForLoops](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a>ConcurrentGarbageCollection

`ConcurrentGarbageCollection` 属性配置是否启用 [后台（并发）垃圾回收](../../standard/garbage-collection/background-gc.md)。 将值设置为 `false` 以禁用后台垃圾回收。 有关详细信息，请参阅[后台 GC](../run-time-config/garbage-collector.md#background-gc)。

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a>InvariantGlobalization

`InvariantGlobalization` 属性配置应用是否在全球化固定模式下运行，这意味着它无权访问特定于区域性的数据。 将值设置为 `true` 以在全球化固定模式下运行。 有关详细信息，请参阅[固定模式](../run-time-config/globalization.md#invariant-mode)。

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a>RetainVMGarbageCollection

`RetainVMGarbageCollection` 属性配置垃圾回收器，以将已删除的内存段放置在备用列表上供将来使用或释放它们。 将值设置为 `true` 会告知垃圾回收器将段放在备用列表上。 有关详细信息，请参阅[保留 VM](../run-time-config/garbage-collector.md#retain-vm)。

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a>ServerGarbageCollection

`ServerGarbageCollection` 属性配置应用程序是使用[工作站垃圾回收还是服务器垃圾回收](../../standard/garbage-collection/workstation-server-gc.md)。 将值设置为 `true` 以使用服务器垃圾回收。 有关详细信息，请参阅[工作站与服务器](../run-time-config/garbage-collector.md#workstation-vs-server)。

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a>ThreadPoolMaxThreads

`ThreadPoolMaxThreads` 属性配置工作线程池的最大线程数。 有关详细信息，请参阅[最大线程数](../run-time-config/threading.md#maximum-threads)。

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a>ThreadPoolMinThreads

`ThreadPoolMinThreads` 属性配置工作线程池的最小线程数。 有关详细信息，请参阅[最小线程数](../run-time-config/threading.md#minimum-threads)。

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a>TieredCompilation

`TieredCompilation` 属性配置实时 (JIT) 编译器是否使用[分层编译](../whats-new/dotnet-core-3-0.md#tiered-compilation)。 将值设置为 `false` 以禁用分层编译。 有关详细信息，请参阅[分层编译](../run-time-config/compilation.md#tiered-compilation)。

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a>TieredCompilationQuickJit

`TieredCompilationQuickJit` 属性配置 JIT 编译器是否使用快速 JIT。 将值设置为 `false` 以禁用快速 JIT。 有关详细信息，请参阅[快速 JIT](../run-time-config/compilation.md#quick-jit)。

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a>TieredCompilationQuickJitForLoops

`TieredCompilationQuickJitForLoops` 配置 JIT 编译器是否对包含循环的方法使用快速 JIT。 将值设置为 `true` 以对包含循环的方法启用快速 JIT。 有关详细信息，请参阅[适用于循环的快速 JIT](../run-time-config/compilation.md#quick-jit-for-loops)。

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a>引用属性和项

- [AssetTargetFallback](#assettargetfallback)
- [PackageReference](#packagereference)
- [ProjectReference](#projectreference)
- [引用](#reference)
- [还原属性](#restore-properties)

### <a name="assettargetfallback"></a>AssetTargetFallback

使用 `AssetTargetFallback` 属性，可以为项目引用和 NuGet 包指定其他兼容的框架版本。 例如，如果使用 `PackageReference` 指定包依赖项，但该包不包含与项目的 `TargetFramework` 兼容的资源，则可使用 `AssetTargetFallback` 属性。 使用 `AssetTargetFallback` 中指定的每个目标框架重新检查引用包的兼容性。

可以将 `AssetTargetFallback` 属性设置为一个或多个[目标框架版本](../../standard/frameworks.md#supported-target-framework-versions)。

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a>PackageReference

`PackageReference` 项定义了对 NuGet 包的引用。

`Include` 属性指定包 ID。 `Version` 特性指定版本或版本范围。 若要了解如何指定最低版本、最高版本、范围或完全匹配，请参阅[版本范围](/nuget/concepts/package-versioning#version-ranges)。 还可以将下面的元数据添加到项目引用中：`IncludeAssets`、`ExcludeAssets` 和 `PrivateAssets`。

以下示例中的项目文件片段引用 [System.Runtime](https://www.nuget.org/packages/System.Runtime/) 包。

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

有关详细信息，请参阅[项目文件中的包引用](/nuget/consume-packages/package-references-in-project-files)。

### <a name="projectreference"></a>ProjectReference

`ProjectReference` 项定义对另一个项目的引用。 被引用的项目作为 NuGet 包依赖项添加，即它被视为与 `PackageReference` 相同。

`Include` 特性指定项目路径。 还可以将下面的元数据添加到项目引用中：`IncludeAssets`、`ExcludeAssets` 和 `PrivateAssets`。

以下示例中的项目文件片段引用名为 `Project2` 的项目。

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a>参考

`Reference` 项定义对程序集文件的引用。

`Include` 特性用于指定文件名，`HintPath` 元数据用于指定程序集路径。

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a>还原属性

还原被引用的包会安装它的所有直接依赖项，以及这些依赖项的全部依赖项。 可以通过指定 `RestorePackagesPath` 和 `RestoreIgnoreFailedSources` 等属性来自定义包还原。 若要详细了解这些属性和其他属性，请参阅[还原目标](/nuget/reference/msbuild-targets#restore-target)。

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a>请参阅

- [MSBuild 架构引用](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [通用 MSBuild 属性](/visualstudio/msbuild/common-msbuild-project-properties)
- [NuGet 包的 MSBuild 属性](/nuget/reference/msbuild-targets#pack-target)
- [NuGet 还原的 MSBuild 属性](/nuget/reference/msbuild-targets#restore-properties)
- [自定义生成](/visualstudio/msbuild/customize-your-build)
