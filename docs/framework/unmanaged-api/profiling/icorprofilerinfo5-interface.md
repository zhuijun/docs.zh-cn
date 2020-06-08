---
title: ICorProfilerInfo5 接口
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
ms.openlocfilehash: 82f6262c2c576b49be4e7fcaa14043950df4c67a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495622"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="7a811-102">ICorProfilerInfo5 接口</span><span class="sxs-lookup"><span data-stu-id="7a811-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="7a811-103">[仅在 .NET Framework 4.5.2 及更高版本中受支持]</span><span class="sxs-lookup"><span data-stu-id="7a811-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="7a811-104">[ICorProfilerInfo4](icorprofilerinfo4-interface.md)的子类，它提供代码探查器用于与公共语言运行时（CLR）进行通信以控制事件监视的方法。</span><span class="sxs-lookup"><span data-stu-id="7a811-104">A subclass of [ICorProfilerInfo4](icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a811-105">方法</span><span class="sxs-lookup"><span data-stu-id="7a811-105">Methods</span></span>  
  
|<span data-ttu-id="7a811-106">方法</span><span class="sxs-lookup"><span data-stu-id="7a811-106">Method</span></span>|<span data-ttu-id="7a811-107">说明</span><span class="sxs-lookup"><span data-stu-id="7a811-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a811-108">GetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="7a811-108">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="7a811-109">获取探查器要为其接收来自 CLR 的通知的当前事件类别。</span><span class="sxs-lookup"><span data-stu-id="7a811-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="7a811-110">SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="7a811-110">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="7a811-111">设置一个指定事件类型的值，探查器将为该类事件接收来自 CLR 的事件通知。</span><span class="sxs-lookup"><span data-stu-id="7a811-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a811-112">注解</span><span class="sxs-lookup"><span data-stu-id="7a811-112">Remarks</span></span>  
 <span data-ttu-id="7a811-113">此接口上的可用方法旨在替换[ICorProfilerInfo：： GetEventMask](icorprofilerinfo-geteventmask-method.md)和[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="7a811-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a811-114">要求</span><span class="sxs-lookup"><span data-stu-id="7a811-114">Requirements</span></span>  
 <span data-ttu-id="7a811-115">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7a811-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a811-116">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7a811-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7a811-117">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a811-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a811-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7a811-118">See also</span></span>

- [<span data-ttu-id="7a811-119">分析接口</span><span class="sxs-lookup"><span data-stu-id="7a811-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
