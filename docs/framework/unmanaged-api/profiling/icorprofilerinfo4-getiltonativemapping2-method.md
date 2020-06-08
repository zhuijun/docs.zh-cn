---
title: ICorProfilerInfo4::GetILToNativeMapping2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetILToNativeMapping2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type:
- apiref
ms.openlocfilehash: 9a6ee58cda5e0b673b3ff1378240f89323e30194
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496031"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a><span data-ttu-id="ff843-102">ICorProfilerInfo4::GetILToNativeMapping2 方法</span><span class="sxs-lookup"><span data-stu-id="ff843-102">ICorProfilerInfo4::GetILToNativeMapping2 Method</span></span>
<span data-ttu-id="ff843-103">针对指定函数的 JIT 重新编译版本中包含的代码，获取 Microsoft 中间语言 (MSIL) 偏移量到本机偏移量的映射。</span><span class="sxs-lookup"><span data-stu-id="ff843-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff843-104">语法</span><span class="sxs-lookup"><span data-stu-id="ff843-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff843-105">参数</span><span class="sxs-lookup"><span data-stu-id="ff843-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ff843-106">[in] 包含代码的函数 ID。</span><span class="sxs-lookup"><span data-stu-id="ff843-106">[in] The ID of the function that contains the code.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="ff843-107">[in] JIT 重新编译的函数的标识。</span><span class="sxs-lookup"><span data-stu-id="ff843-107">[in] The identity of the JIT-recompiled function.</span></span> <span data-ttu-id="ff843-108">.NET Framework 4.5 中的标识必须为零。</span><span class="sxs-lookup"><span data-stu-id="ff843-108">The identity must be zero in the .NET Framework 4.5.</span></span>  
  
 `cMap`  
 <span data-ttu-id="ff843-109">[in] `map` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="ff843-109">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="ff843-110">[out] COR_DEBUG_IL_TO_NATIVE_MAP 结构的可用总数。</span><span class="sxs-lookup"><span data-stu-id="ff843-110">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="ff843-111">[out] `COR_DEBUG_IL_TO_NATIVE_MAP` 结构的数组，其中每个结构均指定偏移量。</span><span class="sxs-lookup"><span data-stu-id="ff843-111">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="ff843-112">`GetILToNativeMapping2` 方法返回后，`map` 将包含部分或全部 `COR_DEBUG_IL_TO_NATIVE_MAP` 结构。</span><span class="sxs-lookup"><span data-stu-id="ff843-112">After the `GetILToNativeMapping2` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff843-113">注解</span><span class="sxs-lookup"><span data-stu-id="ff843-113">Remarks</span></span>  
 <span data-ttu-id="ff843-114">`GetILToNativeMapping2`与[ICorProfilerInfo：： GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md)方法类似，只是它允许探查器在将来的版本中指定重新编译的函数的 ID。</span><span class="sxs-lookup"><span data-stu-id="ff843-114">`GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff843-115">.NET Framework 4.5 中未实现[ICorProfilerFunctionControl：： SetILInstrumentedCodeMap](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)方法，因此，JIT 重新编译的函数不能具有与最初编译的函数不同的 IL 到本机映射。</span><span class="sxs-lookup"><span data-stu-id="ff843-115">The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the .NET Framework 4.5, so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function.</span></span> <span data-ttu-id="ff843-116">因此， `GetILToNativeMapping2` 在 .NET Framework 4.5 中不能使用非零 JIT 重新编译的 ID 调用。</span><span class="sxs-lookup"><span data-stu-id="ff843-116">As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="ff843-117">`GetILToNativeMapping2` 方法返回 `COR_DEBUG_IL_TO_NATIVE_MAP` 结构的数组。</span><span class="sxs-lookup"><span data-stu-id="ff843-117">The `GetILToNativeMapping2` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="ff843-118">为了传达特定范围的本机指令与代码的特殊区域（例如序言）相对应，数组中的条目可以 `ilOffset` 将其字段设置为[CorDebugIlToNativeMappingTypes](../debugging/cordebugiltonativemappingtypes-enumeration.md)枚举的值。</span><span class="sxs-lookup"><span data-stu-id="ff843-118">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="ff843-119">返回 `GetILToNativeMapping2` 后，必须验证 `map` 缓冲区大小是否足以包含所有 `COR_DEBUG_IL_TO_NATIVE_MAP` 结构。</span><span class="sxs-lookup"><span data-stu-id="ff843-119">After `GetILToNativeMapping2` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="ff843-120">为此，请将 `cMap` 的值和 `pcMap` 参数的值进行比较。</span><span class="sxs-lookup"><span data-stu-id="ff843-120">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="ff843-121">如果 `pcMap` 值乘以 `COR_DEBUG_IL_TO_NATIVE_MAP` 结构的大小所得的值大于 `cMap`，请分配更大的 `map` 缓冲区、将 `cMap` 更新为新的更大大小，并再次调用 `GetILToNativeMapping2`。</span><span class="sxs-lookup"><span data-stu-id="ff843-121">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping2` again.</span></span>  
  
 <span data-ttu-id="ff843-122">或者，可以先用长度为零的 `map` 缓冲区调用 `GetILToNativeMapping2` 以获取正确的缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="ff843-122">Alternatively, you can first call `GetILToNativeMapping2` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="ff843-123">然后，可将缓冲区大小设置为 `pcMap` 中返回的值，并再次调用 `GetILToNativeMapping2`。</span><span class="sxs-lookup"><span data-stu-id="ff843-123">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff843-124">要求</span><span class="sxs-lookup"><span data-stu-id="ff843-124">Requirements</span></span>  
 <span data-ttu-id="ff843-125">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff843-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff843-126">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ff843-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ff843-127">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff843-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff843-128">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff843-128">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff843-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ff843-129">See also</span></span>

- [<span data-ttu-id="ff843-130">GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="ff843-130">GetILToNativeMapping Method</span></span>](icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="ff843-131">ICorProfilerInfo4 接口</span><span class="sxs-lookup"><span data-stu-id="ff843-131">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="ff843-132">分析接口</span><span class="sxs-lookup"><span data-stu-id="ff843-132">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="ff843-133">分析</span><span class="sxs-lookup"><span data-stu-id="ff843-133">Profiling</span></span>](index.md)
