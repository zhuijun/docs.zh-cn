---
title: 代码分析中断性变更
description: 列出 .NET Core 源代码分析器中的中断性变更。
ms.date: 08/22/2020
ms.openlocfilehash: 8b2b50c5f03a3ca971aefd0f2cf53624dfa82274
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465557"
---
# <a name="code-analysis-breaking-changes"></a><span data-ttu-id="a0134-103">代码分析中断性变更</span><span class="sxs-lookup"><span data-stu-id="a0134-103">Code analysis breaking changes</span></span>

<span data-ttu-id="a0134-104">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="a0134-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="a0134-105">重大更改</span><span class="sxs-lookup"><span data-stu-id="a0134-105">Breaking change</span></span> | <span data-ttu-id="a0134-106">引入的版本</span><span class="sxs-lookup"><span data-stu-id="a0134-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="a0134-107">CA1831：使用 AsSpan 或 AsMemory，而不是基于范围的索引器</span><span class="sxs-lookup"><span data-stu-id="a0134-107">CA1831: Use AsSpan or AsMemory instead of Range-based indexer</span></span>](#ca1831-use-asspan-or-asmemory-instead-of-range-based-indexer) | <span data-ttu-id="a0134-108">5.0</span><span class="sxs-lookup"><span data-stu-id="a0134-108">5.0</span></span> |
| [<span data-ttu-id="a0134-109">CA2014:请勿在循环中使用 stackalloc</span><span class="sxs-lookup"><span data-stu-id="a0134-109">CA2014: Do not use stackalloc in loops</span></span>](#ca2014-do-not-use-stackalloc-in-loops) | <span data-ttu-id="a0134-110">5.0</span><span class="sxs-lookup"><span data-stu-id="a0134-110">5.0</span></span> |
| [<span data-ttu-id="a0134-111">CA2015：请勿为派生自 \<T> 的类型定义终结器</span><span class="sxs-lookup"><span data-stu-id="a0134-111">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | <span data-ttu-id="a0134-112">5.0</span><span class="sxs-lookup"><span data-stu-id="a0134-112">5.0</span></span> |
| [<span data-ttu-id="a0134-113">CA2247：TaskCompletionSource 构造函数的参数应为 TaskCreationOptions 值</span><span class="sxs-lookup"><span data-stu-id="a0134-113">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | <span data-ttu-id="a0134-114">5.0</span><span class="sxs-lookup"><span data-stu-id="a0134-114">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="a0134-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="a0134-115">.NET 5.0</span></span>

[!INCLUDE [range-based-indexer-on-string](../../../includes/core-changes/codeanalysis/5.0/range-based-indexer-on-string.md)]

***

[!INCLUDE [stackalloc-in-loops](../../../includes/core-changes/codeanalysis/5.0/stackalloc-in-loops.md)]

***

[!INCLUDE [finalizers-for-memorymanager-types](../../../includes/core-changes/codeanalysis/5.0/finalizers-for-memorymanager-types.md)]

***

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ctor-arg-should-be-taskcreationoptions.md)]

***
