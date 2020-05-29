---
title: 比较 project.json 和 csproj
description: 查看 project.json 和 csproj 元素之间的映射。
author: natemcmaster
ms.date: 03/13/2017
ms.openlocfilehash: a997b48f645ed58d15610a68aee7c67411f9763f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205834"
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a><span data-ttu-id="23b33-103">project.json 和 csproj 属性之间的映射</span><span class="sxs-lookup"><span data-stu-id="23b33-103">A mapping between project.json and csproj properties</span></span>

<span data-ttu-id="23b33-104">作者 [Nate McMaster](https://github.com/natemcmaster)</span><span class="sxs-lookup"><span data-stu-id="23b33-104">By [Nate McMaster](https://github.com/natemcmaster)</span></span>

<span data-ttu-id="23b33-105">.NET Core 工具的开发过程中实施了一项重要的设计更改，即不再支持 *project.json* 文件，而是将 .NET Core 项目转移到 MSBuild/csproj 格式。</span><span class="sxs-lookup"><span data-stu-id="23b33-105">During the development of the .NET Core tooling, an important design change was made to no longer support *project.json* files and instead move the .NET Core projects to the MSBuild/csproj format.</span></span>

<span data-ttu-id="23b33-106">本文介绍 *project.json* 中的设置如何以 MSBuild/csproj 格式表示，以便用户可学习如何使用新格式，并了解将项目升级到最新版本的工具时由迁移工具做出的更改。</span><span class="sxs-lookup"><span data-stu-id="23b33-106">This article shows how the settings in *project.json* are represented in the MSBuild/csproj format so you can learn how to use the new format and understand the changes made by the migration tools when you're upgrading your project to the latest version of the tooling.</span></span>

## <a name="the-csproj-format"></a><span data-ttu-id="23b33-107">csproj 格式</span><span class="sxs-lookup"><span data-stu-id="23b33-107">The csproj format</span></span>

<span data-ttu-id="23b33-108">新格式 \*.csproj 是一种基于 XML 的格式。</span><span class="sxs-lookup"><span data-stu-id="23b33-108">The new format, \*.csproj, is an XML-based format.</span></span> <span data-ttu-id="23b33-109">以下示例演示使用 `Microsoft.NET.Sdk` 的 .NET Core 项目的根节点。</span><span class="sxs-lookup"><span data-stu-id="23b33-109">The following example shows the root node of a .NET Core project using the `Microsoft.NET.Sdk`.</span></span> <span data-ttu-id="23b33-110">对于 Web 项目，所使用的 SDK 是 `Microsoft.NET.Sdk.Web`。</span><span class="sxs-lookup"><span data-stu-id="23b33-110">For web projects, the SDK used is `Microsoft.NET.Sdk.Web`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a><span data-ttu-id="23b33-111">常见顶级属性</span><span class="sxs-lookup"><span data-stu-id="23b33-111">Common top-level properties</span></span>

### <a name="name"></a><span data-ttu-id="23b33-112">NAME</span><span class="sxs-lookup"><span data-stu-id="23b33-112">name</span></span>

```json
{
  "name": "MyProjectName"
}
```

<span data-ttu-id="23b33-113">不再支持。</span><span class="sxs-lookup"><span data-stu-id="23b33-113">No longer supported.</span></span> <span data-ttu-id="23b33-114">在 csproj 中，这取决于项目文件名（通常与目录名称匹配）。</span><span class="sxs-lookup"><span data-stu-id="23b33-114">In csproj, this is determined by the project filename, which usually matches the directory name.</span></span> <span data-ttu-id="23b33-115">例如 `MyProjectName.csproj`。</span><span class="sxs-lookup"><span data-stu-id="23b33-115">For example, `MyProjectName.csproj`.</span></span>

<span data-ttu-id="23b33-116">默认情况下，项目文件名还指定 `<AssemblyName>` 和 `<PackageId>` 属性的值。</span><span class="sxs-lookup"><span data-stu-id="23b33-116">By default, the project filename also specifies the value of the `<AssemblyName>` and `<PackageId>` properties.</span></span>

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

<span data-ttu-id="23b33-117">如果 `buildOptions\outputName` 属性是在 project.json 中定义的，`<AssemblyName>` 将具有不同于 `<PackageId>` 的其他值。</span><span class="sxs-lookup"><span data-stu-id="23b33-117">The `<AssemblyName>` will have a different value than `<PackageId>` if `buildOptions\outputName` property was defined in project.json.</span></span>
<span data-ttu-id="23b33-118">有关详细信息，请参阅[其他常用生成选项](#other-common-build-options)。</span><span class="sxs-lookup"><span data-stu-id="23b33-118">For more information, see [Other common build options](#other-common-build-options).</span></span>

### <a name="version"></a><span data-ttu-id="23b33-119">version</span><span class="sxs-lookup"><span data-stu-id="23b33-119">version</span></span>

```json
{
  "version": "1.0.0-alpha-*"
}
```

<span data-ttu-id="23b33-120">使用 `VersionPrefix` 和 `VersionSuffix` 属性：</span><span class="sxs-lookup"><span data-stu-id="23b33-120">Use the `VersionPrefix` and `VersionSuffix` properties:</span></span>

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

<span data-ttu-id="23b33-121">还可以使用 `Version` 属性，但这可能会在打包过程中替代版本设置：</span><span class="sxs-lookup"><span data-stu-id="23b33-121">You can also use the `Version` property, but this may override version settings during packaging:</span></span>

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a><span data-ttu-id="23b33-122">其他常用根级别选项</span><span class="sxs-lookup"><span data-stu-id="23b33-122">Other common root-level options</span></span>

```json
{
  "authors": [ "Anne", "Bob" ],
  "company": "Contoso",
  "language": "en-US",
  "title": "My library",
  "description": "This is my library.\r\nAnd it's really great!",
  "copyright": "Nugetizer 3000",
  "userSecretsId": "xyz123"
}
```

```xml
<PropertyGroup>
  <Authors>Anne;Bob</Authors>
  <Company>Contoso</Company>
  <NeutralLanguage>en-US</NeutralLanguage>
  <AssemblyTitle>My library</AssemblyTitle>
  <Description>This is my library.
And it's really great!</Description>
  <Copyright>Nugetizer 3000</Copyright>
  <UserSecretsId>xyz123</UserSecretsId>
</PropertyGroup>
```

## <a name="frameworks"></a><span data-ttu-id="23b33-123">框架</span><span class="sxs-lookup"><span data-stu-id="23b33-123">frameworks</span></span>

### <a name="one-target-framework"></a><span data-ttu-id="23b33-124">一个目标框架</span><span class="sxs-lookup"><span data-stu-id="23b33-124">One target framework</span></span>

```json
{
  "frameworks": {
    "netcoreapp1.0": {}
  }
}
```

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp1.0</TargetFramework>
</PropertyGroup>
```

### <a name="multiple-target-frameworks"></a><span data-ttu-id="23b33-125">多个目标框架</span><span class="sxs-lookup"><span data-stu-id="23b33-125">Multiple target frameworks</span></span>

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

<span data-ttu-id="23b33-126">使用 `TargetFrameworks` 属性定义目标框架的列表。</span><span class="sxs-lookup"><span data-stu-id="23b33-126">Use the `TargetFrameworks` property to define your list of target frameworks.</span></span> <span data-ttu-id="23b33-127">使用分号来分隔多个框架值。</span><span class="sxs-lookup"><span data-stu-id="23b33-127">Use semi-colon to separate multiple framework values.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a><span data-ttu-id="23b33-128">依赖项</span><span class="sxs-lookup"><span data-stu-id="23b33-128">dependencies</span></span>

> [!IMPORTANT]
> <span data-ttu-id="23b33-129">如果依赖项是一个**项目**而不是包，则格式不同。</span><span class="sxs-lookup"><span data-stu-id="23b33-129">If the dependency is a **project** and not a package, the format is different.</span></span>
> <span data-ttu-id="23b33-130">有关详细信息，请参阅[依赖项类型](#dependency-type)部分。</span><span class="sxs-lookup"><span data-stu-id="23b33-130">For more information, see the [dependency type](#dependency-type) section.</span></span>

### <a name="netstandardlibrary-metapackage"></a><span data-ttu-id="23b33-131">NETStandard.Library 元包</span><span class="sxs-lookup"><span data-stu-id="23b33-131">NETStandard.Library metapackage</span></span>

```json
{
  "dependencies": {
    "NETStandard.Library": "1.6.0"
  }
}
```

```xml
<PropertyGroup>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

### <a name="microsoftnetcoreapp-metapackage"></a><span data-ttu-id="23b33-132">Microsoft.NETCore.App 元包</span><span class="sxs-lookup"><span data-stu-id="23b33-132">Microsoft.NETCore.App metapackage</span></span>

```json
{
  "dependencies": {
    "Microsoft.NETCore.App": "1.0.0"
  }
}
```

```xml
<PropertyGroup>
  <RuntimeFrameworkVersion>1.0.3</RuntimeFrameworkVersion>
</PropertyGroup>
```

<span data-ttu-id="23b33-133">迁移项目中的 `<RuntimeFrameworkVersion>` 值由已安装的 SDK 版本确定。</span><span class="sxs-lookup"><span data-stu-id="23b33-133">The `<RuntimeFrameworkVersion>` value in the migrated project is determined by the version of SDK that's installed.</span></span>

### <a name="top-level-dependencies"></a><span data-ttu-id="23b33-134">顶级依赖项</span><span class="sxs-lookup"><span data-stu-id="23b33-134">Top-level dependencies</span></span>

```json
{
  "dependencies": {
    "Microsoft.AspNetCore": "1.1.0"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore" Version="1.1.0" />
</ItemGroup>
```

### <a name="per-framework-dependencies"></a><span data-ttu-id="23b33-135">依赖项（按框架）</span><span class="sxs-lookup"><span data-stu-id="23b33-135">Per-framework dependencies</span></span>

```json
{
  "framework": {
    "net451": {
      "dependencies": {
        "System.Collections.Immutable": "1.3.1"
      }
    },
    "netstandard1.5": {
      "dependencies": {
        "Newtonsoft.Json": "9.0.1"
      }
    }
  }
}
```

```xml
<ItemGroup Condition="'$(TargetFramework)'=='net451'">
  <PackageReference Include="System.Collections.Immutable" Version="1.3.1" />
</ItemGroup>

<ItemGroup Condition="'$(TargetFramework)'=='netstandard1.5'">
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
</ItemGroup>
```

### <a name="imports"></a><span data-ttu-id="23b33-136">导入</span><span class="sxs-lookup"><span data-stu-id="23b33-136">imports</span></span>

```json
{
  "dependencies": {
    "YamlDotNet": "4.0.1-pre309"
  },
  "frameworks": {
    "netcoreapp1.0": {
      "imports": [
        "dnxcore50",
        "dotnet"
      ]
    }
  }
}
```

```xml
<PropertyGroup>
  <PackageTargetFallback>dnxcore50;dotnet</PackageTargetFallback>
</PropertyGroup>
<ItemGroup>
  <PackageReference Include="YamlDotNet" Version="4.0.1-pre309" />
</ItemGroup>
```

### <a name="dependency-type"></a><span data-ttu-id="23b33-137">依赖项类型</span><span class="sxs-lookup"><span data-stu-id="23b33-137">dependency type</span></span>

#### <a name="type-project"></a><span data-ttu-id="23b33-138">类型：项目</span><span class="sxs-lookup"><span data-stu-id="23b33-138">type: project</span></span>

```json
{
  "dependencies": {
    "MyOtherProject": "1.0.0-*",
    "AnotherProject": {
      "type": "project"
    }
  }
}
```

```xml
<ItemGroup>
  <ProjectReference Include="..\MyOtherProject\MyOtherProject.csproj" />
  <ProjectReference Include="..\AnotherProject\AnotherProject.csproj" />
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="23b33-139">这将打破 `dotnet pack --version-suffix $suffix` 确定项目引用的依赖项版本的方式。</span><span class="sxs-lookup"><span data-stu-id="23b33-139">This will break the way that `dotnet pack --version-suffix $suffix` determines the dependency version of a project reference.</span></span>

#### <a name="type-build"></a><span data-ttu-id="23b33-140">类型：生成</span><span class="sxs-lookup"><span data-stu-id="23b33-140">type: build</span></span>

```json
{
  "dependencies": {
    "Microsoft.EntityFrameworkCore.Design": {
      "version": "1.1.0",
      "type": "build"
    }
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="1.1.0" PrivateAssets="All" />
</ItemGroup>
```

#### <a name="type-platform"></a><span data-ttu-id="23b33-141">类型：平台</span><span class="sxs-lookup"><span data-stu-id="23b33-141">type: platform</span></span>

```json
{
  "dependencies": {
    "Microsoft.NETCore.App": {
      "version": "1.1.0",
      "type": "platform"
    }
  }
}
```

<span data-ttu-id="23b33-142">csproj 中没有等效项。</span><span class="sxs-lookup"><span data-stu-id="23b33-142">There is no equivalent in csproj.</span></span>

## <a name="runtimes"></a><span data-ttu-id="23b33-143">runtimes</span><span class="sxs-lookup"><span data-stu-id="23b33-143">runtimes</span></span>

```json
{
  "runtimes": {
    "win7-x64": {},
    "osx.10.11-x64": {},
    "ubuntu.16.04-x64": {}
  }
}
```

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win7-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="standalone-apps-self-contained-deployment"></a><span data-ttu-id="23b33-144">独立应用（独立部署）</span><span class="sxs-lookup"><span data-stu-id="23b33-144">Standalone apps (self-contained deployment)</span></span>

<span data-ttu-id="23b33-145">在 project.json 中，定义 `runtimes` 部分意味着应用在生成和发布期间独立。</span><span class="sxs-lookup"><span data-stu-id="23b33-145">In project.json, defining a `runtimes` section means the app was standalone during build and publish.</span></span>
<span data-ttu-id="23b33-146">在 MSBuild 中，生成期间所有项目均*可移植*，但可发布为独立。</span><span class="sxs-lookup"><span data-stu-id="23b33-146">In MSBuild, all projects are *portable* during build, but can be published as standalone.</span></span>

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

<span data-ttu-id="23b33-147">有关详细信息，请参阅[独立部署 (SCD)](../deploying/index.md#publish-self-contained)。</span><span class="sxs-lookup"><span data-stu-id="23b33-147">For more information, see [Self-contained deployments (SCD)](../deploying/index.md#publish-self-contained).</span></span>

## <a name="tools"></a><span data-ttu-id="23b33-148">工具</span><span class="sxs-lookup"><span data-stu-id="23b33-148">tools</span></span>

```json
{
  "tools": {
    "Microsoft.EntityFrameworkCore.Tools.DotNet": "1.0.0-*"
  }
}
```

```xml
<ItemGroup>
  <DotNetCliToolReference Include="Microsoft.EntityFrameworkCore.Tools.DotNet" Version="1.0.0" />
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="23b33-149">csproj 中不支持工具上的 `imports`。</span><span class="sxs-lookup"><span data-stu-id="23b33-149">`imports` on tools are not supported in csproj.</span></span> <span data-ttu-id="23b33-150">需要导入的工具无法用于新的 `Microsoft.NET.Sdk`。</span><span class="sxs-lookup"><span data-stu-id="23b33-150">Tools that need imports will not work with the new `Microsoft.NET.Sdk`.</span></span>

## <a name="buildoptions"></a><span data-ttu-id="23b33-151">buildOptions</span><span class="sxs-lookup"><span data-stu-id="23b33-151">buildOptions</span></span>

<span data-ttu-id="23b33-152">另请参阅[文件](#files)。</span><span class="sxs-lookup"><span data-stu-id="23b33-152">See also [Files](#files).</span></span>

### <a name="emitentrypoint"></a><span data-ttu-id="23b33-153">emitEntryPoint</span><span class="sxs-lookup"><span data-stu-id="23b33-153">emitEntryPoint</span></span>

```json
{
  "buildOptions": {
    "emitEntryPoint": true
  }
}
```

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="23b33-154">如果 `emitEntryPoint` 为 `false`，`OutputType` 的值会转换为 `Library`（这是默认值）：</span><span class="sxs-lookup"><span data-stu-id="23b33-154">If `emitEntryPoint` was `false`, the value of `OutputType` is converted to `Library`, which is the default value:</span></span>

```json
{
  "buildOptions": {
    "emitEntryPoint": false
  }
}
```

```xml
<PropertyGroup>
  <OutputType>Library</OutputType>
  <!-- or, omit altogether. It defaults to 'Library' -->
</PropertyGroup>
```

### <a name="keyfile"></a><span data-ttu-id="23b33-155">keyFile</span><span class="sxs-lookup"><span data-stu-id="23b33-155">keyFile</span></span>

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

<span data-ttu-id="23b33-156">`keyFile` 元素在 MSBuild 中扩展为三个属性：</span><span class="sxs-lookup"><span data-stu-id="23b33-156">The `keyFile` element expands to three properties in MSBuild:</span></span>

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a><span data-ttu-id="23b33-157">其他常用生成选项</span><span class="sxs-lookup"><span data-stu-id="23b33-157">Other common build options</span></span>

```json
{
  "buildOptions": {
    "warningsAsErrors": true,
    "nowarn": ["CS0168", "CS0219"],
    "xmlDoc": true,
    "preserveCompilationContext": true,
    "outputName": "Different.AssemblyName",
    "debugType": "portable",
    "allowUnsafe": true,
    "define": ["TEST", "OTHERCONDITION"]
  }
}
```

```xml
<PropertyGroup>
  <TreatWarningsAsErrors>true</TreatWarningsAsErrors>
  <NoWarn>$(NoWarn);CS0168;CS0219</NoWarn>
  <GenerateDocumentationFile>true</GenerateDocumentationFile>
  <PreserveCompilationContext>true</PreserveCompilationContext>
  <AssemblyName>Different.AssemblyName</AssemblyName>
  <DebugType>portable</DebugType>
  <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  <DefineConstants>$(DefineConstants);TEST;OTHERCONDITION</DefineConstants>
</PropertyGroup>
```

## <a name="packoptions"></a><span data-ttu-id="23b33-158">packOptions</span><span class="sxs-lookup"><span data-stu-id="23b33-158">packOptions</span></span>

<span data-ttu-id="23b33-159">另请参阅[文件](#files)。</span><span class="sxs-lookup"><span data-stu-id="23b33-159">See also [Files](#files).</span></span>

### <a name="common-pack-options"></a><span data-ttu-id="23b33-160">常用包选项</span><span class="sxs-lookup"><span data-stu-id="23b33-160">Common pack options</span></span>

```json
{
  "packOptions": {
    "summary": "numl is a machine learning library intended to ease the use of using standard modeling techniques for both prediction and clustering.",
    "tags": ["machine learning", "framework"],
    "releaseNotes": "Version 0.9.12-beta",
    "iconUrl": "http://numl.net/images/ico.png",
    "projectUrl": "http://numl.net",
    "licenseUrl": "https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md",
    "requireLicenseAcceptance": false,
    "repository": {
      "type": "git",
      "url": "https://raw.githubusercontent.com/sethjuarez/numl"
    },
    "owners": ["Seth Juarez"]
  }
}
```

```xml
<PropertyGroup>
  <!-- summary is not migrated from project.json, but you can use the <Description> property for that if needed. -->
  <PackageTags>machine learning;framework</PackageTags>
  <PackageReleaseNotes>Version 0.9.12-beta</PackageReleaseNotes>
  <PackageIconUrl>http://numl.net/images/ico.png</PackageIconUrl>
  <PackageProjectUrl>http://numl.net</PackageProjectUrl>
  <PackageLicenseUrl>https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md</PackageLicenseUrl>
  <PackageRequireLicenseAcceptance>false</PackageRequireLicenseAcceptance>
  <RepositoryType>git</RepositoryType>
  <RepositoryUrl>https://raw.githubusercontent.com/sethjuarez/numl</RepositoryUrl>
  <!-- owners is not supported in MSBuild -->
</PropertyGroup>
```

<span data-ttu-id="23b33-161">MSBuild 中没有 `owners` 元素的等效项。</span><span class="sxs-lookup"><span data-stu-id="23b33-161">There is no equivalent for the `owners` element in MSBuild.</span></span> <span data-ttu-id="23b33-162">对于 `summary`，可以使用 MSBuild `<Description>` 属性。</span><span class="sxs-lookup"><span data-stu-id="23b33-162">For `summary`, you can use the MSBuild `<Description>` property.</span></span> <span data-ttu-id="23b33-163">`summary` 的值未自动迁移到该属性，因为该属性已映射到 [`description`](#other-common-root-level-options) 元素。</span><span class="sxs-lookup"><span data-stu-id="23b33-163">The value of `summary` is not migrated automatically to that property, since that property is mapped to the [`description`](#other-common-root-level-options) element.</span></span>

## <a name="scripts"></a><span data-ttu-id="23b33-164">脚本</span><span class="sxs-lookup"><span data-stu-id="23b33-164">scripts</span></span>

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

<span data-ttu-id="23b33-165">它们在 MSBuild 中的等效项是[目标](/visualstudio/msbuild/msbuild-targets)：</span><span class="sxs-lookup"><span data-stu-id="23b33-165">Their equivalents in MSBuild are [targets](/visualstudio/msbuild/msbuild-targets):</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```

## <a name="runtimeoptions"></a><span data-ttu-id="23b33-166">runtimeOptions</span><span class="sxs-lookup"><span data-stu-id="23b33-166">runtimeOptions</span></span>

```json
{
  "runtimeOptions": {
    "configProperties": {
      "System.GC.Server": true,
      "System.GC.Concurrent": true,
      "System.GC.RetainVM": true,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

<span data-ttu-id="23b33-167">此组中除“`System.GC.Server`”属性以外的所有设置与迁移过程中被提升为根对象的选项一并被置于项目文件夹下名为 runtimeconfig.template.json 的文件中：</span><span class="sxs-lookup"><span data-stu-id="23b33-167">All settings in this group, except for the `System.GC.Server` property, are placed into a file called *runtimeconfig.template.json* in the project folder, with options lifted to the root object during the migration process:</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": true,
    "System.GC.RetainVM": true,
    "System.Threading.ThreadPool.MinThreads": 4,
    "System.Threading.ThreadPool.MaxThreads": 25
  }
}
```

<span data-ttu-id="23b33-168">`System.GC.Server` 属性已迁移到 csproj 文件：</span><span class="sxs-lookup"><span data-stu-id="23b33-168">The `System.GC.Server` property is migrated into the csproj file:</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

<span data-ttu-id="23b33-169">但可以在 csproj 以及 MSBuild 属性中设置所有这些值：</span><span class="sxs-lookup"><span data-stu-id="23b33-169">However, you can set all those values in the csproj as well as MSBuild properties:</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
</PropertyGroup>
```

## <a name="shared"></a><span data-ttu-id="23b33-170">共享</span><span class="sxs-lookup"><span data-stu-id="23b33-170">shared</span></span>

```json
{
  "shared": "shared/**/*.cs"
}
```

<span data-ttu-id="23b33-171">在 csproj 中不支持。</span><span class="sxs-lookup"><span data-stu-id="23b33-171">Not supported in csproj.</span></span> <span data-ttu-id="23b33-172">改为在 .nuspec 文件中创建包含内容文件。</span><span class="sxs-lookup"><span data-stu-id="23b33-172">Instead, create include content files in your *.nuspec* file.</span></span>
<span data-ttu-id="23b33-173">有关详细信息，请参阅[包含内容文件](/nuget/schema/nuspec#including-content-files)。</span><span class="sxs-lookup"><span data-stu-id="23b33-173">For more information, see [Including content files](/nuget/schema/nuspec#including-content-files).</span></span>

## <a name="files"></a><span data-ttu-id="23b33-174">文件</span><span class="sxs-lookup"><span data-stu-id="23b33-174">files</span></span>

<span data-ttu-id="23b33-175">在 *project.json* 中，可将生成和打包操作扩展为从不同的文件夹进行编译和嵌入。</span><span class="sxs-lookup"><span data-stu-id="23b33-175">In *project.json*, build and pack could be extended to compile and embed from different folders.</span></span>
<span data-ttu-id="23b33-176">在 MSBuild 中，使用[项](/visualstudio/msbuild/common-msbuild-project-items)实现此操作。</span><span class="sxs-lookup"><span data-stu-id="23b33-176">In MSBuild, this is done using [items](/visualstudio/msbuild/common-msbuild-project-items).</span></span> <span data-ttu-id="23b33-177">以下示例是一个常见转换：</span><span class="sxs-lookup"><span data-stu-id="23b33-177">The following example is a common conversion:</span></span>

```json
{
  "buildOptions": {
    "compile": {
      "copyToOutput": "notes.txt",
      "include": "../Shared/*.cs",
      "exclude": "../Shared/Not/*.cs"
    },
    "embed": {
      "include": "../Shared/*.resx"
    }
  },
  "packOptions": {
    "include": "Views/",
    "mappings": {
      "some/path/in/project.txt": "in/package.txt"
    }
  },
  "publishOptions": {
    "include": [
      "files/",
      "publishnotes.txt"
    ]
  }
}
```

```xml
<ItemGroup>
  <Compile Include="..\Shared\*.cs" Exclude="..\Shared\Not\*.cs" />
  <EmbeddedResource Include="..\Shared\*.resx" />
  <Content Include="Views\**\*" PackagePath="%(Identity)" />
  <None Include="some/path/in/project.txt" Pack="true" PackagePath="in/package.txt" />
  
  <None Include="notes.txt" CopyToOutputDirectory="Always" />
  <!-- CopyToOutputDirectory = { Always, PreserveNewest, Never } -->

  <Content Include="files\**\*" CopyToPublishDirectory="PreserveNewest" />
  <None Include="publishnotes.txt" CopyToPublishDirectory="Always" />
  <!-- CopyToPublishDirectory = { Always, PreserveNewest, Never } -->
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="23b33-178">许多默认 [glob 模式](https://en.wikipedia.org/wiki/Glob_(programming))由 .NET Core SDK 自动添加。</span><span class="sxs-lookup"><span data-stu-id="23b33-178">Many of the default [globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are added automatically by the .NET Core SDK.</span></span> <span data-ttu-id="23b33-179">有关详细信息，请参阅[默认编译包括](../project-sdk/overview.md#default-compilation-includes)。</span><span class="sxs-lookup"><span data-stu-id="23b33-179">For more information, see [Default compilation includes](../project-sdk/overview.md#default-compilation-includes).</span></span>

<span data-ttu-id="23b33-180">所有 MSBuild `ItemGroup` 元素都支持`Include`、`Exclude` 和 `Remove`。</span><span class="sxs-lookup"><span data-stu-id="23b33-180">All MSBuild `ItemGroup` elements support `Include`, `Exclude`, and `Remove`.</span></span>

<span data-ttu-id="23b33-181">可使用 `PackagePath="path"` 修改 .nupkg 内的包布局。</span><span class="sxs-lookup"><span data-stu-id="23b33-181">Package layout inside the .nupkg can be modified with `PackagePath="path"`.</span></span>

<span data-ttu-id="23b33-182">除 `Content` 外，大多数项组需要显式添加要包括在包中的 `Pack="true"`。</span><span class="sxs-lookup"><span data-stu-id="23b33-182">Except for `Content`, most item groups require explicitly adding `Pack="true"` to be included in the package.</span></span> <span data-ttu-id="23b33-183">`Content` 将被置于包中的 *content* 文件夹，因为 `<IncludeContentInPack>` 属性默认设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="23b33-183">`Content` will be put in the *content* folder in a package since the MSBuild `<IncludeContentInPack>` property is set to `true` by default.</span></span>
<span data-ttu-id="23b33-184">有关详细信息，请参阅[在包中包含内容](/nuget/schema/msbuild-targets#including-content-in-a-package)。</span><span class="sxs-lookup"><span data-stu-id="23b33-184">For more information, see [Including content in a package](/nuget/schema/msbuild-targets#including-content-in-a-package).</span></span>

<span data-ttu-id="23b33-185">`PackagePath="%(Identity)"` 是一种将包路径设置为项目相对文件路径的快捷方法。</span><span class="sxs-lookup"><span data-stu-id="23b33-185">`PackagePath="%(Identity)"` is a short way of setting package path to the project-relative file path.</span></span>

## <a name="testrunner"></a><span data-ttu-id="23b33-186">testRunner</span><span class="sxs-lookup"><span data-stu-id="23b33-186">testRunner</span></span>

### <a name="xunit"></a><span data-ttu-id="23b33-187">xUnit</span><span class="sxs-lookup"><span data-stu-id="23b33-187">xUnit</span></span>

```json
{
  "testRunner": "xunit",
  "dependencies": {
    "dotnet-test-xunit": "<any>"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-*" />
  <PackageReference Include="xunit" Version="2.2.0-*" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0-*" />
</ItemGroup>
```

### <a name="mstest"></a><span data-ttu-id="23b33-188">MSTest</span><span class="sxs-lookup"><span data-stu-id="23b33-188">MSTest</span></span>

```json
{
  "testRunner": "mstest",
  "dependencies": {
    "dotnet-test-mstest": "<any>"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-*" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.12-*" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.11-*" />
</ItemGroup>
```

## <a name="see-also"></a><span data-ttu-id="23b33-189">请参阅</span><span class="sxs-lookup"><span data-stu-id="23b33-189">See also</span></span>

- [<span data-ttu-id="23b33-190">CLI 中更改的简要概述</span><span class="sxs-lookup"><span data-stu-id="23b33-190">High-level overview of changes in CLI</span></span>](cli-msbuild-architecture.md)
