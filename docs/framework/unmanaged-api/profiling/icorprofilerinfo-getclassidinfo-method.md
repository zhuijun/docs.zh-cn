---
title: ICorProfilerInfo::GetClassIDInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassIDInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassIDInfo
helpviewer_keywords:
- GetClassIDInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetClassIDInfo method [.NET Framework profiling]
ms.assetid: 9e93b99e-5aca-415c-8e37-7f33753b612d
topic_type:
- apiref
ms.openlocfilehash: 4fbee938ae86b338f2beb0b48feeee46f144a4a0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498487"
---
# <a name="icorprofilerinfogetclassidinfo-method"></a><span data-ttu-id="e8646-102">ICorProfilerInfo::GetClassIDInfo 方法</span><span class="sxs-lookup"><span data-stu-id="e8646-102">ICorProfilerInfo::GetClassIDInfo Method</span></span>
<span data-ttu-id="e8646-103">获取指定类的父模块和元数据标记。</span><span class="sxs-lookup"><span data-stu-id="e8646-103">Gets the parent module and the metadata token for the specified class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8646-104">语法</span><span class="sxs-lookup"><span data-stu-id="e8646-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8646-105">参数</span><span class="sxs-lookup"><span data-stu-id="e8646-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="e8646-106">中要获取其信息的类的 ID。</span><span class="sxs-lookup"><span data-stu-id="e8646-106">[in] The ID of the class for which to get the information.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="e8646-107">弄指向类的父模块的 ID 的指针。</span><span class="sxs-lookup"><span data-stu-id="e8646-107">[out] A pointer to the ID of the parent module of the class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="e8646-108">弄指向类的元数据标记的指针。</span><span class="sxs-lookup"><span data-stu-id="e8646-108">[out] A pointer to the metadata token for the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8646-109">注解</span><span class="sxs-lookup"><span data-stu-id="e8646-109">Remarks</span></span>  
 <span data-ttu-id="e8646-110">探查器代码可调用[ICorProfilerInfo：： GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md)以获取给定模块的元数据接口。</span><span class="sxs-lookup"><span data-stu-id="e8646-110">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="e8646-111">返回至 `pTypeDefToken` 所引用的位置的元数据标记可用于访问类的元数据。</span><span class="sxs-lookup"><span data-stu-id="e8646-111">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="e8646-112">若要获取有关泛型类型的详细信息，请使用[ICorProfilerInfo2：： GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md)。</span><span class="sxs-lookup"><span data-stu-id="e8646-112">To get more information for generic types, use [ICorProfilerInfo2::GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8646-113">要求</span><span class="sxs-lookup"><span data-stu-id="e8646-113">Requirements</span></span>  
 <span data-ttu-id="e8646-114">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8646-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8646-115">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e8646-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e8646-116">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8646-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8646-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8646-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8646-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e8646-118">See also</span></span>

- [<span data-ttu-id="e8646-119">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="e8646-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
