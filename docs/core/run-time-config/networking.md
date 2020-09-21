---
title: 网络配置设置
description: 了解为 .NET Core 应用配置网络的运行时设置。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: d43b68206cc82f4a41df02bd5998702b4f5d0590
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538128"
---
# <a name="run-time-configuration-options-for-networking"></a>用于网络的运行时配置选项

## <a name="http2-protocol"></a>HTTP/2 协议

- 配置是否启用对 HTTP/2 协议的支持。

- 如果省略此设置，则会禁用对 HTTP/2 协议的支持。 它等效于将值设置为 `false`。

- 已在 .NET Core 3.0 中引入。

| | 设置名 | 值 |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false` - 禁用<br/>`true` - 启用 |
| **环境变量** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0` - 禁用<br/>`1` - 启用 |

## <a name="usesocketshttphandler"></a>UseSocketsHttpHandler

- 配置 <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> 是使用 <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> 还是使用旧的 HTTP 协议堆栈（在 Windows 上为 <xref:System.Net.Http.WinHttpHandler>，在 Linux 上为基于 [libcurl](https://curl.haxx.se/libcurl/) 实现的内部类 `CurlHandler`。）

  > [!NOTE]
  > 可使用高级别网络 API，而不是直接实例化 <xref:System.Net.Http.HttpClientHandler> 类。 此设置还会影响高级别网络 API 使用的 HTTP 协议堆栈类型，包括 <xref:System.Net.Http.HttpClient> 和 [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118))。

- 如果省略此设置，<xref:System.Net.Http.HttpClientHandler> 将使用 <xref:System.Net.Http.SocketsHttpHandler>。 它等效于将值设置为 `true`。

- 可通过调用 <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> 方法，以编程方式配置此设置。

| | 设置名 | 值 |
| - | - | - |
| **runtimeconfig.json** | `System.Net.Http.UseSocketsHttpHandler` | `true` - 允许使用 <xref:System.Net.Http.SocketsHttpHandler><br/>`false` - 允许使用 Windows 上的 <xref:System.Net.Http.WinHttpHandler> 或 Linux 上的 [libcurl](https://curl.haxx.se/libcurl/) |
| **环境变量** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1` - 允许使用 <xref:System.Net.Http.SocketsHttpHandler><br/>`0` - 允许使用 Windows 上的 <xref:System.Net.Http.WinHttpHandler> 或 Linux 上的 [libcurl](https://curl.haxx.se/libcurl/) |

> [!NOTE]
> 从 .NET 5 开始，`System.Net.Http.UseSocketsHttpHandler` 设置不再可用。
