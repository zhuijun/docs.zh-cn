---
title: ICorProfilerFunctionEnum::Skip 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
ms.openlocfilehash: 0f096f76ec47cfe3399e9184eb82bf20040efbbb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503037"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="7f001-102">ICorProfilerFunctionEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="7f001-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="7f001-103">将枚举器的游标从其当前位置前移，以便跳过指定数量的元素。</span><span class="sxs-lookup"><span data-stu-id="7f001-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f001-104">语法</span><span class="sxs-lookup"><span data-stu-id="7f001-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f001-105">参数</span><span class="sxs-lookup"><span data-stu-id="7f001-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7f001-106">中要跳过的元素数。</span><span class="sxs-lookup"><span data-stu-id="7f001-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f001-107">返回值</span><span class="sxs-lookup"><span data-stu-id="7f001-107">Return Value</span></span>  
 <span data-ttu-id="7f001-108">此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。</span><span class="sxs-lookup"><span data-stu-id="7f001-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7f001-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f001-109">HRESULT</span></span>|<span data-ttu-id="7f001-110">说明</span><span class="sxs-lookup"><span data-stu-id="7f001-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f001-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f001-111">S_OK</span></span>|<span data-ttu-id="7f001-112">`celt`元素已被跳过。</span><span class="sxs-lookup"><span data-stu-id="7f001-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="7f001-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7f001-113">S_FALSE</span></span>|<span data-ttu-id="7f001-114">`celt`跳过的元素数少于个，这表示没有更多元素。</span><span class="sxs-lookup"><span data-stu-id="7f001-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f001-115">注解</span><span class="sxs-lookup"><span data-stu-id="7f001-115">Remarks</span></span>  
 <span data-ttu-id="7f001-116">此枚举器的游标的新位置为（当前位置） + `celt` 。</span><span class="sxs-lookup"><span data-stu-id="7f001-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f001-117">要求</span><span class="sxs-lookup"><span data-stu-id="7f001-117">Requirements</span></span>  
 <span data-ttu-id="7f001-118">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f001-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f001-119">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7f001-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7f001-120">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f001-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f001-121">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f001-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f001-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f001-122">See also</span></span>

- [<span data-ttu-id="7f001-123">ICorProfilerFunctionEnum 接口</span><span class="sxs-lookup"><span data-stu-id="7f001-123">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="7f001-124">分析接口</span><span class="sxs-lookup"><span data-stu-id="7f001-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
