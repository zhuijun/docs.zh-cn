---
title: ICorProfilerInfo::GetFunctionFromToken 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionFromToken method [.NET Framework profiling]
- GetFunctionFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0eed759f-cce8-405d-88dc-9ee293a38928
topic_type:
- apiref
ms.openlocfilehash: 18c3b6e840ec1f6cb1481c8d752e6399dcdae077
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498136"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="00f83-102">ICorProfilerInfo::GetFunctionFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="00f83-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="00f83-103">获取函数的 ID。</span><span class="sxs-lookup"><span data-stu-id="00f83-103">Gets the ID of a function.</span></span> <span data-ttu-id="00f83-104">此方法在 .NET Framework 版本2.0 中已过时。</span><span class="sxs-lookup"><span data-stu-id="00f83-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="00f83-105">改为使用[ICorProfilerInfo2：： GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="00f83-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00f83-106">语法</span><span class="sxs-lookup"><span data-stu-id="00f83-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="00f83-107">备注</span><span class="sxs-lookup"><span data-stu-id="00f83-107">Remarks</span></span>  
 <span data-ttu-id="00f83-108">此 `GetFunctionFromToken` 方法不适用于泛型函数或泛型类型中的函数; 它现在已过时。</span><span class="sxs-lookup"><span data-stu-id="00f83-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="00f83-109">用于 `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` 所有函数。</span><span class="sxs-lookup"><span data-stu-id="00f83-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00f83-110">要求</span><span class="sxs-lookup"><span data-stu-id="00f83-110">Requirements</span></span>  
 <span data-ttu-id="00f83-111">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00f83-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00f83-112">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="00f83-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00f83-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00f83-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00f83-114">**.NET Framework 版本：** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="00f83-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00f83-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="00f83-115">See also</span></span>

- [<span data-ttu-id="00f83-116">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="00f83-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
