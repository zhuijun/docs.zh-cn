---
title: ICorProfilerInfo4::RequestRevert 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
ms.openlocfilehash: b85a7893cf5271c65bc842bb6ea598c825225376
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495718"
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="4afcc-102">ICorProfilerInfo4::RequestRevert 方法</span><span class="sxs-lookup"><span data-stu-id="4afcc-102">ICorProfilerInfo4::RequestRevert Method</span></span>
<span data-ttu-id="4afcc-103">将指定函数的所有实例还原为其初始版本。</span><span class="sxs-lookup"><span data-stu-id="4afcc-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4afcc-104">语法</span><span class="sxs-lookup"><span data-stu-id="4afcc-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4afcc-105">参数</span><span class="sxs-lookup"><span data-stu-id="4afcc-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="4afcc-106">[in] 要还原的函数数目。</span><span class="sxs-lookup"><span data-stu-id="4afcc-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="4afcc-107">[in] 指定（`module`、`methodDef`）对的 `moduleId` 部分，它标识要还原的函数。</span><span class="sxs-lookup"><span data-stu-id="4afcc-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="4afcc-108">[in] 指定（`module`、`methodDef`）对的 `methodId` 部分，它标识要还原的函数。</span><span class="sxs-lookup"><span data-stu-id="4afcc-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="4afcc-109">[out] 在本主题后面的“状态 HRESULT”章节中列出的 HRESULT 数组。</span><span class="sxs-lookup"><span data-stu-id="4afcc-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="4afcc-110">每个 HRESULT 表示尝试还原并行数组 `moduleIds` 和 `methodIds` 中指定的每个函数是成功还是失败。</span><span class="sxs-lookup"><span data-stu-id="4afcc-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4afcc-111">返回值</span><span class="sxs-lookup"><span data-stu-id="4afcc-111">Return Value</span></span>  
 <span data-ttu-id="4afcc-112">此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。</span><span class="sxs-lookup"><span data-stu-id="4afcc-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4afcc-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4afcc-113">HRESULT</span></span>|<span data-ttu-id="4afcc-114">说明</span><span class="sxs-lookup"><span data-stu-id="4afcc-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4afcc-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="4afcc-115">S_OK</span></span>|<span data-ttu-id="4afcc-116">尝试还原所有请求；但是，必须检查返回的状态数组，确定成功还原了哪些函数。</span><span class="sxs-lookup"><span data-stu-id="4afcc-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="4afcc-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="4afcc-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="4afcc-118">探查器必须实现[ICorProfilerCallback4](icorprofilercallback4-interface.md)接口，以便支持此调用。</span><span class="sxs-lookup"><span data-stu-id="4afcc-118">The profiler must implement the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="4afcc-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="4afcc-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="4afcc-120">尚未启用 JIT 重新编译。</span><span class="sxs-lookup"><span data-stu-id="4afcc-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="4afcc-121">必须通过使用[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)方法设置标志来在初始化期间启用 JIT 重新编译 `COR_PRF_ENABLE_REJIT` 。</span><span class="sxs-lookup"><span data-stu-id="4afcc-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="4afcc-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4afcc-122">E_INVALIDARG</span></span>|<span data-ttu-id="4afcc-123">`cFunctions` 为 0，或者 `moduleIds` 或 `methodIds` 为 `NULL`。</span><span class="sxs-lookup"><span data-stu-id="4afcc-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="4afcc-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4afcc-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4afcc-125">CLR 无法完成请求，因为它已耗尽内存。</span><span class="sxs-lookup"><span data-stu-id="4afcc-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="4afcc-126">状态 HRESULTS</span><span class="sxs-lookup"><span data-stu-id="4afcc-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="4afcc-127">状态数组 HRESULT</span><span class="sxs-lookup"><span data-stu-id="4afcc-127">Status array HRESULT</span></span>|<span data-ttu-id="4afcc-128">说明</span><span class="sxs-lookup"><span data-stu-id="4afcc-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="4afcc-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="4afcc-129">S_OK</span></span>|<span data-ttu-id="4afcc-130">已成功还原相应函数。</span><span class="sxs-lookup"><span data-stu-id="4afcc-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="4afcc-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4afcc-131">E_INVALIDARG</span></span>|<span data-ttu-id="4afcc-132">`moduleID` 或 `methodDef` 参数为 `NULL`。</span><span class="sxs-lookup"><span data-stu-id="4afcc-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="4afcc-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="4afcc-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="4afcc-134">该模块尚未完全加载，或正在被卸载。</span><span class="sxs-lookup"><span data-stu-id="4afcc-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="4afcc-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="4afcc-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="4afcc-136">已动态生成指定模块（例如通过 `Reflection.Emit` 生成）。</span><span class="sxs-lookup"><span data-stu-id="4afcc-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="4afcc-137">因此，此方法不支持它。</span><span class="sxs-lookup"><span data-stu-id="4afcc-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="4afcc-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="4afcc-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="4afcc-139">CLR 无法还原指定函数，因为找不到对应的活动的重新编译请求。</span><span class="sxs-lookup"><span data-stu-id="4afcc-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="4afcc-140">从未请求重新编译或此函数已还原。</span><span class="sxs-lookup"><span data-stu-id="4afcc-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="4afcc-141">其他</span><span class="sxs-lookup"><span data-stu-id="4afcc-141">Other</span></span>|<span data-ttu-id="4afcc-142">操作系统返回了 CLR 控件范围之外的失败。</span><span class="sxs-lookup"><span data-stu-id="4afcc-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="4afcc-143">例如，如果用于更改内存页访问权限保护的系统调用失败，将显示操作系统错误。</span><span class="sxs-lookup"><span data-stu-id="4afcc-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4afcc-144">注解</span><span class="sxs-lookup"><span data-stu-id="4afcc-144">Remarks</span></span>  
 <span data-ttu-id="4afcc-145">在下次调用任何已还原的函数实例时，将运行此函数的初始版本。</span><span class="sxs-lookup"><span data-stu-id="4afcc-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="4afcc-146">如果已在运行某个函数，则将完成正在运行的版本的执行操作。</span><span class="sxs-lookup"><span data-stu-id="4afcc-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4afcc-147">要求</span><span class="sxs-lookup"><span data-stu-id="4afcc-147">Requirements</span></span>  
 <span data-ttu-id="4afcc-148">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4afcc-148">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4afcc-149">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4afcc-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4afcc-150">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4afcc-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4afcc-151">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4afcc-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4afcc-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4afcc-152">See also</span></span>

- [<span data-ttu-id="4afcc-153">ICorProfilerInfo4 接口</span><span class="sxs-lookup"><span data-stu-id="4afcc-153">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="4afcc-154">分析接口</span><span class="sxs-lookup"><span data-stu-id="4afcc-154">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="4afcc-155">分析</span><span class="sxs-lookup"><span data-stu-id="4afcc-155">Profiling</span></span>](index.md)
