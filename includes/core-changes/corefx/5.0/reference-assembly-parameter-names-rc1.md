---
ms.openlocfilehash: 760c9ce2427bc1f5e9276e66ecb6d2cf2ed83c16
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738810"
---
### <a name="parameter-names-changed-in-rc1"></a>RC1 中的参数名称已更改

某些引用程序集参数名称已更改以匹配实现程序集中的参数名称。

#### <a name="change-description"></a>更改描述

在以前的 .NET 5.0 预览版和 RC 版本中，某些[引用程序集](../../../../docs/standard/assembly/reference-assemblies.md)参数名称与实现程序集中的对应参数不同。 使用命名参数和反射时，这可能会导致出现问题。

在 .NET 5.0 RC2 中，这些不匹配的参数名称在引用程序集中已更新，以与实现程序集中的相应参数名完全匹配。

下表显示了更改的 API 和参数名称。

| API | 旧参数名称 | 新参数名称 |
| - | - | - |
| <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)> | `traceOptions` | `traceFlags` |
| <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=nameWithType> | `suffix` | `prefix` |

#### <a name="reason-for-change"></a>更改原因

更改参数名称以保持一致性，避免在使用命名参数和反射时出现故障。

#### <a name="version-introduced"></a>引入的版本

5.0 RC2

#### <a name="recommended-action"></a>建议操作

如果由于参数名称更改而遇到编译器错误，请相应地更新参数名称。

#### <a name="category"></a>类别

Core .NET 库

#### <a name="affected-apis"></a>受影响的 API

- <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)>
- <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.ActivityContext.#ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)`
- `M:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)`

-->
