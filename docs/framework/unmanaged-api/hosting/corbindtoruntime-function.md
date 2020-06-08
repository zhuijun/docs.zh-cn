---
title: CorBindToRuntime 函数
ms.date: 03/30/2017
api_name:
- CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntime
helpviewer_keywords:
- CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type:
- apiref
ms.openlocfilehash: 52594c36c54c74941371f9950fbc6fb543b86de0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493547"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="0dc11-102">CorBindToRuntime 函数</span><span class="sxs-lookup"><span data-stu-id="0dc11-102">CorBindToRuntime Function</span></span>
<span data-ttu-id="0dc11-103">使非托管宿主能够将公共语言运行时（CLR）加载到进程中。</span><span class="sxs-lookup"><span data-stu-id="0dc11-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="0dc11-104">此函数已在 .NET Framework 4 中弃用。</span><span class="sxs-lookup"><span data-stu-id="0dc11-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dc11-105">语法</span><span class="sxs-lookup"><span data-stu-id="0dc11-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dc11-106">参数</span><span class="sxs-lookup"><span data-stu-id="0dc11-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="0dc11-107">中一个字符串，描述要加载的 CLR 的版本。</span><span class="sxs-lookup"><span data-stu-id="0dc11-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="0dc11-108">.NET Framework 中的版本号由以句点分隔的四个部分组成：*主*版本. 次要版本. 内部版本号. 修订号。</span><span class="sxs-lookup"><span data-stu-id="0dc11-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="0dc11-109">传递的字符串 `pwszVersion` 必须以字符 "v" 开头，后跟版本号的前三个部分（例如，"v 1.0.1529"）。</span><span class="sxs-lookup"><span data-stu-id="0dc11-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="0dc11-110">某些版本的 CLR 随策略声明一起安装，后者指定与以前版本的 CLR 的兼容性。</span><span class="sxs-lookup"><span data-stu-id="0dc11-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="0dc11-111">默认情况下，启动填充程序将 `pwszVersion` 根据策略语句进行评估，并加载与请求的版本兼容的运行时的最新版本。</span><span class="sxs-lookup"><span data-stu-id="0dc11-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="0dc11-112">主机可以通过为参数传递值来强制填充程序跳过策略评估并加载中指定的确切版本 `pwszVersion` `STARTUP_LOADER_SAFEMODE` `flags` ，如下所述。</span><span class="sxs-lookup"><span data-stu-id="0dc11-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="0dc11-113">如果调用方为指定 null `pwszVersion` ，则加载最新版本的运行时。</span><span class="sxs-lookup"><span data-stu-id="0dc11-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="0dc11-114">如果传递 null，则主机将无法控制加载的运行时版本。</span><span class="sxs-lookup"><span data-stu-id="0dc11-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="0dc11-115">虽然这种方法可能适用于某些情况，但强烈建议主机提供要加载的特定版本。</span><span class="sxs-lookup"><span data-stu-id="0dc11-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="0dc11-116">中一个字符串，指定是加载 CLR 的服务器还是工作站版本。</span><span class="sxs-lookup"><span data-stu-id="0dc11-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="0dc11-117">有效值为 `svr` 和 `wks`。</span><span class="sxs-lookup"><span data-stu-id="0dc11-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="0dc11-118">服务器版本经过优化，可利用多个处理器进行垃圾回收，工作站构建针对单处理器计算机上运行的客户端应用程序进行了优化。</span><span class="sxs-lookup"><span data-stu-id="0dc11-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="0dc11-119">如果 `pwszBuildFlavor` 设置为 null，则加载工作站生成。</span><span class="sxs-lookup"><span data-stu-id="0dc11-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="0dc11-120">在单处理器计算机上运行时，始终会加载工作站构建，即使将 `pwszBuildFlavor` 设置为 `svr` 。</span><span class="sxs-lookup"><span data-stu-id="0dc11-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="0dc11-121">但是，如果将 `pwszBuildFlavor` 设置为 `svr` ，并且指定了并发垃圾回收（请参阅参数的说明 `flags` ），则将加载服务器生成。</span><span class="sxs-lookup"><span data-stu-id="0dc11-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="0dc11-122">中`CLSID`用于实现[ICorRuntimeHost](icorruntimehost-interface.md)或[ICLRRuntimeHost](iclrruntimehost-interface.md)接口的 coclass 的。</span><span class="sxs-lookup"><span data-stu-id="0dc11-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="0dc11-123">支持的值为 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="0dc11-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="0dc11-124">中所 `IID` 请求的接口的 `rclsid` 。</span><span class="sxs-lookup"><span data-stu-id="0dc11-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="0dc11-125">支持的值为 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="0dc11-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="0dc11-126">弄返回的接口指针 `riid` 。</span><span class="sxs-lookup"><span data-stu-id="0dc11-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0dc11-127">注解</span><span class="sxs-lookup"><span data-stu-id="0dc11-127">Remarks</span></span>  
 <span data-ttu-id="0dc11-128">如果 `pwszVersion` 指定不存在的运行时版本，则 `CorBindToRuntimeEx` 返回的 HRESULT 值为 CLR_E_SHIM_RUNTIMELOAD。</span><span class="sxs-lookup"><span data-stu-id="0dc11-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="0dc11-129">执行上下文和 Windows 标识流</span><span class="sxs-lookup"><span data-stu-id="0dc11-129">Execution Context and Flow of Windows Identity</span></span>  
 <span data-ttu-id="0dc11-130">在 CLR 版本1中， <xref:System.Security.Principal.WindowsIdentity> 对象不流经异步点，如新线程、线程池或计时器回调。</span><span class="sxs-lookup"><span data-stu-id="0dc11-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="0dc11-131">在 CLR 版本2.0 中， <xref:System.Threading.ExecutionContext> 对象包装了有关当前正在执行的线程的某些信息，并在所有异步点（而不是跨应用程序域边界）对其进行流传递。</span><span class="sxs-lookup"><span data-stu-id="0dc11-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="0dc11-132">同样， <xref:System.Security.Principal.WindowsIdentity> 对象还在任何异步点上流动。</span><span class="sxs-lookup"><span data-stu-id="0dc11-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="0dc11-133">因此，线程上的当前模拟（如果有）也会流动。</span><span class="sxs-lookup"><span data-stu-id="0dc11-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="0dc11-134">可以通过两种方式更改流：</span><span class="sxs-lookup"><span data-stu-id="0dc11-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="0dc11-135">通过修改 <xref:System.Threading.ExecutionContext> 设置以在每个线程的基础上取消流（请参阅 <xref:System.Threading.ExecutionContext.SuppressFlow%2A> 、 <xref:System.Security.SecurityContext.SuppressFlow%2A> 和 <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> 方法）。</span><span class="sxs-lookup"><span data-stu-id="0dc11-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="0dc11-136">通过将进程默认模式更改为版本1兼容模式，该模式中的 <xref:System.Security.Principal.WindowsIdentity> 对象不会在任何异步点上流动，无论 <xref:System.Threading.ExecutionContext> 当前线程上的设置如何。</span><span class="sxs-lookup"><span data-stu-id="0dc11-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="0dc11-137">更改默认模式的方式取决于您使用的是托管可执行文件还是非托管承载接口来加载 CLR：</span><span class="sxs-lookup"><span data-stu-id="0dc11-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="0dc11-138">对于托管可执行文件，必须将 `enabled` 元素的属性设置 [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) 为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="0dc11-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="0dc11-139">对于非托管承载接口，请在 `STARTUP_LEGACY_IMPERSONATION` `flags` 调用函数时在参数中设置标志 `CorBindToRuntimeEx` 。</span><span class="sxs-lookup"><span data-stu-id="0dc11-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="0dc11-140">版本1兼容性模式适用于整个进程和进程中的所有应用程序域。</span><span class="sxs-lookup"><span data-stu-id="0dc11-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0dc11-141">注解</span><span class="sxs-lookup"><span data-stu-id="0dc11-141">Remarks</span></span>  
 <span data-ttu-id="0dc11-142">[CorBindToRuntimeEx](corbindtoruntimeex-function.md)和 `CorBindToRuntime` 执行相同的操作，但 `CorBindToRuntimeEx` 函数允许您设置标志来指定 CLR 的行为。</span><span class="sxs-lookup"><span data-stu-id="0dc11-142">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dc11-143">要求</span><span class="sxs-lookup"><span data-stu-id="0dc11-143">Requirements</span></span>  
 <span data-ttu-id="0dc11-144">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0dc11-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dc11-145">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0dc11-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0dc11-146">**库：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0dc11-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0dc11-147">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dc11-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dc11-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0dc11-148">See also</span></span>

- [<span data-ttu-id="0dc11-149">CorBindToCurrentRuntime 函数</span><span class="sxs-lookup"><span data-stu-id="0dc11-149">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="0dc11-150">CorBindToRuntimeByCfg 函数</span><span class="sxs-lookup"><span data-stu-id="0dc11-150">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="0dc11-151">CorBindToRuntimeEx 函数</span><span class="sxs-lookup"><span data-stu-id="0dc11-151">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="0dc11-152">CorBindToRuntimeHost 函数</span><span class="sxs-lookup"><span data-stu-id="0dc11-152">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="0dc11-153">ICorRuntimeHost 接口</span><span class="sxs-lookup"><span data-stu-id="0dc11-153">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="0dc11-154">弃用的 CLR 承载函数</span><span class="sxs-lookup"><span data-stu-id="0dc11-154">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
