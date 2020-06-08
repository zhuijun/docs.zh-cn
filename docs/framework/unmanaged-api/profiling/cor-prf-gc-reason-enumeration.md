---
title: COR_PRF_GC_REASON 枚举
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_REASON
helpviewer_keywords:
- COR_PRF_GC_REASON enumeration [.NET Framework profiling]
ms.assetid: 72822b95-a7fb-485e-9d55-1cb016d9a458
topic_type:
- apiref
ms.openlocfilehash: 409a21238f172e5ecdaa8d5bfa237a9f3fe46345
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500898"
---
# <a name="cor_prf_gc_reason-enumeration"></a><span data-ttu-id="c2617-102">COR_PRF_GC_REASON 枚举</span><span class="sxs-lookup"><span data-stu-id="c2617-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="c2617-103">指示当前发生垃圾回收的原因。</span><span class="sxs-lookup"><span data-stu-id="c2617-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2617-104">语法</span><span class="sxs-lookup"><span data-stu-id="c2617-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="c2617-105">成员</span><span class="sxs-lookup"><span data-stu-id="c2617-105">Members</span></span>  
  
|<span data-ttu-id="c2617-106">成员</span><span class="sxs-lookup"><span data-stu-id="c2617-106">Member</span></span>|<span data-ttu-id="c2617-107">描述</span><span class="sxs-lookup"><span data-stu-id="c2617-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="c2617-108">垃圾回收由 <xref:System.GC.Collect%2A> 方法引起。</span><span class="sxs-lookup"><span data-stu-id="c2617-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="c2617-109">原因未指定。</span><span class="sxs-lookup"><span data-stu-id="c2617-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2617-110">要求</span><span class="sxs-lookup"><span data-stu-id="c2617-110">Requirements</span></span>  
 <span data-ttu-id="c2617-111">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c2617-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2617-112">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c2617-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c2617-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2617-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2617-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2617-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2617-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2617-115">See also</span></span>

- [<span data-ttu-id="c2617-116">分析枚举</span><span class="sxs-lookup"><span data-stu-id="c2617-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
