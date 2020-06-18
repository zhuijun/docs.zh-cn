---
title: ICorDebugHeapSegmentEnum::Next 方法
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
ms.openlocfilehash: 3d4e44eefaf99a40b9c4f1c45e7dd81192f8b607
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904268"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="b588a-102">ICorDebugHeapSegmentEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="b588a-102">ICorDebugHeapSegmentEnum::Next Method</span></span>
<span data-ttu-id="b588a-103">获取指定数量的[COR_SEGMENT](cor-segment-structure.md)实例，这些实例包含有关托管堆的内存区域的信息。</span><span class="sxs-lookup"><span data-stu-id="b588a-103">Gets the specified number of [COR_SEGMENT](cor-segment-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b588a-104">语法</span><span class="sxs-lookup"><span data-stu-id="b588a-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b588a-105">参数</span><span class="sxs-lookup"><span data-stu-id="b588a-105">Parameters</span></span>  
 <span data-ttu-id="b588a-106">celt</span><span class="sxs-lookup"><span data-stu-id="b588a-106">celt</span></span>  
 <span data-ttu-id="b588a-107">中要检索的段数。</span><span class="sxs-lookup"><span data-stu-id="b588a-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="b588a-108">段</span><span class="sxs-lookup"><span data-stu-id="b588a-108">segments</span></span>  
 <span data-ttu-id="b588a-109">弄指针数组，其中每个都指向一个[COR_SEGMENT](cor-segment-structure.md)对象，该对象提供有关托管堆中的内存区域的信息。</span><span class="sxs-lookup"><span data-stu-id="b588a-109">[out] An array of pointers, each of which points to a [COR_SEGMENT](cor-segment-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="b588a-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="b588a-110">pceltFetched</span></span>  
 <span data-ttu-id="b588a-111">弄一个指针，指向在中实际返回的[COR_SEGMENT](cor-segment-structure.md)对象的数量 `segments` 。</span><span class="sxs-lookup"><span data-stu-id="b588a-111">[out] A pointer to the number of [COR_SEGMENT](cor-segment-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="b588a-112">如果 `celt` 为 1，此值可能为 `null`。</span><span class="sxs-lookup"><span data-stu-id="b588a-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b588a-113">备注</span><span class="sxs-lookup"><span data-stu-id="b588a-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b588a-114">要求</span><span class="sxs-lookup"><span data-stu-id="b588a-114">Requirements</span></span>  
 <span data-ttu-id="b588a-115">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b588a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b588a-116">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b588a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b588a-117">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b588a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b588a-118">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b588a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b588a-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b588a-119">See also</span></span>

- [<span data-ttu-id="b588a-120">ICorDebugHeapSegmentEnum 接口</span><span class="sxs-lookup"><span data-stu-id="b588a-120">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="b588a-121">调试接口</span><span class="sxs-lookup"><span data-stu-id="b588a-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
