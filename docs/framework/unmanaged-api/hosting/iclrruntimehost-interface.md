---
title: ICLRRuntimeHost 接口
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
ms.openlocfilehash: 72caac0aafe7f9c5919057a6ad2565258aec6a50
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504065"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="32fbb-102">ICLRRuntimeHost 接口</span><span class="sxs-lookup"><span data-stu-id="32fbb-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="32fbb-103">提供与 .NET Framework 版本1中提供的[ICorRuntimeHost](icorruntimehost-interface.md)接口类似的功能，其中包含以下更改：</span><span class="sxs-lookup"><span data-stu-id="32fbb-103">Provides functionality similar to that of the [ICorRuntimeHost](icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="32fbb-104">用于设置宿主控件接口的[SetHostControl](iclrruntimehost-sethostcontrol-method.md)方法的添加。</span><span class="sxs-lookup"><span data-stu-id="32fbb-104">The addition of the [SetHostControl](iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="32fbb-105">省略提供的某些方法 `ICorRuntimeHost` 。</span><span class="sxs-lookup"><span data-stu-id="32fbb-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="32fbb-106">方法</span><span class="sxs-lookup"><span data-stu-id="32fbb-106">Methods</span></span>  
  
|<span data-ttu-id="32fbb-107">方法</span><span class="sxs-lookup"><span data-stu-id="32fbb-107">Method</span></span>|<span data-ttu-id="32fbb-108">说明</span><span class="sxs-lookup"><span data-stu-id="32fbb-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="32fbb-109">ExecuteApplication 方法</span><span class="sxs-lookup"><span data-stu-id="32fbb-109">ExecuteApplication Method</span></span>](iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="32fbb-110">在基于清单的 ClickOnce 部署方案中用于指定要在新域中激活的应用程序。</span><span class="sxs-lookup"><span data-stu-id="32fbb-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="32fbb-111">ExecuteInAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="32fbb-111">ExecuteInAppDomain Method</span></span>](iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="32fbb-112">指定 <xref:System.AppDomain> 要在其中执行指定的托管代码的。</span><span class="sxs-lookup"><span data-stu-id="32fbb-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="32fbb-113">ExecuteInDefaultAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="32fbb-113">ExecuteInDefaultAppDomain Method</span></span>](iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="32fbb-114">在指定的程序集中调用指定类型的指定方法。</span><span class="sxs-lookup"><span data-stu-id="32fbb-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="32fbb-115">GetCLRControl 方法</span><span class="sxs-lookup"><span data-stu-id="32fbb-115">GetCLRControl Method</span></span>](iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="32fbb-116">获取宿主可用于自定义公共语言运行时（CLR）的各个方面的[ICLRControl](iclrcontrol-interface.md)类型的接口指针。</span><span class="sxs-lookup"><span data-stu-id="32fbb-116">Gets an interface pointer of type [ICLRControl](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="32fbb-117">GetCurrentAppDomainId 方法</span><span class="sxs-lookup"><span data-stu-id="32fbb-117">GetCurrentAppDomainId Method</span></span>](iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="32fbb-118">获取当前正在执行的的数值标识符 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="32fbb-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="32fbb-119">SetHostControl 方法</span><span class="sxs-lookup"><span data-stu-id="32fbb-119">SetHostControl Method</span></span>](iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="32fbb-120">设置宿主控件接口。</span><span class="sxs-lookup"><span data-stu-id="32fbb-120">Sets the host control interface.</span></span> <span data-ttu-id="32fbb-121">`SetHostControl`调用之前必须调用 `Start` 。</span><span class="sxs-lookup"><span data-stu-id="32fbb-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="32fbb-122">Start 方法</span><span class="sxs-lookup"><span data-stu-id="32fbb-122">Start Method</span></span>](iclrruntimehost-start-method.md)|<span data-ttu-id="32fbb-123">将 CLR 初始化为一个进程。</span><span class="sxs-lookup"><span data-stu-id="32fbb-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="32fbb-124">Stop 方法</span><span class="sxs-lookup"><span data-stu-id="32fbb-124">Stop Method</span></span>](iclrruntimehost-stop-method.md)|<span data-ttu-id="32fbb-125">停止由运行时执行的代码。</span><span class="sxs-lookup"><span data-stu-id="32fbb-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="32fbb-126">UnloadAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="32fbb-126">UnloadAppDomain Method</span></span>](iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="32fbb-127">卸载 <xref:System.AppDomain> 对应于指定数值标识符的。</span><span class="sxs-lookup"><span data-stu-id="32fbb-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32fbb-128">注解</span><span class="sxs-lookup"><span data-stu-id="32fbb-128">Remarks</span></span>  
 <span data-ttu-id="32fbb-129">从 .NET Framework 4 开始，使用[ICLRMetaHost](iclrmetahost-interface.md)接口获取指向[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)接口的指针，然后调用[ICLRRuntimeInfo：： GetInterface](iclrruntimeinfo-getinterface-method.md)方法以获取指向的指针 `ICLRRuntimeHost` 。</span><span class="sxs-lookup"><span data-stu-id="32fbb-129">Starting with the .NET Framework 4, use the [ICLRMetaHost](iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="32fbb-130">在 .NET Framework 的早期版本中，主机 `ICLRRuntimeHost` 通过调用[CorBindToRuntimeEx](corbindtoruntimeex-function.md)或[CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)获取指向实例的指针。</span><span class="sxs-lookup"><span data-stu-id="32fbb-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="32fbb-131">若要提供 .NET Framework 版本2.0 中提供的任何技术的实现，必须使用 `ICLRRuntimeHost` 而不是 `ICorRuntimeHost` 。</span><span class="sxs-lookup"><span data-stu-id="32fbb-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="32fbb-132">请不要在调用[ExecuteApplication](iclrruntimehost-executeapplication-method.md)方法之前调用[Start](iclrruntimehost-start-method.md)方法来激活基于清单的应用程序。</span><span class="sxs-lookup"><span data-stu-id="32fbb-132">Do not call the [Start](iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="32fbb-133">如果 `Start` 首先调用方法， `ExecuteApplication` 方法调用将失败。</span><span class="sxs-lookup"><span data-stu-id="32fbb-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32fbb-134">要求</span><span class="sxs-lookup"><span data-stu-id="32fbb-134">Requirements</span></span>  
 <span data-ttu-id="32fbb-135">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="32fbb-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32fbb-136">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="32fbb-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="32fbb-137">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="32fbb-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32fbb-138">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32fbb-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32fbb-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32fbb-139">See also</span></span>

- [<span data-ttu-id="32fbb-140">CorBindToCurrentRuntime 函数</span><span class="sxs-lookup"><span data-stu-id="32fbb-140">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="32fbb-141">CorBindToRuntimeEx 函数</span><span class="sxs-lookup"><span data-stu-id="32fbb-141">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="32fbb-142">ICLRControl 接口</span><span class="sxs-lookup"><span data-stu-id="32fbb-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="32fbb-143">ICorRuntimeHost 接口</span><span class="sxs-lookup"><span data-stu-id="32fbb-143">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="32fbb-144">承载接口</span><span class="sxs-lookup"><span data-stu-id="32fbb-144">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="32fbb-145">CLRRuntimeHost 组件类</span><span class="sxs-lookup"><span data-stu-id="32fbb-145">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
