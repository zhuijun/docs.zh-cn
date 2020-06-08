---
title: ICorProfilerInfo2::EnumModuleFrozenObjects 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.EnumModuleFrozenObjects
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::EnumModuleFrozenObjects
helpviewer_keywords:
- EnumModuleFrozenObjects method [.NET Framework profiling]
- ICorProfilerInfo2::EnumModuleFrozenObjects method [.NET Framework profiling]
ms.assetid: 920b6483-7064-4d64-8613-fcc38ccf9b1e
topic_type:
- apiref
ms.openlocfilehash: 1fe44f8f84c079e920c8c82fb9d52d1980d3b852
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497200"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="04fc9-102">ICorProfilerInfo2::EnumModuleFrozenObjects 方法</span><span class="sxs-lookup"><span data-stu-id="04fc9-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="04fc9-103">获取一个枚举器，该枚举数允许对指定模块中的冻结对象进行迭代。此方法已过时。</span><span class="sxs-lookup"><span data-stu-id="04fc9-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04fc9-104">语法</span><span class="sxs-lookup"><span data-stu-id="04fc9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04fc9-105">参数</span><span class="sxs-lookup"><span data-stu-id="04fc9-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="04fc9-106">中包含要枚举的冻结对象的模块的 ID。</span><span class="sxs-lookup"><span data-stu-id="04fc9-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="04fc9-107">弄一个指针，指向用于枚举冻结对象的[ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md)接口的地址。</span><span class="sxs-lookup"><span data-stu-id="04fc9-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04fc9-108">要求</span><span class="sxs-lookup"><span data-stu-id="04fc9-108">Requirements</span></span>  
 <span data-ttu-id="04fc9-109">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="04fc9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04fc9-110">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="04fc9-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="04fc9-111">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04fc9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04fc9-112">**.NET Framework 版本：** 3.5、3.0 SP1、3.0、2.0 SP1、2。0</span><span class="sxs-lookup"><span data-stu-id="04fc9-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04fc9-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="04fc9-113">See also</span></span>

- [<span data-ttu-id="04fc9-114">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="04fc9-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="04fc9-115">ICorProfilerInfo2 接口</span><span class="sxs-lookup"><span data-stu-id="04fc9-115">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
