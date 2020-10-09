---
ms.openlocfilehash: d61a3b3dd855d783d7bff7cb74e5b84969e60860
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608038"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a><span data-ttu-id="3641d-101">ASP.NET 多部分处理不正确可能会导致丢失窗体数据。</span><span class="sxs-lookup"><span data-stu-id="3641d-101">ASP.NET Incorrect multipart handling may result in lost form data.</span></span>

#### <a name="details"></a><span data-ttu-id="3641d-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="3641d-102">Details</span></span>

<span data-ttu-id="3641d-103">在面向 .NET Framework 4.7.2 及更低版本的应用程序中，ASP.NET 可能会错误地解析多部分边界值，从而导致窗体数据在请求执行期间不可用。</span><span class="sxs-lookup"><span data-stu-id="3641d-103">In applications that target .NET Framework 4.7.2 and earlier versions, ASP.NET might incorrectly parse multipart boundary values, resulting in form data being unavailable during request execution.</span></span> <span data-ttu-id="3641d-104">面向 .NET Framework 4.8 或更高版本的应用程序正确解析多部分数据，因此在请求执行期间可以使用窗体值。</span><span class="sxs-lookup"><span data-stu-id="3641d-104">Applications that target .NET Framework 4.8 or later versions correctly parse multipart data, so form values are available during request execution.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3641d-105">建议</span><span class="sxs-lookup"><span data-stu-id="3641d-105">Suggestion</span></span>

<span data-ttu-id="3641d-106">从运行 .NET Framework 4.8 的应用程序开始，在面向 .NET Framework 4.8 或更高版本时使用 <code>targetFrameworkVersion</code> 元素，默认行为将更改为竖线分隔符。</span><span class="sxs-lookup"><span data-stu-id="3641d-106">Starting with applications running on .NET Framework 4.8, when targeting .NET Framework 4.8 or later by using the <code>targetFrameworkVersion</code> element, the default behavior changes to strip delimiters.</span></span> <span data-ttu-id="3641d-107">在面向上述框架版本或不使用 <code>targetFrameworkVersion</code> 时，仍会返回一些值的尾随分隔符。此行为也可以通过 <code>appSetting</code> 显式控制：</span><span class="sxs-lookup"><span data-stu-id="3641d-107">When targeting previous framework versions or not using <code>targetFrameworkVersion</code>, trailing delimiters for some values are still returned.This behavior can also be explicitly controlled with an <code>appSetting</code>:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="3641d-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="3641d-108">Name</span></span>    | <span data-ttu-id="3641d-109">“值”</span><span class="sxs-lookup"><span data-stu-id="3641d-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3641d-110">范围</span><span class="sxs-lookup"><span data-stu-id="3641d-110">Scope</span></span>   |<span data-ttu-id="3641d-111">未知</span><span class="sxs-lookup"><span data-stu-id="3641d-111">Unknown</span></span>|
|<span data-ttu-id="3641d-112">Version</span><span class="sxs-lookup"><span data-stu-id="3641d-112">Version</span></span>|<span data-ttu-id="3641d-113">4.8</span><span class="sxs-lookup"><span data-stu-id="3641d-113">4.8</span></span>|
|<span data-ttu-id="3641d-114">类型</span><span class="sxs-lookup"><span data-stu-id="3641d-114">Type</span></span>|<span data-ttu-id="3641d-115">运行时</span><span class="sxs-lookup"><span data-stu-id="3641d-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="3641d-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="3641d-116">Affected APIs</span></span>

- <xref:System.Web.HttpRequest.Form?displayProperty=nameWithType>
- <xref:System.Web.HttpRequest.Files?displayProperty=nameWithType>
- <xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.HttpRequest.Form`
- `P:System.Web.HttpRequest.Files`
- `P:System.Web.HttpRequest.ContentEncoding`

-->
