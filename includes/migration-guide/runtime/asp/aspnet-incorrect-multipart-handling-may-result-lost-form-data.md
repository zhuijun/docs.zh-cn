---
ms.openlocfilehash: 135d59de135c8416d384b221379f912c8a9172ad
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621927"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a><span data-ttu-id="2bfa9-101">ASP.NET 多部分处理不正确可能会导致丢失窗体数据。</span><span class="sxs-lookup"><span data-stu-id="2bfa9-101">ASP.NET Incorrect multipart handling may result in lost form data.</span></span>

#### <a name="details"></a><span data-ttu-id="2bfa9-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="2bfa9-102">Details</span></span>

<span data-ttu-id="2bfa9-103">在面向 .NET Framework 4.7.2 及更低版本的应用程序中，ASP.Net 可能会错误地解析多部分边界值，从而导致窗体数据在请求执行期间不可用。</span><span class="sxs-lookup"><span data-stu-id="2bfa9-103">In applications that target .NET Framework 4.7.2 and earlier versions, ASP.Net might incorrectly parse multipart boundary values, resulting in form data being unavailable during request execution.</span></span> <span data-ttu-id="2bfa9-104">面向 .NET Framework 4.8 或更高版本的应用程序正确解析多部分数据，因此在请求执行期间可以使用窗体值。</span><span class="sxs-lookup"><span data-stu-id="2bfa9-104">Applications that target .NET Framework 4.8 or later versions correctly parse multipart data, so form values are available during request execution.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2bfa9-105">建议</span><span class="sxs-lookup"><span data-stu-id="2bfa9-105">Suggestion</span></span>

<span data-ttu-id="2bfa9-106">从运行 .NET Framework 4.8 的应用程序开始，在面向 .NET Framework 4.8 或更高版本时使用 <code>targetFrameworkVersion</code> 元素，默认行为将更改为竖线分隔符。</span><span class="sxs-lookup"><span data-stu-id="2bfa9-106">Starting with applications running on .NET Framework 4.8, when targeting .NET Framework 4.8 or later by using the <code>targetFrameworkVersion</code> element, the default behavior changes to strip delimiters.</span></span> <span data-ttu-id="2bfa9-107">在面向上述框架版本或不使用 <code>targetFrameworkVersion</code> 时，仍会返回一些值的尾随分隔符。此行为也可以通过 <code>appSetting</code> 显式控制：</span><span class="sxs-lookup"><span data-stu-id="2bfa9-107">When targeting previous framework versions or not using <code>targetFrameworkVersion</code>, trailing delimiters for some values are still returned.This behavior can also be explicitly controlled with an <code>appSetting</code>:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="2bfa9-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="2bfa9-108">Name</span></span>    | <span data-ttu-id="2bfa9-109">“值”</span><span class="sxs-lookup"><span data-stu-id="2bfa9-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2bfa9-110">范围</span><span class="sxs-lookup"><span data-stu-id="2bfa9-110">Scope</span></span>   |<span data-ttu-id="2bfa9-111">未知</span><span class="sxs-lookup"><span data-stu-id="2bfa9-111">Unknown</span></span>|
|<span data-ttu-id="2bfa9-112">Version</span><span class="sxs-lookup"><span data-stu-id="2bfa9-112">Version</span></span>|<span data-ttu-id="2bfa9-113">4.8</span><span class="sxs-lookup"><span data-stu-id="2bfa9-113">4.8</span></span>|
|<span data-ttu-id="2bfa9-114">类型</span><span class="sxs-lookup"><span data-stu-id="2bfa9-114">Type</span></span>|<span data-ttu-id="2bfa9-115">运行时</span><span class="sxs-lookup"><span data-stu-id="2bfa9-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2bfa9-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="2bfa9-116">Affected APIs</span></span>

-<xref:System.Web.HttpRequest.Form?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.Files?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
