---
ms.openlocfilehash: 0d38e2177377e7e9ea911071eb65aa13aa1f5900
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496167"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a><span data-ttu-id="1ab43-101">.NET Framework 4.7.2 中默认启用 "dataAnnotations:dataTypeAttribute:disableRegEx" 应用设置</span><span class="sxs-lookup"><span data-stu-id="1ab43-101">"dataAnnotations:dataTypeAttribute:disableRegEx" app setting is on by default in .NET Framework 4.7.2</span></span>

#### <a name="details"></a><span data-ttu-id="1ab43-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="1ab43-102">Details</span></span>

<span data-ttu-id="1ab43-103">.NET Framework 4.6.1 中引入了应用设置 (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>)，允许用户在数据类型属性（如 <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>、<xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType> 和 <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>）中禁用正则表达式。</span><span class="sxs-lookup"><span data-stu-id="1ab43-103">In .NET Framework 4.6.1, an app setting (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) was introduced that allows users to disable the use of regular expressions in data type attributes (such as <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType>, and <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="1ab43-104">这有助于减少安全漏洞，如可避免使用特定正则表达式进行拒绝服务攻击的可能性。</span><span class="sxs-lookup"><span data-stu-id="1ab43-104">This helps to reduce security vulnerability such as avoiding the possibility of a Denial of Service attack using specific regular expressions.</span></span><br/><span data-ttu-id="1ab43-105">在 .NET Framework 4.6.1 中，禁用 RegEx 使用这项应用设置默认设置为 <code>false</code>。</span><span class="sxs-lookup"><span data-stu-id="1ab43-105">In .NET Framework 4.6.1, this app setting to disable RegEx usage was set to <code>false</code> by default.</span></span> <span data-ttu-id="1ab43-106">从 .NET Framework 4.7.2 开始，此配置开关默认设置为 <code>true</code>，以进一步减少面向 .NET Framework 4.7.2 及更高版本的 Web 应用程序的安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="1ab43-106">Starting with .NET Framework 4.7.2, this config switch is set to <code>true</code> by default to further reduce secure vulnerability for web applications that target .NET Framework 4.7.2 and above.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1ab43-107">建议</span><span class="sxs-lookup"><span data-stu-id="1ab43-107">Suggestion</span></span>

<span data-ttu-id="1ab43-108">如果发现升级到 .NET Framework 4.7.2 后 Web 应用程序中的正则表达式不起作用，则可将 <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> 设置的值更新为 <code>false</code>，从而还原到之前的行为。</span><span class="sxs-lookup"><span data-stu-id="1ab43-108">If you find that regular expressions in your web application do not work after upgrading to .NET Framework 4.7.2, you can update the value of the <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> setting to <code>false</code> to revert to the previous behavior.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="1ab43-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="1ab43-109">Name</span></span>    | <span data-ttu-id="1ab43-110">“值”</span><span class="sxs-lookup"><span data-stu-id="1ab43-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1ab43-111">范围</span><span class="sxs-lookup"><span data-stu-id="1ab43-111">Scope</span></span>   |<span data-ttu-id="1ab43-112">次要</span><span class="sxs-lookup"><span data-stu-id="1ab43-112">Minor</span></span>|
|<span data-ttu-id="1ab43-113">版本</span><span class="sxs-lookup"><span data-stu-id="1ab43-113">Version</span></span>|<span data-ttu-id="1ab43-114">4.7.2</span><span class="sxs-lookup"><span data-stu-id="1ab43-114">4.7.2</span></span>|
|<span data-ttu-id="1ab43-115">类型</span><span class="sxs-lookup"><span data-stu-id="1ab43-115">Type</span></span>|<span data-ttu-id="1ab43-116">运行时</span><span class="sxs-lookup"><span data-stu-id="1ab43-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="1ab43-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="1ab43-117">Affected APIs</span></span>

<span data-ttu-id="1ab43-118">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="1ab43-118">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
