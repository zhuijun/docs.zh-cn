---
title: 单文件应用程序
description: 了解单文件应用程序的本质以及应考虑使用此应用程序部署模型的原因。
author: lakshanf
ms.author: lakshanf
ms.date: 08/28/2020
ms.openlocfilehash: 795ea98a9fd9d672b199eb2d9b24151340ef8246
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495742"
---
# <a name="single-file-deployment-and-executable"></a>单文件部署和可执行文件

通过将所有依赖应用程序的文件捆绑到一个二进制文件中，为应用程序开发人员提供一个具有吸引力的选项，那就是将应用程序作为单个文件进行部署和分发。 此部署模型从 .NET Core 3.0 开始提供，在 .NET 5.0 中进行了增强。 之前在 .NET Core 3.0 中，当用户运行单文件应用时，.NET Core 主机先将所有文件提取到一个临时目录，然后再运行该应用程序。 .NET 5.0 改进了这一体验，它可直接运行代码，无需从应用中提取文件。

单文件部署可用于[依赖框架的部署模型](index.md#publish-framework-dependent)和[独立应用程序](index.md#publish-self-contained)。 独立应用程序中单个文件的大小很大，因为它包含运行时和框架库。 单文件部署选项可与 [ReadyToRun](../tools/dotnet-publish.md) 和 [Trim（.NET 5.0 中的一项试验功能）](trim-self-contained.md)发布选项结合使用。

使用单文件时需要注意一些事项，首先是使用路径信息来查找相对于应用程序的位置的文件。 <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> API 将返回空字符串，这是从内存中加载的程序集的默认行为。 编译器将在生成时提供此 API 的警告，提醒开发人员注意特定行为。 如果需要应用程序目录的路径，则 <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> API 将返回 AppHost（单文件捆绑包本身）所在的目录。 托管的 C++ 应用程序不太适合进行单文件部署，建议使用 C# 编写应用程序来使单文件兼容。

默认情况下，单文件不捆绑本机库。 在 Linux 上，我们将运行时预链接到捆绑包中，并且仅将应用程序本机库部署到单文件应用所在的目录中。 在 Windows 上，我们仅预链接托管代码，而且运行时库和应用程序本机库都部署到单文件应用所在的目录中。 目的是确保提供良好的调试体验，这要求将本机文件从单文件中排除。 可选择设置标志 `IncludeNativeLibrariesForSelfExtract`，从而在单文件捆绑包中包含本机库，但在运行单文件应用程序时，这些文件将被提取到客户端计算机上的临时目录中。

## <a name="exclude-files-from-being-embedded"></a>将文件排除在嵌入之外

通过设置以下元数据，可明确指定不在单文件中嵌入某些文件：

```xml
<ExcludeFromSingleFile>true</ExcludeFromSingleFile>
```

例如，若要将某些文件放置在发布目录中，但不将它们捆绑到单文件中：

```xml
<ItemGroup>
  <Content Update="Plugin.dll">
    <CopyToPublishDirectory>PreserveNewest</CopyToPublishDirectory>
    <ExcludeFromSingleFile>true</ExcludeFromSingleFile>
  </Content>
</ItemGroup>
```

## <a name="publish-a-single-file-app---cli"></a>发布单文件应用 - CLI

使用 [dotnet publish](../tools/dotnet-publish.md) 命令发布单文件应用程序。 发布应用时，请设置以下属性：

- 针对特定运行时进行发布：`-r win-x64`
- 作为单个文件进行发布：`-p:PublishSingleFile=true`

以下示例将 Windows 应用作为独立的单文件应用程序发布。

```dotnetcli
dotnet publish -r win-x64 -p:PublishSingleFile=true --self-contained true
```

以下示例将 Linux 应用作为依赖框架的单文件应用程序发布。

```dotnetcli
dotnet publish -r linux-x64 -p:PublishSingleFile=true --self-contained false
```

有关详细信息，请参阅[使用 .NET Core CLI 发布 .NET Core 应用](deploy-with-cli.md)。

## <a name="publish-a-single-file-app---visual-studio"></a>发布单文件应用 - Visual Studio

Visual Studio 创建可重用的发布配置文件，用于控制应用程序的发布方式。

01. 在“解决方案资源管理器”窗格中，右键单击要发布的项目  。 选择“发布”。

    :::image type="content" source="media/single-file/visual-studio-solution-explorer.png" alt-text="解决方案资源管理器，其中右键单击菜单突出显示了“发布”选项。":::

    如果还没有发布配置文件，请按照说明创建一个并选择“文件夹”目标类型  。

01. 选择“编辑”  。

    :::image type="content" source="media/single-file/visual-studio-publish-edit-settings.png" alt-text="带有“编辑”按钮的 Visual Studio 发布配置文件。":::

01. 在“配置文件设置”对话框中，设置以下选项  ：

    - 将“部署模式”设置为“自包含”   。
    - 将“目标运行时”设置为要发布到的平台  。
    - 选择“生成单个文件”。

    选择“保存”保存设置并返回到“发布”对话框   。

    :::image type="content" source="media/single-file/visual-studio-publish-single-file-properties.png" alt-text="“配置文件设置”对话框，其中突出显示了“部署模式”、“目标运行时”和“单个文件”选项。":::

01. 选择“发布”，将应用作为单个文件发布。

有关详细信息，请参阅[使用 Visual Studio 发布 .NET Core 应用](deploy-with-vs.md)。

## <a name="publish-a-single-file-app---visual-studio-for-mac"></a>发布单文件应用 - Visual Studio for Mac

Visual Studio for Mac 不提供将应用作为单个文件发布的选项。 你需要按照[发布单文件应用 - CLI](#publish-a-single-file-app---cli) 部分中的说明手动发布。 有关详细信息，请参阅[使用 .NET Core CLI 发布 .NET Core 应用](deploy-with-cli.md)。

## <a name="see-also"></a>请参阅

- [.NET Core 应用程序部署](index.md)。
- [使用 .NET Core CLI 发布 .NET Core 应用](deploy-with-cli.md)。
- [使用 Visual Studio 发布 .NET Core 应用](deploy-with-vs.md)。
- [`dotnet publish` 命令](../tools/dotnet-publish.md)。
