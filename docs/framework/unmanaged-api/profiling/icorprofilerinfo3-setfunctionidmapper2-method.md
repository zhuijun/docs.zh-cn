---
title: ICorProfilerInfo3::SetFunctionIDMapper2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type:
- apiref
ms.openlocfilehash: 723cb277a7df592e0494505018f7422e4e40f5f6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496147"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a><span data-ttu-id="38f13-102">ICorProfilerInfo3::SetFunctionIDMapper2 方法</span><span class="sxs-lookup"><span data-stu-id="38f13-102">ICorProfilerInfo3::SetFunctionIDMapper2 Method</span></span>
<span data-ttu-id="38f13-103">指定将调用以将 `FunctionID` 值映射至替换值（传递至探查器的输入/退出挂钩）的探查器实现函数。</span><span class="sxs-lookup"><span data-stu-id="38f13-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span> <span data-ttu-id="38f13-104">此方法将[ICorProfilerInfo：： SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)方法与其他数据参数进行扩展，探查器可能会使用该参数来消除运行时之间的歧义。</span><span class="sxs-lookup"><span data-stu-id="38f13-104">This method extends the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method with an additional data parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38f13-105">语法</span><span class="sxs-lookup"><span data-stu-id="38f13-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38f13-106">参数</span><span class="sxs-lookup"><span data-stu-id="38f13-106">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="38f13-107">中指向[FunctionIDMapper2](functionidmapper2-function.md)实现的指针，将调用该指针以将 `FunctionID` 值映射到其可选值。</span><span class="sxs-lookup"><span data-stu-id="38f13-107">[in] A pointer to a [FunctionIDMapper2](functionidmapper2-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
 `clientData`  
 <span data-ttu-id="38f13-108">中传递给当前运行时所做的每个[FunctionIDMapper2](functionidmapper2-function.md)函数调用的指针。</span><span class="sxs-lookup"><span data-stu-id="38f13-108">[in] A pointer that is passed to every [FunctionIDMapper2](functionidmapper2-function.md) function call made by the current runtime.</span></span> <span data-ttu-id="38f13-109">探查器可使用此信息来消除运行时之间的歧义。</span><span class="sxs-lookup"><span data-stu-id="38f13-109">The profiler can use this information to disambiguate among runtimes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38f13-110">返回值</span><span class="sxs-lookup"><span data-stu-id="38f13-110">Return Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38f13-111">注解</span><span class="sxs-lookup"><span data-stu-id="38f13-111">Remarks</span></span>  
 <span data-ttu-id="38f13-112">FunctionID 值的替代项将传递到探查器的函数入口/出口挂钩（[FunctionEnter3](functionenter3-function.md)、 [FunctionLeave3](functionleave3-function.md)和[FunctionTailcall3](functiontailcall3-function.md) [; 或 FunctionEnter3WithInfo](functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](functionleave3withinfo-function.md)和[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)）（由[SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)或[SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)方法指定）。</span><span class="sxs-lookup"><span data-stu-id="38f13-112">The alternatives for the FunctionID values will be passed to the profiler's function entry/exit hooks ([FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md); or [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)) that are specified by the [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) or [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method.</span></span>  
  
 <span data-ttu-id="38f13-113">此 `FunctionIDMapper2` 方法只能设置一次; 建议在[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)回调中进行设置。</span><span class="sxs-lookup"><span data-stu-id="38f13-113">The `FunctionIDMapper2` method can be set only once; we recommend that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38f13-114">要求</span><span class="sxs-lookup"><span data-stu-id="38f13-114">Requirements</span></span>  
 <span data-ttu-id="38f13-115">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38f13-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38f13-116">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="38f13-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="38f13-117">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38f13-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38f13-118">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38f13-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f13-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="38f13-119">See also</span></span>

- [<span data-ttu-id="38f13-120">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="38f13-120">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="38f13-121">ICorProfilerInfo3 接口</span><span class="sxs-lookup"><span data-stu-id="38f13-121">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="38f13-122">分析接口</span><span class="sxs-lookup"><span data-stu-id="38f13-122">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="38f13-123">分析</span><span class="sxs-lookup"><span data-stu-id="38f13-123">Profiling</span></span>](index.md)
