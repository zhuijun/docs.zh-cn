---
ms.openlocfilehash: 8b804d23247b95381f3ff83bc12c32215a420fb6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614413"
---
### <a name="wpf-appdomain-shutdown-handling-may-now-call-dispatcherinvoke-in-cleanup-of-weak-events"></a><span data-ttu-id="e4bd7-101">WPF AppDomain 关闭处理现在可以调用 Dispatcher.Invoke 以清理弱事件</span><span class="sxs-lookup"><span data-stu-id="e4bd7-101">WPF AppDomain Shutdown Handling May Now Call Dispatcher.Invoke in Cleanup of Weak Events</span></span>

#### <a name="details"></a><span data-ttu-id="e4bd7-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="e4bd7-102">Details</span></span>

<span data-ttu-id="e4bd7-103">在 .NET Framework 4.7.1 及更早的版本中，在 AppDomain 关闭期间，WPF 可能会在 .NET 终结器线程上创建 <xref:System.Windows.Threading.Dispatcher?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e4bd7-103">In .NET Framework 4.7.1 and earlier versions, WPF potentially creates a <xref:System.Windows.Threading.Dispatcher?displayProperty=nameWithType> on the .NET finalizer thread during AppDomain shutdown.</span></span>  <span data-ttu-id="e4bd7-104">此问题已在 .NET Framework 4.7.2 和更高版本中得到修复，方法是使弱事件的清理能够感知线程。</span><span class="sxs-lookup"><span data-stu-id="e4bd7-104">This was fixed in .NET Framework 4.7.2 and later versions by making the cleanup of weak events thread-aware.</span></span>  <span data-ttu-id="e4bd7-105">因此，WPF 可能会调用 <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> 来完成清理过程。在某些应用程序中，终结器计时的这一更改可能在 AppDomain 或进程关闭期间导致异常。</span><span class="sxs-lookup"><span data-stu-id="e4bd7-105">Due to this, WPF may call <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> to complete the cleanup process.In certain applications, this change in finalizer timing can potentially cause exceptions during AppDomain or process shutdown.</span></span>  <span data-ttu-id="e4bd7-106">这种情况常见于未在进程或 AppDomain 关闭之前正确关闭在工作线程上运行的调度程序的应用程序中。</span><span class="sxs-lookup"><span data-stu-id="e4bd7-106">This is generally seen in applications that do not correctly shut down dispatchers running on worker threads prior to process or AppDomain shutdown.</span></span>  <span data-ttu-id="e4bd7-107">此类应用程序应负责正确管理调度程序的生存期。</span><span class="sxs-lookup"><span data-stu-id="e4bd7-107">Such applications should take care to properly manage the lifetime of dispatchers.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e4bd7-108">建议</span><span class="sxs-lookup"><span data-stu-id="e4bd7-108">Suggestion</span></span>

<span data-ttu-id="e4bd7-109">在 .NET Framework 4.7.2 及更高版本中，开发人员可以禁用此修补程序以帮助缓解（但不能消除）由于清理更改而导致的计时问题。若要禁用清理中的更改，请使用以下 AppContext 标志。</span><span class="sxs-lookup"><span data-stu-id="e4bd7-109">In .NET Framework 4.7.2 and later versions, developers can disable this fix in order to help alleviate (but not eliminate) timing issues that may occur due to the cleanup change.To disable the change in cleanup, use the following AppContext flag.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotInvokeInWeakEventTableShutdownListener=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="e4bd7-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="e4bd7-110">Name</span></span>    | <span data-ttu-id="e4bd7-111">“值”</span><span class="sxs-lookup"><span data-stu-id="e4bd7-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e4bd7-112">范围</span><span class="sxs-lookup"><span data-stu-id="e4bd7-112">Scope</span></span>   | <span data-ttu-id="e4bd7-113">边缘</span><span class="sxs-lookup"><span data-stu-id="e4bd7-113">Edge</span></span>        |
| <span data-ttu-id="e4bd7-114">Version</span><span class="sxs-lookup"><span data-stu-id="e4bd7-114">Version</span></span> | <span data-ttu-id="e4bd7-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="e4bd7-115">4.7.2</span></span>       |
| <span data-ttu-id="e4bd7-116">类型</span><span class="sxs-lookup"><span data-stu-id="e4bd7-116">Type</span></span>    | <span data-ttu-id="e4bd7-117">重定目标</span><span class="sxs-lookup"><span data-stu-id="e4bd7-117">Retargeting</span></span> |
