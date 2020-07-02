---
ms.openlocfilehash: 9131c91b34f4c24653dea37ea39af6be6e072287
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619855"
---
### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a><span data-ttu-id="0fac5-101">Enumerable.Empty&lt;TResult&gt; 始终返回缓存的实例</span><span class="sxs-lookup"><span data-stu-id="0fac5-101">Enumerable.Empty&lt;TResult&gt; always returns cached instance</span></span>

#### <a name="details"></a><span data-ttu-id="0fac5-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="0fac5-102">Details</span></span>

<span data-ttu-id="0fac5-103">从 .NET Framework 4.5 开始，<xref:System.Linq.Enumerable.Empty%60%601> 始终返回缓存的内部实例 <xref:System.Collections.Generic.IEnumerable%601>。以前，在调用 API 时，<xref:System.Linq.Enumerable.Empty%60%601> 将缓存空 <xref:System.Collections.Generic.IEnumerable%601>，这意味着在同时快速调用 <xref:System.Linq.Enumerable.Empty%60%601> 的某些情况下，针对 API 的不同调用将返回不同的类型实例。</span><span class="sxs-lookup"><span data-stu-id="0fac5-103">Beginning in .NET Framework 4.5, <xref:System.Linq.Enumerable.Empty%60%601> always returns a cached internal instance <xref:System.Collections.Generic.IEnumerable%601>.Previously, <xref:System.Linq.Enumerable.Empty%60%601> would cache an empty <xref:System.Collections.Generic.IEnumerable%601> at the time the API was called, meaning that in some conditions in which <xref:System.Linq.Enumerable.Empty%60%601> was called rapidly and concurrently, different instances of the type could be returned for different calls to the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0fac5-104">建议</span><span class="sxs-lookup"><span data-stu-id="0fac5-104">Suggestion</span></span>

<span data-ttu-id="0fac5-105">因为以前的行为不确定，所以代码不太可能依赖它。</span><span class="sxs-lookup"><span data-stu-id="0fac5-105">Because the previous behavior was non-deterministic, code is unlikely to depend on it.</span></span> <span data-ttu-id="0fac5-106">但是，如果出现需要比较空枚举并希望它们有时不相等这一罕见情形，应创建显式空数组 (<code>new T[0]</code>)，而非使用 <xref:System.Linq.Enumerable.Empty%60%601>。</span><span class="sxs-lookup"><span data-stu-id="0fac5-106">However, in the unlikely case that empty enumerables are being compared and expected to sometimes be unequal, explicit empty arrays should be created (<code>new T[0]</code>) instead of using <xref:System.Linq.Enumerable.Empty%60%601>.</span></span>

| <span data-ttu-id="0fac5-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="0fac5-107">Name</span></span>    | <span data-ttu-id="0fac5-108">“值”</span><span class="sxs-lookup"><span data-stu-id="0fac5-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0fac5-109">范围</span><span class="sxs-lookup"><span data-stu-id="0fac5-109">Scope</span></span>   |<span data-ttu-id="0fac5-110">边缘</span><span class="sxs-lookup"><span data-stu-id="0fac5-110">Edge</span></span>|
|<span data-ttu-id="0fac5-111">Version</span><span class="sxs-lookup"><span data-stu-id="0fac5-111">Version</span></span>|<span data-ttu-id="0fac5-112">4.5</span><span class="sxs-lookup"><span data-stu-id="0fac5-112">4.5</span></span>|
|<span data-ttu-id="0fac5-113">类型</span><span class="sxs-lookup"><span data-stu-id="0fac5-113">Type</span></span>|<span data-ttu-id="0fac5-114">运行时</span><span class="sxs-lookup"><span data-stu-id="0fac5-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0fac5-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="0fac5-115">Affected APIs</span></span>

-<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|
