---
title: ICorProfilerCallback5::ConditionalWeakTableElementReferences 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5.ConditionalWeakTableReferences
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ConditionalWeakTableElementReferences
helpviewer_keywords:
- ConditionalWeakTableElementReferences method, ICorProfilerCallback5 interface [.NET Framework profiling]
- ICorProfilerCallback5::ConditionalWeakTableElementReferences method [.NET Framework profiling]
ms.assetid: 532c7a02-a9de-4cea-bb2b-7f470da594de
topic_type:
- apiref
ms.openlocfilehash: 17fbc99b30921f795c1f7ff882ec73432aade8c6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499241"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a><span data-ttu-id="8955b-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences 方法</span><span class="sxs-lookup"><span data-stu-id="8955b-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences Method</span></span>

<span data-ttu-id="8955b-103">标识这些根通过直接成员字段引用和 `ConditionalWeakTable` 依赖关系引用的对象的传递闭包。</span><span class="sxs-lookup"><span data-stu-id="8955b-103">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>

## <a name="syntax"></a><span data-ttu-id="8955b-104">语法</span><span class="sxs-lookup"><span data-stu-id="8955b-104">Syntax</span></span>

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a><span data-ttu-id="8955b-105">参数</span><span class="sxs-lookup"><span data-stu-id="8955b-105">Parameters</span></span>

`cRootRefs`\
<span data-ttu-id="8955b-106">[in] `keyRefIds`、`valueRefIds` 和 `rootIds` 数组中的元素数。</span><span class="sxs-lookup"><span data-stu-id="8955b-106">[in] The number of elements in the `keyRefIds`, `valueRefIds`, and `rootIds` arrays.</span></span>

`keyRefIds`\
<span data-ttu-id="8955b-107">[in] 一个包含对象 ID 的数组，其中每个对象 ID 都包含相关句柄对中主要元素的 `ObjectID`。</span><span class="sxs-lookup"><span data-stu-id="8955b-107">[in] An array of object IDs, each of which contains the `ObjectID` for the primary element in the dependent handle pair.</span></span>

`valueRefIds`\
<span data-ttu-id="8955b-108">[in] 一个包含对象 ID 的数组，其中每个对象 ID 都包含相关句柄对中次要元素的 `ObjectID`。</span><span class="sxs-lookup"><span data-stu-id="8955b-108">[in] An array of object IDs, each of which contains the `ObjectID` for the secondary element in the dependent handle pair.</span></span> <span data-ttu-id="8955b-109">（ `keyRefIds[i]` 保持 `valueRefIds[i]` 活动状态。）</span><span class="sxs-lookup"><span data-stu-id="8955b-109">(`keyRefIds[i]` keeps `valueRefIds[i]` alive.)</span></span>

`rootIds`\
<span data-ttu-id="8955b-110">[in] 一个包含 `GCHandleID` 值的数组，这些值指向包含有关垃圾回收根的附加信息的整数。</span><span class="sxs-lookup"><span data-stu-id="8955b-110">[in] An array of `GCHandleID` values that point to an integer that contains additional information about the garbage collection root.</span></span>

<span data-ttu-id="8955b-111">在该回调本身中，由 `ObjectID` 方法返回的任何 `ConditionalWeakTableElementReferences` 值都无效，因为垃圾回收器可能正处于将对象从旧位置移到新位置的过程中。</span><span class="sxs-lookup"><span data-stu-id="8955b-111">None of the `ObjectID` values returned by the `ConditionalWeakTableElementReferences` method are valid during the callback itself, because the garbage collector may be in the process of moving objects from old to new locations.</span></span> <span data-ttu-id="8955b-112">因此，探查器不应在 `ConditionalWeakTableElementReferences` 调用期间尝试检查对象。</span><span class="sxs-lookup"><span data-stu-id="8955b-112">Therefore, profilers should not attempt to inspect objects during a `ConditionalWeakTableElementReferences` call.</span></span> <span data-ttu-id="8955b-113">在 `GarbageCollectionFinished` 时，已经将所有对象都移动到其新位置，并且检查可能已完成。</span><span class="sxs-lookup"><span data-stu-id="8955b-113">At `GarbageCollectionFinished`, all objects have been moved to their new locations, and inspection may be done.</span></span>

## <a name="example"></a><span data-ttu-id="8955b-114">示例</span><span class="sxs-lookup"><span data-stu-id="8955b-114">Example</span></span>

<span data-ttu-id="8955b-115">下面的代码示例演示如何实现[ICorProfilerCallback5](icorprofilercallback5-interface.md)并使用此方法。</span><span class="sxs-lookup"><span data-stu-id="8955b-115">The following code example demonstrates how to implement [ICorProfilerCallback5](icorprofilercallback5-interface.md) and use this method.</span></span>

```cpp
HRESULT Callback5Impl::ConditionalWeakTableElementReferences(
    ULONG      cRootRefs,
    ObjectID   keyRefIds[],
    ObjectID   valueRefIds[],
    GCHandleID rootIds[])
{
    printf("Callback5Impl::ConditionalWeakTableElementReferences called\n");
    for (unsigned int i = 0; i < cRootRefs; ++i)
    {
        // Save dependency to XML for later retrieval
        PersistDependencyToXml(rootIds[i], keyRefIds[i], valueRefIds[i]);
        // or store dependency to an internal map
        m_cwt_deps->add_dep(rootIds[i], keyRefIds[i], valueRefIds[i]);
        // or add arc to object graph
        m_obj_graph->add_arc(keyRefIds[i], valueRefIds[i], rootIds[i]);
    }
    return S_OK;
}
```

## <a name="remarks"></a><span data-ttu-id="8955b-116">注解</span><span class="sxs-lookup"><span data-stu-id="8955b-116">Remarks</span></span>

<span data-ttu-id="8955b-117">.NET Framework 4.5 或更高版本的探查器将实现[ICorProfilerCallback5](icorprofilercallback5-interface.md)接口并记录由方法指定的依赖项 `ConditionalWeakTableElementReferences` 。</span><span class="sxs-lookup"><span data-stu-id="8955b-117">A profiler for the .NET Framework 4.5 or later versions implements the [ICorProfilerCallback5](icorprofilercallback5-interface.md) interface and records the dependencies specified by the `ConditionalWeakTableElementReferences` method.</span></span> <span data-ttu-id="8955b-118">`ICorProfilerCallback5`提供条目所表示的活动对象之间的依赖关系的完整集合 `ConditionalWeakTable` 。</span><span class="sxs-lookup"><span data-stu-id="8955b-118">`ICorProfilerCallback5` provides the complete set of dependencies among live objects represented by `ConditionalWeakTable` entries.</span></span> <span data-ttu-id="8955b-119">使用[ICorProfilerCallback：： ObjectReferences](icorprofilercallback-objectreferences-method.md)方法指定的这些依赖项和成员字段引用，托管探查器可以生成活动对象的完整对象图。</span><span class="sxs-lookup"><span data-stu-id="8955b-119">These dependencies and the member field references specified by the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) method enable a managed profiler to generate the full object graph of live objects.</span></span>

## <a name="requirements"></a><span data-ttu-id="8955b-120">要求</span><span class="sxs-lookup"><span data-stu-id="8955b-120">Requirements</span></span>

<span data-ttu-id="8955b-121">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8955b-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="8955b-122">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8955b-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="8955b-123">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8955b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8955b-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8955b-124">See also</span></span>

- [<span data-ttu-id="8955b-125">ICorProfilerCallback5 接口</span><span class="sxs-lookup"><span data-stu-id="8955b-125">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)
