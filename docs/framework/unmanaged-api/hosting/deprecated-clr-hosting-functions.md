---
title: 弃用的 CLR 承载函数
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 083d0ff285abb4a99ad05c791bc504ff7f282c6a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504363"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="1fc14-102">弃用的 CLR 承载函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-102">Deprecated CLR Hosting Functions</span></span>
<span data-ttu-id="1fc14-103">本部分介绍了早期版本的托管 API 使用的非托管全局静态函数。</span><span class="sxs-lookup"><span data-stu-id="1fc14-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="1fc14-104">除了仅由 .NET Framework 使用的基础结构函数（ `_Cor*` 函数）之外，这些函数在 .NET Framework 4 中已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="1fc14-105">激活函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-105">Activation functions</span></span>  
 [<span data-ttu-id="1fc14-106">ClrCreateManagedInstance 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-106">ClrCreateManagedInstance Function</span></span>](clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="1fc14-107">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-107">Deprecated.</span></span> <span data-ttu-id="1fc14-108">创建指定托管类型的实例。</span><span class="sxs-lookup"><span data-stu-id="1fc14-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="1fc14-109">CoInitializeCor 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-109">CoInitializeCor Function</span></span>](coinitializecor-function.md)  
 <span data-ttu-id="1fc14-110">已过时。</span><span class="sxs-lookup"><span data-stu-id="1fc14-110">Obsolete.</span></span> <span data-ttu-id="1fc14-111">若要初始化公共语言运行时（CLR），请使用[CorBindToRuntimeEx](corbindtoruntimeex-function.md)或[CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)。</span><span class="sxs-lookup"><span data-stu-id="1fc14-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="1fc14-112">CoInitializeEE 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-112">CoInitializeEE Function</span></span>](coinitializeee-function.md)  
 <span data-ttu-id="1fc14-113">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-113">Deprecated.</span></span> <span data-ttu-id="1fc14-114">确保 CLR 执行引擎已加载到进程中。</span><span class="sxs-lookup"><span data-stu-id="1fc14-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="1fc14-115">改为使用[ICLRRuntimeHost：： Start](iclrruntimehost-start-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="1fc14-115">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="1fc14-116">CorBindToCurrentRuntime 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-116">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)  
 <span data-ttu-id="1fc14-117">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-117">Deprecated.</span></span> <span data-ttu-id="1fc14-118">使用存储在 XML 文件中的版本信息将公共语言运行时（CLR）加载到进程中。</span><span class="sxs-lookup"><span data-stu-id="1fc14-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="1fc14-119">CorBindToRuntime 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-119">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)  
 <span data-ttu-id="1fc14-120">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-120">Deprecated.</span></span> <span data-ttu-id="1fc14-121">使非托管宿主能够将 CLR 加载到进程中。</span><span class="sxs-lookup"><span data-stu-id="1fc14-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="1fc14-122">CorBindToRuntimeByCfg 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-122">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="1fc14-123">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-123">Deprecated.</span></span> <span data-ttu-id="1fc14-124">使用从 XML 文件读取的版本信息将 CLR 加载到进程中。</span><span class="sxs-lookup"><span data-stu-id="1fc14-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="1fc14-125">CorBindToRuntimeEx 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-125">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)  
 <span data-ttu-id="1fc14-126">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-126">Deprecated.</span></span> <span data-ttu-id="1fc14-127">使非托管宿主能够将 CLR 加载到进程中，并允许您设置标志来指定 CLR 的行为。</span><span class="sxs-lookup"><span data-stu-id="1fc14-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="1fc14-128">CorBindToRuntimeHost 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)  
 <span data-ttu-id="1fc14-129">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-129">Deprecated.</span></span> <span data-ttu-id="1fc14-130">使宿主可以将指定版本的 CLR 加载到进程中。</span><span class="sxs-lookup"><span data-stu-id="1fc14-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="1fc14-131">GetCORRequiredVersion 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-131">GetCORRequiredVersion Function</span></span>](getcorrequiredversion-function.md)  
 <span data-ttu-id="1fc14-132">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-132">Deprecated.</span></span> <span data-ttu-id="1fc14-133">获取所需的 CLR 版本号。</span><span class="sxs-lookup"><span data-stu-id="1fc14-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="1fc14-134">GetCORSystemDirectory 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-134">GetCORSystemDirectory Function</span></span>](getcorsystemdirectory-function.md)  
 <span data-ttu-id="1fc14-135">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-135">Deprecated.</span></span> <span data-ttu-id="1fc14-136">返回加载到进程中的 CLR 的安装目录。</span><span class="sxs-lookup"><span data-stu-id="1fc14-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="1fc14-137">GetRealProcAddress 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-137">GetRealProcAddress Function</span></span>](getrealprocaddress-function.md)  
 <span data-ttu-id="1fc14-138">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-138">Deprecated.</span></span> <span data-ttu-id="1fc14-139">获取从安装的最新版本的 CLR 导出的指定函数的地址。</span><span class="sxs-lookup"><span data-stu-id="1fc14-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="1fc14-140">GetRequestedRuntimeInfo 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-140">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="1fc14-141">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-141">Deprecated.</span></span> <span data-ttu-id="1fc14-142">获取有关应用程序请求的 CLR 的版本和目录信息。</span><span class="sxs-lookup"><span data-stu-id="1fc14-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="1fc14-143">CLR 版本函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-143">CLR version functions</span></span>  
 <span data-ttu-id="1fc14-144">本节中的函数返回 CLR 版本;它们不激活 CLR。</span><span class="sxs-lookup"><span data-stu-id="1fc14-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="1fc14-145">GetCORVersion 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-145">GetCORVersion Function</span></span>](getcorversion-function.md)  
 <span data-ttu-id="1fc14-146">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-146">Deprecated.</span></span> <span data-ttu-id="1fc14-147">返回当前进程中正在运行的 CLR 的版本号。</span><span class="sxs-lookup"><span data-stu-id="1fc14-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="1fc14-148">GetFileVersion 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-148">GetFileVersion Function</span></span>](getfileversion-function.md)  
 <span data-ttu-id="1fc14-149">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-149">Deprecated.</span></span> <span data-ttu-id="1fc14-150">使用指定的缓冲区获取指定文件的 CLR 版本信息。</span><span class="sxs-lookup"><span data-stu-id="1fc14-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="1fc14-151">GetRequestedRuntimeVersion 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-151">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)  
 <span data-ttu-id="1fc14-152">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-152">Deprecated.</span></span> <span data-ttu-id="1fc14-153">获取指定应用程序请求的 CLR 的版本号。</span><span class="sxs-lookup"><span data-stu-id="1fc14-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="1fc14-154">如果未安装该版本，则获取在请求版本之前安装的最新版本。</span><span class="sxs-lookup"><span data-stu-id="1fc14-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="1fc14-155">GetRequestedRuntimeVersionForCLSID 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="1fc14-156">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-156">Deprecated.</span></span> <span data-ttu-id="1fc14-157">获取具有指定 CLSID 的类的相应 CLR 版本信息。</span><span class="sxs-lookup"><span data-stu-id="1fc14-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="1fc14-158">GetVersionFromProcess 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-158">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)  
 <span data-ttu-id="1fc14-159">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-159">Deprecated.</span></span> <span data-ttu-id="1fc14-160">获取与指定的进程句柄关联的 CLR 的版本号。</span><span class="sxs-lookup"><span data-stu-id="1fc14-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="1fc14-161">LockClrVersion 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-161">LockClrVersion Function</span></span>](lockclrversion-function.md)  
 <span data-ttu-id="1fc14-162">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-162">Deprecated.</span></span> <span data-ttu-id="1fc14-163">允许主机在显式初始化 CLR 之前确定将在进程内使用的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="1fc14-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="1fc14-164">承载函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-164">Hosting functions</span></span>  
 [<span data-ttu-id="1fc14-165">CallFunctionShim 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-165">CallFunctionShim Function</span></span>](callfunctionshim-function.md)  
 <span data-ttu-id="1fc14-166">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-166">Deprecated.</span></span> <span data-ttu-id="1fc14-167">对指定库中具有指定名称和参数的函数进行调用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="1fc14-168">CoEEShutDownCOM 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-168">CoEEShutDownCOM Function</span></span>](coeeshutdowncom-function.md)  
 <span data-ttu-id="1fc14-169">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-169">Deprecated.</span></span> <span data-ttu-id="1fc14-170">从进程中卸载 COM 程序集。</span><span class="sxs-lookup"><span data-stu-id="1fc14-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="1fc14-171">CorExitProcess 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-171">CorExitProcess Function</span></span>](corexitprocess-function.md)  
 <span data-ttu-id="1fc14-172">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-172">Deprecated.</span></span> <span data-ttu-id="1fc14-173">关闭当前的非托管进程。</span><span class="sxs-lookup"><span data-stu-id="1fc14-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="1fc14-174">CorLaunchApplication 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-174">CorLaunchApplication Function</span></span>](corlaunchapplication-function.md)  
 <span data-ttu-id="1fc14-175">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-175">Deprecated.</span></span> <span data-ttu-id="1fc14-176">使用指定的清单和其他应用程序数据，在指定的网络路径下启动应用程序。</span><span class="sxs-lookup"><span data-stu-id="1fc14-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="1fc14-177">CorMarkThreadInThreadPool 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-177">CorMarkThreadInThreadPool Function</span></span>](cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="1fc14-178">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-178">Deprecated.</span></span> <span data-ttu-id="1fc14-179">标记当前正在执行的线程池线程以执行托管代码。</span><span class="sxs-lookup"><span data-stu-id="1fc14-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="1fc14-180">从 .NET Framework 版本2.0 开始，此函数不起作用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="1fc14-181">这不是必需的，并且可以从代码中删除。</span><span class="sxs-lookup"><span data-stu-id="1fc14-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="1fc14-182">CoUninitializeCor 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-182">CoUninitializeCor Function</span></span>](couninitializecor-function.md)  
 <span data-ttu-id="1fc14-183">已过时。</span><span class="sxs-lookup"><span data-stu-id="1fc14-183">Obsolete.</span></span> <span data-ttu-id="1fc14-184">CLR 无法从进程中卸载。</span><span class="sxs-lookup"><span data-stu-id="1fc14-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="1fc14-185">CoUninitializeEE 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-185">CoUninitializeEE Function</span></span>](couninitializeee-function.md)  
 <span data-ttu-id="1fc14-186">已过时。</span><span class="sxs-lookup"><span data-stu-id="1fc14-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="1fc14-187">CreateDebuggingInterfaceFromVersion 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-187">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="1fc14-188">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-188">Deprecated.</span></span> <span data-ttu-id="1fc14-189">基于指定的版本信息创建[ICorDebug](../debugging/icordebug-interface.md)对象。</span><span class="sxs-lookup"><span data-stu-id="1fc14-189">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="1fc14-190">CreateICeeFileGen 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-190">CreateICeeFileGen Function</span></span>](createiceefilegen-function.md)  
 <span data-ttu-id="1fc14-191">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-191">Deprecated.</span></span> <span data-ttu-id="1fc14-192">创建[ICeeFileGen](iceefilegen-class.md)对象。</span><span class="sxs-lookup"><span data-stu-id="1fc14-192">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="1fc14-193">DestroyICeeFileGen 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-193">DestroyICeeFileGen Function</span></span>](destroyiceefilegen-function.md)  
 <span data-ttu-id="1fc14-194">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-194">Deprecated.</span></span> <span data-ttu-id="1fc14-195">销毁[ICeeFileGen](iceefilegen-class.md)对象。</span><span class="sxs-lookup"><span data-stu-id="1fc14-195">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="1fc14-196">FExecuteInAppDomainCallback 函数指针</span><span class="sxs-lookup"><span data-stu-id="1fc14-196">FExecuteInAppDomainCallback Function Pointer</span></span>](fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="1fc14-197">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-197">Deprecated.</span></span> <span data-ttu-id="1fc14-198">指向 CLR 调用以执行托管代码的函数。</span><span class="sxs-lookup"><span data-stu-id="1fc14-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="1fc14-199">FLockClrVersionCallback 函数指针</span><span class="sxs-lookup"><span data-stu-id="1fc14-199">FLockClrVersionCallback Function Pointer</span></span>](flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="1fc14-200">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-200">Deprecated.</span></span> <span data-ttu-id="1fc14-201">指向一个函数，CLR 将调用该函数以通知宿主初始化已启动或已完成。</span><span class="sxs-lookup"><span data-stu-id="1fc14-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="1fc14-202">GetCLRIdentityManager 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-202">GetCLRIdentityManager Function</span></span>](getclridentitymanager-function.md)  
 <span data-ttu-id="1fc14-203">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-203">Deprecated.</span></span> <span data-ttu-id="1fc14-204">获取一个指向接口的指针，该接口允许 CLR 管理标识。</span><span class="sxs-lookup"><span data-stu-id="1fc14-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="1fc14-205">LoadLibraryShim 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-205">LoadLibraryShim Function</span></span>](loadlibraryshim-function.md)  
 <span data-ttu-id="1fc14-206">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-206">Deprecated.</span></span> <span data-ttu-id="1fc14-207">加载 .NET Framework DLL 的指定版本。</span><span class="sxs-lookup"><span data-stu-id="1fc14-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="1fc14-208">LoadStringRC 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-208">LoadStringRC Function</span></span>](loadstringrc-function.md)  
 <span data-ttu-id="1fc14-209">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-209">Deprecated.</span></span> <span data-ttu-id="1fc14-210">使用当前线程的默认区域性将 HRESULT 值转换为错误消息。</span><span class="sxs-lookup"><span data-stu-id="1fc14-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="1fc14-211">LoadStringRCEx 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-211">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)  
 <span data-ttu-id="1fc14-212">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-212">Deprecated.</span></span> <span data-ttu-id="1fc14-213">将 HRESULT 值转换为指定区域性的适当错误消息。</span><span class="sxs-lookup"><span data-stu-id="1fc14-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="1fc14-214">LPOVERLAPPED_COMPLETION_ROUTINE 函数指针</span><span class="sxs-lookup"><span data-stu-id="1fc14-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="1fc14-215">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-215">Deprecated.</span></span> <span data-ttu-id="1fc14-216">指向一个函数，该函数在设备的重叠（即异步） i/o 完成时通知宿主。</span><span class="sxs-lookup"><span data-stu-id="1fc14-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="1fc14-217">LPTHREAD_START_ROUTINE 函数指针</span><span class="sxs-lookup"><span data-stu-id="1fc14-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="1fc14-218">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-218">Deprecated.</span></span> <span data-ttu-id="1fc14-219">指向一个函数，该函数通知宿主线程已开始执行。</span><span class="sxs-lookup"><span data-stu-id="1fc14-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="1fc14-220">RunDll32ShimW 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-220">RunDll32ShimW Function</span></span>](rundll32shimw-function.md)  
 <span data-ttu-id="1fc14-221">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-221">Deprecated.</span></span> <span data-ttu-id="1fc14-222">执行指定的命令。</span><span class="sxs-lookup"><span data-stu-id="1fc14-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="1fc14-223">WAITORTIMERCALLBACK 函数指针</span><span class="sxs-lookup"><span data-stu-id="1fc14-223">WAITORTIMERCALLBACK Function Pointer</span></span>](waitortimercallback-function-pointer.md)  
 <span data-ttu-id="1fc14-224">已弃用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-224">Deprecated.</span></span> <span data-ttu-id="1fc14-225">指向一个函数，该函数通知宿主等待句柄已终止或超时。</span><span class="sxs-lookup"><span data-stu-id="1fc14-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="1fc14-226">基础结构函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-226">Infrastructure functions</span></span>  
 <span data-ttu-id="1fc14-227">本节中的函数仅供 .NET Framework 使用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="1fc14-228">_CorDllMain 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-228">_CorDllMain Function</span></span>](cordllmain-function.md)  
 <span data-ttu-id="1fc14-229">初始化 CLR，查找 DLL 程序集的 CLR 头中的托管入口点，然后开始执行。</span><span class="sxs-lookup"><span data-stu-id="1fc14-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="1fc14-230">_CorExeMain 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-230">_CorExeMain Function</span></span>](corexemain-function.md)  
 <span data-ttu-id="1fc14-231">初始化 CLR，查找可执行程序集的 CLR 头中的托管入口点，然后开始执行。</span><span class="sxs-lookup"><span data-stu-id="1fc14-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="1fc14-232">_CorExeMain2 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-232">_CorExeMain2 Function</span></span>](corexemain2-function.md)  
 <span data-ttu-id="1fc14-233">执行指定的内存映射代码中的入口点。</span><span class="sxs-lookup"><span data-stu-id="1fc14-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="1fc14-234">此函数由操作系统加载程序调用。</span><span class="sxs-lookup"><span data-stu-id="1fc14-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="1fc14-235">_CorImageUnloading 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-235">_CorImageUnloading Function</span></span>](corimageunloading-function.md)  
 <span data-ttu-id="1fc14-236">卸载托管模块映像时通知加载程序。</span><span class="sxs-lookup"><span data-stu-id="1fc14-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="1fc14-237">_CorValidateImage 函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-237">_CorValidateImage Function</span></span>](corvalidateimage-function.md)  
 <span data-ttu-id="1fc14-238">验证托管模块映像，并在加载后通知操作系统加载程序。</span><span class="sxs-lookup"><span data-stu-id="1fc14-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fc14-239">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1fc14-239">See also</span></span>

- [<span data-ttu-id="1fc14-240">.NET Framework 4 承载全局静态函数</span><span class="sxs-lookup"><span data-stu-id="1fc14-240">.NET Framework 4 Hosting Global Static Functions</span></span>](net-framework-4-hosting-global-static-functions.md)
