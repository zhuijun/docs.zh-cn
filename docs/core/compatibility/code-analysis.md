---
title: 代码分析中断性变更
description: 列出 .NET Core 源代码分析器中的中断性变更。
ms.date: 09/02/2020
ms.openlocfilehash: 20badd69b316e1d87700b3c5061a71d648b71c64
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065130"
---
# <a name="code-analysis-breaking-changes"></a><span data-ttu-id="0e2c5-103">代码分析中断性变更</span><span class="sxs-lookup"><span data-stu-id="0e2c5-103">Code analysis breaking changes</span></span>

<span data-ttu-id="0e2c5-104">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="0e2c5-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="0e2c5-105">重大更改</span><span class="sxs-lookup"><span data-stu-id="0e2c5-105">Breaking change</span></span> | <span data-ttu-id="0e2c5-106">引入的版本</span><span class="sxs-lookup"><span data-stu-id="0e2c5-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="0e2c5-107">CA1416：平台兼容性</span><span class="sxs-lookup"><span data-stu-id="0e2c5-107">CA1416: Platform compatibility</span></span>](#ca1416-platform-compatibility) | <span data-ttu-id="0e2c5-108">5.0</span><span class="sxs-lookup"><span data-stu-id="0e2c5-108">5.0</span></span> |
| [<span data-ttu-id="0e2c5-109">CA1417：P/Invoke 的字符串参数上的 OutAttribute</span><span class="sxs-lookup"><span data-stu-id="0e2c5-109">CA1417: OutAttribute on string parameter for P/Invoke</span></span>](#ca1417-outattribute-on-string-parameter-for-pinvoke) | <span data-ttu-id="0e2c5-110">5.0</span><span class="sxs-lookup"><span data-stu-id="0e2c5-110">5.0</span></span> |
| [<span data-ttu-id="0e2c5-111">CA1831：为字符串使用 AsSpan 而不是基于范围的索引器</span><span class="sxs-lookup"><span data-stu-id="0e2c5-111">CA1831: Use AsSpan instead of Range-based indexers for string</span></span>](#ca1831-use-asspan-instead-of-range-based-indexers-for-string) | <span data-ttu-id="0e2c5-112">5.0</span><span class="sxs-lookup"><span data-stu-id="0e2c5-112">5.0</span></span> |
| [<span data-ttu-id="0e2c5-113">CA2013:请勿将 ReferenceEquals 与值类型结合使用</span><span class="sxs-lookup"><span data-stu-id="0e2c5-113">CA2013: Do not use ReferenceEquals with value types</span></span>](#ca2013-do-not-use-referenceequals-with-value-types) | <span data-ttu-id="0e2c5-114">5.0</span><span class="sxs-lookup"><span data-stu-id="0e2c5-114">5.0</span></span> |
| [<span data-ttu-id="0e2c5-115">CA2014:请勿在循环中使用 stackalloc</span><span class="sxs-lookup"><span data-stu-id="0e2c5-115">CA2014: Do not use stackalloc in loops</span></span>](#ca2014-do-not-use-stackalloc-in-loops) | <span data-ttu-id="0e2c5-116">5.0</span><span class="sxs-lookup"><span data-stu-id="0e2c5-116">5.0</span></span> |
| [<span data-ttu-id="0e2c5-117">CA2015：请勿为派生自 \<T> 的类型定义终结器</span><span class="sxs-lookup"><span data-stu-id="0e2c5-117">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | <span data-ttu-id="0e2c5-118">5.0</span><span class="sxs-lookup"><span data-stu-id="0e2c5-118">5.0</span></span> |
| [<span data-ttu-id="0e2c5-119">CA2247：TaskCompletionSource 构造函数的参数应为 TaskCreationOptions 值</span><span class="sxs-lookup"><span data-stu-id="0e2c5-119">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | <span data-ttu-id="0e2c5-120">5.0</span><span class="sxs-lookup"><span data-stu-id="0e2c5-120">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="0e2c5-121">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="0e2c5-121">.NET 5.0</span></span>

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

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ca2247-ctor-arg-should-be-taskcreationoptions.md)]

***
