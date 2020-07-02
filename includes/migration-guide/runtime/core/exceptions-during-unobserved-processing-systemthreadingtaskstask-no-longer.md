---
ms.openlocfilehash: 5ba2ddb76ab946339449246840667ba4a48e9c66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619837"
---
### <a name="exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a><span data-ttu-id="923f1-101">System.Threading.Tasks.Task 未观察处理中的异常不再在终接器线程上传播</span><span class="sxs-lookup"><span data-stu-id="923f1-101">Exceptions during unobserved processing in System.Threading.Tasks.Task no longer propagate on finalizer thread</span></span>

#### <a name="details"></a><span data-ttu-id="923f1-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="923f1-102">Details</span></span>

<span data-ttu-id="923f1-103">由于 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 类表示异步操作，它捕获在异步处理过程中出现的所有非严重异常。</span><span class="sxs-lookup"><span data-stu-id="923f1-103">Because the <xref:System.Threading.Tasks.Task?displayProperty=fullName> class represents an asynchronous operation, it catches all non-severe exceptions that occur during asynchronous processing.</span></span> <span data-ttu-id="923f1-104">在 .NET Framework 4.5 中，如果未观察到异常，且代码绝不会等待任务，则异常将不再在终结器线程上传播并在垃圾回收期间不会导致进程崩溃。</span><span class="sxs-lookup"><span data-stu-id="923f1-104">In the .NET Framework 4.5, if an exception is not observed and your code never waits on the task, the exception will no longer propagate on the finalizer thread and crash the process during garbage collection.</span></span> <span data-ttu-id="923f1-105">此更改增强了使用 Task 类执行未观察到的异步处理的应用程序的可靠性。</span><span class="sxs-lookup"><span data-stu-id="923f1-105">This change enhances the reliability of applications that use the Task class to perform unobserved asynchronous processing.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="923f1-106">建议</span><span class="sxs-lookup"><span data-stu-id="923f1-106">Suggestion</span></span>

<span data-ttu-id="923f1-107">如果应用依赖于未观察到的异步异常传播到终接器线程，可通过向 <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> 事件提供相应的处理程序，或通过设置[运行时配置元素](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)来还原以前的行为。</span><span class="sxs-lookup"><span data-stu-id="923f1-107">If an app depends on unobserved asynchronous exceptions propagating to the finalizer thread, the previous behavior can be restored by providing an appropriate handler for the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event, or by setting a [runtime configuration element](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md).</span></span>

| <span data-ttu-id="923f1-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="923f1-108">Name</span></span>    | <span data-ttu-id="923f1-109">“值”</span><span class="sxs-lookup"><span data-stu-id="923f1-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="923f1-110">范围</span><span class="sxs-lookup"><span data-stu-id="923f1-110">Scope</span></span>   |<span data-ttu-id="923f1-111">边缘</span><span class="sxs-lookup"><span data-stu-id="923f1-111">Edge</span></span>|
|<span data-ttu-id="923f1-112">Version</span><span class="sxs-lookup"><span data-stu-id="923f1-112">Version</span></span>|<span data-ttu-id="923f1-113">4.5</span><span class="sxs-lookup"><span data-stu-id="923f1-113">4.5</span></span>|
|<span data-ttu-id="923f1-114">类型</span><span class="sxs-lookup"><span data-stu-id="923f1-114">Type</span></span>|<span data-ttu-id="923f1-115">运行时</span><span class="sxs-lookup"><span data-stu-id="923f1-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="923f1-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="923f1-116">Affected APIs</span></span>

-<xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Action,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start(System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType></li></ul>|
