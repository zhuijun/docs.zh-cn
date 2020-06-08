---
title: ICorProfilerModuleEnum::Skip 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type:
- apiref
ms.openlocfilehash: b48b782b7c8be35bfb815d72758f0bc316fb2114
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494717"
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="14c8e-102">ICorProfilerModuleEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="14c8e-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="14c8e-103">将枚举器的游标从其当前位置前移，以便跳过指定数量的元素。</span><span class="sxs-lookup"><span data-stu-id="14c8e-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14c8e-104">语法</span><span class="sxs-lookup"><span data-stu-id="14c8e-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14c8e-105">参数</span><span class="sxs-lookup"><span data-stu-id="14c8e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="14c8e-106">中要跳过的元素数。</span><span class="sxs-lookup"><span data-stu-id="14c8e-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14c8e-107">返回值</span><span class="sxs-lookup"><span data-stu-id="14c8e-107">Return Value</span></span>  
 <span data-ttu-id="14c8e-108">此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。</span><span class="sxs-lookup"><span data-stu-id="14c8e-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="14c8e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="14c8e-109">HRESULT</span></span>|<span data-ttu-id="14c8e-110">说明</span><span class="sxs-lookup"><span data-stu-id="14c8e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="14c8e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="14c8e-111">S_OK</span></span>|<span data-ttu-id="14c8e-112">`celt`元素已被跳过。</span><span class="sxs-lookup"><span data-stu-id="14c8e-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="14c8e-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="14c8e-113">S_FALSE</span></span>|<span data-ttu-id="14c8e-114">`celt`跳过的元素数少于个，这表示没有更多元素。</span><span class="sxs-lookup"><span data-stu-id="14c8e-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14c8e-115">注解</span><span class="sxs-lookup"><span data-stu-id="14c8e-115">Remarks</span></span>  
 <span data-ttu-id="14c8e-116">此枚举器的游标的新位置为（当前位置） + `celt` 。</span><span class="sxs-lookup"><span data-stu-id="14c8e-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14c8e-117">要求</span><span class="sxs-lookup"><span data-stu-id="14c8e-117">Requirements</span></span>  
 <span data-ttu-id="14c8e-118">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="14c8e-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14c8e-119">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="14c8e-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="14c8e-120">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14c8e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14c8e-121">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14c8e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14c8e-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="14c8e-122">See also</span></span>

- [<span data-ttu-id="14c8e-123">ICorProfilerModuleEnum 接口</span><span class="sxs-lookup"><span data-stu-id="14c8e-123">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="14c8e-124">分析接口</span><span class="sxs-lookup"><span data-stu-id="14c8e-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
