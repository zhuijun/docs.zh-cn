---
ms.openlocfilehash: 00ffc782c9a15c0d88f797f52372b4658706b350
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619881"
---
### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a><span data-ttu-id="70c1a-101">从 .NET Framework 4.5 开始，GlyphRun.ComputeInkBoundingBox() 和 FormattedText.Extent 返回不同的值</span><span class="sxs-lookup"><span data-stu-id="70c1a-101">GlyphRun.ComputeInkBoundingBox() and FormattedText.Extent return different values beginning in .NET Framework 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="70c1a-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="70c1a-102">Details</span></span>

<span data-ttu-id="70c1a-103">.NET Framework 4.5 改进了 <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> 和 <xref:System.Windows.Media.FormattedText.Extent>，以解决在 .NET Framework 4.0 中，框在某些情况下因过小而无法包含字形的问题。</span><span class="sxs-lookup"><span data-stu-id="70c1a-103">Improvements were made to <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> and <xref:System.Windows.Media.FormattedText.Extent> in the .NET Framework 4.5 to address issues where the boxes were too small for the contained glyphs in some cases in the .NET Framework 4.0.</span></span> <span data-ttu-id="70c1a-104">因此，从 .NET Framework 4.5 开始，某些范围框将更大，从而使 UI 布局产生细微差异。</span><span class="sxs-lookup"><span data-stu-id="70c1a-104">As a result of this, some bounding boxes will be larger beginning in the .NET Framework 4.5, resulting in subtle differences in UI layout.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="70c1a-105">建议</span><span class="sxs-lookup"><span data-stu-id="70c1a-105">Suggestion</span></span>

<span data-ttu-id="70c1a-106">请注意，某些字形范围框大小已增加。</span><span class="sxs-lookup"><span data-stu-id="70c1a-106">Be aware that some glyph bounding box sizes have increased.</span></span> <span data-ttu-id="70c1a-107">这些更改通常会改进展示和点击框测试，但如果需要使用旧（.NET 4.5 之前的）行为，可通过以下条目添加到 app.config 文件进行选择：</span><span class="sxs-lookup"><span data-stu-id="70c1a-107">These changes will usually improve presentation and hit box testing, but if the older (pre-.NET 4.5) behavior is desired, it can be opted into by adding the following entry to the app.config file:</span></span><pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="70c1a-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="70c1a-108">Name</span></span>    | <span data-ttu-id="70c1a-109">“值”</span><span class="sxs-lookup"><span data-stu-id="70c1a-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="70c1a-110">范围</span><span class="sxs-lookup"><span data-stu-id="70c1a-110">Scope</span></span>   |<span data-ttu-id="70c1a-111">边缘</span><span class="sxs-lookup"><span data-stu-id="70c1a-111">Edge</span></span>|
|<span data-ttu-id="70c1a-112">Version</span><span class="sxs-lookup"><span data-stu-id="70c1a-112">Version</span></span>|<span data-ttu-id="70c1a-113">4.5</span><span class="sxs-lookup"><span data-stu-id="70c1a-113">4.5</span></span>|
|<span data-ttu-id="70c1a-114">类型</span><span class="sxs-lookup"><span data-stu-id="70c1a-114">Type</span></span>|<span data-ttu-id="70c1a-115">运行时</span><span class="sxs-lookup"><span data-stu-id="70c1a-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="70c1a-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="70c1a-116">Affected APIs</span></span>

-<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType></li><li><xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType></li></ul>|
