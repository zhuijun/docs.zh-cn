---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 6822757608429ca5f4ef9520ab7574d440b67b26
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495251"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a><span data-ttu-id="9828c-102">ICorProfilerInfo8：： GetFunctionFromIP3 方法</span><span class="sxs-lookup"><span data-stu-id="9828c-102">ICorProfilerInfo8::GetFunctionFromIP3 Method</span></span>

<span data-ttu-id="9828c-103">将托管代码指令指针映射到 FunctionID。</span><span class="sxs-lookup"><span data-stu-id="9828c-103">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="9828c-104">此方法适用于动态和非动态方法。</span><span class="sxs-lookup"><span data-stu-id="9828c-104">This method works for both dynamic and non-dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="9828c-105">语法</span><span class="sxs-lookup"><span data-stu-id="9828c-105">Syntax</span></span>

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

## <a name="parameters"></a><span data-ttu-id="9828c-106">参数</span><span class="sxs-lookup"><span data-stu-id="9828c-106">Parameters</span></span>

- `ip`

  <span data-ttu-id="9828c-107">\[in] 托管代码中的指令指针。</span><span class="sxs-lookup"><span data-stu-id="9828c-107">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="9828c-108">\[out] 函数 ID。</span><span class="sxs-lookup"><span data-stu-id="9828c-108">\[out] The function ID.</span></span>

- `pReJitId`

  <span data-ttu-id="9828c-109">\[out] 函数的 JIT 重新编译版本的标识。</span><span class="sxs-lookup"><span data-stu-id="9828c-109">\[out] The identity of the JIT-recompiled version of the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="9828c-110">注解</span><span class="sxs-lookup"><span data-stu-id="9828c-110">Remarks</span></span>

<span data-ttu-id="9828c-111">此方法适用于动态和非动态方法。</span><span class="sxs-lookup"><span data-stu-id="9828c-111">This method works for both dynamic and non-dynamic methods.</span></span> <span data-ttu-id="9828c-112">它是[GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md)的超集，只适用于具有元数据的函数。</span><span class="sxs-lookup"><span data-stu-id="9828c-112">It is a superset of [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), which only works for functions with metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="9828c-113">要求</span><span class="sxs-lookup"><span data-stu-id="9828c-113">Requirements</span></span>

<span data-ttu-id="9828c-114">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9828c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="9828c-115">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9828c-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="9828c-116">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9828c-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="9828c-117">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9828c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9828c-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9828c-118">See also</span></span>

- [<span data-ttu-id="9828c-119">ICorProfilerInfo8 接口</span><span class="sxs-lookup"><span data-stu-id="9828c-119">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
