---
title: FunctionLeave2 函数
ms.date: 03/30/2017
api_name:
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
ms.openlocfilehash: a2a3d58e0631fceab96c32f9d86fef25973fed84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500658"
---
# <a name="functionleave2-function"></a><span data-ttu-id="43b34-102">FunctionLeave2 函数</span><span class="sxs-lookup"><span data-stu-id="43b34-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="43b34-103">通知探查器函数将要返回到调用方，并提供有关堆栈帧和函数返回值的信息。</span><span class="sxs-lookup"><span data-stu-id="43b34-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43b34-104">语法</span><span class="sxs-lookup"><span data-stu-id="43b34-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43b34-105">参数</span><span class="sxs-lookup"><span data-stu-id="43b34-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="43b34-106">\[in] 返回的函数的标识符。</span><span class="sxs-lookup"><span data-stu-id="43b34-106">\[in] The identifier of the function that is returning.</span></span>

- `clientData`

  <span data-ttu-id="43b34-107">\[in] 重新映射的函数标识符，先前通过[FunctionIDMapper](functionidmapper-function.md)函数指定的探查器。</span><span class="sxs-lookup"><span data-stu-id="43b34-107">\[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>

- `func`

  <span data-ttu-id="43b34-108">\[in] 一个 `COR_PRF_FRAME_INFO` 值，该值指向有关堆栈帧的信息。</span><span class="sxs-lookup"><span data-stu-id="43b34-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="43b34-109">探查器应将此视为不透明的句柄，该句柄可传递回[ICorProfilerInfo2：： GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md)方法中的执行引擎。</span><span class="sxs-lookup"><span data-stu-id="43b34-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `retvalRange`

  <span data-ttu-id="43b34-110">\[in] 一个指向[COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md)结构的指针，该结构指定函数的返回值的内存位置。</span><span class="sxs-lookup"><span data-stu-id="43b34-110">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>

  <span data-ttu-id="43b34-111">若要访问返回值信息， `COR_PRF_ENABLE_FUNCTION_RETVAL` 必须设置标志。</span><span class="sxs-lookup"><span data-stu-id="43b34-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="43b34-112">探查器可以使用[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)方法来设置事件标志。</span><span class="sxs-lookup"><span data-stu-id="43b34-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="43b34-113">注解</span><span class="sxs-lookup"><span data-stu-id="43b34-113">Remarks</span></span>  
 <span data-ttu-id="43b34-114">`func` `retvalRange` 当函数返回后，和参数的值无效， `FunctionLeave2` 因为值可能会更改或被销毁。</span><span class="sxs-lookup"><span data-stu-id="43b34-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="43b34-115">`FunctionLeave2`函数是回调; 必须实现它。</span><span class="sxs-lookup"><span data-stu-id="43b34-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="43b34-116">实现必须使用 `__declspec` （ `naked` ）存储类特性。</span><span class="sxs-lookup"><span data-stu-id="43b34-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="43b34-117">在调用此函数之前，执行引擎不会保存任何注册。</span><span class="sxs-lookup"><span data-stu-id="43b34-117">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="43b34-118">进入时，必须保存使用的所有寄存器，包括浮点单元（FPU）中的所有寄存器。</span><span class="sxs-lookup"><span data-stu-id="43b34-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="43b34-119">退出时，必须通过弹出由其调用方推送的所有参数来还原堆栈。</span><span class="sxs-lookup"><span data-stu-id="43b34-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="43b34-120">的实现 `FunctionLeave2` 不应被阻止，因为它将延迟垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="43b34-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="43b34-121">实现不应尝试垃圾回收，因为堆栈可能不处于垃圾回收友好状态。</span><span class="sxs-lookup"><span data-stu-id="43b34-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="43b34-122">如果尝试垃圾回收，则运行时将被阻止，直到 `FunctionLeave2` 返回。</span><span class="sxs-lookup"><span data-stu-id="43b34-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="43b34-123">此外，该 `FunctionLeave2` 函数不得调入托管代码或以任何方式导致托管的内存分配。</span><span class="sxs-lookup"><span data-stu-id="43b34-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43b34-124">要求</span><span class="sxs-lookup"><span data-stu-id="43b34-124">Requirements</span></span>  
 <span data-ttu-id="43b34-125">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="43b34-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43b34-126">**标头：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="43b34-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="43b34-127">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43b34-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43b34-128">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43b34-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b34-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="43b34-129">See also</span></span>

- [<span data-ttu-id="43b34-130">FunctionEnter2 函数</span><span class="sxs-lookup"><span data-stu-id="43b34-130">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="43b34-131">FunctionTailcall2 函数</span><span class="sxs-lookup"><span data-stu-id="43b34-131">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="43b34-132">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="43b34-132">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="43b34-133">分析全局静态函数</span><span class="sxs-lookup"><span data-stu-id="43b34-133">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
