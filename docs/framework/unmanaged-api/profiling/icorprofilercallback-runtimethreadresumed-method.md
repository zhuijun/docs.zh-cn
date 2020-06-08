---
title: ICorProfilerCallback::RuntimeThreadResumed 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadResumed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadResumed
helpviewer_keywords:
- ICorProfilerCallback::RuntimeThreadResumed method [.NET Framework profiling]
- RuntimeThreadResumed method [.NET Framework profiling]
ms.assetid: da984f89-4f53-4ab0-ae6f-3e2ee6085994
topic_type:
- apiref
ms.openlocfilehash: d3949189a72583ebb50b67a270694a31f1eb23dc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503206"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="b17dc-102">ICorProfilerCallback::RuntimeThreadResumed 方法</span><span class="sxs-lookup"><span data-stu-id="b17dc-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="b17dc-103">通知探查器指定的线程在挂起后已恢复。</span><span class="sxs-lookup"><span data-stu-id="b17dc-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b17dc-104">语法</span><span class="sxs-lookup"><span data-stu-id="b17dc-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b17dc-105">参数</span><span class="sxs-lookup"><span data-stu-id="b17dc-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="b17dc-106">中已恢复的线程的 ID。</span><span class="sxs-lookup"><span data-stu-id="b17dc-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b17dc-107">要求</span><span class="sxs-lookup"><span data-stu-id="b17dc-107">Requirements</span></span>  
 <span data-ttu-id="b17dc-108">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b17dc-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b17dc-109">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b17dc-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b17dc-110">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b17dc-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b17dc-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b17dc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b17dc-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b17dc-112">See also</span></span>

- [<span data-ttu-id="b17dc-113">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="b17dc-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b17dc-114">RuntimeThreadSuspended 方法</span><span class="sxs-lookup"><span data-stu-id="b17dc-114">RuntimeThreadSuspended Method</span></span>](icorprofilercallback-runtimethreadsuspended-method.md)
