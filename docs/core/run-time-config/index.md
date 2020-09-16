---
title: 运行时配置选项
description: 了解如何使用运行时配置设置来配置 .NET Core 应用程序。
ms.date: 01/21/2020
ms.openlocfilehash: 21673a221d0f21202febf4730b955da66132d5f7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538193"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="79236-103">.NET Core 运行时配置设置</span><span class="sxs-lookup"><span data-stu-id="79236-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="79236-104">.NET Core 支持使用配置文件和环境变量在运行时配置 .NET Core 应用程序的行为。</span><span class="sxs-lookup"><span data-stu-id="79236-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="79236-105">如果出现以下情况，则运行时配置是一个不错的选择：</span><span class="sxs-lookup"><span data-stu-id="79236-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="79236-106">你不拥有或控制应用程序的源代码，因此无法以编程方式对其进行配置。</span><span class="sxs-lookup"><span data-stu-id="79236-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="79236-107">应用程序的多个实例在单个系统上同时运行，并且你想要将每个实例配置为获得最佳性能。</span><span class="sxs-lookup"><span data-stu-id="79236-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="79236-108">本文档正在编写中。</span><span class="sxs-lookup"><span data-stu-id="79236-108">This documentation is a work in progress.</span></span> <span data-ttu-id="79236-109">如果你注意到此处提供的信息不完整或不准确，可以[创建一个问题](https://github.com/dotnet/docs/issues)告知我们，或[提交拉取请求](https://github.com/dotnet/docs/pulls)以解决问题。</span><span class="sxs-lookup"><span data-stu-id="79236-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="79236-110">要了解如何提交 dotnet/docs 存储库的拉取请求，请参阅[参与者指南](/contribute/dotnet/dotnet-contribute)。</span><span class="sxs-lookup"><span data-stu-id="79236-110">For information about submitting pull requests for the dotnet/docs repository, see the [contributor's guide](/contribute/dotnet/dotnet-contribute).</span></span>

<span data-ttu-id="79236-111">.NET Core 提供了以下机制，它们可用于配置运行时应用程序行为：</span><span class="sxs-lookup"><span data-stu-id="79236-111">.NET Core provides the following mechanisms for configuring application behavior at run time:</span></span>

- <span data-ttu-id="79236-112">[runtimeconfig.json 文件](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="79236-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="79236-113">MSBuild 属性</span><span class="sxs-lookup"><span data-stu-id="79236-113">MSBuild properties</span></span>](#msbuild-properties)

- [<span data-ttu-id="79236-114">环境变量</span><span class="sxs-lookup"><span data-stu-id="79236-114">Environment variables</span></span>](#environment-variables)

> [!TIP]
> <span data-ttu-id="79236-115">如果使用环境变量配置运行时选项，会将设置应用于所有 .NET Core 应用。</span><span class="sxs-lookup"><span data-stu-id="79236-115">Configuring a run-time option by using an environment variable applies the setting to all .NET Core apps.</span></span> <span data-ttu-id="79236-116">如果在 runtimeconfig.json 或项目文件中配置运行时选择，则仅将设置应用于此应用程序。</span><span class="sxs-lookup"><span data-stu-id="79236-116">Configuring a run-time option in the *runtimeconfig.json* or project file applies the setting to that application only.</span></span>

<span data-ttu-id="79236-117">某些配置值还可以通过调用 <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> 方法以编程方式进行设置。</span><span class="sxs-lookup"><span data-stu-id="79236-117">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="79236-118">文档此部分的文章按类别组织，例如[调试](debugging-profiling.md)和[垃圾回收](garbage-collector.md)。</span><span class="sxs-lookup"><span data-stu-id="79236-118">The articles in this section of the documentation are organized by category, for example, [debugging](debugging-profiling.md) and [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="79236-119">如果适用，将显示 runtimeconfig.json 文件、MSBuild 属性、环境变量的配置选项；对于 .NET Framework 项目，还会显示 app.config 文件的配置选项以便交叉引用。 </span><span class="sxs-lookup"><span data-stu-id="79236-119">Where applicable, configuration options are shown for *runtimeconfig.json* files, MSBuild properties, environment variables, and, for cross-reference, *app.config* files for .NET Framework projects.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="79236-120">runtimeconfig.json</span><span class="sxs-lookup"><span data-stu-id="79236-120">runtimeconfig.json</span></span>

<span data-ttu-id="79236-121">[构建](../tools/dotnet-build.md)项目时，将在输出目录中生成 *[appname].runtimeconfig.json* 文件。</span><span class="sxs-lookup"><span data-stu-id="79236-121">When a project is [built](../tools/dotnet-build.md), an *[appname].runtimeconfig.json* file is generated in the output directory.</span></span> <span data-ttu-id="79236-122">如果项目文件所在的文件夹中存在 *runtimeconfig.template.json* 文件，它包含的任何配置选项都将合并到 *[appname].runtimeconfig.json* 文件中。</span><span class="sxs-lookup"><span data-stu-id="79236-122">If a *runtimeconfig.template.json* file exists in the same folder as the project file, any configuration options it contains are merged into the *[appname].runtimeconfig.json* file.</span></span> <span data-ttu-id="79236-123">如果自行构建应用，请将所有配置选项放在 *runtimeconfig.template.json* 文件中。</span><span class="sxs-lookup"><span data-stu-id="79236-123">If you're building the app yourself, put any configuration options in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="79236-124">如果只是运行应用，请将其直接插入 [appname].runtimeconfig.template.json 文件中。</span><span class="sxs-lookup"><span data-stu-id="79236-124">If you're just running the app, insert them directly into the *[appname].runtimeconfig.json* file.</span></span>

> [!NOTE]
> <span data-ttu-id="79236-125">后续生成中将覆盖 [appname].runtimeconfig.template.json 文件。</span><span class="sxs-lookup"><span data-stu-id="79236-125">The *[appname].runtimeconfig.json* file will get overwritten on subsequent builds.</span></span>

<span data-ttu-id="79236-126">在 runtimeconfig.json 文件的 configProperties 部分指定运行时配置选项。</span><span class="sxs-lookup"><span data-stu-id="79236-126">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* files.</span></span> <span data-ttu-id="79236-127">此部分包含窗体：</span><span class="sxs-lookup"><span data-stu-id="79236-127">This section has the form:</span></span>

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a><span data-ttu-id="79236-128">示例 [appname].runtimeconfig.template.json 文件</span><span class="sxs-lookup"><span data-stu-id="79236-128">Example [appname].runtimeconfig.json file</span></span>

<span data-ttu-id="79236-129">如果要将这些选项放在输出 JSON 文件中，请将它们嵌套在 `runtimeOptions` 属性下。</span><span class="sxs-lookup"><span data-stu-id="79236-129">If you're placing the options in the output JSON file, nest them under the `runtimeOptions` property.</span></span>

```json
{
  "runtimeOptions": {
    "tfm": "netcoreapp3.1",
    "framework": {
      "name": "Microsoft.NETCore.App",
      "version": "3.1.0"
    },
    "configProperties": {
      "System.GC.Concurrent": false,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

### <a name="example-runtimeconfigtemplatejson-file"></a><span data-ttu-id="79236-130">示例 runtimeconfig.template.json 文件</span><span class="sxs-lookup"><span data-stu-id="79236-130">Example runtimeconfig.template.json file</span></span>

<span data-ttu-id="79236-131">如果要将这些选项放在模板 JSON 文件中，请省略 `runtimeOptions` 属性。</span><span class="sxs-lookup"><span data-stu-id="79236-131">If you're placing the options in the template JSON file, omit the `runtimeOptions` property.</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a><span data-ttu-id="79236-132">MSBuild 属性</span><span class="sxs-lookup"><span data-stu-id="79236-132">MSBuild properties</span></span>

<span data-ttu-id="79236-133">可以使用 SDK 样式 .NET Core 项目的 .csproj 或 .vbproj 文件中的 MSBuild 属性设置某些运行时配置选项。 </span><span class="sxs-lookup"><span data-stu-id="79236-133">Some run-time configuration options can be set using MSBuild properties in the *.csproj* or *.vbproj* file of SDK-style .NET Core projects.</span></span> <span data-ttu-id="79236-134">MSBuild 属性优先于在 *runtimeconfig.template.json* 文件中设置的选项。</span><span class="sxs-lookup"><span data-stu-id="79236-134">MSBuild properties take precedence over options set in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="79236-135">它们还会覆盖生成时在 [appname].runtimeconfig.json 文件中设置的任何选项。</span><span class="sxs-lookup"><span data-stu-id="79236-135">They also overwrite any options you set in the *[appname].runtimeconfig.json* file at build time.</span></span>

<span data-ttu-id="79236-136">下面是一个示例 SDK 样式项目文件，其中包含用于配置运行时行为的 MSBuild 属性：</span><span class="sxs-lookup"><span data-stu-id="79236-136">Here is an example SDK-style project file with MSBuild properties for configuring run-time behavior:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
    <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="79236-137">用于配置运行时行为的 MSBuild 属性记录在每个区域各自的文章中，例如[垃圾回收](garbage-collector.md)。</span><span class="sxs-lookup"><span data-stu-id="79236-137">MSBuild properties for configuring run-time behavior are noted in the individual articles for each area, for example, [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="79236-138">它们还在 SDK 样式项目的 MSBuild 属性参考的[运行时配置](../project-sdk/msbuild-props.md#run-time-configuration-properties)部分中列出。</span><span class="sxs-lookup"><span data-stu-id="79236-138">They are also listed in the [Run-time configuration](../project-sdk/msbuild-props.md#run-time-configuration-properties) section of the MSBuild properties reference for SDK-style projects.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="79236-139">环境变量</span><span class="sxs-lookup"><span data-stu-id="79236-139">Environment variables</span></span>

<span data-ttu-id="79236-140">环境变量可用于提供一些运行时配置信息。</span><span class="sxs-lookup"><span data-stu-id="79236-140">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="79236-141">如果使用环境变量配置运行时选项，会将设置应用于所有 .NET Core 应用。</span><span class="sxs-lookup"><span data-stu-id="79236-141">Configuring a run-time option by using an environment variable applies the setting to all .NET Core apps.</span></span> <span data-ttu-id="79236-142">指定为环境变量的配置旋钮通常有 COMPlus_ 前缀。</span><span class="sxs-lookup"><span data-stu-id="79236-142">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="79236-143">可以使用 Windows 控制面板、命令行或通过在 Windows 和 Unix 系统上调用 <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> 方法以编程方式定义环境变量。</span><span class="sxs-lookup"><span data-stu-id="79236-143">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="79236-144">下面的示例演示如何在命令行中设置环境变量：</span><span class="sxs-lookup"><span data-stu-id="79236-144">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
