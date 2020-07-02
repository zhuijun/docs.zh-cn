---
ms.openlocfilehash: 3eab96149be1e40d528cfd552bbe05ca766cf4e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619842"
---
### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a><span data-ttu-id="b99b8-101">释放对象后，System.Threading.Tasks.Task 不再引发 ObjectDisposedException</span><span class="sxs-lookup"><span data-stu-id="b99b8-101">System.Threading.Tasks.Task no longer throw ObjectDisposedException after object is disposed</span></span>

#### <a name="details"></a><span data-ttu-id="b99b8-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="b99b8-102">Details</span></span>

<span data-ttu-id="b99b8-103">除 <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle> 外，<xref:System.Threading.Tasks.Task?displayProperty=fullName> 方法在处置对象后不再引发 <xref:System.ObjectDisposedException?displayProperty=fullName> 异常。此更改支持使用缓存任务。</span><span class="sxs-lookup"><span data-stu-id="b99b8-103">Except for <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, <xref:System.Threading.Tasks.Task?displayProperty=fullName> methods no longer throw an <xref:System.ObjectDisposedException?displayProperty=fullName> exception after the object is disposed.This change supports the use of cached tasks.</span></span> <span data-ttu-id="b99b8-104">例如，方法会返回一个缓存任务来表示已完成的操作，而不是分配新任务。</span><span class="sxs-lookup"><span data-stu-id="b99b8-104">For example, a method can return a cached task to represent an already completed operation instead of allocating a new task.</span></span> <span data-ttu-id="b99b8-105">在以前的 .NET Framework 版本中无法执行此操作，因为任务的任何使用者都可以处置它（呈现为不可用）。</span><span class="sxs-lookup"><span data-stu-id="b99b8-105">This was impossible in previous .NET Framework versions, because any consumer of the task could dispose of it, which rendered it unusable.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b99b8-106">建议</span><span class="sxs-lookup"><span data-stu-id="b99b8-106">Suggestion</span></span>

<span data-ttu-id="b99b8-107">请注意，如果释放对象，Task 方法可能不再引发 <xref:System.ObjectDisposedException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="b99b8-107">Be aware that Task methods may no longer throw <xref:System.ObjectDisposedException?displayProperty=fullName> in cases when the object is disposed.</span></span> <span data-ttu-id="b99b8-108">如果某个应用依靠此异常了解任务是否已释放，应对其进行更新以使用 <xref:System.Threading.Tasks.Task.Status> 显式检查任务状态。</span><span class="sxs-lookup"><span data-stu-id="b99b8-108">If an app was depending on this exception to know that a task was disposed, it should be updated to explicitly check the task's status using <xref:System.Threading.Tasks.Task.Status>.</span></span>

| <span data-ttu-id="b99b8-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="b99b8-109">Name</span></span>    | <span data-ttu-id="b99b8-110">“值”</span><span class="sxs-lookup"><span data-stu-id="b99b8-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b99b8-111">范围</span><span class="sxs-lookup"><span data-stu-id="b99b8-111">Scope</span></span>   |<span data-ttu-id="b99b8-112">次要</span><span class="sxs-lookup"><span data-stu-id="b99b8-112">Minor</span></span>|
|<span data-ttu-id="b99b8-113">Version</span><span class="sxs-lookup"><span data-stu-id="b99b8-113">Version</span></span>|<span data-ttu-id="b99b8-114">4.5</span><span class="sxs-lookup"><span data-stu-id="b99b8-114">4.5</span></span>|
|<span data-ttu-id="b99b8-115">类型</span><span class="sxs-lookup"><span data-stu-id="b99b8-115">Type</span></span>|<span data-ttu-id="b99b8-116">运行时</span><span class="sxs-lookup"><span data-stu-id="b99b8-116">Runtime</span></span>|
