---
ms.openlocfilehash: bba9659b92e5aabc276c585929c99898316036c5
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359125"
---
### <a name="hardware-intrinsic-issupported-checks-may-differ-for-nested-types"></a><span data-ttu-id="1e0c2-101">嵌套类型的硬件内部 IsSupported 检查可能有所不同</span><span class="sxs-lookup"><span data-stu-id="1e0c2-101">Hardware intrinsic IsSupported checks may differ for nested types</span></span>

<span data-ttu-id="1e0c2-102">现在，如果检查 `<Isa>.X64.IsSupported`（其中 `<Isa>` 引用了 <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> 命名空间中的类），可能会生成与 .NET 早期版本不同的结果。</span><span class="sxs-lookup"><span data-stu-id="1e0c2-102">Checking `<Isa>.X64.IsSupported`, where `<Isa>` refers to the classes in the <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> namespace, may now produce a different result to previous versions of .NET.</span></span>

> [!TIP]
> <span data-ttu-id="1e0c2-103">ISA 的全称是工业标准体系结构。</span><span class="sxs-lookup"><span data-stu-id="1e0c2-103">*ISA* stands for industry standard architecture.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1e0c2-104">引入的版本</span><span class="sxs-lookup"><span data-stu-id="1e0c2-104">Version introduced</span></span>

<span data-ttu-id="1e0c2-105">5.0 预览版 8</span><span class="sxs-lookup"><span data-stu-id="1e0c2-105">5.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="1e0c2-106">更改说明</span><span class="sxs-lookup"><span data-stu-id="1e0c2-106">Change description</span></span>

<span data-ttu-id="1e0c2-107">在 .NET 的早期版本中，某些 <xref:System.Runtime.Intrinsics.X86> 硬件内部类型（例如 <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType>）未公开嵌套的 `X64` 类。</span><span class="sxs-lookup"><span data-stu-id="1e0c2-107">In previous versions of .NET, some of the <xref:System.Runtime.Intrinsics.X86> hardware-intrinsic types, for example, <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType>, didn't expose a nested `X64` class.</span></span> <span data-ttu-id="1e0c2-108">对于这些类型，调用 `<Isa>.X64.IsSupported` 解析为父类 `<Isa>` 的嵌套 `X64` 类上的 `IsSupported` 属性。</span><span class="sxs-lookup"><span data-stu-id="1e0c2-108">For these types, calling `<Isa>.X64.IsSupported` resolved to an `IsSupported` property on a nested `X64` class of a parent class of `<Isa>`.</span></span> <span data-ttu-id="1e0c2-109">这意味着即使 `<Isa>.IsSupported` 返回 `false`，该属性也可返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="1e0c2-109">This meant that the property could return `true` even when `<Isa>.IsSupported` returns `false`.</span></span>

<span data-ttu-id="1e0c2-110">在 .NET 5.0 及更高版本中，所有 <xref:System.Runtime.Intrinsics.X86> 类型都公开适当报告支持的嵌套的 `X64` 类。</span><span class="sxs-lookup"><span data-stu-id="1e0c2-110">In .NET 5.0 and later versions, all of the <xref:System.Runtime.Intrinsics.X86> types expose a nested `X64` class that appropriately reports support.</span></span> <span data-ttu-id="1e0c2-111">这可确保一般层次结构保持正确；如果 `<Isa>.X64.IsSupported` 为 `true`，则也可假定 `<Isa>.IsSupported` 为 `true`。</span><span class="sxs-lookup"><span data-stu-id="1e0c2-111">This ensures that the general hierarchy remains correct, and that if `<Isa>.X64.IsSupported` is `true`, then `<Isa>.IsSupported` can also be assumed to be `true`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1e0c2-112">更改原因</span><span class="sxs-lookup"><span data-stu-id="1e0c2-112">Reason for change</span></span>

<span data-ttu-id="1e0c2-113">预期结果是，如果 `<Isa>.X64.IsSupported` 为 `true`，则也暗示 `<Isa>.IsSupported` 为 `true`。</span><span class="sxs-lookup"><span data-stu-id="1e0c2-113">It was intended that if `<Isa>.X64.IsSupported` is `true`, `<Isa>.IsSupported` is also implied to be `true`.</span></span> <span data-ttu-id="1e0c2-114">但是，由于成员解析在 C# 中的工作方式，没有嵌套的 `X64` 类的类会导致并不总是这种结果且用户代码中会出现 bug。</span><span class="sxs-lookup"><span data-stu-id="1e0c2-114">However, due to how member resolution works in C#, classes that didn't have a nested `X64` class exposed a situation where this wasn't always the case and led to bugs in user code.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1e0c2-115">建议操作</span><span class="sxs-lookup"><span data-stu-id="1e0c2-115">Recommended action</span></span>

<span data-ttu-id="1e0c2-116">如有必要，请调整检查 `IsSupported` 的代码，以检查相应的 ISA。</span><span class="sxs-lookup"><span data-stu-id="1e0c2-116">If necessary, adjust code that checks `IsSupported` to check for the appropriate ISA.</span></span>

#### <a name="category"></a><span data-ttu-id="1e0c2-117">类别</span><span class="sxs-lookup"><span data-stu-id="1e0c2-117">Category</span></span>

<span data-ttu-id="1e0c2-118">Core .NET 库</span><span class="sxs-lookup"><span data-stu-id="1e0c2-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1e0c2-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="1e0c2-119">Affected APIs</span></span>

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
