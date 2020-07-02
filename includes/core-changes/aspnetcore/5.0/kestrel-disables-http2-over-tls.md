---
ms.openlocfilehash: 92210f6becb5a5a43893ee0fd51ef51e2ddd7f8d
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325233"
---
### <a name="kestrel-http2-disabled-over-tls-on-incompatible-windows-versions"></a><span data-ttu-id="ccf60-101">Kestrel：在不兼容的 Windows 版本上通过 TLS 禁用 HTTP/2</span><span class="sxs-lookup"><span data-stu-id="ccf60-101">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>

<span data-ttu-id="ccf60-102">要在 Windows 上启用基于传输层安全性 (TLS) 的 HTTP/2，需要满足以下两个要求：</span><span class="sxs-lookup"><span data-stu-id="ccf60-102">To enable HTTP/2 over Transport Layer Security (TLS) on Windows, two requirements need to be met:</span></span>

- <span data-ttu-id="ccf60-103">应用层协议协商 (ALPN) 支持，从 Windows 8.1 和 Windows Server 2012 R2 开始提供。</span><span class="sxs-lookup"><span data-stu-id="ccf60-103">Application-Layer Protocol Negotiation (ALPN) support, which is available starting with Windows 8.1 and Windows Server 2012 R2.</span></span>
- <span data-ttu-id="ccf60-104">与 HTTP/2 兼容的一组密码，从 Windows 10 和 Windows Server 2016 开始提供。</span><span class="sxs-lookup"><span data-stu-id="ccf60-104">A set of ciphers compatible with HTTP/2, which is available starting with Windows 10 and Windows Server 2016.</span></span>

<span data-ttu-id="ccf60-105">因此，配置基于 TLS 的 HTTP/2 时，Kestrel 的行为已更改为：</span><span class="sxs-lookup"><span data-stu-id="ccf60-105">As such, Kestrel's behavior when HTTP/2 over TLS is configured has changed to:</span></span>

- <span data-ttu-id="ccf60-106">当 [ListenOptions.HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) 设置为 `Http1AndHttp2` 时，降级到 `Http1` 并记录 `Information` 级别的消息。</span><span class="sxs-lookup"><span data-stu-id="ccf60-106">Downgrade to `Http1` and log a message at the `Information` level when [ListenOptions.HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) is set to `Http1AndHttp2`.</span></span> <span data-ttu-id="ccf60-107">`Http1AndHttp2` 是 `ListenOptions.HttpProtocols` 的默认值。</span><span class="sxs-lookup"><span data-stu-id="ccf60-107">`Http1AndHttp2` is the default value for `ListenOptions.HttpProtocols`.</span></span>
- <span data-ttu-id="ccf60-108">当 `ListenOptions.HttpProtocols` 设置为 `Http2` 时，引发 `NotSupportedException`。</span><span class="sxs-lookup"><span data-stu-id="ccf60-108">Throw a `NotSupportedException` when `ListenOptions.HttpProtocols` is set to `Http2`.</span></span>

