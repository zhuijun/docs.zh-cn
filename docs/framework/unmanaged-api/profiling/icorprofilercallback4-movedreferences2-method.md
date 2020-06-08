---
title: ICorProfilerCallback4::MovedReferences2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.MovedReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type:
- apiref
ms.openlocfilehash: 79e54cde8757bbe690f9b7c4344a2a3cb19cf627
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499377"
---
# <a name="icorprofilercallback4movedreferences2-method"></a><span data-ttu-id="fa9b1-102">ICorProfilerCallback4::MovedReferences2 方法</span><span class="sxs-lookup"><span data-stu-id="fa9b1-102">ICorProfilerCallback4::MovedReferences2 Method</span></span>
<span data-ttu-id="fa9b1-103">调用以报告堆中对象的新布局（压缩垃圾回收产生的结果）。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span> <span data-ttu-id="fa9b1-104">如果探查器实现了[ICorProfilerCallback4](icorprofilercallback4-interface.md)接口，则调用此方法。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="fa9b1-105">此回调可替换[ICorProfilerCallback：： MovedReferences](icorprofilercallback-movedreferences-method.md)方法，因为它可以报告长度超过在 ULONG 中可表达的内容的更大范围的对象。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-105">This callback replaces the [ICorProfilerCallback::MovedReferences](icorprofilercallback-movedreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa9b1-106">语法</span><span class="sxs-lookup"><span data-stu-id="fa9b1-106">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa9b1-107">参数</span><span class="sxs-lookup"><span data-stu-id="fa9b1-107">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="fa9b1-108">[in] 因压缩垃圾回收而被移动的连续对象的块数。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-108">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="fa9b1-109">即 `cMovedObjectIDRanges` 的值是 `oldObjectIDRangeStart`、`newObjectIDRangeStart` 和 `cObjectIDRangeLength` 数组的总大小。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-109">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="fa9b1-110">`MovedReferences2` 的接下来的三个参数是并行数组。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-110">The next three arguments of `MovedReferences2` are parallel arrays.</span></span> <span data-ttu-id="fa9b1-111">换言之，`oldObjectIDRangeStart[i]`、`newObjectIDRangeStart[i]` 和 `cObjectIDRangeLength[i]` 都涉及单个连续对象单块。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-111">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="fa9b1-112">[in] `ObjectID` 值的数组，其中每个值均为内存中连续活动对象块的旧（垃圾回收前）起始地址。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-112">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="fa9b1-113">[in] `ObjectID` 值的数组，其中每个值均为内存中连续活动对象块的新（垃圾回收后）起始地址。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-113">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="fa9b1-114">[in] 整数数组，其中每个整数均为内存中的连续对象块的大小。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-114">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="fa9b1-115">`oldObjectIDRangeStart` 和 `newObjectIDRangeStart` 数组中引用的每个块均有指定的大小。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-115">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa9b1-116">注解</span><span class="sxs-lookup"><span data-stu-id="fa9b1-116">Remarks</span></span>  
 <span data-ttu-id="fa9b1-117">压缩垃圾回收器将收回由不活动对象占用的内存，但不会压缩释放的空间。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="fa9b1-118">因此，可能在堆中移动活动对象，并且由以前的通知分发的 `ObjectID` 值也可能更改。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="fa9b1-119">假定现有 `ObjectID` 值 (`oldObjectID`) 在以下范围内：</span><span class="sxs-lookup"><span data-stu-id="fa9b1-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="fa9b1-120">在这种情况下，从范围起始到对象起始位置的偏移量如下所示：</span><span class="sxs-lookup"><span data-stu-id="fa9b1-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="fa9b1-121">对于以下范围内的任何 `i` 值：</span><span class="sxs-lookup"><span data-stu-id="fa9b1-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="fa9b1-122">0 <=`i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="fa9b1-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="fa9b1-123">可以按以下方式计算出新的 `ObjectID`：</span><span class="sxs-lookup"><span data-stu-id="fa9b1-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="fa9b1-124">`newObjectID` = `newObjectIDRangeStart[i]`+ （ `oldObjectID` – `oldObjectIDRangeStart[i]` ）</span><span class="sxs-lookup"><span data-stu-id="fa9b1-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="fa9b1-125">在该回调本身中，由 `MovedReferences2` 传递的任何 `ObjectID` 值都无效，因为垃圾回收器可能正在将对象从旧位置移至新位置。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-125">None of the `ObjectID` values passed by `MovedReferences2` are valid during the callback itself, because the garbage collector might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="fa9b1-126">因此，探查器不应在 `MovedReferences2` 调用期间尝试检查对象。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences2` call.</span></span> <span data-ttu-id="fa9b1-127">[ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)回调指示所有对象已移动到其新位置，并可执行检查。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-127">A [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
 <span data-ttu-id="fa9b1-128">如果探查器同时实现[ICorProfilerCallback](icorprofilercallback-interface.md)和[ICorProfilerCallback4](icorprofilercallback4-interface.md)接口，则在 `MovedReferences2` [ICorProfilerCallback：： MovedReferences](icorprofilercallback-movedreferences-method.md)方法之前调用方法，但前提是该 `MovedReferences2` 方法成功返回。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-128">If the profiler implements both the [ICorProfilerCallback](icorprofilercallback-interface.md) and the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interfaces, the `MovedReferences2` method is called before the [ICorProfilerCallback::MovedReferences](icorprofilercallback-movedreferences-method.md) method, but only if the `MovedReferences2` method returns successfully.</span></span> <span data-ttu-id="fa9b1-129">探查器可以返回一个 HRESULT，指示由 `MovedReferences2` 方法引发的故障，以避免调用第二种方法。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-129">Profilers can return an HRESULT that indicates failure from the `MovedReferences2` method, to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa9b1-130">要求</span><span class="sxs-lookup"><span data-stu-id="fa9b1-130">Requirements</span></span>  
 <span data-ttu-id="fa9b1-131">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fa9b1-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa9b1-132">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fa9b1-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fa9b1-133">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa9b1-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa9b1-134">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa9b1-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa9b1-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa9b1-135">See also</span></span>

- [<span data-ttu-id="fa9b1-136">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="fa9b1-136">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="fa9b1-137">MovedReferences 方法</span><span class="sxs-lookup"><span data-stu-id="fa9b1-137">MovedReferences Method</span></span>](icorprofilercallback-movedreferences-method.md)
- [<span data-ttu-id="fa9b1-138">ICorProfilerCallback4 接口</span><span class="sxs-lookup"><span data-stu-id="fa9b1-138">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="fa9b1-139">分析接口</span><span class="sxs-lookup"><span data-stu-id="fa9b1-139">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="fa9b1-140">分析</span><span class="sxs-lookup"><span data-stu-id="fa9b1-140">Profiling</span></span>](index.md)
