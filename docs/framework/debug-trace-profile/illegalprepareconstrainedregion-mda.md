---
title: illegalPrepareConstrainedRegion MDA
description: 查看 illegalPrepareConstrainedRegion 托管调试助手，如果 PrepareConstrainedRegions 调用后不是 try 语句，则会调用该助手。
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
ms.openlocfilehash: d6a0d1d95840ebd735806c5547730ae9e0b2aace
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051280"
---
# <a name="illegalprepareconstrainedregion-mda"></a><span data-ttu-id="38275-103">illegalPrepareConstrainedRegion MDA</span><span class="sxs-lookup"><span data-stu-id="38275-103">illegalPrepareConstrainedRegion MDA</span></span>
<span data-ttu-id="38275-104"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> 方法调用不立即出现在异常处理程序的 `try` 语句之前时，会激活 `illegalPrepareConstrainedRegion` 托管调试助手 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="38275-104">The `illegalPrepareConstrainedRegion` managed debugging assistant (MDA) is activated when a <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> method call does not immediately precede the `try` statement of the exception handler.</span></span> <span data-ttu-id="38275-105">此限制处于 MSIL 级别，因此允许调用和 `try` 之间存在非代码生成的源，比如注释。</span><span class="sxs-lookup"><span data-stu-id="38275-105">This restriction is at the MSIL level, so it is permissible to have non-code-generating source between the call and the `try`, such as comments.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="38275-106">症状</span><span class="sxs-lookup"><span data-stu-id="38275-106">Symptoms</span></span>  
 <span data-ttu-id="38275-107">受约束的执行区域 (CER) 从未以这种方式处理，而是作为简单的异常处理块（`finally` 或 `catch`）处理。</span><span class="sxs-lookup"><span data-stu-id="38275-107">A constrained execution region (CER) that is never treated as such, but as a simple exception handling block (`finally` or `catch`).</span></span> <span data-ttu-id="38275-108">因此，如果内存不足或线程中止，此区域不会运行。</span><span class="sxs-lookup"><span data-stu-id="38275-108">As a consequence, the region does not run in the event of an out-of-memory condition or a thread abort.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="38275-109">原因</span><span class="sxs-lookup"><span data-stu-id="38275-109">Cause</span></span>  
 <span data-ttu-id="38275-110">CER 的准备模式未正确执行。</span><span class="sxs-lookup"><span data-stu-id="38275-110">The preparation pattern for a CER is not followed correctly.</span></span>  <span data-ttu-id="38275-111">这是一个错误事件。</span><span class="sxs-lookup"><span data-stu-id="38275-111">This is an error event.</span></span> <span data-ttu-id="38275-112"><xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>用于标记异常处理程序的方法调用在其块中引入 CER 时 `catch` / `finally` / `fault` / `filter` 必须在语句之前立即使用 `try` 。</span><span class="sxs-lookup"><span data-stu-id="38275-112">The <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method call used to mark exception handlers as introducing a CER in their `catch`/`finally`/`fault`/`filter` blocks must be used immediately before the `try` statement.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="38275-113">解决方法</span><span class="sxs-lookup"><span data-stu-id="38275-113">Resolution</span></span>  
 <span data-ttu-id="38275-114">确保对 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 的调用在 `try` 语句之前立即发生。</span><span class="sxs-lookup"><span data-stu-id="38275-114">Ensure that the call to <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> happens immediately before the `try` statement.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="38275-115">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="38275-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="38275-116">此 MDA 对 CLR 无任何影响。</span><span class="sxs-lookup"><span data-stu-id="38275-116">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="38275-117">输出</span><span class="sxs-lookup"><span data-stu-id="38275-117">Output</span></span>  
 <span data-ttu-id="38275-118">MDA 显示调用 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> 方法的方法名称、MSIL 偏移，以及指示调用不会立即出现在 try 块开头的消息。</span><span class="sxs-lookup"><span data-stu-id="38275-118">The MDA displays the name of the method calling the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> method, the MSIL offset, and a message indicating the call does not immediately precede the beginning of the try block.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="38275-119">配置</span><span class="sxs-lookup"><span data-stu-id="38275-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="38275-120">示例</span><span class="sxs-lookup"><span data-stu-id="38275-120">Example</span></span>  
 <span data-ttu-id="38275-121">以下示例代码演示导致激活此 MDA 的模式。</span><span class="sxs-lookup"><span data-stu-id="38275-121">The following code example demonstrates the pattern that causes this MDA to be activated.</span></span>  
  
```csharp
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="38275-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="38275-122">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [<span data-ttu-id="38275-123">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="38275-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="38275-124">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="38275-124">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
