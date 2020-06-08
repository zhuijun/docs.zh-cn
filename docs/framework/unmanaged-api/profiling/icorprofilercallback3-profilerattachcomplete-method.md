---
title: ICorProfilerCallback3::ProfilerAttachComplete 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
ms.openlocfilehash: bcc938ff9322fca4f45366fdc695e0c3901484b5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499657"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="8d716-102">ICorProfilerCallback3::ProfilerAttachComplete 方法</span><span class="sxs-lookup"><span data-stu-id="8d716-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="8d716-103">由公共语言运行时（CLR）调用以指示探查器现在可以调用[ICorProfilerInfo3：： EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md)和[ICorProfilerInfo3：： EnumModules](icorprofilerinfo3-enummodules-method.md)追赶方法。</span><span class="sxs-lookup"><span data-stu-id="8d716-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d716-104">语法</span><span class="sxs-lookup"><span data-stu-id="8d716-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="8d716-105">备注</span><span class="sxs-lookup"><span data-stu-id="8d716-105">Remarks</span></span>  
 <span data-ttu-id="8d716-106">`ProfilerAttachComplete`调用[ICorProfilerCallback3：： InitializeForAttach](icorprofilercallback3-initializeforattach-method.md)方法后发出回调。</span><span class="sxs-lookup"><span data-stu-id="8d716-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="8d716-107">指示如下内容：</span><span class="sxs-lookup"><span data-stu-id="8d716-107">It indicates the following:</span></span>  
  
- <span data-ttu-id="8d716-108">已激活 `InitializeForAttach` 中的探测器请求的回调。</span><span class="sxs-lookup"><span data-stu-id="8d716-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="8d716-109">探查器现在可以对关联的 ID 执行追赶操作，而不必担心丢失通知。</span><span class="sxs-lookup"><span data-stu-id="8d716-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="8d716-110">CLR 将忽略从此回调返回的值。</span><span class="sxs-lookup"><span data-stu-id="8d716-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d716-111">要求</span><span class="sxs-lookup"><span data-stu-id="8d716-111">Requirements</span></span>  
 <span data-ttu-id="8d716-112">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d716-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d716-113">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8d716-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8d716-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d716-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d716-115">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d716-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d716-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8d716-116">See also</span></span>

- [<span data-ttu-id="8d716-117">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="8d716-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8d716-118">ICorProfilerInfo3 接口</span><span class="sxs-lookup"><span data-stu-id="8d716-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="8d716-119">分析接口</span><span class="sxs-lookup"><span data-stu-id="8d716-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="8d716-120">分析</span><span class="sxs-lookup"><span data-stu-id="8d716-120">Profiling</span></span>](index.md)
