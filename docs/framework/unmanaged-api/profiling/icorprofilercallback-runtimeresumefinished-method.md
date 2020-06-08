---
title: ICorProfilerCallback::RuntimeResumeFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeFinished
helpviewer_keywords:
- RuntimeResumeFinished method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeResumeFinished method [.NET Framework profiling]
ms.assetid: 76de0494-dc49-426b-887d-bee98806a982
topic_type:
- apiref
ms.openlocfilehash: 8bc97bb0d36a046353587a95aa2b79eff12866e0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499878"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="3ce35-102">ICorProfilerCallback::RuntimeResumeFinished 方法</span><span class="sxs-lookup"><span data-stu-id="3ce35-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="3ce35-103">通知探查器运行时已恢复所有运行时线程并返回到正常操作。</span><span class="sxs-lookup"><span data-stu-id="3ce35-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ce35-104">语法</span><span class="sxs-lookup"><span data-stu-id="3ce35-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="3ce35-105">备注</span><span class="sxs-lookup"><span data-stu-id="3ce35-105">Remarks</span></span>  
 <span data-ttu-id="3ce35-106">`RuntimeResumeFinished`不保证回调与[ICorProfilerCallback：： RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)回调在同一线程上发生。</span><span class="sxs-lookup"><span data-stu-id="3ce35-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="3ce35-107">但是，它可以保证在与[ICorProfilerCallback：： RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md)回调相同的线程上发生。</span><span class="sxs-lookup"><span data-stu-id="3ce35-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ce35-108">要求</span><span class="sxs-lookup"><span data-stu-id="3ce35-108">Requirements</span></span>  
 <span data-ttu-id="3ce35-109">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce35-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ce35-110">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3ce35-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3ce35-111">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ce35-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ce35-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ce35-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ce35-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ce35-113">See also</span></span>

- [<span data-ttu-id="3ce35-114">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="3ce35-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
