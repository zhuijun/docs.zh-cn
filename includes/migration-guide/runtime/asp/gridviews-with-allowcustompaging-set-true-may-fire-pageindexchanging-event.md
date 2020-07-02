---
ms.openlocfilehash: 3b329bf5ba2af4d3ab9c3e203e99daba8ca0d0c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619818"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a><span data-ttu-id="9f278-101">AllowCustomPaging 设为 true 的 GridViews 可能在离开视图最后一页时触发 PageIndexChanging 事件</span><span class="sxs-lookup"><span data-stu-id="9f278-101">GridViews with AllowCustomPaging set to true may fire the PageIndexChanging event when leaving the final page of the view</span></span>

#### <a name="details"></a><span data-ttu-id="9f278-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="9f278-102">Details</span></span>

<span data-ttu-id="9f278-103">.NET Framework 4.5 中的 bug 导致 <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName> 有时在遇到已启用 <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName> 的 <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> 时不会触发。</span><span class="sxs-lookup"><span data-stu-id="9f278-103">A bug in the .NET Framework 4.5 causes <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName> to sometimes not fire for <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName>s that have enabled <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9f278-104">建议</span><span class="sxs-lookup"><span data-stu-id="9f278-104">Suggestion</span></span>

<span data-ttu-id="9f278-105">此问题已在 .NET Framework 4.6 中解决，因此升级到该版本的 .NET Framework 即可解决该问题。</span><span class="sxs-lookup"><span data-stu-id="9f278-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span> <span data-ttu-id="9f278-106">作为解决方法，应用可以对任何满足以下条件的 <code>Page_Load</code> 执行显式 BindGrid（<xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> 在最后一页且 Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> 不同于 <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName>）。</span><span class="sxs-lookup"><span data-stu-id="9f278-106">As a work-around, the app can do an explicit BindGrid on any <code>Page_Load</code> that would hit these conditions (the <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> is on the last page and Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> is different from <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName>).</span></span> <span data-ttu-id="9f278-107">或者，可以将应用修改为允许分页（不是自定义分页），因为该方案不演示此问题。</span><span class="sxs-lookup"><span data-stu-id="9f278-107">Alternatively, the app can be modified to allow paging (instead of custom paging), as that scenario does not demonstrate the problem.</span></span>

| <span data-ttu-id="9f278-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="9f278-108">Name</span></span>    | <span data-ttu-id="9f278-109">“值”</span><span class="sxs-lookup"><span data-stu-id="9f278-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9f278-110">范围</span><span class="sxs-lookup"><span data-stu-id="9f278-110">Scope</span></span>   |<span data-ttu-id="9f278-111">次要</span><span class="sxs-lookup"><span data-stu-id="9f278-111">Minor</span></span>|
|<span data-ttu-id="9f278-112">Version</span><span class="sxs-lookup"><span data-stu-id="9f278-112">Version</span></span>|<span data-ttu-id="9f278-113">4.5</span><span class="sxs-lookup"><span data-stu-id="9f278-113">4.5</span></span>|
|<span data-ttu-id="9f278-114">类型</span><span class="sxs-lookup"><span data-stu-id="9f278-114">Type</span></span>|<span data-ttu-id="9f278-115">运行时</span><span class="sxs-lookup"><span data-stu-id="9f278-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9f278-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="9f278-116">Affected APIs</span></span>

-<xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|
