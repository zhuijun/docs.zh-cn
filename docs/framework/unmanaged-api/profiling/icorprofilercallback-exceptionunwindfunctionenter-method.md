---
title: ICorProfilerCallback::ExceptionUnwindFunctionEnter 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter method [.NET Framework profiling]
- ExceptionUnwindFunctionEnter method [.NET Framework profiling]
ms.assetid: ea3dc625-5650-4bf4-8e67-01e42be065b1
topic_type:
- apiref
ms.openlocfilehash: 5e50255342abae43565fd3556964c24ba4385eb8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500125"
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="abf26-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter 方法</span><span class="sxs-lookup"><span data-stu-id="abf26-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>
<span data-ttu-id="abf26-103">通知探查器异常处理的展开阶段已开始展开某个函数。</span><span class="sxs-lookup"><span data-stu-id="abf26-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abf26-104">语法</span><span class="sxs-lookup"><span data-stu-id="abf26-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abf26-105">参数</span><span class="sxs-lookup"><span data-stu-id="abf26-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="abf26-106">\[in] 要展开的函数的 ID。</span><span class="sxs-lookup"><span data-stu-id="abf26-106">\[in] The ID of the function that is being unwound.</span></span>

## <a name="remarks"></a><span data-ttu-id="abf26-107">注解</span><span class="sxs-lookup"><span data-stu-id="abf26-107">Remarks</span></span>  
 <span data-ttu-id="abf26-108">探查器不应在此方法的实现中被阻止，因为堆栈可能不处于允许垃圾回收的状态，因此无法启用抢先垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="abf26-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="abf26-109">如果探查器在此处阻止并且试图进行垃圾回收，则运行时将被阻止，直到此回调返回。</span><span class="sxs-lookup"><span data-stu-id="abf26-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="abf26-110">探查器的此方法的实现不应调入托管代码或以任何方式导致托管内存分配。</span><span class="sxs-lookup"><span data-stu-id="abf26-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abf26-111">要求</span><span class="sxs-lookup"><span data-stu-id="abf26-111">Requirements</span></span>  
 <span data-ttu-id="abf26-112">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="abf26-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abf26-113">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="abf26-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="abf26-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abf26-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abf26-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abf26-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abf26-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="abf26-116">See also</span></span>

- [<span data-ttu-id="abf26-117">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="abf26-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="abf26-118">ExceptionUnwindFunctionLeave 方法</span><span class="sxs-lookup"><span data-stu-id="abf26-118">ExceptionUnwindFunctionLeave Method</span></span>](icorprofilercallback-exceptionunwindfunctionleave-method.md)
