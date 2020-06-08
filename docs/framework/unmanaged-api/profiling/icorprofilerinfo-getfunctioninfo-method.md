---
title: ICorProfilerInfo::GetFunctionInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type:
- apiref
ms.openlocfilehash: e7193526bb0da1d28da4bf6bde108fc4d3fba273
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503011"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="73d84-102">ICorProfilerInfo::GetFunctionInfo 方法</span><span class="sxs-lookup"><span data-stu-id="73d84-102">ICorProfilerInfo::GetFunctionInfo Method</span></span>
<span data-ttu-id="73d84-103">获取指定函数的父类和元数据标记。</span><span class="sxs-lookup"><span data-stu-id="73d84-103">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73d84-104">语法</span><span class="sxs-lookup"><span data-stu-id="73d84-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73d84-105">参数</span><span class="sxs-lookup"><span data-stu-id="73d84-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="73d84-106">中要获取其父类和元数据标记的函数的 ID。</span><span class="sxs-lookup"><span data-stu-id="73d84-106">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="73d84-107">[out] 一个指向函数的父类的指针。</span><span class="sxs-lookup"><span data-stu-id="73d84-107">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="73d84-108">[out] 一个指向在其中定义函数父类的模块的指针。</span><span class="sxs-lookup"><span data-stu-id="73d84-108">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="73d84-109">[out] 指向函数的元数据标记的指针。</span><span class="sxs-lookup"><span data-stu-id="73d84-109">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73d84-110">注解</span><span class="sxs-lookup"><span data-stu-id="73d84-110">Remarks</span></span>  
 <span data-ttu-id="73d84-111">探查器代码可调用[ICorProfilerInfo：： GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md)以获取给定模块的元数据接口。</span><span class="sxs-lookup"><span data-stu-id="73d84-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="73d84-112">然后，返回到 `pToken` 所引用位置的元数据标记便可用于访问该函数的元数据。</span><span class="sxs-lookup"><span data-stu-id="73d84-112">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="73d84-113">对于 `ClassID` 泛型类中的函数，如果没有关于函数使用的更多上下文信息，则可能无法获得。</span><span class="sxs-lookup"><span data-stu-id="73d84-113">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="73d84-114">在这种情况下， `pClassId` 将为0。</span><span class="sxs-lookup"><span data-stu-id="73d84-114">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="73d84-115">探查器代码应将[ICorProfilerInfo2：： GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md)与 COR_PRF_FRAME_INFO 值一起使用，以提供更多上下文。</span><span class="sxs-lookup"><span data-stu-id="73d84-115">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73d84-116">要求</span><span class="sxs-lookup"><span data-stu-id="73d84-116">Requirements</span></span>  
 <span data-ttu-id="73d84-117">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="73d84-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73d84-118">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="73d84-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="73d84-119">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73d84-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73d84-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73d84-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73d84-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="73d84-121">See also</span></span>

- [<span data-ttu-id="73d84-122">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="73d84-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
