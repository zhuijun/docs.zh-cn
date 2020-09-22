---
title: 代码分析中断性变更
description: 列出 .NET Core 源代码分析器中的中断性变更。
ms.date: 09/02/2020
ms.openlocfilehash: 3cbe2ecf5d08084db542db0c2da016f1f391452e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538913"
---
# <a name="code-analysis-breaking-changes"></a><span data-ttu-id="f398c-103">代码分析中断性变更</span><span class="sxs-lookup"><span data-stu-id="f398c-103">Code analysis breaking changes</span></span>

<span data-ttu-id="f398c-104">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="f398c-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="f398c-105">重大更改</span><span class="sxs-lookup"><span data-stu-id="f398c-105">Breaking change</span></span> | <span data-ttu-id="f398c-106">引入的版本</span><span class="sxs-lookup"><span data-stu-id="f398c-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="f398c-107">CA1416：平台兼容性</span><span class="sxs-lookup"><span data-stu-id="f398c-107">CA1416: Platform compatibility</span></span>](#ca1416-platform-compatibility) | <span data-ttu-id="f398c-108">5.0</span><span class="sxs-lookup"><span data-stu-id="f398c-108">5.0</span></span> |
| [<span data-ttu-id="f398c-109">CA1417：P/Invoke 的字符串参数上的 OutAttribute</span><span class="sxs-lookup"><span data-stu-id="f398c-109">CA1417: OutAttribute on string parameter for P/Invoke</span></span>](#ca1417-outattribute-on-string-parameter-for-pinvoke) | <span data-ttu-id="f398c-110">5.0</span><span class="sxs-lookup"><span data-stu-id="f398c-110">5.0</span></span> |
| [<span data-ttu-id="f398c-111">CA1831：为字符串使用 AsSpan 而不是基于范围的索引器</span><span class="sxs-lookup"><span data-stu-id="f398c-111">CA1831: Use AsSpan instead of Range-based indexers for string</span></span>](#ca1831-use-asspan-instead-of-range-based-indexers-for-string) | <span data-ttu-id="f398c-112">5.0</span><span class="sxs-lookup"><span data-stu-id="f398c-112">5.0</span></span> |
| [<span data-ttu-id="f398c-113">CA2013:请勿将 ReferenceEquals 与值类型结合使用</span><span class="sxs-lookup"><span data-stu-id="f398c-113">CA2013: Do not use ReferenceEquals with value types</span></span>](#ca2013-do-not-use-referenceequals-with-value-types) | <span data-ttu-id="f398c-114">5.0</span><span class="sxs-lookup"><span data-stu-id="f398c-114">5.0</span></span> |
| [<span data-ttu-id="f398c-115">CA2014:请勿在循环中使用 stackalloc</span><span class="sxs-lookup"><span data-stu-id="f398c-115">CA2014: Do not use stackalloc in loops</span></span>](#ca2014-do-not-use-stackalloc-in-loops) | <span data-ttu-id="f398c-116">5.0</span><span class="sxs-lookup"><span data-stu-id="f398c-116">5.0</span></span> |
| [<span data-ttu-id="f398c-117">CA2015：请勿为派生自 \<T> 的类型定义终结器</span><span class="sxs-lookup"><span data-stu-id="f398c-117">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | <span data-ttu-id="f398c-118">5.0</span><span class="sxs-lookup"><span data-stu-id="f398c-118">5.0</span></span> |
| [<span data-ttu-id="f398c-119">CA2200:再次引发以保留堆栈详细信息</span><span class="sxs-lookup"><span data-stu-id="f398c-119">CA2200: Rethrow to preserve stack details</span></span>](#ca2200-rethrow-to-preserve-stack-details) | <span data-ttu-id="f398c-120">5.0</span><span class="sxs-lookup"><span data-stu-id="f398c-120">5.0</span></span> |
| [<span data-ttu-id="f398c-121">CA2247：TaskCompletionSource 构造函数的参数应为 TaskCreationOptions 值</span><span class="sxs-lookup"><span data-stu-id="f398c-121">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | <span data-ttu-id="f398c-122">5.0</span><span class="sxs-lookup"><span data-stu-id="f398c-122">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="f398c-123">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="f398c-123">.NET 5.0</span></span>

[!INCLUDE [ca1416-platform-compatibility-analyzer](../../../includes/core-changes/codeanalysis/5.0/ca1416-platform-compatibility-analyzer.md)]

***

[!INCLUDE [outattributes-on-pinvoke-string-parameters](../../../includes/core-changes/codeanalysis/5.0/ca1417-outattributes-on-pinvoke-string-parameters.md)]

***

[!INCLUDE [range-based-indexer-on-string](../../../includes/core-changes/codeanalysis/5.0/ca1831-range-based-indexer-on-string.md)]

***

[!INCLUDE [referenceequals-on-value-types](../../../includes/core-changes/codeanalysis/5.0/ca2013-referenceequals-on-value-types.md)]

***

[!INCLUDE [stackalloc-in-loops](../../../includes/core-changes/codeanalysis/5.0/ca2014-stackalloc-in-loops.md)]

***

[!INCLUDE [finalizers-for-memorymanager-types](../../../includes/core-changes/codeanalysis/5.0/ca2015-finalizers-for-memorymanager-types.md)]

***

[!INCLUDE [ca2200-rethrow-to-preserve-stack-details](../../../includes/core-changes/codeanalysis/5.0/ca2200-rethrow-to-preserve-stack-details.md)]

***

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ca2247-ctor-arg-should-be-taskcreationoptions.md)]

***
