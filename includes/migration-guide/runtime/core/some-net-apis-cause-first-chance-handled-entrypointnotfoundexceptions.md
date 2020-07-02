---
ms.openlocfilehash: ed526095459a48aa37b585dfed79cc12b9fb9e56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621941"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a><span data-ttu-id="e3317-101">一些 .NET API 会导致最可能的（已处理）EntryPointNotFoundExceptions</span><span class="sxs-lookup"><span data-stu-id="e3317-101">Some .NET APIs cause first chance (handled) EntryPointNotFoundExceptions</span></span>

#### <a name="details"></a><span data-ttu-id="e3317-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="e3317-102">Details</span></span>

<span data-ttu-id="e3317-103">在 .NET Framework 4.5 中，少量 .NET 方法开始引发最可能的 <xref:System.EntryPointNotFoundException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="e3317-103">In the .NET Framework 4.5, a small number of .NET methods began throwing first chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span> <span data-ttu-id="e3317-104">这些异常在 .NET Framework 内进行处理，但可能会中断不希望出现最可能的异常的测试自动化。</span><span class="sxs-lookup"><span data-stu-id="e3317-104">These exceptions were handled within the .NET Framework, but could break test automation that did not expect the first chance exceptions.</span></span> <span data-ttu-id="e3317-105">启用 HighVersionLie 后，这些相同的 API 会中断一些 ApiVerifier 方案。</span><span class="sxs-lookup"><span data-stu-id="e3317-105">These same APIs break some ApiVerifier scenarios when HighVersionLie is enabled.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e3317-106">建议</span><span class="sxs-lookup"><span data-stu-id="e3317-106">Suggestion</span></span>

<span data-ttu-id="e3317-107">升级到 .NET Framework 4.5.1 可避免此 bug 出现。</span><span class="sxs-lookup"><span data-stu-id="e3317-107">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="e3317-108">还可以更新测试自动化以便不中断对最可能的 <xref:System.EntryPointNotFoundException?displayProperty=fullName> 的操作。</span><span class="sxs-lookup"><span data-stu-id="e3317-108">Alternatively, test automation can be updated to not break on first-chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span>

| <span data-ttu-id="e3317-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="e3317-109">Name</span></span>    | <span data-ttu-id="e3317-110">“值”</span><span class="sxs-lookup"><span data-stu-id="e3317-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e3317-111">范围</span><span class="sxs-lookup"><span data-stu-id="e3317-111">Scope</span></span>   |<span data-ttu-id="e3317-112">边缘</span><span class="sxs-lookup"><span data-stu-id="e3317-112">Edge</span></span>|
|<span data-ttu-id="e3317-113">Version</span><span class="sxs-lookup"><span data-stu-id="e3317-113">Version</span></span>|<span data-ttu-id="e3317-114">4.5</span><span class="sxs-lookup"><span data-stu-id="e3317-114">4.5</span></span>|
|<span data-ttu-id="e3317-115">类型</span><span class="sxs-lookup"><span data-stu-id="e3317-115">Type</span></span>|<span data-ttu-id="e3317-116">运行时</span><span class="sxs-lookup"><span data-stu-id="e3317-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e3317-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="e3317-117">Affected APIs</span></span>

-<xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)></li></ul>|
