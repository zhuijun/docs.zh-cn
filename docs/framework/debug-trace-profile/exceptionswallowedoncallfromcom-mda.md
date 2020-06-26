---
title: exceptionSwallowedOnCallFromCom MDA
description: 查看 .NET 中的 exceptionSwallowedOnCallFromCOM 托管调试助手。 如果引发了异常，但没有正确的报告方法，则会发生此 MDA。
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
ms.openlocfilehash: 434f06cf953147d5c245e625db997bed6dbef700
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415948"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a><span data-ttu-id="0b2d9-104">exceptionSwallowedOnCallFromCom MDA</span><span class="sxs-lookup"><span data-stu-id="0b2d9-104">exceptionSwallowedOnCallFromCom MDA</span></span>
<span data-ttu-id="0b2d9-105">如果在通过不具有非托管 HRESULT 返回类型的方法从 COM 中调用公共语言运行时 (CLR) 代码时，引发了一个异常，将激活 `exceptionSwallowedOnCallFromCOM` 托管调试助手 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="0b2d9-105">The `exceptionSwallowedOnCallFromCOM` managed debugging assistant (MDA) is activated when an exception is thrown from common language runtime (CLR) code called from COM via a method that does not have an unmanaged HRESULT return type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="0b2d9-106">症状</span><span class="sxs-lookup"><span data-stu-id="0b2d9-106">Symptoms</span></span>  
 <span data-ttu-id="0b2d9-107">调用 COM 中的某个托管组件返回值 FALSE 或 0。</span><span class="sxs-lookup"><span data-stu-id="0b2d9-107">A call to a managed component from COM returns with a value of FALSE or 0.</span></span> <span data-ttu-id="0b2d9-108">或者，如果该方法具有 void 返回类型，则可能没有任何迹象显示在执行该方法期间引发了异常。</span><span class="sxs-lookup"><span data-stu-id="0b2d9-108">Alternatively, if the method has a void return type, there may be no indication that an exception was thrown during the execution of the method.</span></span> <span data-ttu-id="0b2d9-109">在这种情况下，将以静默方式捕获异常并且执行将返回到 COM 调用方。</span><span class="sxs-lookup"><span data-stu-id="0b2d9-109">In this case, the exception will be silently caught and execution will return to the COM caller.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="0b2d9-110">原因</span><span class="sxs-lookup"><span data-stu-id="0b2d9-110">Cause</span></span>  
 <span data-ttu-id="0b2d9-111">引发了一个异常，但是没有有效的方法来报告该异常。</span><span class="sxs-lookup"><span data-stu-id="0b2d9-111">An exception was thrown, but there is no valid way to report it.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="0b2d9-112">解决方法</span><span class="sxs-lookup"><span data-stu-id="0b2d9-112">Resolution</span></span>  
 <span data-ttu-id="0b2d9-113">仅提供信息，不一定会指出 Bug。</span><span class="sxs-lookup"><span data-stu-id="0b2d9-113">Informational only, not necessarily indicative of a bug.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0b2d9-114">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="0b2d9-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="0b2d9-115">此 MDA 对 CLR 无任何影响。</span><span class="sxs-lookup"><span data-stu-id="0b2d9-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="0b2d9-116">它只报告有关以静默方式捕获的异常的数据。</span><span class="sxs-lookup"><span data-stu-id="0b2d9-116">It only reports data about silently caught exceptions.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0b2d9-117">输出</span><span class="sxs-lookup"><span data-stu-id="0b2d9-117">Output</span></span>  
 <span data-ttu-id="0b2d9-118">信息性消息包括方法名称、类型名称和异常消息。</span><span class="sxs-lookup"><span data-stu-id="0b2d9-118">Informational message containing the method name, type name, and exception message.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="0b2d9-119">配置</span><span class="sxs-lookup"><span data-stu-id="0b2d9-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b2d9-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="0b2d9-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="0b2d9-121">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="0b2d9-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="0b2d9-122">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="0b2d9-122">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
