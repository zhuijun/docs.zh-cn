---
title: ICorProfilerInfo5::SetEventMask2 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
ms.openlocfilehash: 8027cdcde8281c363207e309bf65fcd90c03b626
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495614"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="b3b25-102">ICorProfilerInfo5::SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="b3b25-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="b3b25-103">[仅在 .NET Framework 4.5.2 及更高版本中受支持]</span><span class="sxs-lookup"><span data-stu-id="b3b25-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b3b25-104">设置一个值，用于指定探查器需要从公共语言运行时 (CLR) 接收其事件通知的事件的类型。</span><span class="sxs-lookup"><span data-stu-id="b3b25-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="b3b25-105">它提供的功能比[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)方法更多。</span><span class="sxs-lookup"><span data-stu-id="b3b25-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3b25-106">语法</span><span class="sxs-lookup"><span data-stu-id="b3b25-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3b25-107">参数</span><span class="sxs-lookup"><span data-stu-id="b3b25-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="b3b25-108">[in] 一个指定事件类别的 4 字节的值。</span><span class="sxs-lookup"><span data-stu-id="b3b25-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="b3b25-109">每个位都可控制不同的功能、行为或事件类型。</span><span class="sxs-lookup"><span data-stu-id="b3b25-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="b3b25-110">[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)枚举中描述了这些位。</span><span class="sxs-lookup"><span data-stu-id="b3b25-110">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="b3b25-111">[in] 一个指定事件类别的 4 字节的值。</span><span class="sxs-lookup"><span data-stu-id="b3b25-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="b3b25-112">每个位都可控制不同的功能、行为或事件类型。</span><span class="sxs-lookup"><span data-stu-id="b3b25-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="b3b25-113">[COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md)枚举中描述了这些位。</span><span class="sxs-lookup"><span data-stu-id="b3b25-113">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3b25-114">注解</span><span class="sxs-lookup"><span data-stu-id="b3b25-114">Remarks</span></span>  
 <span data-ttu-id="b3b25-115">`SetEventMask2` 方法用于设置探查器订阅的回调。</span><span class="sxs-lookup"><span data-stu-id="b3b25-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="b3b25-116">通常，你可以调用[GetEventMask2](icorprofilerinfo5-geteventmask2-method.md)方法来确定设置了哪些位，对其 `pdwEventsLow` 和 `pdwEventsHigh` 值以及要设置的任何新位执行逻辑 "或"，然后调用 `SetEventMask2` 方法。</span><span class="sxs-lookup"><span data-stu-id="b3b25-116">Typically, you call the [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="b3b25-117">此方法是[SetEventMask](icorprofilerinfo-seteventmask-method.md)方法的建议替代方法。</span><span class="sxs-lookup"><span data-stu-id="b3b25-117">This method is the recommended alternative to the [SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3b25-118">要求</span><span class="sxs-lookup"><span data-stu-id="b3b25-118">Requirements</span></span>  
 <span data-ttu-id="b3b25-119">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b25-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3b25-120">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b3b25-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b3b25-121">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3b25-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3b25-122">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3b25-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b25-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b3b25-123">See also</span></span>

- [<span data-ttu-id="b3b25-124">ICorProfilerInfo5 接口</span><span class="sxs-lookup"><span data-stu-id="b3b25-124">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="b3b25-125">GetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="b3b25-125">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)
