---
title: .NET Framework 与 .NET Core 之间的差异
description: 介绍 Windows Presentation Foundation (WPF) 的 .NET Framework 实现与 .NET Core WPF 之间的差异。 迁移应用时，你应考虑以下不兼容性。
author: adegeo
ms.date: 09/21/2019
ms.author: adegeo
ms.openlocfilehash: 3bedc30046c36d4c5430feedf5854276ebaef8aa
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325688"
---
# <a name="differences-in-wpf"></a>WPF 中的差异

本文介绍了 .NET Core 上的 Windows Presentation Foundation (WPF) 与 .NET Framework 之间的差异。 WPF for .NET Core 是一个[开放源代码框架](https://github.com/dotnet/wpf)，它是从原始 WPF for .NET Framework 源代码派生而来的。

.NET Framework 有一些 .NET Core 不支持的功能。 关于不支持的技术的详细信息，请参阅 [.NET Framework 技术在 .NET Core 上不可用](../../core/porting/net-framework-tech-unavailable.md)。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a>SDK 样式项目

.NET Core 使用 SDK 样式项目文件。 这些项目文件与 Visual Studio 管理的传统 .NET Framework 项目文件不同。 要将 .NET Framework WPF 应用迁移到 .NET Core，必须转换项目。 有关详细信息，请参阅[将 WPF 应用迁移到 .NET Core 3.0](convert-project-from-net-framework.md)。

## <a name="nuget-package-references"></a>NuGet 包引用

如果 .NET Framework 应用在 packages.config  文件中列出其 NuGet 依赖项，请迁移为 [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) 格式：

1. 在 Visual Studio 中，打开“解决方案资源管理器”  窗格。
1. 在 WPF 项目中，右键单击“packages.config”   > “将 packages.config 迁移到 PackageReference”  。

![正在升级到 PackageReference](media/differences-from-net-framework/package-reference-migration.png)

将出现一个对话框，显示计算出的顶级 NuGet 依赖关系，并询问应将其他哪些 NuGet 包提升到顶级。 选择“确定”  ，然后将“packages.config”  文件从项目中删除，并将 `<PackageReference>` 元素添加到项目文件中。

当项目使用 `<PackageReference>` 时，包不会存储在本地“Packages”  文件夹中，而是全局存储。 打开项目文件，删除任何引用到“Packages”  文件夹的 `<Analyzer>` 元素。 这些分析器会自动包含在 NuGet 包引用中。

## <a name="code-access-security"></a>代码访问安全性

.NET Core 或 WPF for .NET Core 不支持代码访问安全性 (CAS)。 在完全信任的前提下，处理所有与 CAS 相关的功能。 WPF for .NET Core 会删除与 CAS 相关的代码。 这些类型的公共 API 表面仍然存在，以确保对这些类型的调用成功。

公开定义的 CAS 相关类型被移出 WPF 程序集，并移入 Core .NET 库程序集中。 WPF 程序集将类型转发设置为移动类型的新位置。

| 源程序集 | 目标程序集 | 类型                |
| --------------- | --------------- | ------------------- |
| *WindowsBase.dll* | *System.Security.Permissions.dll* | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| *System.Xaml.dll* | *System.Security.Permissions.dll* | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| *System.Xaml.dll* | *System.Windows.Extension.dll*    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> 为了最大限度地减少移植摩擦，`XamlAccessLevel` 类型中保留了用于存储和检索与以下属性有关的信息的功能。
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a>后续步骤

- [了解如何将 .NET Framework WPF 应用移植到 .NET Core。](convert-project-from-net-framework.md)
