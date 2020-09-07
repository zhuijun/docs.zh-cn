---
ms.openlocfilehash: d9e1624bbeb91db63bc284b8eb52643938eb42e5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496992"
---
### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a><span data-ttu-id="f300d-101">从 .NET Framework 4.5 开始，GlyphRun.ComputeInkBoundingBox() 和 FormattedText.Extent 返回不同的值</span><span class="sxs-lookup"><span data-stu-id="f300d-101">GlyphRun.ComputeInkBoundingBox() and FormattedText.Extent return different values beginning in .NET Framework 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="f300d-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="f300d-102">Details</span></span>

<span data-ttu-id="f300d-103">.NET Framework 4.5 改进了 <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> 和 <xref:System.Windows.Media.FormattedText.Extent>，以解决在 .NET Framework 4.0 中，框在某些情况下因过小而无法包含字形的问题。</span><span class="sxs-lookup"><span data-stu-id="f300d-103">Improvements were made to <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> and <xref:System.Windows.Media.FormattedText.Extent> in the .NET Framework 4.5 to address issues where the boxes were too small for the contained glyphs in some cases in the .NET Framework 4.0.</span></span> <span data-ttu-id="f300d-104">因此，从 .NET Framework 4.5 开始，某些范围框将更大，从而使 UI 布局产生细微差异。</span><span class="sxs-lookup"><span data-stu-id="f300d-104">As a result of this, some bounding boxes will be larger beginning in the .NET Framework 4.5, resulting in subtle differences in UI layout.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f300d-105">建议</span><span class="sxs-lookup"><span data-stu-id="f300d-105">Suggestion</span></span>

<span data-ttu-id="f300d-106">请注意，某些字形范围框大小已增加。</span><span class="sxs-lookup"><span data-stu-id="f300d-106">Be aware that some glyph bounding box sizes have increased.</span></span> <span data-ttu-id="f300d-107">这些更改通常会改进展示和点击框测试，但如果需要使用旧（.NET 4.5 之前的）行为，可通过以下条目添加到 app.config 文件进行选择：</span><span class="sxs-lookup"><span data-stu-id="f300d-107">These changes will usually improve presentation and hit box testing, but if the older (pre-.NET 4.5) behavior is desired, it can be opted into by adding the following entry to the app.config file:</span></span><pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="f300d-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="f300d-108">Name</span></span>    | <span data-ttu-id="f300d-109">“值”</span><span class="sxs-lookup"><span data-stu-id="f300d-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f300d-110">范围</span><span class="sxs-lookup"><span data-stu-id="f300d-110">Scope</span></span>   |<span data-ttu-id="f300d-111">边缘</span><span class="sxs-lookup"><span data-stu-id="f300d-111">Edge</span></span>|
|<span data-ttu-id="f300d-112">Version</span><span class="sxs-lookup"><span data-stu-id="f300d-112">Version</span></span>|<span data-ttu-id="f300d-113">4.5</span><span class="sxs-lookup"><span data-stu-id="f300d-113">4.5</span></span>|
|<span data-ttu-id="f300d-114">类型</span><span class="sxs-lookup"><span data-stu-id="f300d-114">Type</span></span>|<span data-ttu-id="f300d-115">运行时</span><span class="sxs-lookup"><span data-stu-id="f300d-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="f300d-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="f300d-116">Affected APIs</span></span>

- <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType>
- <xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Media.GlyphRun.ComputeInkBoundingBox`
- `P:System.Windows.Media.FormattedText.Extent`

-->
