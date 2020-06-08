---
title: ICorProfilerCallback4::ReJITCompilationFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type:
- apiref
ms.openlocfilehash: ff06c285bf5306977b520ed9ff845e70fb25989a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499371"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="f8d13-102">ICorProfilerCallback4::ReJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="f8d13-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>
<span data-ttu-id="f8d13-103">通知探查器实时（JIT）编译器已完成对某个函数的重新编译。</span><span class="sxs-lookup"><span data-stu-id="f8d13-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8d13-104">语法</span><span class="sxs-lookup"><span data-stu-id="f8d13-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8d13-105">参数</span><span class="sxs-lookup"><span data-stu-id="f8d13-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f8d13-106">中已重新编译的函数的 ID。</span><span class="sxs-lookup"><span data-stu-id="f8d13-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="f8d13-107">[in] JIT 重新编译的函数的标识。</span><span class="sxs-lookup"><span data-stu-id="f8d13-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="f8d13-108">中一个值，该值指示 JIT 重新编译是否成功。</span><span class="sxs-lookup"><span data-stu-id="f8d13-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="f8d13-109">[in] `true`指示阻止可能会导致运行时等待调用线程从该回调返回;`false`指示阻止操作不会影响运行时的操作。</span><span class="sxs-lookup"><span data-stu-id="f8d13-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="f8d13-110">的值 `true` 不会损害运行时，但会影响分析结果。</span><span class="sxs-lookup"><span data-stu-id="f8d13-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8d13-111">要求</span><span class="sxs-lookup"><span data-stu-id="f8d13-111">Requirements</span></span>  
 <span data-ttu-id="f8d13-112">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f8d13-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8d13-113">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f8d13-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f8d13-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8d13-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8d13-115">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8d13-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8d13-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f8d13-116">See also</span></span>

- [<span data-ttu-id="f8d13-117">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="f8d13-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f8d13-118">ICorProfilerCallback4 接口</span><span class="sxs-lookup"><span data-stu-id="f8d13-118">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="f8d13-119">JITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="f8d13-119">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="f8d13-120">ReJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="f8d13-120">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
