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
# <a name="msbuild-breaking-changes"></a><span data-ttu-id="14c59-103">MSBuild 中断性变更</span><span class="sxs-lookup"><span data-stu-id="14c59-103">MSBuild breaking changes</span></span>

<span data-ttu-id="14c59-104">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="14c59-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="14c59-105">重大更改</span><span class="sxs-lookup"><span data-stu-id="14c59-105">Breaking change</span></span> | <span data-ttu-id="14c59-106">引入的版本</span><span class="sxs-lookup"><span data-stu-id="14c59-106">Version introduced</span></span> |
| - | - |
| [<span data-ttu-id="14c59-107">面向 .NET 5 时，未定义 NETCOREAPP3_1 预处理器符号</span><span class="sxs-lookup"><span data-stu-id="14c59-107">NETCOREAPP3_1 preprocessor symbol is not defined when targeting .NET 5</span></span>](#netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5) | <span data-ttu-id="14c59-108">5.0</span><span class="sxs-lookup"><span data-stu-id="14c59-108">5.0</span></span> |
| [<span data-ttu-id="14c59-109">PublishDepsFilePath 行为变更</span><span class="sxs-lookup"><span data-stu-id="14c59-109">PublishDepsFilePath behavior change</span></span>](#publishdepsfilepath-behavior-change) | <span data-ttu-id="14c59-110">5.0</span><span class="sxs-lookup"><span data-stu-id="14c59-110">5.0</span></span> |
| [<span data-ttu-id="14c59-111">默认导入 Directory.Packages.props 文件</span><span class="sxs-lookup"><span data-stu-id="14c59-111">Directory.Packages.props files is imported by default</span></span>](#directorypackagesprops-files-is-imported-by-default) | <span data-ttu-id="14c59-112">5.0</span><span class="sxs-lookup"><span data-stu-id="14c59-112">5.0</span></span> |
| [<span data-ttu-id="14c59-113">资源清单文件名更改</span><span class="sxs-lookup"><span data-stu-id="14c59-113">Resource manifest file name change</span></span>](#resource-manifest-file-name-change) | <span data-ttu-id="14c59-114">3.0</span><span class="sxs-lookup"><span data-stu-id="14c59-114">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="14c59-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="14c59-115">.NET 5.0</span></span>

[!INCLUDE [netcoreapp3_1-preprocessor-symbol-not-defined](../../../includes/core-changes/msbuild/5.0/netcoreapp3_1-preprocessor-symbol-not-defined.md)]

***

[!INCLUDE [publishdepsfilepath-behavior-change](../../../includes/core-changes/msbuild/5.0/publishdepsfilepath-behavior-change.md)]

***

[!INCLUDE [directory-packages-props-imported-by-default](../../../includes/core-changes/msbuild/5.0/directory-packages-props-imported-by-default.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="14c59-116">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="14c59-116">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***
