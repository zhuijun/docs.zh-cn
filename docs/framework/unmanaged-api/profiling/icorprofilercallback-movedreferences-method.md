---
title: ICorProfilerCallback::MovedReferences 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.MovedReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::MovedReferences
helpviewer_keywords:
- MovedReferences method [.NET Framework profiling]
- ICorProfilerCallback::MovedReferences method [.NET Framework profiling]
ms.assetid: 996c71ae-0676-4616-a085-84ebf507649d
topic_type:
- apiref
ms.openlocfilehash: 1214182c95f7d0304ec920a2ea7dae91b1f4a790
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503326"
---
# <a name="icorprofilercallbackmovedreferences-method"></a><span data-ttu-id="5e0dc-102">ICorProfilerCallback::MovedReferences 方法</span><span class="sxs-lookup"><span data-stu-id="5e0dc-102">ICorProfilerCallback::MovedReferences Method</span></span>
<span data-ttu-id="5e0dc-103">调用以报告堆中对象的新布局（压缩垃圾回收产生的结果）。</span><span class="sxs-lookup"><span data-stu-id="5e0dc-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e0dc-104">语法</span><span class="sxs-lookup"><span data-stu-id="5e0dc-104">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e0dc-105">参数</span><span class="sxs-lookup"><span data-stu-id="5e0dc-105">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="5e0dc-106">[in] 因压缩垃圾回收而被移动的连续对象的块数。</span><span class="sxs-lookup"><span data-stu-id="5e0dc-106">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="5e0dc-107">即 `cMovedObjectIDRanges` 的值是 `oldObjectIDRangeStart`、`newObjectIDRangeStart` 和 `cObjectIDRangeLength` 数组的总大小。</span><span class="sxs-lookup"><span data-stu-id="5e0dc-107">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="5e0dc-108">`MovedReferences` 的接下来的三个参数是并行数组。</span><span class="sxs-lookup"><span data-stu-id="5e0dc-108">The next three arguments of `MovedReferences` are parallel arrays.</span></span> <span data-ttu-id="5e0dc-109">换言之，`oldObjectIDRangeStart[i]`、`newObjectIDRangeStart[i]` 和 `cObjectIDRangeLength[i]` 都涉及单个连续对象单块。</span><span class="sxs-lookup"><span data-stu-id="5e0dc-109">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="5e0dc-110">[in] `ObjectID` 值的数组，其中每个值均为内存中连续活动对象块的旧（垃圾回收前）起始地址。</span><span class="sxs-lookup"><span data-stu-id="5e0dc-110">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="5e0dc-111">[in] `ObjectID` 值的数组，其中每个值均为内存中连续活动对象块的新（垃圾回收后）起始地址。</span><span class="sxs-lookup"><span data-stu-id="5e0dc-111">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="5e0dc-112">[in] 整数数组，其中每个整数均为内存中的连续对象块的大小。</span><span class="sxs-lookup"><span data-stu-id="5e0dc-112">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="5e0dc-113">`oldObjectIDRangeStart` 和 `newObjectIDRangeStart` 数组中引用的每个块均有指定的大小。</span><span class="sxs-lookup"><span data-stu-id="5e0dc-113">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e0dc-114">注解</span><span class="sxs-lookup"><span data-stu-id="5e0dc-114">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5e0dc-115">此方法将 64 位平台上大于 4 GB 的对象的大小报告为 `MAX_ULONG`。</span><span class="sxs-lookup"><span data-stu-id="5e0dc-115">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="5e0dc-116">若要获取大于 4 GB 的对象的大小，请改用[ICorProfilerCallback4：： MovedReferences2](icorprofilercallback4-movedreferences2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="5e0dc-116">To get the size of objects that are larger than 4 GB, use the [ICorProfilerCallback4::MovedReferences2](icorprofilercallback4-movedreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="5e0dc-117">压缩垃圾回收器将收回由不活动对象占用的内存，但不会压缩释放的空间。</span><span class="sxs-lookup"><span data-stu-id="5e0dc-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="5e0dc-118">因此，可能在堆中移动活动对象，并且由以前的通知分发的 `ObjectID` 值也可能更改。</span><span class="sxs-lookup"><span data-stu-id="5e0dc-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="5e0dc-119">假定现有 `ObjectID` 值 (`oldObjectID`) 在以下范围内：</span><span class="sxs-lookup"><span data-stu-id="5e0dc-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="5e0dc-120">在这种情况下，从范围起始到对象起始位置的偏移量如下所示：</span><span class="sxs-lookup"><span data-stu-id="5e0dc-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="5e0dc-121">对于以下范围内的任何 `i` 值：</span><span class="sxs-lookup"><span data-stu-id="5e0dc-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="5e0dc-122">0 <=`i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="5e0dc-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="5e0dc-123">可以按以下方式计算出新的 `ObjectID`：</span><span class="sxs-lookup"><span data-stu-id="5e0dc-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="5e0dc-124">`newObjectID` = `newObjectIDRangeStart[i]`+ （ `oldObjectID` – `oldObjectIDRangeStart[i]` ）</span><span class="sxs-lookup"><span data-stu-id="5e0dc-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="5e0dc-125">`MovedReferences` 传递的 `ObjectID` 值在回调过程中均是无效的，因为垃圾回收可能正处于将对象从旧位置移到新位置的阶段。</span><span class="sxs-lookup"><span data-stu-id="5e0dc-125">None of the `ObjectID` values passed by `MovedReferences` are valid during the callback itself, because the garbage collection might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="5e0dc-126">因此，探查器不应在 `MovedReferences` 调用期间尝试检查对象。</span><span class="sxs-lookup"><span data-stu-id="5e0dc-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences` call.</span></span> <span data-ttu-id="5e0dc-127">[ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)回调指示所有对象已移动到其新位置，并可执行检查。</span><span class="sxs-lookup"><span data-stu-id="5e0dc-127">A [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e0dc-128">要求</span><span class="sxs-lookup"><span data-stu-id="5e0dc-128">Requirements</span></span>  
 <span data-ttu-id="5e0dc-129">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e0dc-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e0dc-130">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5e0dc-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5e0dc-131">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e0dc-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e0dc-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e0dc-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e0dc-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5e0dc-133">See also</span></span>

- [<span data-ttu-id="5e0dc-134">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="5e0dc-134">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="5e0dc-135">MovedReferences2 方法</span><span class="sxs-lookup"><span data-stu-id="5e0dc-135">MovedReferences2 Method</span></span>](icorprofilercallback4-movedreferences2-method.md)
- [<span data-ttu-id="5e0dc-136">分析接口</span><span class="sxs-lookup"><span data-stu-id="5e0dc-136">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="5e0dc-137">分析</span><span class="sxs-lookup"><span data-stu-id="5e0dc-137">Profiling</span></span>](index.md)
