---
title: ICorProfilerInfo::GetModuleInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
ms.openlocfilehash: 751f2ac44e543fed76c7031791bb57d75ed0fd48
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498097"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="40d1c-102">ICorProfilerInfo::GetModuleInfo 方法</span><span class="sxs-lookup"><span data-stu-id="40d1c-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="40d1c-103">给定模块 ID 后，将返回模块的文件名和模块的父程序集的 ID。</span><span class="sxs-lookup"><span data-stu-id="40d1c-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40d1c-104">语法</span><span class="sxs-lookup"><span data-stu-id="40d1c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40d1c-105">参数</span><span class="sxs-lookup"><span data-stu-id="40d1c-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="40d1c-106">[in] 将为其检索信息的模块的 ID。</span><span class="sxs-lookup"><span data-stu-id="40d1c-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="40d1c-107">[out] 加载模块的基址。</span><span class="sxs-lookup"><span data-stu-id="40d1c-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="40d1c-108">[in] `szName` 返回缓冲区的长度（以字符为单位）。</span><span class="sxs-lookup"><span data-stu-id="40d1c-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="40d1c-109">[out] 指向返回的模块文件名总字符长度的指针。</span><span class="sxs-lookup"><span data-stu-id="40d1c-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="40d1c-110">[out] 调用方提供的宽字符缓冲区。</span><span class="sxs-lookup"><span data-stu-id="40d1c-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="40d1c-111">方法返回后，此缓冲区包含模块的文件名。</span><span class="sxs-lookup"><span data-stu-id="40d1c-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="40d1c-112">[out] 指向模块的父程序集的 ID 的指针。</span><span class="sxs-lookup"><span data-stu-id="40d1c-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40d1c-113">注解</span><span class="sxs-lookup"><span data-stu-id="40d1c-113">Remarks</span></span>  
 <span data-ttu-id="40d1c-114">对于动态模块，`szName` 参数是空字符串，并且基址是 0（零）。</span><span class="sxs-lookup"><span data-stu-id="40d1c-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="40d1c-115">尽管在 `GetModuleInfo` 模块的 ID 存在后可以调用方法，但在探查器接收到[ICorProfilerCallback：： ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md)回调之前，父程序集的 ID 将不可用。</span><span class="sxs-lookup"><span data-stu-id="40d1c-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="40d1c-116">返回 `GetModuleInfo` 后，必须验证 `szName` 缓冲区的大小是否足够包含模块的完整文件名。</span><span class="sxs-lookup"><span data-stu-id="40d1c-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="40d1c-117">为此，请比较 `pcchName` 指向的值和 `cchName` 参数的值。</span><span class="sxs-lookup"><span data-stu-id="40d1c-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="40d1c-118">如果 `pcchName` 指向的值大于 `cchName`，请分配更大的 `szName` 缓冲区，并用新的、更大的大小更新 `cchName`，然后再次调用 `GetModuleInfo`。</span><span class="sxs-lookup"><span data-stu-id="40d1c-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="40d1c-119">或者，可以先用长度为零的 `szName` 缓冲区调用 `GetModuleInfo` 以获取正确的缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="40d1c-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="40d1c-120">然后，可将缓冲区大小设置为 `pcchName` 中返回的值，并再次调用 `GetModuleInfo`。</span><span class="sxs-lookup"><span data-stu-id="40d1c-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40d1c-121">要求</span><span class="sxs-lookup"><span data-stu-id="40d1c-121">Requirements</span></span>  
 <span data-ttu-id="40d1c-122">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="40d1c-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40d1c-123">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="40d1c-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="40d1c-124">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40d1c-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40d1c-125">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40d1c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40d1c-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="40d1c-126">See also</span></span>

- [<span data-ttu-id="40d1c-127">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="40d1c-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="40d1c-128">分析接口</span><span class="sxs-lookup"><span data-stu-id="40d1c-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="40d1c-129">分析</span><span class="sxs-lookup"><span data-stu-id="40d1c-129">Profiling</span></span>](index.md)
- [<span data-ttu-id="40d1c-130">GetModuleInfo2 方法</span><span class="sxs-lookup"><span data-stu-id="40d1c-130">GetModuleInfo2 Method</span></span>](icorprofilerinfo3-getmoduleinfo2-method.md)
