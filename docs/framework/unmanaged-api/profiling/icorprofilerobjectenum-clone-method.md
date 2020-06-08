---
title: ICorProfilerObjectEnum::Clone 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type:
- apiref
ms.openlocfilehash: a2a54c32c0713b4b69d8f2a0272687cbe9420610
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494756"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="5a543-102">ICorProfilerObjectEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="5a543-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="5a543-103">获取一个接口指针，该指针指向此[ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md)接口的副本。</span><span class="sxs-lookup"><span data-stu-id="5a543-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a543-104">语法</span><span class="sxs-lookup"><span data-stu-id="5a543-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a543-105">参数</span><span class="sxs-lookup"><span data-stu-id="5a543-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="5a543-106">弄指向接口指针的指针，该指针指向此接口的副本 `ICorProfilerObjectEnum` 。</span><span class="sxs-lookup"><span data-stu-id="5a543-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="5a543-107">副本单独维护自己的枚举状态。</span><span class="sxs-lookup"><span data-stu-id="5a543-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="5a543-108">但是，副本的初始光标位置将与此枚举器的当前游标位置相同。</span><span class="sxs-lookup"><span data-stu-id="5a543-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a543-109">要求</span><span class="sxs-lookup"><span data-stu-id="5a543-109">Requirements</span></span>  
 <span data-ttu-id="5a543-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a543-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a543-111">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5a543-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5a543-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a543-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a543-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a543-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a543-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5a543-114">See also</span></span>

- [<span data-ttu-id="5a543-115">ICorProfilerObjectEnum 接口</span><span class="sxs-lookup"><span data-stu-id="5a543-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
