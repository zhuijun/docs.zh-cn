---
title: 如何调试 CLR 激活问题
description: 请参阅如何调试 .NET 中的公共语言运行时 (CLR) 激活问题。 查看和调试 CLR 激活日志，这在确定根本原因时可能很有用。
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
ms.openlocfilehash: 5215e82aebf93fa8d6d1937563ab348126a01d97
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622609"
---
# <a name="how-to-debug-clr-activation-issues"></a><span data-ttu-id="ac091-104">如何调试 CLR 激活问题</span><span class="sxs-lookup"><span data-stu-id="ac091-104">How to debug CLR activation issues</span></span>

<span data-ttu-id="ac091-105">如果在使用正确版本的公共语言运行时 (CLR) 运行应用程序时遇到问题，可以查看和调试 CLR 激活日志。</span><span class="sxs-lookup"><span data-stu-id="ac091-105">If you encounter problems in getting your application to run with the correct version of the common language runtime (CLR), you can view and debug CLR activation logs.</span></span> <span data-ttu-id="ac091-106">如果应用程序加载不同于预期的 CLR 版本或者根本未加载 CLR，这些日志对于确定激活问题的根本原因非常有用。</span><span class="sxs-lookup"><span data-stu-id="ac091-106">These logs can be very useful in determining the root cause of an activation issue, when your application either loads a different CLR version than expected or doesn't load the CLR at all.</span></span> <span data-ttu-id="ac091-107">[.NET Framework 初始化错误：管理用户体验](initialization-errors-managing-the-user-experience.md)中探讨了未能找到应用程序 CLR 的体验。</span><span class="sxs-lookup"><span data-stu-id="ac091-107">The [.NET Framework Initialization Errors: Managing the User Experience](initialization-errors-managing-the-user-experience.md) discusses the experience when no CLR is found for an application.</span></span>

<span data-ttu-id="ac091-108">可以通过使用 HKEY_LOCAL_MACHINE 注册表项或系统环境变量在系统范围内启用 CLR 激活日志记录。</span><span class="sxs-lookup"><span data-stu-id="ac091-108">CLR activation logging can be enabled system-wide by using an HKEY_LOCAL_MACHINE registry key or a system environment variable.</span></span> <span data-ttu-id="ac091-109">在删除注册表项或环境变量前，将持续生成日志。</span><span class="sxs-lookup"><span data-stu-id="ac091-109">The log will be generated until the registry entry or the environment variable is removed.</span></span> <span data-ttu-id="ac091-110">或者，可以使用用户或进程局部环境变量来启用具有不同范围和持续时间的日志记录。</span><span class="sxs-lookup"><span data-stu-id="ac091-110">Alternatively, you can use a user or process-local environment variable to enable logging with a different scope and duration.</span></span>

<span data-ttu-id="ac091-111">CLR 激活日志不应与[程序集绑定日志](../tools/fuslogvw-exe-assembly-binding-log-viewer.md)混淆，两者完全不同。</span><span class="sxs-lookup"><span data-stu-id="ac091-111">CLR activation logs shouldn't be confused with [assembly binding logs](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), which are entirely different.</span></span>

## <a name="to-enable-clr-activation-logging"></a><span data-ttu-id="ac091-112">启用 CLR 激活日志记录</span><span class="sxs-lookup"><span data-stu-id="ac091-112">To enable CLR activation logging</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="ac091-113">使用注册表</span><span class="sxs-lookup"><span data-stu-id="ac091-113">Using the registry</span></span>

1. <span data-ttu-id="ac091-114">在注册表编辑器中，导航到 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework（在 32 位计算机上）或 HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework 文件夹（在 64 位计算机上）。</span><span class="sxs-lookup"><span data-stu-id="ac091-114">In the Registry Editor, navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework (on a 32-bit computer) or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework folder (on a 64-bit computer).</span></span>

2. <span data-ttu-id="ac091-115">添加名为 `CLRLoadLogDir` 的字符串值，并将其设置为要存储 CLR 激活日志的现有目录的完整路径。</span><span class="sxs-lookup"><span data-stu-id="ac091-115">Add a string value named `CLRLoadLogDir`, and set it to the full path of an existing directory where you'd like to store CLR activation logs.</span></span>

<span data-ttu-id="ac091-116">保持启用激活记录，直至删除字符串值。</span><span class="sxs-lookup"><span data-stu-id="ac091-116">Activation logging remains enabled until you remove the string value.</span></span>

