---
title: ICorProfilerCallback::JITCompilationFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
ms.openlocfilehash: 0da67f0d4be779cc21481d03a21209620289888e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500049"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="9a2b8-102">ICorProfilerCallback::JITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="9a2b8-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="9a2b8-103">通知探查器，实时（JIT）编译器已完成编译函数。</span><span class="sxs-lookup"><span data-stu-id="9a2b8-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a2b8-104">语法</span><span class="sxs-lookup"><span data-stu-id="9a2b8-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a2b8-105">参数</span><span class="sxs-lookup"><span data-stu-id="9a2b8-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="9a2b8-106">\[in] 编译的函数的 ID。</span><span class="sxs-lookup"><span data-stu-id="9a2b8-106">\[in] The ID of the function that was compiled.</span></span>

- `hrStatus`

  <span data-ttu-id="9a2b8-107">\[in] 一个值，该值指示编译是否成功。</span><span class="sxs-lookup"><span data-stu-id="9a2b8-107">\[in] A value indicating whether compilation was successful.</span></span>

- `fIsSafeToBlock`

  <span data-ttu-id="9a2b8-108">\[in] 一个值，该值指示探查器是否会影响运行时的操作。</span><span class="sxs-lookup"><span data-stu-id="9a2b8-108">\[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="9a2b8-109">`true`如果阻止可能会导致运行时等待调用线程从此回调返回，则该值为; 否则为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="9a2b8-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>

  <span data-ttu-id="9a2b8-110">尽管的值 `true` 不会损害运行时，但它可能会使分析结果变形。</span><span class="sxs-lookup"><span data-stu-id="9a2b8-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>

## <a name="requirements"></a><span data-ttu-id="9a2b8-111">要求</span><span class="sxs-lookup"><span data-stu-id="9a2b8-111">Requirements</span></span>  
 <span data-ttu-id="9a2b8-112">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9a2b8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a2b8-113">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9a2b8-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9a2b8-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a2b8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a2b8-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a2b8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a2b8-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a2b8-116">See also</span></span>

- [<span data-ttu-id="9a2b8-117">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="9a2b8-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9a2b8-118">JITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="9a2b8-118">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
