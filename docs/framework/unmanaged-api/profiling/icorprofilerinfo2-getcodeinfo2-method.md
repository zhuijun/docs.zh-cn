---
title: ICorProfilerInfo2::GetCodeInfo2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
ms.openlocfilehash: 04ce9ebded4be7ac3b20a4ceb78dd02294bbff4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502888"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="24db0-102">ICorProfilerInfo2::GetCodeInfo2 方法</span><span class="sxs-lookup"><span data-stu-id="24db0-102">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>
<span data-ttu-id="24db0-103">获取与指定 `FunctionID` 关联的本机代码的范围。</span><span class="sxs-lookup"><span data-stu-id="24db0-103">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24db0-104">语法</span><span class="sxs-lookup"><span data-stu-id="24db0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24db0-105">参数</span><span class="sxs-lookup"><span data-stu-id="24db0-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="24db0-106">[in] 与本机代码关联的函数的 ID。</span><span class="sxs-lookup"><span data-stu-id="24db0-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="24db0-107">[in] `codeInfos` 数组的大小。</span><span class="sxs-lookup"><span data-stu-id="24db0-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="24db0-108">弄指向可用[COR_PRF_CODE_INFO](cor-prf-code-info-structure.md)结构总数的指针。</span><span class="sxs-lookup"><span data-stu-id="24db0-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="24db0-109">[out] 调用方提供的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="24db0-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="24db0-110">返回此方法后，它包含一个 `COR_PRF_CODE_INFO` 结构数组，每个结构描述一个本机代码块。</span><span class="sxs-lookup"><span data-stu-id="24db0-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24db0-111">注解</span><span class="sxs-lookup"><span data-stu-id="24db0-111">Remarks</span></span>  
 <span data-ttu-id="24db0-112">范围按 Microsoft 中间语言 (MSIL) 偏移递增的顺序进行排序。</span><span class="sxs-lookup"><span data-stu-id="24db0-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="24db0-113">返回 `GetCodeInfo2` 后，必须验证 `codeInfos` 缓冲区大小是否足以包含所有 `COR_PRF_CODE_INFO` 结构。</span><span class="sxs-lookup"><span data-stu-id="24db0-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="24db0-114">为此，请将 `cCodeInfos` 的值和 `cchName` 参数的值进行比较。</span><span class="sxs-lookup"><span data-stu-id="24db0-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="24db0-115">如果由 `COR_PRF_CODE_INFO` 结构大小划分的 `cCodeInfos` 值小于 `pcCodeInfos` 值，请分配更大的 `codeInfos` 缓冲区，将 `cCodeInfos` 更新为新的更大大小，并再次调用 `GetCodeInfo2`。</span><span class="sxs-lookup"><span data-stu-id="24db0-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="24db0-116">或者，可以先用长度为零的 `codeInfos` 缓冲区调用 `GetCodeInfo2` 以获取正确的缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="24db0-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="24db0-117">然后可将 `codeInfos` 缓冲区大小设置为 `pcCodeInfos` 中返回的，乘以 `COR_PRF_CODE_INFO` 结构大小的值，并再次调用 `GetCodeInfo2`。</span><span class="sxs-lookup"><span data-stu-id="24db0-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24db0-118">要求</span><span class="sxs-lookup"><span data-stu-id="24db0-118">Requirements</span></span>  
 <span data-ttu-id="24db0-119">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="24db0-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24db0-120">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="24db0-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="24db0-121">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24db0-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24db0-122">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24db0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24db0-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="24db0-123">See also</span></span>

- [<span data-ttu-id="24db0-124">GetCodeInfo3 方法</span><span class="sxs-lookup"><span data-stu-id="24db0-124">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)
- [<span data-ttu-id="24db0-125">ICorProfilerInfo2 接口</span><span class="sxs-lookup"><span data-stu-id="24db0-125">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="24db0-126">分析接口</span><span class="sxs-lookup"><span data-stu-id="24db0-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="24db0-127">分析</span><span class="sxs-lookup"><span data-stu-id="24db0-127">Profiling</span></span>](index.md)