### <a name="using-an-environment-variable"></a><span data-ttu-id="ac091-117">使用环境变量</span><span class="sxs-lookup"><span data-stu-id="ac091-117">Using an environment variable</span></span>

- <span data-ttu-id="ac091-118">将 `COMPLUS_CLRLoadLogDir` 环境变量设置为字符串，该字符串表示要存储 CLR 激活日志的现有目录的完整路径。</span><span class="sxs-lookup"><span data-stu-id="ac091-118">Set the `COMPLUS_CLRLoadLogDir` environment variable to a string that represents the full path of an existing directory where you'd like to store CLR activation logs.</span></span>

    <span data-ttu-id="ac091-119">环境变量的设置方式将决定其作用域：</span><span class="sxs-lookup"><span data-stu-id="ac091-119">How you set the environment variable determines its scope:</span></span>

  - <span data-ttu-id="ac091-120">如果在系统级别进行设置，将对该计算机上的所有 .NET Framework 应用程序启用激活日志记录，直至删除环境变量。</span><span class="sxs-lookup"><span data-stu-id="ac091-120">If you set it at the system level, activation logging is enabled for all .NET Framework applications on that computer until the environment variable is removed.</span></span>

  - <span data-ttu-id="ac091-121">如果在用户级别进行设置，则仅对当前用户帐户启用激活日志记录。</span><span class="sxs-lookup"><span data-stu-id="ac091-121">If you set it at the user level, activation logging is enabled only for the current user account.</span></span> <span data-ttu-id="ac091-122">在删除环境变量前，将持续记录。</span><span class="sxs-lookup"><span data-stu-id="ac091-122">Logging continues until the environment variable is removed.</span></span>

  - <span data-ttu-id="ac091-123">如果在加载 CLR 前，从进程内进行设置，将在进程终止前持续启用激活日志记录。</span><span class="sxs-lookup"><span data-stu-id="ac091-123">If you set it from within the process before loading the CLR, activation logging is enabled until the process terminates.</span></span>

  - <span data-ttu-id="ac091-124">如果在运行应用程序之前，在命令提示符下进行设置，将对通过该命令提示符运行的任意应用程序启用激活日志记录。</span><span class="sxs-lookup"><span data-stu-id="ac091-124">If you set it at a command prompt before you run an application, activation logging is enabled for any application that is run from that command prompt.</span></span>

    <span data-ttu-id="ac091-125">例如，若要将激活日志存储在具有进程级作用域的 c:\clrloadlogs 目录中，请在运行应用程序之前打开“命令提示符”窗口并键入以下内容：</span><span class="sxs-lookup"><span data-stu-id="ac091-125">For example, to store activation logs in the c:\clrloadlogs directory with process-level scope, open a Command Prompt window and type the following before you run the application:</span></span>

    ```console
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs
    ```

## <a name="example"></a><span data-ttu-id="ac091-126">示例</span><span class="sxs-lookup"><span data-stu-id="ac091-126">Example</span></span>

<span data-ttu-id="ac091-127">CLR 激活日志提供大量关于 CLR 激活和 CLR 宿主 API 的用法的数据。</span><span class="sxs-lookup"><span data-stu-id="ac091-127">CLR activation logs provide a large amount of data about CLR activation and the use of the CLR hosting APIs.</span></span> <span data-ttu-id="ac091-128">如本文所述，大部分数据由 Microsoft 内部使用，但有些数据对开发人员也非常有用。</span><span class="sxs-lookup"><span data-stu-id="ac091-128">Most of this data is used internally by Microsoft, but some of the data can also be useful to developers, as described in this article.</span></span>

<span data-ttu-id="ac091-129">日志反映了 CLR 宿主 API 的调用顺序。</span><span class="sxs-lookup"><span data-stu-id="ac091-129">The log reflects the order in which the CLR hosting APIs were called.</span></span> <span data-ttu-id="ac091-130">它还包括有关计算机上检测到的已安装运行时集的有用数据。</span><span class="sxs-lookup"><span data-stu-id="ac091-130">It also includes useful data about the set of installed runtimes detected on the computer.</span></span> <span data-ttu-id="ac091-131">CLR 激活日志格式本身不进行存档，但可用于帮助需要解决 CLR 激活问题的开发人员。</span><span class="sxs-lookup"><span data-stu-id="ac091-131">The CLR activation log format is not itself documented, but can be used to aid developers who need to resolve CLR activation issues.</span></span>

> [!NOTE]
> <span data-ttu-id="ac091-132">在使用该 CLR 的进程终止前，无法打开激活日志。</span><span class="sxs-lookup"><span data-stu-id="ac091-132">You cannot open an activation log until the process that uses the CLR has terminated.</span></span>

