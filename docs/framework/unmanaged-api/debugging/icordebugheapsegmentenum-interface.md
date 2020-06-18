---
title: ICorDebugHeapSegmentEnum 接口
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
ms.openlocfilehash: acf490895db35af1c5d0d1e7fe7e3de5ae2a16b6
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904281"
---
# <a name="icordebugheapsegmentenum-interface"></a><span data-ttu-id="e4bce-102">ICorDebugHeapSegmentEnum 接口</span><span class="sxs-lookup"><span data-stu-id="e4bce-102">ICorDebugHeapSegmentEnum Interface</span></span>
<span data-ttu-id="e4bce-103">提供针对托管堆的内存区域的枚举器。</span><span class="sxs-lookup"><span data-stu-id="e4bce-103">Provides an enumerator for the memory regions of the managed heap.</span></span> <span data-ttu-id="e4bce-104">此接口是 ICorDebugEnum 接口的子类。</span><span class="sxs-lookup"><span data-stu-id="e4bce-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4bce-105">方法</span><span class="sxs-lookup"><span data-stu-id="e4bce-105">Methods</span></span>  
  
|<span data-ttu-id="e4bce-106">方法</span><span class="sxs-lookup"><span data-stu-id="e4bce-106">Method</span></span>|<span data-ttu-id="e4bce-107">说明</span><span class="sxs-lookup"><span data-stu-id="e4bce-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4bce-108">Next 方法</span><span class="sxs-lookup"><span data-stu-id="e4bce-108">Next Method</span></span>](icordebugheapsegmentenum-next-method.md)|<span data-ttu-id="e4bce-109">获取指定数量的[COR_SEGMENT](cor-segment-structure.md)实例，这些实例包含有关托管堆区域的信息。</span><span class="sxs-lookup"><span data-stu-id="e4bce-109">Gets the specified number of [COR_SEGMENT](cor-segment-structure.md) instances that contain information about regions of the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4bce-110">注解</span><span class="sxs-lookup"><span data-stu-id="e4bce-110">Remarks</span></span>  
 <span data-ttu-id="e4bce-111">`ICorDebugHeapSegmentEnum`接口实现 ICorDebugEnum 接口。</span><span class="sxs-lookup"><span data-stu-id="e4bce-111">The `ICorDebugHeapSegmentEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="e4bce-112">`ICorDebugHeapSegmentEnum`实例通过调用[ICorDebugProcess5：： EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md)方法填充[COR_SEGMENT](cor-segment-structure.md)的实例。</span><span class="sxs-lookup"><span data-stu-id="e4bce-112">An `ICorDebugHeapSegmentEnum` instance is populated with [COR_SEGMENT](cor-segment-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeapRegions](icordebugprocess5-enumerateheapregions-method.md) method.</span></span> <span data-ttu-id="e4bce-113">可以通过调用[ICorDebugHeapSegmentEnum：： Next](icordebugheapsegmentenum-next-method.md)方法枚举集合中的[COR_SEGMENT](cor-segment-structure.md)对象。</span><span class="sxs-lookup"><span data-stu-id="e4bce-113">The [COR_SEGMENT](cor-segment-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapSegmentEnum::Next](icordebugheapsegmentenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="e4bce-114">`ICorDebugHeapSegmentEnum`集合对象枚举可能包含托管对象的所有内存区域，但不保证托管对象实际驻留在这些区域中。</span><span class="sxs-lookup"><span data-stu-id="e4bce-114">An `ICorDebugHeapSegmentEnum` collection object enumerates all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="e4bce-115">它可能包括有关空的或保留的内存区域的信息。</span><span class="sxs-lookup"><span data-stu-id="e4bce-115">It may include information about empty or reserved memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4bce-116">要求</span><span class="sxs-lookup"><span data-stu-id="e4bce-116">Requirements</span></span>  
 <span data-ttu-id="e4bce-117">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e4bce-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4bce-118">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4bce-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4bce-119">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4bce-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4bce-120">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4bce-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4bce-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4bce-121">See also</span></span>

- [<span data-ttu-id="e4bce-122">调试接口</span><span class="sxs-lookup"><span data-stu-id="e4bce-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
