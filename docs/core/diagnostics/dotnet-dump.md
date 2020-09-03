---
title: dotnet-dump - .NET Core
description: 安装和使用 dotnet-dump 命令行工具。
ms.date: 10/14/2019
ms.openlocfilehash: 5489011538a4a11d60b333f0230a718c88722c97
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140927"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a><span data-ttu-id="e904d-103">转储收集和分析实用工具 (dotnet-dump)</span><span class="sxs-lookup"><span data-stu-id="e904d-103">Dump collection and analysis utility (dotnet-dump)</span></span>

<span data-ttu-id="e904d-104"> 本文适用于： ✔️ .NET Core 3.0 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="e904d-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

> [!NOTE]
> <span data-ttu-id="e904d-105">macOS 上不支持 `dotnet-dump`。</span><span class="sxs-lookup"><span data-stu-id="e904d-105">`dotnet-dump` isn't supported on macOS.</span></span>

## <a name="install-dotnet-dump"></a><span data-ttu-id="e904d-106">安装 dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="e904d-106">Install dotnet-dump</span></span>

<span data-ttu-id="e904d-107">若要安装最新版 `dotnet-dump` [NuGet 包](https://www.nuget.org/packages/dotnet-dump)，请使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="e904d-107">To install the latest release version of the `dotnet-dump` [NuGet package](https://www.nuget.org/packages/dotnet-dump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a><span data-ttu-id="e904d-108">摘要</span><span class="sxs-lookup"><span data-stu-id="e904d-108">Synopsis</span></span>

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="e904d-109">描述</span><span class="sxs-lookup"><span data-stu-id="e904d-109">Description</span></span>

<span data-ttu-id="e904d-110">`dotnet-dump` 全局工具是在未涉及任何本机调试器（如 Linux 上的 `lldb`）的情况下收集和分析 Windows 和 Linux 转储的方法。</span><span class="sxs-lookup"><span data-stu-id="e904d-110">The `dotnet-dump` global tool is a way to collect and analyze Windows and Linux dumps without any native debugger involved like `lldb` on Linux.</span></span> <span data-ttu-id="e904d-111">在 `lldb` 无法正常运行的平台（如 Alpine Linux）上，此工具非常重要。</span><span class="sxs-lookup"><span data-stu-id="e904d-111">This tool is important on platforms like Alpine Linux where a fully working `lldb` isn't available.</span></span> <span data-ttu-id="e904d-112">借助 `dotnet-dump` 工具，可以运行 SOS 命令来分析崩溃和垃圾回收器 (GC)，但它不是本机调试器，因此不支持显示本机堆栈帧之类的操作。</span><span class="sxs-lookup"><span data-stu-id="e904d-112">The `dotnet-dump` tool allows you to run SOS commands to analyze crashes and the garbage collector (GC), but it isn't a native debugger so things like displaying native stack frames aren't supported.</span></span>

## <a name="options"></a><span data-ttu-id="e904d-113">选项</span><span class="sxs-lookup"><span data-stu-id="e904d-113">Options</span></span>

- **`--version`**

  <span data-ttu-id="e904d-114">显示 dotnet-dump 实用工具的版本。</span><span class="sxs-lookup"><span data-stu-id="e904d-114">Displays the version of the dotnet-dump utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="e904d-115">显示命令行帮助。</span><span class="sxs-lookup"><span data-stu-id="e904d-115">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="e904d-116">命令</span><span class="sxs-lookup"><span data-stu-id="e904d-116">Commands</span></span>

| <span data-ttu-id="e904d-117">命令</span><span class="sxs-lookup"><span data-stu-id="e904d-117">Command</span></span>                                     |
| ------------------------------------------- |
| [<span data-ttu-id="e904d-118">dotnet-dump collect</span><span class="sxs-lookup"><span data-stu-id="e904d-118">dotnet-dump collect</span></span>](#dotnet-dump-collect) |
| [<span data-ttu-id="e904d-119">dotnet-dump analyze</span><span class="sxs-lookup"><span data-stu-id="e904d-119">dotnet-dump analyze</span></span>](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a><span data-ttu-id="e904d-120">dotnet-dump collect</span><span class="sxs-lookup"><span data-stu-id="e904d-120">dotnet-dump collect</span></span>

<span data-ttu-id="e904d-121">从进程捕获转储。</span><span class="sxs-lookup"><span data-stu-id="e904d-121">Captures a dump from a process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e904d-122">摘要</span><span class="sxs-lookup"><span data-stu-id="e904d-122">Synopsis</span></span>

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a><span data-ttu-id="e904d-123">选项</span><span class="sxs-lookup"><span data-stu-id="e904d-123">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="e904d-124">显示命令行帮助。</span><span class="sxs-lookup"><span data-stu-id="e904d-124">Shows command-line help.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="e904d-125">指定从中收集内存转储的进程的 ID 号。</span><span class="sxs-lookup"><span data-stu-id="e904d-125">Specifies the process ID number to collect a memory dump from.</span></span>

- **`--type <Heap|Mini>`**

  <span data-ttu-id="e904d-126">指定转储类型，它确定从进程收集的信息的类型。</span><span class="sxs-lookup"><span data-stu-id="e904d-126">Specifies the dump type, which determines the kinds of information that are collected from the process.</span></span> <span data-ttu-id="e904d-127">分为两种类型：</span><span class="sxs-lookup"><span data-stu-id="e904d-127">There are two types:</span></span>

  - <span data-ttu-id="e904d-128">`Heap` - 大型且相对全面的转储，其中包含模块列表、线程列表、所有堆栈、异常信息、句柄信息和除映射图像以外的所有内存。</span><span class="sxs-lookup"><span data-stu-id="e904d-128">`Heap` - A large and relatively comprehensive dump containing module lists, thread lists, all stacks, exception information, handle information, and all memory except for mapped images.</span></span>
  - <span data-ttu-id="e904d-129">`Mini` - 小型转储，其中包含模块列表、线程列表、异常信息和所有堆栈。</span><span class="sxs-lookup"><span data-stu-id="e904d-129">`Mini` - A small dump containing module lists, thread lists, exception information, and all stacks.</span></span>

  <span data-ttu-id="e904d-130">如果未指定，则 `Heap` 为默认类型。</span><span class="sxs-lookup"><span data-stu-id="e904d-130">If not specified, `Heap` is the default.</span></span>

- **`-o|--output <output_dump_path>`**

  <span data-ttu-id="e904d-131">应在其中写入收集的转储的完整路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="e904d-131">The full path and file name where the collected dump should be written.</span></span>

  <span data-ttu-id="e904d-132">如果未指定：</span><span class="sxs-lookup"><span data-stu-id="e904d-132">If not specified:</span></span>

  - <span data-ttu-id="e904d-133">在 Windows 上默认为 .\dump_YYYYMMDD_HHMMSS.dmp  。</span><span class="sxs-lookup"><span data-stu-id="e904d-133">Defaults to *.\dump_YYYYMMDD_HHMMSS.dmp* on Windows.</span></span>
  - <span data-ttu-id="e904d-134">在 Linux 上默认为 ./core_YYYYMMDD_HHMMSS  。</span><span class="sxs-lookup"><span data-stu-id="e904d-134">Defaults to *./core_YYYYMMDD_HHMMSS* on Linux.</span></span>

  <span data-ttu-id="e904d-135">YYYYMMDD 为年/月/日，HHMMSS 为小时/分钟/秒。</span><span class="sxs-lookup"><span data-stu-id="e904d-135">YYYYMMDD is Year/Month/Day and HHMMSS is Hour/Minute/Second.</span></span>

- **`--diag`**

  <span data-ttu-id="e904d-136">启用转储收集诊断日志记录。</span><span class="sxs-lookup"><span data-stu-id="e904d-136">Enables dump collection diagnostic logging.</span></span>

## <a name="dotnet-dump-analyze"></a><span data-ttu-id="e904d-137">dotnet-dump analyze</span><span class="sxs-lookup"><span data-stu-id="e904d-137">dotnet-dump analyze</span></span>

<span data-ttu-id="e904d-138">启动交互式 shell 以了解转储。</span><span class="sxs-lookup"><span data-stu-id="e904d-138">Starts an interactive shell to explore a dump.</span></span> <span data-ttu-id="e904d-139">shell 接受各种 [SOS 命令](#analyze-sos-commands)。</span><span class="sxs-lookup"><span data-stu-id="e904d-139">The shell accepts various [SOS commands](#analyze-sos-commands).</span></span>

### <a name="synopsis"></a><span data-ttu-id="e904d-140">摘要</span><span class="sxs-lookup"><span data-stu-id="e904d-140">Synopsis</span></span>

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a><span data-ttu-id="e904d-141">自变量</span><span class="sxs-lookup"><span data-stu-id="e904d-141">Arguments</span></span>

- **`<dump_path>`**

  <span data-ttu-id="e904d-142">指定要分析的转储文件的路径。</span><span class="sxs-lookup"><span data-stu-id="e904d-142">Specifies the path to the dump file to analyze.</span></span>

### <a name="options"></a><span data-ttu-id="e904d-143">选项</span><span class="sxs-lookup"><span data-stu-id="e904d-143">Options</span></span>

- **`-c|--command <debug_command>`**

  <span data-ttu-id="e904d-144">指定要在启动时在 shell 中运行的[命令](#analyze-sos-commands)。</span><span class="sxs-lookup"><span data-stu-id="e904d-144">Specifies the [command](#analyze-sos-commands) to run in the shell on start.</span></span>

### <a name="analyze-sos-commands"></a><span data-ttu-id="e904d-145">分析 SOS 命令</span><span class="sxs-lookup"><span data-stu-id="e904d-145">Analyze SOS commands</span></span>

| <span data-ttu-id="e904d-146">命令</span><span class="sxs-lookup"><span data-stu-id="e904d-146">Command</span></span>                             | <span data-ttu-id="e904d-147">函数</span><span class="sxs-lookup"><span data-stu-id="e904d-147">Function</span></span>                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | <span data-ttu-id="e904d-148">显示所有可用命令</span><span class="sxs-lookup"><span data-stu-id="e904d-148">Displays all available commands</span></span>                                                               |
| `soshelp|help <command>`            | <span data-ttu-id="e904d-149">执行指定的命令。</span><span class="sxs-lookup"><span data-stu-id="e904d-149">Displays the specified command.</span></span>                                                               |
| `exit|quit`                         | <span data-ttu-id="e904d-150">退出交互模式。</span><span class="sxs-lookup"><span data-stu-id="e904d-150">Exits interactive mode.</span></span>                                                                       |
| `clrstack <arguments>`              | <span data-ttu-id="e904d-151">仅提供托管代码的堆栈跟踪。</span><span class="sxs-lookup"><span data-stu-id="e904d-151">Provides a stack trace of managed code only.</span></span>                                                  |
| `clrthreads <arguments>`            | <span data-ttu-id="e904d-152">列出正在运行的托管线程。</span><span class="sxs-lookup"><span data-stu-id="e904d-152">Lists the managed threads running.</span></span>                                                            |
| `dumpasync <arguments>`             | <span data-ttu-id="e904d-153">显示有关垃圾回收堆上异步状态机的信息。</span><span class="sxs-lookup"><span data-stu-id="e904d-153">Displays information about async state machines on the garbage-collected heap.</span></span>                |
| `dumpassembly <arguments>`          | <span data-ttu-id="e904d-154">显示有关程序集的详细信息。</span><span class="sxs-lookup"><span data-stu-id="e904d-154">Displays details about an assembly.</span></span>                                                           |
| `dumpclass <arguments>`             | <span data-ttu-id="e904d-155">显示有关指定地址处的 EE 类结构的信息。</span><span class="sxs-lookup"><span data-stu-id="e904d-155">Displays information about a EE class structure at the specified address.</span></span>                     |
| `dumpdelegate <arguments>`          | <span data-ttu-id="e904d-156">显示有关委托的信息。</span><span class="sxs-lookup"><span data-stu-id="e904d-156">Displays information about a delegate.</span></span>                                                        |
| `dumpdomain <arguments>`            | <span data-ttu-id="e904d-157">显示所有 AppDomain 和域中的所有程序集的信息。</span><span class="sxs-lookup"><span data-stu-id="e904d-157">Displays information all the AppDomains and all assemblies within the domains.</span></span>                |
| `dumpheap <arguments>`              | <span data-ttu-id="e904d-158">显示有关垃圾回收堆的信息和有关对象的收集统计信息。</span><span class="sxs-lookup"><span data-stu-id="e904d-158">Displays info about the garbage-collected heap and collection statistics about objects.</span></span>       |
| `dumpil <arguments>`                | <span data-ttu-id="e904d-159">显示与托管方法关联的 Microsoft 中间语言 (MSIL)。</span><span class="sxs-lookup"><span data-stu-id="e904d-159">Displays the Microsoft intermediate language (MSIL) that is associated with a managed method.</span></span> |
| `dumplog <arguments>`               | <span data-ttu-id="e904d-160">将内存中压力日志的内容写入到指定文件。</span><span class="sxs-lookup"><span data-stu-id="e904d-160">Writes the contents of an in-memory stress log to the specified file.</span></span>                         |
| `dumpmd <arguments>`                | <span data-ttu-id="e904d-161">显示有关指定地址处的 MethodDesc 结构的信息。</span><span class="sxs-lookup"><span data-stu-id="e904d-161">Displays information about a MethodDesc structure at the specified address.</span></span>                   |
| `dumpmodule <arguments>`            | <span data-ttu-id="e904d-162">显示有关指定地址处的 EE 模块结构的信息。</span><span class="sxs-lookup"><span data-stu-id="e904d-162">Displays information about a EE module structure at the specified address.</span></span>                    |
| `dumpmt <arguments>`                | <span data-ttu-id="e904d-163">显示有关指定地址处的方法表的信息。</span><span class="sxs-lookup"><span data-stu-id="e904d-163">Displays information about a method table at the specified address.</span></span>                           |
| `dumpobj <arguments>`               | <span data-ttu-id="e904d-164">显示有关指定地址处的对象的信息。</span><span class="sxs-lookup"><span data-stu-id="e904d-164">Displays info about an object at the specified address.</span></span>                                       |
| `dso|dumpstackobjects <arguments>`  | <span data-ttu-id="e904d-165">显示在当前堆栈的边界内找到的所有托管对象。</span><span class="sxs-lookup"><span data-stu-id="e904d-165">Displays all managed objects found within the bounds of the current stack.</span></span>                    |
| `eeheap <arguments>`                | <span data-ttu-id="e904d-166">显示有关内部运行时数据结构所使用的进程内存的信息。</span><span class="sxs-lookup"><span data-stu-id="e904d-166">Displays info about process memory consumed by internal runtime data structures.</span></span>              |
| `finalizequeue <arguments>`         | <span data-ttu-id="e904d-167">显示所有已进行终结注册的对象。</span><span class="sxs-lookup"><span data-stu-id="e904d-167">Displays all objects registered for finalization.</span></span>                                             |
| `gcroot <arguments>`                | <span data-ttu-id="e904d-168">显示有关对指定地址处的对象的引用（或根）的信息。</span><span class="sxs-lookup"><span data-stu-id="e904d-168">Displays info about references (or roots) to an object at the specified address.</span></span>              |
| `gcwhere <arguments>`               | <span data-ttu-id="e904d-169">显示传入参数在 GC 堆中的位置。</span><span class="sxs-lookup"><span data-stu-id="e904d-169">Displays the location in the GC heap of the argument passed in.</span></span>                               |
| `ip2md <arguments>`                 | <span data-ttu-id="e904d-170">显示 JIT 代码中指定地址处的 MethodDesc 结构。</span><span class="sxs-lookup"><span data-stu-id="e904d-170">Displays the MethodDesc structure at the specified address in JIT code.</span></span>                       |
| `histclear <arguments>`             | <span data-ttu-id="e904d-171">释放由 `hist*` 命令系列使用的任何资源。</span><span class="sxs-lookup"><span data-stu-id="e904d-171">Releases any resources used by the family of `hist*` commands.</span></span>                                |
| `histinit <arguments>`              | <span data-ttu-id="e904d-172">从保存在调试对象中的压力日志初始化 SOS 结构。</span><span class="sxs-lookup"><span data-stu-id="e904d-172">Initializes the SOS structures from the stress log saved in the debuggee.</span></span>                     |
| `histobj <arguments>`               | <span data-ttu-id="e904d-173">显示与 `<arguments>` 相关的垃圾回收压力日志重定位。</span><span class="sxs-lookup"><span data-stu-id="e904d-173">Displays the garbage collection stress log relocations related to `<arguments>`.</span></span>              |
| `histobjfind <arguments>`           | <span data-ttu-id="e904d-174">显示在指定地址处引用对象的所有日志项。</span><span class="sxs-lookup"><span data-stu-id="e904d-174">Displays all the log entries that reference an object at the specified address.</span></span>               |
| `histroot <arguments>`              | <span data-ttu-id="e904d-175">显示与指定根的提升和重定位相关的信息。</span><span class="sxs-lookup"><span data-stu-id="e904d-175">Displays information related to both promotions and relocations of the specified root.</span></span>        |
| `lm|modules`                        | <span data-ttu-id="e904d-176">显示进程中的本机模块。</span><span class="sxs-lookup"><span data-stu-id="e904d-176">Displays the native modules in the process.</span></span>                                                   |
| `name2ee <arguments>`               | <span data-ttu-id="e904d-177">显示 `<argument>` 的 MethodTable 结构和 EEClass 结构。</span><span class="sxs-lookup"><span data-stu-id="e904d-177">Displays the MethodTable structure and EEClass structure for the `<argument>`.</span></span>                |
| `pe|printexception <arguments>`     | <span data-ttu-id="e904d-178">显示从地址 `<argument>` 处的 Exception 类派生的任何对象。</span><span class="sxs-lookup"><span data-stu-id="e904d-178">Displays any object derived from the Exception class at the address `<argument>`.</span></span>             |
| `setsymbolserver <arguments>`       | <span data-ttu-id="e904d-179">启用符号服务器支持</span><span class="sxs-lookup"><span data-stu-id="e904d-179">Enables the symbol server support</span></span>                                                             |
| `syncblk <arguments>`               | <span data-ttu-id="e904d-180">显示 SyncBlock 持有者信息。</span><span class="sxs-lookup"><span data-stu-id="e904d-180">Displays the SyncBlock holder info.</span></span>                                                           |
| `threads|setthread <threadid>`      | <span data-ttu-id="e904d-181">设置或显示 SOS 命令的当前线程 ID。</span><span class="sxs-lookup"><span data-stu-id="e904d-181">Sets or displays the current thread ID for the SOS commands.</span></span>                                  |

## <a name="using-dotnet-dump"></a><span data-ttu-id="e904d-182">使用 `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="e904d-182">Using `dotnet-dump`</span></span>

<span data-ttu-id="e904d-183">第一步是收集转储。</span><span class="sxs-lookup"><span data-stu-id="e904d-183">The first step is to collect a dump.</span></span> <span data-ttu-id="e904d-184">如果已生成核心转储，则可以跳过此步骤。</span><span class="sxs-lookup"><span data-stu-id="e904d-184">This step can be skipped if a core dump has already been generated.</span></span> <span data-ttu-id="e904d-185">操作系统或 .NET Core 运行时的内置[转储生成功能](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md)均可以创建核心转储。</span><span class="sxs-lookup"><span data-stu-id="e904d-185">The operating system or the .NET Core runtime's built-in [dump generation feature](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) can each create core dumps.</span></span>

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

<span data-ttu-id="e904d-186">现在，使用 `analyze` 命令分析核心转储：</span><span class="sxs-lookup"><span data-stu-id="e904d-186">Now analyze the core dump with the `analyze` command:</span></span>

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

<span data-ttu-id="e904d-187">此操作会显示一个交互式会话，该会话接受以下类似命令：</span><span class="sxs-lookup"><span data-stu-id="e904d-187">This action brings up an interactive session that accepts commands like:</span></span>

```console
> clrstack
OS Thread Id: 0x573d (0)
    Child SP               IP Call Site
00007FFD28B42C58 00007fb22c1a8ed9 [HelperMethodFrame_PROTECTOBJ: 00007ffd28b42c58] System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo) [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.Program.Foo4(System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.Program.Foo2(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.Program.Foo1(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.Program.Main(System.String[]) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]
00007FFD28B43210 00007fb22aa9cedf [GCFrame: 00007ffd28b43210]
00007FFD28B43610 00007fb22aa9cedf [GCFrame: 00007ffd28b43610]
```

<span data-ttu-id="e904d-188">查看已终止应用的未经处理的异常：</span><span class="sxs-lookup"><span data-stu-id="e904d-188">To see an unhandled exception that killed your app:</span></span>

```console
> pe -lines
Exception object: 00007fb18c038590
Exception type:   System.Reflection.TargetInvocationException
Message:          Exception has been thrown by the target of an invocation.
InnerException:   System.Exception, Use !PrintException 00007FB18C038368 to see more.
StackTrace (generated):
SP               IP               Function
00007FFD28B42DD0 0000000000000000 System.Private.CoreLib.dll!System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Private.CoreLib.dll!System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo)+0xa7 [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.dll!SymbolTestApp.Program.Foo4(System.String)+0x15d [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.dll!SymbolTestApp.Program.Foo2(Int32, System.String)+0x34 [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.dll!SymbolTestApp.Program.Foo1(Int32, System.String)+0x3a [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.dll!SymbolTestApp.Program.Main(System.String[])+0x6e [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]

StackTraceString: <none>
HResult: 80131604
```

## <a name="special-instructions-for-docker"></a><span data-ttu-id="e904d-189">Docker 的特殊说明</span><span class="sxs-lookup"><span data-stu-id="e904d-189">Special instructions for Docker</span></span>

<span data-ttu-id="e904d-190">如果在 Docker 下运行，则转储集合需要 `SYS_PTRACE` 功能（`--cap-add=SYS_PTRACE` 或 `--privileged`）。</span><span class="sxs-lookup"><span data-stu-id="e904d-190">If you're running under Docker, dump collection requires `SYS_PTRACE` capabilities (`--cap-add=SYS_PTRACE` or `--privileged`).</span></span>

<span data-ttu-id="e904d-191">在 Microsoft .NET Core SDK Linux Docker 映像上，某些 `dotnet-dump` 命令可能会引发以下异常：</span><span class="sxs-lookup"><span data-stu-id="e904d-191">On Microsoft .NET Core SDK Linux Docker images, some `dotnet-dump` commands can throw the following exception:</span></span>

> <span data-ttu-id="e904d-192">未经处理的异常：System.DllNotFoundException:无法加载共享库“libdl.so”或其依赖项之一的异常。</span><span class="sxs-lookup"><span data-stu-id="e904d-192">Unhandled exception: System.DllNotFoundException: Unable to load shared library 'libdl.so' or one of its dependencies' exception.</span></span>

<span data-ttu-id="e904d-193">若要解决此问题，请安装“libc6-dev”包。</span><span class="sxs-lookup"><span data-stu-id="e904d-193">To work around this problem, install the "libc6-dev" package.</span></span>

## <a name="see-also"></a><span data-ttu-id="e904d-194">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e904d-194">See also</span></span>

- [<span data-ttu-id="e904d-195">收集和分析内存转储博客</span><span class="sxs-lookup"><span data-stu-id="e904d-195">Collecting and analyzing memory dumps blog</span></span>](https://devblogs.microsoft.com/dotnet/collecting-and-analyzing-memory-dumps/)
- [<span data-ttu-id="e904d-196">堆分析工具 (dotnet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="e904d-196">Heap analysis tool (dotnet-gcdump)</span></span>](dotnet-gcdump.md)
