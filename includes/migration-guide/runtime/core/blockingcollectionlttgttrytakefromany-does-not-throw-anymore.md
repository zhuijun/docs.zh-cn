---
ms.openlocfilehash: 277a91fbfbf0c6aaaa0dc044ef0c079ad8607699
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497657"
---
### <a name="blockingcollectionlttgttrytakefromany-does-not-throw-anymore"></a><span data-ttu-id="bbffc-101">BlockingCollection&lt;T&gt;.TryTakeFromAny 不会再引发任何异常</span><span class="sxs-lookup"><span data-stu-id="bbffc-101">BlockingCollection&lt;T&gt;.TryTakeFromAny does not throw anymore</span></span>

#### <a name="details"></a><span data-ttu-id="bbffc-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="bbffc-102">Details</span></span>

<span data-ttu-id="bbffc-103">如果其中一个输入集合标记为已完成，则 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> 不会再返回 -1，<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> 也不会再引发异常。</span><span class="sxs-lookup"><span data-stu-id="bbffc-103">If one of the input collections is marked completed, <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer returns -1 and <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer throws an exception.</span></span> <span data-ttu-id="bbffc-104">当其中一个集合为空或已完成，但其他集合仍具有可检索的项时，可通过此更改来使用这些集合。</span><span class="sxs-lookup"><span data-stu-id="bbffc-104">This change makes it possible to work with collections when one of the collections is either empty or completed, but the other collection still has items that can be retrieved.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bbffc-105">建议</span><span class="sxs-lookup"><span data-stu-id="bbffc-105">Suggestion</span></span>

<span data-ttu-id="bbffc-106">如果在阻止集合已完成的情况下，在 TryTakeFromAny 返回 -1 或 TakeFromAny 引发异常时用于控制流，此类代码现在应改为使用 <code>.Any(b =&gt; b.IsCompleted)</code> 检测该条件。</span><span class="sxs-lookup"><span data-stu-id="bbffc-106">If TryTakeFromAny returning -1 or TakeFromAny throwing were used for control-flow purposes in cases of a blocking collection being completed, such code should now be changed to use <code>.Any(b =&gt; b.IsCompleted)</code> to detect that condition.</span></span>

| <span data-ttu-id="bbffc-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="bbffc-107">Name</span></span>    | <span data-ttu-id="bbffc-108">“值”</span><span class="sxs-lookup"><span data-stu-id="bbffc-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bbffc-109">范围</span><span class="sxs-lookup"><span data-stu-id="bbffc-109">Scope</span></span>   |<span data-ttu-id="bbffc-110">次要</span><span class="sxs-lookup"><span data-stu-id="bbffc-110">Minor</span></span>|
|<span data-ttu-id="bbffc-111">Version</span><span class="sxs-lookup"><span data-stu-id="bbffc-111">Version</span></span>|<span data-ttu-id="bbffc-112">4.5</span><span class="sxs-lookup"><span data-stu-id="bbffc-112">4.5</span></span>|
|<span data-ttu-id="bbffc-113">类型</span><span class="sxs-lookup"><span data-stu-id="bbffc-113">Type</span></span>|<span data-ttu-id="bbffc-114">运行时</span><span class="sxs-lookup"><span data-stu-id="bbffc-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="bbffc-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="bbffc-115">Affected APIs</span></span>

- <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Int32)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Concurrent.BlockingCollection`1.TakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.Threading.CancellationToken)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.Int32)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.TimeSpan)``
- ``M:System.Collections.Concurrent.BlockingCollection`1.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{`0}[],`0@,System.TimeSpan)``

-->
