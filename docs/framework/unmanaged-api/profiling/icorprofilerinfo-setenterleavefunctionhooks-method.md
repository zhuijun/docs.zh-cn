---
title: ICorProfilerInfo::SetEnterLeaveFunctionHooks 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
ms.openlocfilehash: cf0726a12b0274fd7a38e82b66c33430d26b031a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497447"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="12bbe-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks 方法</span><span class="sxs-lookup"><span data-stu-id="12bbe-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="12bbe-103">指定在托管函数的 "enter"、"leave" 和 "tailcall" 挂钩上调用的探查器实现函数。</span><span class="sxs-lookup"><span data-stu-id="12bbe-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12bbe-104">语法</span><span class="sxs-lookup"><span data-stu-id="12bbe-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12bbe-105">参数</span><span class="sxs-lookup"><span data-stu-id="12bbe-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="12bbe-106">中指向要用作[FunctionEnter](functionenter-function.md)回调的实现的指针。</span><span class="sxs-lookup"><span data-stu-id="12bbe-106">[in] A pointer to the implementation to be used as the [FunctionEnter](functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="12bbe-107">中指向要用作[FunctionLeave](functionleave-function.md)回调的实现的指针。</span><span class="sxs-lookup"><span data-stu-id="12bbe-107">[in] A pointer to the implementation to be used as the [FunctionLeave](functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="12bbe-108">中指向要用作[FunctionTailcall](functiontailcall-function.md)回调的实现的指针。</span><span class="sxs-lookup"><span data-stu-id="12bbe-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12bbe-109">注解</span><span class="sxs-lookup"><span data-stu-id="12bbe-109">Remarks</span></span>  
 <span data-ttu-id="12bbe-110">在 .NET Framework 版本1.0 中，每个函数指针均可为 null，以禁用相应的回调。</span><span class="sxs-lookup"><span data-stu-id="12bbe-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="12bbe-111">一次只能有一个回调集处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="12bbe-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="12bbe-112">因此，如果探查器同时调用 `SetEnterLeaveFunctionHooks` 和[ICorProfilerInfo2：： SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)，则 `SetEnterLeaveFunctionHooks2` 优先使用。</span><span class="sxs-lookup"><span data-stu-id="12bbe-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="12bbe-113">只能 `SetEnterLeaveFunctionHooks` 从探查器的[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)回调调用此方法。</span><span class="sxs-lookup"><span data-stu-id="12bbe-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12bbe-114">要求</span><span class="sxs-lookup"><span data-stu-id="12bbe-114">Requirements</span></span>  
 <span data-ttu-id="12bbe-115">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="12bbe-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12bbe-116">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="12bbe-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12bbe-117">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12bbe-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12bbe-118">**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12bbe-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12bbe-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12bbe-119">See also</span></span>

- [<span data-ttu-id="12bbe-120">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="12bbe-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
