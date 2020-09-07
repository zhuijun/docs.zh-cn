---
ms.openlocfilehash: 9d0791f00db7d830fc5d327af30218a0bbfcb25f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496147"
---
### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a><span data-ttu-id="50a0e-101">带有超时自变量的 Task.WaitAll 方法的行为更改</span><span class="sxs-lookup"><span data-stu-id="50a0e-101">Change in behavior for Task.WaitAll methods with time-out arguments</span></span>

#### <a name="details"></a><span data-ttu-id="50a0e-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="50a0e-102">Details</span></span>

<span data-ttu-id="50a0e-103"><xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> 行为在 .NET Framework 4.5 中变得更加一致。在 .NET Framework 4 中，这些方法的行为不一致。</span><span class="sxs-lookup"><span data-stu-id="50a0e-103"><xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> behavior was made more consistent in .NET Framework 4.5.In the .NET Framework 4, these methods behaved inconsistently.</span></span> <span data-ttu-id="50a0e-104">当超时到期时，如果在调用此方法之前已完成或已取消一个或多个任务，则此方法会引发 <xref:System.AggregateException?displayProperty=fullName> 异常。</span><span class="sxs-lookup"><span data-stu-id="50a0e-104">When the time-out expired, if one or more tasks were completed or canceled before the method call, the method threw an <xref:System.AggregateException?displayProperty=fullName> exception.</span></span> <span data-ttu-id="50a0e-105">在超时到期时，如果在调用此方法之前尚未完成或取消任何任务，但在调用此方法之后，一个或多个任务进入了这些状态，则该方法返回 false。</span><span class="sxs-lookup"><span data-stu-id="50a0e-105">When the time-out expired, if no tasks were completed or canceled before the method call, but one or more tasks entered these states after the method call, the method returned false.</span></span><br/><br/><span data-ttu-id="50a0e-106">在 .NET Framework 4.5 中，如果在超时时间间隔到期时仍有任务在运行，这些方法重载现在将返回 false；仅当取消某个输入任务（无论是在方法调用之前还是之后取消）且没有任务仍在运行时，它们才将引发 <xref:System.AggregateException?displayProperty=fullName> 异常。</span><span class="sxs-lookup"><span data-stu-id="50a0e-106">In the .NET Framework 4.5, these method overloads now return false if any tasks are still running when the time-out interval expired, and they throw an <xref:System.AggregateException?displayProperty=fullName> exception only if an input task was cancelled (regardless of whether it was before or after the method call) and no other tasks are still running.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="50a0e-107">建议</span><span class="sxs-lookup"><span data-stu-id="50a0e-107">Suggestion</span></span>

<span data-ttu-id="50a0e-108">如果 <xref:System.AggregateException?displayProperty=fullName> 已捕获作为检测在调用 <xref:System.Threading.Tasks.Task.WaitAll%2A> 之前已取消的任务的方法，该代码应通过 <xref:System.Threading.Tasks.Task.IsCanceled%2A> 属性（例如：.Any(t =&gt; t.IsCanceled)）执行相同的检测操作，因为 .NET Framework 4.6 仅当所有等待任务在超时前均已完成时才会引发。</span><span class="sxs-lookup"><span data-stu-id="50a0e-108">If an <xref:System.AggregateException?displayProperty=fullName> was being caught as a means of detecting a task that was cancelled prior to the <xref:System.Threading.Tasks.Task.WaitAll%2A> call being invoked, that code should instead do the same detection via the  <xref:System.Threading.Tasks.Task.IsCanceled%2A> property (for example: .Any(t =&gt; t.IsCanceled)) since .NET Framework 4.6 will only throw in that case if all awaited tasks are completed prior to the timeout.</span></span>

| <span data-ttu-id="50a0e-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="50a0e-109">Name</span></span>    | <span data-ttu-id="50a0e-110">“值”</span><span class="sxs-lookup"><span data-stu-id="50a0e-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="50a0e-111">范围</span><span class="sxs-lookup"><span data-stu-id="50a0e-111">Scope</span></span>   |<span data-ttu-id="50a0e-112">次要</span><span class="sxs-lookup"><span data-stu-id="50a0e-112">Minor</span></span>|
|<span data-ttu-id="50a0e-113">Version</span><span class="sxs-lookup"><span data-stu-id="50a0e-113">Version</span></span>|<span data-ttu-id="50a0e-114">4.5</span><span class="sxs-lookup"><span data-stu-id="50a0e-114">4.5</span></span>|
|<span data-ttu-id="50a0e-115">类型</span><span class="sxs-lookup"><span data-stu-id="50a0e-115">Type</span></span>|<span data-ttu-id="50a0e-116">运行时</span><span class="sxs-lookup"><span data-stu-id="50a0e-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="50a0e-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="50a0e-117">Affected APIs</span></span>

- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)`
- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)`
- `M:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)`

-->
