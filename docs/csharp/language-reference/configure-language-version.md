---
title: C# 语言版本控制 - C# 指南
description: 了解如何根据项目确定 C# 语言版本，以及背后的原因。 了解如何手动重写默认值。
ms.custom: updateeachrelease
ms.date: 08/11/2020
ms.openlocfilehash: 327a98da37b97830ac7f752a3621a92d8cb161e0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495455"
---
# <a name="c-language-versioning"></a><span data-ttu-id="88c2e-104">C# 语言版本控制</span><span class="sxs-lookup"><span data-stu-id="88c2e-104">C# language versioning</span></span>

<span data-ttu-id="88c2e-105">最新的 C# 编译器根据项目的一个或多个目标框架确定默认语言版本。</span><span class="sxs-lookup"><span data-stu-id="88c2e-105">The latest C# compiler determines a default language version based on your project's target framework or frameworks.</span></span> <span data-ttu-id="88c2e-106">Visual Studio 不提供用于更改值的 UI，但可以通过编辑 .csproj 文件来更改值。</span><span class="sxs-lookup"><span data-stu-id="88c2e-106">Visual Studio doesn't provide a UI to change the value, but you can change it by editing the *csproj* file.</span></span> <span data-ttu-id="88c2e-107">此默认选择可确保使用与目标框架兼容的最新语言版本。</span><span class="sxs-lookup"><span data-stu-id="88c2e-107">The choice of default ensures that you use the latest language version compatible with your target framework.</span></span> <span data-ttu-id="88c2e-108">你将从访问与项目目标兼容的最新语言功能中受益。</span><span class="sxs-lookup"><span data-stu-id="88c2e-108">You benefit from access to the latest language features compatible with your project's target.</span></span> <span data-ttu-id="88c2e-109">此默认选择还可确保不会使用需要类型或运行时行为在目标框架中不可用的语言。</span><span class="sxs-lookup"><span data-stu-id="88c2e-109">This default choice also ensures you don't use a language that requires types or runtime behavior not available in your target framework.</span></span> <span data-ttu-id="88c2e-110">选择比默认版本更高的语言版本可能导致难以诊断编译时和运行时错误。</span><span class="sxs-lookup"><span data-stu-id="88c2e-110">Choosing a language version newer than the default can cause hard to diagnose compile-time and runtime errors.</span></span>

<span data-ttu-id="88c2e-111">本文中的规则适用于随 Visual Studio 2019 或 .NET SDK 一起提供的编译器。</span><span class="sxs-lookup"><span data-stu-id="88c2e-111">The rules in this article apply to the compiler delivered with Visual Studio 2019 or the .NET SDK.</span></span> <span data-ttu-id="88c2e-112">默认情况下，Visual Studio 2017 安装或早期 .NET Core SDK 版本中包含的 C# 编译器以 C# 7.0 为目标。</span><span class="sxs-lookup"><span data-stu-id="88c2e-112">The C# compilers that are part of the Visual Studio 2017 installation or earlier .NET Core SDK versions target C# 7.0 by default.</span></span>

<span data-ttu-id="88c2e-113">C# 8.0 仅在 .NET Core 3.x 及更高版本上受支持。</span><span class="sxs-lookup"><span data-stu-id="88c2e-113">C# 8.0 is supported only on .NET Core 3.x and newer versions.</span></span> <span data-ttu-id="88c2e-114">许多最新功能需要 .NET Core 3.x 中引入的库和运行时功能：</span><span class="sxs-lookup"><span data-stu-id="88c2e-114">Many of the newest features require library and runtime features introduced in .NET Core 3.x:</span></span>

