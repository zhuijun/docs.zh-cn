---
title: ICorRuntimeHost 接口
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost
helpviewer_keywords:
- ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type:
- apiref
ms.openlocfilehash: 4b8018bb84dea08987d91f351b1ab0d9f3b48c56
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503895"
---
# <a name="icorruntimehost-interface"></a><span data-ttu-id="d6934-102">ICorRuntimeHost 接口</span><span class="sxs-lookup"><span data-stu-id="d6934-102">ICorRuntimeHost Interface</span></span>
<span data-ttu-id="d6934-103">提供使宿主能够显式启动和停止公共语言运行时（CLR）、创建和配置应用程序域、访问默认域以及枚举在进程中运行的所有域的方法。</span><span class="sxs-lookup"><span data-stu-id="d6934-103">Provides methods that enable the host to start and stop the common language runtime (CLR) explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>  
  
 <span data-ttu-id="d6934-104">在 .NET Framework 版本2.0 中，此接口由[ICLRRuntimeHost](iclrruntimehost-interface.md)取代。</span><span class="sxs-lookup"><span data-stu-id="d6934-104">In the .NET Framework version 2.0, this interface is superceded by [ICLRRuntimeHost](iclrruntimehost-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d6934-105">方法</span><span class="sxs-lookup"><span data-stu-id="d6934-105">Methods</span></span>  
  
|<span data-ttu-id="d6934-106">方法</span><span class="sxs-lookup"><span data-stu-id="d6934-106">Method</span></span>|<span data-ttu-id="d6934-107">说明</span><span class="sxs-lookup"><span data-stu-id="d6934-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d6934-108">CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-108">CloseEnum Method</span></span>](icorruntimehost-closeenum-method.md)|<span data-ttu-id="d6934-109">将域枚举器重置回域列表的开头。</span><span class="sxs-lookup"><span data-stu-id="d6934-109">Resets a domain enumerator back to the beginning of the domain list.</span></span>|  
|[<span data-ttu-id="d6934-110">CreateDomain 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-110">CreateDomain Method</span></span>](icorruntimehost-createdomain-method.md)|<span data-ttu-id="d6934-111">创建应用程序域。</span><span class="sxs-lookup"><span data-stu-id="d6934-111">Creates an application domain.</span></span> <span data-ttu-id="d6934-112">调用方接收类型为的实例的接口指针 <xref:System._AppDomain> <xref:System.AppDomain?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="d6934-112">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>|  
|[<span data-ttu-id="d6934-113">CreateDomainEx 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-113">CreateDomainEx Method</span></span>](icorruntimehost-createdomainex-method.md)|<span data-ttu-id="d6934-114">创建应用程序域。</span><span class="sxs-lookup"><span data-stu-id="d6934-114">Creates an application domain.</span></span> <span data-ttu-id="d6934-115">此方法允许调用方传递 IAppDomainSetup 实例，以配置返回的实例的附加功能 <xref:System._AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="d6934-115">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>|  
|[<span data-ttu-id="d6934-116">CreateDomainSetup 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-116">CreateDomainSetup Method</span></span>](icorruntimehost-createdomainsetup-method.md)|<span data-ttu-id="d6934-117">获取实例的类型的接口指针 `IAppDomainSetup` <xref:System.AppDomainSetup> 。</span><span class="sxs-lookup"><span data-stu-id="d6934-117">Gets an interface pointer of type `IAppDomainSetup` to an <xref:System.AppDomainSetup> instance.</span></span> <span data-ttu-id="d6934-118">`IAppDomainSetup`提供用于配置应用程序域在创建之前的各个方面的方法。</span><span class="sxs-lookup"><span data-stu-id="d6934-118">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>|  
|[<span data-ttu-id="d6934-119">CreateEvidence 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-119">CreateEvidence Method</span></span>](icorruntimehost-createevidence-method.md)|<span data-ttu-id="d6934-120">获取类型的接口指针 <xref:System.Security.Principal.IIdentity> ，该指针允许主机创建要传递给[CreateDomain](icorruntimehost-createdomain-method.md)或[CreateDomainEx](icorruntimehost-createdomainex-method.md)的安全证据。</span><span class="sxs-lookup"><span data-stu-id="d6934-120">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity>, which allows the host to create security evidence to pass to [CreateDomain](icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md).</span></span>|  
|[<span data-ttu-id="d6934-121">CreateLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-121">CreateLogicalThreadState Method</span></span>](icorruntimehost-createlogicalthreadstate-method.md)|<span data-ttu-id="d6934-122">请勿使用。</span><span class="sxs-lookup"><span data-stu-id="d6934-122">Do not use.</span></span>|  
|[<span data-ttu-id="d6934-123">CurrentDomain 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-123">CurrentDomain Method</span></span>](icorruntimehost-currentdomain-method.md)|<span data-ttu-id="d6934-124">获取类型的接口指针 <xref:System._AppDomain> ，该指针表示当前线程上加载的域。</span><span class="sxs-lookup"><span data-stu-id="d6934-124">Gets an interface pointer of type <xref:System._AppDomain> that represents the domain loaded on the current thread.</span></span>|  
|[<span data-ttu-id="d6934-125">DeleteLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-125">DeleteLogicalThreadState Method</span></span>](icorruntimehost-deletelogicalthreadstate-method.md)|<span data-ttu-id="d6934-126">请勿使用。</span><span class="sxs-lookup"><span data-stu-id="d6934-126">Do not use.</span></span>|  
|[<span data-ttu-id="d6934-127">EnumDomains 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-127">EnumDomains Method</span></span>](icorruntimehost-enumdomains-method.md)|<span data-ttu-id="d6934-128">获取当前进程中的域的枚举数。</span><span class="sxs-lookup"><span data-stu-id="d6934-128">Gets an enumerator for the domains in the current process.</span></span>|  
|[<span data-ttu-id="d6934-129">GetConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-129">GetConfiguration Method</span></span>](icorruntimehost-getconfiguration-method.md)|<span data-ttu-id="d6934-130">获取一个对象，该对象允许宿主指定 CLR 的回调配置。</span><span class="sxs-lookup"><span data-stu-id="d6934-130">Gets an object that allows the host to specify the callback configuration of the CLR.</span></span>|  
|[<span data-ttu-id="d6934-131">GetDefaultDomain 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-131">GetDefaultDomain Method</span></span>](icorruntimehost-getdefaultdomain-method.md)|<span data-ttu-id="d6934-132">获取类型的接口指针 <xref:System._AppDomain> ，该指针表示当前进程的默认域。</span><span class="sxs-lookup"><span data-stu-id="d6934-132">Gets an interface pointer of type <xref:System._AppDomain> that represents the default domain for the current process.</span></span>|  
|[<span data-ttu-id="d6934-133">LocksHeldByLogicalThread 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-133">LocksHeldByLogicalThread Method</span></span>](icorruntimehost-locksheldbylogicalthread-method.md)|<span data-ttu-id="d6934-134">请勿使用。</span><span class="sxs-lookup"><span data-stu-id="d6934-134">Do not use.</span></span>|  
|[<span data-ttu-id="d6934-135">MapFile 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-135">MapFile Method</span></span>](icorruntimehost-mapfile-method.md)|<span data-ttu-id="d6934-136">将指定的文件映射到内存。</span><span class="sxs-lookup"><span data-stu-id="d6934-136">Maps the specified file into memory.</span></span> <span data-ttu-id="d6934-137">此方法已过时。</span><span class="sxs-lookup"><span data-stu-id="d6934-137">This method is obsolete.</span></span>|  
|[<span data-ttu-id="d6934-138">NextDomain 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-138">NextDomain Method</span></span>](icorruntimehost-nextdomain-method.md)|<span data-ttu-id="d6934-139">获取一个接口指针，该指针指向枚举中的下一个域。</span><span class="sxs-lookup"><span data-stu-id="d6934-139">Gets an interface pointer to the next domain in the enumeration.</span></span>|  
|[<span data-ttu-id="d6934-140">Start 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-140">Start Method</span></span>](icorruntimehost-start-method.md)|<span data-ttu-id="d6934-141">启动 CLR。</span><span class="sxs-lookup"><span data-stu-id="d6934-141">Starts the CLR.</span></span>|  
|[<span data-ttu-id="d6934-142">Stop 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-142">Stop Method</span></span>](icorruntimehost-stop-method.md)|<span data-ttu-id="d6934-143">停止执行当前进程的运行时中的代码。</span><span class="sxs-lookup"><span data-stu-id="d6934-143">Stops the execution of code in the runtime for the current process.</span></span>|  
|[<span data-ttu-id="d6934-144">SwitchInLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-144">SwitchInLogicalThreadState Method</span></span>](icorruntimehost-switchinlogicalthreadstate-method.md)|<span data-ttu-id="d6934-145">请勿使用。</span><span class="sxs-lookup"><span data-stu-id="d6934-145">Do not use.</span></span>|  
|[<span data-ttu-id="d6934-146">SwitchOutLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-146">SwitchOutLogicalThreadState Method</span></span>](icorruntimehost-switchoutlogicalthreadstate-method.md)|<span data-ttu-id="d6934-147">请勿使用。</span><span class="sxs-lookup"><span data-stu-id="d6934-147">Do not use.</span></span>|  
|[<span data-ttu-id="d6934-148">UnloadDomain 方法</span><span class="sxs-lookup"><span data-stu-id="d6934-148">UnloadDomain Method</span></span>](icorruntimehost-unloaddomain-method.md)|<span data-ttu-id="d6934-149">从当前进程中卸载指定的应用程序域。</span><span class="sxs-lookup"><span data-stu-id="d6934-149">Unloads the specified application domain from the current process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6934-150">要求</span><span class="sxs-lookup"><span data-stu-id="d6934-150">Requirements</span></span>  
 <span data-ttu-id="d6934-151">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d6934-151">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6934-152">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d6934-152">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6934-153">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="d6934-153">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6934-154">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="d6934-154">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6934-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d6934-155">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="d6934-156">承载</span><span class="sxs-lookup"><span data-stu-id="d6934-156">Hosting</span></span>](index.md)
- [<span data-ttu-id="d6934-157">ICLRRuntimeHost 接口</span><span class="sxs-lookup"><span data-stu-id="d6934-157">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- <span data-ttu-id="d6934-158">[运行时主机](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d6934-158">[Runtime Hosts](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
- [<span data-ttu-id="d6934-159">承载接口</span><span class="sxs-lookup"><span data-stu-id="d6934-159">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="d6934-160">CorRuntimeHost 组件类</span><span class="sxs-lookup"><span data-stu-id="d6934-160">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
