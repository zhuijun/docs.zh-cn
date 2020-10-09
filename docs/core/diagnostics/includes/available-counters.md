---
ms.openlocfilehash: 4ffef401c07dbb27db7c0225acdc6817d95bfe11
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2020
ms.locfileid: "91451361"
---
## <a name="available-counters"></a>可用的计数器

通过各种 .NET 包，使用 EventCounters 发布关于垃圾回收 (GC)、实时 (JIT)、程序集、异常、线程、网络和 Web 请求的基本指标。

### <a name="systemruntime-counters"></a>“System.Runtime”计数器

以下计数器作为 .NET 运行时的一部分发布，并在 [`RuntimeEventSource.cs`](https://github.com/dotnet/coreclr/blob/master/src/System.Private.CoreLib/src/System/Diagnostics/Eventing/RuntimeEventSource.cs) 中进行维护。

| 计数器 | 说明 |
|--|--|
| :::no-loc text="% Time in GC since last GC"::: (`time-in-gc`) | 自上次 GC 以来 GC 的时间百分比 |
| :::no-loc text="Allocation Rate"::: (`alloc-rate`) | 分配率（字节） |
| :::no-loc text="CPU Usage"::: (`cpu-usage`) | 进程的 CPU 使用率百分比 |
| :::no-loc text="Exception Count"::: (`exception-count`) | 已发生的异常数 |
| :::no-loc text="GC Heap Size"::: (`gc-heap-size`) | 根据 <xref:System.GC.GetTotalMemory(System.Boolean)?displayProperty=nameWithType> 认为要分配的字节数 |
| :::no-loc text="Gen 0 GC Count"::: (`gen-0-gc-count`) | 第 0 代 GC 发生的次数 |
| :::no-loc text="Gen 0 Size"::: (`gen-0-size`) | 第 0 代 GC 的字节数 |
| :::no-loc text="Gen 1 GC Count"::: (`gen-1-gc-count`) | 第 1 代 GC 发生的次数 |
| :::no-loc text="Gen 1 Size"::: (`gen-1-size`) | 第 1 代 GC 的字节数 |
| :::no-loc text="Gen 2 GC Count"::: (`gen-2-gc-count`) | 第 2 代 GC 发生的次数 |
| :::no-loc text="Gen 2 Size"::: (`gen-2-size`) | 第 2 代 GC 的字节数 |
| :::no-loc text="LOH Size"::: (`loh-size`) | 第 3 代 GC 的字节数 |
| :::no-loc text="POH Size"::: (`poh-size`) | 已固定对象堆的字节数（在 .NET 5 及更高版本中可用） |
| :::no-loc text="GC Fragmentation"::: (`gc-fragmentation`) | GC 堆碎片（在 .NET 5 及更高版本中可用） |
| :::no-loc text="Monitor Lock Contention Count"::: (`monitor-lock-contention-count`) | 尝试锁定监视器时出现争用的次数，基于 <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> |
| :::no-loc text="Number of Active Timers"::: (`active-timer-count`) | 当前活动的 <xref:System.Threading.Timer> 实例的计数，基于 <xref:System.Threading.Timer.ActiveCount?displayProperty=nameWithType> |
| :::no-loc text="Number of Assemblies Loaded"::: (`assembly-count`) | 在某个时间点加载到进程中的 <xref:System.Reflection.Assembly> 实例的计数 |
| :::no-loc text="ThreadPool Completed Work Item Count"::: (`threadpool-completed-items-count`) | 迄今为止 <xref:System.Threading.ThreadPool> 中已处理的工作项数 |
| :::no-loc text="ThreadPool Queue Length"::: (`threadpool-queue-length`) | <xref:System.Threading.ThreadPool> 中当前已加入处理队列的工作项数 |
| :::no-loc text="ThreadPool Thread Count"::: (`threadpool-thread-count`) | <xref:System.Threading.ThreadPool> 中当前存在的线程池线程数，基于 <xref:System.Threading.ThreadPool.ThreadCount?displayProperty=nameWithType> |
| :::no-loc text="Working Set"::: (`working-set`) | 某个时间点映射到进程上下文的物理内存量，基于 <xref:System.Environment.WorkingSet?displayProperty=nameWithType> |
| :::no-loc text="IL Bytes Jitted"::: (`il-bytes-jitted`) | JIT 编译的 IL 的总大小，以字节为单位（在 .NET 5 及更高版本中可用） |
| :::no-loc text="Method Jitted Count"::: (`method-jitted-count`) | JIT 编译的方法数（在 .NET 5 及更高版本中可用） |

### <a name="microsoftaspnetcorehosting-counters"></a>“Microsoft.AspNetCore.Hosting”计数器

以下计数器作为 [ASP.NET Core](/aspnet/core) 的一部分发布，并在 [`HostingEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/master/src/Hosting/Hosting/src/Internal/HostingEventSource.cs) 中进行维护。

| 计数器 | 说明 |
|--|--|
| :::no-loc text="Current Requests"::: (`current-requests`) | 已启动但尚未停止的请求总数 |
| :::no-loc text="Failed Requests"::: (`failed-requests`) | 应用生命周期内发生的失败请求总数 |
| :::no-loc text="Request Rate"::: (`requests-per-second`) | 每秒发生的请求数 |
| :::no-loc text="Total Requests"::: (`total-requests`) | 应用生命周期内发生的请求总数 |

### <a name="microsoftaspnetcorehttpconnections-counters"></a>“Microsoft.AspNetCore.Http.Connections”计数器

以下计数器作为 [ASP.NET Core SignalR](/aspnet/core/signalr/introduction) 的一部分发布，并在 [`HttpConnectionsEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/master/src/SignalR/common/Http.Connections/src/Internal/HttpConnectionsEventSource.cs) 中进行维护。

| 计数器 | 说明 |
|--|--|
| :::no-loc text="Average Connection Duration"::: (`connections-duration`) | 连接的平均持续时间（毫秒） |
| :::no-loc text="Current Connections"::: (`current-connections`) | 已启动但尚未停止的活动连接数 |
| :::no-loc text="Total Connections Started"::: (`connections-started`) | 已启动的连接总数 |
| :::no-loc text="Total Connections Stopped"::: (`connections-stopped`) | 已停止的连接总数 |
| :::no-loc text="Total Connections Timed Out"::: (`connections-timed-out`) | 已超时的连接总数 |

### <a name="microsoft-aspnetcore-server-kestrel-counters"></a>“Microsoft-AspNetCore-Server-Kestrel”计数器

以下计数器作为 [ASP.NET Core Kestrel Web 服务器](/aspnet/core/fundamentals/servers/kestrel)的一部分发布，并在 [`KestrelEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/master/src/Servers/Kestrel/Core/src/Internal/Infrastructure/KestrelEventSource.cs) 中进行维护。

| 计数器 | 说明 |
|--|--|
| :::no-loc text="Connection Queue Length"::: (`connection-queue-length`) | 连接队列的当前长度 |
| :::no-loc text="Connection Rate"::: (`connections-per-second`) | 到 Web 服务器的每秒连接数 |
| :::no-loc text="Current Connections"::: (`current-connections`) | 到 Web 服务器的当前活动连接数 |
| :::no-loc text="Current TLS Handshakes"::: (`current-tls-handshakes`) | 当前 TLS 握手数 |
| :::no-loc text="Current Upgraded Requests (WebSockets)"::: (`current-upgraded-requests`) | 当前升级请求数 (WebSockets) |
| :::no-loc text="Failed TLS Handshakes"::: (`failed-tls-handshakes`) | 失败的 TLS 握手总数 |
| :::no-loc text="Request Queue Length"::: (`request-queue-length`) | 请求队列的当前长度 |
| :::no-loc text="TLS Handshake Rate"::: (`tls-handshakes-per-second`) | 每秒的 TLS 握手数 |
| :::no-loc text="Total Connections"::: (`total-connections`) | 到 Web 服务器的连接总数 |
| :::no-loc text="Total TLS Handshakes"::: (`total-tls-handshakes`) | Web 服务器的 TLS 握手总数 |
