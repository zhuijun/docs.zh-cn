---
title: ICorProfilerCallback::JITCompilationStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
ms.openlocfilehash: 57981ef134dc3f30337d47f5cee426a25d0414cf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500034"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="c09f4-102">ICorProfilerCallback::JITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="c09f4-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="c09f4-103">通知探查器实时（JIT）编译器已开始编译函数。</span><span class="sxs-lookup"><span data-stu-id="c09f4-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c09f4-104">语法</span><span class="sxs-lookup"><span data-stu-id="c09f4-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c09f4-105">参数</span><span class="sxs-lookup"><span data-stu-id="c09f4-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c09f4-106">中要开始编译的函数的 ID。</span><span class="sxs-lookup"><span data-stu-id="c09f4-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="c09f4-107">中指示探查器是否会影响运行时的操作的值。</span><span class="sxs-lookup"><span data-stu-id="c09f4-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="c09f4-108">`true`如果阻止可能会导致运行时等待调用线程从此回调返回，则该值为; 否则为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="c09f4-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="c09f4-109">尽管的值 `true` 不会损害运行时，但它可能会使分析结果变形。</span><span class="sxs-lookup"><span data-stu-id="c09f4-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c09f4-110">注解</span><span class="sxs-lookup"><span data-stu-id="c09f4-110">Remarks</span></span>  
 <span data-ttu-id="c09f4-111">`JITCompilationStarted`由于运行时处理类构造函数的方式，每个函数可以接收多对和[ICorProfilerCallback：： JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md)调用。</span><span class="sxs-lookup"><span data-stu-id="c09f4-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="c09f4-112">例如，运行时开始 JIT 编译方法 A，但类 B 的类构造函数需要运行。</span><span class="sxs-lookup"><span data-stu-id="c09f4-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="c09f4-113">因此，运行时 JIT 编译类 B 的构造函数并运行它。</span><span class="sxs-lookup"><span data-stu-id="c09f4-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="c09f4-114">当构造函数正在运行时，它会调用方法 A，这将导致再次 JIT 编译方法 A。</span><span class="sxs-lookup"><span data-stu-id="c09f4-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="c09f4-115">在此方案中，方法 A 的第一次 JIT 编译将暂停。</span><span class="sxs-lookup"><span data-stu-id="c09f4-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="c09f4-116">但是，将使用 JIT 编译事件来报告 JIT 编译方法 A 的两种尝试。</span><span class="sxs-lookup"><span data-stu-id="c09f4-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="c09f4-117">如果探查器将通过调用[ICorProfilerInfo：： SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md)方法替换方法 A 的 Microsoft 中间语言（MSIL）代码，则它必须为这两个事件都 `JITCompilationStarted` 使用同一 MSIL 块。</span><span class="sxs-lookup"><span data-stu-id="c09f4-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="c09f4-118">当两个线程同时进行回调时，探查器必须支持 JIT 回调的序列。</span><span class="sxs-lookup"><span data-stu-id="c09f4-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="c09f4-119">例如，线程 A 调用 `JITCompilationStarted` 。</span><span class="sxs-lookup"><span data-stu-id="c09f4-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="c09f4-120">但是，在线程 A 调用之前 `JITCompilationFinished` ，线程 B 使用线程 A 的回调中的函数 ID 调用[ICorProfilerCallback：： ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) `JITCompilationStarted` 。</span><span class="sxs-lookup"><span data-stu-id="c09f4-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="c09f4-121">由于探查器尚未收到对的调用，因此该函数 ID 可能会似乎无效 `JITCompilationFinished` 。</span><span class="sxs-lookup"><span data-stu-id="c09f4-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="c09f4-122">但是，在这种情况下，函数 ID 有效。</span><span class="sxs-lookup"><span data-stu-id="c09f4-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c09f4-123">要求</span><span class="sxs-lookup"><span data-stu-id="c09f4-123">Requirements</span></span>  
 <span data-ttu-id="c09f4-124">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c09f4-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c09f4-125">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c09f4-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c09f4-126">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c09f4-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c09f4-127">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c09f4-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c09f4-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c09f4-128">See also</span></span>

- [<span data-ttu-id="c09f4-129">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="c09f4-129">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c09f4-130">JITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="c09f4-130">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
