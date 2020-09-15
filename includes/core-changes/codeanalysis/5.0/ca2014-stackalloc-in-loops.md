---
ms.openlocfilehash: a51160a8ab5a4b437e51db31def577f8d8f50182
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065127"
---
### <a name="ca2014-do-not-use-stackalloc-in-loops"></a>CA2014:请勿在循环中使用 stackalloc

从 .NET 5.0 开始，默认启用 .NET 代码分析器规则 [CA2014](/visualstudio/code-quality/ca2014)。 对于在循环内使用 [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) 表达式的任何 C# 代码，它都会生成一个生成警告。

#### <a name="change-description"></a>更改说明

从 .NET 5.0 开始，.NET SDK 包括 [.NET 源代码分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。 其中一些规则会默认启用，包括 [CA2014](/visualstudio/code-quality/ca2014)。 如果项目包含违反此规则的代码，并已被配置为将警告视为错误，则此更改可能会中断生成。

规则 CA2014 会查找在循环中使用 [stackalloc 表达式](../../../../docs/csharp/language-reference/operators/stackalloc.md)的 C# 代码。 [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) 从当前堆栈帧中分配内存。 在当前方法调用返回之前，不会释放内存，这可能导致堆栈溢出。 因为无法捕获堆栈溢出异常，应用将在发生堆栈溢出时终止。

#### <a name="version-introduced"></a>引入的版本

5.0 预览版 8

#### <a name="recommended-action"></a>建议操作

- 不要在循环内使用 [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md)。 在循环外分配内存块，然后在循环内重用它。 有关详细信息，请参阅 [CA2014](/visualstudio/code-quality/ca2014)。

- 若要完全禁用代码分析，请在项目文件中将 `EnableNETAnalyzers` 设置为 `false`。 有关详细信息，请参阅 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。

#### <a name="category"></a>类别

代码分析

#### <a name="affected-apis"></a>受影响的 API

无法通过 API 分析检测到。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
