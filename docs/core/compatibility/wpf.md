---
title: WPF 中断性变更
description: 列出适用于 .NET Core 和 .NET 5 的 Windows Presentation Framework 中的中断性变更。
ms.date: 09/08/2020
ms.openlocfilehash: 3bd5cb585509118fbc3ca9ca08c6ed15b4853b93
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679300"
---
# <a name="breaking-changes-in-windows-presentation-framework-wpf"></a><span data-ttu-id="44546-103">Windows Presentation Framework (WPF) 中的中断性变更</span><span class="sxs-lookup"><span data-stu-id="44546-103">Breaking changes in Windows Presentation Framework (WPF)</span></span>

<span data-ttu-id="44546-104">WPF 支持已添加到版本 3.0 中的 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="44546-104">WPF support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="44546-105">本文按引入了中断性变更的 .NET 版本列出了 WPF 的中断性变更。</span><span class="sxs-lookup"><span data-stu-id="44546-105">This article lists breaking changes for WPF by the .NET version in which they were introduced.</span></span> <span data-ttu-id="44546-106">如果要从 .NET Framework 或 .NET Core 的早期版本（3.0 或更高版本）升级 WPF 应用，本文能为你提供帮助。</span><span class="sxs-lookup"><span data-stu-id="44546-106">If you're upgrading a WPF app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="44546-107">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="44546-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="44546-108">重大更改</span><span class="sxs-lookup"><span data-stu-id="44546-108">Breaking change</span></span> | <span data-ttu-id="44546-109">引入的版本</span><span class="sxs-lookup"><span data-stu-id="44546-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="44546-110">对于 WPF 和 WinForms 应用，OutputType 设置为 WinExe</span><span class="sxs-lookup"><span data-stu-id="44546-110">OutputType set to WinExe for WPF and WinForms apps</span></span>](#outputtype-set-to-winexe-for-wpf-and-winforms-apps) | <span data-ttu-id="44546-111">5.0</span><span class="sxs-lookup"><span data-stu-id="44546-111">5.0</span></span> |
| [<span data-ttu-id="44546-112">WinForms 和 WPF 应用使用 Microsoft.NET.Sdk</span><span class="sxs-lookup"><span data-stu-id="44546-112">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>](#winforms-and-wpf-apps-use-microsoftnetsdk) | <span data-ttu-id="44546-113">5.0</span><span class="sxs-lookup"><span data-stu-id="44546-113">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="44546-114">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="44546-114">.NET 5.0</span></span>

[!INCLUDE [automatically-infer-winexe-output-type](../../../includes/core-changes/windowsforms/5.0/automatically-infer-winexe-output-type.md)]

***

[!INCLUDE [sdk-and-target-framework-change](../../../includes/core-changes/windowsforms/5.0/sdk-and-target-framework-change.md)]

***
