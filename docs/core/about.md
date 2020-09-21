---
title: .NET Core 概述
description: 了解 .NET Core 的特性和组合，并将其与其他 .NET 实现进行比较。
ms.date: 03/26/2020
ms.openlocfilehash: e99939cf85cc441fd473e4d033e22b1a5d053638
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539003"
---
# <a name="net-core-overview"></a>.NET Core 概述

> [!div class="button"]
> [下载 .NET Core](https://dotnet.microsoft.com/download)

.NET Core 具有以下特性：

- 跨平台：可在 Windows、macOS 和 Linux [操作系统](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)上运行。
- **开放源代码：** .NET Core 框架是[开放源代码](https://github.com/dotnet/core)，使用 MIT 和 Apache 2 许可证。 .NET Core 是一个 [.NET Foundation](https://dotnetfoundation.org/) 项目。
- 现代：它实现了异步编程、使用结构的无复制模式和容器的资源调控等现代范例。
- **性能：** 通过各种功能（如[硬件内部函数](https://devblogs.microsoft.com/dotnet/hardware-intrinsics-in-net-core/)、[分层编译](https://github.com/dotnet/coreclr/blob/master/Documentation/design-docs/tiered-compilation.md)和 [Span\<T>](../standard/memory-and-spans/index.md)）来提供[高性能](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-core-3-0/)。
- 跨环境一致：在多个操作系统和体系结构（包括 x64、x86 和 ARM）上以相同的行为运行代码。
- **命令行工具：** 包括可用于本地开发和持续集成的易于使用的命令行工具。
- **部署灵活：** 可以在应用中包含 .NET Core 或并行安装它（用户或系统范围安装）。 可搭配 [Docker 容器](docker/introduction.md)使用。

## <a name="languages"></a>语言

可以使用 [C#](../csharp/index.yml)、[Visual Basic](../visual-basic/index.yml) 和 [F#](../fsharp/index.yml) 语言编写适用于 .NET Core 的应用程序和库。 这些语言可在你喜欢的文本编辑器或集成开发环境 (IDE) 中使用，包括：

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Visual Studio Code](https://code.visualstudio.com/download)

编辑器集成部分由 [OmniSharp](https://www.omnisharp.net/) 和 [Ionide](https://ionide.io) 项目的参与者提供。

## <a name="apis"></a>API

.NET Core 公开用于生成任意类型的应用的框架：

* 使用 [ASP.NET Core](/aspnet/core/) 的云应用
* 使用 [Xamarin](/xamarin) 的移动应用
* 使用 [System.Device.GPIO](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0) 的 IoT 应用
* 使用 [WPF](../desktop-wpf/overview/index.md) 和 Windows 窗体的 Windows 客户端应用
* 机器学习 [ML.NET](../machine-learning/index.yml)

包括满足常见需求的多个 API：

- 基元类型，如 <xref:System.Boolean?displayProperty=nameWithType> 和 <xref:System.Int32?displayProperty=nameWithType>。
- 集合，例如 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 和 <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>。
- 实用程序类型，例如 <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 和 <xref:System.IO.FileStream?displayProperty=nameWithType>。
- 数据类型，例如 <xref:System.Data.DataSet?displayProperty=nameWithType> 和 <xref:System.Data.Entity.DbSet?displayProperty=nameWithType>。
- 高性能类型，例如 <xref:System.Span%601?displayProperty=nameWithType>、<xref:System.Numerics.Vector?displayProperty=nameWithType> 和 [Pipelines](../standard/io/pipelines.md)。

.NET Core 通过实现 [.NET Standard](../standard/net-standard.md) 规范提供 .NET Framework 和 Mono API 的兼容性。

## <a name="composition"></a>撰写

.NET Core 包括以下部分：

- [.NET Core 运行时](https://github.com/dotnet/runtime/tree/master/src/coreclr)：提供类型系统、程序集加载、垃圾回收器、本机互操作和其他基本服务。 [.NET Core 框架库](https://github.com/dotnet/runtime/tree/master/src/libraries)：提供基元数据类型、应用编写类型和基本实用程序。
- [ASP.NET Core 运行时](https://github.com/dotnet/aspnetcore)：提供一个框架来生成基于云且连接到 Internet 的新式应用程序，例如 Web 应用、IoT 应用和移动后端。
- [.NET Core SDK](https://github.com/dotnet/sdk) 和语言编译器（[Roslyn](https://github.com/dotnet/roslyn) 和 [F#](https://github.com/microsoft/visualfsharp)）：提供 .NET Core 开发人员体验。
- [dotnet 命令](./tools/dotnet.md)：用于启动 .NET Core 应用和 CLI 命令。 它选择并托管运行时，提供程序集加载策略并启动应用和工具。

### <a name="open-source"></a>开源

[.NET Core](about.md) 是一个通用的[开放源代码](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)开发平台。 可以针对 x64、x86、ARM32 和 ARM64 处理器创建适用于 Windows、macOS 和 Linux 的 .NET Core 应用。 为[云](/aspnet/core/)、[IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)、[客户端 UI](../desktop-wpf/overview/index.md) 和[机器学习](../machine-learning/index.yml)提供了框架和 API。

## <a name="support"></a>支持

[Microsoft 支持](https://dotnet.microsoft.com/platform/support/policy)在 Windows、macOS 和 Linux 上使用 .NET Core。 它会定期更新以保证安全和质量（每月的第二个星期二）。

Microsoft 的 .NET Core 二进制发行版在 Azure 中的 Microsoft 维护服务器上进行生成和测试，并遵循 Microsoft 的工程和安全实践。

[Red Hat 支持在 Red Hat Enterprise Linux (RHEL) 上使用 .NET Core](https://developers.redhat.com/topics/dotnet/)。 Red Hat 从源中生成 .NET Core，并在 [Red Hat 软件集合](https://developers.redhat.com/products/softwarecollections/overview/)中提供它。 Red Hat 和 Microsoft 开展协作，共同确保 .NET Core 能够在 RHEL 上正常运行。

[Tizen 支持在 Tizen 平台上使用 .NET Core](https://developer.tizen.org/development/training/.net-application)。
