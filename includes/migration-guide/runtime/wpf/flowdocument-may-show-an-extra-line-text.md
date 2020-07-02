---
ms.openlocfilehash: 0470cefc05fb5da6a6195ee0a96f04feef01fd10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619882"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a><span data-ttu-id="2a076-101">FlowDocument 可能显示额外的文本行</span><span class="sxs-lookup"><span data-stu-id="2a076-101">FlowDocument may show an extra line of text</span></span>

#### <a name="details"></a><span data-ttu-id="2a076-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="2a076-102">Details</span></span>

<span data-ttu-id="2a076-103">在某些情况下，当 <xref:System.Windows.Documents.FlowDocument> 元素在 .NET Framework 4.5 上运行时，可能显示额外的文本行，这是与它在 .NET Framework 4.0 上运行时显示的不同之处。</span><span class="sxs-lookup"><span data-stu-id="2a076-103">In some cases, a <xref:System.Windows.Documents.FlowDocument> element will display an extra line of text when running on the .NET Framework 4.5 compared to how it displayed when run on the .NET Framework 4.0.</span></span> <span data-ttu-id="2a076-104">暂未出现已知的案例显示此更改导致任意文本难以阅读或显示不明，但是它可能导致出现之前 <xref:System.Windows.Documents.FlowDocument> 视图中忽略的文本。</span><span class="sxs-lookup"><span data-stu-id="2a076-104">There are no known cases of the change causing any text to be displayed poorly or illegibly, but it could cause text to appear that previously was omitted from a <xref:System.Windows.Documents.FlowDocument>'s view.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2a076-105">建议</span><span class="sxs-lookup"><span data-stu-id="2a076-105">Suggestion</span></span>

<span data-ttu-id="2a076-106">在某些情况下，减少一个显示元素的 PageHeight 属性可能还原之前显示的行数。</span><span class="sxs-lookup"><span data-stu-id="2a076-106">In some cases, decreasing the display element's PageHeight property by one can restore the previous number of displayed lines.</span></span>

| <span data-ttu-id="2a076-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="2a076-107">Name</span></span>    | <span data-ttu-id="2a076-108">“值”</span><span class="sxs-lookup"><span data-stu-id="2a076-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2a076-109">范围</span><span class="sxs-lookup"><span data-stu-id="2a076-109">Scope</span></span>   |<span data-ttu-id="2a076-110">边缘</span><span class="sxs-lookup"><span data-stu-id="2a076-110">Edge</span></span>|
|<span data-ttu-id="2a076-111">Version</span><span class="sxs-lookup"><span data-stu-id="2a076-111">Version</span></span>|<span data-ttu-id="2a076-112">4.5</span><span class="sxs-lookup"><span data-stu-id="2a076-112">4.5</span></span>|
|<span data-ttu-id="2a076-113">类型</span><span class="sxs-lookup"><span data-stu-id="2a076-113">Type</span></span>|<span data-ttu-id="2a076-114">运行时</span><span class="sxs-lookup"><span data-stu-id="2a076-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2a076-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="2a076-115">Affected APIs</span></span>

-<xref:System.Windows.Documents.FlowDocument.%23ctor></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor></li></ul>|
