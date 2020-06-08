---
title: EPolicyAction 枚举
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
ms.openlocfilehash: 901c62e6f2519fc4f9251f348c77b11bbe0992be
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504340"
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="f2020-102">EPolicyAction 枚举</span><span class="sxs-lookup"><span data-stu-id="f2020-102">EPolicyAction Enumeration</span></span>
<span data-ttu-id="f2020-103">描述主机可为[EClrOperation](eclroperation-enumeration.md)描述的操作设置的策略操作以及[EClrFailure](eclrfailure-enumeration.md)描述的故障。</span><span class="sxs-lookup"><span data-stu-id="f2020-103">Describes the policy actions the host can set for operations described by [EClrOperation](eclroperation-enumeration.md) and failures described by [EClrFailure](eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2020-104">语法</span><span class="sxs-lookup"><span data-stu-id="f2020-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a><span data-ttu-id="f2020-105">成员</span><span class="sxs-lookup"><span data-stu-id="f2020-105">Members</span></span>  
  
|<span data-ttu-id="f2020-106">成员</span><span class="sxs-lookup"><span data-stu-id="f2020-106">Member</span></span>|<span data-ttu-id="f2020-107">描述</span><span class="sxs-lookup"><span data-stu-id="f2020-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="f2020-108">指定公共语言运行时（CLR）应正常中止线程。</span><span class="sxs-lookup"><span data-stu-id="f2020-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="f2020-109">正常中止包括尝试运行所有 `finally` 块、 `catch` 与线程中止相关的任何块和终结器。</span><span class="sxs-lookup"><span data-stu-id="f2020-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="f2020-110">指定 CLR 应进入禁用状态。</span><span class="sxs-lookup"><span data-stu-id="f2020-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="f2020-111">在受影响的进程中，不能再执行其他托管代码，并且阻止线程进入 CLR。</span><span class="sxs-lookup"><span data-stu-id="f2020-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="f2020-112">指定 CLR 应尝试正常退出进程，包括运行终结器并执行清理和日志记录操作。</span><span class="sxs-lookup"><span data-stu-id="f2020-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="f2020-113">指定 CLR 应立即退出进程，而无需运行终结器或执行清理和日志记录操作。</span><span class="sxs-lookup"><span data-stu-id="f2020-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="f2020-114">但是，通知将发送到调试器。</span><span class="sxs-lookup"><span data-stu-id="f2020-114">However, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="f2020-115">指定不执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="f2020-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="f2020-116">指定 CLR 应执行强制的线程中止。</span><span class="sxs-lookup"><span data-stu-id="f2020-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="f2020-117">只 `catch` `finally` 会执行标记为的和块 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="f2020-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="f2020-118">指定 CLR 应退出进程，而不运行终结器或日志记录操作。</span><span class="sxs-lookup"><span data-stu-id="f2020-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="f2020-119">指定 CLR 应执行的强制卸载 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="f2020-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="f2020-120">仅执行标记为的终结器 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="f2020-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="f2020-121">同样，在其堆栈中具有此类的所有线程都 <xref:System.AppDomain> 将接收 `ThreadAbortException` ，但仅 `catch` 执行标记为的和 `finally` 块 <xref:System.EnterpriseServices.MustRunInClientContextAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="f2020-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="f2020-122">指定应引发适用于条件的异常，例如内存不足、缓冲区溢出，等等。</span><span class="sxs-lookup"><span data-stu-id="f2020-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="f2020-123">指定 <xref:System.AppDomain> 应卸载。</span><span class="sxs-lookup"><span data-stu-id="f2020-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="f2020-124">CLR 尝试运行终结器。</span><span class="sxs-lookup"><span data-stu-id="f2020-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2020-125">注解</span><span class="sxs-lookup"><span data-stu-id="f2020-125">Remarks</span></span>  
 <span data-ttu-id="f2020-126">宿主通过调用[ICLRPolicyManager](iclrpolicymanager-interface.md)接口的方法来设置策略操作。</span><span class="sxs-lookup"><span data-stu-id="f2020-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="f2020-127">有关 "强制" 和 "正常中止" 的信息，请参阅[EClrOperation](eclroperation-enumeration.md)枚举。</span><span class="sxs-lookup"><span data-stu-id="f2020-127">For information about rude and graceful aborts, see the [EClrOperation](eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2020-128">要求</span><span class="sxs-lookup"><span data-stu-id="f2020-128">Requirements</span></span>  
 <span data-ttu-id="f2020-129">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f2020-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2020-130">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f2020-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f2020-131">**库：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f2020-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2020-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2020-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2020-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f2020-133">See also</span></span>

- [<span data-ttu-id="f2020-134">EClrFailure 枚举</span><span class="sxs-lookup"><span data-stu-id="f2020-134">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="f2020-135">ICLRPolicyManager 接口</span><span class="sxs-lookup"><span data-stu-id="f2020-135">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="f2020-136">IHostPolicyManager 接口</span><span class="sxs-lookup"><span data-stu-id="f2020-136">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="f2020-137">承载枚举</span><span class="sxs-lookup"><span data-stu-id="f2020-137">Hosting Enumerations</span></span>](hosting-enumerations.md)
