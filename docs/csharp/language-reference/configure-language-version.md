---
title: C# 语言版本控制 - C# 指南
description: 了解如何根据项目确定 C# 语言版本，以及背后的原因。 了解如何手动重写默认值。
ms.custom: updateeachrelease
ms.date: 05/20/2020
ms.openlocfilehash: a27f3210f399f1bed190c18d778cf3824772d576
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656844"
---
# <a name="c-language-versioning"></a>C# 语言版本控制

最新的 C# 编译器根据项目的一个或多个目标框架确定默认语言版本。 Visual Studio 不提供用于更改值的 UI，但可以通过编辑 .csproj 文件来更改值。 此默认选择可确保使用与目标框架兼容的最新语言版本。 你将从访问与项目目标兼容的最新语言功能中受益。 此默认选择还可确保不会使用需要类型或运行时行为在目标框架中不可用的语言。 选择比默认版本更高的语言版本可能导致难以诊断编译时和运行时错误。

本文中的规则适用于随 Visual Studio 2019 或 .NET Core 3.0 SDK 一起提供的编译器。 默认情况下，Visual Studio 2017 安装或早期 .NET Core SDK 版本中包含的 C# 编译器以 C# 7.0 为目标。

C# 8.0（和更高版本）仅在 .NET Core 3.x 和更高版本上受支持。 许多最新功能需要 .NET Core 3.x 中引入的库和运行时功能：

- [默认接口实现](../whats-new/csharp-8.md#default-interface-methods)需要使用 .NET Core 3.0 CLR 中的新功能。
- [异步流](../whats-new/csharp-8.md#asynchronous-streams)需要使用新类型 <xref:System.IAsyncDisposable?displayProperty=nameWithType>、<xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType> 和 <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>。
- [索引和范围](../whats-new/csharp-8.md#indices-and-ranges)需要使用新类型 <xref:System.Index?displayProperty=nameWithType> 和 <xref:System.Range?displayProperty=nameWithType>。
- [可为 null 的引用类型](../whats-new/csharp-8.md#nullable-reference-types)利用几个[特性](attributes/nullable-analysis.md)来提供更准确的警告。 这些特性是在 .NET Core 3.0 中添加的。 其他目标框架并未使用这些特性中的任何一种进行批注。 这意味着可为 null 的警告可能无法准确反映潜在问题。

## <a name="defaults"></a>默认值

编译器根据以下规则确定默认值：

| 目标框架 | version | C# 语言版本的默认值 |
|------------------|---------|-----------------------------|
| .NET Core        | 3.x     | C# 8.0                      |
| .NET Core        | 2.x     | C# 7.3                      |
| .NET Standard    | 2.1     | C# 8.0                      |
| .NET Standard    | 2.0     | C# 7.3                      |
| .NET Standard    | 1.x     | C# 7.3                      |
| .NET Framework   | 全部     | C# 7.3                      |

如果你的项目是以具有相应预览语言版本的预览框架为目标，那么使用的语言版本是预览语言版本。 你可在任何环境中使用该预览版提供的最新功能，而不会影响面向已发布 .NET Core 版本的项目。

## <a name="override-a-default"></a>替代默认值

如果必须明确指定 C# 版本，可以通过以下几种方式实现：

- 手动编辑[项目文件](#edit-the-project-file)。
- 为[子目录中的多个项目](#configure-multiple-projects)设置语言版本。
- 配置 [`-langversion` 编译器选项](compiler-options/langversion-compiler-option.md)。

### <a name="edit-the-project-file"></a>编辑项目文件

可在项目文件中设置语言版本。 例如，如果你明确希望访问预览功能，请添加如下元素：

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

值 `preview` 使用编译器支持的最新可用的预览 C# 语言版本。

### <a name="configure-multiple-projects"></a>配置多个项目

若要配置多个目录，可以创建包含 `<LangVersion>` 元素的 Directory.Build.props 文件。 通常是在解决方案目录中完成这件事。 将以下内容添加到解决方案目录中的 Directory.Build.props 文件：

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

包含该文件的目录的所有子目录中的版本都将使用 C# 预览版。 有关详细信息，请参阅关于[自定义生成](/visualstudio/msbuild/customize-your-build)的文章。

## <a name="c-language-version-reference"></a>C# 语言版本引用

下表显示当前所有 C# 语言版本。 如果编译器较旧，它可能不一定能识别每个值。 如果安装的是 .NET Core 3.0 或更高版本，则可以访问列出的所有内容。

[!INCLUDE [langversion-table](includes/langversion-table.md)]

> [!TIP]
> 打开 [Visual Studio 的开发人员命令提示](../../framework/tools/developer-command-prompt-for-vs.md)，运行以下命令以查看计算机上可用的语言版本列表。
>
> ```CMD
> csc -langversion:?
> ```
>
> 质疑此类 [-langversion](compiler-options/langversion-compiler-option.md) 编译选项时，将打印类似于下面的内容：
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
