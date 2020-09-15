---
ms.openlocfilehash: 8f03e5166e7f1f598e9bba7fb8c550809f287b82
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615603"
---
### <a name="htmltextwriter-does-not-render-br-element-correctly"></a><span data-ttu-id="845c7-101">HtmlTextWriter 未正确呈现 `<br/>` 元素</span><span class="sxs-lookup"><span data-stu-id="845c7-101">HtmlTextWriter does not render `<br/>` element correctly</span></span>

#### <a name="details"></a><span data-ttu-id="845c7-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="845c7-102">Details</span></span>

<span data-ttu-id="845c7-103">从 .NET Framework 4.6 开始，调用带有 `<BR />` 的 <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> 和 <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> 将正确插入唯一 `<BR />`（而非两个）</span><span class="sxs-lookup"><span data-stu-id="845c7-103">Beginning in the .NET Framework 4.6, calling <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> and <xref:System.Web.UI.HtmlTextWriter.RenderEndTag> with a `<BR />` element will correctly insert only one `<BR />` (instead of two)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="845c7-104">建议</span><span class="sxs-lookup"><span data-stu-id="845c7-104">Suggestion</span></span>

<span data-ttu-id="845c7-105">如果应用依赖于多余的 `<BR />` 标记，应再次调用 <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)>。</span><span class="sxs-lookup"><span data-stu-id="845c7-105">If an app depended on the extra `<BR />` tag, <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)> should be called a second time.</span></span> <span data-ttu-id="845c7-106">请注意，此行为更改仅影响面向 .NET Framework 4.6 或更高版本的应用，因此另一选项是面向以前版本的 .NET Framework 以便获取旧行为。</span><span class="sxs-lookup"><span data-stu-id="845c7-106">Note that this behavior change only affects apps that target the .NET Framework 4.6 or later, so another option is to target a previous version of the .NET Framework in order to get the old behavior.</span></span>

| <span data-ttu-id="845c7-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="845c7-107">Name</span></span>    | <span data-ttu-id="845c7-108">“值”</span><span class="sxs-lookup"><span data-stu-id="845c7-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="845c7-109">范围</span><span class="sxs-lookup"><span data-stu-id="845c7-109">Scope</span></span>   | <span data-ttu-id="845c7-110">边缘</span><span class="sxs-lookup"><span data-stu-id="845c7-110">Edge</span></span>        |
| <span data-ttu-id="845c7-111">Version</span><span class="sxs-lookup"><span data-stu-id="845c7-111">Version</span></span> | <span data-ttu-id="845c7-112">4.6</span><span class="sxs-lookup"><span data-stu-id="845c7-112">4.6</span></span>         |
| <span data-ttu-id="845c7-113">类型</span><span class="sxs-lookup"><span data-stu-id="845c7-113">Type</span></span>    | <span data-ttu-id="845c7-114">重定目标</span><span class="sxs-lookup"><span data-stu-id="845c7-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="845c7-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="845c7-115">Affected APIs</span></span>

- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.String)?displayProperty=nameWithType>
- <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag(System.Web.UI.HtmlTextWriterTag)?displayProperty=nameWithType>
