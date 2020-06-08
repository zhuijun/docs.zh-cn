---
title: ICorProfilerInfo::SetFunctionIDMapper 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetFunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetFunctionIDMapper
helpviewer_keywords:
- ICorProfilerInfo::SetFunctionIDMapper method [.NET Framework profiling]
- SetFunctionIDMapper method [.NET Framework profiling]
ms.assetid: 1a6e5dae-d366-4497-9c02-7b5b1f43f9ec
topic_type:
- apiref
ms.openlocfilehash: 5272c5bf256f6e21a83470db094ab79317932018
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497473"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="216e6-102">ICorProfilerInfo::SetFunctionIDMapper 方法</span><span class="sxs-lookup"><span data-stu-id="216e6-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>
<span data-ttu-id="216e6-103">指定将调用以将 `FunctionID` 值映射至替换值（传递至探查器的输入/退出挂钩）的探查器实现函数。</span><span class="sxs-lookup"><span data-stu-id="216e6-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="216e6-104">语法</span><span class="sxs-lookup"><span data-stu-id="216e6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="216e6-105">参数</span><span class="sxs-lookup"><span data-stu-id="216e6-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="216e6-106">中指向[FunctionIDMapper](functionidmapper-function.md)实现的指针，将调用该指针以将 `FunctionID` 值映射到其可选值。</span><span class="sxs-lookup"><span data-stu-id="216e6-106">[in] A pointer to the [FunctionIDMapper](functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="216e6-107">注解</span><span class="sxs-lookup"><span data-stu-id="216e6-107">Remarks</span></span>  
 <span data-ttu-id="216e6-108">值的替代 `FunctionID` 项将传递到由[ICorProfilerInfo2：： SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)方法指定的探查器的函数入口/出口挂钩（[FunctionEnter2](functionenter2-function.md)、 [FunctionLeave2](functionleave2-function.md)和[FunctionTailcall2](functiontailcall2-function.md)）。</span><span class="sxs-lookup"><span data-stu-id="216e6-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="216e6-109">只能 `FunctionIDMapper` 设置一次，并建议你在[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)回调中对其进行设置。</span><span class="sxs-lookup"><span data-stu-id="216e6-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="216e6-110">要求</span><span class="sxs-lookup"><span data-stu-id="216e6-110">Requirements</span></span>  
 <span data-ttu-id="216e6-111">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="216e6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="216e6-112">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="216e6-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="216e6-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="216e6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="216e6-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="216e6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="216e6-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="216e6-115">See also</span></span>

- [<span data-ttu-id="216e6-116">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="216e6-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
