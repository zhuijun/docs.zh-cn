---
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: e3d5a09730cb8e477bd506749017a403acff1696
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540551"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="d541d-102">ICorProfilerInfo10：： RequestReJITWithInliners 方法</span><span class="sxs-lookup"><span data-stu-id="d541d-102">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>

<span data-ttu-id="d541d-103">ReJITs 请求的方法，以及所请求的方法的任何 inliners。</span><span class="sxs-lookup"><span data-stu-id="d541d-103">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>

## <a name="syntax"></a><span data-ttu-id="d541d-104">语法</span><span class="sxs-lookup"><span data-stu-id="d541d-104">Syntax</span></span>

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a><span data-ttu-id="d541d-105">参数</span><span class="sxs-lookup"><span data-stu-id="d541d-105">Parameters</span></span>

- `dwRejitFlags`

  <span data-ttu-id="d541d-106">\[in] [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md)的位掩码。</span><span class="sxs-lookup"><span data-stu-id="d541d-106">\[in] A bitmask of [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span></span>

- `cFunctions`

  <span data-ttu-id="d541d-107">\[in] 要重新编译的函数的数目。</span><span class="sxs-lookup"><span data-stu-id="d541d-107">\[in] The number of functions to recompile.</span></span>

- `moduleIds`

  <span data-ttu-id="d541d-108">\[in] 指定 `moduleId` (的部分 `module` ，) 对，用于 `methodDef` 标识要重新编译的函数。</span><span class="sxs-lookup"><span data-stu-id="d541d-108">\[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

- `methodIds`

  <span data-ttu-id="d541d-109">\[in] 指定 `methodId` (的部分 `module` ，) 对，用于 `methodDef` 标识要重新编译的函数。</span><span class="sxs-lookup"><span data-stu-id="d541d-109">\[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="d541d-110">备注</span><span class="sxs-lookup"><span data-stu-id="d541d-110">Remarks</span></span>

<span data-ttu-id="d541d-111">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) 不会对内联方法进行任何跟踪。</span><span class="sxs-lookup"><span data-stu-id="d541d-111">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="d541d-112">探查器应阻止内联或跟踪内联，并 `RequestReJIT` 为所有 inliners 调用以确保内联方法的每个实例都已 ReJITted。</span><span class="sxs-lookup"><span data-stu-id="d541d-112">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="d541d-113">这会在附加上出现 ReJIT 问题，因为探查器不会监视内联。</span><span class="sxs-lookup"><span data-stu-id="d541d-113">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="d541d-114">可以调用此方法来保证完整的 inliners 集也会 ReJITted。</span><span class="sxs-lookup"><span data-stu-id="d541d-114">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>

## <a name="requirements"></a><span data-ttu-id="d541d-115">要求</span><span class="sxs-lookup"><span data-stu-id="d541d-115">Requirements</span></span>

<span data-ttu-id="d541d-116">**平台：** 请参阅 [支持 .Net Core 的操作系统](../../../core/install/windows.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="d541d-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="d541d-117">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d541d-117">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="d541d-118">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d541d-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="d541d-119">**.Net 版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d541d-119">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d541d-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="d541d-120">See also</span></span>

- [<span data-ttu-id="d541d-121">ICorProfilerInfo10 接口</span><span class="sxs-lookup"><span data-stu-id="d541d-121">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
