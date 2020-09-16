---
title: ICorDebugFunction3::GetActiveReJitRequestILCode 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugFunction3.GetActiveReJitRequestILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type:
- apiref
ms.openlocfilehash: 8c502c082c2cf90d87c195df531de686e2a6d914
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544253"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="0ecca-102">ICorDebugFunction3::GetActiveReJitRequestILCode 方法</span><span class="sxs-lookup"><span data-stu-id="0ecca-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="0ecca-103">[仅在 .NET Framework 4.5.2 及更高版本中受支持]</span><span class="sxs-lookup"><span data-stu-id="0ecca-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="0ecca-104">获取一个接口指针，该指针指向包含活动 ReJIT 请求中的 IL 的 [ICorDebugILCode](icordebugilcode-interface.md) 。</span><span class="sxs-lookup"><span data-stu-id="0ecca-104">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ecca-105">语法</span><span class="sxs-lookup"><span data-stu-id="0ecca-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ecca-106">参数</span><span class="sxs-lookup"><span data-stu-id="0ecca-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="0ecca-107">指向活动 ReJIT 请求中的 IL 的指针。</span><span class="sxs-lookup"><span data-stu-id="0ecca-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ecca-108">备注</span><span class="sxs-lookup"><span data-stu-id="0ecca-108">Remarks</span></span>  
 <span data-ttu-id="0ecca-109">如果此 `ICorDebugFunction3` 对象表示的方法具有活动 ReJIT 请求，则 `ppReJitedILCode` 将返回指向其 IL 的指针。</span><span class="sxs-lookup"><span data-stu-id="0ecca-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="0ecca-110">如果没有活动请求（这是常见情况），则 `ppReJitedILCode` 为 **null**。</span><span class="sxs-lookup"><span data-stu-id="0ecca-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="0ecca-111">ReJIT 请求在执行从 [ICorProfilerCallback4：： GetReJITParameters](../profiling/icorprofilercallback4-getrejitparameters-method.md) 方法调用返回后变为活动状态。</span><span class="sxs-lookup"><span data-stu-id="0ecca-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="0ecca-112">可能尚未对它进行 JIT 编译，而且线程可能仍然在原始版本的代码中执行。</span><span class="sxs-lookup"><span data-stu-id="0ecca-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="0ecca-113">在探查器调用 [ICorProfilerInfo4：： RequestRevert](../profiling/icorprofilerinfo4-requestrevert-method.md) 方法的过程中，ReJIT 请求将变为非活动状态。</span><span class="sxs-lookup"><span data-stu-id="0ecca-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="0ecca-114">即使还原了 IL 之后，线程仍然可在 JIT 编译 (ReJIT) 的代码中执行。</span><span class="sxs-lookup"><span data-stu-id="0ecca-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ecca-115">要求</span><span class="sxs-lookup"><span data-stu-id="0ecca-115">Requirements</span></span>  
 <span data-ttu-id="0ecca-116">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ecca-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ecca-117">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ecca-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ecca-118">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ecca-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ecca-119">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ecca-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ecca-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="0ecca-120">See also</span></span>

- [<span data-ttu-id="0ecca-121">ICorDebugFunction3 接口</span><span class="sxs-lookup"><span data-stu-id="0ecca-121">ICorDebugFunction3 Interface</span></span>](icordebugfunction3-interface.md)
- [<span data-ttu-id="0ecca-122">调试接口</span><span class="sxs-lookup"><span data-stu-id="0ecca-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0ecca-123">ReJIT：操作方法指南</span><span class="sxs-lookup"><span data-stu-id="0ecca-123">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
