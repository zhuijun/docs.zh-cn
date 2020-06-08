---
title: FunctionEnter3WithInfo 函数
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
ms.openlocfilehash: ff4b32185e604611eaaead2847c11bc139d405a6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500684"
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="db428-102">FunctionEnter3WithInfo 函数</span><span class="sxs-lookup"><span data-stu-id="db428-102">FunctionEnter3WithInfo Function</span></span>
<span data-ttu-id="db428-103">通知探查器控制正在传递到函数，并提供一个句柄，该句柄可传递给[ICorProfilerInfo3：： GetFunctionEnter3Info 方法](icorprofilerinfo3-getfunctionenter3info-method.md)以检索堆栈帧和函数自变量。</span><span class="sxs-lookup"><span data-stu-id="db428-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db428-104">语法</span><span class="sxs-lookup"><span data-stu-id="db428-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db428-105">参数</span><span class="sxs-lookup"><span data-stu-id="db428-105">Parameters</span></span>

- `functionIDOrClientID`

  <span data-ttu-id="db428-106">\[in] 控件传递到的函数的标识符。</span><span class="sxs-lookup"><span data-stu-id="db428-106">\[in] The identifier of the function to which control is passed.</span></span>

- `eltInfo`

  <span data-ttu-id="db428-107">\[in] 一个表示有关给定堆栈帧的信息的不透明的句柄。</span><span class="sxs-lookup"><span data-stu-id="db428-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="db428-108">此句柄仅在其传递到的回调期间有效。</span><span class="sxs-lookup"><span data-stu-id="db428-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="db428-109">注解</span><span class="sxs-lookup"><span data-stu-id="db428-109">Remarks</span></span>  
 <span data-ttu-id="db428-110">`FunctionEnter3WithInfo`回调方法会在调用函数时通知探查器，并使探查器可以使用[ICorProfilerInfo3：： GetFunctionEnter3Info 方法](icorprofilerinfo3-getfunctionenter3info-method.md)来检查参数值。</span><span class="sxs-lookup"><span data-stu-id="db428-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="db428-111">若要访问参数信息， `COR_PRF_ENABLE_FUNCTION_ARGS` 必须设置标志。</span><span class="sxs-lookup"><span data-stu-id="db428-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="db428-112">探查器可以使用[ICorProfilerInfo：： SetEventMask 方法](icorprofilerinfo-seteventmask-method.md)来设置事件标志，然后使用[ICorProfilerInfo3：： SetEnterLeaveFunctionHooks3WithInfo 方法](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)来注册此函数的实现。</span><span class="sxs-lookup"><span data-stu-id="db428-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="db428-113">`FunctionEnter3WithInfo`函数是回调; 必须实现它。</span><span class="sxs-lookup"><span data-stu-id="db428-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="db428-114">实现必须使用 `__declspec(naked)` 存储类特性。</span><span class="sxs-lookup"><span data-stu-id="db428-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="db428-115">在调用此函数之前，执行引擎不会保存任何注册。</span><span class="sxs-lookup"><span data-stu-id="db428-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="db428-116">进入时，必须保存使用的所有寄存器，包括浮点单元（FPU）中的所有寄存器。</span><span class="sxs-lookup"><span data-stu-id="db428-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="db428-117">退出时，必须通过弹出由其调用方推送的所有参数来还原堆栈。</span><span class="sxs-lookup"><span data-stu-id="db428-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="db428-118">的实现 `FunctionEnter3WithInfo` 不应阻塞，因为它将延迟垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="db428-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="db428-119">实现不应尝试垃圾回收，因为堆栈可能不处于垃圾回收友好状态。</span><span class="sxs-lookup"><span data-stu-id="db428-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="db428-120">如果尝试垃圾回收，则运行时将被阻止，直到 `FunctionEnter3WithInfo` 返回。</span><span class="sxs-lookup"><span data-stu-id="db428-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="db428-121">`FunctionEnter3WithInfo`函数不得调入托管代码或以任何方式导致托管内存分配。</span><span class="sxs-lookup"><span data-stu-id="db428-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db428-122">要求</span><span class="sxs-lookup"><span data-stu-id="db428-122">Requirements</span></span>  
 <span data-ttu-id="db428-123">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="db428-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db428-124">**标头：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="db428-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="db428-125">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db428-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db428-126">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db428-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db428-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="db428-127">See also</span></span>

- [<span data-ttu-id="db428-128">GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="db428-128">GetFunctionEnter3Info</span></span>](icorprofilerinfo3-getfunctionenter3info-method.md)
- [<span data-ttu-id="db428-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="db428-129">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="db428-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="db428-130">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="db428-131">分析全局静态函数</span><span class="sxs-lookup"><span data-stu-id="db428-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
