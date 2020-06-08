---
title: ICLRPolicyManager::SetActionOnFailure 方法
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
ms.openlocfilehash: 727cd82226b9a59c4879ffea5e87f93dd5fe38c9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504103"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="29e8b-102">ICLRPolicyManager::SetActionOnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="29e8b-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>
<span data-ttu-id="29e8b-103">指定发生指定的故障时公共语言运行时（CLR）应执行的策略操作。</span><span class="sxs-lookup"><span data-stu-id="29e8b-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29e8b-104">语法</span><span class="sxs-lookup"><span data-stu-id="29e8b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29e8b-105">参数</span><span class="sxs-lookup"><span data-stu-id="29e8b-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="29e8b-106">中[EClrFailure](eclrfailure-enumeration.md)值之一，指示要采取措施的故障类型。</span><span class="sxs-lookup"><span data-stu-id="29e8b-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="29e8b-107">中[EPolicyAction](epolicyaction-enumeration.md)值之一，指示发生失败时要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="29e8b-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="29e8b-108">有关支持的值的列表，请参阅 "备注" 部分。</span><span class="sxs-lookup"><span data-stu-id="29e8b-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29e8b-109">返回值</span><span class="sxs-lookup"><span data-stu-id="29e8b-109">Return Value</span></span>  
  
|<span data-ttu-id="29e8b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29e8b-110">HRESULT</span></span>|<span data-ttu-id="29e8b-111">说明</span><span class="sxs-lookup"><span data-stu-id="29e8b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="29e8b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="29e8b-112">S_OK</span></span>|<span data-ttu-id="29e8b-113">`SetActionOnFailure`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="29e8b-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="29e8b-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="29e8b-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="29e8b-115">CLR 未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="29e8b-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="29e8b-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="29e8b-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="29e8b-117">调用超时。</span><span class="sxs-lookup"><span data-stu-id="29e8b-117">The call timed out.</span></span>|  
|<span data-ttu-id="29e8b-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="29e8b-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="29e8b-119">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="29e8b-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="29e8b-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="29e8b-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="29e8b-121">已阻止的线程或纤程正在等待某个事件时，该事件被取消。</span><span class="sxs-lookup"><span data-stu-id="29e8b-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="29e8b-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="29e8b-122">E_FAIL</span></span>|<span data-ttu-id="29e8b-123">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="29e8b-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="29e8b-124">方法返回 E_FAIL 后，CLR 在该进程内将不再可用。</span><span class="sxs-lookup"><span data-stu-id="29e8b-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="29e8b-125">对宿主方法的后续调用会返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="29e8b-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="29e8b-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="29e8b-126">E_INVALIDARG</span></span>|<span data-ttu-id="29e8b-127">无法为指定的操作设置策略操作，或者为该操作指定了无效的策略操作。</span><span class="sxs-lookup"><span data-stu-id="29e8b-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29e8b-128">注解</span><span class="sxs-lookup"><span data-stu-id="29e8b-128">Remarks</span></span>  
 <span data-ttu-id="29e8b-129">默认情况下，CLR 在无法分配内存等资源时引发异常。</span><span class="sxs-lookup"><span data-stu-id="29e8b-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="29e8b-130">`SetActionOnFailure`允许主机通过指定在失败时要执行的策略操作来重写此行为。</span><span class="sxs-lookup"><span data-stu-id="29e8b-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="29e8b-131">下表显示了支持的[EClrFailure](eclrfailure-enumeration.md)和[EPolicyAction](epolicyaction-enumeration.md)值的组合。</span><span class="sxs-lookup"><span data-stu-id="29e8b-131">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="29e8b-132">（ [EClrFailure](eclrfailure-enumeration.md)值中省略了 FAIL_ 前缀。）</span><span class="sxs-lookup"><span data-stu-id="29e8b-132">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="29e8b-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="29e8b-133">NonCriticalResource</span></span>|<span data-ttu-id="29e8b-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="29e8b-134">CriticalResource</span></span>|<span data-ttu-id="29e8b-135">FatalRuntime</span><span class="sxs-lookup"><span data-stu-id="29e8b-135">FatalRuntime</span></span>|<span data-ttu-id="29e8b-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="29e8b-136">OrphanedLock</span></span>|<span data-ttu-id="29e8b-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="29e8b-137">StackOverflow</span></span>|<span data-ttu-id="29e8b-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="29e8b-138">AccessViolation</span></span>|<span data-ttu-id="29e8b-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="29e8b-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="29e8b-140">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-140">X</span></span>|<span data-ttu-id="29e8b-141">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-141">X</span></span>||||<span data-ttu-id="29e8b-142">空值</span><span class="sxs-lookup"><span data-stu-id="29e8b-142">N/A</span></span>||  
