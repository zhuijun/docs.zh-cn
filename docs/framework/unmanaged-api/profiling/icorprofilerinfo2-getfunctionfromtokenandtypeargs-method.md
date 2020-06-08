---
title: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type:
- apiref
ms.openlocfilehash: 7f1276e1adeece086ca7b6791eb6e870faf4d010
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502868"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="fa8e4-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs 方法</span><span class="sxs-lookup"><span data-stu-id="fa8e4-102">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="fa8e4-103">`FunctionID`使用指定的元数据标记（包含类）和 `ClassID` 任何类型参数的值获取函数的。</span><span class="sxs-lookup"><span data-stu-id="fa8e4-103">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa8e4-104">语法</span><span class="sxs-lookup"><span data-stu-id="fa8e4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa8e4-105">参数</span><span class="sxs-lookup"><span data-stu-id="fa8e4-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="fa8e4-106">中函数所在模块的 ID。</span><span class="sxs-lookup"><span data-stu-id="fa8e4-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="fa8e4-107">中`mdMethodDef`引用函数的元数据标记。</span><span class="sxs-lookup"><span data-stu-id="fa8e4-107">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="fa8e4-108">中函数的包含类的 ID。</span><span class="sxs-lookup"><span data-stu-id="fa8e4-108">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="fa8e4-109">中给定函数的类型参数的数目。</span><span class="sxs-lookup"><span data-stu-id="fa8e4-109">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="fa8e4-110">对于非泛型函数，此值必须为零。</span><span class="sxs-lookup"><span data-stu-id="fa8e4-110">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="fa8e4-111">中值的数组 `ClassID` ，其中每个值都是函数的参数。</span><span class="sxs-lookup"><span data-stu-id="fa8e4-111">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="fa8e4-112">如果设置为零，则的值 `typeArgs` 可以为 NULL `cTypeArgs` 。</span><span class="sxs-lookup"><span data-stu-id="fa8e4-112">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="fa8e4-113">弄指向指定函数的的指针 `FunctionID` 。</span><span class="sxs-lookup"><span data-stu-id="fa8e4-113">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa8e4-114">注解</span><span class="sxs-lookup"><span data-stu-id="fa8e4-114">Remarks</span></span>  
 <span data-ttu-id="fa8e4-115">`GetFunctionFromTokenAndTypeArgs`使用 `mdMethodRef` 元数据而不是 `mdMethodDef` 元数据标记调用方法可能会产生不可预知的结果。</span><span class="sxs-lookup"><span data-stu-id="fa8e4-115">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="fa8e4-116">传递时，调用方应将解析 `mdMethodRef` 为 `mdMethodDef` 。</span><span class="sxs-lookup"><span data-stu-id="fa8e4-116">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="fa8e4-117">如果尚未加载该函数，则调用 `GetFunctionFromTokenAndTypeArgs` 将导致加载，这在许多上下文中是一个危险操作。</span><span class="sxs-lookup"><span data-stu-id="fa8e4-117">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="fa8e4-118">例如，在模块或类型加载过程中调用此方法可能会导致无限循环，因为运行时尝试循环加载某些功能。</span><span class="sxs-lookup"><span data-stu-id="fa8e4-118">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="fa8e4-119">通常， `GetFunctionFromTokenAndTypeArgs` 不建议使用。</span><span class="sxs-lookup"><span data-stu-id="fa8e4-119">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="fa8e4-120">如果探查器对特定函数的事件感兴趣，则它们应存储 `ModuleID` `mdMethodDef` 该函数的和，并使用[ICorProfilerInfo2：： GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md)来检查给定的是否 `FunctionID` 是所需函数的。</span><span class="sxs-lookup"><span data-stu-id="fa8e4-120">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa8e4-121">要求</span><span class="sxs-lookup"><span data-stu-id="fa8e4-121">Requirements</span></span>  
 <span data-ttu-id="fa8e4-122">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fa8e4-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa8e4-123">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fa8e4-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fa8e4-124">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa8e4-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa8e4-125">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa8e4-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa8e4-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa8e4-126">See also</span></span>

- [<span data-ttu-id="fa8e4-127">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="fa8e4-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="fa8e4-128">ICorProfilerInfo2 接口</span><span class="sxs-lookup"><span data-stu-id="fa8e4-128">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
