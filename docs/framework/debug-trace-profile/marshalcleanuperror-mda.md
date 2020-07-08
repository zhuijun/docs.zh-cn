---
title: marshalCleanupError MDA
description: 查看 marshalCleanupError 托管调试助手（MDA），因为在清理临时结构时出现意外错误。
ms.date: 03/30/2017
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
ms.openlocfilehash: 3c7498d6f51484de3a2e84d611a2634f53724ab6
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051605"
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="5c1ef-103">marshalCleanupError MDA</span><span class="sxs-lookup"><span data-stu-id="5c1ef-103">marshalCleanupError MDA</span></span>
<span data-ttu-id="5c1ef-104">如果公共语言运行时 (CLR) 在尝试清理那些用于封送本机代码和托管代码边界之间的数据类型的临时结构和内存时遇到错误，则将激活 `marshalCleanupError` 托管调试助手 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="5c1ef-104">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5c1ef-105">症状</span><span class="sxs-lookup"><span data-stu-id="5c1ef-105">Symptoms</span></span>  
 <span data-ttu-id="5c1ef-106">进行本机代码和托管代码转换时发生内存泄漏，线程区域性等运行时状态无法还原，或 <xref:System.Runtime.InteropServices.SafeHandle> 清理中发生错误。</span><span class="sxs-lookup"><span data-stu-id="5c1ef-106">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5c1ef-107">原因</span><span class="sxs-lookup"><span data-stu-id="5c1ef-107">Cause</span></span>  
 <span data-ttu-id="5c1ef-108">清理临时结构时发生意外错误。</span><span class="sxs-lookup"><span data-stu-id="5c1ef-108">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5c1ef-109">解决方法</span><span class="sxs-lookup"><span data-stu-id="5c1ef-109">Resolution</span></span>  
 <span data-ttu-id="5c1ef-110">检查所有 <xref:System.Runtime.InteropServices.SafeHandle> 析构函数、终结器和自定义封送拆收器实现中是否存在错误。</span><span class="sxs-lookup"><span data-stu-id="5c1ef-110">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5c1ef-111">对运行时的影响</span><span class="sxs-lookup"><span data-stu-id="5c1ef-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="5c1ef-112">此 MDA 对 CLR 无任何影响。</span><span class="sxs-lookup"><span data-stu-id="5c1ef-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5c1ef-113">输出</span><span class="sxs-lookup"><span data-stu-id="5c1ef-113">Output</span></span>  
 <span data-ttu-id="5c1ef-114">报告在清理期间失败的操作的消息。</span><span class="sxs-lookup"><span data-stu-id="5c1ef-114">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5c1ef-115">配置</span><span class="sxs-lookup"><span data-stu-id="5c1ef-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c1ef-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="5c1ef-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="5c1ef-117">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="5c1ef-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="5c1ef-118">互操作封送处理</span><span class="sxs-lookup"><span data-stu-id="5c1ef-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
