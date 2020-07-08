---
title: invalidIUnknown MDA
description: 查看 invalidIUnknown 托管调试助手（MDA），在将无效的 IUnknown 指针传递到本机代码的托管代码时激活该助手。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
ms.openlocfilehash: 65d704463ed746390ff1710b590bf080013bf53d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051722"
---
# <a name="invalidiunknown-mda"></a><span data-ttu-id="b03ce-103">invalidIUnknown MDA</span><span class="sxs-lookup"><span data-stu-id="b03ce-103">invalidIUnknown MDA</span></span>
<span data-ttu-id="b03ce-104">当将无效的`IUnknown` 指针从本地代码传递到托管代码时，`invalidIUnknown`托管调试助手 (MDA) 将被激活。</span><span class="sxs-lookup"><span data-stu-id="b03ce-104">The `invalidIUnknown` managed debugging assistant (MDA) is activated when an invalid `IUnknown` pointer is passed to managed code from native code.</span></span> <span data-ttu-id="b03ce-105">当查询 `IUnknown` 接口时，`IUnknown` 将无法成功返回。</span><span class="sxs-lookup"><span data-stu-id="b03ce-105">The `IUnknown` fails to return success when queried for the `IUnknown` interface.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b03ce-106">症状</span><span class="sxs-lookup"><span data-stu-id="b03ce-106">Symptoms</span></span>  
 <span data-ttu-id="b03ce-107">参数封送处理期间，封送处理某个 COM 接口指针时，发生意外错误。</span><span class="sxs-lookup"><span data-stu-id="b03ce-107">An unexpected error occurs when marshaling a COM interface pointer during argument marshaling.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b03ce-108">原因</span><span class="sxs-lookup"><span data-stu-id="b03ce-108">Cause</span></span>  
 <span data-ttu-id="b03ce-109">将 COM 接口上一个不正确的 `QueryInterface` 实现传递给了 CLR。</span><span class="sxs-lookup"><span data-stu-id="b03ce-109">An incorrect `QueryInterface` implementation on the COM interface passed to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b03ce-110">解决方法</span><span class="sxs-lookup"><span data-stu-id="b03ce-110">Resolution</span></span>  
 <span data-ttu-id="b03ce-111">更正 `QueryInterface` 实现。</span><span class="sxs-lookup"><span data-stu-id="b03ce-111">Correct the `QueryInterface` implementation.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b03ce-112">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="b03ce-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="b03ce-113">此 MDA 对 CLR 无任何影响。</span><span class="sxs-lookup"><span data-stu-id="b03ce-113">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b03ce-114">输出</span><span class="sxs-lookup"><span data-stu-id="b03ce-114">Output</span></span>  
 <span data-ttu-id="b03ce-115">对错误的说明。</span><span class="sxs-lookup"><span data-stu-id="b03ce-115">The description of the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b03ce-116">配置</span><span class="sxs-lookup"><span data-stu-id="b03ce-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b03ce-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="b03ce-117">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="b03ce-118">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="b03ce-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="b03ce-119">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="b03ce-119">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
