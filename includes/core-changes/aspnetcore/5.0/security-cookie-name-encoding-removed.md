---
ms.openlocfilehash: 492d3e61acff31d3d6858a1c27cf353b04a05e36
ms.sourcegitcommit: d4f7ba08f2a45a9dbef53be597eed6d4a9410f29
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2020
ms.locfileid: "86401973"
---
### <a name="security-cookie-name-encoding-removed"></a><span data-ttu-id="8fc9f-101">安全性：Cookie 名称编码已删除</span><span class="sxs-lookup"><span data-stu-id="8fc9f-101">Security: Cookie name encoding removed</span></span>

<span data-ttu-id="8fc9f-102">[HTTP Cookie 标准](https://tools.ietf.org/html/rfc6265#section-4.1.1) 仅允许在 Cookie 名称和值中使用特定字符。</span><span class="sxs-lookup"><span data-stu-id="8fc9f-102">The [HTTP cookie standard](https://tools.ietf.org/html/rfc6265#section-4.1.1) allows only specific characters in cookie names and values.</span></span> <span data-ttu-id="8fc9f-103">为了支持不允许的字符，ASP.NET Core：</span><span class="sxs-lookup"><span data-stu-id="8fc9f-103">To support disallowed characters, ASP.NET Core:</span></span>

* <span data-ttu-id="8fc9f-104">在创建响应 Cookie 时进行编码。</span><span class="sxs-lookup"><span data-stu-id="8fc9f-104">Encodes when creating a response cookie.</span></span>
* <span data-ttu-id="8fc9f-105">在读取请求 Cookie 时进行解码。</span><span class="sxs-lookup"><span data-stu-id="8fc9f-105">Decodes when reading a request cookie.</span></span>

<span data-ttu-id="8fc9f-106">在 ASP.NET Core 5.0 中，此编码行为因安全问题发生了更改。</span><span class="sxs-lookup"><span data-stu-id="8fc9f-106">In ASP.NET Core 5.0, this encoding behavior changed in response to a security concern.</span></span>

<span data-ttu-id="8fc9f-107">有关讨论，请参阅 GitHub 问题 [dotnet/aspnetcore#23578](https://github.com/dotnet/aspnetcore/issues/23578)。</span><span class="sxs-lookup"><span data-stu-id="8fc9f-107">For discussion, see GitHub issue [dotnet/aspnetcore#23578](https://github.com/dotnet/aspnetcore/issues/23578).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8fc9f-108">引入的版本</span><span class="sxs-lookup"><span data-stu-id="8fc9f-108">Version introduced</span></span>

<span data-ttu-id="8fc9f-109">5.0 预览版 8</span><span class="sxs-lookup"><span data-stu-id="8fc9f-109">5.0 Preview 8</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8fc9f-110">旧行为</span><span class="sxs-lookup"><span data-stu-id="8fc9f-110">Old behavior</span></span>

<span data-ttu-id="8fc9f-111">对响应 Cookie 名称进行编码。</span><span class="sxs-lookup"><span data-stu-id="8fc9f-111">Response cookie names are encoded.</span></span> <span data-ttu-id="8fc9f-112">对请求 Cookie 名称进行解码。</span><span class="sxs-lookup"><span data-stu-id="8fc9f-112">Request cookie names are decoded.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="8fc9f-113">新行为</span><span class="sxs-lookup"><span data-stu-id="8fc9f-113">New behavior</span></span>

<span data-ttu-id="8fc9f-114">删除了 Cookie 名称的编码和解码。</span><span class="sxs-lookup"><span data-stu-id="8fc9f-114">Encoding and decoding of cookie names was removed.</span></span> <span data-ttu-id="8fc9f-115">对于先前[受支持的 ASP.NET Core 版本](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)，团队计划就地缓解解码问题。</span><span class="sxs-lookup"><span data-stu-id="8fc9f-115">For prior [supported versions](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) of ASP.NET Core, the team plans to mitigate the decoding issue in-place.</span></span> <span data-ttu-id="8fc9f-116">此外，使用无效的 Cookie 名称调用 <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> 将引发 <xref:System.ArgumentException> 类型的异常。</span><span class="sxs-lookup"><span data-stu-id="8fc9f-116">Additionally, calling <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> with an invalid cookie name throws an exception of type <xref:System.ArgumentException>.</span></span> <span data-ttu-id="8fc9f-117">Cookie 值的编码和解码保持不变。</span><span class="sxs-lookup"><span data-stu-id="8fc9f-117">Encoding and decoding of cookie values remains unchanged.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8fc9f-118">更改原因</span><span class="sxs-lookup"><span data-stu-id="8fc9f-118">Reason for change</span></span>

<span data-ttu-id="8fc9f-119">在[多个 Web 框架](https://github.com/advisories/GHSA-j6w9-fv6q-3q52)中发现了问题。</span><span class="sxs-lookup"><span data-stu-id="8fc9f-119">An issue was discovered in [multiple web frameworks](https://github.com/advisories/GHSA-j6w9-fv6q-3q52).</span></span> <span data-ttu-id="8fc9f-120">编码和解码可以使攻击者使用诸如 `__%48ost-` 的编码值来假冒 `__Host-` 之类的保留前缀，从而绕过称为 [Cookie 前缀](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00)的安全功能。</span><span class="sxs-lookup"><span data-stu-id="8fc9f-120">The encoding and decoding could allow an attacker to bypass a security feature called [cookie prefixes](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) by spoofing reserved prefixes like `__Host-` with encoded values like `__%48ost-`.</span></span> <span data-ttu-id="8fc9f-121">此攻击需要利用辅助攻击（例如跨站点脚本 (XSS) 漏洞）在网站中注入欺诈性 Cookie。</span><span class="sxs-lookup"><span data-stu-id="8fc9f-121">The attack requires a secondary exploit to inject the spoofed cookies, such as a cross-site scripting (XSS) vulnerability, in the website.</span></span> <span data-ttu-id="8fc9f-122">默认情况下，ASP.NET Core 或者 `Microsoft.Owin` 库或模板中不使用这些前缀。</span><span class="sxs-lookup"><span data-stu-id="8fc9f-122">These prefixes aren't used by default in ASP.NET Core or `Microsoft.Owin` libraries or templates.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8fc9f-123">建议操作</span><span class="sxs-lookup"><span data-stu-id="8fc9f-123">Recommended action</span></span>

<span data-ttu-id="8fc9f-124">如果要将项目迁移到 ASP.NET Core 5.0 或更高版本，请确保其 Cookie 名称符合[令牌规范要求](https://tools.ietf.org/html/rfc2616#section-2.2)：ASCII 字符不包括控件和分隔符 `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT`。</span><span class="sxs-lookup"><span data-stu-id="8fc9f-124">If you're moving projects to ASP.NET Core 5.0 or later, ensure that their cookie names conform to the [token specification requirements](https://tools.ietf.org/html/rfc2616#section-2.2): ASCII characters excluding controls and separators `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT`.</span></span> <span data-ttu-id="8fc9f-125">如果在 Cookie 名称或其他 HTTP 标头中使用非 ASCII 字符，则可能导致服务器异常或客户端不正确地往返。</span><span class="sxs-lookup"><span data-stu-id="8fc9f-125">The use of non-ASCII characters in cookie names or other HTTP headers may cause an exception from the server or be improperly round-tripped by the client.</span></span>

#### <a name="category"></a><span data-ttu-id="8fc9f-126">类别</span><span class="sxs-lookup"><span data-stu-id="8fc9f-126">Category</span></span>

<span data-ttu-id="8fc9f-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8fc9f-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8fc9f-128">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="8fc9f-128">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.HttpRequest.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpResponse.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinRequest.Cookies?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinResponse.Cookies?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.HttpRequest.Cookies`
- `Overload:Microsoft.AspNetCore.Http.HttpResponse.Cookies`
- `P:Microsoft.Owin.IOwinRequest.Cookies`
- `P:Microsoft.Owin.IOwinResponse.Cookies`

-->
