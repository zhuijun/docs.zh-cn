---
title: ICorProfilerInfo2::GetObjectGeneration 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetObjectGeneration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type:
- apiref
ms.openlocfilehash: 1263202c1fe524c924a88b9356e5ab9116cea553
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502855"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="21e2a-102">ICorProfilerInfo2::GetObjectGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="21e2a-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>
<span data-ttu-id="21e2a-103">获取包含指定对象的堆段。</span><span class="sxs-lookup"><span data-stu-id="21e2a-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21e2a-104">语法</span><span class="sxs-lookup"><span data-stu-id="21e2a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21e2a-105">参数</span><span class="sxs-lookup"><span data-stu-id="21e2a-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="21e2a-106">中对象的 ID。</span><span class="sxs-lookup"><span data-stu-id="21e2a-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="21e2a-107">弄指向[COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md)结构的指针，该结构描述要进行垃圾回收的代中的内存范围（即块）。</span><span class="sxs-lookup"><span data-stu-id="21e2a-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="21e2a-108">此范围包含指定的对象。</span><span class="sxs-lookup"><span data-stu-id="21e2a-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21e2a-109">注解</span><span class="sxs-lookup"><span data-stu-id="21e2a-109">Remarks</span></span>  
 <span data-ttu-id="21e2a-110">`GetObjectGeneration`如果垃圾回收未进行，则可以从任何探查器回调调用方法。</span><span class="sxs-lookup"><span data-stu-id="21e2a-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="21e2a-111">也就是说，它可从任何回调调用， [ICorProfilerCallback2：： GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md)和[ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)之间发生的回调除外。</span><span class="sxs-lookup"><span data-stu-id="21e2a-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21e2a-112">要求</span><span class="sxs-lookup"><span data-stu-id="21e2a-112">Requirements</span></span>  
 <span data-ttu-id="21e2a-113">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="21e2a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21e2a-114">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="21e2a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21e2a-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21e2a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21e2a-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21e2a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e2a-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="21e2a-117">See also</span></span>

- [<span data-ttu-id="21e2a-118">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="21e2a-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="21e2a-119">ICorProfilerInfo2 接口</span><span class="sxs-lookup"><span data-stu-id="21e2a-119">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
