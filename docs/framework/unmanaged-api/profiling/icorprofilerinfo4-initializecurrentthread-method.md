---
title: ICorProfilerInfo4::InitializeCurrentThread 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
ms.openlocfilehash: 1f3ff3e9b68aa30f424f4b2fe6c7cacd2cddd544
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495926"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="4b787-102">ICorProfilerInfo4::InitializeCurrentThread 方法</span><span class="sxs-lookup"><span data-stu-id="4b787-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="4b787-103">在同一线程上的后续探查器 API 调用之前初始化当前线程，以便避免死锁。</span><span class="sxs-lookup"><span data-stu-id="4b787-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b787-104">语法</span><span class="sxs-lookup"><span data-stu-id="4b787-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="4b787-105">备注</span><span class="sxs-lookup"><span data-stu-id="4b787-105">Remarks</span></span>  
 <span data-ttu-id="4b787-106">建议在 `InitializeCurrentThread` 存在挂起的线程时，调用将调用探查器 API 的任何线程。</span><span class="sxs-lookup"><span data-stu-id="4b787-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="4b787-107">此方法通常由创建自己的线程的探查器使用，用来调用[ICorProfilerInfo2：:D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md)方法，在目标线程挂起时执行堆栈遍历。</span><span class="sxs-lookup"><span data-stu-id="4b787-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="4b787-108">通过在 `InitializeCurrentThread` 探查器首次创建采样线程时调用一次，探查器可以确保在第一次调用期间，CLR 在第一次调用期间要执行的延迟的每个线程初始化 `DoStackSnapshot` 现在可以在没有其他线程挂起时安全地发生。</span><span class="sxs-lookup"><span data-stu-id="4b787-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b787-109">`InitializeCurrentThread`预先执行初始化来完成接受锁定的任务，可能会死锁。</span><span class="sxs-lookup"><span data-stu-id="4b787-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="4b787-110">`InitializeCurrentThread`仅当没有挂起的线程时才调用。</span><span class="sxs-lookup"><span data-stu-id="4b787-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b787-111">要求</span><span class="sxs-lookup"><span data-stu-id="4b787-111">Requirements</span></span>  
 <span data-ttu-id="4b787-112">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4b787-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b787-113">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4b787-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4b787-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b787-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b787-115">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b787-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b787-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b787-116">See also</span></span>

- [<span data-ttu-id="4b787-117">ICorProfilerInfo4 接口</span><span class="sxs-lookup"><span data-stu-id="4b787-117">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="4b787-118">分析接口</span><span class="sxs-lookup"><span data-stu-id="4b787-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="4b787-119">分析</span><span class="sxs-lookup"><span data-stu-id="4b787-119">Profiling</span></span>](index.md)
