---
title: ICLRProfiling::AttachProfiler 方法
ms.date: 03/30/2017
api_name:
- IClrProfiling.AttachProfiler Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- IClrProfiling::AttachProfiler
helpviewer_keywords:
- AttachProfiler method [.NET Framework profiling]
- IClrProfiling::AttachProfiler method [.NET Framework profiling]
ms.assetid: 535a6839-c443-405b-a6f4-e2af90725d5b
topic_type:
- apiref
ms.openlocfilehash: 48ac09e1862ae58e79707235e891f72920de1251
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500554"
---
# <a name="iclrprofilingattachprofiler-method"></a><span data-ttu-id="08eed-102">ICLRProfiling::AttachProfiler 方法</span><span class="sxs-lookup"><span data-stu-id="08eed-102">ICLRProfiling::AttachProfiler Method</span></span>
<span data-ttu-id="08eed-103">将指定的探查器附加到指定的进程中。</span><span class="sxs-lookup"><span data-stu-id="08eed-103">Attaches the specified profiler to the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08eed-104">语法</span><span class="sxs-lookup"><span data-stu-id="08eed-104">Syntax</span></span>  
  
```cpp  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a><span data-ttu-id="08eed-105">参数</span><span class="sxs-lookup"><span data-stu-id="08eed-105">Parameters</span></span>

- `dwProfileeProcessID`

  <span data-ttu-id="08eed-106">\[in] 应将探查器附加到的进程的进程 ID。</span><span class="sxs-lookup"><span data-stu-id="08eed-106">\[in] The process ID of the process to which the profiler should be attached.</span></span> <span data-ttu-id="08eed-107">在 64 位计算机上，被分析进程的位数必须匹配调用 `AttachProfiler` 的触发进程的位数。</span><span class="sxs-lookup"><span data-stu-id="08eed-107">On a 64-bit machine, the profiled process's bitness must match the bitness of the trigger process that is calling `AttachProfiler`.</span></span> <span data-ttu-id="08eed-108">如果调用 `AttachProfiler` 的用户帐户具有管理特权，则目标进程可能是系统上的任何进程。</span><span class="sxs-lookup"><span data-stu-id="08eed-108">If the user account under which `AttachProfiler` is called has administrative privileges, the target process may be any process on the system.</span></span> <span data-ttu-id="08eed-109">否则，相同的用户帐户必须拥有目标进程。</span><span class="sxs-lookup"><span data-stu-id="08eed-109">Otherwise, the target process must be owned by the same user account.</span></span>

- `dwMillisecondsMax`

  <span data-ttu-id="08eed-110">\[in] 完成的持续时间（以毫秒为单位） `AttachProfiler` 。</span><span class="sxs-lookup"><span data-stu-id="08eed-110">\[in] The time duration, in milliseconds, for `AttachProfiler` to complete.</span></span> <span data-ttu-id="08eed-111">触发器进程应传递一个特定探查器足以完成其初始化的已知超时。</span><span class="sxs-lookup"><span data-stu-id="08eed-111">The trigger process should pass a timeout that is known to be sufficient for the particular profiler to complete its initialization.</span></span>
  
- `pClsidProfiler`

  <span data-ttu-id="08eed-112">\[in] 一个指针，指向要加载的探查器的 CLSID。</span><span class="sxs-lookup"><span data-stu-id="08eed-112">\[in] A pointer to the CLSID of the profiler to be loaded.</span></span> <span data-ttu-id="08eed-113">`AttachProfiler` 返回后，触发器进程可重用此内存。</span><span class="sxs-lookup"><span data-stu-id="08eed-113">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span>

- `wszProfilerPath`

  <span data-ttu-id="08eed-114">\[in] 要加载的探查器 DLL 文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="08eed-114">\[in] The full path to the profiler’s DLL file to be loaded.</span></span> <span data-ttu-id="08eed-115">此字符串应包含不超过 260 个字符，包括 null 终止符。</span><span class="sxs-lookup"><span data-stu-id="08eed-115">This string should contain no more than 260 characters, including the null terminator.</span></span> <span data-ttu-id="08eed-116">如果 `wszProfilerPath` 为 null 或为空字符串，公共语言运行时 (CLR) 将通过在 `pClsidProfiler` 指向的 CLSID 的注册表中查找探查器的 DLL 文件的位置。</span><span class="sxs-lookup"><span data-stu-id="08eed-116">If `wszProfilerPath` is null or an empty string, the common language runtime (CLR) will try to find the location of the profiler’s DLL file by looking in the registry for the CLSID that `pClsidProfiler` points to.</span></span>

- `pvClientData`

  <span data-ttu-id="08eed-117">\[in] 一个指针，指向由[ICorProfilerCallback3：： InitializeForAttach](icorprofilercallback3-initializeforattach-method.md)方法传递到探查器的数据。</span><span class="sxs-lookup"><span data-stu-id="08eed-117">\[in] A pointer to data to be passed to the profiler by the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method.</span></span> <span data-ttu-id="08eed-118">`AttachProfiler` 返回后，触发器进程可重用此内存。</span><span class="sxs-lookup"><span data-stu-id="08eed-118">The trigger process can reuse this memory after `AttachProfiler` returns.</span></span> <span data-ttu-id="08eed-119">如果 `pvClientData` 为 null，`cbClientData` 必须为 0（零）。</span><span class="sxs-lookup"><span data-stu-id="08eed-119">If `pvClientData` is null, `cbClientData` must be 0 (zero).</span></span>

- `cbClientData`

  <span data-ttu-id="08eed-120">\[in] 指向的数据的大小（以字节为单位） `pvClientData` 。</span><span class="sxs-lookup"><span data-stu-id="08eed-120">\[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>

## <a name="return-value"></a><span data-ttu-id="08eed-121">返回值</span><span class="sxs-lookup"><span data-stu-id="08eed-121">Return Value</span></span>  
 <span data-ttu-id="08eed-122">此方法将返回以下 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="08eed-122">This method returns the following HRESULTs.</span></span>  
  
|<span data-ttu-id="08eed-123">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08eed-123">HRESULT</span></span>|<span data-ttu-id="08eed-124">说明</span><span class="sxs-lookup"><span data-stu-id="08eed-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08eed-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="08eed-125">S_OK</span></span>|<span data-ttu-id="08eed-126">指定的探查器已成功附加到目标进程中。</span><span class="sxs-lookup"><span data-stu-id="08eed-126">The specified profiler has successfully attached to the target process.</span></span>|  
|<span data-ttu-id="08eed-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span><span class="sxs-lookup"><span data-stu-id="08eed-127">CORPROF_E_PROFILER_ALREADY_ACTIVE</span></span>|<span data-ttu-id="08eed-128">已有活动的或附加到目标进程的探查器。</span><span class="sxs-lookup"><span data-stu-id="08eed-128">There is already a profiler active or attaching to the target process.</span></span>|  
|<span data-ttu-id="08eed-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span><span class="sxs-lookup"><span data-stu-id="08eed-129">CORPROF_E_PROFILER_NOT_ATTACHABLE</span></span>|<span data-ttu-id="08eed-130">指定的探查器不支持附件。</span><span class="sxs-lookup"><span data-stu-id="08eed-130">The specified profiler does not support attachment.</span></span> <span data-ttu-id="08eed-131">触发进程可能会尝试附加不同的探查器。</span><span class="sxs-lookup"><span data-stu-id="08eed-131">The trigger process may attempt to attach a different profiler.</span></span>|  
|<span data-ttu-id="08eed-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span><span class="sxs-lookup"><span data-stu-id="08eed-132">CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER</span></span>|<span data-ttu-id="08eed-133">无法请求探查器附件，因为目标进程的版本与当前正在调用 `AttachProfiler` 的进程不兼容。</span><span class="sxs-lookup"><span data-stu-id="08eed-133">Unable to request a profiler attachment, because the version of the target process is incompatible with the current process that is calling `AttachProfiler`.</span></span>|  
|<span data-ttu-id="08eed-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span><span class="sxs-lookup"><span data-stu-id="08eed-134">HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)</span></span>|<span data-ttu-id="08eed-135">触发进程的用户没有访问目标进程的权限。</span><span class="sxs-lookup"><span data-stu-id="08eed-135">The user of the trigger process does not have access to the target process.</span></span>|  
|<span data-ttu-id="08eed-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span><span class="sxs-lookup"><span data-stu-id="08eed-136">HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)</span></span>|<span data-ttu-id="08eed-137">触发进程的用户没有将探查器附加到给定的目标进程所必需的特权。</span><span class="sxs-lookup"><span data-stu-id="08eed-137">The user of the trigger process does not have the privileges necessary to attach a profiler to the given target process.</span></span> <span data-ttu-id="08eed-138">应用程序事件日志可能包含详细信息。</span><span class="sxs-lookup"><span data-stu-id="08eed-138">The application event log may contain more information.</span></span>|  
|<span data-ttu-id="08eed-139">CORPROF_E_IPC_FAILED</span><span class="sxs-lookup"><span data-stu-id="08eed-139">CORPROF_E_IPC_FAILED</span></span>|<span data-ttu-id="08eed-140">与目标进程进行通信时发生错误。</span><span class="sxs-lookup"><span data-stu-id="08eed-140">A failure occurred when communicating with the target process.</span></span> <span data-ttu-id="08eed-141">通常在目标进程已关闭时，会发生此类错误。</span><span class="sxs-lookup"><span data-stu-id="08eed-141">This commonly happens if the target process was shutting down.</span></span>|  
|<span data-ttu-id="08eed-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="08eed-142">HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)</span></span>|<span data-ttu-id="08eed-143">目标进程中不存在或未运行支持附件的 CLR。</span><span class="sxs-lookup"><span data-stu-id="08eed-143">The target process does not exist or is not running a CLR that supports attachment.</span></span> <span data-ttu-id="08eed-144">这可能表示，自调用运行时枚举方法时，就已卸载 CLR。</span><span class="sxs-lookup"><span data-stu-id="08eed-144">This may indicate that the CLR was unloaded since the call to the runtime enumeration method.</span></span>|  
|<span data-ttu-id="08eed-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span><span class="sxs-lookup"><span data-stu-id="08eed-145">HRESULT_FROM_WIN32(ERROR_TIMEOUT)</span></span>|<span data-ttu-id="08eed-146">尚未开始加载探查器，超时就已过期。</span><span class="sxs-lookup"><span data-stu-id="08eed-146">The timeout expired without beginning to load the profiler.</span></span> <span data-ttu-id="08eed-147">可重试附加操作。</span><span class="sxs-lookup"><span data-stu-id="08eed-147">You can retry the attach operation.</span></span> <span data-ttu-id="08eed-148">当目标进程中的终结器运行时间长于超时值时，就会出现超时。</span><span class="sxs-lookup"><span data-stu-id="08eed-148">Timeouts occur when a finalizer in the target process runs for a longer time than the timeout value.</span></span>|  
|<span data-ttu-id="08eed-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="08eed-149">E_INVALIDARG</span></span>|<span data-ttu-id="08eed-150">一个或多个参数具有无效值。</span><span class="sxs-lookup"><span data-stu-id="08eed-150">One or more parameters have invalid values.</span></span>|  
|<span data-ttu-id="08eed-151">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="08eed-151">E_FAIL</span></span>|<span data-ttu-id="08eed-152">出现其他未指定错误。</span><span class="sxs-lookup"><span data-stu-id="08eed-152">Some other, unspecified failure occurred.</span></span>|  
|<span data-ttu-id="08eed-153">其他错误代码</span><span class="sxs-lookup"><span data-stu-id="08eed-153">Other error codes</span></span>|<span data-ttu-id="08eed-154">如果探查器的[ICorProfilerCallback3：： InitializeForAttach](icorprofilercallback3-initializeforattach-method.md)方法返回一个指示失败的 hresult，则 `AttachProfiler` 返回相同的 hresult。</span><span class="sxs-lookup"><span data-stu-id="08eed-154">If the profiler’s [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method returns an HRESULT that indicates failure, `AttachProfiler` returns that same HRESULT.</span></span> <span data-ttu-id="08eed-155">在这种情况下，E_NOTIMPL 将转换为 CORPROF_E_PROFILER_NOT_ATTACHABLE。</span><span class="sxs-lookup"><span data-stu-id="08eed-155">In this case, E_NOTIMPL is converted to CORPROF_E_PROFILER_NOT_ATTACHABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08eed-156">注解</span><span class="sxs-lookup"><span data-stu-id="08eed-156">Remarks</span></span>  
  
## <a name="memory-management"></a><span data-ttu-id="08eed-157">内存管理</span><span class="sxs-lookup"><span data-stu-id="08eed-157">Memory Management</span></span>  
 <span data-ttu-id="08eed-158">与 COM 约定一致，`AttachProfiler` 的调用方（例如，由探查器开发人员创作的触发器代码）将负责分配和释放 `pvClientData` 参数指向的数据的内存。</span><span class="sxs-lookup"><span data-stu-id="08eed-158">In keeping with COM conventions, the caller of `AttachProfiler` (for example, the trigger code authored by the profiler developer) is responsible for allocating and de-allocating the memory for the data that the `pvClientData` parameter points to.</span></span> <span data-ttu-id="08eed-159">当 CLR 执行 `AttachProfiler` 调用时，会创建 `pvClientData` 指向的内存的副本，并将其传输到目标进程中。</span><span class="sxs-lookup"><span data-stu-id="08eed-159">When the CLR executes the `AttachProfiler` call, it makes a copy of the memory that `pvClientData` points to and transmits it to the target process.</span></span> <span data-ttu-id="08eed-160">当目标进程内部的 CLR 接收到自己的 `pvClientData` 块副本时，会通过 `InitializeForAttach` 方法将块传递给探查器，然后从目标进程释放其 `pvClientData` 块的副本。</span><span class="sxs-lookup"><span data-stu-id="08eed-160">When the CLR inside the target process receives its own copy of the `pvClientData` block, it passes the block to the profiler through the `InitializeForAttach` method, and then deallocates its copy of the `pvClientData` block from the target process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08eed-161">要求</span><span class="sxs-lookup"><span data-stu-id="08eed-161">Requirements</span></span>  
 <span data-ttu-id="08eed-162">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="08eed-162">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08eed-163">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="08eed-163">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="08eed-164">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08eed-164">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08eed-165">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08eed-165">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08eed-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="08eed-166">See also</span></span>

- [<span data-ttu-id="08eed-167">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="08eed-167">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="08eed-168">ICorProfilerInfo3 接口</span><span class="sxs-lookup"><span data-stu-id="08eed-168">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="08eed-169">分析接口</span><span class="sxs-lookup"><span data-stu-id="08eed-169">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="08eed-170">分析</span><span class="sxs-lookup"><span data-stu-id="08eed-170">Profiling</span></span>](index.md)
