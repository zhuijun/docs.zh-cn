---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3WithInfo Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
ms.assetid: ca8ea534-e441-47b8-be85-466410988c0a
topic_type:
- apiref
ms.openlocfilehash: d40cb424306535cc502d930dd61e6a1e254667da
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496173"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a><span data-ttu-id="173c8-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo 方法</span><span class="sxs-lookup"><span data-stu-id="173c8-102">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo Method</span></span>
<span data-ttu-id="173c8-103">指定将在托管函数的[FunctionEnter3WithInfo](functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](functionleave3withinfo-function.md)和[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)挂钩上调用的探查器实现函数。</span><span class="sxs-lookup"><span data-stu-id="173c8-103">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="173c8-104">语法</span><span class="sxs-lookup"><span data-stu-id="173c8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="173c8-105">参数</span><span class="sxs-lookup"><span data-stu-id="173c8-105">Parameters</span></span>  
 `pFuncEnter3`  
 <span data-ttu-id="173c8-106">中指向要用作回调的实现的指针 `FunctionEnter3WithInfo` 。</span><span class="sxs-lookup"><span data-stu-id="173c8-106">[in] A pointer to the implementation to be used as the `FunctionEnter3WithInfo` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="173c8-107">中指向要用作回调的实现的指针 `FunctionLeave3WithInfo` 。</span><span class="sxs-lookup"><span data-stu-id="173c8-107">[in] A pointer to the implementation to be used as the `FunctionLeave3WithInfo` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="173c8-108">中指向要用作回调的实现的指针 `FunctionTailcall3WithInfo` 。</span><span class="sxs-lookup"><span data-stu-id="173c8-108">[in] A pointer to the implementation to be used as the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="173c8-109">注解</span><span class="sxs-lookup"><span data-stu-id="173c8-109">Remarks</span></span>  
 <span data-ttu-id="173c8-110">[FunctionEnter3WithInfo](functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](functionleave3withinfo-function.md)和[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)挂钩提供堆栈帧和参数检查。</span><span class="sxs-lookup"><span data-stu-id="173c8-110">The [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) hooks provide stack frame and argument inspection.</span></span> <span data-ttu-id="173c8-111">若要访问该信息， `COR_PRF_ENABLE_FUNCTION_ARGS` `COR_PRF_ENABLE_FUNCTION_RETVAL` 必须设置、和/或 `COR_PRF_ENABLE_FRAME_INFO` 标志。</span><span class="sxs-lookup"><span data-stu-id="173c8-111">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="173c8-112">探查器可以使用[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)方法来设置事件标志，然后使用 `SetEnterLeaveFunctionHooks3WithInfo` 方法来注册此函数的实现。</span><span class="sxs-lookup"><span data-stu-id="173c8-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the `SetEnterLeaveFunctionHooks3WithInfo` method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="173c8-113">一次只能有一组回调处于活动状态，最新版本优先。</span><span class="sxs-lookup"><span data-stu-id="173c8-113">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="173c8-114">因此，如果探查器同时调用[SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)和 `SetEnterLeaveFunctionHooks3WithInfo` ， `SetEnterLeaveFunctionHooks3WithInfo` 则使用。</span><span class="sxs-lookup"><span data-stu-id="173c8-114">Therefore, if a profiler calls both [SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and `SetEnterLeaveFunctionHooks3WithInfo`, `SetEnterLeaveFunctionHooks3WithInfo` is used.</span></span>  
  
 <span data-ttu-id="173c8-115">`SetEnterLeaveFunctionHooks3WithInfo`只能从探查器的[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)回调调用此方法。</span><span class="sxs-lookup"><span data-stu-id="173c8-115">The `SetEnterLeaveFunctionHooks3WithInfo` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="173c8-116">要求</span><span class="sxs-lookup"><span data-stu-id="173c8-116">Requirements</span></span>  
 <span data-ttu-id="173c8-117">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="173c8-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="173c8-118">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="173c8-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="173c8-119">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="173c8-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="173c8-120">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="173c8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="173c8-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="173c8-121">See also</span></span>

- [<span data-ttu-id="173c8-122">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="173c8-122">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="173c8-123">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="173c8-123">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="173c8-124">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="173c8-124">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="173c8-125">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="173c8-125">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="173c8-126">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="173c8-126">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="173c8-127">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="173c8-127">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="173c8-128">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="173c8-128">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="173c8-129">分析全局静态函数</span><span class="sxs-lookup"><span data-stu-id="173c8-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
- [<span data-ttu-id="173c8-130">ICorProfilerInfo3 接口</span><span class="sxs-lookup"><span data-stu-id="173c8-130">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="173c8-131">分析接口</span><span class="sxs-lookup"><span data-stu-id="173c8-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="173c8-132">分析</span><span class="sxs-lookup"><span data-stu-id="173c8-132">Profiling</span></span>](index.md)