> [!NOTE]
> <span data-ttu-id="ac091-133">CLR 激活日志未进行本地化；它们始终用英语生成。</span><span class="sxs-lookup"><span data-stu-id="ac091-133">CLR activation logs are not localized; they are always generated in the English language.</span></span>

<span data-ttu-id="ac091-134">在下面的激活日志示例中，日志后面突出显示和说明了最有用的信息。</span><span class="sxs-lookup"><span data-stu-id="ac091-134">In the following example of an activation log, the most useful information is highlighted and described after the log.</span></span>

```output
532,205950.367,CLR Loading log for C:\Tests\myapp.exe
532,205950.367,Log started at 4:26:12 PM on 10/6/2011
532,205950.367,-----------------------------------
532,205950.382,FunctionCall: _CorExeMain
532,205950.382,FunctionCall: ClrCreateInstance, Clsid: {2EBCD49A-1B47-4A61-B13A-4A03701E594B}, Iid: {E2190695-77B2-492E-8E14-C4B3A7FDD593}
532,205950.382,MethodCall: ICLRMetaHostPolicy::GetRequestedRuntime. Version: (null), Metahost Policy Flags: 0x168, Binary: (null), Iid: {BD39D1D2-BA2F-486A-89B0-B4B0CB466891}
532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
532,205950.382,Input values for ComputeVersionString follow this line
532,205950.382,-----------------------------------
532,205950.382,Default Application Name: C:\Tests\myapp.exe
532,205950.382,IsLegacyBind is: 0
532,205950.382,IsCapped is 0
532,205950.382,SkuCheckFlags are 0
532,205950.382,ShouldEmulateExeLaunch is 0
532,205950.382,LegacyBindRequired is 0
532,205950.382,-----------------------------------
532,205950.382,Parsing config file: C:\Tests\myapp.exe
532,205950.382,UseLegacyV2RuntimeActivationPolicy is set to 0
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe
532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
532,205950.382,ERROR: Version v2.0.50727 is not present on the machine.
532,205950.398,SEM_FAILCRITICALERRORS is set to 0
532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
532,205950.398,FunctionCall: RealDllMain. Reason: 0
532,205950.398,FunctionCall: OnShimDllMainCalled. Reason: 0
```

- <span data-ttu-id="ac091-135">CLR 加载日志提供启动加载托管代码的进程的可执行文件的路径。</span><span class="sxs-lookup"><span data-stu-id="ac091-135">**CLR Loading log** provides the path to the executable that started the process that loaded managed code.</span></span> <span data-ttu-id="ac091-136">请注意，这可能是本地主机。</span><span class="sxs-lookup"><span data-stu-id="ac091-136">Note that this could be a native host.</span></span>

    ```output
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe
    ```

- <span data-ttu-id="ac091-137">安装的运行时是安装在计算机上作为激活请求的候选项的 CLR 版本集。</span><span class="sxs-lookup"><span data-stu-id="ac091-137">**Installed Runtime** is the set of CLR versions installed on the computer that are candidates for the activation request.</span></span>

    ```output
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
    ```

- <span data-ttu-id="ac091-138">生成所用版本是在生成向 [ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).等方法提供的二进制文件时所用的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="ac091-138">**built with version** is the version of the CLR that was used to build the binary that was provided to a method such as [ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span></span>

    ```output
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
    ```

- <span data-ttu-id="ac091-139">功能按需安装是指在 Windows 8 上启用 .NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="ac091-139">**feature-on-demand installation** refers to enabling the .NET Framework 3.5 on Windows 8.</span></span> <span data-ttu-id="ac091-140">请参阅 [.NET Framework 初始化错误：管理用户体验](initialization-errors-managing-the-user-experience.md)，获取有关此方案的详细信息。</span><span class="sxs-lookup"><span data-stu-id="ac091-140">See [.NET Framework Initialization Errors: Managing the User Experience](initialization-errors-managing-the-user-experience.md) for more information about this scenario.</span></span>

    ```output
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
    ```

## <a name="see-also"></a><span data-ttu-id="ac091-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="ac091-141">See also</span></span>

- [<span data-ttu-id="ac091-142">部署</span><span class="sxs-lookup"><span data-stu-id="ac091-142">Deployment</span></span>](index.md)
- [<span data-ttu-id="ac091-143">如何：将应用配置为支持 .NET Framework 4 或更高版本</span><span class="sxs-lookup"><span data-stu-id="ac091-143">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
