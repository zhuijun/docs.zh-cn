---
title: ICorProfilerCallback4::ReJITError 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
ms.openlocfilehash: 488069f3ea16352cb7bb5e81b9a726637a7a65f8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499358"
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="1bd88-102">ICorProfilerCallback4::ReJITError 方法</span><span class="sxs-lookup"><span data-stu-id="1bd88-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="1bd88-103">通知探查器，实时（JIT）编译器在重新编译过程中遇到错误。</span><span class="sxs-lookup"><span data-stu-id="1bd88-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bd88-104">语法</span><span class="sxs-lookup"><span data-stu-id="1bd88-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bd88-105">参数</span><span class="sxs-lookup"><span data-stu-id="1bd88-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="1bd88-106">中`ModuleID`尝试重新编译失败的。</span><span class="sxs-lookup"><span data-stu-id="1bd88-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="1bd88-107">中`MethodDef`尝试重新编译失败的方法的。</span><span class="sxs-lookup"><span data-stu-id="1bd88-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="1bd88-108">中正在重新编译或标记为要重新编译的函数实例。</span><span class="sxs-lookup"><span data-stu-id="1bd88-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="1bd88-109">`NULL`如果失败发生在每个方法的基础上，而不是基于每个实例化的，则此值可能为（例如，如果探查器为要重新编译的方法指定了无效的元数据标记）。</span><span class="sxs-lookup"><span data-stu-id="1bd88-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="1bd88-110">中指示失败性质的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="1bd88-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="1bd88-111">有关值的列表，请参阅状态 HRESULT 部分。</span><span class="sxs-lookup"><span data-stu-id="1bd88-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bd88-112">返回值</span><span class="sxs-lookup"><span data-stu-id="1bd88-112">Return Value</span></span>  
 <span data-ttu-id="1bd88-113">将忽略此回调的返回值。</span><span class="sxs-lookup"><span data-stu-id="1bd88-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="1bd88-114">状态 HRESULTS</span><span class="sxs-lookup"><span data-stu-id="1bd88-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="1bd88-115">状态数组 HRESULT</span><span class="sxs-lookup"><span data-stu-id="1bd88-115">Status array HRESULT</span></span>|<span data-ttu-id="1bd88-116">说明</span><span class="sxs-lookup"><span data-stu-id="1bd88-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="1bd88-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1bd88-117">E_INVALIDARG</span></span>|<span data-ttu-id="1bd88-118">`moduleID`或 `methodDef` 标记为 `NULL` 。</span><span class="sxs-lookup"><span data-stu-id="1bd88-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="1bd88-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="1bd88-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="1bd88-120">该模块尚未完全加载，或正在被卸载。</span><span class="sxs-lookup"><span data-stu-id="1bd88-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="1bd88-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="1bd88-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="1bd88-122">指定的模块是动态生成的（例如，通过 `Reflection.Emit` ），因此不受此方法支持。</span><span class="sxs-lookup"><span data-stu-id="1bd88-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="1bd88-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="1bd88-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="1bd88-124">方法被实例化为可回收的程序集，因此无法重新编译。</span><span class="sxs-lookup"><span data-stu-id="1bd88-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="1bd88-125">请注意，在非反射上下文中定义的类型和函数（例如 `List<MyCollectibleStruct>` ）可实例化为可回收的程序集。</span><span class="sxs-lookup"><span data-stu-id="1bd88-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="1bd88-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1bd88-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1bd88-127">尝试将指定的方法标记为 JIT 重新编译时，CLR 用尽了内存。</span><span class="sxs-lookup"><span data-stu-id="1bd88-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="1bd88-128">其他</span><span class="sxs-lookup"><span data-stu-id="1bd88-128">Other</span></span>|<span data-ttu-id="1bd88-129">操作系统返回了 CLR 控件范围之外的失败。</span><span class="sxs-lookup"><span data-stu-id="1bd88-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="1bd88-130">例如，如果系统调用更改内存页的访问保护失败，则会显示操作系统错误。</span><span class="sxs-lookup"><span data-stu-id="1bd88-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1bd88-131">要求</span><span class="sxs-lookup"><span data-stu-id="1bd88-131">Requirements</span></span>  
 <span data-ttu-id="1bd88-132">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1bd88-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bd88-133">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1bd88-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1bd88-134">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bd88-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bd88-135">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bd88-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bd88-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1bd88-136">See also</span></span>

- [<span data-ttu-id="1bd88-137">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="1bd88-137">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1bd88-138">ICorProfilerCallback4 接口</span><span class="sxs-lookup"><span data-stu-id="1bd88-138">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
