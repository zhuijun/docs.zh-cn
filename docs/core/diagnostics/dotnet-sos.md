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
# <a name="sos-installer-dotnet-sos"></a><span data-ttu-id="2817b-103">SOS 安装程序 (dotnet-sos)</span><span class="sxs-lookup"><span data-stu-id="2817b-103">SOS installer (dotnet-sos)</span></span>

<span data-ttu-id="2817b-104">本文适用于： ✔️ .NET Core 2.1 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="2817b-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install-dotnet-sos"></a><span data-ttu-id="2817b-105">安装 dotnet-sos</span><span class="sxs-lookup"><span data-stu-id="2817b-105">Install dotnet-sos</span></span>

<span data-ttu-id="2817b-106">若要安装最新版 `dotnet-sos` [NuGet 包](https://www.nuget.org/packages/dotnet-sos)，请使用 [dotnet tool install](../tools/dotnet-tool-install.md) 命令：</span><span class="sxs-lookup"><span data-stu-id="2817b-106">To install the latest release version of the `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-sos
```

## <a name="synopsis"></a><span data-ttu-id="2817b-107">摘要</span><span class="sxs-lookup"><span data-stu-id="2817b-107">Synopsis</span></span>

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a><span data-ttu-id="2817b-108">描述</span><span class="sxs-lookup"><span data-stu-id="2817b-108">Description</span></span>

<span data-ttu-id="2817b-109">`dotnet-sos` 全局工具可安装 [SOS 调试器扩展](../../framework/tools/sos-dll-sos-debugging-extension.md)，从而允许从本机调试器（例如 Windows 上的 WinDbg/cdb 以及 Linux 和 macOS 上的 lldb）[检查托管的 .NET Core 状态](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="2817b-109">The `dotnet-sos` global tool installs the [SOS debugger extension](../../framework/tools/sos-dll-sos-debugging-extension.md) allowing [inspection of managed .NET Core state](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) from native debuggers like WinDbg/cdb on Windows and lldb on Linux and macOS.</span></span> <span data-ttu-id="2817b-110">最新版本（WinDbg 或 cdb 的 10.0.18317.1001 版本及更高版本）的 Windows 调试器将自动从 Microsoft 扩展库加载 SOS，因此，只有在 Linux 和 macOS 或在使用较旧的调试工具的 Windows 上，才需要通过 `dotnet-sos` 工具安装 SOS。</span><span class="sxs-lookup"><span data-stu-id="2817b-110">Recent versions of the Windows Debugger (>= version 10.0.18317.1001 of WinDbg or cdb) will load SOS automatically from the Microsoft extension gallery, so installing SOS via the `dotnet-sos` tool is only needed on Linux and macOS or on Windows if using older debugging tools.</span></span>

## <a name="options"></a><span data-ttu-id="2817b-111">选项</span><span class="sxs-lookup"><span data-stu-id="2817b-111">Options</span></span>

- **`--version`**

  <span data-ttu-id="2817b-112">显示版本信息。</span><span class="sxs-lookup"><span data-stu-id="2817b-112">Displays version information.</span></span>

- **`-h|--help`**

  <span data-ttu-id="2817b-113">显示命令行帮助。</span><span class="sxs-lookup"><span data-stu-id="2817b-113">Shows command-line help.</span></span>

## <a name="dotnet-sos-install"></a><span data-ttu-id="2817b-114">安装 dotnet-sos</span><span class="sxs-lookup"><span data-stu-id="2817b-114">dotnet-sos install</span></span>

<span data-ttu-id="2817b-115">在本地安装用于调试 .NET Core 进程的 [SOS 扩展](../../framework/tools/sos-dll-sos-debugging-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="2817b-115">Installs the [SOS extension](../../framework/tools/sos-dll-sos-debugging-extension.md) locally for debugging .NET Core processes.</span></span> <span data-ttu-id="2817b-116">在 macOS 和 Linux 上，将更新 .lldbinit 文件，以便扩展在 lldb 启动时自动加载。</span><span class="sxs-lookup"><span data-stu-id="2817b-116">On macOS and Linux, the .lldbinit file will be updated so that the extension automatically loads at lldb startup.</span></span> <span data-ttu-id="2817b-117">如果在使用较旧的调试工具（低于版本 10.0.18317.1001）的 Windows 上安装 SOS，则需要通过在调试器中运行 `.load %USERPROFILE%\.dotnet\sos\sos.dll` 以在 WinDbg 或 cdb 中手动加载扩展。</span><span class="sxs-lookup"><span data-stu-id="2817b-117">If installing SOS on Windows with older debugging tools (< version 10.0.18317.1001), you will need to manually load the extension in WinDbg or cdb by running `.load %USERPROFILE%\.dotnet\sos\sos.dll` in the debugger.</span></span>

### <a name="synopsis"></a><span data-ttu-id="2817b-118">摘要</span><span class="sxs-lookup"><span data-stu-id="2817b-118">Synopsis</span></span>

```console
dotnet-sos install
```

## <a name="dotnet-sos-uninstall"></a><span data-ttu-id="2817b-119">卸载 dotnet-sos</span><span class="sxs-lookup"><span data-stu-id="2817b-119">dotnet-sos uninstall</span></span>

<span data-ttu-id="2817b-120">卸载 [SOS 扩展](../../framework/tools/sos-dll-sos-debugging-extension.md)，如果该扩展位于 Linux 或 macOS 上，则将其从 lldb 配置中删除。</span><span class="sxs-lookup"><span data-stu-id="2817b-120">Uninstalls the [SOS extension](../../framework/tools/sos-dll-sos-debugging-extension.md) and, if on Linux or macOS, removes it from lldb configuration.</span></span>

### <a name="synopsis"></a><span data-ttu-id="2817b-121">摘要</span><span class="sxs-lookup"><span data-stu-id="2817b-121">Synopsis</span></span>

```console
dotnet-sos uninstall
```
