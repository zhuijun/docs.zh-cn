---
title: 用于移植到 .NET Core 的工具
description: 了解可以用于移植到 .NET Core 的一些工具
author: cartermp
ms.date: 05/03/2020
ms.openlocfilehash: b8678ec72fe5d910d5f8cff4768106e7496f9276
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406123"
---
# <a name="tools-to-help-with-porting-to-net-core"></a><span data-ttu-id="41726-103">用于帮助移植到 .NET Core 的工具</span><span class="sxs-lookup"><span data-stu-id="41726-103">Tools to help with porting to .NET Core</span></span>

<span data-ttu-id="41726-104">你可能会发现本文中列出的工具在移植时非常有用：</span><span class="sxs-lookup"><span data-stu-id="41726-104">You may find the tools listed in this article helpful when porting:</span></span>

- <span data-ttu-id="41726-105">[.NET 可移植性分析器](../../standard/analyzers/portability-analyzer.md) - 可以生成报告的工具链，该报告说明代码在 .NET Framework 和 .NET Core 之间的可移植性：</span><span class="sxs-lookup"><span data-stu-id="41726-105">[.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) - A toolchain that can generate a report of how portable your code is between .NET Framework and .NET Core:</span></span>
  - <span data-ttu-id="41726-106">作为[命令行工具](https://github.com/Microsoft/dotnet-apiport/releases)</span><span class="sxs-lookup"><span data-stu-id="41726-106">As a [command-line tool](https://github.com/Microsoft/dotnet-apiport/releases)</span></span>
  - <span data-ttu-id="41726-107">作为 [Visual Studio 扩展](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span><span class="sxs-lookup"><span data-stu-id="41726-107">As a [Visual Studio extension](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)</span></span>
- <span data-ttu-id="41726-108">[平台兼容性分析器](../../standard/analyzers/platform-compat-analyzer.md) - 一种 Roslyn 分析器，如果开发人员在 API 可能不可用时使用来自调用站点的平台专用 API，它会通知开发人员。</span><span class="sxs-lookup"><span data-stu-id="41726-108">[Platform compatibility analyzer](../../standard/analyzers/platform-compat-analyzer.md) - A Roslyn analyzer that informs developers when they use platform-specific APIs from call sites where the API might not be available.</span></span>
- <span data-ttu-id="41726-109">[.NET API 分析器](../../standard/analyzers/api-analyzer.md) - 一种 Roslyn 分析器，可帮助检测跨平台应用和库中的平台兼容性问题。</span><span class="sxs-lookup"><span data-stu-id="41726-109">[.NET API analyzer](../../standard/analyzers/api-analyzer.md) - A Roslyn analyzer that can help detect platform compatibility issues in cross-platform apps and libraries.</span></span>
- <span data-ttu-id="41726-110">[try-convert](https://www.nuget.org/packages/try-convert/) - .NET Core 全局工具，可用于将项目或整个解决方案转换为 .NET SDK，包括将桌面应用迁移到 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="41726-110">[try-convert](https://www.nuget.org/packages/try-convert/) - A .NET Core global tool that can convert a project or entire solution to the .NET SDK, including moving desktop apps to .NET Core.</span></span> <span data-ttu-id="41726-111">如果创建了更复杂的生成（如自定义任务、目标或导入），并且拒绝许多与 .NET Core 不兼容的项目类型，则不建议使用此工具。</span><span class="sxs-lookup"><span data-stu-id="41726-111">It is not recommended if you have a more complicated build established (such as custom tasks, targets, or imports), and it rejects many project types that are incompatible with .NET Core.</span></span>
