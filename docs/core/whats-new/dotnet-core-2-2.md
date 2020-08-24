---
title: .NET Core 2.2 的新增功能
description: 了解 .NET Core 2.2 的新增功能。
dev_langs:
- csharp
- vb
ms.date: 12/04/2018
ms.openlocfilehash: 656ef9aa2745c935c37b69ae5a54b8d126700e55
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608298"
---
# <a name="whats-new-in-net-core-22"></a><span data-ttu-id="0d49f-103">.NET Core 2.2 的新增功能</span><span class="sxs-lookup"><span data-stu-id="0d49f-103">What's new in .NET Core 2.2</span></span>

<span data-ttu-id="0d49f-104">.NET Core 2.2 包括在应用程序部署、运行时服务的事件处理、Azure SQL 数据库的身份验证、JIT 编译器性能，以及执行 `Main` 方法之前的代码注入方面的增强功能。</span><span class="sxs-lookup"><span data-stu-id="0d49f-104">.NET Core 2.2 includes enhancements in application deployment, event handling for runtime services, authentication to Azure SQL databases, JIT compiler performance, and code injection prior to the execution of the `Main` method.</span></span>

## <a name="new-deployment-mode"></a><span data-ttu-id="0d49f-105">新部署模式</span><span class="sxs-lookup"><span data-stu-id="0d49f-105">New deployment mode</span></span>

