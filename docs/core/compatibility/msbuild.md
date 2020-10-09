---
title: MSBuild 中断性变更
description: 列出 MSBuild for .NET Core 中的中断性变更。
ms.date: 02/10/2020
ms.openlocfilehash: b57c70d21e061c59f26b11a025d4d05ce3b8ca99
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654727"
---
# <a name="msbuild-breaking-changes"></a>MSBuild 中断性变更

本页记录了以下中断性变更：

| 重大更改 | 引入的版本 |
| - | - |
| [面向 .NET 5 时，未定义 NETCOREAPP3_1 预处理器符号](#netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5) | 5.0 |
| [PublishDepsFilePath 行为变更](#publishdepsfilepath-behavior-change) | 5.0 |
| [默认导入 Directory.Packages.props 文件](#directorypackagesprops-files-is-imported-by-default) | 5.0 |
| [资源清单文件名更改](#resource-manifest-file-name-change) | 3.0 |

## <a name="net-50"></a>.NET 5.0

[!INCLUDE [netcoreapp3_1-preprocessor-symbol-not-defined](../../../includes/core-changes/msbuild/5.0/netcoreapp3_1-preprocessor-symbol-not-defined.md)]

***

[!INCLUDE [publishdepsfilepath-behavior-change](../../../includes/core-changes/msbuild/5.0/publishdepsfilepath-behavior-change.md)]

***

[!INCLUDE [directory-packages-props-imported-by-default](../../../includes/core-changes/msbuild/5.0/directory-packages-props-imported-by-default.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
