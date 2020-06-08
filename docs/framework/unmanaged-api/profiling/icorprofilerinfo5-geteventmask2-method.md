---
title: ICorProfilerInfo5::GetEventMask2 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
ms.openlocfilehash: 758e5b71443b127c80c820eb8531056530e81b13
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495692"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="6a942-102">ICorProfilerInfo5::GetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="6a942-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>
<span data-ttu-id="6a942-103">[仅在 .NET Framework 4.5.2 及更高版本中受支持]</span><span class="sxs-lookup"><span data-stu-id="6a942-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6a942-104">获取探查器要从公共语言运行时 (CLR) 中接收通知的当前事件类别。</span><span class="sxs-lookup"><span data-stu-id="6a942-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="6a942-105">它提供[ICorProfilerInfo：： GetEventMask](icorprofilerinfo-geteventmask-method.md)方法未提供的功能。</span><span class="sxs-lookup"><span data-stu-id="6a942-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a942-106">语法</span><span class="sxs-lookup"><span data-stu-id="6a942-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a942-107">参数</span><span class="sxs-lookup"><span data-stu-id="6a942-107">Parameters</span></span>  
 `pdwEventsLow`  
 <span data-ttu-id="6a942-108">[out] 一个指向指定事件类别的 4 字节值的指针。</span><span class="sxs-lookup"><span data-stu-id="6a942-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="6a942-109">每个位都可控制不同的功能、行为或事件类型。</span><span class="sxs-lookup"><span data-stu-id="6a942-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="6a942-110">[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)枚举中描述了这些位。</span><span class="sxs-lookup"><span data-stu-id="6a942-110">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="6a942-111">[out] 一个指向指定事件类别的 4 字节值的指针。</span><span class="sxs-lookup"><span data-stu-id="6a942-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="6a942-112">每个位都可控制不同的功能、行为或事件类型。</span><span class="sxs-lookup"><span data-stu-id="6a942-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="6a942-113">[COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md)枚举中描述了这些位。</span><span class="sxs-lookup"><span data-stu-id="6a942-113">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a942-114">注解</span><span class="sxs-lookup"><span data-stu-id="6a942-114">Remarks</span></span>  
 <span data-ttu-id="6a942-115">`GetEventMask2` 方法用于确定探查器已订阅了哪些回调。</span><span class="sxs-lookup"><span data-stu-id="6a942-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="6a942-116">通常，您 `pdwEventsLow` 需要对和 `pdwEventsHigh` 值以及要设置的任何新位执行逻辑 "或"，然后调用[SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="6a942-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="6a942-117">此方法是[GetEventMask](icorprofilerinfo-geteventmask-method.md)方法的建议替代方法。</span><span class="sxs-lookup"><span data-stu-id="6a942-117">This method is the recommended alternative to the [GetEventMask](icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a942-118">要求</span><span class="sxs-lookup"><span data-stu-id="6a942-118">Requirements</span></span>  
 <span data-ttu-id="6a942-119">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6a942-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a942-120">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6a942-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6a942-121">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a942-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a942-122">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a942-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a942-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6a942-123">See also</span></span>

- [<span data-ttu-id="6a942-124">ICorProfilerInfo5 接口</span><span class="sxs-lookup"><span data-stu-id="6a942-124">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="6a942-125">SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="6a942-125">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)
