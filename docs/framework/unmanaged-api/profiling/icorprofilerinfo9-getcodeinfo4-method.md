---
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: ecaff179378eb417393c0a0d17d0a00d3b99e5a4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541293"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="2074e-102">ICorProfilerInfo9：： GetCodeInfo4 方法</span><span class="sxs-lookup"><span data-stu-id="2074e-102">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>

<span data-ttu-id="2074e-103">给定本机代码起始地址，返回存储此代码的虚拟内存块。</span><span class="sxs-lookup"><span data-stu-id="2074e-103">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>

## <a name="syntax"></a><span data-ttu-id="2074e-104">语法</span><span class="sxs-lookup"><span data-stu-id="2074e-104">Syntax</span></span>

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a><span data-ttu-id="2074e-105">参数</span><span class="sxs-lookup"><span data-stu-id="2074e-105">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="2074e-106">\[in] 指向本机函数开头的指针。</span><span class="sxs-lookup"><span data-stu-id="2074e-106">\[in] A pointer to the start of a native function.</span></span>

- `cCodeInfos`

  <span data-ttu-id="2074e-107">\[in] 数组的大小 `codeInfos` 。</span><span class="sxs-lookup"><span data-stu-id="2074e-107">\[in] The size of the `codeInfos` array.</span></span>

- `pcCodeInfos`

  <span data-ttu-id="2074e-108">\[out] 指向可用 [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 结构总数的指针。</span><span class="sxs-lookup"><span data-stu-id="2074e-108">\[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>

- `codeInfos`

  <span data-ttu-id="2074e-109">\[out] 调用方提供的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="2074e-109">\[out] A caller-provided buffer.</span></span> <span data-ttu-id="2074e-110">返回此方法后，它包含一个 `COR_PRF_CODE_INFO` 结构数组，每个结构描述一个本机代码块。</span><span class="sxs-lookup"><span data-stu-id="2074e-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2074e-111">备注</span><span class="sxs-lookup"><span data-stu-id="2074e-111">Remarks</span></span>

<span data-ttu-id="2074e-112">`GetCodeInfo4`方法类似于[GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md)，只不过它可以查找方法的不同本机版本的代码信息。</span><span class="sxs-lookup"><span data-stu-id="2074e-112">The `GetCodeInfo4` method is similar to [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>

> [!NOTE]
> <span data-ttu-id="2074e-113">`GetCodeInfo4` 可以触发垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="2074e-113">`GetCodeInfo4` can trigger a garbage collection.</span></span>

<span data-ttu-id="2074e-114">范围按公共中间语言 (CIL) 偏移递增的顺序进行排序。</span><span class="sxs-lookup"><span data-stu-id="2074e-114">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>

<span data-ttu-id="2074e-115">`GetCodeInfo4`返回后，必须验证 `codeInfos` 缓冲区大小是否足以包含所有[COR_PRF_CODE_INFO](cor-prf-code-info-structure.md)的结构。</span><span class="sxs-lookup"><span data-stu-id="2074e-115">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="2074e-116">为此，请将 `cCodeInfos` 的值和 `cchName` 参数的值进行比较。</span><span class="sxs-lookup"><span data-stu-id="2074e-116">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="2074e-117">如果 `cCodeInfos` 除以 [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 结构的大小小于 `pcCodeInfos` ，则分配更大的 `codeInfos` 缓冲区， `cCodeInfos` 用新的、更大的大小更新，然后再次调用 `GetCodeInfo4` 。</span><span class="sxs-lookup"><span data-stu-id="2074e-117">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>

<span data-ttu-id="2074e-118">或者，可以先用长度为零的 `codeInfos` 缓冲区调用 `GetCodeInfo4` 以获取正确的缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="2074e-118">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="2074e-119">然后，可以将 `codeInfos` 缓冲区大小设置为中返回的值 `pcCodeInfos` ，再乘以 [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 结构的大小，然后 `GetCodeInfo4` 再次调用。</span><span class="sxs-lookup"><span data-stu-id="2074e-119">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>

## <a name="requirements"></a><span data-ttu-id="2074e-120">要求</span><span class="sxs-lookup"><span data-stu-id="2074e-120">Requirements</span></span>

<span data-ttu-id="2074e-121">**平台：** 请参阅 [支持 .Net Core 的操作系统](../../../core/install/windows.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="2074e-121">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="2074e-122">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2074e-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="2074e-123">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2074e-123">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="2074e-124">**.Net 版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2074e-124">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2074e-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="2074e-125">See also</span></span>

- [<span data-ttu-id="2074e-126">ICorProfilerInfo9 接口</span><span class="sxs-lookup"><span data-stu-id="2074e-126">ICorProfilerInfo9 Interface</span></span>](ICorProfilerInfo9-interface.md)
