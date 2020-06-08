---
title: ICLRGCManager::GetStats 方法
ms.date: 03/30/2017
api_name:
- ICLRGCManager.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type:
- apiref
ms.openlocfilehash: 8622920a81f4b469361ffa879f7a4eeda697cab9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504220"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="a155c-102">ICLRGCManager::GetStats 方法</span><span class="sxs-lookup"><span data-stu-id="a155c-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="a155c-103">获取有关公共语言运行时的垃圾回收系统的当前统计信息集。</span><span class="sxs-lookup"><span data-stu-id="a155c-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a155c-104">语法</span><span class="sxs-lookup"><span data-stu-id="a155c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a155c-105">参数</span><span class="sxs-lookup"><span data-stu-id="a155c-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="a155c-106">[in，out]一个[COR_GC_STATS](cor-gc-stats-structure.md)实例，其中包含请求的统计信息。</span><span class="sxs-lookup"><span data-stu-id="a155c-106">[in, out] A [COR_GC_STATS](cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a155c-107">返回值</span><span class="sxs-lookup"><span data-stu-id="a155c-107">Return Value</span></span>  
  
|<span data-ttu-id="a155c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a155c-108">HRESULT</span></span>|<span data-ttu-id="a155c-109">说明</span><span class="sxs-lookup"><span data-stu-id="a155c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a155c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a155c-110">S_OK</span></span>|<span data-ttu-id="a155c-111">`GetStats`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="a155c-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="a155c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a155c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a155c-113">公共语言运行时（CLR）未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="a155c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a155c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a155c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a155c-115">调用超时。</span><span class="sxs-lookup"><span data-stu-id="a155c-115">The call timed out.</span></span>|  
|<span data-ttu-id="a155c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a155c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a155c-117">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="a155c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a155c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a155c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a155c-119">已阻止的线程或纤程正在等待某个事件时，该事件被取消。</span><span class="sxs-lookup"><span data-stu-id="a155c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a155c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a155c-120">E_FAIL</span></span>|<span data-ttu-id="a155c-121">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="a155c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a155c-122">方法返回 E_FAIL 后，CLR 在该进程内将不再可用。</span><span class="sxs-lookup"><span data-stu-id="a155c-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a155c-123">对宿主方法的后续调用会返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a155c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a155c-124">注解</span><span class="sxs-lookup"><span data-stu-id="a155c-124">Remarks</span></span>  
 <span data-ttu-id="a155c-125">CLR 只计算和返回由的字段指定的统计信息 `Flags` `pStats` 。</span><span class="sxs-lookup"><span data-stu-id="a155c-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="a155c-126">将 `Flags` 字段设置为一个或多个[COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md)枚举的值，以指定要设置[COR_GC_STATS](cor-gc-stats-structure.md)结构中的哪些统计信息。</span><span class="sxs-lookup"><span data-stu-id="a155c-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="a155c-127">用法的示例如下所示：</span><span class="sxs-lookup"><span data-stu-id="a155c-127">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="a155c-128">要求</span><span class="sxs-lookup"><span data-stu-id="a155c-128">Requirements</span></span>  
 <span data-ttu-id="a155c-129">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a155c-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a155c-130">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a155c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a155c-131">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="a155c-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a155c-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a155c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a155c-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a155c-133">See also</span></span>

- [<span data-ttu-id="a155c-134">自动内存管理</span><span class="sxs-lookup"><span data-stu-id="a155c-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="a155c-135">COR_GC_STATS 结构</span><span class="sxs-lookup"><span data-stu-id="a155c-135">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="a155c-136">COR_GC_STAT_TYPES 枚举</span><span class="sxs-lookup"><span data-stu-id="a155c-136">COR_GC_STAT_TYPES Enumeration</span></span>](cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="a155c-137">垃圾回收</span><span class="sxs-lookup"><span data-stu-id="a155c-137">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="a155c-138">ICLRControl 接口</span><span class="sxs-lookup"><span data-stu-id="a155c-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="a155c-139">ICLRGCManager 接口</span><span class="sxs-lookup"><span data-stu-id="a155c-139">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="a155c-140">CLR 承载接口</span><span class="sxs-lookup"><span data-stu-id="a155c-140">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="a155c-141">承载接口</span><span class="sxs-lookup"><span data-stu-id="a155c-141">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="a155c-142">承载</span><span class="sxs-lookup"><span data-stu-id="a155c-142">Hosting</span></span>](index.md)
