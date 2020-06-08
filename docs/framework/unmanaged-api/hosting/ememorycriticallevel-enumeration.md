---
title: EMemoryCriticalLevel 枚举
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
ms.openlocfilehash: 359dd84032fce920892631dda2615f63aa54fa6b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504376"
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="5fd7f-102">EMemoryCriticalLevel 枚举</span><span class="sxs-lookup"><span data-stu-id="5fd7f-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="5fd7f-103">包含一些值，这些值指示在请求特定内存分配但无法满足时，失败所造成的影响。</span><span class="sxs-lookup"><span data-stu-id="5fd7f-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fd7f-104">语法</span><span class="sxs-lookup"><span data-stu-id="5fd7f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="5fd7f-105">成员</span><span class="sxs-lookup"><span data-stu-id="5fd7f-105">Members</span></span>  
  
|<span data-ttu-id="5fd7f-106">成员</span><span class="sxs-lookup"><span data-stu-id="5fd7f-106">Member</span></span>|<span data-ttu-id="5fd7f-107">描述</span><span class="sxs-lookup"><span data-stu-id="5fd7f-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="5fd7f-108">指示分配对于在已请求分配的域中执行托管代码是至关重要的。</span><span class="sxs-lookup"><span data-stu-id="5fd7f-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="5fd7f-109">如果无法分配内存，则 CLR 无法保证域仍可用。</span><span class="sxs-lookup"><span data-stu-id="5fd7f-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="5fd7f-110">主机决定当无法满足分配时要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="5fd7f-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="5fd7f-111">它可以指示 CLR `AppDomain` 自动中止，或通过在[ICLRPolicyManager](iclrpolicymanager-interface.md)上调用方法来使其保持运行。</span><span class="sxs-lookup"><span data-stu-id="5fd7f-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="5fd7f-112">指示分配对于进程中的托管代码执行至关重要。</span><span class="sxs-lookup"><span data-stu-id="5fd7f-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="5fd7f-113">此值在启动和运行终结器时使用。</span><span class="sxs-lookup"><span data-stu-id="5fd7f-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="5fd7f-114">如果无法分配内存，则 CLR 无法在进程中运行。</span><span class="sxs-lookup"><span data-stu-id="5fd7f-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="5fd7f-115">如果分配失败，则会有效地禁用 CLR。</span><span class="sxs-lookup"><span data-stu-id="5fd7f-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="5fd7f-116">对 CLR 的所有后续调用都将失败，并 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="5fd7f-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="5fd7f-117">指示分配对于运行已请求分配的任务至关重要。</span><span class="sxs-lookup"><span data-stu-id="5fd7f-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="5fd7f-118">如果无法分配内存，则 CLR 无法保证任务能够执行。</span><span class="sxs-lookup"><span data-stu-id="5fd7f-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="5fd7f-119">发生故障时，CLR 将 <xref:System.Threading.ThreadAbortException> 在物理操作系统线程上引发。</span><span class="sxs-lookup"><span data-stu-id="5fd7f-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fd7f-120">注解</span><span class="sxs-lookup"><span data-stu-id="5fd7f-120">Remarks</span></span>  
 <span data-ttu-id="5fd7f-121">[IHostMemoryManager](ihostmemorymanager-interface.md)和[IHostMAlloc](ihostmalloc-interface.md)接口中定义的内存分配方法采用此类型的参数。</span><span class="sxs-lookup"><span data-stu-id="5fd7f-121">The memory allocation methods defined in the [IHostMemoryManager](ihostmemorymanager-interface.md) and [IHostMAlloc](ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="5fd7f-122">根据故障的严重性，主机可以决定是立即对分配请求进行故障转移还是要等待，直到它得以满足。</span><span class="sxs-lookup"><span data-stu-id="5fd7f-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fd7f-123">要求</span><span class="sxs-lookup"><span data-stu-id="5fd7f-123">Requirements</span></span>  
 <span data-ttu-id="5fd7f-124">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5fd7f-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fd7f-125">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5fd7f-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5fd7f-126">**库：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5fd7f-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5fd7f-127">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fd7f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fd7f-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5fd7f-128">See also</span></span>

- [<span data-ttu-id="5fd7f-129">ICLRMemoryNotificationCallback 接口</span><span class="sxs-lookup"><span data-stu-id="5fd7f-129">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="5fd7f-130">承载枚举</span><span class="sxs-lookup"><span data-stu-id="5fd7f-130">Hosting Enumerations</span></span>](hosting-enumerations.md)
