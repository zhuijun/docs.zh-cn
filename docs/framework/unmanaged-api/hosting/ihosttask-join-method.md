---
title: IHostTask::Join 方法
ms.date: 03/30/2017
api_name:
- IHostTask.Join
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type:
- apiref
ms.openlocfilehash: 20919bd9889408821cf57817082e3c7d5cebc240
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503908"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="67e95-102">IHostTask::Join 方法</span><span class="sxs-lookup"><span data-stu-id="67e95-102">IHostTask::Join Method</span></span>
<span data-ttu-id="67e95-103">阻止调用任务，直到当前[IHostTask](ihosttask-interface.md)实例表示的任务完成，指定的时间间隔结束，或调用[IHostTask：： Alert](ihosttask-alert-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="67e95-103">Blocks the calling task until the task represented by the current [IHostTask](ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67e95-104">语法</span><span class="sxs-lookup"><span data-stu-id="67e95-104">Syntax</span></span>  
  
```cpp  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67e95-105">参数</span><span class="sxs-lookup"><span data-stu-id="67e95-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="67e95-106">中等待任务终止的时间间隔（以毫秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="67e95-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="67e95-107">如果此时间间隔在任务终止之前过期，则调用任务会取消阻止。</span><span class="sxs-lookup"><span data-stu-id="67e95-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="67e95-108">中[WAIT_OPTION](wait-option-enumeration.md)值之一。</span><span class="sxs-lookup"><span data-stu-id="67e95-108">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values.</span></span> <span data-ttu-id="67e95-109">如果在 `Alert` 过去之前调用，则值 WAIT_ALERTABLE 指示宿主唤醒任务 `milliseconds` 。</span><span class="sxs-lookup"><span data-stu-id="67e95-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67e95-110">返回值</span><span class="sxs-lookup"><span data-stu-id="67e95-110">Return Value</span></span>  
  
|<span data-ttu-id="67e95-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="67e95-111">HRESULT</span></span>|<span data-ttu-id="67e95-112">说明</span><span class="sxs-lookup"><span data-stu-id="67e95-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="67e95-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="67e95-113">S_OK</span></span>|<span data-ttu-id="67e95-114">`Join`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="67e95-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="67e95-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="67e95-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="67e95-116">公共语言运行时（CLR）未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="67e95-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="67e95-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="67e95-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="67e95-118">调用超时。</span><span class="sxs-lookup"><span data-stu-id="67e95-118">The call timed out.</span></span>|  
|<span data-ttu-id="67e95-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="67e95-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="67e95-120">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="67e95-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="67e95-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="67e95-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="67e95-122">已阻止的线程或纤程正在等待事件，或当前 `IHostTask` 实例未与任务关联时，已取消该事件。</span><span class="sxs-lookup"><span data-stu-id="67e95-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="67e95-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="67e95-123">E_FAIL</span></span>|<span data-ttu-id="67e95-124">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="67e95-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="67e95-125">当方法返回 E_FAIL 时，CLR 在该进程内将不再可用。</span><span class="sxs-lookup"><span data-stu-id="67e95-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="67e95-126">对宿主方法的后续调用会返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="67e95-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="67e95-127">要求</span><span class="sxs-lookup"><span data-stu-id="67e95-127">Requirements</span></span>  
 <span data-ttu-id="67e95-128">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67e95-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67e95-129">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="67e95-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="67e95-130">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="67e95-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="67e95-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67e95-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67e95-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67e95-132">See also</span></span>

- [<span data-ttu-id="67e95-133">ICLRTask 接口</span><span class="sxs-lookup"><span data-stu-id="67e95-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="67e95-134">ICLRTaskManager 接口</span><span class="sxs-lookup"><span data-stu-id="67e95-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="67e95-135">IHostTask 接口</span><span class="sxs-lookup"><span data-stu-id="67e95-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="67e95-136">IHostTaskManager 接口</span><span class="sxs-lookup"><span data-stu-id="67e95-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="67e95-137">WAIT_OPTION 枚举</span><span class="sxs-lookup"><span data-stu-id="67e95-137">WAIT_OPTION Enumeration</span></span>](wait-option-enumeration.md)
