---
title: ICorProfilerCallback::RuntimeSuspendFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type:
- apiref
ms.openlocfilehash: 64611fa7368f05de906b71b08bda8f1e7c460bf3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503232"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="22f08-102">ICorProfilerCallback::RuntimeSuspendFinished 方法</span><span class="sxs-lookup"><span data-stu-id="22f08-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>
<span data-ttu-id="22f08-103">通知探查器运行时已完成所有运行时线程的挂起。</span><span class="sxs-lookup"><span data-stu-id="22f08-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22f08-104">语法</span><span class="sxs-lookup"><span data-stu-id="22f08-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="22f08-105">备注</span><span class="sxs-lookup"><span data-stu-id="22f08-105">Remarks</span></span>  
 <span data-ttu-id="22f08-106">允许非托管代码中的所有运行时线程继续运行，直到它们尝试重新进入运行时。</span><span class="sxs-lookup"><span data-stu-id="22f08-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="22f08-107">此时，它们也将被挂起，直到运行时恢复。</span><span class="sxs-lookup"><span data-stu-id="22f08-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="22f08-108">这也适用于输入运行时的新线程。</span><span class="sxs-lookup"><span data-stu-id="22f08-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="22f08-109">如果运行时中的所有线程已处于中断的代码中，则会立即将其挂起，或者当它们到达中断的代码时要求它们挂起。</span><span class="sxs-lookup"><span data-stu-id="22f08-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="22f08-110">`RuntimeSuspendFinished`保证回调与[ICorProfilerCallback：： RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)回调在同一线程上发生。</span><span class="sxs-lookup"><span data-stu-id="22f08-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22f08-111">要求</span><span class="sxs-lookup"><span data-stu-id="22f08-111">Requirements</span></span>  
 <span data-ttu-id="22f08-112">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="22f08-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22f08-113">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="22f08-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="22f08-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22f08-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22f08-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22f08-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22f08-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="22f08-116">See also</span></span>

- [<span data-ttu-id="22f08-117">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="22f08-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="22f08-118">RuntimeSuspendAborted 方法</span><span class="sxs-lookup"><span data-stu-id="22f08-118">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
