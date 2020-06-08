---
title: ICLROnEventManager::UnregisterActionOnEvent 方法
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.UnregisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::UnregisterActionOnEvent
helpviewer_keywords:
- UnRegisterActionOnEvent method [.NET Framework hosting]
- ICLROnEventManager::UnRegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: 4c02ec37-cdf0-46b2-890e-235092741236
topic_type:
- apiref
ms.openlocfilehash: a3018d8477d5abd7d03ad8675503624d2e44e8f4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504129"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="2fa43-102">ICLROnEventManager::UnregisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="2fa43-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="2fa43-103">为指定的事件注销先前注册的回调指针。</span><span class="sxs-lookup"><span data-stu-id="2fa43-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fa43-104">语法</span><span class="sxs-lookup"><span data-stu-id="2fa43-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fa43-105">参数</span><span class="sxs-lookup"><span data-stu-id="2fa43-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="2fa43-106">中[EClrEvent](eclrevent-enumeration.md)值之一，指示要撤消注册的回调指针的事件 `pAction` 。</span><span class="sxs-lookup"><span data-stu-id="2fa43-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="2fa43-107">中指向作为参数传递给[RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md)方法的[IActionOnCLREvent](iactiononclrevent-interface.md)对象的指针。</span><span class="sxs-lookup"><span data-stu-id="2fa43-107">[in] A pointer to an [IActionOnCLREvent](iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2fa43-108">返回值</span><span class="sxs-lookup"><span data-stu-id="2fa43-108">Return Value</span></span>  
  
|<span data-ttu-id="2fa43-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2fa43-109">HRESULT</span></span>|<span data-ttu-id="2fa43-110">说明</span><span class="sxs-lookup"><span data-stu-id="2fa43-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2fa43-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2fa43-111">S_OK</span></span>|<span data-ttu-id="2fa43-112">`UnregisterActionOnEvent`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="2fa43-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="2fa43-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2fa43-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2fa43-114">公共语言运行时（CLR）未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="2fa43-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2fa43-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2fa43-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2fa43-116">调用超时。</span><span class="sxs-lookup"><span data-stu-id="2fa43-116">The call timed out.</span></span>|  
|<span data-ttu-id="2fa43-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2fa43-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2fa43-118">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="2fa43-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2fa43-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2fa43-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2fa43-120">已阻止的线程或纤程正在等待某个事件时，该事件被取消。</span><span class="sxs-lookup"><span data-stu-id="2fa43-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2fa43-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2fa43-121">E_FAIL</span></span>|<span data-ttu-id="2fa43-122">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="2fa43-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2fa43-123">方法返回 E_FAIL 后，CLR 在该进程内将不再可用。</span><span class="sxs-lookup"><span data-stu-id="2fa43-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2fa43-124">对宿主方法的后续调用会返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2fa43-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2fa43-125">要求</span><span class="sxs-lookup"><span data-stu-id="2fa43-125">Requirements</span></span>  
 <span data-ttu-id="2fa43-126">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2fa43-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fa43-127">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="2fa43-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2fa43-128">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="2fa43-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2fa43-129">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fa43-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fa43-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2fa43-130">See also</span></span>

- [<span data-ttu-id="2fa43-131">EClrEvent 枚举</span><span class="sxs-lookup"><span data-stu-id="2fa43-131">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="2fa43-132">IActionOnCLREvent 接口</span><span class="sxs-lookup"><span data-stu-id="2fa43-132">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="2fa43-133">ICLRControl 接口</span><span class="sxs-lookup"><span data-stu-id="2fa43-133">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="2fa43-134">ICLROnEventManager 接口</span><span class="sxs-lookup"><span data-stu-id="2fa43-134">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
