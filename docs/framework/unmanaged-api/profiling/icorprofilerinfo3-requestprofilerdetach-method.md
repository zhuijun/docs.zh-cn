---
title: ICorProfilerInfo3::RequestProfilerDetach 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.RequestProfilerDetach Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::RequestProfilerDetach
helpviewer_keywords:
- RequestProfilerDetach method [.NET Framework profiling]
- ICorProfilerInfo3::RequestProfilerDetach method [.NET Framework profiling]
ms.assetid: ea102e62-0454-4477-bcf3-126773acd184
topic_type:
- apiref
ms.openlocfilehash: 627df3600b920e2fe2250f2fc3da51c852edc774
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496202"
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a><span data-ttu-id="30866-102">ICorProfilerInfo3::RequestProfilerDetach 方法</span><span class="sxs-lookup"><span data-stu-id="30866-102">ICorProfilerInfo3::RequestProfilerDetach Method</span></span>
<span data-ttu-id="30866-103">指示运行时分离探查器。</span><span class="sxs-lookup"><span data-stu-id="30866-103">Instructs the runtime to detach the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30866-104">语法</span><span class="sxs-lookup"><span data-stu-id="30866-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30866-105">参数</span><span class="sxs-lookup"><span data-stu-id="30866-105">Parameters</span></span>  
 `dwExpectedCompletionMilliseconds`  
 <span data-ttu-id="30866-106">[in] 公共语言运行时 (CLR) 在检查卸载探查器是否安全之前应等待的事件长度（以毫秒计）。</span><span class="sxs-lookup"><span data-stu-id="30866-106">[in] The length of time, in milliseconds, the common language runtime (CLR) should wait before checking to see whether it is safe to unload the profiler.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30866-107">返回值</span><span class="sxs-lookup"><span data-stu-id="30866-107">Return Value</span></span>  
 <span data-ttu-id="30866-108">此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。</span><span class="sxs-lookup"><span data-stu-id="30866-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="30866-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="30866-109">HRESULT</span></span>|<span data-ttu-id="30866-110">说明</span><span class="sxs-lookup"><span data-stu-id="30866-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="30866-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="30866-111">S_OK</span></span>|<span data-ttu-id="30866-112">分离请求有效，且分离过程现在另一线程上继续执行。</span><span class="sxs-lookup"><span data-stu-id="30866-112">The detach request is valid, and the detach procedure is now continuing on another thread.</span></span> <span data-ttu-id="30866-113">完全分离后，将发出 `ProfilerDetachSucceeded` 事件。</span><span class="sxs-lookup"><span data-stu-id="30866-113">When the detach is fully complete, a `ProfilerDetachSucceeded` event is issued.</span></span>|  
