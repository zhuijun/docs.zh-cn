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
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>编写自定义 .NET Core 主机以从本机代码控制 .NET 运行时

像所有的托管代码一样，.NET Core 应用程序也由主机执行。 主机负责启动运行时（包括 JIT 和垃圾回收器等组件）和调用托管的入口点。

托管 .NET Core 运行时是高级方案，在大多数情况下，.NET Core 开发人员无需担心托管问题，因为 .NET Core 生成过程会提供默认主机来运行 .NET Core 应用程序。 虽然在某些特殊情况下，它对显式托管 .NET Core 运行时非常有用 - 无论是作为一种在本机进程中调用托管代码的方式还是为了获得对运行时工作原理更好的控制。

本文概述了从本机代码启动 .NET Core 运行时和在其中执行托管代码的必要步骤。

## <a name="prerequisites"></a>先决条件

由于主机是本机应用程序，所以本教程将介绍如何构造 C++ 应用程序以托管 .NET Core。 将需要一个 C++ 开发环境（例如，[Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) 提供的环境）。

还将需要一个简单的 .NET Core 应用程序来测试主机，因此应安装 [.NET Core SDK](https://dotnet.microsoft.com/download) 并[构建一个小型的 .NET Core 测试应用](with-visual-studio.md)（例如，“Hello World”应用）。 使用通过新 .NET Core 控制台项目模板创建的“Hello World”应用就足够了。

## <a name="hosting-apis"></a>承载 API
可以使用三种不同的 API 来托管 .NET Core。 本文（及其相关的[示例](https://github.com/dotnet/samples/tree/master/core/hosting)）涵盖所有选项。

* 在 .NET Core 3.0 及更高版本中托管 .NET Core 运行时的首选方法是借助 `nethost` 和 `hostfxr` 库的 API。 由这些入口点来处理查找和设置运行时进行初始化所遇到的复杂性；通过它们，还可启动托管应用程序和调用静态托管方法。
* 托管低于 .NET Core 3.0 的 .NET Core 运行时的首选方法是使用 [CoreClrHost.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/hosts/inc/coreclrhost.h) API。 此 API 公开一些函数，用于轻松地启动和停止运行时并调用托管代码（通过启动托管 exe 或通过调用静态托管方法）。
* 也可以使用 [mscoree.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/mscoree.h) 中的 `ICLRRuntimeHost4` 接口承载 .NET Core。 此 API 比 CoreClrHost.h 出现的时间更早，因此你可能看到过使用此 API 的较旧版本的主机。 它仍然可用，并且比起 CoreClrHost，它可以对主机进程进行更多控制。 但是对于大多数方案，CoreClrHost.h 现在是首选，因为它的 API 更简单。

## <a name="sample-hosts"></a>示例主机

有关展示在下面的教程中所述步骤的[示例主机](https://github.com/dotnet/samples/tree/master/core/hosting)，请访问 dotnet/samples GitHub 存储库。 该示例中的注释清楚地将这些教程中已编号的步骤与它们在示例中的执行位置关联。 有关下载说明，请参阅[示例和教程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

请记住，示例主机的用途在于提供学习指导，在纠错方面不甚严谨，其重在可读性而非效率。

## <a name="create-a-host-using-nethosth-and-hostfxrh"></a>使用 NetHost.h 和 HostFxr.h 创建主机

以下步骤详细说明如何使用 `nethost` 和 `hostfxr` 库在本机应用程序中启动 .NET Core 运行时并调用托管静态方法。 [示例](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr)使用安装了 .NET SDK 的 `nethost` 标头和库，并从 [dotnet/core-setup](https://github.com/dotnet/core-setup) 复制 [`coreclr_delegates.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/coreclr_delegates.h) 和 [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) 文件。

### <a name="step-1---load-hostfxr-and-get-exported-hosting-functions"></a>步骤 1 - 加载 HostFxr 并获取导出的托管函数

`nethost` 库提供用于查找 `hostfxr` 库的 `get_hostfxr_path` 函数。 `hostfxr` 库公开用于托管 .NET Core 运行时的函数。 函数的完整列表可在 [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) 和[本机托管设计文档](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/native-hosting.md)中找到。 示例和本教程使用以下函数：

* `hostfxr_initialize_for_runtime_config`：初始化主机上下文，并使用指定的运行时配置准备初始化 .NET Core 运行时。
* `hostfxr_get_runtime_delegate`：获取对运行时功能的委托。
* `hostfxr_close`：关闭主机上下文。

使用 `get_hostfxr_path` 找到了 `hostfxr` 库。 随后加载此库并检索其导出。

[!code-cpp[HostFxrHost#LoadHostFxr](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadHostFxr)]

### <a name="step-2---initialize-and-start-the-net-core-runtime"></a>步骤 2 - 初始化和启动 .NET Core 运行时

`hostfxr_initialize_for_runtime_config` 和 `hostfxr_get_runtime_delegate` 函数使用将加载的托管组件的运行时配置初始化并启动 .NET Core 运行时。 `hostfxr_get_runtime_delegate` 函数用于获取运行时委托，允许加载托管程序集并获取指向该程序集中的静态方法的函数指针。

[!code-cpp[HostFxrHost#Initialize](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#Initialize)]

### <a name="step-3---load-managed-assembly-and-get-function-pointer-to-a-managed-method"></a>步骤 3 - 加载托管程序集并获取指向托管方法的函数指针

将调用运行时委托以加载托管程序集并获取指向托管方法的函数指针。 委托需要程序集路径、类型名称和方法名称作为输入，并返回可用于调用托管方法的函数指针。

[!code-cpp[HostFxrHost#LoadAndGet](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadAndGet)]

该示例通过在调用运行时委托时将 `nullptr` 作为委托类型名称传递，对托管方法使用默认签名：

```csharp
public delegate int ComponentEntryPoint(IntPtr args, int sizeBytes);
```

可以通过在调用运行时委托时指定委托类型名称来使用其他签名。

### <a name="step-4---run-managed-code"></a>步骤 4 - 运行托管代码！

本机主机现在可以调用托管方法，并向其传递所需的参数。

[!code-cpp[HostFxrHost#CallManaged](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#CallManaged)]

## <a name="create-a-host-using-coreclrhosth"></a>使用 CoreClrHost.h 创建主机

以下步骤详细说明如何使用 CoreClrHost.h API 在本机应用程序中启动 .NET Core 运行时并调用托管静态方法。 本文档中的代码片段使用一些特定于 Windows 的 API，但是[完整示例主机](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost)同时显示 Windows 和 Linux 的代码路径。

[Unix CoreRun 主机](https://github.com/dotnet/runtime/tree/master/src/coreclr/src/hosts/unixcorerun)显示使用 coreclrhost.h 的更为复杂的真实托管示例。

### <a name="step-1---find-and-load-coreclr"></a>步骤 1 - 查找和加载 CoreCLR

.NET Core 运行时 API 位于 coreclr.dll（对于 Windows）、libcoreclr.so（对于 Linux）或 libcoreclr.dylib（对于 macOS）  。 承载 .NET Core 的第一步是加载 CoreCLR 库。 一些主机探测不同的路径或使用输入参数来查找库，而另一些主机能够从某个路径（例如，紧邻主机的路径，或从计算机范围内的位置）加载库。

找到库之后，系统会使用 `LoadLibraryEx`（对于 Windows）或 `dlopen`（对于 Linux/macOS）加载库。

[!code-cpp[CoreClrHost#1](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a>步骤 2 - 获取 .NET Core 承载函数

CoreClrHost 有几个可用于承载 .NET Core 的重要方法：

* `coreclr_initialize`：启动 .NET Core 运行时并设置默认（且仅设置）AppDomain。
* `coreclr_execute_assembly`：执行托管程序集。
* `coreclr_create_delegate`：创建指向托管方法的函数指针。
* `coreclr_shutdown`：关闭 .NET Core 运行时。
* `coreclr_shutdown_2`：如 `coreclr_shutdown`，但还会检索托管代码的退出代码。

加载 CoreCLR 库之后，下一步是使用 `GetProcAddress`（对于 Windows）或 `dlsym`（对于 Linux/macOS）引用这些函数。

[!code-cpp[CoreClrHost#2](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a>步骤 3 - 准备运行时属性

在启动运行时之前，有必要准备一些属性来指定行为（特别是关于程序集加载器的行为）。

常用属性包括：

* `TRUSTED_PLATFORM_ASSEMBLIES` 这是程序集路径列表（对于 Windows，使用“;”分隔，对于 Linux，使用“:”分隔），运行时在默认情况下能够解析这些路径。 一些主机有硬编码清单，其中列出了它们可以加载的程序集。 其他主机将把任何库放在这个列表上的特定位置（例如 coreclr.dll 旁边）。
* `APP_PATHS` 这是一个用来探测程序集的路径的列表（如果在受信任的平台程序集 (TPA) 列表中找不到程序集）。 因为主机使用 TPA 列表可以更好地控制加载哪些程序集，所以对于主机来说，确定要加载的程序集并显式列出它们是最佳做法。 但是，如果需要探测运行时，则此属性可以支持该方案。
* `APP_NI_PATHS` 此列表与 APP_PATHS 相似，不同之处在于其中的路径用于探测本机映像。
* `NATIVE_DLL_SEARCH_DIRECTORIES` 此属性是一个路径列表，加载程序在查找通过 p/invoke 调用的本机库时应使用这些路径进行探测。
* `PLATFORM_RESOURCE_ROOTS` 此列表包含的路径用于探测资源附属程序集（在区域性特定的子目录中）。

在此示例主机中，TPA 列表是通过简单列出当前目录中的所有库来进行构造的：

[!code-cpp[CoreClrHost#7](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#7)]

因为该示例简单，所以只需要 `TRUSTED_PLATFORM_ASSEMBLIES` 属性：

[!code-cpp[CoreClrHost#3](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a>步骤 4 - 启动运行时

与 mscoree.h hosting API（上面所述）不同，CoreCLRHost.h API 使用一个调用启动运行时并创建默认的 AppDomain。 `coreclr_initialize` 函数采用基本路径、名称和前面描述的属性，并通过 `hostHandle` 参数将图柄返回到主机。

[!code-cpp[CoreClrHost#4](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a>步骤 5 - 运行托管代码！

启动运行时之后，主机可以调用托管代码。 这可以通过两种不同的方法实现。 与本教程相关的示例代码使用 `coreclr_create_delegate` 函数创建静态托管方法的委托。 此 API 采用[程序集名称](../../standard/assembly/names.md)、符合命名空间条件的类型名称和方法名称作为输入，并返回可用于调用该方法的委托。

[!code-cpp[CoreClrHost#5](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#5)]

在此示例中，主机现在可以调用 `managedDelegate` 来运行 `ManagedWorker.DoWork` 方法。

或者，可以使用 `coreclr_execute_assembly` 函数启动托管可执行文件。 此 API 采用程序集路径和实参数组作为输入形参。 它在该路径加载程序集并调用其主方法。

```C++
int hr = executeAssembly(
        hostHandle,
        domainId,
        argumentCount,
        arguments,
        "HelloWorld.exe",
        (unsigned int*)&exitCode);
```

### <a name="step-6---shutdown-and-clean-up"></a>步骤 6 - 关闭和清理

最后，主机完成运行托管代码后，使用 `coreclr_shutdown` 或 `coreclr_shutdown_2` 关闭 .NET Core 运行时。

[!code-cpp[CoreClrHost#6](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#6)]

CoreCLR 不支持重新初始化或卸载。 请勿重新调用 `coreclr_initialize` 或卸载 CoreCLR 库。

## <a name="create-a-host-using-mscoreeh"></a>使用 Mscoree.h 创建主机

如前所述，CoreClrHost.h 现在是承载 .NET Core 运行时的首选方法。 但是，如果 CoreClrHost.h 接口不够用（例如，需要非标准的启动标志，或者在默认域上需要 AppDomainManager），仍然可以使用 `ICLRRuntimeHost4` 接口。 这些说明将指导你使用 mscoree.h 执行承载 .NET Core 的操作。

[CoreRun 主机](https://github.com/dotnet/runtime/tree/master/src/coreclr/src/hosts/corerun)显示使用 mscoree.h 的更为复杂的真实托管示例。

### <a name="a-note-about-mscoreeh"></a>有关 mscoree.h 的说明
`ICLRRuntimeHost4` .NET Core 承载接口在 [MSCOREE.IDL](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/inc/MSCOREE.IDL) 中定义。 主机需要引用的此文件 (mscoree.h) 的标头版本，该版本是在构建 [.NET Core 运行时](https://github.com/dotnet/runtime/)时通过 MIDL 生成。 如果不想构建 .NET Core 运行时，还可在 dotnet/runtime 存储库中将 mscoree.h 获取为[预生成的标头](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/)。

### <a name="step-1---identify-the-managed-entry-point"></a>步骤 1 - 标识托管的入口点
引用必要的标头后（例如，[mscoree.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/mscoree.h) 和 stdio.h），.NET Core 主机必须完成的首要任务之一就是找到要使用的托管入口点。 在示例主机中，通过将主机的第一个命令行参数作为托管的二进制文件（将执行该文件的 `main` 方法）的路径，即可完成此操作。

[!code-cpp[NetCoreHost#1](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#1)]

### <a name="step-2---find-and-load-coreclr"></a>步骤 2 - 查找和加载 CoreCLR
.NET Core 运行时 API 位于 *CoreCLR.dll*（在 Windows 上）中。 若要获取托管接口 (`ICLRRuntimeHost4`)，就必须查找并加载 *CoreCLR.dll*。 由主机定义用于规定 *CoreCLR.dll* 查找方式的约定。 一些主机会预期文件位于一个常用的计算机范围内的位置（如 %programfiles%\dotnet\shared\Microsoft.NETCore.App\2.1.6）。 其他主机会预期 *CoreCLR.dll* 从主机本身或要托管的应用旁的某个位置进行加载。 还有一些主机可能会参考环境变量来查找库。

在 Linux 或 macOS 上，核心运行时库分别是 libcoreclr.so 或者 libcoreclr.dylib。

示例主机会为 *CoreCLR.dll* 探测几个常用位置。 找到后，必须通过 `LoadLibrary`（在 Linux/macOS 上通过 `dlopen`）进行加载。

[!code-cpp[NetCoreHost#2](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost4-instance"></a>步骤 3 - 获取 ICLRRuntimeHost4 实例
通过在 `GetCLRRuntimeHost` 上调用 `GetProcAddress`（或在 Linux/macOS 上调用 `dlsym`），然后再调用该函数来检索 `ICLRRuntimeHost4` 托管接口。

[!code-cpp[NetCoreHost#3](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#3)]

### <a name="step-4---set-startup-flags-and-start-the-runtime"></a>步骤 4 - 设置启动标志并启动运行时
有了 `ICLRRuntimeHost4`，现在便可指定运行时范围内的启动标志并启动该运行时。 启动标志决定要使用的垃圾回收器 (GC)（并发垃圾回收器或服务器）、是使用单个 AppDomain 还是多个 Appdomain，以及要使用的加载程序优化策略（对于非特定于域的程序集加载）。

[!code-cpp[NetCoreHost#4](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#4)]

通过调用 `Start` 函数启动运行时。

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>步骤 5 - 准备 AppDomain 设置
启动运行时后，将需要设置 AppDomain。 但创建 .NET AppDomain 时必须指定大量选项，因此必须先准备这些选项。

AppDomain 标志指定与安全性和互操作性相关的 AppDomain 行为。 早期 Silverlight 主机对沙盒用户代码使用这些设置，但大多数现代 .NET Core 主机以完全信任的方式运行用户代码并启用互操作。

[!code-cpp[NetCoreHost#5](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#5)]

确定要使用的 AppDomain 标志后，必须定义 AppDomain 属性。 该属性是字符串的键/值对。 这些属性中的许多与 AppDomain 程序集的加载方式相关。

常见 AppDomain 属性包括：

* `TRUSTED_PLATFORM_ASSEMBLIES` 这是程序集路径列表（在 Windows 上，以 `;` 分隔；在 Linux/macOS 上，以 `:` 分隔），AppDomain 应优先加载它们，并完全信任它们（甚至是在部分信任的域中，也不例外）。 此列表应包含“框架”程序集和其他受信任的模块，与 .NET Framework 方案中的 GAC 类似。 一些主机会将任何库置于此列表上的 *coreclr.dll* 旁，其他主机具有硬编码的清单，其中列出了用于所需用途的受信任程序集。
* `APP_PATHS` 这是一个用来探测程序集的路径的列表（如果在受信任的平台程序集 (TPA) 列表中找不到程序集）。 因为主机使用 TPA 列表可以更好地控制加载哪些程序集，所以对于主机来说，确定要加载的程序集并显式列出它们是最佳做法。 但是，如果需要探测运行时，则此属性可以支持该方案。
* `APP_NI_PATHS` 此列表与 APP_PATHS 非常相似，不同之处在于其中的路径用于探测本机映像。
* `NATIVE_DLL_SEARCH_DIRECTORIES` 此属性是一个路径列表，加载程序在查找通过 p/invoke 调用的本机 DLL 时应使用这些路径进行探测。
* `PLATFORM_RESOURCE_ROOTS` 此列表包含的路径用于探测资源附属程序集（在区域性特定的子目录中）。

在[简单示例主机](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithMscoree)中，这些属性将进行如下设置：

[!code-cpp[NetCoreHost#6](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>步骤 6 - 创建 AppDomain
所有 AppDomain 标志和属性都准备都就绪后，可使用 `ICLRRuntimeHost4::CreateAppDomainWithManager` 设置 AppDomain。 此函数选择性地采用完全限定的程序集名称和类型名称作为域的 AppDomain 管理器。 AppDomain 管理器可允许主机控制 AppDomain 行为的某些方面，并且如果主机不打算直接调用用户代码，它可能会提供用于启动托管代码的入口点。

[!code-cpp[NetCoreHost#7](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>步骤 7 - 运行托管代码！
现在 AppDomain 启动并运行后，主机可以开始执行托管的代码。 执行此操作的最简单方法是使用 `ICLRRuntimeHost4::ExecuteAssembly` 调用托管程序集的入口点方法。 请注意，此函数仅适用于单一域方案。

[!code-cpp[NetCoreHost#8](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#8)]

如果 `ExecuteAssembly` 不满足主机的需要，那么另一种方法是使用 `CreateDelegate` 创建指向静态托管方法的函数指针。 这要求主机知道要调用的方法的签名（以创建函数指针类型），但允许主机调用代码而不是程序集的入口点。 第二个参数中提供的程序集名称是要加载的库的[完全托管程序集名称](../../standard/assembly/names.md)。

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

### <a name="step-8---clean-up"></a>步骤 8 - 清理
最后，主机应随后通过卸载 Appdomain、停止运行时并释放 `ICLRRuntimeHost4` 引用来进行清理。

[!code-cpp[NetCoreHost#9](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#9)]

CoreCLR 不支持卸载。 请勿卸载 CoreCLR 库。

## <a name="conclusion"></a>结束语
构建主机后，可以通过从命令行运行主机并传递其所需的任何参数（例如，要运行用于 mscoree 示例主机的托管应用）来对主机进行测试。 指定主机要运行的 .NET Core 应用时，请务必使用 `dotnet build` 生成的 .dll。 `dotnet publish` 为独立应用程序生成的可执行文件（.exe 文件）实际上是默认的 .NET Core 主机（以便可直接从主流方案中的命令行启动应用）；用户代码被编译为具有相同名称的 dll。

如果开始时操作不起作用，请再次检查 coreclr.dll 是否在主机预期的位置可用、TPA 列表中是否包含了所有必需的框架库以及 CoreCLR 的位数（32 位或 64 位）是否匹配主机的构建方式。

托管 .NET Core 运行时是高级方案，许多开发人员并不需要实施这一方案，但对于那些需要从本机进程启动托管代码的人员，或需要更好地控制 .NET Core 运行时的行为的人员而言，它会非常有用。
