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
# <a name="msbuild-breaking-changes"></a><span data-ttu-id="4a252-103">MSBuild 中断性变更</span><span class="sxs-lookup"><span data-stu-id="4a252-103">MSBuild breaking changes</span></span>

<span data-ttu-id="4a252-104">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="4a252-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="4a252-105">重大更改</span><span class="sxs-lookup"><span data-stu-id="4a252-105">Breaking change</span></span> | <span data-ttu-id="4a252-106">引入的版本</span><span class="sxs-lookup"><span data-stu-id="4a252-106">Version introduced</span></span> |
| - | - |
| [<span data-ttu-id="4a252-107">PublishDepsFilePath 行为变更</span><span class="sxs-lookup"><span data-stu-id="4a252-107">PublishDepsFilePath behavior change</span></span>](#publishdepsfilepath-behavior-change) | <span data-ttu-id="4a252-108">5.0</span><span class="sxs-lookup"><span data-stu-id="4a252-108">5.0</span></span> |
| [<span data-ttu-id="4a252-109">默认导入 Directory.Packages.props 文件</span><span class="sxs-lookup"><span data-stu-id="4a252-109">Directory.Packages.props files is imported by default</span></span>](#directorypackagesprops-files-is-imported-by-default) | <span data-ttu-id="4a252-110">5.0</span><span class="sxs-lookup"><span data-stu-id="4a252-110">5.0</span></span> |
| [<span data-ttu-id="4a252-111">资源清单文件名更改</span><span class="sxs-lookup"><span data-stu-id="4a252-111">Resource manifest file name change</span></span>](#resource-manifest-file-name-change) | <span data-ttu-id="4a252-112">3.0</span><span class="sxs-lookup"><span data-stu-id="4a252-112">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="4a252-113">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="4a252-113">.NET 5.0</span></span>

[!INCLUDE [publishdepsfilepath-behavior-change](../../../includes/core-changes/msbuild/5.0/publishdepsfilepath-behavior-change.md)]

***

[!INCLUDE [directory-packages-props-imported-by-default](../../../includes/core-changes/msbuild/5.0/directory-packages-props-imported-by-default.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="4a252-114">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4a252-114">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
