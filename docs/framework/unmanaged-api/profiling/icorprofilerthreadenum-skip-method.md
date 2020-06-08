---
title: ICorProfilerThreadEnum::Skip 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
ms.openlocfilehash: 4218faf1c324175424ab20305224f7f2fa51bb7a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494210"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="4fd79-102">ICorProfilerThreadEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="4fd79-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="4fd79-103">从当前位置前移枚举器的光标，以便跳过指定的元素数量。</span><span class="sxs-lookup"><span data-stu-id="4fd79-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fd79-104">语法</span><span class="sxs-lookup"><span data-stu-id="4fd79-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fd79-105">参数</span><span class="sxs-lookup"><span data-stu-id="4fd79-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="4fd79-106">中要跳过的元素数。</span><span class="sxs-lookup"><span data-stu-id="4fd79-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4fd79-107">返回值</span><span class="sxs-lookup"><span data-stu-id="4fd79-107">Return Value</span></span>  
 <span data-ttu-id="4fd79-108">此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。</span><span class="sxs-lookup"><span data-stu-id="4fd79-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4fd79-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4fd79-109">HRESULT</span></span>|<span data-ttu-id="4fd79-110">说明</span><span class="sxs-lookup"><span data-stu-id="4fd79-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4fd79-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4fd79-111">S_OK</span></span>|<span data-ttu-id="4fd79-112">`celt`元素已被跳过。</span><span class="sxs-lookup"><span data-stu-id="4fd79-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="4fd79-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4fd79-113">S_FALSE</span></span>|<span data-ttu-id="4fd79-114">`celt`跳过的元素数少于个，这表示没有更多元素。</span><span class="sxs-lookup"><span data-stu-id="4fd79-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fd79-115">注解</span><span class="sxs-lookup"><span data-stu-id="4fd79-115">Remarks</span></span>  
 <span data-ttu-id="4fd79-116">此枚举器的游标的新位置为（当前位置） + `celt` 。</span><span class="sxs-lookup"><span data-stu-id="4fd79-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fd79-117">要求</span><span class="sxs-lookup"><span data-stu-id="4fd79-117">Requirements</span></span>  
 <span data-ttu-id="4fd79-118">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4fd79-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fd79-119">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4fd79-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4fd79-120">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fd79-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fd79-121">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fd79-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fd79-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4fd79-122">See also</span></span>

- [<span data-ttu-id="4fd79-123">ICorProfilerThreadEnum 接口</span><span class="sxs-lookup"><span data-stu-id="4fd79-123">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="4fd79-124">分析接口</span><span class="sxs-lookup"><span data-stu-id="4fd79-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
