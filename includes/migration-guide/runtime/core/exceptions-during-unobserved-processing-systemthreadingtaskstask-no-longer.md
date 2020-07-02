---
ms.openlocfilehash: 5ba2ddb76ab946339449246840667ba4a48e9c66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619837"
---
### <a name="exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>System.Threading.Tasks.Task 未观察处理中的异常不再在终接器线程上传播

#### <a name="details"></a>详细信息

由于 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 类表示异步操作，它捕获在异步处理过程中出现的所有非严重异常。 在 .NET Framework 4.5 中，如果未观察到异常，且代码绝不会等待任务，则异常将不再在终结器线程上传播并在垃圾回收期间不会导致进程崩溃。 此更改增强了使用 Task 类执行未观察到的异步处理的应用程序的可靠性。

#### <a name="suggestion"></a>建议

如果应用依赖于未观察到的异步异常传播到终接器线程，可通过向 <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> 事件提供相应的处理程序，或通过设置[运行时配置元素](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)来还原以前的行为。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.5|
|类型|运行时

#### <a name="affected-apis"></a>受影响的 API

-<xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Action,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start(System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType></li></ul>|
