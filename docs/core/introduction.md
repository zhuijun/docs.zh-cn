---
title: .NET Core 简介和概述
description: .NET Core 是一种高性能的模块化 .NET 实现，用于创建 Windows、Linux 和 macOS 应用。 了解 .NET Core 以开始使用。
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: b28ad965e54680e2e1134c389266741ade28084f
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226577"
---
# <a name="introduction-to-net-core"></a>.NET Core 简介

[.NET Core](about.md) 是一个通用的[开放源代码](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)开发平台。 可以使用多种编程语言针对 x64、x86、ARM32 和 ARM64 处理器创建适用于 Windows、macOS 和 Linux 的 .NET Core 应用。 为[云](/aspnet/core/)、[IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)、[客户端 UI](../desktop-wpf/overview/index.md) 和[机器学习](/dotnet/machine-learning/)提供了框架和 API。

[下载 .NET Core SDK](https://dotnet.microsoft.com/download)，尝试在计算机上使用 .NET Core。 最新版是 [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)。

## <a name="download-net-core"></a>下载 .NET Core

可以按下列方式获取 .NET Core：

* [适用于 Windows 和 macOS 的安装程序](https://dotnet.microsoft.com/download)
* [Linux 包](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [Docker 容器](https://hub.docker.com/_/microsoft-dotnet-core/)
* [Zip 和 tarball](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [安装脚本](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [发行说明](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a>创建首个应用程序

安装 .NET Core SDK 后，打开命令提示符。 使用以下命令创建并运行应用程序：

```dotnetcli
dotnet new console
dotnet run
```

您应看到以下输出：

```output
Hello World!
```

## <a name="contribute"></a>参与

.NET Core 是一个开放平台。 欢迎所有人参与。

* [开发人员社区](https://developercommunity.visualstudio.com/spaces/61/index.html)的文件产品问题。
* 产品贡献应该在一个项目存储库上进行，例如 [dotnet/runtime](https://github.com/dotnet/runtime)、[dotnet/sdk](https://github.com/dotnet/sdk)、[dotnet/rosyln](https://github.com/dotnet/roslyn) 或 [aspnetcore](https://github.com/dotnet/aspnetcore)。 有关详细信息，请参阅 [.NET Core 存储库](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md)。

## <a name="support"></a>支持

.NET Core 受 Windows、macOS 和 Linux 上的 Microsoft 和 Red Hat Enterprise Linux 上的 Red Hat 支持。

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [.NET Core 教程](tutorials/index.md)

> [!div class="nextstepaction"]
> [在浏览器中试用 .NET Core](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
