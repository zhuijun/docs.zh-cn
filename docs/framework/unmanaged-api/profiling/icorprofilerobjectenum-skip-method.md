---
title: ICorProfilerObjectEnum::Skip 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type:
- apiref
ms.openlocfilehash: 2248f99b76aaabff4bd3dc78b6e777a95692bb9c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494512"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="62bac-102">ICorProfilerObjectEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="62bac-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="62bac-103">将此枚举器的光标从其当前位置前移，以便跳过指定数目的元素。</span><span class="sxs-lookup"><span data-stu-id="62bac-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62bac-104">语法</span><span class="sxs-lookup"><span data-stu-id="62bac-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62bac-105">参数</span><span class="sxs-lookup"><span data-stu-id="62bac-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="62bac-106">中要跳过的元素数。</span><span class="sxs-lookup"><span data-stu-id="62bac-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62bac-107">注解</span><span class="sxs-lookup"><span data-stu-id="62bac-107">Remarks</span></span>  
 <span data-ttu-id="62bac-108">此枚举器的游标的新位置为：（当前位置） + `celt` 。</span><span class="sxs-lookup"><span data-stu-id="62bac-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62bac-109">要求</span><span class="sxs-lookup"><span data-stu-id="62bac-109">Requirements</span></span>  
 <span data-ttu-id="62bac-110">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62bac-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62bac-111">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="62bac-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="62bac-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62bac-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62bac-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62bac-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62bac-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62bac-114">See also</span></span>

- [<span data-ttu-id="62bac-115">ICorProfilerObjectEnum 接口</span><span class="sxs-lookup"><span data-stu-id="62bac-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
