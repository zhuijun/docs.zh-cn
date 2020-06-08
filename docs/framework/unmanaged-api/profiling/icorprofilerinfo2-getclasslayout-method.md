---
title: ICorProfilerInfo2::GetClassLayout 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type:
- apiref
ms.openlocfilehash: ac35b18ce8c45c95bb2fb8e820423470ca1b75bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497148"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="923a3-102">ICorProfilerInfo2::GetClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="923a3-102">ICorProfilerInfo2::GetClassLayout Method</span></span>
<span data-ttu-id="923a3-103">获取内存中由指定的类定义的字段的布局信息。</span><span class="sxs-lookup"><span data-stu-id="923a3-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="923a3-104">也就是说，此方法获取类的字段的偏移量。</span><span class="sxs-lookup"><span data-stu-id="923a3-104">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="923a3-105">语法</span><span class="sxs-lookup"><span data-stu-id="923a3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="923a3-106">参数</span><span class="sxs-lookup"><span data-stu-id="923a3-106">Parameters</span></span>  
 `classID`  
 <span data-ttu-id="923a3-107">[in] 将为其检索布局的类的 ID。</span><span class="sxs-lookup"><span data-stu-id="923a3-107">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="923a3-108">[in，out][COR_FIELD_OFFSET](../metadata/cor-field-offset-structure.md)结构的数组，其中每个结构都包含类的字段的标记和偏移量。</span><span class="sxs-lookup"><span data-stu-id="923a3-108">[in, out] An array of [COR_FIELD_OFFSET](../metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="923a3-109">[in] `rFieldOffset` 数组的大小。</span><span class="sxs-lookup"><span data-stu-id="923a3-109">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="923a3-110">[out] 指向可用元素总数的指针。</span><span class="sxs-lookup"><span data-stu-id="923a3-110">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="923a3-111">如果 `cFieldOffset` 为 0，则此值指示所需元素的数目。</span><span class="sxs-lookup"><span data-stu-id="923a3-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="923a3-112">[out] 指向包含类的大小（以字节为单位）的位置的指针。</span><span class="sxs-lookup"><span data-stu-id="923a3-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="923a3-113">注解</span><span class="sxs-lookup"><span data-stu-id="923a3-113">Remarks</span></span>  
 <span data-ttu-id="923a3-114">`GetClassLayout` 方法仅返回由类自身定义的字段。</span><span class="sxs-lookup"><span data-stu-id="923a3-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="923a3-115">如果类的父类也定义了字段，探查器必须对父类调用 `GetClassLayout` 以获取这些字段。</span><span class="sxs-lookup"><span data-stu-id="923a3-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="923a3-116">如果你通过字符串类使用 `GetClassLayout`，则该方法将失败，错误代码为 E_INVALIDARG。</span><span class="sxs-lookup"><span data-stu-id="923a3-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="923a3-117">使用[ICorProfilerInfo2：： GetStringLayout](icorprofilerinfo2-getstringlayout-method.md)获取有关字符串布局的信息。</span><span class="sxs-lookup"><span data-stu-id="923a3-117">Use [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="923a3-118">当使用数组类来调用 `GetClassLayout` 时，它也将失败。</span><span class="sxs-lookup"><span data-stu-id="923a3-118">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="923a3-119">返回 `GetClassLayout` 后，必须验证 `rFieldOffset` 缓冲区是否具有用于包含所有可用 `COR_FIELD_OFFSET` 结构的足够空间。</span><span class="sxs-lookup"><span data-stu-id="923a3-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="923a3-120">若要执行此操作，请将 `pcFieldOffset` 指向的值与 `COR_FIELD_OFFSET` 结构的大小除以 `rFieldOffset` 大小所得的值进行比较。</span><span class="sxs-lookup"><span data-stu-id="923a3-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="923a3-121">如果 `rFieldOffset` 不够大，则分配更大的 `rFieldOffset` 缓冲区，用新的、更大的大小来更新 `cFieldOffset`并再次调用 `GetClassLayout`。</span><span class="sxs-lookup"><span data-stu-id="923a3-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="923a3-122">或者，可以先用长度为零的 `rFieldOffset` 缓冲区调用 `GetClassLayout` 以获取正确的缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="923a3-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="923a3-123">然后，可将缓冲区大小设置为 `pcFieldOffset` 中返回的值，并再次调用 `GetClassLayout`。</span><span class="sxs-lookup"><span data-stu-id="923a3-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="923a3-124">要求</span><span class="sxs-lookup"><span data-stu-id="923a3-124">Requirements</span></span>  
 <span data-ttu-id="923a3-125">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="923a3-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="923a3-126">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="923a3-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="923a3-127">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="923a3-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="923a3-128">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="923a3-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="923a3-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="923a3-129">See also</span></span>

- [<span data-ttu-id="923a3-130">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="923a3-130">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="923a3-131">ICorProfilerInfo2 接口</span><span class="sxs-lookup"><span data-stu-id="923a3-131">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="923a3-132">分析接口</span><span class="sxs-lookup"><span data-stu-id="923a3-132">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="923a3-133">分析</span><span class="sxs-lookup"><span data-stu-id="923a3-133">Profiling</span></span>](index.md)
