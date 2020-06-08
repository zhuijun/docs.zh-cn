---
title: ICorProfilerCallback2::RootReferences2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
ms.openlocfilehash: 2ce58113f40c8eb67a89b6ab6c9bb8f755975bd5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499748"
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="3b45e-102">ICorProfilerCallback2::RootReferences2 方法</span><span class="sxs-lookup"><span data-stu-id="3b45e-102">ICorProfilerCallback2::RootReferences2 Method</span></span>
<span data-ttu-id="3b45e-103">发生垃圾回收后，通知探查器有关根引用的信息。</span><span class="sxs-lookup"><span data-stu-id="3b45e-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="3b45e-104">此方法是[ICorProfilerCallback：： RootReferences](icorprofilercallback-rootreferences-method.md)方法的扩展。</span><span class="sxs-lookup"><span data-stu-id="3b45e-104">This method is an extension of the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b45e-105">语法</span><span class="sxs-lookup"><span data-stu-id="3b45e-105">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b45e-106">参数</span><span class="sxs-lookup"><span data-stu-id="3b45e-106">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="3b45e-107">中`rootRefIds`、 `rootKinds` 、 `rootFlags` 和数组中的元素数 `rootIds` 。</span><span class="sxs-lookup"><span data-stu-id="3b45e-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="3b45e-108">中对象 Id 的数组，其中每个对象都引用堆栈上的静态对象或对象。</span><span class="sxs-lookup"><span data-stu-id="3b45e-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="3b45e-109">数组中的元素 `rootKinds` 提供用于对数组中的相应元素进行分类的信息 `rootRefIds` 。</span><span class="sxs-lookup"><span data-stu-id="3b45e-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="3b45e-110">中一个[COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md)值的数组，这些值指示垃圾回收根的类型。</span><span class="sxs-lookup"><span data-stu-id="3b45e-110">[in] An array of [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="3b45e-111">中描述垃圾回收根属性的[COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md)值的数组。</span><span class="sxs-lookup"><span data-stu-id="3b45e-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="3b45e-112">中一个 UINT_PTR 值的数组，这些值指向一个整数，该整数包含有关垃圾回收根的其他信息，具体取决于 `rootKinds` 参数的值。</span><span class="sxs-lookup"><span data-stu-id="3b45e-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="3b45e-113">如果根的类型为堆栈，则根 ID 适用于包含变量的函数。</span><span class="sxs-lookup"><span data-stu-id="3b45e-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="3b45e-114">如果该根 ID 为0，则该函数是 CLR 内部的一个未命名函数。</span><span class="sxs-lookup"><span data-stu-id="3b45e-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="3b45e-115">如果根的类型为句柄，则根 ID 用于垃圾回收句柄。</span><span class="sxs-lookup"><span data-stu-id="3b45e-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="3b45e-116">对于其他根类型，该 ID 是不透明值，应忽略它。</span><span class="sxs-lookup"><span data-stu-id="3b45e-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b45e-117">注解</span><span class="sxs-lookup"><span data-stu-id="3b45e-117">Remarks</span></span>  
 <span data-ttu-id="3b45e-118">`rootRefIds`、 `rootKinds` 、 `rootFlags` 和 `rootIds` 数组是并行数组。</span><span class="sxs-lookup"><span data-stu-id="3b45e-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="3b45e-119">也就是说，、 `rootRefIds[i]` 、 `rootKinds[i]` `rootFlags[i]` 和 `rootIds[i]` 都涉及到相同的根。</span><span class="sxs-lookup"><span data-stu-id="3b45e-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="3b45e-120">同时 `RootReferences` `RootReferences2` 调用和来通知探查器。</span><span class="sxs-lookup"><span data-stu-id="3b45e-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="3b45e-121">探查器通常会实现一种方法或另一种方法，但不能同时实现两者，因为传入的信息 `RootReferences2` 是传入的的超集 `RootReferences` 。</span><span class="sxs-lookup"><span data-stu-id="3b45e-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="3b45e-122">中的项可以为 `rootRefIds` 零，这意味着对应的根引用为 null，并且不引用托管堆上的对象。</span><span class="sxs-lookup"><span data-stu-id="3b45e-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="3b45e-123">返回的对象 Id 在 `RootReferences2` 回调过程中无效，因为垃圾回收可能正处于将对象从旧地址移到新地址的过程中。</span><span class="sxs-lookup"><span data-stu-id="3b45e-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="3b45e-124">因此，探查器不应在 `RootReferences2` 调用期间尝试检查对象。</span><span class="sxs-lookup"><span data-stu-id="3b45e-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="3b45e-125">调用[ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)时，所有对象已移动到它们的新位置，并且可以安全检查。</span><span class="sxs-lookup"><span data-stu-id="3b45e-125">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b45e-126">要求</span><span class="sxs-lookup"><span data-stu-id="3b45e-126">Requirements</span></span>  
 <span data-ttu-id="3b45e-127">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b45e-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b45e-128">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3b45e-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3b45e-129">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b45e-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b45e-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b45e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b45e-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3b45e-131">See also</span></span>

- [<span data-ttu-id="3b45e-132">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="3b45e-132">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3b45e-133">ICorProfilerCallback2 接口</span><span class="sxs-lookup"><span data-stu-id="3b45e-133">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
