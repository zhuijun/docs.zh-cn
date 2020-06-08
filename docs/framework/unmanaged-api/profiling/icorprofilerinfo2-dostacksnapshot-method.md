---
title: ICorProfilerInfo2::DoStackSnapshot 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.DoStackSnapshot
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type:
- apiref
ms.openlocfilehash: b9a7142de01d818390b740a795f70a4606952780
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497369"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a><span data-ttu-id="18f52-102">ICorProfilerInfo2::DoStackSnapshot 方法</span><span class="sxs-lookup"><span data-stu-id="18f52-102">ICorProfilerInfo2::DoStackSnapshot Method</span></span>
<span data-ttu-id="18f52-103">遍历指定线程的堆栈上的托管帧，并通过回调将信息发送到探查器。</span><span class="sxs-lookup"><span data-stu-id="18f52-103">Walks the managed frames on the stack for the specified thread, and sends information to the profiler through a callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18f52-104">语法</span><span class="sxs-lookup"><span data-stu-id="18f52-104">Syntax</span></span>  
  
```cpp  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18f52-105">参数</span><span class="sxs-lookup"><span data-stu-id="18f52-105">Parameters</span></span>  
 `thread`  
 <span data-ttu-id="18f52-106">中目标线程的 ID。</span><span class="sxs-lookup"><span data-stu-id="18f52-106">[in] The ID of the target thread.</span></span>  
  
 <span data-ttu-id="18f52-107">在中传递 null 会 `thread` 生成当前线程的快照。</span><span class="sxs-lookup"><span data-stu-id="18f52-107">Passing null in `thread` yields a snapshot of the current thread.</span></span> <span data-ttu-id="18f52-108">如果 `ThreadID` 传递了不同线程的，则公共语言运行时（CLR）会挂起该线程，执行快照，然后恢复。</span><span class="sxs-lookup"><span data-stu-id="18f52-108">If a `ThreadID` of a different thread is passed, the common language runtime (CLR) suspends that thread, performs the snapshot, and resumes.</span></span>  
  
 `callback`  
 <span data-ttu-id="18f52-109">中指向[StackSnapshotCallback](stacksnapshotcallback-function.md)方法的实现的指针，CLR 调用此方法为探查器提供有关每个托管帧以及每次运行非托管帧的信息。</span><span class="sxs-lookup"><span data-stu-id="18f52-109">[in] A pointer to the implementation of the [StackSnapshotCallback](stacksnapshotcallback-function.md) method, which is called by the CLR to provide the profiler with information on each managed frame and each run of unmanaged frames.</span></span>  
  
 <span data-ttu-id="18f52-110">`StackSnapshotCallback`方法由探查器编写器实现。</span><span class="sxs-lookup"><span data-stu-id="18f52-110">The `StackSnapshotCallback` method is implemented by the profiler writer.</span></span>  
  
 `infoFlags`  
 <span data-ttu-id="18f52-111">中一个[COR_PRF_SNAPSHOT_INFO](cor-prf-snapshot-info-enumeration.md)枚举的值，该值指定要为每个帧传递回的数据量 `StackSnapshotCallback` 。</span><span class="sxs-lookup"><span data-stu-id="18f52-111">[in] A value of the [COR_PRF_SNAPSHOT_INFO](cor-prf-snapshot-info-enumeration.md) enumeration, which specifies the amount of data to be passed back for each frame by `StackSnapshotCallback`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="18f52-112">中指向客户端数据的指针，它将直接传递给 `StackSnapshotCallback` 回调函数。</span><span class="sxs-lookup"><span data-stu-id="18f52-112">[in] A pointer to the client data, which is passed straight through to the `StackSnapshotCallback` callback function.</span></span>  
  
 `context`  
 <span data-ttu-id="18f52-113">中指向 Win32 结构的指针 `CONTEXT` ，该结构用于对堆栈审核进行种子设定。</span><span class="sxs-lookup"><span data-stu-id="18f52-113">[in] A pointer to a Win32 `CONTEXT` structure, which is used to seed the stack walk.</span></span> <span data-ttu-id="18f52-114">Win32 `CONTEXT` 结构包含 cpu 寄存器的值，表示特定时刻的 cpu 状态。</span><span class="sxs-lookup"><span data-stu-id="18f52-114">The Win32 `CONTEXT` structure contains values of the CPU registers and represents the state of the CPU at a particular moment in time.</span></span>  
  
 <span data-ttu-id="18f52-115">如果堆栈顶部是非托管的帮助程序代码，则 seed 有助于 CLR 确定开始堆栈审核的位置;否则，将忽略种子。</span><span class="sxs-lookup"><span data-stu-id="18f52-115">The seed helps the CLR determine where to begin the stack walk, if the top of the stack is unmanaged helper code; otherwise, the seed is ignored.</span></span> <span data-ttu-id="18f52-116">必须为异步审核提供种子。</span><span class="sxs-lookup"><span data-stu-id="18f52-116">A seed must be supplied for an asynchronous walk.</span></span> <span data-ttu-id="18f52-117">如果执行同步审核，则不需要种子。</span><span class="sxs-lookup"><span data-stu-id="18f52-117">If you are doing a synchronous walk, no seed is necessary.</span></span>  
  
 <span data-ttu-id="18f52-118">`context`仅当在参数中传递了 COR_PRF_SNAPSHOT_CONTEXT 标志时，此参数才有效 `infoFlags` 。</span><span class="sxs-lookup"><span data-stu-id="18f52-118">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in the `infoFlags` parameter.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="18f52-119">中`CONTEXT`由参数引用的结构的大小 `context` 。</span><span class="sxs-lookup"><span data-stu-id="18f52-119">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18f52-120">注解</span><span class="sxs-lookup"><span data-stu-id="18f52-120">Remarks</span></span>  
 <span data-ttu-id="18f52-121">传递 null 以 `thread` 生成当前线程的快照。</span><span class="sxs-lookup"><span data-stu-id="18f52-121">Passing null for `thread` yields a snapshot of the current thread.</span></span> <span data-ttu-id="18f52-122">仅当目标线程在此时挂起时，才能对其他线程执行快照操作。</span><span class="sxs-lookup"><span data-stu-id="18f52-122">Snapshots can be taken of other threads only if the target thread is suspended at the time.</span></span>  
  
 <span data-ttu-id="18f52-123">当探查器需要遍历堆栈时，它会调用 `DoStackSnapshot` 。</span><span class="sxs-lookup"><span data-stu-id="18f52-123">When the profiler wants to walk the stack, it calls `DoStackSnapshot`.</span></span> <span data-ttu-id="18f52-124">在 CLR 从该调用返回之前，它将多次调用 `StackSnapshotCallback` 堆栈上的每个托管帧（或运行非托管帧）。</span><span class="sxs-lookup"><span data-stu-id="18f52-124">Before the CLR returns from that call, it calls your `StackSnapshotCallback` several times, once for each managed frame (or run of unmanaged frames) on the stack.</span></span> <span data-ttu-id="18f52-125">如果遇到非托管帧，则必须自行对其进行演练。</span><span class="sxs-lookup"><span data-stu-id="18f52-125">When unmanaged frames are encountered, you must walk them yourself.</span></span>  
  
 <span data-ttu-id="18f52-126">遍历堆栈的顺序与帧被推送到堆栈上的顺序相反：叶（上传）帧优先于最后一个（第一个推送的）帧。</span><span class="sxs-lookup"><span data-stu-id="18f52-126">The order in which the stack is walked is the reverse of how the frames were pushed onto the stack: leaf (last-pushed) frame first, main (first-pushed) frame last.</span></span>  
  
 <span data-ttu-id="18f52-127">有关如何对探查器进行编程以遍历托管堆栈的详细信息，请参阅[.NET Framework 2.0：基础和更高版本中的探查器堆栈遍历](https://docs.microsoft.com/previous-versions/dotnet/articles/bb264782(v=msdn.10))。</span><span class="sxs-lookup"><span data-stu-id="18f52-127">For more information about how to program the profiler to walk managed stacks, see [Profiler Stack Walking in the .NET Framework 2.0: Basics and Beyond](https://docs.microsoft.com/previous-versions/dotnet/articles/bb264782(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="18f52-128">堆栈审核可以是同步的，也可以是异步的，如以下各节所述。</span><span class="sxs-lookup"><span data-stu-id="18f52-128">A stack walk can be synchronous or asynchronous, as explained in the following sections.</span></span>  
  
## <a name="synchronous-stack-walk"></a><span data-ttu-id="18f52-129">同步堆栈遍历</span><span class="sxs-lookup"><span data-stu-id="18f52-129">Synchronous Stack Walk</span></span>  
 <span data-ttu-id="18f52-130">同步堆栈审核包括遍历当前线程的堆栈以响应回调。</span><span class="sxs-lookup"><span data-stu-id="18f52-130">A synchronous stack walk involves walking the stack of the current thread in response to a callback.</span></span> <span data-ttu-id="18f52-131">它不需要进行种子设定或暂停。</span><span class="sxs-lookup"><span data-stu-id="18f52-131">It does not require seeding or suspending.</span></span>  
  
 <span data-ttu-id="18f52-132">当在响应 CLR 调用某个探查器的[ICorProfilerCallback](icorprofilercallback-interface.md) （或[ICorProfilerCallback2](icorprofilercallback2-interface.md)）方法时，您可以进行同步调用，以 `DoStackSnapshot` 遍历当前线程的堆栈。</span><span class="sxs-lookup"><span data-stu-id="18f52-132">You make a synchronous call when, in response to the CLR calling one of your profiler's [ICorProfilerCallback](icorprofilercallback-interface.md) (or [ICorProfilerCallback2](icorprofilercallback2-interface.md)) methods, you call `DoStackSnapshot` to walk the stack of the current thread.</span></span> <span data-ttu-id="18f52-133">当你想要在通知（如[ICorProfilerCallback：： ObjectAllocated](icorprofilercallback-objectallocated-method.md)）上查看堆栈的外观时，这非常有用。</span><span class="sxs-lookup"><span data-stu-id="18f52-133">This is useful when you want to see what the stack looks like at a notification such as [ICorProfilerCallback::ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span></span> <span data-ttu-id="18f52-134">只需 `DoStackSnapshot` 从方法中调用 `ICorProfilerCallback` ，并在和参数中传递 null `context` `thread` 。</span><span class="sxs-lookup"><span data-stu-id="18f52-134">You just call `DoStackSnapshot` from within your `ICorProfilerCallback` method, passing null in the `context` and `thread` parameters.</span></span>  
  
## <a name="asynchronous-stack-walk"></a><span data-ttu-id="18f52-135">异步堆栈遍历</span><span class="sxs-lookup"><span data-stu-id="18f52-135">Asynchronous Stack Walk</span></span>  
 <span data-ttu-id="18f52-136">异步堆栈审核需要遍历不同线程的堆栈，或遍历当前线程的堆栈，而不是响应回调，但通过劫持当前线程的指令指针。</span><span class="sxs-lookup"><span data-stu-id="18f52-136">An asynchronous stack walk entails walking the stack of a different thread, or walking the stack of the current thread, not in response to a callback, but by hijacking the current thread's instruction pointer.</span></span> <span data-ttu-id="18f52-137">如果堆栈顶部是非托管代码，而不是平台调用（PInvoke）或 COM 调用的一部分，而是 CLR 本身中的帮助程序代码，则异步审核需要种子。</span><span class="sxs-lookup"><span data-stu-id="18f52-137">An asynchronous walk requires a seed if the top of the stack is unmanaged code that is not part of a platform invoke (PInvoke) or COM call, but helper code in the CLR itself.</span></span> <span data-ttu-id="18f52-138">例如，执行实时（JIT）编译或垃圾回收的代码是帮助器代码。</span><span class="sxs-lookup"><span data-stu-id="18f52-138">For example, code that does just-in-time (JIT) compiling or garbage collection is helper code.</span></span>  
  
 <span data-ttu-id="18f52-139">您可以通过直接挂起目标线程并自己遍历其堆栈来获取种子，直到找到最顶层的托管帧。</span><span class="sxs-lookup"><span data-stu-id="18f52-139">You obtain a seed by directly suspending the target thread and walking its stack yourself, until you find the topmost managed frame.</span></span> <span data-ttu-id="18f52-140">挂起目标线程后，获取目标线程的当前注册上下文。</span><span class="sxs-lookup"><span data-stu-id="18f52-140">After the target thread is suspended, get the target thread's current register context.</span></span> <span data-ttu-id="18f52-141">接下来，通过调用[ICorProfilerInfo：： GetFunctionFromIP](icorprofilerinfo-getfunctionfromip-method.md)确定寄存器上下文是否指向非托管代码，如果它返回的 `FunctionID` 值等于零，则该框架为非托管代码。</span><span class="sxs-lookup"><span data-stu-id="18f52-141">Next, determine whether the register context points to unmanaged code by calling [ICorProfilerInfo::GetFunctionFromIP](icorprofilerinfo-getfunctionfromip-method.md) — if it returns a `FunctionID` equal to zero, the frame is unmanaged code.</span></span> <span data-ttu-id="18f52-142">现在，遍历堆栈直至到达第一个托管帧，然后基于该帧的注册上下文计算种子上下文。</span><span class="sxs-lookup"><span data-stu-id="18f52-142">Now, walk the stack until you reach the first managed frame, and then calculate the seed context based on the register context for that frame.</span></span>  
  
 <span data-ttu-id="18f52-143">调用 `DoStackSnapshot` 种子上下文以开始异步堆栈遍历。</span><span class="sxs-lookup"><span data-stu-id="18f52-143">Call `DoStackSnapshot` with your seed context to begin the asynchronous stack walk.</span></span> <span data-ttu-id="18f52-144">如果未提供种子， `DoStackSnapshot` 可能会跳过堆栈顶部的托管帧，因此，将为您提供不完整的堆栈审核。</span><span class="sxs-lookup"><span data-stu-id="18f52-144">If you do not supply a seed, `DoStackSnapshot` might skip managed frames at the top of the stack and, consequently, will give you an incomplete stack walk.</span></span> <span data-ttu-id="18f52-145">如果提供了种子，则它必须指向 JIT 编译的或本机图像生成器（Ngen.exe）生成的代码;否则， `DoStackSnapshot` 将返回失败代码 CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX。</span><span class="sxs-lookup"><span data-stu-id="18f52-145">If you do supply a seed, it must point to JIT-compiled or Native Image Generator (Ngen.exe)-generated code; otherwise, `DoStackSnapshot` returns the failure code, CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.</span></span>  
  
 <span data-ttu-id="18f52-146">异步堆栈审核可能会导致死锁或访问冲突，除非你遵循以下准则：</span><span class="sxs-lookup"><span data-stu-id="18f52-146">Asynchronous stack walks can easily cause deadlocks or access violations, unless you follow these guidelines:</span></span>  
  
- <span data-ttu-id="18f52-147">当你直接挂起线程时，请记住，只有从未运行托管代码的线程才能挂起另一个线程。</span><span class="sxs-lookup"><span data-stu-id="18f52-147">When you directly suspend threads, remember that only a thread that has never run managed code can suspend another thread.</span></span>  
  
- <span data-ttu-id="18f52-148">始终在[ICorProfilerCallback：： ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md)回调中阻止，直到该线程的堆栈遍历完成。</span><span class="sxs-lookup"><span data-stu-id="18f52-148">Always block in your [ICorProfilerCallback::ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md) callback until that thread's stack walk is complete.</span></span>  
  
- <span data-ttu-id="18f52-149">当探查器调入可触发垃圾回收的 CLR 函数时，不要持有锁。</span><span class="sxs-lookup"><span data-stu-id="18f52-149">Do not hold a lock while your profiler calls into a CLR function that can trigger a garbage collection.</span></span> <span data-ttu-id="18f52-150">也就是说，如果拥有的线程可能发出调用来触发垃圾回收，则不要持有锁。</span><span class="sxs-lookup"><span data-stu-id="18f52-150">That is, do not hold a lock if the owning thread might make a call that triggers a garbage collection.</span></span>  
  
 <span data-ttu-id="18f52-151">如果 `DoStackSnapshot` 从探查器已创建的线程中调用，以便可以遍历单独目标线程的堆栈，还会发生死锁的风险。</span><span class="sxs-lookup"><span data-stu-id="18f52-151">There is also a risk of deadlock if you call `DoStackSnapshot` from a thread that your profiler has created so that you can walk the stack of a separate target thread.</span></span> <span data-ttu-id="18f52-152">第一次创建的线程会输入某些 `ICorProfilerInfo*` 方法（包括 `DoStackSnapshot` ），clr 将在该线程上执行每个线程特定于 CLR 的初始化。</span><span class="sxs-lookup"><span data-stu-id="18f52-152">The first time the thread you created enters certain `ICorProfilerInfo*` methods (including `DoStackSnapshot`), the CLR will perform per-thread, CLR-specific initialization on that thread.</span></span> <span data-ttu-id="18f52-153">如果探查器已挂起要尝试遍历其堆栈的目标线程，并且如果该目标线程发生了对每个线程初始化执行所需的锁，则会发生死锁。</span><span class="sxs-lookup"><span data-stu-id="18f52-153">If your profiler has suspended the target thread whose stack you are trying to walk, and if that target thread happened to own a lock necessary for performing this per-thread initialization, a deadlock will occur.</span></span> <span data-ttu-id="18f52-154">若要避免这种死锁，请在 `DoStackSnapshot` 探查器创建的线程中执行初始调用以遍历单独的目标线程，但不要首先挂起目标线程。</span><span class="sxs-lookup"><span data-stu-id="18f52-154">To avoid this deadlock, make an initial call into `DoStackSnapshot` from your profiler-created thread to walk a separate target thread, but do not suspend the target thread first.</span></span> <span data-ttu-id="18f52-155">此初始调用可确保在发生死锁的情况下，每个线程的初始化都可以完成。</span><span class="sxs-lookup"><span data-stu-id="18f52-155">This initial call ensures that the per-thread initialization can complete without deadlock.</span></span> <span data-ttu-id="18f52-156">如果 `DoStackSnapshot` 成功并报告至少一个帧，则在该点之后，此探查器创建的线程将会挂起任何目标线程，并调用 `DoStackSnapshot` 来遍历该目标线程的堆栈。</span><span class="sxs-lookup"><span data-stu-id="18f52-156">If `DoStackSnapshot` succeeds and reports at least one frame, after that point, it will be safe for that profiler-created thread to suspend any target thread and call `DoStackSnapshot` to walk the stack of that target thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18f52-157">要求</span><span class="sxs-lookup"><span data-stu-id="18f52-157">Requirements</span></span>  
 <span data-ttu-id="18f52-158">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="18f52-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18f52-159">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="18f52-159">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="18f52-160">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18f52-160">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18f52-161">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18f52-161">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18f52-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="18f52-162">See also</span></span>

- [<span data-ttu-id="18f52-163">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="18f52-163">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="18f52-164">ICorProfilerInfo2 接口</span><span class="sxs-lookup"><span data-stu-id="18f52-164">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
