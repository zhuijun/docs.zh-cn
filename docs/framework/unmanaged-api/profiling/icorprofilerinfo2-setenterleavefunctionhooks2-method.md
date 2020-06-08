---
title: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
ms.openlocfilehash: 78489aae840ff17e68b10bd7593fb7be4dae1af7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496711"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="06bc1-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="06bc1-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="06bc1-103">指定要在已更新版本的托管函数 "enter"、"leave" 和 "tailcall" 挂钩上调用的探查器实现函数。</span><span class="sxs-lookup"><span data-stu-id="06bc1-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06bc1-104">语法</span><span class="sxs-lookup"><span data-stu-id="06bc1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06bc1-105">参数</span><span class="sxs-lookup"><span data-stu-id="06bc1-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="06bc1-106">中指向要用作[FunctionEnter2](functionenter2-function.md)回调的实现的指针。</span><span class="sxs-lookup"><span data-stu-id="06bc1-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="06bc1-107">中指向要用作[FunctionLeave2](functionleave2-function.md)回调的实现的指针。</span><span class="sxs-lookup"><span data-stu-id="06bc1-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="06bc1-108">中指向要用作[FunctionTailcall2](functiontailcall2-function.md)回调的实现的指针。</span><span class="sxs-lookup"><span data-stu-id="06bc1-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06bc1-109">注解</span><span class="sxs-lookup"><span data-stu-id="06bc1-109">Remarks</span></span>  
 <span data-ttu-id="06bc1-110">此 `SetEnterLeaveFunctionHooks2` 方法类似于[ICorProfilerInfo：： SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="06bc1-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="06bc1-111">使用前者来指定要用作输入/保留/tailcall 回调的较新版本的函数，并使用后者来指定要用作较早版本的 enter/leave/tailcall 回调的函数。</span><span class="sxs-lookup"><span data-stu-id="06bc1-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="06bc1-112">一次只能有一个回调集处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="06bc1-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="06bc1-113">因此，如果探查器调用 `ICorProfilerInfo::SetEnterLeaveFunctionHooks` 和 `SetEnterLeaveFunctionHooks2` ， `SetEnterLeaveFunctionHooks2` 则使用。</span><span class="sxs-lookup"><span data-stu-id="06bc1-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="06bc1-114">`SetEnterLeaveFunctionHooks2`只能从探查器的[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)回调调用此方法。</span><span class="sxs-lookup"><span data-stu-id="06bc1-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06bc1-115">要求</span><span class="sxs-lookup"><span data-stu-id="06bc1-115">Requirements</span></span>  
 <span data-ttu-id="06bc1-116">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="06bc1-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06bc1-117">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="06bc1-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="06bc1-118">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06bc1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06bc1-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06bc1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06bc1-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06bc1-120">See also</span></span>

- [<span data-ttu-id="06bc1-121">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="06bc1-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="06bc1-122">ICorProfilerInfo2 接口</span><span class="sxs-lookup"><span data-stu-id="06bc1-122">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
