---
ms.openlocfilehash: 58dbb54d42d89b450134758072e3133ae4e6b13d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497950"
---
### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a><span data-ttu-id="85a2e-101">释放对象后，System.Threading.Tasks.Task 不再引发 ObjectDisposedException</span><span class="sxs-lookup"><span data-stu-id="85a2e-101">System.Threading.Tasks.Task no longer throw ObjectDisposedException after object is disposed</span></span>

#### <a name="details"></a><span data-ttu-id="85a2e-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="85a2e-102">Details</span></span>

<span data-ttu-id="85a2e-103">除 <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle> 外，<xref:System.Threading.Tasks.Task?displayProperty=fullName> 方法在处置对象后不再引发 <xref:System.ObjectDisposedException?displayProperty=fullName> 异常。此更改支持使用缓存任务。</span><span class="sxs-lookup"><span data-stu-id="85a2e-103">Except for <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, <xref:System.Threading.Tasks.Task?displayProperty=fullName> methods no longer throw an <xref:System.ObjectDisposedException?displayProperty=fullName> exception after the object is disposed.This change supports the use of cached tasks.</span></span> <span data-ttu-id="85a2e-104">例如，方法会返回一个缓存任务来表示已完成的操作，而不是分配新任务。</span><span class="sxs-lookup"><span data-stu-id="85a2e-104">For example, a method can return a cached task to represent an already completed operation instead of allocating a new task.</span></span> <span data-ttu-id="85a2e-105">在以前的 .NET Framework 版本中无法执行此操作，因为任务的任何使用者都可以处置它（呈现为不可用）。</span><span class="sxs-lookup"><span data-stu-id="85a2e-105">This was impossible in previous .NET Framework versions, because any consumer of the task could dispose of it, which rendered it unusable.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="85a2e-106">建议</span><span class="sxs-lookup"><span data-stu-id="85a2e-106">Suggestion</span></span>

<span data-ttu-id="85a2e-107">请注意，如果释放对象，Task 方法可能不再引发 <xref:System.ObjectDisposedException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="85a2e-107">Be aware that Task methods may no longer throw <xref:System.ObjectDisposedException?displayProperty=fullName> in cases when the object is disposed.</span></span> <span data-ttu-id="85a2e-108">如果某个应用依靠此异常了解任务是否已释放，应对其进行更新以使用 <xref:System.Threading.Tasks.Task.Status> 显式检查任务状态。</span><span class="sxs-lookup"><span data-stu-id="85a2e-108">If an app was depending on this exception to know that a task was disposed, it should be updated to explicitly check the task's status using <xref:System.Threading.Tasks.Task.Status>.</span></span>

| <span data-ttu-id="85a2e-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="85a2e-109">Name</span></span>    | <span data-ttu-id="85a2e-110">“值”</span><span class="sxs-lookup"><span data-stu-id="85a2e-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="85a2e-111">范围</span><span class="sxs-lookup"><span data-stu-id="85a2e-111">Scope</span></span>   |<span data-ttu-id="85a2e-112">次要</span><span class="sxs-lookup"><span data-stu-id="85a2e-112">Minor</span></span>|
|<span data-ttu-id="85a2e-113">Version</span><span class="sxs-lookup"><span data-stu-id="85a2e-113">Version</span></span>|<span data-ttu-id="85a2e-114">4.5</span><span class="sxs-lookup"><span data-stu-id="85a2e-114">4.5</span></span>|
|<span data-ttu-id="85a2e-115">类型</span><span class="sxs-lookup"><span data-stu-id="85a2e-115">Type</span></span>|<span data-ttu-id="85a2e-116">运行时</span><span class="sxs-lookup"><span data-stu-id="85a2e-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="85a2e-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="85a2e-117">Affected APIs</span></span>

<span data-ttu-id="85a2e-118">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="85a2e-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
