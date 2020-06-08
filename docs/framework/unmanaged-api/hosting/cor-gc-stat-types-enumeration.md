---
title: COR_GC_STAT_TYPES 枚举
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
ms.openlocfilehash: d7e78dfc4beba67cc376b221d0cd49f7200f5d23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501685"
---
# <a name="cor_gc_stat_types-enumeration"></a><span data-ttu-id="fee7d-102">COR_GC_STAT_TYPES 枚举</span><span class="sxs-lookup"><span data-stu-id="fee7d-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="fee7d-103">指定要为垃圾回收记录的统计信息。</span><span class="sxs-lookup"><span data-stu-id="fee7d-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fee7d-104">语法</span><span class="sxs-lookup"><span data-stu-id="fee7d-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="fee7d-105">备注</span><span class="sxs-lookup"><span data-stu-id="fee7d-105">Remarks</span></span>  
 <span data-ttu-id="fee7d-106">此枚举指定[COR_GC_STATS](cor-gc-stats-structure.md)结构中的哪些统计信息由[ICLRGCManager：： GetStats](iclrgcmanager-getstats-method.md)方法设置。</span><span class="sxs-lookup"><span data-stu-id="fee7d-106">This enumeration specifies which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="fee7d-107">成员</span><span class="sxs-lookup"><span data-stu-id="fee7d-107">Members</span></span>  
  
|<span data-ttu-id="fee7d-108">成员</span><span class="sxs-lookup"><span data-stu-id="fee7d-108">Member</span></span>|<span data-ttu-id="fee7d-109">描述</span><span class="sxs-lookup"><span data-stu-id="fee7d-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="fee7d-110">记录为每个代执行的垃圾回收数。</span><span class="sxs-lookup"><span data-stu-id="fee7d-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="fee7d-111">记录内存使用情况和垃圾回收大小统计信息。</span><span class="sxs-lookup"><span data-stu-id="fee7d-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fee7d-112">要求</span><span class="sxs-lookup"><span data-stu-id="fee7d-112">Requirements</span></span>  
 <span data-ttu-id="fee7d-113">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fee7d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fee7d-114">**标头：** GCHost，GCHost</span><span class="sxs-lookup"><span data-stu-id="fee7d-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="fee7d-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fee7d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee7d-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fee7d-116">See also</span></span>

- [<span data-ttu-id="fee7d-117">COR_GC_STATS 结构</span><span class="sxs-lookup"><span data-stu-id="fee7d-117">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="fee7d-118">承载枚举</span><span class="sxs-lookup"><span data-stu-id="fee7d-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
