---
title: ICorProfilerCallback::ExceptionCatcherEnter 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
ms.openlocfilehash: 9d0ef4da4ba6c8db49bcb0b40911756f7d9db66d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500308"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="4509c-102">ICorProfilerCallback::ExceptionCatcherEnter 方法</span><span class="sxs-lookup"><span data-stu-id="4509c-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="4509c-103">通知探查器控制正在传递到适当的 `catch` 块。</span><span class="sxs-lookup"><span data-stu-id="4509c-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4509c-104">语法</span><span class="sxs-lookup"><span data-stu-id="4509c-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4509c-105">参数</span><span class="sxs-lookup"><span data-stu-id="4509c-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="4509c-106">\[in] 包含该块的函数的标识符 `catch` 。</span><span class="sxs-lookup"><span data-stu-id="4509c-106">\[in] The identifier of the function containing the `catch` block.</span></span>
  
- `objectId`

  <span data-ttu-id="4509c-107">\[in] 正在处理的异常的标识符。</span><span class="sxs-lookup"><span data-stu-id="4509c-107">\[in] The identifier of the exception being handled.</span></span>

## <a name="remarks"></a><span data-ttu-id="4509c-108">注解</span><span class="sxs-lookup"><span data-stu-id="4509c-108">Remarks</span></span>  
 <span data-ttu-id="4509c-109">`ExceptionCatcherEnter`仅当 catch 点位于用实时（JIT）编译器编译的代码中时，才会调用方法。</span><span class="sxs-lookup"><span data-stu-id="4509c-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="4509c-110">在非托管代码中或在运行时的内部代码中捕获的异常将不会调用此通知。</span><span class="sxs-lookup"><span data-stu-id="4509c-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="4509c-111">由于 `objectId` 垃圾回收可能已在通知后移动了对象，因此会再次传递该值 `ExceptionThrown` 。</span><span class="sxs-lookup"><span data-stu-id="4509c-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="4509c-112">探查器不应在此方法的实现中被阻止，因为堆栈可能不处于允许垃圾回收的状态，因此无法启用抢先垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="4509c-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="4509c-113">如果探查器在此处阻止并且试图进行垃圾回收，则运行时将被阻止，直到此回调返回。</span><span class="sxs-lookup"><span data-stu-id="4509c-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="4509c-114">探查器的此方法的实现不应调入托管代码或以任何方式导致托管内存分配。</span><span class="sxs-lookup"><span data-stu-id="4509c-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4509c-115">要求</span><span class="sxs-lookup"><span data-stu-id="4509c-115">Requirements</span></span>  
 <span data-ttu-id="4509c-116">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4509c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4509c-117">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4509c-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4509c-118">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4509c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4509c-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4509c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4509c-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4509c-120">See also</span></span>

- [<span data-ttu-id="4509c-121">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="4509c-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="4509c-122">ExceptionCatcherLeave 方法</span><span class="sxs-lookup"><span data-stu-id="4509c-122">ExceptionCatcherLeave Method</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)
