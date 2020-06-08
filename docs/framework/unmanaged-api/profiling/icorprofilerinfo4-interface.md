---
title: ICorProfilerInfo4 接口
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
ms.openlocfilehash: 58d11e9084f53c69f2656b4f0ee6bc7d2cc4ae21
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495861"
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="dbdfd-102">ICorProfilerInfo4 接口</span><span class="sxs-lookup"><span data-stu-id="dbdfd-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="dbdfd-103">提供代码探查器用于与公共语言运行时（CLR）进行通信以控制事件监视和请求信息的方法。</span><span class="sxs-lookup"><span data-stu-id="dbdfd-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="dbdfd-104">.</span><span class="sxs-lookup"><span data-stu-id="dbdfd-104">.</span></span> <span data-ttu-id="dbdfd-105">`ICorProfilerInfo4`接口是其他接口的扩展 `ICorProfilerInfo` 。</span><span class="sxs-lookup"><span data-stu-id="dbdfd-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="dbdfd-106">它提供了用于支持实时（JIT）重新编译的新方法，已添加到 .NET Framework 4.5。</span><span class="sxs-lookup"><span data-stu-id="dbdfd-106">It provides new methods to support just-in-time (JIT) recompilation, added in the .NET Framework 4.5.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dbdfd-107">方法</span><span class="sxs-lookup"><span data-stu-id="dbdfd-107">Methods</span></span>  
  
|<span data-ttu-id="dbdfd-108">方法</span><span class="sxs-lookup"><span data-stu-id="dbdfd-108">Method</span></span>|<span data-ttu-id="dbdfd-109">说明</span><span class="sxs-lookup"><span data-stu-id="dbdfd-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dbdfd-110">EnumJITedFunctions2 方法</span><span class="sxs-lookup"><span data-stu-id="dbdfd-110">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="dbdfd-111">返回之前 JIT 编译和 JIT 重新编译的所有函数的枚举器。</span><span class="sxs-lookup"><span data-stu-id="dbdfd-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="dbdfd-112">EnumThreads 方法</span><span class="sxs-lookup"><span data-stu-id="dbdfd-112">EnumThreads Method</span></span>](icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="dbdfd-113">获取一个枚举器，该枚举器提供按顺序循环访问所分析进程中所有托管线程的集合的方法。</span><span class="sxs-lookup"><span data-stu-id="dbdfd-113">Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="dbdfd-114">GetCodeInfo3 方法</span><span class="sxs-lookup"><span data-stu-id="dbdfd-114">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="dbdfd-115">获取本机代码的范围，该代码与指定函数的 JIT 重新编译版本相关联。</span><span class="sxs-lookup"><span data-stu-id="dbdfd-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="dbdfd-116">GetFunctionFromIP2 方法</span><span class="sxs-lookup"><span data-stu-id="dbdfd-116">GetFunctionFromIP2 Method</span></span>](icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="dbdfd-117">将托管代码指令指针映射到指定函数的 JIT 重新编译版本。</span><span class="sxs-lookup"><span data-stu-id="dbdfd-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="dbdfd-118">GetILToNativeMapping2 方法</span><span class="sxs-lookup"><span data-stu-id="dbdfd-118">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="dbdfd-119">从 Microsoft 中间语言（MSIL）偏移量到指定函数的 JIT 重新编译版本中包含的代码的本机偏移量的映射。</span><span class="sxs-lookup"><span data-stu-id="dbdfd-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="dbdfd-120">GetObjectSize2 方法</span><span class="sxs-lookup"><span data-stu-id="dbdfd-120">GetObjectSize2 Method</span></span>](icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="dbdfd-121">返回指定的对象的大小。</span><span class="sxs-lookup"><span data-stu-id="dbdfd-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="dbdfd-122">GetReJITIDs 方法</span><span class="sxs-lookup"><span data-stu-id="dbdfd-122">GetReJITIDs Method</span></span>](icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="dbdfd-123">返回 Id 的数组，这些 Id 标识仍分配的指定函数的所有 JIT 重新编译版本。</span><span class="sxs-lookup"><span data-stu-id="dbdfd-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="dbdfd-124">InitializeCurrentThread 方法</span><span class="sxs-lookup"><span data-stu-id="dbdfd-124">InitializeCurrentThread Method</span></span>](icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="dbdfd-125">在同一线程上的后续探查器 API 调用之前初始化当前线程，以便避免死锁。</span><span class="sxs-lookup"><span data-stu-id="dbdfd-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="dbdfd-126">RequestReJIT 方法</span><span class="sxs-lookup"><span data-stu-id="dbdfd-126">RequestReJIT Method</span></span>](icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="dbdfd-127">请求 JIT 重新编译指定函数的所有实例。</span><span class="sxs-lookup"><span data-stu-id="dbdfd-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="dbdfd-128">RequestRevert 方法</span><span class="sxs-lookup"><span data-stu-id="dbdfd-128">RequestRevert Method</span></span>](icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="dbdfd-129">将指定函数的所有实例还原为其初始版本。</span><span class="sxs-lookup"><span data-stu-id="dbdfd-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbdfd-130">注解</span><span class="sxs-lookup"><span data-stu-id="dbdfd-130">Remarks</span></span>  
 <span data-ttu-id="dbdfd-131">CLR 通过使用自由线程模型实现 `ICorProfilerInfo4` 接口的方法。</span><span class="sxs-lookup"><span data-stu-id="dbdfd-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="dbdfd-132">每个方法均返回一个 HRESULT，指示成功或失败。</span><span class="sxs-lookup"><span data-stu-id="dbdfd-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="dbdfd-133">有关可能的返回代码的列表，请参阅 CorError.h 文件。</span><span class="sxs-lookup"><span data-stu-id="dbdfd-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbdfd-134">要求</span><span class="sxs-lookup"><span data-stu-id="dbdfd-134">Requirements</span></span>  
 <span data-ttu-id="dbdfd-135">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dbdfd-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbdfd-136">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dbdfd-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dbdfd-137">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbdfd-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbdfd-138">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbdfd-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbdfd-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dbdfd-139">See also</span></span>

- [<span data-ttu-id="dbdfd-140">分析接口</span><span class="sxs-lookup"><span data-stu-id="dbdfd-140">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="dbdfd-141">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="dbdfd-141">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