- <span data-ttu-id="88c2e-115">[默认接口实现](../whats-new/csharp-8.md#default-interface-methods)需要使用 .NET Core 3.0 CLR 中的新功能。</span><span class="sxs-lookup"><span data-stu-id="88c2e-115">[Default interface implementation](../whats-new/csharp-8.md#default-interface-methods) requires new features in the .NET Core 3.0 CLR.</span></span>
- <span data-ttu-id="88c2e-116">[异步流](../whats-new/csharp-8.md#asynchronous-streams)需要使用新类型 <xref:System.IAsyncDisposable?displayProperty=nameWithType>、<xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType> 和 <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="88c2e-116">[Async streams](../whats-new/csharp-8.md#asynchronous-streams) require the new types <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>, and <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="88c2e-117">[索引和范围](../whats-new/csharp-8.md#indices-and-ranges)需要使用新类型 <xref:System.Index?displayProperty=nameWithType> 和 <xref:System.Range?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="88c2e-117">[Indices and ranges](../whats-new/csharp-8.md#indices-and-ranges) require the new types <xref:System.Index?displayProperty=nameWithType> and <xref:System.Range?displayProperty=nameWithType>.</span></span>
- <span data-ttu-id="88c2e-118">[可为 null 的引用类型](../whats-new/csharp-8.md#nullable-reference-types)利用几个[特性](attributes/nullable-analysis.md)来提供更准确的警告。</span><span class="sxs-lookup"><span data-stu-id="88c2e-118">[Nullable reference types](../whats-new/csharp-8.md#nullable-reference-types) make use of several [attributes](attributes/nullable-analysis.md) to provide better warnings.</span></span> <span data-ttu-id="88c2e-119">这些特性是在 .NET Core 3.0 中添加的。</span><span class="sxs-lookup"><span data-stu-id="88c2e-119">Those attributes were added in .NET Core 3.0.</span></span> <span data-ttu-id="88c2e-120">其他目标框架并未使用这些特性中的任何一种进行批注。</span><span class="sxs-lookup"><span data-stu-id="88c2e-120">Other target frameworks haven't been annotated with any of these attributes.</span></span> <span data-ttu-id="88c2e-121">这意味着可为 null 的警告可能无法准确反映潜在问题。</span><span class="sxs-lookup"><span data-stu-id="88c2e-121">That means nullable warnings may not accurately reflect potential issues.</span></span>

<span data-ttu-id="88c2e-122">C# 9.0 仅在 .NET 5 及更高版本上受支持。</span><span class="sxs-lookup"><span data-stu-id="88c2e-122">C# 9.0 is supported only on .NET 5 and newer versions.</span></span>

## <a name="defaults"></a><span data-ttu-id="88c2e-123">默认值</span><span class="sxs-lookup"><span data-stu-id="88c2e-123">Defaults</span></span>

<span data-ttu-id="88c2e-124">编译器根据以下规则确定默认值：</span><span class="sxs-lookup"><span data-stu-id="88c2e-124">The compiler determines a default based on these rules:</span></span>

| <span data-ttu-id="88c2e-125">目标框架</span><span class="sxs-lookup"><span data-stu-id="88c2e-125">Target framework</span></span> | <span data-ttu-id="88c2e-126">version</span><span class="sxs-lookup"><span data-stu-id="88c2e-126">version</span></span> | <span data-ttu-id="88c2e-127">C# 语言版本的默认值</span><span class="sxs-lookup"><span data-stu-id="88c2e-127">C# language version default</span></span> |
|------------------|---------|-----------------------------|
| <span data-ttu-id="88c2e-128">.NET</span><span class="sxs-lookup"><span data-stu-id="88c2e-128">.NET</span></span>             | <span data-ttu-id="88c2e-129">5.x</span><span class="sxs-lookup"><span data-stu-id="88c2e-129">5.x</span></span>     | <span data-ttu-id="88c2e-130">C# 9.0</span><span class="sxs-lookup"><span data-stu-id="88c2e-130">C# 9.0</span></span>                      |
| <span data-ttu-id="88c2e-131">.NET Core</span><span class="sxs-lookup"><span data-stu-id="88c2e-131">.NET Core</span></span>        | <span data-ttu-id="88c2e-132">3.x</span><span class="sxs-lookup"><span data-stu-id="88c2e-132">3.x</span></span>     | <span data-ttu-id="88c2e-133">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="88c2e-133">C# 8.0</span></span>                      |
| <span data-ttu-id="88c2e-134">.NET Core</span><span class="sxs-lookup"><span data-stu-id="88c2e-134">.NET Core</span></span>        | <span data-ttu-id="88c2e-135">2.x</span><span class="sxs-lookup"><span data-stu-id="88c2e-135">2.x</span></span>     | <span data-ttu-id="88c2e-136">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="88c2e-136">C# 7.3</span></span>                      |
| <span data-ttu-id="88c2e-137">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="88c2e-137">.NET Standard</span></span>    | <span data-ttu-id="88c2e-138">2.1</span><span class="sxs-lookup"><span data-stu-id="88c2e-138">2.1</span></span>     | <span data-ttu-id="88c2e-139">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="88c2e-139">C# 8.0</span></span>                      |
| <span data-ttu-id="88c2e-140">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="88c2e-140">.NET Standard</span></span>    | <span data-ttu-id="88c2e-141">2.0</span><span class="sxs-lookup"><span data-stu-id="88c2e-141">2.0</span></span>     | <span data-ttu-id="88c2e-142">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="88c2e-142">C# 7.3</span></span>                      |
| <span data-ttu-id="88c2e-143">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="88c2e-143">.NET Standard</span></span>    | <span data-ttu-id="88c2e-144">1.x</span><span class="sxs-lookup"><span data-stu-id="88c2e-144">1.x</span></span>     | <span data-ttu-id="88c2e-145">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="88c2e-145">C# 7.3</span></span>                      |
| <span data-ttu-id="88c2e-146">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="88c2e-146">.NET Framework</span></span>   | <span data-ttu-id="88c2e-147">全部</span><span class="sxs-lookup"><span data-stu-id="88c2e-147">all</span></span>     | <span data-ttu-id="88c2e-148">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="88c2e-148">C# 7.3</span></span>                      |

<span data-ttu-id="88c2e-149">如果你的项目是以具有相应预览语言版本的预览框架为目标，那么使用的语言版本是预览语言版本。</span><span class="sxs-lookup"><span data-stu-id="88c2e-149">When your project targets a preview framework that has a corresponding preview language version, the language version used is the preview language version.</span></span> <span data-ttu-id="88c2e-150">你可在任何环境中使用该预览版提供的最新功能，而不会影响面向已发布 .NET Core 版本的项目。</span><span class="sxs-lookup"><span data-stu-id="88c2e-150">You use the latest features with that preview in any environment, without affecting projects that target a released .NET Core version.</span></span>

> [!TIP]
> <span data-ttu-id="88c2e-151">若要了解当前使用的语言版本，请在代码中添加 `#error version`（区分大小写）。</span><span class="sxs-lookup"><span data-stu-id="88c2e-151">To know what language version you're currently using, put `#error version` (case sensitive) in your code.</span></span> <span data-ttu-id="88c2e-152">这样做可使编译器生成诊断 CS8304，并显示一条消息，其中包含正在使用的编译器版本和当前选择的语言版本。</span><span class="sxs-lookup"><span data-stu-id="88c2e-152">This makes the compiler produce a diagnostic, CS8304, with a message containing the compiler version being used and the current selected language version.</span></span>

## <a name="override-a-default"></a><span data-ttu-id="88c2e-153">替代默认值</span><span class="sxs-lookup"><span data-stu-id="88c2e-153">Override a default</span></span>

<span data-ttu-id="88c2e-154">如果必须明确指定 C# 版本，可以通过以下几种方式实现：</span><span class="sxs-lookup"><span data-stu-id="88c2e-154">If you must specify your C# version explicitly, you can do so in several ways:</span></span>

- <span data-ttu-id="88c2e-155">手动编辑[项目文件](#edit-the-project-file)。</span><span class="sxs-lookup"><span data-stu-id="88c2e-155">Manually edit your [project file](#edit-the-project-file).</span></span>
- <span data-ttu-id="88c2e-156">为[子目录中的多个项目](#configure-multiple-projects)设置语言版本。</span><span class="sxs-lookup"><span data-stu-id="88c2e-156">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="88c2e-157">配置 [`-langversion` 编译器选项](compiler-options/langversion-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="88c2e-157">Configure the [`-langversion` compiler option](compiler-options/langversion-compiler-option.md).</span></span>

### <a name="edit-the-project-file"></a><span data-ttu-id="88c2e-158">编辑项目文件</span><span class="sxs-lookup"><span data-stu-id="88c2e-158">Edit the project file</span></span>

<span data-ttu-id="88c2e-159">可在项目文件中设置语言版本。</span><span class="sxs-lookup"><span data-stu-id="88c2e-159">You can set the language version in your project file.</span></span> <span data-ttu-id="88c2e-160">例如，如果你明确希望访问预览功能，请添加如下元素：</span><span class="sxs-lookup"><span data-stu-id="88c2e-160">For example, if you explicitly want access to preview features, add an element like this:</span></span>

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="88c2e-161">值 `preview` 使用编译器支持的最新可用的预览 C# 语言版本。</span><span class="sxs-lookup"><span data-stu-id="88c2e-161">The value `preview` uses the latest available preview C# language version that your compiler supports.</span></span>

### <a name="configure-multiple-projects"></a><span data-ttu-id="88c2e-162">配置多个项目</span><span class="sxs-lookup"><span data-stu-id="88c2e-162">Configure multiple projects</span></span>

<span data-ttu-id="88c2e-163">若要配置多个目录，可以创建包含 `<LangVersion>` 元素的 Directory.Build.props 文件。</span><span class="sxs-lookup"><span data-stu-id="88c2e-163">To configure multiple projects, you can create a **Directory.Build.props** file that contains the `<LangVersion>` element.</span></span> <span data-ttu-id="88c2e-164">通常是在解决方案目录中完成这件事。</span><span class="sxs-lookup"><span data-stu-id="88c2e-164">You typically do that in your solution directory.</span></span> <span data-ttu-id="88c2e-165">将以下内容添加到解决方案目录中的 Directory.Build.props 文件：</span><span class="sxs-lookup"><span data-stu-id="88c2e-165">Add the following to a **Directory.Build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="88c2e-166">包含该文件的目录的所有子目录中的版本都将使用 C# 预览版。</span><span class="sxs-lookup"><span data-stu-id="88c2e-166">Builds in all subdirectories of the directory containing that file will use the preview C# version.</span></span> <span data-ttu-id="88c2e-167">有关详细信息，请参阅关于[自定义生成](/visualstudio/msbuild/customize-your-build)的文章。</span><span class="sxs-lookup"><span data-stu-id="88c2e-167">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="c-language-version-reference"></a><span data-ttu-id="88c2e-168">C# 语言版本引用</span><span class="sxs-lookup"><span data-stu-id="88c2e-168">C# language version reference</span></span>

<span data-ttu-id="88c2e-169">下表显示当前所有 C# 语言版本。</span><span class="sxs-lookup"><span data-stu-id="88c2e-169">The following table shows all current C# language versions.</span></span> <span data-ttu-id="88c2e-170">如果编译器较旧，它可能不一定能识别每个值。</span><span class="sxs-lookup"><span data-stu-id="88c2e-170">Your compiler may not necessarily understand every value if it's older.</span></span> <span data-ttu-id="88c2e-171">如果安装的是 .NET Core 3.0 或更高版本，则可以访问列出的所有内容。</span><span class="sxs-lookup"><span data-stu-id="88c2e-171">If you install .NET Core 3.0 or later, then you have access to everything listed.</span></span>

[!INCLUDE [langversion-table](includes/langversion-table.md)]

> [!TIP]
> <span data-ttu-id="88c2e-172">打开 [Visual Studio 的开发人员命令提示](../../framework/tools/developer-command-prompt-for-vs.md)，运行以下命令以查看计算机上可用的语言版本列表。</span><span class="sxs-lookup"><span data-stu-id="88c2e-172">Open the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), and run the following command to see the listing of language versions available on your machine.</span></span>
>
> ```CMD
> csc -langversion:?
> ```
>
> <span data-ttu-id="88c2e-173">质疑此类 [-langversion](compiler-options/langversion-compiler-option.md) 编译选项时，将打印类似于下面的内容：</span><span class="sxs-lookup"><span data-stu-id="88c2e-173">Questioning the [-langversion](compiler-options/langversion-compiler-option.md) compile option like this, will print something similar to the following:</span></span>
>
> ```CMD
> Supported language versions:
> default
> 1
> 2
> 3
> 4
> 5
> 6
> 7.0
> 7.1
> 7.2
> 7.3
> 8.0 (default)
> latestmajor
> preview
> latest
> ```
