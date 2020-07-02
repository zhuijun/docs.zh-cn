---
title: raceOnRCWCleanup MDA
description: 查看 raceOnRCWCleanup 托管调试助手（MDA），如果在另一个线程上或在 .NET 中释放线程堆栈上使用了 RCW，则会激活该助手。
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
ms.openlocfilehash: e86ef96bebb648c7927ae5fec8b68fc4429b268b
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803646"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="38e74-103">raceOnRCWCleanup MDA</span><span class="sxs-lookup"><span data-stu-id="38e74-103">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="38e74-104">当使用命令（如 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> 方法）发出一个调用来发布[运行时可调用包装](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) 时，如果公共语言运行时 (CLR) 检测到该包装正在使用中，则激活 `raceOnRCWCleanup` 托管调试助手 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="38e74-104">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="38e74-105">症状</span><span class="sxs-lookup"><span data-stu-id="38e74-105">Symptoms</span></span>  
 <span data-ttu-id="38e74-106">使用 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> 或类似方法释放 RCW 期间或之后发生访问冲突或内存损坏。</span><span class="sxs-lookup"><span data-stu-id="38e74-106">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="38e74-107">原因</span><span class="sxs-lookup"><span data-stu-id="38e74-107">Cause</span></span>  
 <span data-ttu-id="38e74-108">正在另一个线程中或释放线程堆栈中使用 RCW。</span><span class="sxs-lookup"><span data-stu-id="38e74-108">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="38e74-109">无法释放使用中的 RCW。</span><span class="sxs-lookup"><span data-stu-id="38e74-109">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="38e74-110">解决方法</span><span class="sxs-lookup"><span data-stu-id="38e74-110">Resolution</span></span>  
 <span data-ttu-id="38e74-111">不要释放在当前或在其他线程中可能使用的 RCW。</span><span class="sxs-lookup"><span data-stu-id="38e74-111">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="38e74-112">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="38e74-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="38e74-113">此 MDA 对 CLR 无任何影响。</span><span class="sxs-lookup"><span data-stu-id="38e74-113">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="38e74-114">Output</span><span class="sxs-lookup"><span data-stu-id="38e74-114">Output</span></span>  
 <span data-ttu-id="38e74-115">描述错误的消息。</span><span class="sxs-lookup"><span data-stu-id="38e74-115">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="38e74-116">Configuration</span><span class="sxs-lookup"><span data-stu-id="38e74-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="38e74-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="38e74-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="38e74-118">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="38e74-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="38e74-119">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="38e74-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