<span data-ttu-id="0d49f-106">从 .NET Core 2.2 开始，可以部署[依赖于框架的可执行文件](../deploying/index.md#publish-framework-dependent)，这是“.exe”  文件而不是“.dll”  文件。</span><span class="sxs-lookup"><span data-stu-id="0d49f-106">Starting with .NET Core 2.2, you can deploy [framework-dependent executables](../deploying/index.md#publish-framework-dependent), which are **.exe** files instead of **.dll** files.</span></span> <span data-ttu-id="0d49f-107">与依赖框架的部署在功能上类似，依赖框架的可执行文件 (FDE) 仍然依赖于存在的 .NET Core 的共享系统级版本来运行。</span><span class="sxs-lookup"><span data-stu-id="0d49f-107">Functionally similar to framework-dependent deployments, framework-dependent executables (FDE) still rely on the presence of a shared system-wide version of .NET Core to run.</span></span> <span data-ttu-id="0d49f-108">应用程序只包含代码和任何第三方依赖项。</span><span class="sxs-lookup"><span data-stu-id="0d49f-108">Your app contains only your code and any third-party dependencies.</span></span> <span data-ttu-id="0d49f-109">与依赖框架的部署不同，FDE 特定于平台。</span><span class="sxs-lookup"><span data-stu-id="0d49f-109">Unlike framework-dependent deployments, FDEs are platform-specific.</span></span>

<span data-ttu-id="0d49f-110">这种新的部署模式在构建可执行文件（而不是库）方面具有独特优势，这意味着你可以直接运行应用程序，而无需首先调用 `dotnet`。</span><span class="sxs-lookup"><span data-stu-id="0d49f-110">This new deployment mode has the distinct advantage of building an executable instead of a library, which means you can run your app directly without invoking `dotnet` first.</span></span>

## <a name="core"></a><span data-ttu-id="0d49f-111">核心</span><span class="sxs-lookup"><span data-stu-id="0d49f-111">Core</span></span>

<span data-ttu-id="0d49f-112">**在运行时服务中处理事件**</span><span class="sxs-lookup"><span data-stu-id="0d49f-112">**Handling events in runtime services**</span></span>

<span data-ttu-id="0d49f-113">你可能经常希望监视应用程序的运行时服务（如 GC、JIT 和 ThreadPool）的使用情况，以了解它们如何影响应用程序。</span><span class="sxs-lookup"><span data-stu-id="0d49f-113">You may often want to monitor your application's use of runtime services, such as the GC, JIT, and ThreadPool, to understand how they impact your application.</span></span><span data-ttu-id="0d49f-114"> 在 Windows 系统上，这通常通过监视当前进程的 ETW 事件来完成。</span><span class="sxs-lookup"><span data-stu-id="0d49f-114"> On Windows systems, this is commonly done by monitoring the ETW events of the current process.</span></span><span data-ttu-id="0d49f-115"> 虽然这仍然可以很好地工作，但是如果你在低特权环境中或者在 Linux 或 macOS 上运行，那么并不总是能够使用 ETW。</span><span class="sxs-lookup"><span data-stu-id="0d49f-115"> While this continues to work well, it's not always possible to use ETW if you're running in a low-privilege environment or on Linux or macOS.</span></span>

<span data-ttu-id="0d49f-116">从 .NET Core 2.2 开始，现在可以使用 <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> 类来使用 CoreCLR 事件。</span><span class="sxs-lookup"><span data-stu-id="0d49f-116">Starting with .NET Core 2.2, CoreCLR events can now be consumed using the <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="0d49f-117">这些事件描述了诸如 GC、JIT、ThreadPool 和 interop 等运行时服务的行为。</span><span class="sxs-lookup"><span data-stu-id="0d49f-117">These events describe the behavior of such runtime services as GC, JIT, ThreadPool, and interop.</span></span> <span data-ttu-id="0d49f-118">这些事件与作为 CoreCLR ETW 提供程序的一部分公开的事件相同。</span><span class="sxs-lookup"><span data-stu-id="0d49f-118">These are the same events that are exposed as part of the CoreCLR ETW provider.</span></span><span data-ttu-id="0d49f-119">  这允许应用程序使用这些事件或使用传输机制将它们发送到遥测聚合服务。</span><span class="sxs-lookup"><span data-stu-id="0d49f-119">  This allows for applications to consume these events or use a transport mechanism to send them to a telemetry aggregation service.</span></span> <span data-ttu-id="0d49f-120">可以在以下代码示例中看到如何订阅事件：</span><span class="sxs-lookup"><span data-stu-id="0d49f-120">You can see how to subscribe to events in the following code sample:</span></span>

```csharp
internal sealed class SimpleEventListener : EventListener
{
    // Called whenever an EventSource is created.
    protected override void OnEventSourceCreated(EventSource eventSource)
    {
        // Watch for the .NET runtime EventSource and enable all of its events.
        if (eventSource.Name.Equals("Microsoft-Windows-DotNETRuntime"))
        {
            EnableEvents(eventSource, EventLevel.Verbose, (EventKeywords)(-1));
        }
    }

    // Called whenever an event is written.
    protected override void OnEventWritten(EventWrittenEventArgs eventData)
    {
        // Write the contents of the event to the console.
        Console.WriteLine($"ThreadID = {eventData.OSThreadId} ID = {eventData.EventId} Name = {eventData.EventName}");
        for (int i = 0; i < eventData.Payload.Count; i++)
        {
            string payloadString = eventData.Payload[i]?.ToString() ?? string.Empty;
            Console.WriteLine($"\tName = \"{eventData.PayloadNames[i]}\" Value = \"{payloadString}\"");
        }
        Console.WriteLine("\n");
    }
}
```

<span data-ttu-id="0d49f-121">此外，.NET Core 2.2 向 <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> 类添加了以下两个属性来提供有关 ETW 事件的其他信息：</span><span class="sxs-lookup"><span data-stu-id="0d49f-121">In addition, .NET Core 2.2 adds the following two properties to the <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> class to provide additional information about ETW events:</span></span>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a><span data-ttu-id="0d49f-122">数据</span><span class="sxs-lookup"><span data-stu-id="0d49f-122">Data</span></span>

<span data-ttu-id="0d49f-123">**使用 SqlConnection.AccessToken 属性对 Azure SQL 数据库进行 AAD 身份验证**</span><span class="sxs-lookup"><span data-stu-id="0d49f-123">**AAD authentication to Azure SQL databases with the SqlConnection.AccessToken property**</span></span>

<span data-ttu-id="0d49f-124">从 .NET Core 2.2 开始，由 Azure Active Directory 颁发的访问令牌可用于对 Azure SQL 数据库进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="0d49f-124">Starting with .NET Core 2.2, an access token issued by Azure Active Directory can be used to authenticate to an Azure SQL database.</span></span> <span data-ttu-id="0d49f-125">若要支持访问令牌，必须将 <xref:System.Data.SqlClient.SqlConnection.AccessToken> 属性添加到 <xref:System.Data.SqlClient.SqlConnection> 类。</span><span class="sxs-lookup"><span data-stu-id="0d49f-125">To support access tokens, the <xref:System.Data.SqlClient.SqlConnection.AccessToken> property has been added to the <xref:System.Data.SqlClient.SqlConnection> class.</span></span> <span data-ttu-id="0d49f-126">若要利用 AAD 身份验证，请下载 System.Data.SqlClient NuGet 包的版本 4.6。</span><span class="sxs-lookup"><span data-stu-id="0d49f-126">To take advantage of AAD authentication, download version 4.6 of the System.Data.SqlClient NuGet package.</span></span> <span data-ttu-id="0d49f-127">若要使用功能，可以使用包含在 [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet 包中的[适用于 .NET 的 Active Directory 身份验证库](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet)获取访问令牌值。</span><span class="sxs-lookup"><span data-stu-id="0d49f-127">In order to use the feature, you can obtain the access token value using the [Active Directory Authentication Library for .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) contained in the [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet package.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="0d49f-128">JIT 编译器改进</span><span class="sxs-lookup"><span data-stu-id="0d49f-128">JIT compiler improvements</span></span>

<span data-ttu-id="0d49f-129">**分层编译仍然是一项可选功能**</span><span class="sxs-lookup"><span data-stu-id="0d49f-129">**Tiered compilation remains an opt-in feature**</span></span>

<span data-ttu-id="0d49f-130">在 .NET Core 2.1，JIT 编译器实现了一项新的编译器技术，即“分层编译”  ，作为可选功能。</span><span class="sxs-lookup"><span data-stu-id="0d49f-130">In .NET Core 2.1, the JIT compiler implemented a new compiler technology, *tiered compilation*, as an opt-in feature.</span></span> <span data-ttu-id="0d49f-131">分层编译旨在提高性能。</span><span class="sxs-lookup"><span data-stu-id="0d49f-131">The goal of tiered compilation is improved performance.</span></span> <span data-ttu-id="0d49f-132">由 JIT 编译器执行的重要任务之一是优化代码执行。</span><span class="sxs-lookup"><span data-stu-id="0d49f-132">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="0d49f-133">然而，对于很少使用的代码路径，相比执行未优化代码所花费的运行时，编译器可能需要更多的时间来优化代码。</span><span class="sxs-lookup"><span data-stu-id="0d49f-133">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends executing unoptimized code.</span></span> <span data-ttu-id="0d49f-134">分层编译介绍了 JIT 编译中的两个阶段：</span><span class="sxs-lookup"><span data-stu-id="0d49f-134">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="0d49f-135">第一层  ，将尽可能快地生成代码。</span><span class="sxs-lookup"><span data-stu-id="0d49f-135">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="0d49f-136">第二层  ，将为那些频繁执行的方法生成优化代码。</span><span class="sxs-lookup"><span data-stu-id="0d49f-136">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="0d49f-137">为了增强性能，第二层编译并行执行。</span><span class="sxs-lookup"><span data-stu-id="0d49f-137">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="0d49f-138">有关分层编译可能带来的性能改进的信息，请参阅[宣布发布 .NET Core 2.2 预览版 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/)。</span><span class="sxs-lookup"><span data-stu-id="0d49f-138">For information on the performance improvement that can result from tiered compilation, see [Announcing .NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span></span>

<span data-ttu-id="0d49f-139">在 .NET Core 2.2 预览版 2 中，默认情况下已启用分层编译。</span><span class="sxs-lookup"><span data-stu-id="0d49f-139">In .NET Core 2.2 Preview 2, tiered compilation was enabled by default.</span></span> <span data-ttu-id="0d49f-140">但是，我们仍然没有准备好在默认情况下启用分层编译。</span><span class="sxs-lookup"><span data-stu-id="0d49f-140">However, we've decided that we are still not ready to enable tiered compilation by default.</span></span> <span data-ttu-id="0d49f-141">因此在 .NET Core 2.2 中，分层编译仍是一项可选功能。</span><span class="sxs-lookup"><span data-stu-id="0d49f-141">So in .NET Core 2.2, tiered compilation continues to be an opt-in feature.</span></span> <span data-ttu-id="0d49f-142">有关选择加入分层编译的信息，请参阅 [.NET Core 2.1 中的新增功能](dotnet-core-2-1.md)中的 [Jit 编译器改进](dotnet-core-2-1.md#jit-compiler-improvements)。</span><span class="sxs-lookup"><span data-stu-id="0d49f-142">For information on opting in to tiered compilation, see [Jit compiler improvements](dotnet-core-2-1.md#jit-compiler-improvements) in [What's new in .NET Core 2.1](dotnet-core-2-1.md).</span></span>

## <a name="runtime"></a><span data-ttu-id="0d49f-143">运行时</span><span class="sxs-lookup"><span data-stu-id="0d49f-143">Runtime</span></span>

<span data-ttu-id="0d49f-144">**在执行 Main 方法之前注入代码**</span><span class="sxs-lookup"><span data-stu-id="0d49f-144">**Injecting code prior to executing the Main method**</span></span>

<span data-ttu-id="0d49f-145">从 .NET Core 2.2 开始，可以使用启动挂钩注入代码，然后再运行应用程序的 Main 方法。</span><span class="sxs-lookup"><span data-stu-id="0d49f-145">Starting with .NET Core 2.2, you can use a startup hook to inject code prior to running an application's Main method.</span></span> <span data-ttu-id="0d49f-146">启动挂钩使主机可以在部署应用程序之后自定义其行为，而不需要重新编译或更改应用程序。</span><span class="sxs-lookup"><span data-stu-id="0d49f-146">Startup hooks make it possible for a host to customize the behavior of applications after they have been deployed without needing to recompile or change the application.</span></span>

<span data-ttu-id="0d49f-147">我们希望托管提供商定义自定义配置和策略，包括可能会影响主入口点加载行为的设置，如 <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> 行为。</span><span class="sxs-lookup"><span data-stu-id="0d49f-147">We expect hosting providers to define custom configuration and policy, including settings that potentially influence the load behavior of the main entry point, such as the <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> behavior.</span></span> <span data-ttu-id="0d49f-148">挂钩可用于设置跟踪或遥测注入，以设置回调进行处理，或定义其他环境相关的行为。</span><span class="sxs-lookup"><span data-stu-id="0d49f-148">The hook can be used to set up tracing or telemetry injection, to set up callbacks for handling, or to define other environment-dependent behavior.</span></span> <span data-ttu-id="0d49f-149">挂钩独立于入口点，因此不需要修改用户代码。</span><span class="sxs-lookup"><span data-stu-id="0d49f-149">The hook is separate from the entry point, so that user code doesn't need to be modified.</span></span>

<span data-ttu-id="0d49f-150">有关详细信息，请参阅[主机启动挂钩](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md)。</span><span class="sxs-lookup"><span data-stu-id="0d49f-150">See [Host startup hook](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d49f-151">请参阅</span><span class="sxs-lookup"><span data-stu-id="0d49f-151">See also</span></span>

- [<span data-ttu-id="0d49f-152">.NET Core 3.1 的新增功能</span><span class="sxs-lookup"><span data-stu-id="0d49f-152">What's new in .NET Core 3.1</span></span>](dotnet-core-3-1.md)
- [<span data-ttu-id="0d49f-153">ASP.NET Core 2.2 的新增功能</span><span class="sxs-lookup"><span data-stu-id="0d49f-153">What's new in ASP.NET Core 2.2</span></span>](/aspnet/core/release-notes/aspnetcore-2.2)
- [<span data-ttu-id="0d49f-154">EF Core 2.2 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="0d49f-154">New features in EF Core 2.2</span></span>](/ef/core/what-is-new/ef-core-2.2)
