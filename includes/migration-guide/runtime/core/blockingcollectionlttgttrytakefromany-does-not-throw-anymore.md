---
ms.openlocfilehash: a8f51dfa1c82e3b166449d2432dfe8a9b96564b9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619828"
---
### <a name="blockingcollectionlttgttrytakefromany-does-not-throw-anymore"></a><span data-ttu-id="9cb93-101">BlockingCollection&lt;T&gt;.TryTakeFromAny 不会再引发任何异常</span><span class="sxs-lookup"><span data-stu-id="9cb93-101">BlockingCollection&lt;T&gt;.TryTakeFromAny does not throw anymore</span></span>

#### <a name="details"></a><span data-ttu-id="9cb93-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="9cb93-102">Details</span></span>

<span data-ttu-id="9cb93-103">如果其中一个输入集合标记为已完成，则 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> 不会再返回 -1，<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> 也不会再引发异常。</span><span class="sxs-lookup"><span data-stu-id="9cb93-103">If one of the input collections is marked completed, <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer returns -1 and <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer throws an exception.</span></span> <span data-ttu-id="9cb93-104">当其中一个集合为空或已完成，但其他集合仍具有可检索的项时，可通过此更改来使用这些集合。</span><span class="sxs-lookup"><span data-stu-id="9cb93-104">This change makes it possible to work with collections when one of the collections is either empty or completed, but the other collection still has items that can be retrieved.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9cb93-105">建议</span><span class="sxs-lookup"><span data-stu-id="9cb93-105">Suggestion</span></span>

<span data-ttu-id="9cb93-106">如果在阻止集合已完成的情况下，在 TryTakeFromAny 返回 -1 或 TakeFromAny 引发异常时用于控制流，此类代码现在应改为使用 <code>.Any(b =&gt; b.IsCompleted)</code> 检测该条件。</span><span class="sxs-lookup"><span data-stu-id="9cb93-106">If TryTakeFromAny returning -1 or TakeFromAny throwing were used for control-flow purposes in cases of a blocking collection being completed, such code should now be changed to use <code>.Any(b =&gt; b.IsCompleted)</code> to detect that condition.</span></span>

| <span data-ttu-id="9cb93-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="9cb93-107">Name</span></span>    | <span data-ttu-id="9cb93-108">“值”</span><span class="sxs-lookup"><span data-stu-id="9cb93-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9cb93-109">范围</span><span class="sxs-lookup"><span data-stu-id="9cb93-109">Scope</span></span>   |<span data-ttu-id="9cb93-110">次要</span><span class="sxs-lookup"><span data-stu-id="9cb93-110">Minor</span></span>|
|<span data-ttu-id="9cb93-111">Version</span><span class="sxs-lookup"><span data-stu-id="9cb93-111">Version</span></span>|<span data-ttu-id="9cb93-112">4.5</span><span class="sxs-lookup"><span data-stu-id="9cb93-112">4.5</span></span>|
|<span data-ttu-id="9cb93-113">类型</span><span class="sxs-lookup"><span data-stu-id="9cb93-113">Type</span></span>|<span data-ttu-id="9cb93-114">运行时</span><span class="sxs-lookup"><span data-stu-id="9cb93-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9cb93-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="9cb93-115">Affected APIs</span></span>

-<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType></li></ul>|
