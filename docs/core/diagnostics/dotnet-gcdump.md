---
title: dotnet-gcdump - .NET Core
description: 安装和使用 dotnet-gcdump 命令行工具。
ms.date: 07/26/2020
ms.openlocfilehash: a7b19f4d7487677b975621e7267a17894dae2e3a
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656646"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a>堆分析工具 (dotnet-gcdump)

**本文适用于：** ✔️ .NET Core 3.1 SDK 及更高版本

## <a name="install-dotnet-gcdump"></a>安装 dotnet-gcdump

若要安装最新版 `dotnet-gcdump` [NuGet 包](https://www.nuget.org/packages/dotnet-gcdump)，请使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：

```dotnetcli
dotnet tool install -g dotnet-gcdump
```

## <a name="synopsis"></a>摘要

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a>描述

`dotnet-gcdump` 全局工具可用于为活动 .NET 进程收集 GC（垃圾回收器）转储。 它使用 EventPipe 技术，这是 Windows 上 ETW 的一个跨平台替代方法。 创建 GC 转储时需要在目标进程中触发 GC、开启特殊事件并从事件流中重新生成对象根图。 此过程允许在进程运行时以最小的开销收集 GC 转储。 这些转储对于以下几种情况非常有用：

- 比较多个时间点堆上的对象数。
- 分析对象的根（回答诸如“还有哪些引用此类型的内容？”等问题）。
- 收集有关堆上的对象计数的常规统计信息。

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a>查看从 dotnet-gcdump 捕获的 GC 转储

在 Windows 上，可以在 [PerfView](https://github.com/microsoft/perfview) 中查看 `.gcdump` 文件，以便进行分析，也可在 Visual Studio 中查看该文件。 目前，无法在非 Windows 平台上打开 `.gcdump`。

可以收集多个 `.gcdump`，并在 Visual Studio 中同时打开它们以获取比较体验。

## <a name="options"></a>选项

- **`--version`**

  显示 `dotnet-gcdump` 实用工具的版本。

- **`-h|--help`**

  显示命令行帮助。

## `dotnet-gcdump collect`

从当前正在运行的进程中收集 GC 转储。

### <a name="synopsis"></a>摘要

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a>选项

- **`-h|--help`**

  显示命令行帮助。

- **`-p|--process-id <pid>`**

  可从中收集 GC 转储的进程 ID。

- **`-o|--output <gcdump-file-path>`**

  应写入收集 GC 转储的路径。 默认为 .\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump。

- **`-v|--verbose`**

  收集 GC 转储时输出日志。

- **`-t|--timeout <timeout>`**

  如果收集 GC 转储的时间超过了此秒数，则放弃收集。 默认值为 30。

- **`-n|--name <name>`**

  可从中收集 GC 转储的进程的名称。

## `dotnet-gcdump ps`

列出可为其收集 GC 转储的 dotnet 进程。

### <a name="synopsis"></a>摘要

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

从以前生成的 GC 转储或从正在运行的进程生成报表，并将其写入 `stdout`。

### <a name="synopsis"></a>摘要

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a>选项

- **`-h|--help`**

  显示命令行帮助。

- **`-p|--process-id <pid>`**

  可从中收集 GC 转储的进程 ID。

- **`-t|--report-type <HeapStat>`**

  可生成报表的类型。 可用选项：heapstat（默认）。

## <a name="troubleshoot"></a>疑难解答

- gcdump 中没有类型信息。

   在 .NET Core 3.1 之前，存在一个问题，即使用 EventPipe 调用 gcdump 时，gcdump 之间的类型缓存没有清除。 这导致确定类型信息所需的事件未发送给第二个和后续 gcdump。 此问题已在 .NET Core 3.1-preview2 中得以修复。

- COM 和静态类型不在 GC 转储中。

   在 .NET Core 3.1-preview2 之前，存在一个问题，即通过 EventPipe 调用 GC 转储时，不会发送静态和 COM 类型。 此问题已在 .NET Core 3.1-preview2 中得以修复。
