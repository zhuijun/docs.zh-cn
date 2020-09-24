---
title: MSBuild 中断性变更
description: 列出 MSBuild for .NET Core 中的中断性变更。
ms.date: 02/10/2020
ms.openlocfilehash: 7493516dff68b8bd45740c9877ebf21886e667ff
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679315"
---
# <a name="msbuild-breaking-changes"></a>MSBuild 中断性变更

本页记录了以下中断性变更：

| 重大更改 | 引入的版本 |
| - | - |
| [PublishDepsFilePath 行为变更](#publishdepsfilepath-behavior-change) | 5.0 |
| [默认导入 Directory.Packages.props 文件](#directorypackagesprops-files-is-imported-by-default) | 5.0 |
| [资源清单文件名更改](#resource-manifest-file-name-change) | 3.0 |

## <a name="net-50"></a>.NET 5.0

[!INCLUDE [publishdepsfilepath-behavior-change](../../../includes/core-changes/msbuild/5.0/publishdepsfilepath-behavior-change.md)]

***

[!INCLUDE [directory-packages-props-imported-by-default](../../../includes/core-changes/msbuild/5.0/directory-packages-props-imported-by-default.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
