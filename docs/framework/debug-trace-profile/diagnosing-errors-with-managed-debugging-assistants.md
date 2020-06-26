---
title: 使用托管调试助手诊断错误
description: 通过托管调试助手诊断 .NET 中的错误。 Mda 是与 CLR 结合使用的调试辅助工具，用于提供运行时状态信息。
ms.date: 08/14/2018
f1_keywords:
- EHMDA
helpviewer_keywords:
- run-time error debugging
- managed code, run-time debugging
- resource debugging
- registry, MDAs
- common language runtime, debugging
- MDAs (managed debugging assistants)
- configuration files [.NET Framework], debugging runtime events
- messages, managed debugging assistants
- application configuration files, managed debugging assistants
- debugging [.NET Framework], managed debugging assistants
- environment variables, MDAs
- access violation debugging [.NET Framework]
- diagnostics, managed debugging assistants
- unmanaged code, run-time debugging
- default debug output stream
- memory, debugging
- app.config files, managed debugging assistants
- managed debugging assistants (MDAs)
- debugging [.NET Framework], run-time errors
- trapping events
- runtime, error debugging
- disabling MDAs
- output, managed debugging assistants
- errors [.NET Framework], managed debugging assistants
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
ms.openlocfilehash: ac6fdc09fb057cc55659ce076d37ab96fe2354d1
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416091"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a><span data-ttu-id="2e06b-104">用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="2e06b-104">Diagnose Errors with Managed Debugging Assistants</span></span>

<span data-ttu-id="2e06b-105">托管调试助手 (MDA) 是调试辅助程序，它与公共语言运行时 (CLR) 一起工作以提供关于运行时状态的信息。</span><span class="sxs-lookup"><span data-stu-id="2e06b-105">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="2e06b-106">这些助手可生成关于你无法通过其他方式捕获的运行时事件的信息性消息。</span><span class="sxs-lookup"><span data-stu-id="2e06b-106">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="2e06b-107">可以使用 MDA 隔离在托管代码和非托管代码之间转换时发生的、难以发现的应用程序 Bug。</span><span class="sxs-lookup"><span data-stu-id="2e06b-107">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span>

