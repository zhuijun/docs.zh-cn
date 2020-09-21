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
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="9acac-103">用于网络的运行时配置选项</span><span class="sxs-lookup"><span data-stu-id="9acac-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="9acac-104">HTTP/2 协议</span><span class="sxs-lookup"><span data-stu-id="9acac-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="9acac-105">配置是否启用对 HTTP/2 协议的支持。</span><span class="sxs-lookup"><span data-stu-id="9acac-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>

- <span data-ttu-id="9acac-106">如果省略此设置，则会禁用对 HTTP/2 协议的支持。</span><span class="sxs-lookup"><span data-stu-id="9acac-106">If you omit this setting, support for the HTTP/2 protocol is disabled.</span></span> <span data-ttu-id="9acac-107">它等效于将值设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="9acac-107">This is equivalent to setting the value to `false`.</span></span>

- <span data-ttu-id="9acac-108">已在 .NET Core 3.0 中引入。</span><span class="sxs-lookup"><span data-stu-id="9acac-108">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="9acac-109">设置名</span><span class="sxs-lookup"><span data-stu-id="9acac-109">Setting name</span></span> | <span data-ttu-id="9acac-110">值</span><span class="sxs-lookup"><span data-stu-id="9acac-110">Values</span></span> |
| - | - | - |
| <span data-ttu-id="9acac-111">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="9acac-111">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="9acac-112">`false` - 禁用</span><span class="sxs-lookup"><span data-stu-id="9acac-112">`false` - disabled</span></span><br/><span data-ttu-id="9acac-113">`true` - 启用</span><span class="sxs-lookup"><span data-stu-id="9acac-113">`true` - enabled</span></span> |
| <span data-ttu-id="9acac-114">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="9acac-114">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="9acac-115">`0` - 禁用</span><span class="sxs-lookup"><span data-stu-id="9acac-115">`0` - disabled</span></span><br/><span data-ttu-id="9acac-116">`1` - 启用</span><span class="sxs-lookup"><span data-stu-id="9acac-116">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="9acac-117">UseSocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="9acac-117">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="9acac-118">配置 <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> 是使用 <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> 还是使用旧的 HTTP 协议堆栈（在 Windows 上为 <xref:System.Net.Http.WinHttpHandler>，在 Linux 上为基于 [libcurl](https://curl.haxx.se/libcurl/) 实现的内部类 `CurlHandler`。）</span><span class="sxs-lookup"><span data-stu-id="9acac-118">Configures whether <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uses <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or older HTTP protocol stacks (<xref:System.Net.Http.WinHttpHandler> on Windows and `CurlHandler`, an internal class implemented on top of [libcurl](https://curl.haxx.se/libcurl/), on Linux).</span></span>

  > [!NOTE]
  > <span data-ttu-id="9acac-119">可使用高级别网络 API，而不是直接实例化 <xref:System.Net.Http.HttpClientHandler> 类。</span><span class="sxs-lookup"><span data-stu-id="9acac-119">You may be using high-level networking APIs instead of directly instantiating the <xref:System.Net.Http.HttpClientHandler> class.</span></span> <span data-ttu-id="9acac-120">此设置还会影响高级别网络 API 使用的 HTTP 协议堆栈类型，包括 <xref:System.Net.Http.HttpClient> 和 [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118))。</span><span class="sxs-lookup"><span data-stu-id="9acac-120">This setting also affects which HTTP protocol stack is used by high-level networking APIs, including <xref:System.Net.Http.HttpClient> and [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118)).</span></span>

- <span data-ttu-id="9acac-121">如果省略此设置，<xref:System.Net.Http.HttpClientHandler> 将使用 <xref:System.Net.Http.SocketsHttpHandler>。</span><span class="sxs-lookup"><span data-stu-id="9acac-121">If you omit this setting, <xref:System.Net.Http.HttpClientHandler> uses <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="9acac-122">它等效于将值设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="9acac-122">This is equivalent to setting the value to `true`.</span></span>

- <span data-ttu-id="9acac-123">可通过调用 <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> 方法，以编程方式配置此设置。</span><span class="sxs-lookup"><span data-stu-id="9acac-123">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="9acac-124">设置名</span><span class="sxs-lookup"><span data-stu-id="9acac-124">Setting name</span></span> | <span data-ttu-id="9acac-125">值</span><span class="sxs-lookup"><span data-stu-id="9acac-125">Values</span></span> |
| - | - | - |
| <span data-ttu-id="9acac-126">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="9acac-126">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="9acac-127">`true` - 允许使用 <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="9acac-127">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="9acac-128">`false` - 允许使用 Windows 上的 <xref:System.Net.Http.WinHttpHandler> 或 Linux 上的 [libcurl](https://curl.haxx.se/libcurl/)</span><span class="sxs-lookup"><span data-stu-id="9acac-128">`false` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |
| <span data-ttu-id="9acac-129">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="9acac-129">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="9acac-130">`1` - 允许使用 <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="9acac-130">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="9acac-131">`0` - 允许使用 Windows 上的 <xref:System.Net.Http.WinHttpHandler> 或 Linux 上的 [libcurl](https://curl.haxx.se/libcurl/)</span><span class="sxs-lookup"><span data-stu-id="9acac-131">`0` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |

> [!NOTE]
> <span data-ttu-id="9acac-132">从 .NET 5 开始，`System.Net.Http.UseSocketsHttpHandler` 设置不再可用。</span><span class="sxs-lookup"><span data-stu-id="9acac-132">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>
