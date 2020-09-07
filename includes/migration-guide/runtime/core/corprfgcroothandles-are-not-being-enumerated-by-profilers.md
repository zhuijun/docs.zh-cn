---
ms.openlocfilehash: 25437dcc0c814ed2265b2efb34316af48b372ebd
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496543"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="ce80f-101">探查器未枚举 COR_PRF_GC_ROOT_HANDLEs</span><span class="sxs-lookup"><span data-stu-id="ce80f-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

#### <a name="details"></a><span data-ttu-id="ce80f-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="ce80f-102">Details</span></span>

<span data-ttu-id="ce80f-103">在 .NET Framework v4.5.1 中，分析 API <code>RootReferences2()</code> 错误地不会返回 <code>COR_PRF_GC_ROOT_HANDLE</code>（而是返回 <code>COR_PRF_GC_ROOT_OTHER</code>）。</span><span class="sxs-lookup"><span data-stu-id="ce80f-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="ce80f-104">此问题已从 .NET Framework 4.6 开始修复。</span><span class="sxs-lookup"><span data-stu-id="ce80f-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ce80f-105">建议</span><span class="sxs-lookup"><span data-stu-id="ce80f-105">Suggestion</span></span>

<span data-ttu-id="ce80f-106">此问题已在 .NET Framework 4.6 中解决，因此升级到该版本的 .NET Framework 即可解决该问题。</span><span class="sxs-lookup"><span data-stu-id="ce80f-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="ce80f-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="ce80f-107">Name</span></span>    | <span data-ttu-id="ce80f-108">“值”</span><span class="sxs-lookup"><span data-stu-id="ce80f-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ce80f-109">范围</span><span class="sxs-lookup"><span data-stu-id="ce80f-109">Scope</span></span>   |<span data-ttu-id="ce80f-110">次要</span><span class="sxs-lookup"><span data-stu-id="ce80f-110">Minor</span></span>|
|<span data-ttu-id="ce80f-111">Version</span><span class="sxs-lookup"><span data-stu-id="ce80f-111">Version</span></span>|<span data-ttu-id="ce80f-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="ce80f-112">4.5.1</span></span>|
|<span data-ttu-id="ce80f-113">类型</span><span class="sxs-lookup"><span data-stu-id="ce80f-113">Type</span></span>|<span data-ttu-id="ce80f-114">运行时</span><span class="sxs-lookup"><span data-stu-id="ce80f-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ce80f-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="ce80f-115">Affected APIs</span></span>

<span data-ttu-id="ce80f-116">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="ce80f-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
