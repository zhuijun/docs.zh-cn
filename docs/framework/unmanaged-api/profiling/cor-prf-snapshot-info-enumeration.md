---
title: COR_PRF_SNAPSHOT_INFO 枚举
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
ms.openlocfilehash: 6168c5b27868a261871b292e17ca02b04ae89917
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500775"
---
# <a name="cor_prf_snapshot_info-enumeration"></a><span data-ttu-id="320f5-102">COR_PRF_SNAPSHOT_INFO 枚举</span><span class="sxs-lookup"><span data-stu-id="320f5-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="320f5-103">指定在每次调用探查器的[StackSnapshotCallback](stacksnapshotcallback-function.md)函数时要通过堆栈快照传递回多少数据。</span><span class="sxs-lookup"><span data-stu-id="320f5-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="320f5-104">语法</span><span class="sxs-lookup"><span data-stu-id="320f5-104">Syntax</span></span>  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="320f5-105">成员</span><span class="sxs-lookup"><span data-stu-id="320f5-105">Members</span></span>  
  
|<span data-ttu-id="320f5-106">成员</span><span class="sxs-lookup"><span data-stu-id="320f5-106">Members</span></span>|<span data-ttu-id="320f5-107">说明</span><span class="sxs-lookup"><span data-stu-id="320f5-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="320f5-108">指示必须为所有 `StackSnapshotCallback` 参数（参数除外）传递值 `context` 。</span><span class="sxs-lookup"><span data-stu-id="320f5-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="320f5-109">指示必须为所有 `StackSnapshotCallback` 参数（包括参数）传递值 `context` 。</span><span class="sxs-lookup"><span data-stu-id="320f5-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="320f5-110">指示将使用更简单的替代堆栈遍历算法。</span><span class="sxs-lookup"><span data-stu-id="320f5-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="320f5-111">注解</span><span class="sxs-lookup"><span data-stu-id="320f5-111">Remarks</span></span>  
 <span data-ttu-id="320f5-112">枚举提供的值 `COR_PRF_SNAPSHOT_INFO` 将作为参数传递给[DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="320f5-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="320f5-113">要求</span><span class="sxs-lookup"><span data-stu-id="320f5-113">Requirements</span></span>  
 <span data-ttu-id="320f5-114">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="320f5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="320f5-115">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="320f5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="320f5-116">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="320f5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="320f5-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="320f5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="320f5-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="320f5-118">See also</span></span>

- [<span data-ttu-id="320f5-119">DoStackSnapshot 方法</span><span class="sxs-lookup"><span data-stu-id="320f5-119">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="320f5-120">分析枚举</span><span class="sxs-lookup"><span data-stu-id="320f5-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
