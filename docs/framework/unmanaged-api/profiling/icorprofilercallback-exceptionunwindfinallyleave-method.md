---
title: ICorProfilerCallback::ExceptionUnwindFinallyLeave 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type:
- apiref
ms.openlocfilehash: 8da9098e882dd4b4c1f60e4428ebe68421e629e1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500138"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="cf343-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave 方法</span><span class="sxs-lookup"><span data-stu-id="cf343-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="cf343-103">通知探查器异常处理的展开阶段已离开 `finally` 子句。</span><span class="sxs-lookup"><span data-stu-id="cf343-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf343-104">语法</span><span class="sxs-lookup"><span data-stu-id="cf343-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="cf343-105">备注</span><span class="sxs-lookup"><span data-stu-id="cf343-105">Remarks</span></span>  
 <span data-ttu-id="cf343-106">探查器不应在此调用期间被阻止，因为堆栈可能不处于允许垃圾回收的状态，因此无法启用抢先垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="cf343-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="cf343-107">如果探查器在此处阻止并且试图进行垃圾回收，则运行时将被阻止，直到此回调返回。</span><span class="sxs-lookup"><span data-stu-id="cf343-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="cf343-108">此外，在此调用期间，探查器不得调入托管代码或以任何方式导致托管内存分配。</span><span class="sxs-lookup"><span data-stu-id="cf343-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf343-109">要求</span><span class="sxs-lookup"><span data-stu-id="cf343-109">Requirements</span></span>  
 <span data-ttu-id="cf343-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cf343-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf343-111">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cf343-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cf343-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf343-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf343-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf343-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf343-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cf343-114">See also</span></span>

- [<span data-ttu-id="cf343-115">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="cf343-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="cf343-116">ExceptionUnwindFinallyEnter 方法</span><span class="sxs-lookup"><span data-stu-id="cf343-116">ExceptionUnwindFinallyEnter Method</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)
