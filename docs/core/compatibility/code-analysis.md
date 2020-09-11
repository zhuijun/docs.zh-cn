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
# <a name="code-analysis-breaking-changes"></a>代码分析中断性变更

本页记录了以下中断性变更：

| 重大更改 | 引入的版本 |
| - | :-: |
| [CA1831：使用 AsSpan 或 AsMemory，而不是基于范围的索引器](#ca1831-use-asspan-or-asmemory-instead-of-range-based-indexer) | 5.0 |
| [CA2014:请勿在循环中使用 stackalloc](#ca2014-do-not-use-stackalloc-in-loops) | 5.0 |
| [CA2015：请勿为派生自 \<T> 的类型定义终结器](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | 5.0 |
| [CA2247：TaskCompletionSource 构造函数的参数应为 TaskCreationOptions 值](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | 5.0 |

## <a name="net-50"></a>.NET 5.0

[!INCLUDE [range-based-indexer-on-string](../../../includes/core-changes/codeanalysis/5.0/range-based-indexer-on-string.md)]

***

[!INCLUDE [stackalloc-in-loops](../../../includes/core-changes/codeanalysis/5.0/stackalloc-in-loops.md)]

***

[!INCLUDE [finalizers-for-memorymanager-types](../../../includes/core-changes/codeanalysis/5.0/finalizers-for-memorymanager-types.md)]

***

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ctor-arg-should-be-taskcreationoptions.md)]

***