<span data-ttu-id="ccf60-109">有关讨论，请参阅问题 [dotnet/aspnetcore#23068](https://github.com/dotnet/aspnetcore/issues/23068)。</span><span class="sxs-lookup"><span data-stu-id="ccf60-109">For discussion, see issue [dotnet/aspnetcore#23068](https://github.com/dotnet/aspnetcore/issues/23068).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ccf60-110">引入的版本</span><span class="sxs-lookup"><span data-stu-id="ccf60-110">Version introduced</span></span>

<span data-ttu-id="ccf60-111">ASP.NET Core 5.0 预览版 7</span><span class="sxs-lookup"><span data-stu-id="ccf60-111">ASP.NET Core 5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ccf60-112">旧行为</span><span class="sxs-lookup"><span data-stu-id="ccf60-112">Old behavior</span></span>

<span data-ttu-id="ccf60-113">下表概述了配置基于 TLS 的 HTTP/2 时的行为。</span><span class="sxs-lookup"><span data-stu-id="ccf60-113">The following table outlines the behavior when HTTP/2 over TLS is configured.</span></span>

| <span data-ttu-id="ccf60-114">协议</span><span class="sxs-lookup"><span data-stu-id="ccf60-114">Protocols</span></span> | <span data-ttu-id="ccf60-115">Windows 7、</span><span class="sxs-lookup"><span data-stu-id="ccf60-115">Windows 7,</span></span><br /><span data-ttu-id="ccf60-116">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="ccf60-116">Windows Server 2008 R2,</span></span><br /><span data-ttu-id="ccf60-117">或更早版本</span><span class="sxs-lookup"><span data-stu-id="ccf60-117">or earlier</span></span> | <span data-ttu-id="ccf60-118">Windows 8、</span><span class="sxs-lookup"><span data-stu-id="ccf60-118">Windows 8,</span></span><br /><span data-ttu-id="ccf60-119">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="ccf60-119">Windows Server 2012</span></span> | <span data-ttu-id="ccf60-120">Windows 8.1、</span><span class="sxs-lookup"><span data-stu-id="ccf60-120">Windows 8.1,</span></span><br /><span data-ttu-id="ccf60-121">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ccf60-121">Windows Server 2012 R2</span></span> | <span data-ttu-id="ccf60-122">Windows 10、</span><span class="sxs-lookup"><span data-stu-id="ccf60-122">Windows 10,</span></span><br /><span data-ttu-id="ccf60-123">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="ccf60-123">Windows Server 2016,</span></span><br /><span data-ttu-id="ccf60-124">或更高版本</span><span class="sxs-lookup"><span data-stu-id="ccf60-124">or newer</span></span> |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | <span data-ttu-id="ccf60-125">引发 `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="ccf60-125">Throw `NotSupportedException`</span></span>                   | <span data-ttu-id="ccf60-126">TLS 握手期间出错</span><span class="sxs-lookup"><span data-stu-id="ccf60-126">Error during TLS handshake</span></span>     | <span data-ttu-id="ccf60-127">TLS 握手期间出错 &ast;</span><span class="sxs-lookup"><span data-stu-id="ccf60-127">Error during TLS handshake &ast;</span></span>     | <span data-ttu-id="ccf60-128">无错误</span><span class="sxs-lookup"><span data-stu-id="ccf60-128">No error</span></span> |
| `Http1AndHttp2` | <span data-ttu-id="ccf60-129">降级到 `Http1`</span><span class="sxs-lookup"><span data-stu-id="ccf60-129">Downgrade to `Http1`</span></span>                    | <span data-ttu-id="ccf60-130">降级到 `Http1`</span><span class="sxs-lookup"><span data-stu-id="ccf60-130">Downgrade to `Http1`</span></span>     | <span data-ttu-id="ccf60-131">TLS 握手期间出错 &ast;</span><span class="sxs-lookup"><span data-stu-id="ccf60-131">Error during TLS handshake &ast;</span></span>     | <span data-ttu-id="ccf60-132">无错误</span><span class="sxs-lookup"><span data-stu-id="ccf60-132">No error</span></span> |

<span data-ttu-id="ccf60-133">&ast; 配置兼容密码套件以支持这些方案。</span><span class="sxs-lookup"><span data-stu-id="ccf60-133">&ast; Configure compatible cipher suites to enable these scenarios.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ccf60-134">新行为</span><span class="sxs-lookup"><span data-stu-id="ccf60-134">New behavior</span></span>

<span data-ttu-id="ccf60-135">下表概述了配置基于 TLS 的 HTTP/2 时的行为。</span><span class="sxs-lookup"><span data-stu-id="ccf60-135">The following table outlines the behavior when HTTP/2 over TLS is configured.</span></span>

| <span data-ttu-id="ccf60-136">协议</span><span class="sxs-lookup"><span data-stu-id="ccf60-136">Protocols</span></span> | <span data-ttu-id="ccf60-137">Windows 7、</span><span class="sxs-lookup"><span data-stu-id="ccf60-137">Windows 7,</span></span><br /><span data-ttu-id="ccf60-138">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="ccf60-138">Windows Server 2008 R2,</span></span><br /><span data-ttu-id="ccf60-139">或更早版本</span><span class="sxs-lookup"><span data-stu-id="ccf60-139">or earlier</span></span> | <span data-ttu-id="ccf60-140">Windows 8、</span><span class="sxs-lookup"><span data-stu-id="ccf60-140">Windows 8,</span></span><br /><span data-ttu-id="ccf60-141">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="ccf60-141">Windows Server 2012</span></span> | <span data-ttu-id="ccf60-142">Windows 8.1、</span><span class="sxs-lookup"><span data-stu-id="ccf60-142">Windows 8.1,</span></span><br /><span data-ttu-id="ccf60-143">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ccf60-143">Windows Server 2012 R2</span></span> | <span data-ttu-id="ccf60-144">Windows 10、</span><span class="sxs-lookup"><span data-stu-id="ccf60-144">Windows 10,</span></span><br /><span data-ttu-id="ccf60-145">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="ccf60-145">Windows Server 2016,</span></span><br /><span data-ttu-id="ccf60-146">或更高版本</span><span class="sxs-lookup"><span data-stu-id="ccf60-146">or newer</span></span> |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | <span data-ttu-id="ccf60-147">引发 `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="ccf60-147">Throw `NotSupportedException`</span></span>                   | <span data-ttu-id="ccf60-148">引发 `NotSupportedException`</span><span class="sxs-lookup"><span data-stu-id="ccf60-148">Throw `NotSupportedException`</span></span>     | <span data-ttu-id="ccf60-149">引发 `NotSupportedException` &ast;&ast;</span><span class="sxs-lookup"><span data-stu-id="ccf60-149">Throw `NotSupportedException` &ast;&ast;</span></span>     | <span data-ttu-id="ccf60-150">无错误</span><span class="sxs-lookup"><span data-stu-id="ccf60-150">No error</span></span> |
| `Http1AndHttp2` | <span data-ttu-id="ccf60-151">降级到 `Http1`</span><span class="sxs-lookup"><span data-stu-id="ccf60-151">Downgrade to `Http1`</span></span>                    | <span data-ttu-id="ccf60-152">降级到 `Http1`</span><span class="sxs-lookup"><span data-stu-id="ccf60-152">Downgrade to `Http1`</span></span>     | <span data-ttu-id="ccf60-153">降级到 `Http1` &ast;&ast;</span><span class="sxs-lookup"><span data-stu-id="ccf60-153">Downgrade to `Http1` &ast;&ast;</span></span>     | <span data-ttu-id="ccf60-154">无错误</span><span class="sxs-lookup"><span data-stu-id="ccf60-154">No error</span></span> |

<span data-ttu-id="ccf60-155">&ast;&ast; 配置兼容的密码套件并将应用上下文切换 `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` 设置为 `true` 以启用这些方案。</span><span class="sxs-lookup"><span data-stu-id="ccf60-155">&ast;&ast; Configure compatible cipher suites and set the app context switch `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` to `true` to enable these scenarios.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ccf60-156">更改原因</span><span class="sxs-lookup"><span data-stu-id="ccf60-156">Reason for change</span></span>

<span data-ttu-id="ccf60-157">此更改可确保在较早的 Windows 版本上尽早、尽可能清晰地呈现基于 TLS 的 HTTP/2 的兼容性错误。</span><span class="sxs-lookup"><span data-stu-id="ccf60-157">This change ensures compatibility errors for HTTP/2 over TLS on older Windows versions are surfaced as early and as clearly as possible.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ccf60-158">建议操作</span><span class="sxs-lookup"><span data-stu-id="ccf60-158">Recommended action</span></span>

<span data-ttu-id="ccf60-159">确保在不兼容的 Windows 版本上禁用基于 TLS 的 HTTP/2。</span><span class="sxs-lookup"><span data-stu-id="ccf60-159">Ensure HTTP/2 over TLS is disabled on incompatible Windows versions.</span></span> <span data-ttu-id="ccf60-160">Windows 8.1 和 Windows Server 2012 R2 是不兼容的，因为默认情况下它们缺少必要的密码。</span><span class="sxs-lookup"><span data-stu-id="ccf60-160">Windows 8.1 and Windows Server 2012 R2 are incompatible since they lack the necessary ciphers by default.</span></span> <span data-ttu-id="ccf60-161">但是，可以将“计算机配置”设置更新为使用 HTTP/2 兼容密码。</span><span class="sxs-lookup"><span data-stu-id="ccf60-161">However, it's possible to update the Computer Configuration settings to use HTTP/2 compatible ciphers.</span></span> <span data-ttu-id="ccf60-162">有关详细信息，请参阅 [Windows 8.1 中的 TLS 密码套件](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1)。</span><span class="sxs-lookup"><span data-stu-id="ccf60-162">For more information, see [TLS cipher suites in Windows 8.1](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1).</span></span> <span data-ttu-id="ccf60-163">配置完成后，必须通过设置应用上下文切换 `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2`，在 Kestrel 上启用基于 TLS 的 HTTP/2。</span><span class="sxs-lookup"><span data-stu-id="ccf60-163">Once configured, HTTP/2 over TLS on Kestrel must be enabled by setting the app context switch `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2`.</span></span> <span data-ttu-id="ccf60-164">例如：</span><span class="sxs-lookup"><span data-stu-id="ccf60-164">For example:</span></span>

```csharp
AppContext.SetSwitch("Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2", true);
```

<span data-ttu-id="ccf60-165">未更改基础支持。</span><span class="sxs-lookup"><span data-stu-id="ccf60-165">No underlying support has changed.</span></span> <span data-ttu-id="ccf60-166">例如，基于 TLS 的 HTTP/2 在 Windows 8 或 Windows Server 2012 上始终无效。</span><span class="sxs-lookup"><span data-stu-id="ccf60-166">For example, HTTP/2 over TLS has never worked on Windows 8 or Windows Server 2012.</span></span> <span data-ttu-id="ccf60-167">此更改将修改这些不受支持的方案中错误的呈现方式。</span><span class="sxs-lookup"><span data-stu-id="ccf60-167">This change modifies how errors in these unsupported scenarios are presented.</span></span>

#### <a name="category"></a><span data-ttu-id="ccf60-168">类别</span><span class="sxs-lookup"><span data-stu-id="ccf60-168">Category</span></span>

<span data-ttu-id="ccf60-169">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ccf60-169">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ccf60-170">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="ccf60-170">Affected APIs</span></span>

<span data-ttu-id="ccf60-171">None</span><span class="sxs-lookup"><span data-stu-id="ccf60-171">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
