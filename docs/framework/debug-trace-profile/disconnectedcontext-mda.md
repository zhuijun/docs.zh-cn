---
title: disconnectedContext MDA
description: 查看 .NET 中的 disconnectedContext 托管调试助手，当 CLR 试图转换到断开连接的单元或上下文时，将调用该助手。
ms.date: 03/30/2017
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
ms.openlocfilehash: 0b24aadefab7a7cb2a5294f25e674d188beec814
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416078"
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="61460-103">disconnectedContext MDA</span><span class="sxs-lookup"><span data-stu-id="61460-103">disconnectedContext MDA</span></span>
<span data-ttu-id="61460-104">如果 CLR 在处理关于 COM 对象的请求时尝试转换到断开连接的单元或上下文，将激活 `disconnectedContext` 托管调试助手 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="61460-104">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="61460-105">症状</span><span class="sxs-lookup"><span data-stu-id="61460-105">Symptoms</span></span>  
 <span data-ttu-id="61460-106">将对[运行时可调通包装器](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) 的调用发送到当前单元或上下文中的基础 COM 组件，而不是发送到调用所在的 COM 组件。</span><span class="sxs-lookup"><span data-stu-id="61460-106">Calls made on a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="61460-107">如果该 COM 组件不是多线程的（例如，在单线程单元 (STA) 组件的情况中），则将导致损坏或数据丢失。</span><span class="sxs-lookup"><span data-stu-id="61460-107">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="61460-108">或者，如果 RCW 本身是一个代理，则该调用可能会引发 HRESULT 为 RPC_E_WRONG_THREAD 的 <xref:System.Runtime.InteropServices.COMException>。</span><span class="sxs-lookup"><span data-stu-id="61460-108">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="61460-109">原因</span><span class="sxs-lookup"><span data-stu-id="61460-109">Cause</span></span>  
 <span data-ttu-id="61460-110">当 CLR 尝试转换为 OLE 单元或上下文时，OLE 单元或上下文已关闭。</span><span class="sxs-lookup"><span data-stu-id="61460-110">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="61460-111">最常见的原因是：在 STA 单元拥有的所有 COM 组件完全释放之前，STA 单元已经关闭。在用户代码对 RCW 进行显式调用时或在 CLR 自行操作 COM 组件时（例如，在对关联的 RCW 进行了垃圾回收后，CLR 释放 COM 组件），可能会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="61460-111">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="61460-112">解决方法</span><span class="sxs-lookup"><span data-stu-id="61460-112">Resolution</span></span>  
 <span data-ttu-id="61460-113">若要避免发生此问题，请确保在应用程序处理完单元中存在的所有对象之前，拥有 STA 的线程不会终止。</span><span class="sxs-lookup"><span data-stu-id="61460-113">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="61460-114">这也同样适用于上下文；请确保在应用程序处理完上下文中存在的所有 COM 组件之前，上下文不会关闭。</span><span class="sxs-lookup"><span data-stu-id="61460-114">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="61460-115">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="61460-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="61460-116">此 MDA 对 CLR 无任何影响。</span><span class="sxs-lookup"><span data-stu-id="61460-116">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="61460-117">它只报告有关断开连接的上下文的数据。</span><span class="sxs-lookup"><span data-stu-id="61460-117">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="61460-118">输出</span><span class="sxs-lookup"><span data-stu-id="61460-118">Output</span></span>  
 <span data-ttu-id="61460-119">报告断开连接的单元或上下文的上下文 Cookie。</span><span class="sxs-lookup"><span data-stu-id="61460-119">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="61460-120">配置</span><span class="sxs-lookup"><span data-stu-id="61460-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="61460-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="61460-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="61460-122">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="61460-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="61460-123">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="61460-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
