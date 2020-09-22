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
# <a name="code-analysis-breaking-changes"></a>代码分析中断性变更

本页记录了以下中断性变更：

| 重大更改 | 引入的版本 |
| - | :-: |
| [CA1416：平台兼容性](#ca1416-platform-compatibility) | 5.0 |
| [CA1417：P/Invoke 的字符串参数上的 OutAttribute](#ca1417-outattribute-on-string-parameter-for-pinvoke) | 5.0 |
| [CA1831：为字符串使用 AsSpan 而不是基于范围的索引器](#ca1831-use-asspan-instead-of-range-based-indexers-for-string) | 5.0 |
| [CA2013:请勿将 ReferenceEquals 与值类型结合使用](#ca2013-do-not-use-referenceequals-with-value-types) | 5.0 |
| [CA2014:请勿在循环中使用 stackalloc](#ca2014-do-not-use-stackalloc-in-loops) | 5.0 |
| [CA2015：请勿为派生自 \<T> 的类型定义终结器](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | 5.0 |
| [CA2200:再次引发以保留堆栈详细信息](#ca2200-rethrow-to-preserve-stack-details) | 5.0 |
| [CA2247：TaskCompletionSource 构造函数的参数应为 TaskCreationOptions 值](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | 5.0 |

## <a name="net-50"></a>.NET 5.0

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