<span data-ttu-id="2e06b-108">您可以通过向 Windows 注册表添加项或通过设置环境变量来[启用或禁用](#enable-and-disable-mdas)所有 mda。</span><span class="sxs-lookup"><span data-stu-id="2e06b-108">You can [enable or disable](#enable-and-disable-mdas) all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="2e06b-109">可使用应用程序配置设置来启用特定的 MDA。</span><span class="sxs-lookup"><span data-stu-id="2e06b-109">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="2e06b-110">可以在应用程序的配置文件中为某些单独的 MDA 设置其他配置设置。</span><span class="sxs-lookup"><span data-stu-id="2e06b-110">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="2e06b-111">由于将在加载运行时后分析这些配置文件，因此必须在托管应用程序启动之前启用 MDA。</span><span class="sxs-lookup"><span data-stu-id="2e06b-111">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="2e06b-112">不能为已经启动的应用程序启用 MDA。</span><span class="sxs-lookup"><span data-stu-id="2e06b-112">You cannot enable it for applications that have already started.</span></span>

<span data-ttu-id="2e06b-113">下表列出了 .NET Framework 附带的 Mda：</span><span class="sxs-lookup"><span data-stu-id="2e06b-113">The following table lists the MDAs that ship with the .NET Framework:</span></span>

|||
|-|-|
|[<span data-ttu-id="2e06b-114">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="2e06b-114">asynchronousThreadAbort</span></span>](asynchronousthreadabort-mda.md)|[<span data-ttu-id="2e06b-115">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="2e06b-115">bindingFailure</span></span>](bindingfailure-mda.md)|
|[<span data-ttu-id="2e06b-116">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="2e06b-116">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="2e06b-117">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="2e06b-117">contextSwitchDeadlock</span></span>](contextswitchdeadlock-mda.md)|
|[<span data-ttu-id="2e06b-118">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="2e06b-118">dangerousThreadingAPI</span></span>](dangerousthreadingapi-mda.md)|[<span data-ttu-id="2e06b-119">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="2e06b-119">dateTimeInvalidLocalFormat</span></span>](datetimeinvalidlocalformat-mda.md)|
|[<span data-ttu-id="2e06b-120">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="2e06b-120">dirtyCastAndCallOnInterface</span></span>](dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="2e06b-121">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="2e06b-121">disconnectedContext</span></span>](disconnectedcontext-mda.md)|
|[<span data-ttu-id="2e06b-122">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="2e06b-122">dllMainReturnsFalse</span></span>](dllmainreturnsfalse-mda.md)|[<span data-ttu-id="2e06b-123">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="2e06b-123">exceptionSwallowedOnCallFromCom</span></span>](exceptionswallowedoncallfromcom-mda.md)|
|[<span data-ttu-id="2e06b-124">failedQI</span><span class="sxs-lookup"><span data-stu-id="2e06b-124">failedQI</span></span>](failedqi-mda.md)|[<span data-ttu-id="2e06b-125">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="2e06b-125">fatalExecutionEngineError</span></span>](fatalexecutionengineerror-mda.md)|
|[<span data-ttu-id="2e06b-126">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="2e06b-126">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="2e06b-127">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="2e06b-127">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)|
|[<span data-ttu-id="2e06b-128">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="2e06b-128">illegalPrepareConstrainedRegion</span></span>](illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="2e06b-129">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="2e06b-129">invalidApartmentStateChange</span></span>](invalidapartmentstatechange-mda.md)|
|[<span data-ttu-id="2e06b-130">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="2e06b-130">invalidCERCall</span></span>](invalidcercall-mda.md)|[<span data-ttu-id="2e06b-131">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="2e06b-131">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)|
|[<span data-ttu-id="2e06b-132">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="2e06b-132">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)|[<span data-ttu-id="2e06b-133">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="2e06b-133">invalidIUnknown</span></span>](invalidiunknown-mda.md)|
|[<span data-ttu-id="2e06b-134">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="2e06b-134">invalidMemberDeclaration</span></span>](invalidmemberdeclaration-mda.md)|[<span data-ttu-id="2e06b-135">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="2e06b-135">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)|
|[<span data-ttu-id="2e06b-136">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="2e06b-136">invalidVariant</span></span>](invalidvariant-mda.md)|[<span data-ttu-id="2e06b-137">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="2e06b-137">jitCompilationStart</span></span>](jitcompilationstart-mda.md)|
|[<span data-ttu-id="2e06b-138">loaderLock</span><span class="sxs-lookup"><span data-stu-id="2e06b-138">loaderLock</span></span>](loaderlock-mda.md)|[<span data-ttu-id="2e06b-139">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="2e06b-139">loadFromContext</span></span>](loadfromcontext-mda.md)|
|[<span data-ttu-id="2e06b-140">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="2e06b-140">marshalCleanupError</span></span>](marshalcleanuperror-mda.md)|[<span data-ttu-id="2e06b-141">marshaling</span><span class="sxs-lookup"><span data-stu-id="2e06b-141">marshaling</span></span>](marshaling-mda.md)|
|[<span data-ttu-id="2e06b-142">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="2e06b-142">memberInfoCacheCreation</span></span>](memberinfocachecreation-mda.md)|[<span data-ttu-id="2e06b-143">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="2e06b-143">moduloObjectHashcode</span></span>](moduloobjecthashcode-mda.md)|
|[<span data-ttu-id="2e06b-144">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="2e06b-144">nonComVisibleBaseClass</span></span>](noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="2e06b-145">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="2e06b-145">notMarshalable</span></span>](notmarshalable-mda.md)|
|[<span data-ttu-id="2e06b-146">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="2e06b-146">openGenericCERCall</span></span>](opengenericcercall-mda.md)|[<span data-ttu-id="2e06b-147">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="2e06b-147">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)|
|[<span data-ttu-id="2e06b-148">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="2e06b-148">pInvokeLog</span></span>](pinvokelog-mda.md)|[<span data-ttu-id="2e06b-149">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="2e06b-149">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)|
|[<span data-ttu-id="2e06b-150">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="2e06b-150">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)|[<span data-ttu-id="2e06b-151">入</span><span class="sxs-lookup"><span data-stu-id="2e06b-151">reentrancy</span></span>](reentrancy-mda.md)|
|[<span data-ttu-id="2e06b-152">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="2e06b-152">releaseHandleFailed</span></span>](releasehandlefailed-mda.md)|[<span data-ttu-id="2e06b-153">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="2e06b-153">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)|
|[<span data-ttu-id="2e06b-154">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="2e06b-154">streamWriterBufferedDataLost</span></span>](streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="2e06b-155">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="2e06b-155">virtualCERCall</span></span>](virtualcercall-mda.md)|

<span data-ttu-id="2e06b-156">默认情况下，.NET Framework 会为所有托管调试器激活 MDA 的子集。</span><span class="sxs-lookup"><span data-stu-id="2e06b-156">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="2e06b-157">可以通过选择**Windows**  >  "**调试**" 菜单上的 "Windows**异常设置**"，然后展开 "**托管调试助手**" 列表，在 Visual Studio 中查看默认设置。</span><span class="sxs-lookup"><span data-stu-id="2e06b-157">You can view the default set in Visual Studio by choosing **Windows** > **Exception Settings** on the **Debug** menu, and then expanding the **Managed Debugging Assistants** list.</span></span>

![Visual Studio 中的 "异常设置" 窗口](./media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a><span data-ttu-id="2e06b-159">启用和禁用 Mda</span><span class="sxs-lookup"><span data-stu-id="2e06b-159">Enable and Disable MDAs</span></span>

<span data-ttu-id="2e06b-160">可使用注册表项、环境变量和应用程序配置设置，启用和禁用 MDA。</span><span class="sxs-lookup"><span data-stu-id="2e06b-160">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="2e06b-161">若要使用应用程序配置设置，必须启用注册表项或环境变量。</span><span class="sxs-lookup"><span data-stu-id="2e06b-161">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>

> [!TIP]
> <span data-ttu-id="2e06b-162">无论何时收到 MDA 通知，都可以阻止 Visual Studio 显示 MDA 对话框，而不是禁用 Mda。</span><span class="sxs-lookup"><span data-stu-id="2e06b-162">Instead of disabling MDAs, you can prevent Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="2e06b-163">为此，请**Windows**  >  在 "**调试**" 菜单上选择 "Windows**异常设置**"，展开 "**托管调试助手**" 列表，然后选中或清除单个 MDA 的 "**引发时中断**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="2e06b-163">To do that, choose **Windows** > **Exception Settings** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Break When Thrown** check box for the individual MDA.</span></span>

### <a name="registry-key"></a><span data-ttu-id="2e06b-164">注册表项</span><span class="sxs-lookup"><span data-stu-id="2e06b-164">Registry Key</span></span>

<span data-ttu-id="2e06b-165">若要启用 Mda，请添加**HKEY_LOCAL_MACHINE \software\microsoft \\ 。NETFramework\MDA**子项（类型 REG_SZ，值为1）。</span><span class="sxs-lookup"><span data-stu-id="2e06b-165">To enable MDAs, add the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA** subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="2e06b-166">将以下示例复制到一个名为*mdaenable.reg*的文本文件中。打开 Windows 注册表编辑器（RegEdit.exe），并从 "**文件**" 菜单中选择 "**导入**"。</span><span class="sxs-lookup"><span data-stu-id="2e06b-166">Copy the following example into a text file named *MDAEnable.reg*. Open the Windows Registry Editor (RegEdit.exe), and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="2e06b-167">选择*mdaenable.reg*文件以在该计算机上启用 mda。</span><span class="sxs-lookup"><span data-stu-id="2e06b-167">Select the *MDAEnable.reg* file to enable MDAs on that computer.</span></span> <span data-ttu-id="2e06b-168">将子项设置为字符串值**1** （不是 DWORD 值**1**）可启用从*APPLICATIONNAME*.mda.config 文件中读取 MDA 设置。</span><span class="sxs-lookup"><span data-stu-id="2e06b-168">Setting the subkey to string value of **1** (not DWORD value of **1**) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="2e06b-169">例如，记事本的 MDA 配置文件将命名为 notepad.exe.mda.config。</span><span class="sxs-lookup"><span data-stu-id="2e06b-169">For example, the MDA configuration file for Notepad would be named notepad.exe.mda.config.</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="2e06b-170">如果计算机在 64 位操作系统上运行 32 位应用程序，应按下方所示设置 MDA 密钥：</span><span class="sxs-lookup"><span data-stu-id="2e06b-170">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="2e06b-171">有关详细信息，请参阅[特定于应用程序的配置设置](#application-specific-configuration-settings)。</span><span class="sxs-lookup"><span data-stu-id="2e06b-171">See [Application-Specific Configuration Settings](#application-specific-configuration-settings) for more information.</span></span> <span data-ttu-id="2e06b-172">可以使用 COMPLUS_MDA 环境变量重写注册表设置。</span><span class="sxs-lookup"><span data-stu-id="2e06b-172">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="2e06b-173">有关详细信息，请参阅[环境变量](#environment-variable)。</span><span class="sxs-lookup"><span data-stu-id="2e06b-173">See [Environment Variable](#environment-variable) for more information.</span></span>

<span data-ttu-id="2e06b-174">若要禁用 Mda，请使用 Windows 注册表编辑器将 MDA 子项设置为**0** （零）。</span><span class="sxs-lookup"><span data-stu-id="2e06b-174">To disable MDAs, set the MDA subkey to **0** (zero) using the Windows Registry Editor.</span></span>

<span data-ttu-id="2e06b-175">默认情况下，即使未添加该注册表项，有些 MDA 也会在运行附加到调试器的应用程序时启用。</span><span class="sxs-lookup"><span data-stu-id="2e06b-175">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="2e06b-176">如本部分前面所述，可以通过运行*mdadisable.reg*文件来禁用这些助手。</span><span class="sxs-lookup"><span data-stu-id="2e06b-176">You can disable these assistants by running the *MDADisable.reg* file as described earlier in this section.</span></span>

### <a name="environment-variable"></a><span data-ttu-id="2e06b-177">环境变量</span><span class="sxs-lookup"><span data-stu-id="2e06b-177">Environment Variable</span></span>

<span data-ttu-id="2e06b-178">还可以通过环境变量 COMPLUS_MDA 控制 MDA 激活，此变量可重写注册表项。</span><span class="sxs-lookup"><span data-stu-id="2e06b-178">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="2e06b-179">COMPLUS_MDA 字符串是一个区分大小写、以分号分隔的 MDA 名称列表或其他特殊控制字符串。</span><span class="sxs-lookup"><span data-stu-id="2e06b-179">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="2e06b-180">在托管或非托管调试器下启动将默认启用一组 MDA。</span><span class="sxs-lookup"><span data-stu-id="2e06b-180">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="2e06b-181">这是通过在环境变量或注册表项的值前面，隐式附加默认在调试器下启用的、以分号分隔的 MDA 的列表来实现的。</span><span class="sxs-lookup"><span data-stu-id="2e06b-181">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="2e06b-182">特殊控制字符串如下所示：</span><span class="sxs-lookup"><span data-stu-id="2e06b-182">The special control strings are the following:</span></span>

- <span data-ttu-id="2e06b-183">`0` - 停用所有 MDA。</span><span class="sxs-lookup"><span data-stu-id="2e06b-183">`0` - Deactivates all MDAs.</span></span>

- <span data-ttu-id="2e06b-184">`1` - 从 ApplicationName.mda.configg 读取 MDA 设置\*\*。</span><span class="sxs-lookup"><span data-stu-id="2e06b-184">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>

- <span data-ttu-id="2e06b-185">`managedDebugger` - 显式激活在调试器下启动托管可执行文件时隐式激活的所有 MDA。</span><span class="sxs-lookup"><span data-stu-id="2e06b-185">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>

- <span data-ttu-id="2e06b-186">`unmanagedDebugger` - 显式激活在调试器下启动非托管可执行文件时隐式激活的所有 MDA。</span><span class="sxs-lookup"><span data-stu-id="2e06b-186">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>

<span data-ttu-id="2e06b-187">如果存在冲突的设置，则最新的设置将重写先前的设置：</span><span class="sxs-lookup"><span data-stu-id="2e06b-187">If there are conflicting settings, the most recent settings override previous settings:</span></span>

- <span data-ttu-id="2e06b-188">`COMPLUS_MDA=0` 禁用所有 MDA，包括那些在调试器下隐式启用的 MDA。</span><span class="sxs-lookup"><span data-stu-id="2e06b-188">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="2e06b-189">除了调试器下隐式启用的所有 MDA，`COMPLUS_MDA=gcUnmanagedToManaged` 还启用 `gcUnmanagedToManaged`。</span><span class="sxs-lookup"><span data-stu-id="2e06b-189">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="2e06b-190">`COMPLUS_MDA=0;gcUnmanagedToManaged` 启用 `gcUnmanagedToManaged`，但是禁用将在调试器下隐式启用的 MDA。</span><span class="sxs-lookup"><span data-stu-id="2e06b-190">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>

### <a name="application-specific-configuration-settings"></a><span data-ttu-id="2e06b-191">特定于应用程序的配置设置</span><span class="sxs-lookup"><span data-stu-id="2e06b-191">Application-Specific Configuration Settings</span></span>

<span data-ttu-id="2e06b-192">可以在应用程序的 MDA 配置文件中单独地启用、禁用和配置某些助手。</span><span class="sxs-lookup"><span data-stu-id="2e06b-192">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="2e06b-193">若要使用用于配置 MDA 的应用程序配置文件，必须设置 MDA 注册表项或 COMPLUS_MDA 环境变量。</span><span class="sxs-lookup"><span data-stu-id="2e06b-193">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="2e06b-194">应用程序配置文件通常与应用程序的可执行文件 (.exe) 位于同一目录中。</span><span class="sxs-lookup"><span data-stu-id="2e06b-194">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="2e06b-195">文件名的格式为*ApplicationName*.mda.config;例如，notepad.exe.mda.config。在应用程序配置文件中启用的助手可能具有专门设计用于控制该助理行为的属性或元素。</span><span class="sxs-lookup"><span data-stu-id="2e06b-195">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span>

<span data-ttu-id="2e06b-196">下面的示例演示如何启用和配置[封送处理](marshaling-mda.md)：</span><span class="sxs-lookup"><span data-stu-id="2e06b-196">The following example shows how to enable and configure the [marshaling](marshaling-mda.md):</span></span>

```xml
<mdaConfig>
  <assistants>
    <marshaling>
      <methodFilter>
        <match name="*"/>
      </methodFilter>
      <fieldFilter>
        <match name="*"/>
      </fieldFilter>
    </marshaling>
  </assistants>
</mdaConfig>
```

<span data-ttu-id="2e06b-197">对于应用程序中每个托管到非托管的转换，`Marshaling` MDA 会发出有关正封送到非托管类型的托管类型信息。</span><span class="sxs-lookup"><span data-stu-id="2e06b-197">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="2e06b-198">`Marshaling`MDA 还可以分别筛选**MethodFilter**和**fieldFilter**子元素中提供的方法和结构字段的名称。</span><span class="sxs-lookup"><span data-stu-id="2e06b-198">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the **methodFilter** and **fieldFilter** child elements, respectively.</span></span>

<span data-ttu-id="2e06b-199">下面的示例演示如何使用默认设置启用多个 Mda：</span><span class="sxs-lookup"><span data-stu-id="2e06b-199">The following example shows how to enable multiple MDAs by using their default settings:</span></span>

```xml
<mdaConfig>
  <assistants>
    <illegalPrepareConstrainedRegion />
    <invalidCERCall />
    <openGenericCERCall />
    <virtualCERCall />
  </assistants>
</mdaConfig>
```

> [!IMPORTANT]
> <span data-ttu-id="2e06b-200">若在配置文件中指定了多个助手，则必须按字母顺序列出这些助手。</span><span class="sxs-lookup"><span data-stu-id="2e06b-200">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="2e06b-201">例如，若要同时启用 `virtualCERCall` 和 `invalidCERCall` MDA，则必须先添加 `<invalidCERCall />` 项，再添加 `<virtualCERCall />` 项。</span><span class="sxs-lookup"><span data-stu-id="2e06b-201">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="2e06b-202">如果这些项未按字母顺序排列，将显示未处理的无效配置文件异常消息。</span><span class="sxs-lookup"><span data-stu-id="2e06b-202">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>

## <a name="mda-exceptions"></a><span data-ttu-id="2e06b-203">MDA 异常</span><span class="sxs-lookup"><span data-stu-id="2e06b-203">MDA exceptions</span></span>

<span data-ttu-id="2e06b-204">启用 MDA 后，即使代码未在调试器下执行，它也会处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="2e06b-204">When an MDA is enabled, it's active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="2e06b-205">如果在调试器不存在时引发 MDA 事件，尽管这不是未经处理的异常，事件消息也会出现在未经处理的异常对话框中。</span><span class="sxs-lookup"><span data-stu-id="2e06b-205">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="2e06b-206">若要避免出现该对话框，请在代码未在调试环境中执行时，移除 MDA 启用设置。</span><span class="sxs-lookup"><span data-stu-id="2e06b-206">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>

<span data-ttu-id="2e06b-207">当你的代码在 Visual Studio 集成开发环境（IDE）中执行时，你可以避免针对特定 MDA 事件显示的异常对话框。</span><span class="sxs-lookup"><span data-stu-id="2e06b-207">When your code executes in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="2e06b-208">为此，请在 "**调试**" 菜单上选择 " **Windows**  >  **异常设置**"。</span><span class="sxs-lookup"><span data-stu-id="2e06b-208">To do that, on the **Debug** menu, choose **Windows** > **Exception Settings**.</span></span> <span data-ttu-id="2e06b-209">在 "**异常设置**" 窗口中，展开 "**托管调试助手**" 列表，然后清除单个 MDA 的 "**引发时中断**" 复选框。</span><span class="sxs-lookup"><span data-stu-id="2e06b-209">In the **Exception Settings** window, expand the **Managed Debugging Assistants** list, and then clear the **Break When Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="2e06b-210">你还可以使用此对话框来*启用*MDA 异常对话框的显示。</span><span class="sxs-lookup"><span data-stu-id="2e06b-210">You can also use this dialog box to *enable* the display of MDA exception dialog boxes.</span></span>

## <a name="mda-output"></a><span data-ttu-id="2e06b-211">MDA 输出</span><span class="sxs-lookup"><span data-stu-id="2e06b-211">MDA Output</span></span>

<span data-ttu-id="2e06b-212">MDA 输出类似于下面的示例，该示例显示来自 MDA 的输出 `PInvokeStackImbalance` ：</span><span class="sxs-lookup"><span data-stu-id="2e06b-212">MDA output is similar to the following example, which shows the output from the `PInvokeStackImbalance` MDA:</span></span>

<span data-ttu-id="2e06b-213">**调用 PInvoke 函数 "MDATest！MDATest：： StdCall ' 的堆栈不平衡。这很可能是因为托管 PInvoke 签名与非托管目标签名不匹配。检查 PInvoke 签名的调用约定和参数是否与目标非托管签名匹配。**</span><span class="sxs-lookup"><span data-stu-id="2e06b-213">**A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="see-also"></a><span data-ttu-id="2e06b-214">请参阅</span><span class="sxs-lookup"><span data-stu-id="2e06b-214">See also</span></span>

- [<span data-ttu-id="2e06b-215">调试、跟踪和分析</span><span class="sxs-lookup"><span data-stu-id="2e06b-215">Debugging, Tracing, and Profiling</span></span>](index.md)
