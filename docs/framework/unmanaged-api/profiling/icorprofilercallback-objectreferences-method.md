---
title: ICorProfilerCallback::ObjectReferences 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
ms.openlocfilehash: 12a0792e8fafc73b480de6bacc86f98470dfedf7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503284"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="57529-102">ICorProfilerCallback::ObjectReferences 方法</span><span class="sxs-lookup"><span data-stu-id="57529-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="57529-103">通知探查器有关指定的对象正在引用的内存中的对象。</span><span class="sxs-lookup"><span data-stu-id="57529-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57529-104">语法</span><span class="sxs-lookup"><span data-stu-id="57529-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="57529-105">参数</span><span class="sxs-lookup"><span data-stu-id="57529-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="57529-106">中引用对象的对象的 ID。</span><span class="sxs-lookup"><span data-stu-id="57529-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="57529-107">中指定对象是其实例的类的 ID。</span><span class="sxs-lookup"><span data-stu-id="57529-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="57529-108">中指定的对象引用的对象数（即数组中的元素个数 `objectRefIds` ）。</span><span class="sxs-lookup"><span data-stu-id="57529-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="57529-109">中由引用的对象的 Id 数组 `objectId` 。</span><span class="sxs-lookup"><span data-stu-id="57529-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57529-110">注解</span><span class="sxs-lookup"><span data-stu-id="57529-110">Remarks</span></span>  
 <span data-ttu-id="57529-111">`ObjectReferences`完成垃圾回收后，将为堆中剩余的每个对象调用方法。</span><span class="sxs-lookup"><span data-stu-id="57529-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="57529-112">如果探查器从此回调返回错误，则分析服务将停止调用此回调，直到下一次垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="57529-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="57529-113">`ObjectReferences`回调可与[ICorProfilerCallback：： RootReferences](icorprofilercallback-rootreferences-method.md)回调结合使用，以便为运行时创建完整的对象引用关系图。</span><span class="sxs-lookup"><span data-stu-id="57529-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="57529-114">公共语言运行时（CLR）确保每个对象引用只通过方法报告一次 `ObjectReferences` 。</span><span class="sxs-lookup"><span data-stu-id="57529-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="57529-115">返回的对象 Id 在 `ObjectReferences` 回调过程中无效，因为垃圾回收可能是在移动对象的中间。</span><span class="sxs-lookup"><span data-stu-id="57529-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="57529-116">因此，探查器不能尝试在调用过程中检查对象 `ObjectReferences` 。</span><span class="sxs-lookup"><span data-stu-id="57529-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="57529-117">调用[ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)时，垃圾回收已完成，可安全完成检查。</span><span class="sxs-lookup"><span data-stu-id="57529-117">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="57529-118">如果为 null `ClassId` ， `objectId` 则表示具有正在卸载的类型。</span><span class="sxs-lookup"><span data-stu-id="57529-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57529-119">要求</span><span class="sxs-lookup"><span data-stu-id="57529-119">Requirements</span></span>  
 <span data-ttu-id="57529-120">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="57529-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57529-121">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="57529-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="57529-122">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57529-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57529-123">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57529-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57529-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57529-124">See also</span></span>

- [<span data-ttu-id="57529-125">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="57529-125">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
