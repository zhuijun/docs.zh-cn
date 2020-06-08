---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
ms.assetid: f0621465-b84f-40ab-a4e5-56a7abc776a7
topic_type:
- apiref
ms.openlocfilehash: eb658d682ce589b7dfdcfc0228d0c657310e6f7a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496199"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a><span data-ttu-id="4ebbf-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 方法</span><span class="sxs-lookup"><span data-stu-id="4ebbf-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Method</span></span>
<span data-ttu-id="4ebbf-103">指定将在[FunctionEnter3](functionenter3-function.md)、 [FunctionLeave3](functionleave3-function.md)和[FunctionTailcall3](functiontailcall3-function.md)函数上调用的探查器实现函数。</span><span class="sxs-lookup"><span data-stu-id="4ebbf-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ebbf-104">语法</span><span class="sxs-lookup"><span data-stu-id="4ebbf-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ebbf-105">参数</span><span class="sxs-lookup"><span data-stu-id="4ebbf-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="4ebbf-106">中指向要用作回调的实现的指针 `FunctionEnter3` 。</span><span class="sxs-lookup"><span data-stu-id="4ebbf-106">[in] A pointer to the implementation to be used as the `FunctionEnter3` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="4ebbf-107">中指向要用作回调的实现的指针 `FunctionLeave3` 。</span><span class="sxs-lookup"><span data-stu-id="4ebbf-107">[in] A pointer to the implementation to be used as the `FunctionLeave3` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="4ebbf-108">中指向要用作回调的实现的指针 `FunctionTailcall3` 。</span><span class="sxs-lookup"><span data-stu-id="4ebbf-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ebbf-109">注解</span><span class="sxs-lookup"><span data-stu-id="4ebbf-109">Remarks</span></span>  
 <span data-ttu-id="4ebbf-110">[FunctionEnter3](functionenter3-function.md)、 [FunctionLeave3](functionleave3-function.md)和[FunctionTailcall3](functiontailcall3-function.md)挂钩不提供堆栈帧和参数检查。</span><span class="sxs-lookup"><span data-stu-id="4ebbf-110">[FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md) hooks do not provide stack frame and argument inspection.</span></span> <span data-ttu-id="4ebbf-111">若要访问该信息， `COR_PRF_ENABLE_FUNCTION_ARGS` `COR_PRF_ENABLE_FUNCTION_RETVAL` 必须设置、和/或 `COR_PRF_ENABLE_FRAME_INFO` 标志。</span><span class="sxs-lookup"><span data-stu-id="4ebbf-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or  `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="4ebbf-112">探查器可以使用[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)方法来设置事件标志，然后使用[ICorProfilerInfo3：： SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)方法来注册此函数的实现。</span><span class="sxs-lookup"><span data-stu-id="4ebbf-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="4ebbf-113">一次只能有一组回调处于活动状态，最新版本优先。</span><span class="sxs-lookup"><span data-stu-id="4ebbf-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="4ebbf-114">因此，如果探查器同时调用[SetEnterLeaveFunctionHooks2 方法](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)和 `SetEnterLeaveFunctionHooks3` 方法， `SetEnterLeaveFunctionHooks3` 则使用。</span><span class="sxs-lookup"><span data-stu-id="4ebbf-114">Therefore, if a profiler calls both the [SetEnterLeaveFunctionHooks2 Method](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and the `SetEnterLeaveFunctionHooks3` method, `SetEnterLeaveFunctionHooks3` is used.</span></span>  
  
 <span data-ttu-id="4ebbf-115">`SetEnterLeaveFunctionHooks3`只能从探查器的[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)回调调用此方法。</span><span class="sxs-lookup"><span data-stu-id="4ebbf-115">The `SetEnterLeaveFunctionHooks3` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ebbf-116">要求</span><span class="sxs-lookup"><span data-stu-id="4ebbf-116">Requirements</span></span>  
 <span data-ttu-id="4ebbf-117">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4ebbf-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ebbf-118">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4ebbf-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4ebbf-119">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ebbf-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ebbf-120">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ebbf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ebbf-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4ebbf-121">See also</span></span>

- [<span data-ttu-id="4ebbf-122">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="4ebbf-122">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="4ebbf-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="4ebbf-123">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="4ebbf-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="4ebbf-124">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="4ebbf-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="4ebbf-125">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="4ebbf-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="4ebbf-126">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="4ebbf-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="4ebbf-127">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="4ebbf-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="4ebbf-128">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="4ebbf-129">分析全局静态函数</span><span class="sxs-lookup"><span data-stu-id="4ebbf-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
- [<span data-ttu-id="4ebbf-130">ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="4ebbf-130">ICorProfilerInfo3</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="4ebbf-131">分析接口</span><span class="sxs-lookup"><span data-stu-id="4ebbf-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="4ebbf-132">分析</span><span class="sxs-lookup"><span data-stu-id="4ebbf-132">Profiling</span></span>](index.md)
