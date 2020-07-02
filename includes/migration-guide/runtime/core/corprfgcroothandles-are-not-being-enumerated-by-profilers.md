---
ms.openlocfilehash: 4f52535e54607cc824500f9c6a14964a1dec9d32
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619830"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="db882-101">探查器未枚举 COR_PRF_GC_ROOT_HANDLEs</span><span class="sxs-lookup"><span data-stu-id="db882-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

#### <a name="details"></a><span data-ttu-id="db882-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="db882-102">Details</span></span>

<span data-ttu-id="db882-103">在 .NET Framework v4.5.1 中，分析 API <code>RootReferences2()</code> 错误地不会返回 <code>COR_PRF_GC_ROOT_HANDLE</code>（而是返回 <code>COR_PRF_GC_ROOT_OTHER</code>）。</span><span class="sxs-lookup"><span data-stu-id="db882-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="db882-104">此问题已从 .NET Framework 4.6 开始修复。</span><span class="sxs-lookup"><span data-stu-id="db882-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="db882-105">建议</span><span class="sxs-lookup"><span data-stu-id="db882-105">Suggestion</span></span>

<span data-ttu-id="db882-106">此问题已在 .NET Framework 4.6 中解决，因此升级到该版本的 .NET Framework 即可解决该问题。</span><span class="sxs-lookup"><span data-stu-id="db882-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="db882-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="db882-107">Name</span></span>    | <span data-ttu-id="db882-108">“值”</span><span class="sxs-lookup"><span data-stu-id="db882-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="db882-109">范围</span><span class="sxs-lookup"><span data-stu-id="db882-109">Scope</span></span>   |<span data-ttu-id="db882-110">次要</span><span class="sxs-lookup"><span data-stu-id="db882-110">Minor</span></span>|
|<span data-ttu-id="db882-111">Version</span><span class="sxs-lookup"><span data-stu-id="db882-111">Version</span></span>|<span data-ttu-id="db882-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="db882-112">4.5.1</span></span>|
|<span data-ttu-id="db882-113">类型</span><span class="sxs-lookup"><span data-stu-id="db882-113">Type</span></span>|<span data-ttu-id="db882-114">运行时</span><span class="sxs-lookup"><span data-stu-id="db882-114">Runtime</span></span>|
