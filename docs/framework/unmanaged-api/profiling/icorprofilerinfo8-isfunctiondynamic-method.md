---
title: ICorProfilerInfo8::IsFunctionDynamic
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.IsFunctionDynamic
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: c88279d361ea78a2e910c4621e92c500902d9124
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495120"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="4922e-102">ICorProfilerInfo8：： IsFunctionDynamic 方法</span><span class="sxs-lookup"><span data-stu-id="4922e-102">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>

<span data-ttu-id="4922e-103">确定函数是否没有关联的元数据。</span><span class="sxs-lookup"><span data-stu-id="4922e-103">Determines if a function does not have associated metadata.</span></span>

## <a name="syntax"></a><span data-ttu-id="4922e-104">语法</span><span class="sxs-lookup"><span data-stu-id="4922e-104">Syntax</span></span>

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a><span data-ttu-id="4922e-105">参数</span><span class="sxs-lookup"><span data-stu-id="4922e-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="4922e-106">\[in] `FunctionID` 标识相关函数的。</span><span class="sxs-lookup"><span data-stu-id="4922e-106">\[in]  The `FunctionID` that identifies the function in question.</span></span>

- `isDynamic`

  <span data-ttu-id="4922e-107">\[out] 指向的指针 `BOOL` ，它将包含一个值，该值指示该函数是否没有元数据。</span><span class="sxs-lookup"><span data-stu-id="4922e-107">\[out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="4922e-108">注解</span><span class="sxs-lookup"><span data-stu-id="4922e-108">Remarks</span></span>

<span data-ttu-id="4922e-109">如果函数没有元数据，则将其视为动态函数。</span><span class="sxs-lookup"><span data-stu-id="4922e-109">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="4922e-110">某些方法（如 IL 存根或 LCG 方法）没有关联的元数据，可以使用 IMetaDataImport Api 来检索这些元数据。</span><span class="sxs-lookup"><span data-stu-id="4922e-110">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="4922e-111">探查器可以通过指令指针或通过侦听 ICorProfilerCallback 来完成这些方法[：:D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)。</span><span class="sxs-lookup"><span data-stu-id="4922e-111">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="4922e-112">要求</span><span class="sxs-lookup"><span data-stu-id="4922e-112">Requirements</span></span>

<span data-ttu-id="4922e-113">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4922e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="4922e-114">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4922e-114">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="4922e-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4922e-115">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="4922e-116">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4922e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4922e-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4922e-117">See also</span></span>

- [<span data-ttu-id="4922e-118">ICorProfilerInfo8 接口</span><span class="sxs-lookup"><span data-stu-id="4922e-118">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
