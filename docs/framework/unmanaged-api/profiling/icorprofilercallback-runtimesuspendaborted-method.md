---
title: ICorProfilerCallback::RuntimeSuspendAborted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendAborted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type:
- apiref
ms.openlocfilehash: a3fb5c398b8ccd7caba0b005bcf03e64ecef4ba5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503245"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="32ea7-102">ICorProfilerCallback::RuntimeSuspendAborted 方法</span><span class="sxs-lookup"><span data-stu-id="32ea7-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>
<span data-ttu-id="32ea7-103">通知探查器运行时已中止正在进行的运行时挂起。</span><span class="sxs-lookup"><span data-stu-id="32ea7-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32ea7-104">语法</span><span class="sxs-lookup"><span data-stu-id="32ea7-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="32ea7-105">备注</span><span class="sxs-lookup"><span data-stu-id="32ea7-105">Remarks</span></span>  
 <span data-ttu-id="32ea7-106">如果两个线程同时尝试挂起运行时，则运行时挂起可能会中止。</span><span class="sxs-lookup"><span data-stu-id="32ea7-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="32ea7-107">[ICorProfilerCallback：： RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md)回调或 `RuntimeSuspendAborted` 回调将在具有[ICorProfilerCallback：： RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)回调的单个线程上发生。</span><span class="sxs-lookup"><span data-stu-id="32ea7-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="32ea7-108">`RuntimeSuspendAborted`保证回调与回调在同一线程上发生 `RuntimeSuspendStarted` 。</span><span class="sxs-lookup"><span data-stu-id="32ea7-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32ea7-109">要求</span><span class="sxs-lookup"><span data-stu-id="32ea7-109">Requirements</span></span>  
 <span data-ttu-id="32ea7-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="32ea7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32ea7-111">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="32ea7-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="32ea7-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32ea7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32ea7-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32ea7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32ea7-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32ea7-114">See also</span></span>

- [<span data-ttu-id="32ea7-115">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="32ea7-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
