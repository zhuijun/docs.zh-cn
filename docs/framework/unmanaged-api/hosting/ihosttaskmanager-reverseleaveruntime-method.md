---
title: IHostTaskManager::ReverseLeaveRuntime 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseLeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type:
- apiref
ms.openlocfilehash: ea352b189d65e0be6a2bbc81c19a03d1edd8143d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554796"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="648b2-102">IHostTaskManager::ReverseLeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="648b2-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="648b2-103">向宿主通知控制是否正在离开公共语言运行时 (CLR) 并输入从托管代码调用的非托管函数。</span><span class="sxs-lookup"><span data-stu-id="648b2-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="648b2-104">语法</span><span class="sxs-lookup"><span data-stu-id="648b2-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="648b2-105">返回值</span><span class="sxs-lookup"><span data-stu-id="648b2-105">Return Value</span></span>  
  
|<span data-ttu-id="648b2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="648b2-106">HRESULT</span></span>|<span data-ttu-id="648b2-107">说明</span><span class="sxs-lookup"><span data-stu-id="648b2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="648b2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="648b2-108">S_OK</span></span>|<span data-ttu-id="648b2-109">`ReverseLeaveRuntime` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="648b2-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="648b2-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="648b2-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="648b2-111">CLR 未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="648b2-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="648b2-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="648b2-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="648b2-113">调用超时。</span><span class="sxs-lookup"><span data-stu-id="648b2-113">The call timed out.</span></span>|  
|<span data-ttu-id="648b2-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="648b2-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="648b2-115">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="648b2-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="648b2-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="648b2-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="648b2-117">已阻止的线程或纤程正在等待某个事件时，该事件被取消。</span><span class="sxs-lookup"><span data-stu-id="648b2-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="648b2-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="648b2-118">E_FAIL</span></span>|<span data-ttu-id="648b2-119">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="648b2-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="648b2-120">当方法返回 E_FAIL 时，CLR 在该进程内将不再可用。</span><span class="sxs-lookup"><span data-stu-id="648b2-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="648b2-121">对宿主方法的后续调用会返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="648b2-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="648b2-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="648b2-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="648b2-123">没有足够的内存可用来完成请求的资源分配。</span><span class="sxs-lookup"><span data-stu-id="648b2-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="648b2-124">备注</span><span class="sxs-lookup"><span data-stu-id="648b2-124">Remarks</span></span>  
 <span data-ttu-id="648b2-125">CLR 调用 `ReverseLeaveRuntime` 以通知宿主当前正在执行的任务正在将控制权返回给非托管函数，而该函数又通过平台调用从托管代码调用。</span><span class="sxs-lookup"><span data-stu-id="648b2-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="648b2-126">对的每个调用都 `ReverseLeaveRuntime` 匹配对 [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md)的相应调用。</span><span class="sxs-lookup"><span data-stu-id="648b2-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="648b2-127">要求</span><span class="sxs-lookup"><span data-stu-id="648b2-127">Requirements</span></span>  
 <span data-ttu-id="648b2-128">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="648b2-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="648b2-129">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="648b2-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="648b2-130">**库：** 作为中的资源包含 MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="648b2-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="648b2-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="648b2-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="648b2-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="648b2-132">See also</span></span>

- [<span data-ttu-id="648b2-133">CallNeedsHostHook 方法</span><span class="sxs-lookup"><span data-stu-id="648b2-133">CallNeedsHostHook Method</span></span>](ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="648b2-134">EnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="648b2-134">EnterRuntime Method</span></span>](ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="648b2-135">ICLRTask 接口</span><span class="sxs-lookup"><span data-stu-id="648b2-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="648b2-136">ICLRTaskManager 接口</span><span class="sxs-lookup"><span data-stu-id="648b2-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="648b2-137">IHostTask 接口</span><span class="sxs-lookup"><span data-stu-id="648b2-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="648b2-138">IHostTaskManager 接口</span><span class="sxs-lookup"><span data-stu-id="648b2-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="648b2-139">LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="648b2-139">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
- <span data-ttu-id="648b2-140">[平台调用详解](/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="648b2-140">[A Closer Look at Platform Invoke](/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span></span>
