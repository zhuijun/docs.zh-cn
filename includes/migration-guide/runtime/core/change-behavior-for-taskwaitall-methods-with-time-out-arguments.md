---
ms.openlocfilehash: 52406f1e4ea4eda417909e52cf6529631cb0ae33
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619832"
---
### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>带有超时自变量的 Task.WaitAll 方法的行为更改

#### <a name="details"></a>详细信息

<xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> 行为在 .NET Framework 4.5 中变得更加一致。在 .NET Framework 4 中，这些方法的行为不一致。 当超时到期时，如果在调用此方法之前已完成或已取消一个或多个任务，则此方法会引发 <xref:System.AggregateException?displayProperty=fullName> 异常。 在超时到期时，如果在调用此方法之前尚未完成或取消任何任务，但在调用此方法之后，一个或多个任务进入了这些状态，则该方法返回 false。<br/><br/>在 .NET Framework 4.5 中，如果在超时时间间隔到期时仍有任务在运行，这些方法重载现在将返回 false；仅当取消某个输入任务（无论是在方法调用之前还是之后取消）且没有任务仍在运行时，它们才将引发 <xref:System.AggregateException?displayProperty=fullName> 异常。

#### <a name="suggestion"></a>建议

如果 <xref:System.AggregateException?displayProperty=fullName> 已捕获作为检测在调用 <xref:System.Threading.Tasks.Task.WaitAll%2A> 之前已取消的任务的方法，该代码应通过 <xref:System.Threading.Tasks.Task.IsCanceled%2A> 属性（例如：.Any(t =&gt; t.IsCanceled)）执行相同的检测操作，因为 .NET Framework 4.6 仅当所有等待任务在超时前均已完成时才会引发。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |次要|
|Version|4.5|
|类型|运行时

#### <a name="affected-apis"></a>受影响的 API

-<xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType></li></ul>|