|<span data-ttu-id="29e8b-143">eThrowException</span><span class="sxs-lookup"><span data-stu-id="29e8b-143">eThrowException</span></span>|<span data-ttu-id="29e8b-144">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-144">X</span></span>|<span data-ttu-id="29e8b-145">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-145">X</span></span>||||<span data-ttu-id="29e8b-146">空值</span><span class="sxs-lookup"><span data-stu-id="29e8b-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="29e8b-147">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-147">X</span></span>|<span data-ttu-id="29e8b-148">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-148">X</span></span>||||<span data-ttu-id="29e8b-149">空值</span><span class="sxs-lookup"><span data-stu-id="29e8b-149">N/A</span></span>|<span data-ttu-id="29e8b-150">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="29e8b-151">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-151">X</span></span>|<span data-ttu-id="29e8b-152">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-152">X</span></span>||||<span data-ttu-id="29e8b-153">空值</span><span class="sxs-lookup"><span data-stu-id="29e8b-153">N/A</span></span>|<span data-ttu-id="29e8b-154">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="29e8b-155">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-155">X</span></span>|<span data-ttu-id="29e8b-156">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-156">X</span></span>||<span data-ttu-id="29e8b-157">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-157">X</span></span>||<span data-ttu-id="29e8b-158">空值</span><span class="sxs-lookup"><span data-stu-id="29e8b-158">N/A</span></span>|<span data-ttu-id="29e8b-159">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="29e8b-160">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-160">X</span></span>|<span data-ttu-id="29e8b-161">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-161">X</span></span>||<span data-ttu-id="29e8b-162">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-162">X</span></span>|<span data-ttu-id="29e8b-163">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-163">X</span></span>|<span data-ttu-id="29e8b-164">空值</span><span class="sxs-lookup"><span data-stu-id="29e8b-164">N/A</span></span>|<span data-ttu-id="29e8b-165">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="29e8b-166">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-166">X</span></span>|<span data-ttu-id="29e8b-167">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-167">X</span></span>||<span data-ttu-id="29e8b-168">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-168">X</span></span>|<span data-ttu-id="29e8b-169">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-169">X</span></span>|<span data-ttu-id="29e8b-170">空值</span><span class="sxs-lookup"><span data-stu-id="29e8b-170">N/A</span></span>|<span data-ttu-id="29e8b-171">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-171">X</span></span>|  
|<span data-ttu-id="29e8b-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="29e8b-172">eFastExitProcess</span></span>|<span data-ttu-id="29e8b-173">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-173">X</span></span>|<span data-ttu-id="29e8b-174">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-174">X</span></span>||<span data-ttu-id="29e8b-175">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-175">X</span></span>|<span data-ttu-id="29e8b-176">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-176">X</span></span>|<span data-ttu-id="29e8b-177">空值</span><span class="sxs-lookup"><span data-stu-id="29e8b-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="29e8b-178">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-178">X</span></span>|<span data-ttu-id="29e8b-179">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-179">X</span></span>|<span data-ttu-id="29e8b-180">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-180">X</span></span>|<span data-ttu-id="29e8b-181">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-181">X</span></span>|<span data-ttu-id="29e8b-182">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-182">X</span></span>|<span data-ttu-id="29e8b-183">空值</span><span class="sxs-lookup"><span data-stu-id="29e8b-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="29e8b-184">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-184">X</span></span>|<span data-ttu-id="29e8b-185">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-185">X</span></span>|<span data-ttu-id="29e8b-186">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-186">X</span></span>|<span data-ttu-id="29e8b-187">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-187">X</span></span>|<span data-ttu-id="29e8b-188">X</span><span class="sxs-lookup"><span data-stu-id="29e8b-188">X</span></span>|<span data-ttu-id="29e8b-189">空值</span><span class="sxs-lookup"><span data-stu-id="29e8b-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="29e8b-190">要求</span><span class="sxs-lookup"><span data-stu-id="29e8b-190">Requirements</span></span>  
 <span data-ttu-id="29e8b-191">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29e8b-191">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29e8b-192">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="29e8b-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="29e8b-193">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="29e8b-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29e8b-194">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29e8b-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29e8b-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29e8b-195">See also</span></span>

- [<span data-ttu-id="29e8b-196">EClrFailure 枚举</span><span class="sxs-lookup"><span data-stu-id="29e8b-196">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="29e8b-197">EPolicyAction 枚举</span><span class="sxs-lookup"><span data-stu-id="29e8b-197">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="29e8b-198">ICLRControl 接口</span><span class="sxs-lookup"><span data-stu-id="29e8b-198">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="29e8b-199">ICLRPolicyManager 接口</span><span class="sxs-lookup"><span data-stu-id="29e8b-199">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
