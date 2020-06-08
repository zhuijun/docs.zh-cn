---
title: IHostPolicyManager 接口
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
ms.openlocfilehash: d6b34403a45cc40863d79b59396041e496989045
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503921"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="620ec-102">IHostPolicyManager 接口</span><span class="sxs-lookup"><span data-stu-id="620ec-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="620ec-103">提供一些方法，这些方法可通知宿主公共语言运行时（CLR）在中止、超时或失败时所执行的操作。</span><span class="sxs-lookup"><span data-stu-id="620ec-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="620ec-104">方法</span><span class="sxs-lookup"><span data-stu-id="620ec-104">Methods</span></span>  
  
|<span data-ttu-id="620ec-105">方法</span><span class="sxs-lookup"><span data-stu-id="620ec-105">Method</span></span>|<span data-ttu-id="620ec-106">说明</span><span class="sxs-lookup"><span data-stu-id="620ec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="620ec-107">OnDefaultAction 方法</span><span class="sxs-lookup"><span data-stu-id="620ec-107">OnDefaultAction Method</span></span>](ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="620ec-108">向宿主通知 CLR 将使用对[ICLRPolicyManager：： SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md)的调用指定的默认操作来响应线程中止或 <xref:System.AppDomain> 卸载。</span><span class="sxs-lookup"><span data-stu-id="620ec-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="620ec-109">OnFailure 方法</span><span class="sxs-lookup"><span data-stu-id="620ec-109">OnFailure Method</span></span>](ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="620ec-110">向宿主通知 CLR 即将获取调用[ICLRPolicyManager：： SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md)所指定的操作，以响应资源分配或回收失败。</span><span class="sxs-lookup"><span data-stu-id="620ec-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="620ec-111">OnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="620ec-111">OnTimeout Method</span></span>](ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="620ec-112">向宿主通知 CLR 即将使用对[ICLRPolicyManager：： SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md)的调用指定的操作来响应超时。</span><span class="sxs-lookup"><span data-stu-id="620ec-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="620ec-113">要求</span><span class="sxs-lookup"><span data-stu-id="620ec-113">Requirements</span></span>  
 <span data-ttu-id="620ec-114">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="620ec-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="620ec-115">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="620ec-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="620ec-116">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="620ec-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="620ec-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="620ec-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="620ec-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="620ec-118">See also</span></span>

- [<span data-ttu-id="620ec-119">EClrFailure 枚举</span><span class="sxs-lookup"><span data-stu-id="620ec-119">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="620ec-120">EClrOperation 枚举</span><span class="sxs-lookup"><span data-stu-id="620ec-120">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="620ec-121">EPolicyAction 枚举</span><span class="sxs-lookup"><span data-stu-id="620ec-121">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="620ec-122">ICLRPolicyManager 接口</span><span class="sxs-lookup"><span data-stu-id="620ec-122">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="620ec-123">承载接口</span><span class="sxs-lookup"><span data-stu-id="620ec-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
