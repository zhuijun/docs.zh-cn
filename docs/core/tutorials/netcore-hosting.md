---
title: 编写自定义 .NET Core 运行时主机
description: 了解从本机代码托管 .NET Core 运行时，以支持需要控制 .NET Core 运行时工作方式的高级方案。
author: mjrousos
ms.topic: how-to
ms.date: 12/21/2018
ms.openlocfilehash: 2324b61bcffb686a455fcfd154284a2b78aa746b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283489"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a><span data-ttu-id="ff333-103">编写自定义 .NET Core 主机以从本机代码控制 .NET 运行时</span><span class="sxs-lookup"><span data-stu-id="ff333-103">Write a custom .NET Core host to control the .NET runtime from your native code</span></span>

<span data-ttu-id="ff333-104">像所有的托管代码一样，.NET Core 应用程序也由主机执行。</span><span class="sxs-lookup"><span data-stu-id="ff333-104">Like all managed code, .NET Core applications are executed by a host.</span></span> <span data-ttu-id="ff333-105">主机负责启动运行时（包括 JIT 和垃圾回收器等组件）和调用托管的入口点。</span><span class="sxs-lookup"><span data-stu-id="ff333-105">The host is responsible for starting the runtime (including components like the JIT and garbage collector) and invoking managed entry points.</span></span>

<span data-ttu-id="ff333-106">托管 .NET Core 运行时是高级方案，在大多数情况下，.NET Core 开发人员无需担心托管问题，因为 .NET Core 生成过程会提供默认主机来运行 .NET Core 应用程序。</span><span class="sxs-lookup"><span data-stu-id="ff333-106">Hosting the .NET Core runtime is an advanced scenario and, in most cases, .NET Core developers don't need to worry about hosting because .NET Core build processes provide a default host to run .NET Core applications.</span></span> <span data-ttu-id="ff333-107">虽然在某些特殊情况下，它对显式托管 .NET Core 运行时非常有用 - 无论是作为一种在本机进程中调用托管代码的方式还是为了获得对运行时工作原理更好的控制。</span><span class="sxs-lookup"><span data-stu-id="ff333-107">In some specialized circumstances, though, it can be useful to explicitly host the .NET Core runtime, either as a means of invoking managed code in a native process or in order to gain more control over how the runtime works.</span></span>

<span data-ttu-id="ff333-108">本文概述了从本机代码启动 .NET Core 运行时和在其中执行托管代码的必要步骤。</span><span class="sxs-lookup"><span data-stu-id="ff333-108">This article gives an overview of the steps necessary to start the .NET Core runtime from native code and execute managed code in it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ff333-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="ff333-109">Prerequisites</span></span>

<span data-ttu-id="ff333-110">由于主机是本机应用程序，所以本教程将介绍如何构造 C++ 应用程序以托管 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="ff333-110">Because hosts are native applications, this tutorial covers constructing a C++ application to host .NET Core.</span></span> <span data-ttu-id="ff333-111">将需要一个 C++ 开发环境（例如，[Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) 提供的环境）。</span><span class="sxs-lookup"><span data-stu-id="ff333-111">You will need a C++ development environment (such as that provided by [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)).</span></span>

