---
ms.openlocfilehash: 08a9292c5a41e7b9b7c1bcc18ec96460de19863f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621046"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a><span data-ttu-id="cf995-101">存在 Unicode 时支持特殊的相对 URI 表示法</span><span class="sxs-lookup"><span data-stu-id="cf995-101">Support special relative URI notation when Unicode is present</span></span>

#### <a name="details"></a><span data-ttu-id="cf995-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="cf995-102">Details</span></span>

<span data-ttu-id="cf995-103">如果在包含 Unicode 的某些相对 URI 上调用 <xref:System.Uri.TryCreate%2A>，则 <xref:System.Uri> 将不再引发 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="cf995-103"><xref:System.Uri> will no longer throw a <xref:System.NullReferenceException> when calling <xref:System.Uri.TryCreate%2A> on certain relative URIs containing Unicode.</span></span> <span data-ttu-id="cf995-104">下面是重现 <xref:System.NullReferenceException> 最简单的做法，其中两个语句是等效的：</span><span class="sxs-lookup"><span data-stu-id="cf995-104">The simplest reproduction of the <xref:System.NullReferenceException> is below, with the two statements being equivalent:</span></span><pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre><span data-ttu-id="cf995-105">若要重现 <xref:System.NullReferenceException>，以下各项必须为 true：</span><span class="sxs-lookup"><span data-stu-id="cf995-105">To reproduce the <xref:System.NullReferenceException>, the following items must be true:</span></span><ul><li><span data-ttu-id="cf995-106">必须将 URI 指定为相对，方法是在其前追加“http:”，且其后不跟“//”。</span><span class="sxs-lookup"><span data-stu-id="cf995-106">The URI must be specified as relative by prepending it with ‘http:’ and not following it with ‘//’.</span></span></li><li><span data-ttu-id="cf995-107">URI 必须包含百分比编码的 Unicode 或未保留的符号。</span><span class="sxs-lookup"><span data-stu-id="cf995-107">The URI must contain percent-encoded Unicode or unreserved symbols.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="cf995-108">建议</span><span class="sxs-lookup"><span data-stu-id="cf995-108">Suggestion</span></span>

<span data-ttu-id="cf995-109">根据此行为禁用相对 URI 的用户应在创建 URI 时转而指定 <xref:System.UriKind.Absolute?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="cf995-109">Users depending on this behavior to disallow relative URIs should instead specify <xref:System.UriKind.Absolute?displayProperty=nameWithType> when creating a URI.</span></span>

| <span data-ttu-id="cf995-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="cf995-110">Name</span></span>    | <span data-ttu-id="cf995-111">“值”</span><span class="sxs-lookup"><span data-stu-id="cf995-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cf995-112">范围</span><span class="sxs-lookup"><span data-stu-id="cf995-112">Scope</span></span>   |<span data-ttu-id="cf995-113">边缘</span><span class="sxs-lookup"><span data-stu-id="cf995-113">Edge</span></span>|
|<span data-ttu-id="cf995-114">Version</span><span class="sxs-lookup"><span data-stu-id="cf995-114">Version</span></span>|<span data-ttu-id="cf995-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="cf995-115">4.7.2</span></span>|
|<span data-ttu-id="cf995-116">类型</span><span class="sxs-lookup"><span data-stu-id="cf995-116">Type</span></span>|<span data-ttu-id="cf995-117">运行时</span><span class="sxs-lookup"><span data-stu-id="cf995-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cf995-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="cf995-118">Affected APIs</span></span>

-<xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
