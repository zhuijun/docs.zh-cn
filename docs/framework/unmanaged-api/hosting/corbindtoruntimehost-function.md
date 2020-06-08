---
title: CorBindToRuntimeHost 函数
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeHost
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeHost
helpviewer_keywords:
- CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type:
- apiref
ms.openlocfilehash: 9d1c7f4f5b881f7f55539602c152b557a7950472
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504402"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="3d363-102">CorBindToRuntimeHost 函数</span><span class="sxs-lookup"><span data-stu-id="3d363-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="3d363-103">使宿主可以将指定版本的公共语言运行时（CLR）加载到进程中。</span><span class="sxs-lookup"><span data-stu-id="3d363-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="3d363-104">此函数已在 .NET Framework 4 中弃用。</span><span class="sxs-lookup"><span data-stu-id="3d363-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d363-105">语法</span><span class="sxs-lookup"><span data-stu-id="3d363-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,
    [in] LPCWSTR       pwszBuildFlavor,
    [in] LPCWSTR       pwszHostConfigFile,
    [in] VOID*         pReserved,
    [in] DWORD         startupFlags,
    [in] REFCLSID      rclsid,
    [in] REFIID        riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d363-106">参数</span><span class="sxs-lookup"><span data-stu-id="3d363-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="3d363-107">中一个字符串，描述要加载的 CLR 的版本。</span><span class="sxs-lookup"><span data-stu-id="3d363-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="3d363-108">.NET Framework 中的版本号由以句点分隔的四个部分组成：*主*版本. 次要版本. 内部版本号. 修订号。</span><span class="sxs-lookup"><span data-stu-id="3d363-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="3d363-109">传递的字符串 `pwszVersion` 必须以字符 "v" 开头，后跟版本号的前三个部分（例如，"v 1.0.1529"）。</span><span class="sxs-lookup"><span data-stu-id="3d363-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="3d363-110">某些版本的 CLR 随策略声明一起安装，后者指定与以前版本的 CLR 的兼容性。</span><span class="sxs-lookup"><span data-stu-id="3d363-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="3d363-111">默认情况下，启动填充程序将 `pwszVersion` 根据策略语句进行评估，并加载与请求的版本兼容的运行时的最新版本。</span><span class="sxs-lookup"><span data-stu-id="3d363-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="3d363-112">主机可以 `pwszVersion` 通过为参数传递值 STARTUP_LOADER_SAFEMODE 来强制填充程序跳过策略评估并加载中指定的确切版本 `startupFlags` 。</span><span class="sxs-lookup"><span data-stu-id="3d363-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="3d363-113">如果 `pwszVersion` 为，则 `null,` 此方法不加载任何版本的 CLR。</span><span class="sxs-lookup"><span data-stu-id="3d363-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="3d363-114">相反，它将返回 CLR_E_SHIM_RUNTIMELOAD，这表示它未能加载运行时。</span><span class="sxs-lookup"><span data-stu-id="3d363-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="3d363-115">中一个字符串，指定是加载 CLR 的服务器还是工作站版本。</span><span class="sxs-lookup"><span data-stu-id="3d363-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="3d363-116">有效值为 `svr` 和 `wks`。</span><span class="sxs-lookup"><span data-stu-id="3d363-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="3d363-117">服务器版本经过优化，可利用多个处理器进行垃圾回收，工作站构建针对单处理器计算机上运行的客户端应用程序进行了优化。</span><span class="sxs-lookup"><span data-stu-id="3d363-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="3d363-118">如果 `pwszBuildFlavor` 设置为 null，则加载工作站生成。</span><span class="sxs-lookup"><span data-stu-id="3d363-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="3d363-119">在单处理器计算机上运行时，始终会加载工作站构建，即使将 `pwszBuildFlavor` 设置为 `svr` 。</span><span class="sxs-lookup"><span data-stu-id="3d363-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="3d363-120">但是，如果将 `pwszBuildFlavor` 设置为 `svr` ，并且指定了并发垃圾回收（请参阅参数的说明 `startupFlags` ），则将加载服务器生成。</span><span class="sxs-lookup"><span data-stu-id="3d363-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d363-121">在实现 Intel Itanium 体系结构（以前称为 IA-64）的64位系统上运行 WOW64 x86 模拟器的应用程序中不支持并发垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="3d363-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="3d363-122">有关在64位 Windows 系统上使用 WOW64 的详细信息，请参阅[运行32位应用程序](/windows/desktop/WinProg64/running-32-bit-applications)。</span><span class="sxs-lookup"><span data-stu-id="3d363-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="3d363-123">中主机配置文件的名称，该名称指定要加载的 CLR 的版本。</span><span class="sxs-lookup"><span data-stu-id="3d363-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="3d363-124">如果文件名不包含完全限定的路径，则假定该文件与进行调用的可执行文件位于同一目录中。</span><span class="sxs-lookup"><span data-stu-id="3d363-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="3d363-125">中保留以供将来进行扩展。</span><span class="sxs-lookup"><span data-stu-id="3d363-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="3d363-126">中一组标志，这些标志控制并发垃圾回收、非特定于域的代码和参数的行为 `pwszVersion` 。</span><span class="sxs-lookup"><span data-stu-id="3d363-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="3d363-127">如果未设置任何标志，则默认值为单一域。</span><span class="sxs-lookup"><span data-stu-id="3d363-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="3d363-128">有关支持的值的列表，请参阅[STARTUP_FLAGS 枚举](startup-flags-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="3d363-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="3d363-129">中`CLSID`用于实现[ICorRuntimeHost](icorruntimehost-interface.md)或[ICLRRuntimeHost](iclrruntimehost-interface.md)接口的 coclass 的。</span><span class="sxs-lookup"><span data-stu-id="3d363-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="3d363-130">支持的值为 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="3d363-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="3d363-131">中`IID`你请求的接口的。</span><span class="sxs-lookup"><span data-stu-id="3d363-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="3d363-132">支持的值为 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="3d363-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="3d363-133">弄指向已加载的运行时版本的接口指针。</span><span class="sxs-lookup"><span data-stu-id="3d363-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d363-134">要求</span><span class="sxs-lookup"><span data-stu-id="3d363-134">Requirements</span></span>  
 <span data-ttu-id="3d363-135">**平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3d363-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d363-136">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3d363-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="3d363-137">**库：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3d363-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d363-138">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d363-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d363-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3d363-139">See also</span></span>

- [<span data-ttu-id="3d363-140">CorBindToCurrentRuntime 函数</span><span class="sxs-lookup"><span data-stu-id="3d363-140">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="3d363-141">CorBindToRuntime 函数</span><span class="sxs-lookup"><span data-stu-id="3d363-141">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="3d363-142">CorBindToRuntimeByCfg 函数</span><span class="sxs-lookup"><span data-stu-id="3d363-142">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="3d363-143">CorBindToRuntimeEx 函数</span><span class="sxs-lookup"><span data-stu-id="3d363-143">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="3d363-144">ICorRuntimeHost 接口</span><span class="sxs-lookup"><span data-stu-id="3d363-144">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="3d363-145">弃用的 CLR 承载函数</span><span class="sxs-lookup"><span data-stu-id="3d363-145">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
