---
title: ICorProfilerInfo3::GetFunctionTailcall3Info 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
ms.openlocfilehash: e4d0d9ed07c707e51e5833483b71079f2c330505
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496524"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="482f7-102">ICorProfilerInfo3::GetFunctionTailcall3Info 方法</span><span class="sxs-lookup"><span data-stu-id="482f7-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="482f7-103">提供由[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)函数向探查器报告的函数的堆栈帧。</span><span class="sxs-lookup"><span data-stu-id="482f7-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="482f7-104">仅在 `FunctionTailcall3WithInfo` 回调时可调用此方法。</span><span class="sxs-lookup"><span data-stu-id="482f7-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="482f7-105">语法</span><span class="sxs-lookup"><span data-stu-id="482f7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="482f7-106">参数</span><span class="sxs-lookup"><span data-stu-id="482f7-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="482f7-107">中`FunctionID`正在返回的函数的。</span><span class="sxs-lookup"><span data-stu-id="482f7-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="482f7-108">[in] 表示有关给定堆栈帧的信息的不透明的句柄。</span><span class="sxs-lookup"><span data-stu-id="482f7-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="482f7-109">探查器应提供 `eltInfo` 由函数为探查器提供的相同的 `FunctionTailcall3WithInfo` 。</span><span class="sxs-lookup"><span data-stu-id="482f7-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="482f7-110">[out] 表示有关给定堆栈帧的泛型信息的不透明的句柄。</span><span class="sxs-lookup"><span data-stu-id="482f7-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="482f7-111">此句柄仅在探查器调用 `GetFunctionTailcall3Info` 方法的 `FunctionTailcall3WithInfo` 回调时有效。</span><span class="sxs-lookup"><span data-stu-id="482f7-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="482f7-112">备注</span><span class="sxs-lookup"><span data-stu-id="482f7-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="482f7-113">要求</span><span class="sxs-lookup"><span data-stu-id="482f7-113">Requirements</span></span>  
 <span data-ttu-id="482f7-114">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="482f7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="482f7-115">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="482f7-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="482f7-116">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="482f7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="482f7-117">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="482f7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="482f7-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="482f7-118">See also</span></span>

- [<span data-ttu-id="482f7-119">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="482f7-119">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="482f7-120">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="482f7-120">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="482f7-121">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="482f7-121">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="482f7-122">ICorProfilerInfo3 接口</span><span class="sxs-lookup"><span data-stu-id="482f7-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="482f7-123">分析接口</span><span class="sxs-lookup"><span data-stu-id="482f7-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="482f7-124">分析</span><span class="sxs-lookup"><span data-stu-id="482f7-124">Profiling</span></span>](index.md)
