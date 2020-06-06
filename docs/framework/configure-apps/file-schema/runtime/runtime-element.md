---
title: <runtime> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime
helpviewer_keywords:
- <runtime> element
- runtime element
- container tags, <runtime> element
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
ms.openlocfilehash: 3825ae7c3e35193cb835981600fe1ef83097cd2d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74430455"
---
# <a name="runtime-element"></a><span data-ttu-id="6b83f-102">\<runtime> 元素</span><span class="sxs-lookup"><span data-stu-id="6b83f-102">\<runtime> Element</span></span>

<span data-ttu-id="6b83f-103">提供公共语言运行时用来配置应用程序的信息。</span><span class="sxs-lookup"><span data-stu-id="6b83f-103">Provides information used by the common language runtime to configure applications.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;\<runtime>

## <a name="syntax"></a><span data-ttu-id="6b83f-104">语法</span><span class="sxs-lookup"><span data-stu-id="6b83f-104">Syntax</span></span>

```xml
<runtime>
</runtime>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6b83f-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6b83f-105">Attributes and Elements</span></span>

<span data-ttu-id="6b83f-106">以下各节介绍子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6b83f-106">The following sections describe child elements and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6b83f-107">特性</span><span class="sxs-lookup"><span data-stu-id="6b83f-107">Attributes</span></span>

<span data-ttu-id="6b83f-108">无。</span><span class="sxs-lookup"><span data-stu-id="6b83f-108">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6b83f-109">子元素</span><span class="sxs-lookup"><span data-stu-id="6b83f-109">Child Elements</span></span>

|<span data-ttu-id="6b83f-110">元素</span><span class="sxs-lookup"><span data-stu-id="6b83f-110">Element</span></span>|<span data-ttu-id="6b83f-111">说明</span><span class="sxs-lookup"><span data-stu-id="6b83f-111">Description</span></span>|
|-------------|-----------------|
|[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)|<span data-ttu-id="6b83f-112">指定 Windows 标识始终流经异步点，而不考虑执行模拟的方式。</span><span class="sxs-lookup"><span data-stu-id="6b83f-112">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|
|[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)|<span data-ttu-id="6b83f-113">定义 <xref:System.AppContext> 类使用的一个或多个开关，用于提供新功能的选择退出机制。</span><span class="sxs-lookup"><span data-stu-id="6b83f-113">Defines one or more switches used by the <xref:System.AppContext> class to provide an opt-out mechanism for new functionality.</span></span>|
|[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)|<span data-ttu-id="6b83f-114">指定为过程中的默认应用程序域提供应用程序域管理器的程序集。</span><span class="sxs-lookup"><span data-stu-id="6b83f-114">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>|
|[\<appDomainManagerType>](appdomainmanagertype-element.md)|<span data-ttu-id="6b83f-115">指定用作默认应用程序域的应用程序域管理器的类型。</span><span class="sxs-lookup"><span data-stu-id="6b83f-115">Specifies the type that serves as the application domain manager for the default application domain.</span></span>|
|[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)|<span data-ttu-id="6b83f-116">指示运行时在过程的生命周期过程中收集所有应用程序域的统计数据。</span><span class="sxs-lookup"><span data-stu-id="6b83f-116">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>|
|[\<assemblyBinding>](assemblybinding-element-for-runtime.md)|<span data-ttu-id="6b83f-117">包含有关程序集版本重定向和程序集位置的信息。</span><span class="sxs-lookup"><span data-stu-id="6b83f-117">Contains information about assembly version redirection and the locations of assemblies.</span></span>|
|[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)|<span data-ttu-id="6b83f-118">指定是否应绕过对受信任的程序集进行强名称验证。</span><span class="sxs-lookup"><span data-stu-id="6b83f-118">Specifies whether strong name verification for trusted assemblies should be bypassed.</span></span>|
|[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)|<span data-ttu-id="6b83f-119">指定在执行字符串比较时，运行时应使用旧的排序行为。</span><span class="sxs-lookup"><span data-stu-id="6b83f-119">Specifies that the runtime should use legacy sorting behavior when performing string comparisons.</span></span>|
|[\<developmentMode>](developmentmode-element.md)|<span data-ttu-id="6b83f-120">指定运行时是否搜索由 DEVPATH 环境变量指定的目录中的程序集。</span><span class="sxs-lookup"><span data-stu-id="6b83f-120">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|
|[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)|<span data-ttu-id="6b83f-121">指定是否禁用绑定故障的缓存，这是 .NET Framework 版本2.0 中的默认行为。</span><span class="sxs-lookup"><span data-stu-id="6b83f-121">Specifies whether the caching of binding failures, which is the default behavior in the .NET Framework version 2.0, is disabled.</span></span>|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|<span data-ttu-id="6b83f-122">指定在线程启动时是否提交完整线程堆栈。</span><span class="sxs-lookup"><span data-stu-id="6b83f-122">Specifies whether the full thread stack is committed when a thread is started.</span></span>|
|[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)|<span data-ttu-id="6b83f-123">指定是否禁用允许运行时主机为应用程序域重写配置设置的默认行为。</span><span class="sxs-lookup"><span data-stu-id="6b83f-123">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|<span data-ttu-id="6b83f-124">确定日期和时间分析方法是否使用调整后的一组规则来分析仅包含天、月、小时和 AM/PM 指示符的日期字符串。</span><span class="sxs-lookup"><span data-stu-id="6b83f-124">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|
|[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)|<span data-ttu-id="6b83f-125">指定是否强制执行以下计算机配置要求：加密算法必须符合美国联邦信息处理标准 (FIPS)。</span><span class="sxs-lookup"><span data-stu-id="6b83f-125">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>|
|[\<etwEnable>](etwenable-element.md)|<span data-ttu-id="6b83f-126">指定是否为公共语言运行时事件启用 Windows 事件跟踪 (ETW)。</span><span class="sxs-lookup"><span data-stu-id="6b83f-126">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)|<span data-ttu-id="6b83f-127">指定 PerfCounter.dll 是否使用 .NET Framework 版本 1.1 应用程序中的 CategoryOptions 注册表设置，以确定是否加载来自特定于类别的共享内存或全局内存的性能计数器数据。</span><span class="sxs-lookup"><span data-stu-id="6b83f-127">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|
|[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)|<span data-ttu-id="6b83f-128">在 64 位平台上，启用总大小大于 2 千兆字节 (GB) 的数组。</span><span class="sxs-lookup"><span data-stu-id="6b83f-128">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>|
|[\<gcConcurrent>](gcconcurrent-element.md)|<span data-ttu-id="6b83f-129">指定公共语言运行时是否并发运行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="6b83f-129">Specifies whether the common language runtime runs garbage collection concurrently.</span></span>|
|[\<GCCpuGroup>](gccpugroup-element.md)|<span data-ttu-id="6b83f-130">指定垃圾回收是否支持多个 CPU 组。</span><span class="sxs-lookup"><span data-stu-id="6b83f-130">Specifies whether garbage collection supports multiple CPU groups.</span></span>|
|[\<GCHeapAffinitizeMask>](gcheapaffinitizemask-element.md)|<span data-ttu-id="6b83f-131">定义垃圾回收堆和单个处理器之间的关联。</span><span class="sxs-lookup"><span data-stu-id="6b83f-131">Defines the affinity between garbage collection heaps and individual processors.</span></span>|
|[\<GCHeapCount>](gcheapcount-element.md)|<span data-ttu-id="6b83f-132">指定用于服务器垃圾回收的堆/线程数。</span><span class="sxs-lookup"><span data-stu-id="6b83f-132">Specifies the number of heaps/threads to use for server garbage collection.</span></span>|
|[\<GCLOHThreshold>](gclohthreshold-element.md)|<span data-ttu-id="6b83f-133">指定导致垃圾回收器将对象放置在大型对象堆上的阈值大小。</span><span class="sxs-lookup"><span data-stu-id="6b83f-133">Specifies the threshold size that causes the garbage collector to put objects on the large object heap.</span></span>|
|[\<GCNoAffinitize>](gcnoaffinitize-element.md)|<span data-ttu-id="6b83f-134">指定是否对 Cpu 关联服务器垃圾回收线程。</span><span class="sxs-lookup"><span data-stu-id="6b83f-134">Specifies whether or not to affinitize server garbage collection threads with CPUs.</span></span>|
|[\<gcServer>](gcserver-element.md)|<span data-ttu-id="6b83f-135">指定公共语言运行时是否运行服务器垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="6b83f-135">Specifies whether the common language runtime runs server garbage collection.</span></span>|
|[\<generatePublisherEvidence>](generatepublisherevidence-element.md)|<span data-ttu-id="6b83f-136">指定运行时是否使用代码访问安全性 (CAS) 发布服务器策略。</span><span class="sxs-lookup"><span data-stu-id="6b83f-136">Specifies whether the runtime uses code access security (CAS) publisher policy.</span></span>|
|[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)|<span data-ttu-id="6b83f-137">指定运行时是否允许托管的代码捕获访问冲突和其他损坏状态异常。</span><span class="sxs-lookup"><span data-stu-id="6b83f-137">Specifies whether the runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>|
|[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)|<span data-ttu-id="6b83f-138">指定 Windows 标识不流经异步点，而不考虑当前线程上执行上下文的流设置。</span><span class="sxs-lookup"><span data-stu-id="6b83f-138">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>|
|[\<loadfromRemoteSources>](loadfromremotesources-element.md)|<span data-ttu-id="6b83f-139">指定是否将来自远程源的程序集加载为完全信任。</span><span class="sxs-lookup"><span data-stu-id="6b83f-139">Specifies whether assemblies from remote sources are loaded as full trust.</span></span>|
|[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)|<span data-ttu-id="6b83f-140">指定运行时是否使用旧版代码访问安全性 (CAS) 策略。</span><span class="sxs-lookup"><span data-stu-id="6b83f-140">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>|
|[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)|<span data-ttu-id="6b83f-141">指定运行时是否以减慢托管和非托管代码之间的转换速度为代价，在运行时自动修复不正确的平台调用声明。</span><span class="sxs-lookup"><span data-stu-id="6b83f-141">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)|<span data-ttu-id="6b83f-142">指定运行时是否使用固定的内存量来计算 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法的哈希代码。</span><span class="sxs-lookup"><span data-stu-id="6b83f-142">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>|
|[\<PreferComInsteadOfRemoting>](prefercominsteadofmanagedremoting-element.md)|<span data-ttu-id="6b83f-143">指定运行时将使用 COM 互操作来代替跨应用程序域边界的远程。</span><span class="sxs-lookup"><span data-stu-id="6b83f-143">Specifies that the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|
|[\<relativeBindForResources>](relativebindforresources-element.md)|<span data-ttu-id="6b83f-144">优化附属程序集的探测。</span><span class="sxs-lookup"><span data-stu-id="6b83f-144">Optimizes the probe for satellite assemblies.</span></span>|
|[\<shadowCopyVerifyByTimeStamp>](shadowcopyverifybytimestamp-element.md)|<span data-ttu-id="6b83f-145">指定卷影复制是否使用 .NET Framework 4 中引入的默认启动行为，或恢复为 .NET Framework 早期版本的启动行为。</span><span class="sxs-lookup"><span data-stu-id="6b83f-145">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>|
|[\<supportPortability>](supportportability-element.md)|<span data-ttu-id="6b83f-146">通过禁用将程序集视为等效于应用程序可移植性用途的默认行为来指定应用程序可以在两种不同的 .NET Framework 实现中引用同一程序集。</span><span class="sxs-lookup"><span data-stu-id="6b83f-146">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>|
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="6b83f-147">提供默认内存中对象缓存的配置信息。</span><span class="sxs-lookup"><span data-stu-id="6b83f-147">Provides configuration information for the default in-memory object cache.</span></span>|
|[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)|<span data-ttu-id="6b83f-148">指定运行时是否跨所有 CPU 组分发托管的线程。</span><span class="sxs-lookup"><span data-stu-id="6b83f-148">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|
|[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)|<span data-ttu-id="6b83f-149">指定未经处理的任务异常是否应终止正在运行的进程。</span><span class="sxs-lookup"><span data-stu-id="6b83f-149">Specifies whether unhandled task exceptions should terminate a running process.</span></span>|
|[\<TimeSpan_LegacyFormatMode>](timespan-legacyformatmode-element.md)|<span data-ttu-id="6b83f-150">指定运行时是否使用 <xref:System.TimeSpan> 值的旧格式。</span><span class="sxs-lookup"><span data-stu-id="6b83f-150">Specifies whether the runtime uses legacy formatting for <xref:System.TimeSpan> values.</span></span>|
|[\<useLegacyJit>](uselegacyjit-element.md)|<span data-ttu-id="6b83f-151">确定公共语言运行时是否使用实时编译的旧版 64 位 JIT 编译器。</span><span class="sxs-lookup"><span data-stu-id="6b83f-151">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>|
|[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)|<span data-ttu-id="6b83f-152">指定运行时是否按应用程序域计算字符串的哈希代码。</span><span class="sxs-lookup"><span data-stu-id="6b83f-152">Specifies whether the runtime calculates hash codes for strings on a per application domain basis.</span></span>|
|[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)|<span data-ttu-id="6b83f-153">请求运行时在创建内部使用的某些线程时使用显式堆栈大小，而不是默认堆栈大小。</span><span class="sxs-lookup"><span data-stu-id="6b83f-153">Requests that the runtime use explicit stack sizes when it creates certain threads that it uses internally, instead of the default stack size.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6b83f-154">父元素</span><span class="sxs-lookup"><span data-stu-id="6b83f-154">Parent Elements</span></span>

|<span data-ttu-id="6b83f-155">元素</span><span class="sxs-lookup"><span data-stu-id="6b83f-155">Element</span></span>|<span data-ttu-id="6b83f-156">说明</span><span class="sxs-lookup"><span data-stu-id="6b83f-156">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="6b83f-157">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="6b83f-157">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6b83f-158">注解</span><span class="sxs-lookup"><span data-stu-id="6b83f-158">Remarks</span></span>

<span data-ttu-id="6b83f-159">[\<runtime>](runtime-element.md)公共语言运行时使用配置文件部分中的子元素来配置应用程序的执行方式。</span><span class="sxs-lookup"><span data-stu-id="6b83f-159">The child elements in the [\<runtime>](runtime-element.md) section of a configuration file are used by the common language runtime to configure how an application executes.</span></span> <span data-ttu-id="6b83f-160">例如， [\<gcServer>](gcserver-element.md) 元素确定垃圾回收器是否使用工作站垃圾回收或服务器垃圾回收， [\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md) 元素确定公共语言运行时是否在每个应用程序或每个应用程序域计算字符串的哈希代码，以及 `AppContextSwitchOverrides` 元素是否允许库用户选择加入或选择退出库提供的已更改功能。</span><span class="sxs-lookup"><span data-stu-id="6b83f-160">For example, the [\<gcServer>](gcserver-element.md) element determines whether the garbage collector uses workstation garbage collection or server garbage collection, the [\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md) element determines whether the common language runtime calculates hash codes for string on a per-application or a per-application domain basis, and the `AppContextSwitchOverrides` element allows library users to opt in or opt out of changed  functionality provided by a library.</span></span>

<span data-ttu-id="6b83f-161">在 [\<runtime>](runtime-element.md) 应用程序启动时，公共语言运行时将自动读取部分中的元素。</span><span class="sxs-lookup"><span data-stu-id="6b83f-161">The elements in the [\<runtime>](runtime-element.md) section are read automatically by the common language runtime at application startup.</span></span> <span data-ttu-id="6b83f-162">你还可以通过向属性提供其名称来定义非默认应用程序域的配置文件 <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> ; 在加载应用程序域时，将自动读取其设置。</span><span class="sxs-lookup"><span data-stu-id="6b83f-162">You can also define the configuration file for a non-default application domain by supplying its name to the <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> property; its settings are read automatically when the application domain is loaded.</span></span> <span data-ttu-id="6b83f-163">如果需要，您很少需要直接阅读 [\<runtime>](runtime-element.md) 应用程序配置文件的部分中的设置。</span><span class="sxs-lookup"><span data-stu-id="6b83f-163">You should rarely, if ever, have a need to directly read the settings in the [\<runtime>](runtime-element.md) section in your application's configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b83f-164">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b83f-164">See also</span></span>

- [<span data-ttu-id="6b83f-165">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="6b83f-165">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6b83f-166">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="6b83f-166">Configuration File Schema</span></span>](../index.md)
