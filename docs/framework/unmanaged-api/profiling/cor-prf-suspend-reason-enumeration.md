---
title: COR_PRF_SUSPEND_REASON 枚举
ms.date: 03/30/2017
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
ms.openlocfilehash: fdbcbb2da8f449b9275d820763c2a94cca86cd1e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500749"
---
# <a name="cor_prf_suspend_reason-enumeration"></a><span data-ttu-id="5ee1f-102">COR_PRF_SUSPEND_REASON 枚举</span><span class="sxs-lookup"><span data-stu-id="5ee1f-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>
<span data-ttu-id="5ee1f-103">指示运行时挂起的原因。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ee1f-104">语法</span><span class="sxs-lookup"><span data-stu-id="5ee1f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="5ee1f-105">成员</span><span class="sxs-lookup"><span data-stu-id="5ee1f-105">Members</span></span>  
  
|<span data-ttu-id="5ee1f-106">成员</span><span class="sxs-lookup"><span data-stu-id="5ee1f-106">Member</span></span>|<span data-ttu-id="5ee1f-107">描述</span><span class="sxs-lookup"><span data-stu-id="5ee1f-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="5ee1f-108">由于未指定的原因，运行时处于挂起状态。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="5ee1f-109">运行时挂起，可为垃圾回收请求服务。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="5ee1f-110">与垃圾回收相关的回调发生在[ICorProfilerCallback：： RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md)和[ICorProfilerCallback：： RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md)回调之间。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="5ee1f-111">运行时处于挂起状态，以便 `AppDomain` 可以关闭。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="5ee1f-112">当运行时挂起时，运行时将确定正在关闭哪些线程， `AppDomain` 并将其设置为在恢复时中止。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="5ee1f-113">`AppDomain`此挂起期间没有特定的回调。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="5ee1f-114">运行时将挂起，以便代码间距调整可以出现。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="5ee1f-115">仅当实时（JIT）编译器处于活动状态且启用了代码间距调整时，才间距调整可以代码。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="5ee1f-116">代码间距调整回调发生在 `ICorProfilerCallback::RuntimeSuspendFinished` 和 `ICorProfilerCallback::RuntimeResumeStarted` 回调之间。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="5ee1f-117">**注意：** CLR JIT 不会对 .NET Framework 版本2.0 中的函数进行螺距，因此不会在2.0 中使用此值。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="5ee1f-118">运行时处于挂起状态，以使其可以关闭。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="5ee1f-119">它必须挂起所有线程才能完成此操作。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="5ee1f-120">运行时正在进行进程内调试。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="5ee1f-121">运行时挂起，以便准备垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="5ee1f-122">运行时将被挂起，以便进行 JIT 重新编译。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ee1f-123">注解</span><span class="sxs-lookup"><span data-stu-id="5ee1f-123">Remarks</span></span>  
 <span data-ttu-id="5ee1f-124">在非托管代码中的所有运行时线程都允许继续运行，直到它们尝试重新进入运行时为止，此时它们也将挂起，直到运行时恢复。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="5ee1f-125">这也适用于输入运行时的新线程。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="5ee1f-126">如果运行时中的所有线程都处于中断的代码中，或者在它们确实到达中断的代码时要求挂起，则该线程会立即挂起。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ee1f-127">要求</span><span class="sxs-lookup"><span data-stu-id="5ee1f-127">Requirements</span></span>  
 <span data-ttu-id="5ee1f-128">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5ee1f-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ee1f-129">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ee1f-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ee1f-130">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ee1f-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ee1f-131">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ee1f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ee1f-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5ee1f-132">See also</span></span>

- [<span data-ttu-id="5ee1f-133">分析枚举</span><span class="sxs-lookup"><span data-stu-id="5ee1f-133">Profiling Enumerations</span></span>](profiling-enumerations.md)
