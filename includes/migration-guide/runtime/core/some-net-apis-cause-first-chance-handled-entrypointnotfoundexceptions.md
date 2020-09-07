---
ms.openlocfilehash: 6431f3b4d0983c44629e4fe760c75adcc277ddd4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497509"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a><span data-ttu-id="c51c6-101">一些 .NET API 会导致最可能的（已处理）EntryPointNotFoundExceptions</span><span class="sxs-lookup"><span data-stu-id="c51c6-101">Some .NET APIs cause first chance (handled) EntryPointNotFoundExceptions</span></span>

#### <a name="details"></a><span data-ttu-id="c51c6-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="c51c6-102">Details</span></span>

<span data-ttu-id="c51c6-103">在 .NET Framework 4.5 中，少量 .NET 方法开始引发最可能的 <xref:System.EntryPointNotFoundException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="c51c6-103">In the .NET Framework 4.5, a small number of .NET methods began throwing first chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span> <span data-ttu-id="c51c6-104">这些异常在 .NET Framework 内进行处理，但可能会中断不希望出现最可能的异常的测试自动化。</span><span class="sxs-lookup"><span data-stu-id="c51c6-104">These exceptions were handled within the .NET Framework, but could break test automation that did not expect the first chance exceptions.</span></span> <span data-ttu-id="c51c6-105">启用 HighVersionLie 后，这些相同的 API 会中断一些 ApiVerifier 方案。</span><span class="sxs-lookup"><span data-stu-id="c51c6-105">These same APIs break some ApiVerifier scenarios when HighVersionLie is enabled.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c51c6-106">建议</span><span class="sxs-lookup"><span data-stu-id="c51c6-106">Suggestion</span></span>

<span data-ttu-id="c51c6-107">升级到 .NET Framework 4.5.1 可避免此 bug 出现。</span><span class="sxs-lookup"><span data-stu-id="c51c6-107">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="c51c6-108">还可以更新测试自动化以便不中断对最可能的 <xref:System.EntryPointNotFoundException?displayProperty=fullName> 的操作。</span><span class="sxs-lookup"><span data-stu-id="c51c6-108">Alternatively, test automation can be updated to not break on first-chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span>

| <span data-ttu-id="c51c6-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="c51c6-109">Name</span></span>    | <span data-ttu-id="c51c6-110">“值”</span><span class="sxs-lookup"><span data-stu-id="c51c6-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c51c6-111">范围</span><span class="sxs-lookup"><span data-stu-id="c51c6-111">Scope</span></span>   |<span data-ttu-id="c51c6-112">边缘</span><span class="sxs-lookup"><span data-stu-id="c51c6-112">Edge</span></span>|
|<span data-ttu-id="c51c6-113">Version</span><span class="sxs-lookup"><span data-stu-id="c51c6-113">Version</span></span>|<span data-ttu-id="c51c6-114">4.5</span><span class="sxs-lookup"><span data-stu-id="c51c6-114">4.5</span></span>|
|<span data-ttu-id="c51c6-115">类型</span><span class="sxs-lookup"><span data-stu-id="c51c6-115">Type</span></span>|<span data-ttu-id="c51c6-116">运行时</span><span class="sxs-lookup"><span data-stu-id="c51c6-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c51c6-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="c51c6-117">Affected APIs</span></span>

- <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)>

<!--

#### Affected APIs

- `M:System.Diagnostics.Debug.Assert(System.Boolean)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])`
- `M:System.Xml.Serialization.XmlSerializer.#ctor(System.Type)`

-->
