---
ms.openlocfilehash: bba9659b92e5aabc276c585929c99898316036c5
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359125"
---
### <a name="hardware-intrinsic-issupported-checks-may-differ-for-nested-types"></a>嵌套类型的硬件内部 IsSupported 检查可能有所不同

现在，如果检查 `<Isa>.X64.IsSupported`（其中 `<Isa>` 引用了 <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> 命名空间中的类），可能会生成与 .NET 早期版本不同的结果。

> [!TIP]
> ISA 的全称是工业标准体系结构。

#### <a name="version-introduced"></a>引入的版本

5.0 预览版 8

#### <a name="change-description"></a>更改说明

在 .NET 的早期版本中，某些 <xref:System.Runtime.Intrinsics.X86> 硬件内部类型（例如 <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType>）未公开嵌套的 `X64` 类。 对于这些类型，调用 `<Isa>.X64.IsSupported` 解析为父类 `<Isa>` 的嵌套 `X64` 类上的 `IsSupported` 属性。 这意味着即使 `<Isa>.IsSupported` 返回 `false`，该属性也可返回 `true`。

在 .NET 5.0 及更高版本中，所有 <xref:System.Runtime.Intrinsics.X86> 类型都公开适当报告支持的嵌套的 `X64` 类。 这可确保一般层次结构保持正确；如果 `<Isa>.X64.IsSupported` 为 `true`，则也可假定 `<Isa>.IsSupported` 为 `true`。

#### <a name="reason-for-change"></a>更改原因

预期结果是，如果 `<Isa>.X64.IsSupported` 为 `true`，则也暗示 `<Isa>.IsSupported` 为 `true`。 但是，由于成员解析在 C# 中的工作方式，没有嵌套的 `X64` 类的类会导致并不总是这种结果且用户代码中会出现 bug。

#### <a name="recommended-action"></a>建议操作

如有必要，请调整检查 `IsSupported` 的代码，以检查相应的 ISA。

#### <a name="category"></a>类别

Core .NET 库

#### <a name="affected-apis"></a>受影响的 API

- <xref:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported`

-->
