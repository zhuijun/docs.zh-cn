---
title: StackSnapshotCallback 函数
ms.date: 03/30/2017
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
ms.openlocfilehash: a0f5316900dedc6c8983f9e670f60767ed783a40
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493976"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="7907a-102">StackSnapshotCallback 函数</span><span class="sxs-lookup"><span data-stu-id="7907a-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="7907a-103">在堆栈遍历期间，为探查器提供有关每个托管帧和每个托管帧的每个运行的信息，由[ICorProfilerInfo2：:D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md)方法启动。</span><span class="sxs-lookup"><span data-stu-id="7907a-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7907a-104">语法</span><span class="sxs-lookup"><span data-stu-id="7907a-104">Syntax</span></span>  
  
```cpp  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7907a-105">参数</span><span class="sxs-lookup"><span data-stu-id="7907a-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="7907a-106">中如果此值为零，则此回调适用于非托管帧的运行;否则，它是托管函数的标识符，此回调适用于托管帧。</span><span class="sxs-lookup"><span data-stu-id="7907a-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="7907a-107">中帧中的本机代码指令指针的值。</span><span class="sxs-lookup"><span data-stu-id="7907a-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="7907a-108">中一个 `COR_PRF_FRAME_INFO` 值，该值引用有关堆栈帧的信息。</span><span class="sxs-lookup"><span data-stu-id="7907a-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="7907a-109">此值仅在此回调期间有效。</span><span class="sxs-lookup"><span data-stu-id="7907a-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="7907a-110">中`CONTEXT`由参数引用的结构的大小 `context` 。</span><span class="sxs-lookup"><span data-stu-id="7907a-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="7907a-111">中指向 Win32 `CONTEXT` 结构的指针，该结构表示此帧的 CPU 的状态。</span><span class="sxs-lookup"><span data-stu-id="7907a-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="7907a-112">`context`仅当传入 COR_PRF_SNAPSHOT_CONTEXT 标志时，此参数才有效 `ICorProfilerInfo2::DoStackSnapshot` 。</span><span class="sxs-lookup"><span data-stu-id="7907a-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="7907a-113">中指向客户端数据的指针，该数据是通过从直接传递的 `ICorProfilerInfo2::DoStackSnapshot` 。</span><span class="sxs-lookup"><span data-stu-id="7907a-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7907a-114">注解</span><span class="sxs-lookup"><span data-stu-id="7907a-114">Remarks</span></span>  
 <span data-ttu-id="7907a-115">`StackSnapshotCallback`函数由探查器编写器实现。</span><span class="sxs-lookup"><span data-stu-id="7907a-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="7907a-116">必须限制中完成的工作的复杂性 `StackSnapshotCallback` 。</span><span class="sxs-lookup"><span data-stu-id="7907a-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="7907a-117">例如， `ICorProfilerInfo2::DoStackSnapshot` 以异步方式使用时，目标线程可能会持有锁。</span><span class="sxs-lookup"><span data-stu-id="7907a-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="7907a-118">如果中 `StackSnapshotCallback` 的代码需要相同的锁，则可能会不幸死锁。</span><span class="sxs-lookup"><span data-stu-id="7907a-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="7907a-119">`ICorProfilerInfo2::DoStackSnapshot`方法对 `StackSnapshotCallback` 每个托管帧调用一次函数，或在每次运行非托管帧时调用函数。</span><span class="sxs-lookup"><span data-stu-id="7907a-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="7907a-120">如果 `StackSnapshotCallback` 调用来运行非托管帧，则探查器可能会使用寄存器上下文（由 `context` 参数引用）来执行它自己的非托管堆栈遍历。</span><span class="sxs-lookup"><span data-stu-id="7907a-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="7907a-121">在这种情况下，Win32 `CONTEXT` 结构表示在非托管帧运行内最近推送的帧的 CPU 状态。</span><span class="sxs-lookup"><span data-stu-id="7907a-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="7907a-122">尽管 Win32 `CONTEXT` 结构包含所有寄存器的值，但你只应依赖堆栈指针寄存器的值、帧指针寄存器、指令指针寄存器和非易失性（即，保留的）整数寄存器的值。</span><span class="sxs-lookup"><span data-stu-id="7907a-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7907a-123">要求</span><span class="sxs-lookup"><span data-stu-id="7907a-123">Requirements</span></span>  
 <span data-ttu-id="7907a-124">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7907a-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7907a-125">**标头：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="7907a-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7907a-126">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7907a-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7907a-127">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7907a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7907a-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7907a-128">See also</span></span>

- [<span data-ttu-id="7907a-129">DoStackSnapshot 方法</span><span class="sxs-lookup"><span data-stu-id="7907a-129">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="7907a-130">分析全局静态函数</span><span class="sxs-lookup"><span data-stu-id="7907a-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