<span data-ttu-id="ff333-112">还将需要一个简单的 .NET Core 应用程序来测试主机，因此应安装 [.NET Core SDK](https://dotnet.microsoft.com/download) 并[构建一个小型的 .NET Core 测试应用](with-visual-studio.md)（例如，“Hello World”应用）。</span><span class="sxs-lookup"><span data-stu-id="ff333-112">You will also want a simple .NET Core application to test the host with, so you should install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [build a small .NET Core test app](with-visual-studio.md) (such as a 'Hello World' app).</span></span> <span data-ttu-id="ff333-113">使用通过新 .NET Core 控制台项目模板创建的“Hello World”应用就足够了。</span><span class="sxs-lookup"><span data-stu-id="ff333-113">The 'Hello World' app created by the new .NET Core console project template is sufficient.</span></span>

## <a name="hosting-apis"></a><span data-ttu-id="ff333-114">承载 API</span><span class="sxs-lookup"><span data-stu-id="ff333-114">Hosting APIs</span></span>
<span data-ttu-id="ff333-115">可以使用三种不同的 API 来托管 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="ff333-115">There are three different APIs that can be used to host .NET Core.</span></span> <span data-ttu-id="ff333-116">本文（及其相关的[示例](https://github.com/dotnet/samples/tree/master/core/hosting)）涵盖所有选项。</span><span class="sxs-lookup"><span data-stu-id="ff333-116">This article (and its associated [samples](https://github.com/dotnet/samples/tree/master/core/hosting)) covers all options.</span></span>

* <span data-ttu-id="ff333-117">在 .NET Core 3.0 及更高版本中托管 .NET Core 运行时的首选方法是借助 `nethost` 和 `hostfxr` 库的 API。</span><span class="sxs-lookup"><span data-stu-id="ff333-117">The preferred method of hosting the .NET Core runtime in .NET Core 3.0 and above is with the `nethost` and `hostfxr` libraries' APIs.</span></span> <span data-ttu-id="ff333-118">由这些入口点来处理查找和设置运行时进行初始化所遇到的复杂性；通过它们，还可启动托管应用程序和调用静态托管方法。</span><span class="sxs-lookup"><span data-stu-id="ff333-118">These entry points handle the complexity of finding and setting up the runtime for initialization and allow both launching a managed application and calling into a static managed method.</span></span>
* <span data-ttu-id="ff333-119">托管低于 .NET Core 3.0 的 .NET Core 运行时的首选方法是使用 [CoreClrHost.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/hosts/inc/coreclrhost.h) API。</span><span class="sxs-lookup"><span data-stu-id="ff333-119">The preferred method of hosting the .NET Core runtime prior to .NET Core 3.0 is with the [CoreClrHost.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/hosts/inc/coreclrhost.h) API.</span></span> <span data-ttu-id="ff333-120">此 API 公开一些函数，用于轻松地启动和停止运行时并调用托管代码（通过启动托管 exe 或通过调用静态托管方法）。</span><span class="sxs-lookup"><span data-stu-id="ff333-120">This API exposes functions for easily starting and stopping the runtime and invoking managed code (either by launching a managed exe or by calling static managed methods).</span></span>
* <span data-ttu-id="ff333-121">也可以使用 [mscoree.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/mscoree.h) 中的 `ICLRRuntimeHost4` 接口承载 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="ff333-121">.NET Core can also be hosted with the `ICLRRuntimeHost4` interface in [mscoree.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/mscoree.h).</span></span> <span data-ttu-id="ff333-122">此 API 比 CoreClrHost.h 出现的时间更早，因此你可能看到过使用此 API 的较旧版本的主机。</span><span class="sxs-lookup"><span data-stu-id="ff333-122">This API has been around longer than CoreClrHost.h, so you may have seen older hosts using it.</span></span> <span data-ttu-id="ff333-123">它仍然可用，并且比起 CoreClrHost，它可以对主机进程进行更多控制。</span><span class="sxs-lookup"><span data-stu-id="ff333-123">It still works and allows a bit more control over the hosting process than CoreClrHost.</span></span> <span data-ttu-id="ff333-124">但是对于大多数方案，CoreClrHost.h 现在是首选，因为它的 API 更简单。</span><span class="sxs-lookup"><span data-stu-id="ff333-124">For most scenarios, though, CoreClrHost.h is preferred now because of its simpler APIs.</span></span>

## <a name="sample-hosts"></a><span data-ttu-id="ff333-125">示例主机</span><span class="sxs-lookup"><span data-stu-id="ff333-125">Sample Hosts</span></span>

<span data-ttu-id="ff333-126">有关展示在下面的教程中所述步骤的[示例主机](https://github.com/dotnet/samples/tree/master/core/hosting)，请访问 dotnet/samples GitHub 存储库。</span><span class="sxs-lookup"><span data-stu-id="ff333-126">[Sample hosts](https://github.com/dotnet/samples/tree/master/core/hosting) demonstrating the steps outlined in the tutorials below are available in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="ff333-127">该示例中的注释清楚地将这些教程中已编号的步骤与它们在示例中的执行位置关联。</span><span class="sxs-lookup"><span data-stu-id="ff333-127">Comments in the samples clearly associate the numbered steps from these tutorials with where they're performed in the sample.</span></span> <span data-ttu-id="ff333-128">有关下载说明，请参阅[示例和教程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="ff333-128">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="ff333-129">请记住，示例主机的用途在于提供学习指导，在纠错方面不甚严谨，其重在可读性而非效率。</span><span class="sxs-lookup"><span data-stu-id="ff333-129">Keep in mind that the sample hosts are meant to be used for learning purposes, so they are light on error checking and are designed to emphasize readability over efficiency.</span></span>

## <a name="create-a-host-using-nethosth-and-hostfxrh"></a><span data-ttu-id="ff333-130">使用 NetHost.h 和 HostFxr.h 创建主机</span><span class="sxs-lookup"><span data-stu-id="ff333-130">Create a host using NetHost.h and HostFxr.h</span></span>

<span data-ttu-id="ff333-131">以下步骤详细说明如何使用 `nethost` 和 `hostfxr` 库在本机应用程序中启动 .NET Core 运行时并调用托管静态方法。</span><span class="sxs-lookup"><span data-stu-id="ff333-131">The following steps detail how to use the `nethost` and `hostfxr` libraries to start the .NET Core runtime in a native application and call into a managed static method.</span></span> <span data-ttu-id="ff333-132">[示例](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr)使用安装了 .NET SDK 的 `nethost` 标头和库，并从 [dotnet/core-setup](https://github.com/dotnet/core-setup) 复制 [`coreclr_delegates.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/coreclr_delegates.h) 和 [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) 文件。</span><span class="sxs-lookup"><span data-stu-id="ff333-132">The [sample](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr) uses the `nethost` header and library installed with the .NET SDK and copies of the [`coreclr_delegates.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/coreclr_delegates.h) and [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) files from the [dotnet/core-setup](https://github.com/dotnet/core-setup) repository.</span></span>

### <a name="step-1---load-hostfxr-and-get-exported-hosting-functions"></a><span data-ttu-id="ff333-133">步骤 1 - 加载 HostFxr 并获取导出的托管函数</span><span class="sxs-lookup"><span data-stu-id="ff333-133">Step 1 - Load HostFxr and get exported hosting functions</span></span>

<span data-ttu-id="ff333-134">`nethost` 库提供用于查找 `hostfxr` 库的 `get_hostfxr_path` 函数。</span><span class="sxs-lookup"><span data-stu-id="ff333-134">The `nethost` library provides the `get_hostfxr_path` function for locating the `hostfxr` library.</span></span> <span data-ttu-id="ff333-135">`hostfxr` 库公开用于托管 .NET Core 运行时的函数。</span><span class="sxs-lookup"><span data-stu-id="ff333-135">The `hostfxr` library exposes functions for hosting the .NET Core runtime.</span></span> <span data-ttu-id="ff333-136">函数的完整列表可在 [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) 和[本机托管设计文档](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/native-hosting.md)中找到。</span><span class="sxs-lookup"><span data-stu-id="ff333-136">The full list of functions can be found in [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) and the [native hosting design document](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/native-hosting.md).</span></span> <span data-ttu-id="ff333-137">示例和本教程使用以下函数：</span><span class="sxs-lookup"><span data-stu-id="ff333-137">The sample and this tutorial use the following:</span></span>

* <span data-ttu-id="ff333-138">`hostfxr_initialize_for_runtime_config`：初始化主机上下文，并使用指定的运行时配置准备初始化 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="ff333-138">`hostfxr_initialize_for_runtime_config`: Initializes a host context and prepares for initialization of the .NET Core runtime using the specified runtime configuration.</span></span>
* <span data-ttu-id="ff333-139">`hostfxr_get_runtime_delegate`：获取对运行时功能的委托。</span><span class="sxs-lookup"><span data-stu-id="ff333-139">`hostfxr_get_runtime_delegate`: Gets a delegate for runtime functionality.</span></span>
* <span data-ttu-id="ff333-140">`hostfxr_close`：关闭主机上下文。</span><span class="sxs-lookup"><span data-stu-id="ff333-140">`hostfxr_close`: Closes a host context.</span></span>

<span data-ttu-id="ff333-141">使用 `get_hostfxr_path` 找到了 `hostfxr` 库。</span><span class="sxs-lookup"><span data-stu-id="ff333-141">The `hostfxr` library is found using `get_hostfxr_path`.</span></span> <span data-ttu-id="ff333-142">随后加载此库并检索其导出。</span><span class="sxs-lookup"><span data-stu-id="ff333-142">It is then loaded and its exports are retrieved.</span></span>

[!code-cpp[HostFxrHost#LoadHostFxr](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadHostFxr)]

### <a name="step-2---initialize-and-start-the-net-core-runtime"></a><span data-ttu-id="ff333-143">步骤 2 - 初始化和启动 .NET Core 运行时</span><span class="sxs-lookup"><span data-stu-id="ff333-143">Step 2 - Initialize and start the .NET Core runtime</span></span>

<span data-ttu-id="ff333-144">`hostfxr_initialize_for_runtime_config` 和 `hostfxr_get_runtime_delegate` 函数使用将加载的托管组件的运行时配置初始化并启动 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="ff333-144">The `hostfxr_initialize_for_runtime_config` and `hostfxr_get_runtime_delegate` functions initialize and start the .NET Core runtime using the runtime configuration for the managed component that will be loaded.</span></span> <span data-ttu-id="ff333-145">`hostfxr_get_runtime_delegate` 函数用于获取运行时委托，允许加载托管程序集并获取指向该程序集中的静态方法的函数指针。</span><span class="sxs-lookup"><span data-stu-id="ff333-145">The `hostfxr_get_runtime_delegate` function is used to get a runtime delegate that allows loading a managed assembly and getting a function pointer to a static method in that assembly.</span></span>

[!code-cpp[HostFxrHost#Initialize](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#Initialize)]

### <a name="step-3---load-managed-assembly-and-get-function-pointer-to-a-managed-method"></a><span data-ttu-id="ff333-146">步骤 3 - 加载托管程序集并获取指向托管方法的函数指针</span><span class="sxs-lookup"><span data-stu-id="ff333-146">Step 3 - Load managed assembly and get function pointer to a managed method</span></span>

<span data-ttu-id="ff333-147">将调用运行时委托以加载托管程序集并获取指向托管方法的函数指针。</span><span class="sxs-lookup"><span data-stu-id="ff333-147">The runtime delegate is called to load the managed assembly and get a function pointer to a managed method.</span></span> <span data-ttu-id="ff333-148">委托需要程序集路径、类型名称和方法名称作为输入，并返回可用于调用托管方法的函数指针。</span><span class="sxs-lookup"><span data-stu-id="ff333-148">The delegate requires the assembly path, type name, and method name as inputs and returns a function pointer that can be used to invoke the managed method.</span></span>

[!code-cpp[HostFxrHost#LoadAndGet](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadAndGet)]

<span data-ttu-id="ff333-149">该示例通过在调用运行时委托时将 `nullptr` 作为委托类型名称传递，对托管方法使用默认签名：</span><span class="sxs-lookup"><span data-stu-id="ff333-149">By passing `nullptr` as the delegate type name when calling the runtime delegate, the sample uses a default signature for the managed method:</span></span>

```csharp
public delegate int ComponentEntryPoint(IntPtr args, int sizeBytes);
```

<span data-ttu-id="ff333-150">可以通过在调用运行时委托时指定委托类型名称来使用其他签名。</span><span class="sxs-lookup"><span data-stu-id="ff333-150">A different signature can be used by specifying the delegate type name when calling the runtime delegate.</span></span>

### <a name="step-4---run-managed-code"></a><span data-ttu-id="ff333-151">步骤 4 - 运行托管代码！</span><span class="sxs-lookup"><span data-stu-id="ff333-151">Step 4 - Run managed code!</span></span>

<span data-ttu-id="ff333-152">本机主机现在可以调用托管方法，并向其传递所需的参数。</span><span class="sxs-lookup"><span data-stu-id="ff333-152">The native host can now call the managed method and pass it the desired parameters.</span></span>

[!code-cpp[HostFxrHost#CallManaged](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#CallManaged)]

## <a name="create-a-host-using-coreclrhosth"></a><span data-ttu-id="ff333-153">使用 CoreClrHost.h 创建主机</span><span class="sxs-lookup"><span data-stu-id="ff333-153">Create a host using CoreClrHost.h</span></span>

<span data-ttu-id="ff333-154">以下步骤详细说明如何使用 CoreClrHost.h API 在本机应用程序中启动 .NET Core 运行时并调用托管静态方法。</span><span class="sxs-lookup"><span data-stu-id="ff333-154">The following steps detail how to use the CoreClrHost.h API to start the .NET Core runtime in a native application and call into a managed static method.</span></span> <span data-ttu-id="ff333-155">本文档中的代码片段使用一些特定于 Windows 的 API，但是[完整示例主机](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost)同时显示 Windows 和 Linux 的代码路径。</span><span class="sxs-lookup"><span data-stu-id="ff333-155">The code snippets in this document use some Windows-specific APIs, but the [full sample host](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost) shows both Windows and Linux code paths.</span></span>

<span data-ttu-id="ff333-156">[Unix CoreRun 主机](https://github.com/dotnet/runtime/tree/master/src/coreclr/src/hosts/unixcorerun)显示使用 coreclrhost.h 的更为复杂的真实托管示例。</span><span class="sxs-lookup"><span data-stu-id="ff333-156">The [Unix CoreRun host](https://github.com/dotnet/runtime/tree/master/src/coreclr/src/hosts/unixcorerun) shows a more complex, real-world example of hosting using coreclrhost.h.</span></span>

### <a name="step-1---find-and-load-coreclr"></a><span data-ttu-id="ff333-157">步骤 1 - 查找和加载 CoreCLR</span><span class="sxs-lookup"><span data-stu-id="ff333-157">Step 1 - Find and load CoreCLR</span></span>

<span data-ttu-id="ff333-158">.NET Core 运行时 API 位于 coreclr.dll（对于 Windows）、libcoreclr.so（对于 Linux）或 libcoreclr.dylib（对于 macOS）  。</span><span class="sxs-lookup"><span data-stu-id="ff333-158">The .NET Core runtime APIs are in *coreclr.dll* (on Windows), in *libcoreclr.so* (on Linux), or in *libcoreclr.dylib* (on macOS).</span></span> <span data-ttu-id="ff333-159">承载 .NET Core 的第一步是加载 CoreCLR 库。</span><span class="sxs-lookup"><span data-stu-id="ff333-159">The first step to hosting .NET Core is to load the CoreCLR library.</span></span> <span data-ttu-id="ff333-160">一些主机探测不同的路径或使用输入参数来查找库，而另一些主机能够从某个路径（例如，紧邻主机的路径，或从计算机范围内的位置）加载库。</span><span class="sxs-lookup"><span data-stu-id="ff333-160">Some hosts probe different paths or use input parameters to find the library while others know to load it from a certain path (next to the host, for example, or from a machine-wide location).</span></span>

<span data-ttu-id="ff333-161">找到库之后，系统会使用 `LoadLibraryEx`（对于 Windows）或 `dlopen`（对于 Linux/macOS）加载库。</span><span class="sxs-lookup"><span data-stu-id="ff333-161">Once found, the library is loaded with `LoadLibraryEx` (on Windows) or `dlopen` (on Linux/macOS).</span></span>

[!code-cpp[CoreClrHost#1](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a><span data-ttu-id="ff333-162">步骤 2 - 获取 .NET Core 承载函数</span><span class="sxs-lookup"><span data-stu-id="ff333-162">Step 2 - Get .NET Core hosting functions</span></span>

<span data-ttu-id="ff333-163">CoreClrHost 有几个可用于承载 .NET Core 的重要方法：</span><span class="sxs-lookup"><span data-stu-id="ff333-163">CoreClrHost has several important methods useful for hosting .NET Core:</span></span>

* <span data-ttu-id="ff333-164">`coreclr_initialize`：启动 .NET Core 运行时并设置默认（且仅设置）AppDomain。</span><span class="sxs-lookup"><span data-stu-id="ff333-164">`coreclr_initialize`: Starts the .NET Core runtime and sets up the default (and only) AppDomain.</span></span>
* <span data-ttu-id="ff333-165">`coreclr_execute_assembly`：执行托管程序集。</span><span class="sxs-lookup"><span data-stu-id="ff333-165">`coreclr_execute_assembly`: Executes a managed assembly.</span></span>
* <span data-ttu-id="ff333-166">`coreclr_create_delegate`：创建指向托管方法的函数指针。</span><span class="sxs-lookup"><span data-stu-id="ff333-166">`coreclr_create_delegate`: Creates a function pointer to a managed method.</span></span>
* <span data-ttu-id="ff333-167">`coreclr_shutdown`：关闭 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="ff333-167">`coreclr_shutdown`: Shuts down the .NET Core runtime.</span></span>
* <span data-ttu-id="ff333-168">`coreclr_shutdown_2`：如 `coreclr_shutdown`，但还会检索托管代码的退出代码。</span><span class="sxs-lookup"><span data-stu-id="ff333-168">`coreclr_shutdown_2`: Like `coreclr_shutdown`, but also retrieves the managed code's exit code.</span></span>

<span data-ttu-id="ff333-169">加载 CoreCLR 库之后，下一步是使用 `GetProcAddress`（对于 Windows）或 `dlsym`（对于 Linux/macOS）引用这些函数。</span><span class="sxs-lookup"><span data-stu-id="ff333-169">After loading the CoreCLR library, the next step is to get references to these functions using `GetProcAddress` (on Windows) or `dlsym` (on Linux/macOS).</span></span>

[!code-cpp[CoreClrHost#2](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a><span data-ttu-id="ff333-170">步骤 3 - 准备运行时属性</span><span class="sxs-lookup"><span data-stu-id="ff333-170">Step 3 - Prepare runtime properties</span></span>

<span data-ttu-id="ff333-171">在启动运行时之前，有必要准备一些属性来指定行为（特别是关于程序集加载器的行为）。</span><span class="sxs-lookup"><span data-stu-id="ff333-171">Before starting the runtime, it is necessary to prepare some properties to specify behavior (especially concerning the assembly loader).</span></span>

<span data-ttu-id="ff333-172">常用属性包括：</span><span class="sxs-lookup"><span data-stu-id="ff333-172">Common properties include:</span></span>

* <span data-ttu-id="ff333-173">`TRUSTED_PLATFORM_ASSEMBLIES` 这是程序集路径列表（对于 Windows，使用“;”分隔，对于 Linux，使用“:”分隔），运行时在默认情况下能够解析这些路径。</span><span class="sxs-lookup"><span data-stu-id="ff333-173">`TRUSTED_PLATFORM_ASSEMBLIES` This is a list of assembly paths (delimited by ';' on Windows and ':' on Linux) which the runtime will be able to resolve by default.</span></span> <span data-ttu-id="ff333-174">一些主机有硬编码清单，其中列出了它们可以加载的程序集。</span><span class="sxs-lookup"><span data-stu-id="ff333-174">Some hosts have hard-coded manifests listing assemblies they can load.</span></span> <span data-ttu-id="ff333-175">其他主机将把任何库放在这个列表上的特定位置（例如 coreclr.dll 旁边）。</span><span class="sxs-lookup"><span data-stu-id="ff333-175">Others will put any library in certain locations (next to *coreclr.dll*, for example) on this list.</span></span>
* <span data-ttu-id="ff333-176">`APP_PATHS` 这是一个用来探测程序集的路径的列表（如果在受信任的平台程序集 (TPA) 列表中找不到程序集）。</span><span class="sxs-lookup"><span data-stu-id="ff333-176">`APP_PATHS` This is a list of paths to probe in for an assembly if it can't be found in the trusted platform assemblies (TPA) list.</span></span> <span data-ttu-id="ff333-177">因为主机使用 TPA 列表可以更好地控制加载哪些程序集，所以对于主机来说，确定要加载的程序集并显式列出它们是最佳做法。</span><span class="sxs-lookup"><span data-stu-id="ff333-177">Because the host has more control over which assemblies are loaded using the TPA list, it is a best practice for hosts to determine which assemblies they expect to load and list them explicitly.</span></span> <span data-ttu-id="ff333-178">但是，如果需要探测运行时，则此属性可以支持该方案。</span><span class="sxs-lookup"><span data-stu-id="ff333-178">If probing at run time is needed, however, this property can enable that scenario.</span></span>
* <span data-ttu-id="ff333-179">`APP_NI_PATHS` 此列表与 APP_PATHS 相似，不同之处在于其中的路径用于探测本机映像。</span><span class="sxs-lookup"><span data-stu-id="ff333-179">`APP_NI_PATHS` This list is similar to APP_PATHS except that it's meant to be paths that will be probed for native images.</span></span>
* <span data-ttu-id="ff333-180">`NATIVE_DLL_SEARCH_DIRECTORIES` 此属性是一个路径列表，加载程序在查找通过 p/invoke 调用的本机库时应使用这些路径进行探测。</span><span class="sxs-lookup"><span data-stu-id="ff333-180">`NATIVE_DLL_SEARCH_DIRECTORIES` This property is a list of paths the loader should probe when looking for native libraries called via p/invoke.</span></span>
* <span data-ttu-id="ff333-181">`PLATFORM_RESOURCE_ROOTS` 此列表包含的路径用于探测资源附属程序集（在区域性特定的子目录中）。</span><span class="sxs-lookup"><span data-stu-id="ff333-181">`PLATFORM_RESOURCE_ROOTS` This list includes paths to probe in for resource satellite assemblies (in culture-specific subdirectories).</span></span>

<span data-ttu-id="ff333-182">在此示例主机中，TPA 列表是通过简单列出当前目录中的所有库来进行构造的：</span><span class="sxs-lookup"><span data-stu-id="ff333-182">In this sample host, the TPA list is constructed by simply listing all libraries in the current directory:</span></span>

[!code-cpp[CoreClrHost#7](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#7)]

<span data-ttu-id="ff333-183">因为该示例简单，所以只需要 `TRUSTED_PLATFORM_ASSEMBLIES` 属性：</span><span class="sxs-lookup"><span data-stu-id="ff333-183">Because the sample is simple, it only needs the `TRUSTED_PLATFORM_ASSEMBLIES` property:</span></span>

[!code-cpp[CoreClrHost#3](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a><span data-ttu-id="ff333-184">步骤 4 - 启动运行时</span><span class="sxs-lookup"><span data-stu-id="ff333-184">Step 4 - Start the runtime</span></span>

<span data-ttu-id="ff333-185">与 mscoree.h hosting API（上面所述）不同，CoreCLRHost.h API 使用一个调用启动运行时并创建默认的 AppDomain。</span><span class="sxs-lookup"><span data-stu-id="ff333-185">Unlike the mscoree.h hosting API (described below), CoreCLRHost.h APIs start the runtime and create the default AppDomain all with a single call.</span></span> <span data-ttu-id="ff333-186">`coreclr_initialize` 函数采用基本路径、名称和前面描述的属性，并通过 `hostHandle` 参数将图柄返回到主机。</span><span class="sxs-lookup"><span data-stu-id="ff333-186">The `coreclr_initialize` function takes a base path, name, and the properties described earlier and returns back a handle to the host via the `hostHandle` parameter.</span></span>

[!code-cpp[CoreClrHost#4](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a><span data-ttu-id="ff333-187">步骤 5 - 运行托管代码！</span><span class="sxs-lookup"><span data-stu-id="ff333-187">Step 5 - Run managed code!</span></span>

<span data-ttu-id="ff333-188">启动运行时之后，主机可以调用托管代码。</span><span class="sxs-lookup"><span data-stu-id="ff333-188">With the runtime started, the host can call managed code.</span></span> <span data-ttu-id="ff333-189">这可以通过两种不同的方法实现。</span><span class="sxs-lookup"><span data-stu-id="ff333-189">This can be done in a couple of different ways.</span></span> <span data-ttu-id="ff333-190">与本教程相关的示例代码使用 `coreclr_create_delegate` 函数创建静态托管方法的委托。</span><span class="sxs-lookup"><span data-stu-id="ff333-190">The sample code linked to this tutorial uses the `coreclr_create_delegate` function to create a delegate to a static managed method.</span></span> <span data-ttu-id="ff333-191">此 API 采用[程序集名称](../../standard/assembly/names.md)、符合命名空间条件的类型名称和方法名称作为输入，并返回可用于调用该方法的委托。</span><span class="sxs-lookup"><span data-stu-id="ff333-191">This API takes the [assembly name](../../standard/assembly/names.md), namespace-qualified type name, and method name as inputs and returns a delegate that can be used to invoke the method.</span></span>

[!code-cpp[CoreClrHost#5](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#5)]

<span data-ttu-id="ff333-192">在此示例中，主机现在可以调用 `managedDelegate` 来运行 `ManagedWorker.DoWork` 方法。</span><span class="sxs-lookup"><span data-stu-id="ff333-192">In this sample, the host can now call `managedDelegate` to run the `ManagedWorker.DoWork` method.</span></span>

<span data-ttu-id="ff333-193">或者，可以使用 `coreclr_execute_assembly` 函数启动托管可执行文件。</span><span class="sxs-lookup"><span data-stu-id="ff333-193">Alternatively, the `coreclr_execute_assembly` function can be used to launch a managed executable.</span></span> <span data-ttu-id="ff333-194">此 API 采用程序集路径和实参数组作为输入形参。</span><span class="sxs-lookup"><span data-stu-id="ff333-194">This API takes an assembly path and array of arguments as input parameters.</span></span> <span data-ttu-id="ff333-195">它在该路径加载程序集并调用其主方法。</span><span class="sxs-lookup"><span data-stu-id="ff333-195">It loads the assembly at that path and invokes its main method.</span></span>

```C++
int hr = executeAssembly(
        hostHandle,
        domainId,
        argumentCount,
        arguments,
        "HelloWorld.exe",
        (unsigned int*)&exitCode);
```

### <a name="step-6---shutdown-and-clean-up"></a><span data-ttu-id="ff333-196">步骤 6 - 关闭和清理</span><span class="sxs-lookup"><span data-stu-id="ff333-196">Step 6 - Shutdown and clean up</span></span>

<span data-ttu-id="ff333-197">最后，主机完成运行托管代码后，使用 `coreclr_shutdown` 或 `coreclr_shutdown_2` 关闭 .NET Core 运行时。</span><span class="sxs-lookup"><span data-stu-id="ff333-197">Finally, when the host is done running managed code, the .NET Core runtime is shut down with `coreclr_shutdown` or `coreclr_shutdown_2`.</span></span>

[!code-cpp[CoreClrHost#6](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#6)]

<span data-ttu-id="ff333-198">CoreCLR 不支持重新初始化或卸载。</span><span class="sxs-lookup"><span data-stu-id="ff333-198">CoreCLR does not support reinitialization or unloading.</span></span> <span data-ttu-id="ff333-199">请勿重新调用 `coreclr_initialize` 或卸载 CoreCLR 库。</span><span class="sxs-lookup"><span data-stu-id="ff333-199">Do not call `coreclr_initialize` again or unload the CoreCLR library.</span></span>

## <a name="create-a-host-using-mscoreeh"></a><span data-ttu-id="ff333-200">使用 Mscoree.h 创建主机</span><span class="sxs-lookup"><span data-stu-id="ff333-200">Create a host using Mscoree.h</span></span>

<span data-ttu-id="ff333-201">如前所述，CoreClrHost.h 现在是承载 .NET Core 运行时的首选方法。</span><span class="sxs-lookup"><span data-stu-id="ff333-201">As mentioned previously, CoreClrHost.h is now the preferred method of hosting the .NET Core runtime.</span></span> <span data-ttu-id="ff333-202">但是，如果 CoreClrHost.h 接口不够用（例如，需要非标准的启动标志，或者在默认域上需要 AppDomainManager），仍然可以使用 `ICLRRuntimeHost4` 接口。</span><span class="sxs-lookup"><span data-stu-id="ff333-202">The `ICLRRuntimeHost4` interface can still be used, though, if the CoreClrHost.h interfaces aren't sufficient (if non-standard startup flags are needed, for example, or if an AppDomainManager is needed on the default domain).</span></span> <span data-ttu-id="ff333-203">这些说明将指导你使用 mscoree.h 执行承载 .NET Core 的操作。</span><span class="sxs-lookup"><span data-stu-id="ff333-203">These instructions will guide you through hosting .NET Core using mscoree.h.</span></span>

<span data-ttu-id="ff333-204">[CoreRun 主机](https://github.com/dotnet/runtime/tree/master/src/coreclr/src/hosts/corerun)显示使用 mscoree.h 的更为复杂的真实托管示例。</span><span class="sxs-lookup"><span data-stu-id="ff333-204">The [CoreRun host](https://github.com/dotnet/runtime/tree/master/src/coreclr/src/hosts/corerun) shows a more complex, real-world example of hosting using mscoree.h.</span></span>

### <a name="a-note-about-mscoreeh"></a><span data-ttu-id="ff333-205">有关 mscoree.h 的说明</span><span class="sxs-lookup"><span data-stu-id="ff333-205">A note about mscoree.h</span></span>
<span data-ttu-id="ff333-206">`ICLRRuntimeHost4` .NET Core 承载接口在 [MSCOREE.IDL](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/inc/MSCOREE.IDL) 中定义。</span><span class="sxs-lookup"><span data-stu-id="ff333-206">The `ICLRRuntimeHost4` .NET Core hosting interface is defined in [MSCOREE.IDL](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/inc/MSCOREE.IDL).</span></span> <span data-ttu-id="ff333-207">主机需要引用的此文件 (mscoree.h) 的标头版本，该版本是在构建 [.NET Core 运行时](https://github.com/dotnet/runtime/)时通过 MIDL 生成。</span><span class="sxs-lookup"><span data-stu-id="ff333-207">A header version of this file (mscoree.h), which your host will need to reference, is produced via MIDL when the [.NET Core runtime](https://github.com/dotnet/runtime/) is built.</span></span> <span data-ttu-id="ff333-208">如果不想构建 .NET Core 运行时，还可在 dotnet/runtime 存储库中将 mscoree.h 获取为[预生成的标头](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/)。</span><span class="sxs-lookup"><span data-stu-id="ff333-208">If you do not want to build the .NET Core runtime, mscoree.h is also available as a [pre-built header](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/) in the dotnet/runtime repository.</span></span>

### <a name="step-1---identify-the-managed-entry-point"></a><span data-ttu-id="ff333-209">步骤 1 - 标识托管的入口点</span><span class="sxs-lookup"><span data-stu-id="ff333-209">Step 1 - Identify the managed entry point</span></span>
<span data-ttu-id="ff333-210">引用必要的标头后（例如，[mscoree.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/mscoree.h) 和 stdio.h），.NET Core 主机必须完成的首要任务之一就是找到要使用的托管入口点。</span><span class="sxs-lookup"><span data-stu-id="ff333-210">After referencing necessary headers ([mscoree.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/mscoree.h) and stdio.h, for example), one of the first things a .NET Core host must do is locate the managed entry point it will be using.</span></span> <span data-ttu-id="ff333-211">在示例主机中，通过将主机的第一个命令行参数作为托管的二进制文件（将执行该文件的 `main` 方法）的路径，即可完成此操作。</span><span class="sxs-lookup"><span data-stu-id="ff333-211">In our sample host, this is done by just taking the first command-line argument to our host as the path to a managed binary whose `main` method will be executed.</span></span>

[!code-cpp[NetCoreHost#1](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#1)]

### <a name="step-2---find-and-load-coreclr"></a><span data-ttu-id="ff333-212">步骤 2 - 查找和加载 CoreCLR</span><span class="sxs-lookup"><span data-stu-id="ff333-212">Step 2 - Find and load CoreCLR</span></span>
<span data-ttu-id="ff333-213">.NET Core 运行时 API 位于 *CoreCLR.dll*（在 Windows 上）中。</span><span class="sxs-lookup"><span data-stu-id="ff333-213">The .NET Core runtime APIs are in *CoreCLR.dll* (on Windows).</span></span> <span data-ttu-id="ff333-214">若要获取托管接口 (`ICLRRuntimeHost4`)，就必须查找并加载 *CoreCLR.dll*。</span><span class="sxs-lookup"><span data-stu-id="ff333-214">To get our hosting interface (`ICLRRuntimeHost4`), it's necessary to find and load *CoreCLR.dll*.</span></span> <span data-ttu-id="ff333-215">由主机定义用于规定 *CoreCLR.dll* 查找方式的约定。</span><span class="sxs-lookup"><span data-stu-id="ff333-215">It is up to the host to define a convention for how it will locate *CoreCLR.dll*.</span></span> <span data-ttu-id="ff333-216">一些主机会预期文件位于一个常用的计算机范围内的位置（如 %programfiles%\dotnet\shared\Microsoft.NETCore.App\2.1.6）。</span><span class="sxs-lookup"><span data-stu-id="ff333-216">Some hosts expect the file to be present in a well-known machine-wide location (such as *%programfiles%\dotnet\shared\Microsoft.NETCore.App\2.1.6*).</span></span> <span data-ttu-id="ff333-217">其他主机会预期 *CoreCLR.dll* 从主机本身或要托管的应用旁的某个位置进行加载。</span><span class="sxs-lookup"><span data-stu-id="ff333-217">Others expect that *CoreCLR.dll* will be loaded from a location next to either the host itself or the app to be hosted.</span></span> <span data-ttu-id="ff333-218">还有一些主机可能会参考环境变量来查找库。</span><span class="sxs-lookup"><span data-stu-id="ff333-218">Still others might consult an environment variable to find the library.</span></span>

<span data-ttu-id="ff333-219">在 Linux 或 macOS 上，核心运行时库分别是 libcoreclr.so 或者 libcoreclr.dylib。</span><span class="sxs-lookup"><span data-stu-id="ff333-219">On Linux or macOS, the core runtime library is *libcoreclr.so* or *libcoreclr.dylib*, respectively.</span></span>

<span data-ttu-id="ff333-220">示例主机会为 *CoreCLR.dll* 探测几个常用位置。</span><span class="sxs-lookup"><span data-stu-id="ff333-220">Our sample host probes a few common locations for *CoreCLR.dll*.</span></span> <span data-ttu-id="ff333-221">找到后，必须通过 `LoadLibrary`（在 Linux/macOS 上通过 `dlopen`）进行加载。</span><span class="sxs-lookup"><span data-stu-id="ff333-221">Once found, it must be loaded via `LoadLibrary` (or `dlopen` on Linux/macOS).</span></span>

[!code-cpp[NetCoreHost#2](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost4-instance"></a><span data-ttu-id="ff333-222">步骤 3 - 获取 ICLRRuntimeHost4 实例</span><span class="sxs-lookup"><span data-stu-id="ff333-222">Step 3 - Get an ICLRRuntimeHost4 Instance</span></span>
<span data-ttu-id="ff333-223">通过在 `GetCLRRuntimeHost` 上调用 `GetProcAddress`（或在 Linux/macOS 上调用 `dlsym`），然后再调用该函数来检索 `ICLRRuntimeHost4` 托管接口。</span><span class="sxs-lookup"><span data-stu-id="ff333-223">The `ICLRRuntimeHost4` hosting interface is retrieved by calling `GetProcAddress` (or `dlsym` on Linux/macOS) on `GetCLRRuntimeHost`, and then invoking that function.</span></span>

[!code-cpp[NetCoreHost#3](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#3)]

### <a name="step-4---set-startup-flags-and-start-the-runtime"></a><span data-ttu-id="ff333-224">步骤 4 - 设置启动标志并启动运行时</span><span class="sxs-lookup"><span data-stu-id="ff333-224">Step 4 - Set startup flags and start the runtime</span></span>
<span data-ttu-id="ff333-225">有了 `ICLRRuntimeHost4`，现在便可指定运行时范围内的启动标志并启动该运行时。</span><span class="sxs-lookup"><span data-stu-id="ff333-225">With an `ICLRRuntimeHost4` in-hand, we can now specify runtime-wide startup flags and start the runtime.</span></span> <span data-ttu-id="ff333-226">启动标志决定要使用的垃圾回收器 (GC)（并发垃圾回收器或服务器）、是使用单个 AppDomain 还是多个 Appdomain，以及要使用的加载程序优化策略（对于非特定于域的程序集加载）。</span><span class="sxs-lookup"><span data-stu-id="ff333-226">Startup flags determine which garbage collector (GC) to use (concurrent or server), whether we will use a single AppDomain or multiple AppDomains, and what loader optimization policy to use (for domain-neutral loading of assemblies).</span></span>

[!code-cpp[NetCoreHost#4](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#4)]

<span data-ttu-id="ff333-227">通过调用 `Start` 函数启动运行时。</span><span class="sxs-lookup"><span data-stu-id="ff333-227">The runtime is started with a call to the `Start` function.</span></span>

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a><span data-ttu-id="ff333-228">步骤 5 - 准备 AppDomain 设置</span><span class="sxs-lookup"><span data-stu-id="ff333-228">Step 5 - Preparing AppDomain settings</span></span>
<span data-ttu-id="ff333-229">启动运行时后，将需要设置 AppDomain。</span><span class="sxs-lookup"><span data-stu-id="ff333-229">Once the runtime is started, we will want to set up an AppDomain.</span></span> <span data-ttu-id="ff333-230">但创建 .NET AppDomain 时必须指定大量选项，因此必须先准备这些选项。</span><span class="sxs-lookup"><span data-stu-id="ff333-230">There are a number of options that must be specified when creating a .NET AppDomain, however, so it's necessary to prepare those first.</span></span>

<span data-ttu-id="ff333-231">AppDomain 标志指定与安全性和互操作性相关的 AppDomain 行为。</span><span class="sxs-lookup"><span data-stu-id="ff333-231">AppDomain flags specify AppDomain behaviors related to security and interop.</span></span> <span data-ttu-id="ff333-232">早期 Silverlight 主机对沙盒用户代码使用这些设置，但大多数现代 .NET Core 主机以完全信任的方式运行用户代码并启用互操作。</span><span class="sxs-lookup"><span data-stu-id="ff333-232">Older Silverlight hosts used these settings to sandbox user code, but most modern .NET Core hosts run user code as full trust and enable interop.</span></span>

[!code-cpp[NetCoreHost#5](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#5)]

<span data-ttu-id="ff333-233">确定要使用的 AppDomain 标志后，必须定义 AppDomain 属性。</span><span class="sxs-lookup"><span data-stu-id="ff333-233">After deciding which AppDomain flags to use, AppDomain properties must be defined.</span></span> <span data-ttu-id="ff333-234">该属性是字符串的键/值对。</span><span class="sxs-lookup"><span data-stu-id="ff333-234">The properties are key/value pairs of strings.</span></span> <span data-ttu-id="ff333-235">这些属性中的许多与 AppDomain 程序集的加载方式相关。</span><span class="sxs-lookup"><span data-stu-id="ff333-235">Many of the properties relate to how the AppDomain will load assemblies.</span></span>

<span data-ttu-id="ff333-236">常见 AppDomain 属性包括：</span><span class="sxs-lookup"><span data-stu-id="ff333-236">Common AppDomain properties include:</span></span>

* <span data-ttu-id="ff333-237">`TRUSTED_PLATFORM_ASSEMBLIES` 这是程序集路径列表（在 Windows 上，以 `;` 分隔；在 Linux/macOS 上，以 `:` 分隔），AppDomain 应优先加载它们，并完全信任它们（甚至是在部分信任的域中，也不例外）。</span><span class="sxs-lookup"><span data-stu-id="ff333-237">`TRUSTED_PLATFORM_ASSEMBLIES` This is a list of assembly paths (delimited by `;` on Windows and `:` on Linux/macOS) which the AppDomain should prioritize loading and give full trust to (even in partially trusted domains).</span></span> <span data-ttu-id="ff333-238">此列表应包含“框架”程序集和其他受信任的模块，与 .NET Framework 方案中的 GAC 类似。</span><span class="sxs-lookup"><span data-stu-id="ff333-238">This list is meant to contain 'Framework' assemblies and other trusted modules, similar to the GAC in .NET Framework scenarios.</span></span> <span data-ttu-id="ff333-239">一些主机会将任何库置于此列表上的 *coreclr.dll* 旁，其他主机具有硬编码的清单，其中列出了用于所需用途的受信任程序集。</span><span class="sxs-lookup"><span data-stu-id="ff333-239">Some hosts will put any library next to *coreclr.dll* on this list, others have hard-coded manifests listing trusted assemblies for their purposes.</span></span>
* <span data-ttu-id="ff333-240">`APP_PATHS` 这是一个用来探测程序集的路径的列表（如果在受信任的平台程序集 (TPA) 列表中找不到程序集）。</span><span class="sxs-lookup"><span data-stu-id="ff333-240">`APP_PATHS` This is a list of paths to probe in for an assembly if it can't be found in the trusted platform assemblies (TPA) list.</span></span> <span data-ttu-id="ff333-241">因为主机使用 TPA 列表可以更好地控制加载哪些程序集，所以对于主机来说，确定要加载的程序集并显式列出它们是最佳做法。</span><span class="sxs-lookup"><span data-stu-id="ff333-241">Because the host has more control over which assemblies are loaded using the TPA list, it is a best practice for hosts to determine which assemblies they expect to load and list them explicitly.</span></span> <span data-ttu-id="ff333-242">但是，如果需要探测运行时，则此属性可以支持该方案。</span><span class="sxs-lookup"><span data-stu-id="ff333-242">If probing at run time is needed, however, this property can enable that scenario.</span></span>
* <span data-ttu-id="ff333-243">`APP_NI_PATHS` 此列表与 APP_PATHS 非常相似，不同之处在于其中的路径用于探测本机映像。</span><span class="sxs-lookup"><span data-stu-id="ff333-243">`APP_NI_PATHS` This list is very similar to APP_PATHS except that it's meant to be paths that will be probed for native images.</span></span>
* <span data-ttu-id="ff333-244">`NATIVE_DLL_SEARCH_DIRECTORIES` 此属性是一个路径列表，加载程序在查找通过 p/invoke 调用的本机 DLL 时应使用这些路径进行探测。</span><span class="sxs-lookup"><span data-stu-id="ff333-244">`NATIVE_DLL_SEARCH_DIRECTORIES` This property is a list of paths the loader should probe when looking for native DLLs called via p/invoke.</span></span>
* <span data-ttu-id="ff333-245">`PLATFORM_RESOURCE_ROOTS` 此列表包含的路径用于探测资源附属程序集（在区域性特定的子目录中）。</span><span class="sxs-lookup"><span data-stu-id="ff333-245">`PLATFORM_RESOURCE_ROOTS` This list includes paths to probe in for resource satellite assemblies (in culture-specific subdirectories).</span></span>

<span data-ttu-id="ff333-246">在[简单示例主机](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithMscoree)中，这些属性将进行如下设置：</span><span class="sxs-lookup"><span data-stu-id="ff333-246">In our [simple sample host](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithMscoree), these properties are set up as follows:</span></span>

[!code-cpp[NetCoreHost#6](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a><span data-ttu-id="ff333-247">步骤 6 - 创建 AppDomain</span><span class="sxs-lookup"><span data-stu-id="ff333-247">Step 6 - Create the AppDomain</span></span>
<span data-ttu-id="ff333-248">所有 AppDomain 标志和属性都准备都就绪后，可使用 `ICLRRuntimeHost4::CreateAppDomainWithManager` 设置 AppDomain。</span><span class="sxs-lookup"><span data-stu-id="ff333-248">Once all AppDomain flags and properties are prepared, `ICLRRuntimeHost4::CreateAppDomainWithManager` can be used to set up the AppDomain.</span></span> <span data-ttu-id="ff333-249">此函数选择性地采用完全限定的程序集名称和类型名称作为域的 AppDomain 管理器。</span><span class="sxs-lookup"><span data-stu-id="ff333-249">This function optionally takes a fully qualified assembly name and type name to use as the domain's AppDomain manager.</span></span> <span data-ttu-id="ff333-250">AppDomain 管理器可允许主机控制 AppDomain 行为的某些方面，并且如果主机不打算直接调用用户代码，它可能会提供用于启动托管代码的入口点。</span><span class="sxs-lookup"><span data-stu-id="ff333-250">An AppDomain manager can allow a host to control some aspects of AppDomain behavior and may provide entry points for launching managed code if the host doesn't intend to invoke user code directly.</span></span>

[!code-cpp[NetCoreHost#7](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#7)]

### <a name="step-7---run-managed-code"></a><span data-ttu-id="ff333-251">步骤 7 - 运行托管代码！</span><span class="sxs-lookup"><span data-stu-id="ff333-251">Step 7 - Run managed code!</span></span>
<span data-ttu-id="ff333-252">现在 AppDomain 启动并运行后，主机可以开始执行托管的代码。</span><span class="sxs-lookup"><span data-stu-id="ff333-252">With an AppDomain up and running, the host can now start executing managed code.</span></span> <span data-ttu-id="ff333-253">执行此操作的最简单方法是使用 `ICLRRuntimeHost4::ExecuteAssembly` 调用托管程序集的入口点方法。</span><span class="sxs-lookup"><span data-stu-id="ff333-253">The easiest way to do this is to use `ICLRRuntimeHost4::ExecuteAssembly` to invoke a managed assembly's entry point method.</span></span> <span data-ttu-id="ff333-254">请注意，此函数仅适用于单一域方案。</span><span class="sxs-lookup"><span data-stu-id="ff333-254">Note that this function only works in single-domain scenarios.</span></span>

[!code-cpp[NetCoreHost#8](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#8)]

<span data-ttu-id="ff333-255">如果 `ExecuteAssembly` 不满足主机的需要，那么另一种方法是使用 `CreateDelegate` 创建指向静态托管方法的函数指针。</span><span class="sxs-lookup"><span data-stu-id="ff333-255">Another option, if `ExecuteAssembly` doesn't meet your host's needs, is to use `CreateDelegate` to create a function pointer to a static managed method.</span></span> <span data-ttu-id="ff333-256">这要求主机知道要调用的方法的签名（以创建函数指针类型），但允许主机调用代码而不是程序集的入口点。</span><span class="sxs-lookup"><span data-stu-id="ff333-256">This requires the host to know the signature of the method it is calling into (in order to create the function pointer type) but allows hosts the flexibility to invoke code other than an assembly's entry point.</span></span> <span data-ttu-id="ff333-257">第二个参数中提供的程序集名称是要加载的库的[完全托管程序集名称](../../standard/assembly/names.md)。</span><span class="sxs-lookup"><span data-stu-id="ff333-257">The assembly name provided in the second parameter is the [full managed assembly name](../../standard/assembly/names.md) of the library to load.</span></span>

```C++
void *pfnDelegate = NULL;
hr = runtimeHost->CreateDelegate(
    domainId,
    L"HW, Version=1.0.0.0, Culture=neutral", // Target managed assembly
    L"ConsoleApplication.Program",           // Target managed type
    L"Main",                                 // Target entry point (static method)
    (INT_PTR*)&pfnDelegate);

((MainMethodFp*)pfnDelegate)(NULL);
```

### <a name="step-8---clean-up"></a><span data-ttu-id="ff333-258">步骤 8 - 清理</span><span class="sxs-lookup"><span data-stu-id="ff333-258">Step 8 - Clean up</span></span>
<span data-ttu-id="ff333-259">最后，主机应随后通过卸载 Appdomain、停止运行时并释放 `ICLRRuntimeHost4` 引用来进行清理。</span><span class="sxs-lookup"><span data-stu-id="ff333-259">Finally, the host should clean up after itself by unloading AppDomains, stopping the runtime, and releasing the `ICLRRuntimeHost4` reference.</span></span>

[!code-cpp[NetCoreHost#9](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#9)]

<span data-ttu-id="ff333-260">CoreCLR 不支持卸载。</span><span class="sxs-lookup"><span data-stu-id="ff333-260">CoreCLR does not support unloading.</span></span> <span data-ttu-id="ff333-261">请勿卸载 CoreCLR 库。</span><span class="sxs-lookup"><span data-stu-id="ff333-261">Do not unload the CoreCLR library.</span></span>

## <a name="conclusion"></a><span data-ttu-id="ff333-262">结束语</span><span class="sxs-lookup"><span data-stu-id="ff333-262">Conclusion</span></span>
<span data-ttu-id="ff333-263">构建主机后，可以通过从命令行运行主机并传递其所需的任何参数（例如，要运行用于 mscoree 示例主机的托管应用）来对主机进行测试。</span><span class="sxs-lookup"><span data-stu-id="ff333-263">Once your host is built, it can be tested by running it from the command line and passing any arguments the host expects (like the managed app to run for the mscoree example host).</span></span> <span data-ttu-id="ff333-264">指定主机要运行的 .NET Core 应用时，请务必使用 `dotnet build` 生成的 .dll。</span><span class="sxs-lookup"><span data-stu-id="ff333-264">When specifying the .NET Core app for the host to run, be sure to use the .dll that is produced by `dotnet build`.</span></span> <span data-ttu-id="ff333-265">`dotnet publish` 为独立应用程序生成的可执行文件（.exe 文件）实际上是默认的 .NET Core 主机（以便可直接从主流方案中的命令行启动应用）；用户代码被编译为具有相同名称的 dll。</span><span class="sxs-lookup"><span data-stu-id="ff333-265">Executables (.exe files) produced by `dotnet publish` for self-contained applications are actually the default .NET Core host (so that the app can be launched directly from the command line in mainline scenarios); user code is compiled into a dll of the same name.</span></span>

<span data-ttu-id="ff333-266">如果开始时操作不起作用，请再次检查 coreclr.dll 是否在主机预期的位置可用、TPA 列表中是否包含了所有必需的框架库以及 CoreCLR 的位数（32 位或 64 位）是否匹配主机的构建方式。</span><span class="sxs-lookup"><span data-stu-id="ff333-266">If things don't work initially, double-check that *coreclr.dll* is available in the location expected by the host, that all necessary Framework libraries are in the TPA list, and that CoreCLR's bitness (32-bit or 64-bit) matches how the host was built.</span></span>

<span data-ttu-id="ff333-267">托管 .NET Core 运行时是高级方案，许多开发人员并不需要实施这一方案，但对于那些需要从本机进程启动托管代码的人员，或需要更好地控制 .NET Core 运行时的行为的人员而言，它会非常有用。</span><span class="sxs-lookup"><span data-stu-id="ff333-267">Hosting the .NET Core runtime is an advanced scenario that many developers won't require, but for those who need to launch managed code from a native process, or who need more control over the .NET Core runtime's behavior, it can be very useful.</span></span>
