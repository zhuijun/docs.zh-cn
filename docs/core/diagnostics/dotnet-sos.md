---
title: dotnet-sos - .NET Core
description: 了解如何安装和使用 dotnet-sos 命令行工具。
ms.date: 08/26/2020
ms.openlocfilehash: ba83105718909038ca56129ed8a5063aeff12e89
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065079"
---
# <a name="sos-installer-dotnet-sos"></a>SOS 安装程序 (dotnet-sos)

本文适用于： ✔️ .NET Core 2.1 SDK 及更高版本

## <a name="install-dotnet-sos"></a>安装 dotnet-sos

若要安装最新版 `dotnet-sos` [NuGet 包](https://www.nuget.org/packages/dotnet-sos)，请使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：

```dotnetcli
dotnet tool install -g dotnet-sos
```

## <a name="synopsis"></a>摘要

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a>描述

`dotnet-sos` 全局工具可安装 [SOS 调试器扩展](../../framework/tools/sos-dll-sos-debugging-extension.md)，从而允许从本机调试器（例如 Windows 上的 WinDbg/cdb 以及 Linux 和 macOS 上的 lldb）[检查托管的 .NET Core 状态](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md)。 最新版本（WinDbg 或 cdb 的 10.0.18317.1001 版本及更高版本）的 Windows 调试器将自动从 Microsoft 扩展库加载 SOS，因此，只有在 Linux 和 macOS 或在使用较旧的调试工具的 Windows 上，才需要通过 `dotnet-sos` 工具安装 SOS。

## <a name="options"></a>选项

- **`--version`**

  显示版本信息。

- **`-h|--help`**

  显示命令行帮助。

## <a name="dotnet-sos-install"></a>安装 dotnet-sos

在本地安装用于调试 .NET Core 进程的 [SOS 扩展](../../framework/tools/sos-dll-sos-debugging-extension.md)。 在 macOS 和 Linux 上，将更新 .lldbinit 文件，以便扩展在 lldb 启动时自动加载。 如果在使用较旧的调试工具（低于版本 10.0.18317.1001）的 Windows 上安装 SOS，则需要通过在调试器中运行 `.load %USERPROFILE%\.dotnet\sos\sos.dll` 以在 WinDbg 或 cdb 中手动加载扩展。

### <a name="synopsis"></a>摘要

```console
dotnet-sos install
```

## <a name="dotnet-sos-uninstall"></a>卸载 dotnet-sos

卸载 [SOS 扩展](../../framework/tools/sos-dll-sos-debugging-extension.md)，如果该扩展位于 Linux 或 macOS 上，则将其从 lldb 配置中删除。

### <a name="synopsis"></a>摘要

```console
dotnet-sos uninstall
```
