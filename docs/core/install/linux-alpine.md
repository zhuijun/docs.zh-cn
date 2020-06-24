---
title: 在 Alpine 上安装 .NET Core - .NET Core
description: 演示在 Alpine 上安装 .NET Core SDK 和 .NET Core 运行时的各种方法。
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: bbaf4ee9020dcd33c894b5376bf04ad65db8d378
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2020
ms.locfileid: "84771487"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-alpine"></a>在 Alpine 上安装 .NET Core SDK 或 .NET Core 运行时

本文介绍如何在 Alpine 上安装 .NET Core。 如果 Alpine 版本不再受到支持，则该版本不再支持 .NET Core。 不过，这些说明可帮助你在这些版本上运行 .NET Core，即使它不受支持。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

Alpine 没有安装程序。 必须使用[安装脚本](#scripted-install)或按照[手动安装](#manual-install)说明进行操作。

## <a name="supported-distributions"></a>支持的发行版

下表列出了当前支持的 .NET Core 版本以及支持它们的 Alpine 版本。 这些版本在 [.NET Core 到达支持终止日期](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或 [Alpine 的版本到达有效期](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)之前仍受支持。

- ✔️ 指示 Alpine 或 .NET Core 版本仍受支持。
- ❌ 指示 Alpine 或 .NET Core 版本在该 Alpine 发行版本上不受支持。
- 当 Alpine 版本和 .NET Core 版本都有 ✔️ 时，则支持该 OS 和 .NET 的组合。

| Alpine                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 预览版 |
|--------------------------|---------------|---------------|----------------|
| ✔️ 3.12  | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 预览版 |
| ✔️ 3.11  | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 预览版 |
| ✔️ 3.10  | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 预览版 |
| ✔️ 3.9   | ✔️ 2.1        | ✔️ 3.1        | ✔️ 5.0 预览版 |
| ❌ 3.8   | ✔️ 2.1        | ❌ 3.1        | ❌ 5.0 预览版 |

以下版本的 .NET Core 不再受到支持。 这些版本的下载仍保持发布状态：

- 3.0
- 2.2
- 2.0

## <a name="dependencies"></a>依赖项

Alpine Linux 上的 .NET Core 要求安装以下依赖项：

- icu-libs
- krb5-libs
- libintl
- libssl1.1（Alpine v3.9 或更高版本）
- libssl1.0 (Alpine v3.8)
- libstdc++
- lttng-ust
- numactl（可选）
- zlib

## <a name="scripted-install"></a>脚本安装

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>手动安装

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>后续步骤

- [教程：使用 Visual Studio Code 通过 .NET Core SDK 创建控制台应用程序](../tutorials/with-visual-studio-code.md)
