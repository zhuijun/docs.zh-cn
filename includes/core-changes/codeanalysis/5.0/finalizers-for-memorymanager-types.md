---
ms.openlocfilehash: 4fc31f75e8f8cdd50abebd399d9749688e6faa5a
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465560"
---
### <a name="ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert"></a>CA2015:请勿为派生自 MemoryManager\<T> 的类型定义终结器

从 .NET 5.0 开始，默认启用 .NET 代码分析器规则 [CA2015](/visualstudio/code-quality/ca2015)。 对于派生自定义终结器的 <xref:System.Buffers.MemoryManager%601> 的任何类型，它都会生成一个生成警告。

#### <a name="change-description"></a>更改说明

从 .NET 5.0 开始，.NET SDK 包括 [.NET 源代码分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。 其中一些规则会默认启用，包括 [CA2015](/visualstudio/code-quality/ca2015)。 如果项目包含违反此规则的代码，并已被配置为将警告视为错误，则此更改可能会中断生成。

派生自定义终结器的 <xref:System.Buffers.MemoryManager%601> 的规则 CA2015 标记类型。 将终结器添加到派生自 <xref:System.Buffers.MemoryManager%601> 的类型可能表明存在 bug。 这表明在 <xref:System.Span%601> 中获得的本机资源正在被清除，同时 <xref:System.Span%601> 可能仍在使用该资源。

#### <a name="version-introduced"></a>引入的版本

5.0 预览版 8

#### <a name="recommended-action"></a>建议操作

- 删除终结器定义。 有关详细信息，请参阅 [CA2015](/visualstudio/code-quality/ca2015)。

- 若要完全禁用代码分析，请在项目文件中将 `EnableNETAnalyzers` 设置为 `false`。 有关详细信息，请参阅 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。

#### <a name="category"></a>类别

代码分析

#### <a name="affected-apis"></a>受影响的 API

无法通过 API 分析检测到。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
