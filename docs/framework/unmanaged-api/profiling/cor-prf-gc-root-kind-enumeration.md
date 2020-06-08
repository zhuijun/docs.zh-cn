---
title: COR_PRF_GC_ROOT_KIND 枚举
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_KIND
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_KIND
helpviewer_keywords:
- COR_PRF_GC_ROOT_KIND enumeration [.NET Framework profiling]
ms.assetid: b9fb1c03-417f-41d4-aed4-02cb4ade8def
topic_type:
- apiref
ms.openlocfilehash: 0ea584bfff4340e5e9635d6c31e177e88765b582
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500866"
---
# <a name="cor_prf_gc_root_kind-enumeration"></a><span data-ttu-id="c5aa4-102">COR_PRF_GC_ROOT_KIND 枚举</span><span class="sxs-lookup"><span data-stu-id="c5aa4-102">COR_PRF_GC_ROOT_KIND Enumeration</span></span>
<span data-ttu-id="c5aa4-103">指示由[ICorProfilerCallback2：： RootReferences2](icorprofilercallback2-rootreferences2-method.md)回调公开的垃圾回收根的类型。</span><span class="sxs-lookup"><span data-stu-id="c5aa4-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5aa4-104">语法</span><span class="sxs-lookup"><span data-stu-id="c5aa4-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="c5aa4-105">成员</span><span class="sxs-lookup"><span data-stu-id="c5aa4-105">Members</span></span>  
  
|<span data-ttu-id="c5aa4-106">成员</span><span class="sxs-lookup"><span data-stu-id="c5aa4-106">Member</span></span>|<span data-ttu-id="c5aa4-107">描述</span><span class="sxs-lookup"><span data-stu-id="c5aa4-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="c5aa4-108">根是堆栈上的变量。</span><span class="sxs-lookup"><span data-stu-id="c5aa4-108">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="c5aa4-109">根是终结器队列中的条目。</span><span class="sxs-lookup"><span data-stu-id="c5aa4-109">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="c5aa4-110">根为垃圾回收句柄。</span><span class="sxs-lookup"><span data-stu-id="c5aa4-110">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="c5aa4-111">根的类型未指定。</span><span class="sxs-lookup"><span data-stu-id="c5aa4-111">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c5aa4-112">要求</span><span class="sxs-lookup"><span data-stu-id="c5aa4-112">Requirements</span></span>  
 <span data-ttu-id="c5aa4-113">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5aa4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5aa4-114">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c5aa4-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c5aa4-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5aa4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5aa4-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5aa4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5aa4-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5aa4-117">See also</span></span>

- [<span data-ttu-id="c5aa4-118">分析枚举</span><span class="sxs-lookup"><span data-stu-id="c5aa4-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
