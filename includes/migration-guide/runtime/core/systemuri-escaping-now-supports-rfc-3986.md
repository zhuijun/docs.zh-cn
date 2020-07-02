---
ms.openlocfilehash: 1d7dc808d5b514acc582675d6ccdbd5778314624
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619841"
---
### <a name="systemuri-escaping-now-supports-rfc-3986"></a><span data-ttu-id="ec237-101">System.Uri 转义现在支持 RFC 3986</span><span class="sxs-lookup"><span data-stu-id="ec237-101">System.Uri escaping now supports RFC 3986</span></span>

#### <a name="details"></a><span data-ttu-id="ec237-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="ec237-102">Details</span></span>

<span data-ttu-id="ec237-103">.NET Framework 4.5 中对 URI 转义做了更改，可支持 [RFC 3986](https://tools.ietf.org/html/rfc3986)。</span><span class="sxs-lookup"><span data-stu-id="ec237-103">URI escaping has changed in .NET Framework 4.5 to support [RFC 3986](https://tools.ietf.org/html/rfc3986).</span></span> <span data-ttu-id="ec237-104">具体更改包括：</span><span class="sxs-lookup"><span data-stu-id="ec237-104">Specific changes include:</span></span><ul><li><span data-ttu-id="ec237-105"><xref:System.Uri.EscapeDataString(System.String)?displayProperty=fullName> 根据 RFC 3986 转义保留字符。</span><span class="sxs-lookup"><span data-stu-id="ec237-105"><xref:System.Uri.EscapeDataString(System.String)?displayProperty=fullName> escapes reserved characters based on RFC 3986.</span></span></li><li><span data-ttu-id="ec237-106"><xref:System.Uri.EscapeUriString(System.String)?displayProperty=fullName> 未转义保留字符。</span><span class="sxs-lookup"><span data-stu-id="ec237-106"><xref:System.Uri.EscapeUriString(System.String)?displayProperty=fullName> does not escape reserved characters.</span></span></li><li><span data-ttu-id="ec237-107">如果 <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> 遇到无效的转义序列，则它不会引发异常。</span><span class="sxs-lookup"><span data-stu-id="ec237-107"><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> does not throw an exception if it encounters an invalid escape sequence.</span></span></li><li><span data-ttu-id="ec237-108">未保留的转义字符已取消转义。</span><span class="sxs-lookup"><span data-stu-id="ec237-108">Unreserved escaped characters are un-escaped.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="ec237-109">建议</span><span class="sxs-lookup"><span data-stu-id="ec237-109">Suggestion</span></span>

<ul><li><span data-ttu-id="ec237-110">更新应用程序，以便在出现无效转义序列时不依赖于要引发 <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="ec237-110">Update applications to not rely on <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> to throw in the case of an invalid escape sequence.</span></span> <span data-ttu-id="ec237-111">此类序列现在必须直接进行检测。</span><span class="sxs-lookup"><span data-stu-id="ec237-111">Such sequences must be detected directly now.</span></span></li><li><span data-ttu-id="ec237-112">同样，预计转义和非转义 URI 和数据字符串在 .NET Framework 4.0 和 .NET Framework 4.5 中可能会有所不同，并且这些字符串不应直接在各种 .NET 版本中进行比较。</span><span class="sxs-lookup"><span data-stu-id="ec237-112">Similarly, expect that Escaped and Unescaped URI and Data strings may vary from .NET Framework 4.0 and .NET Framework 4.5 and should not be compared across .NET versions directly.</span></span> <span data-ttu-id="ec237-113">而在对这些字符串进行任何比较前，应在单个 .NET 版本中对其进行分析和规范化。</span><span class="sxs-lookup"><span data-stu-id="ec237-113">Instead, they should be parsed and normalized in a single .NET version before any comparisons are made.</span></span></li></ul>

| <span data-ttu-id="ec237-114">“属性”</span><span class="sxs-lookup"><span data-stu-id="ec237-114">Name</span></span>    | <span data-ttu-id="ec237-115">“值”</span><span class="sxs-lookup"><span data-stu-id="ec237-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ec237-116">范围</span><span class="sxs-lookup"><span data-stu-id="ec237-116">Scope</span></span>   |<span data-ttu-id="ec237-117">次要</span><span class="sxs-lookup"><span data-stu-id="ec237-117">Minor</span></span>|
|<span data-ttu-id="ec237-118">Version</span><span class="sxs-lookup"><span data-stu-id="ec237-118">Version</span></span>|<span data-ttu-id="ec237-119">4.5</span><span class="sxs-lookup"><span data-stu-id="ec237-119">4.5</span></span>|
|<span data-ttu-id="ec237-120">类型</span><span class="sxs-lookup"><span data-stu-id="ec237-120">Type</span></span>|<span data-ttu-id="ec237-121">运行时</span><span class="sxs-lookup"><span data-stu-id="ec237-121">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ec237-122">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="ec237-122">Affected APIs</span></span>

-<xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType></li></ul>|
