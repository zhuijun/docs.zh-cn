---
title: ICorProfilerInfo::GetClassFromObject 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromObject
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromObject
helpviewer_keywords:
- GetClassFromObject method [.NET Framework profiling]
- ICorProfilerInfo::GetClassFromObject method [.NET Framework profiling]
ms.assetid: b97493fb-713e-49d5-a73e-5688b2ad0700
topic_type:
- apiref
ms.openlocfilehash: 613267549329d2f48dcd18ae341e47538e414ac0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498526"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="9b5b3-102">ICorProfilerInfo::GetClassFromObject 方法</span><span class="sxs-lookup"><span data-stu-id="9b5b3-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="9b5b3-103">在 `ClassID` 给定对象的情况下，获取该对象的 `ObjectID` 。</span><span class="sxs-lookup"><span data-stu-id="9b5b3-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b5b3-104">语法</span><span class="sxs-lookup"><span data-stu-id="9b5b3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b5b3-105">参数</span><span class="sxs-lookup"><span data-stu-id="9b5b3-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="9b5b3-106">中要获取的对象的 ID `ClassID` 。</span><span class="sxs-lookup"><span data-stu-id="9b5b3-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="9b5b3-107">弄指向返回的的指针 `ClassID` 。</span><span class="sxs-lookup"><span data-stu-id="9b5b3-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b5b3-108">注解</span><span class="sxs-lookup"><span data-stu-id="9b5b3-108">Remarks</span></span>  
 <span data-ttu-id="9b5b3-109">如果为 null `pClassId` ， `objectId` 则表示具有正在卸载的类型。</span><span class="sxs-lookup"><span data-stu-id="9b5b3-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b5b3-110">要求</span><span class="sxs-lookup"><span data-stu-id="9b5b3-110">Requirements</span></span>  
 <span data-ttu-id="9b5b3-111">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9b5b3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b5b3-112">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9b5b3-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9b5b3-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b5b3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b5b3-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b5b3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b5b3-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9b5b3-115">See also</span></span>

- [<span data-ttu-id="9b5b3-116">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="9b5b3-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