|<span data-ttu-id="30866-114">E_CORPROF_E_CALLBACK3_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="30866-114">E_CORPROF_E_CALLBACK3_REQUIRED</span></span>|<span data-ttu-id="30866-115">探查器未能通过[ICorProfilerCallback3](icorprofilercallback3-interface.md)接口的[IUnknown：： QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))尝试，该接口必须实现该接口才能支持分离操作。</span><span class="sxs-lookup"><span data-stu-id="30866-115">The profiler failed an [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) attempt for the [ICorProfilerCallback3](icorprofilercallback3-interface.md) interface, which it must implement to support the detach operation.</span></span> <span data-ttu-id="30866-116">尚未尝试分离。</span><span class="sxs-lookup"><span data-stu-id="30866-116">Detach was not attempted.</span></span>|  
|<span data-ttu-id="30866-117">CORPROF_E_IMMUTABLE_FLAGS_SET</span><span class="sxs-lookup"><span data-stu-id="30866-117">CORPROF_E_IMMUTABLE_FLAGS_SET</span></span>|<span data-ttu-id="30866-118">无法进行分离，因为探查器在启动时设置了不可变标志。</span><span class="sxs-lookup"><span data-stu-id="30866-118">Detachment is impossible because the profiler set immutable flags at startup.</span></span> <span data-ttu-id="30866-119">尚未尝试分离；探查器仍处于完全附加状态。</span><span class="sxs-lookup"><span data-stu-id="30866-119">Detachment was not attempted; the profiler is still fully attached.</span></span>|  
|<span data-ttu-id="30866-120">CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT</span><span class="sxs-lookup"><span data-stu-id="30866-120">CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT</span></span>|<span data-ttu-id="30866-121">分离无法实现，因为探查器使用了检测到的 Microsoft 中间语言（MSIL）代码，或插入了 `enter` / `leave` 挂钩。</span><span class="sxs-lookup"><span data-stu-id="30866-121">Detachment is impossible because the profiler used instrumented Microsoft intermediate language (MSIL) code, or inserted `enter`/`leave` hooks.</span></span> <span data-ttu-id="30866-122">尚未尝试分离；探查器仍处于完全附加状态。</span><span class="sxs-lookup"><span data-stu-id="30866-122">Detachment was not attempted; the profiler is still fully attached.</span></span><br /><br /> <span data-ttu-id="30866-123">**注意**已检测 MSIL 是代码，由探查器使用[SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md)方法提供。</span><span class="sxs-lookup"><span data-stu-id="30866-123">**Note** Instrumented MSIL is code is code that is provided by the profiler using the [SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>|  
|<span data-ttu-id="30866-124">CORPROF_E_RUNTIME_UNINITIALIZED</span><span class="sxs-lookup"><span data-stu-id="30866-124">CORPROF_E_RUNTIME_UNINITIALIZED</span></span>|<span data-ttu-id="30866-125">托管应用程序中的运行时尚未初始化。</span><span class="sxs-lookup"><span data-stu-id="30866-125">The runtime has not been initialized yet in the managed application.</span></span> <span data-ttu-id="30866-126">（也就是说，运行时尚未完全加载。）当在探查器回调的[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)方法内请求分离时，可能会返回此错误代码。</span><span class="sxs-lookup"><span data-stu-id="30866-126">(That is, the runtime has not been fully loaded.) This error code may be returned when detachment is requested inside the profiler callback's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) method.</span></span>|  
|<span data-ttu-id="30866-127">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE</span><span class="sxs-lookup"><span data-stu-id="30866-127">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE</span></span>|<span data-ttu-id="30866-128">在不支持时调用了 `RequestProfilerDetach`。</span><span class="sxs-lookup"><span data-stu-id="30866-128">`RequestProfilerDetach` was called at an unsupported time.</span></span> <span data-ttu-id="30866-129">如果在托管线程上调用方法，而不是从[ICorProfilerCallback](icorprofilercallback-interface.md) [方法中](icorprofilercallback-interface.md)调用，或者不能容忍垃圾回收，则会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="30866-129">This occurs if the method is called on a managed thread but not from within an [ICorProfilerCallback](icorprofilercallback-interface.md) method or from within an [ICorProfilerCallback](icorprofilercallback-interface.md) method that cannot tolerate a garbage collection.</span></span> <span data-ttu-id="30866-130">有关详细信息，请参阅[CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md)。</span><span class="sxs-lookup"><span data-stu-id="30866-130">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30866-131">注解</span><span class="sxs-lookup"><span data-stu-id="30866-131">Remarks</span></span>  
 <span data-ttu-id="30866-132">在分离过程中，分离线程（专为分离探查器创建的线程）有时会检查是否所有线程均已退出探查器的代码。</span><span class="sxs-lookup"><span data-stu-id="30866-132">During the detach procedure, the detach thread (the thread created specifically for detaching the profiler) occasionally checks whether all threads have exited the profiler’s code.</span></span> <span data-ttu-id="30866-133">探查器应通过 `dwExpectedCompletionMilliseconds` 参数估计此操作的耗时。</span><span class="sxs-lookup"><span data-stu-id="30866-133">The profiler should provide an estimate of how long this should take through the `dwExpectedCompletionMilliseconds` parameter.</span></span> <span data-ttu-id="30866-134">最佳使用值是探查器在任何给定 `ICorProfilerCallback*` 方法内通常花费的时间量；此值不应小于探查器预计花费时间量的一半。</span><span class="sxs-lookup"><span data-stu-id="30866-134">A good value to use is the typical amount of time the profiler spends inside any given `ICorProfilerCallback*` method; this value should not be less than half of the maximum amount of time the profiler expects to spend.</span></span>  
  
 <span data-ttu-id="30866-135">分离线程使用 `dwExpectedCompletionMilliseconds` 决定在检查探查器回调代码是否已从所有堆栈中弹出之前需要休眠多长时间。</span><span class="sxs-lookup"><span data-stu-id="30866-135">The detach thread uses `dwExpectedCompletionMilliseconds` to decide how long to sleep before checking whether profiler callback code has been popped off all stacks.</span></span> <span data-ttu-id="30866-136">尽管以下算法的详细信息在 CLR 的未来版本中可能有所更改，但它展示了在确定何时可安全卸载探查器时可使用 `dwExpectedCompletionMilliseconds` 的一种方法。</span><span class="sxs-lookup"><span data-stu-id="30866-136">Although the details of the following algorithm may change in future releases of the CLR, it illustrates one way `dwExpectedCompletionMilliseconds` can be used when determining when it is safe to unload the profiler.</span></span> <span data-ttu-id="30866-137">分离线程先休眠 `dwExpectedCompletionMilliseconds` 毫秒。</span><span class="sxs-lookup"><span data-stu-id="30866-137">The detach thread first sleeps for `dwExpectedCompletionMilliseconds` milliseconds.</span></span> <span data-ttu-id="30866-138">如果在唤醒后，CLR 发现探查器回调代码仍存在，分离线程将再次休眠，这一次是两次 `dwExpectedCompletionMilliseconds` 。</span><span class="sxs-lookup"><span data-stu-id="30866-138">If, after awakening from the sleep, the CLR finds that profiler callback code is still present, the detach thread sleeps again, this time for two times `dwExpectedCompletionMilliseconds` milliseconds.</span></span> <span data-ttu-id="30866-139">如果从第二次休眠状态唤醒后，分离线程仍发现存在探查器回调代码，则将休眠 10 分钟再进行检查。</span><span class="sxs-lookup"><span data-stu-id="30866-139">If, after awakening from this second sleep, the detach thread finds that profiler callback code is still present, it sleeps for 10 minutes before checking again.</span></span> <span data-ttu-id="30866-140">分离线程每隔 10 分钟继续进行重新检查。</span><span class="sxs-lookup"><span data-stu-id="30866-140">The detach thread continues to recheck every 10 minutes.</span></span>  
  
 <span data-ttu-id="30866-141">如果探查器将 `dwExpectedCompletionMilliseconds` 指定为 0（零），CLR 使用默认值 5000，这意味着探查器在 5 秒钟后执行检查，10 秒后再次检查，然后每隔 10 分钟进行重新检查。</span><span class="sxs-lookup"><span data-stu-id="30866-141">If the profiler specifies `dwExpectedCompletionMilliseconds` as 0 (zero), the CLR uses a default value of 5000, which means that it will perform a check after 5 seconds, again after 10 seconds, and then every 10 minutes thereafter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30866-142">要求</span><span class="sxs-lookup"><span data-stu-id="30866-142">Requirements</span></span>  
 <span data-ttu-id="30866-143">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30866-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30866-144">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="30866-144">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="30866-145">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30866-145">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30866-146">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30866-146">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30866-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="30866-147">See also</span></span>

- [<span data-ttu-id="30866-148">ICorProfilerInfo3 接口</span><span class="sxs-lookup"><span data-stu-id="30866-148">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="30866-149">分析接口</span><span class="sxs-lookup"><span data-stu-id="30866-149">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="30866-150">分析</span><span class="sxs-lookup"><span data-stu-id="30866-150">Profiling</span></span>](index.md)
