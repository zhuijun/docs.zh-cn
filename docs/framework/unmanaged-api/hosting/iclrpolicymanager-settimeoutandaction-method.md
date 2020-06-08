---
title: ICLRPolicyManager::SetTimeoutAndAction 方法
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeoutAndAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type:
- apiref
ms.openlocfilehash: 02e836601be72d54f561e077cd3c466470bafb25
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504090"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="8467e-102">ICLRPolicyManager::SetTimeoutAndAction 方法</span><span class="sxs-lookup"><span data-stu-id="8467e-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="8467e-103">设置指定操作的超时值，并指定操作发生时公共语言运行时（CLR）应执行的策略操作。</span><span class="sxs-lookup"><span data-stu-id="8467e-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8467e-104">语法</span><span class="sxs-lookup"><span data-stu-id="8467e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8467e-105">参数</span><span class="sxs-lookup"><span data-stu-id="8467e-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="8467e-106">中[EClrOperation](eclroperation-enumeration.md)值之一，指示要设置超时和策略的操作 `action` 。</span><span class="sxs-lookup"><span data-stu-id="8467e-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="8467e-107">支持以下值：</span><span class="sxs-lookup"><span data-stu-id="8467e-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="8467e-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="8467e-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="8467e-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="8467e-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="8467e-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="8467e-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="8467e-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="8467e-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="8467e-112">中新的超时值（以毫秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="8467e-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="8467e-113">如果值为 "无限" `operation` ，则永远不会超时。</span><span class="sxs-lookup"><span data-stu-id="8467e-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="8467e-114">中[EPolicyAction](epolicyaction-enumeration.md)值之一，指示发生时 CLR 应执行的策略操作 `operation` 。</span><span class="sxs-lookup"><span data-stu-id="8467e-114">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8467e-115">返回值</span><span class="sxs-lookup"><span data-stu-id="8467e-115">Return Value</span></span>  
  
|<span data-ttu-id="8467e-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8467e-116">HRESULT</span></span>|<span data-ttu-id="8467e-117">说明</span><span class="sxs-lookup"><span data-stu-id="8467e-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8467e-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="8467e-118">S_OK</span></span>|<span data-ttu-id="8467e-119">`SetTimeoutAndAction`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="8467e-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="8467e-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8467e-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8467e-121">CLR 未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="8467e-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8467e-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8467e-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8467e-123">调用超时。</span><span class="sxs-lookup"><span data-stu-id="8467e-123">The call timed out.</span></span>|  
|<span data-ttu-id="8467e-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8467e-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8467e-125">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="8467e-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8467e-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8467e-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8467e-127">已阻止的线程或纤程正在等待某个事件时，该事件被取消。</span><span class="sxs-lookup"><span data-stu-id="8467e-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8467e-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8467e-128">E_FAIL</span></span>|<span data-ttu-id="8467e-129">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="8467e-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8467e-130">方法返回 E_FAIL 后，CLR 在该进程内将不再可用。</span><span class="sxs-lookup"><span data-stu-id="8467e-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8467e-131">对宿主方法的后续调用会返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8467e-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8467e-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8467e-132">E_INVALIDARG</span></span>|<span data-ttu-id="8467e-133">无法为指定的设置超时 `operation` ，或者为提供的值无效 `action` 。</span><span class="sxs-lookup"><span data-stu-id="8467e-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8467e-134">注解</span><span class="sxs-lookup"><span data-stu-id="8467e-134">Remarks</span></span>  
 <span data-ttu-id="8467e-135">`SetTimeoutAndAction`封装了[ICLRPolicyManager：： SetTimeout](iclrpolicymanager-settimeout-method.md)和[ICLRPolicyManager：： SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md)方法的功能，可调用这些方法来代替对这两个方法的顺序调用。</span><span class="sxs-lookup"><span data-stu-id="8467e-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8467e-136">并非所有策略操作值都可以指定为 CLR 操作的超时行为。</span><span class="sxs-lookup"><span data-stu-id="8467e-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="8467e-137">有关有效值，请参阅主题的 "备注" 部分。</span><span class="sxs-lookup"><span data-stu-id="8467e-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8467e-138">要求</span><span class="sxs-lookup"><span data-stu-id="8467e-138">Requirements</span></span>  
 <span data-ttu-id="8467e-139">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8467e-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8467e-140">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8467e-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8467e-141">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="8467e-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8467e-142">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8467e-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8467e-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8467e-143">See also</span></span>

- [<span data-ttu-id="8467e-144">EClrOperation 枚举</span><span class="sxs-lookup"><span data-stu-id="8467e-144">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="8467e-145">EPolicyAction 枚举</span><span class="sxs-lookup"><span data-stu-id="8467e-145">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="8467e-146">ICLRPolicyManager 接口</span><span class="sxs-lookup"><span data-stu-id="8467e-146">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="8467e-147">SetActionOnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="8467e-147">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="8467e-148">ICLRPolicyManager：： SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="8467e-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](iclrpolicymanager-settimeoutandaction-method.md)
