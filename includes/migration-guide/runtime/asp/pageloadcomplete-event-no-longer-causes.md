---
ms.openlocfilehash: a84d72813a46d6bb39f4710b35d2c9dc859e30ef
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496310"
---
### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a><span data-ttu-id="efaa7-101">Page.LoadComplete 事件不再导致 System.Web.UI.WebControls.EntityDataSource 控件调用数据绑定</span><span class="sxs-lookup"><span data-stu-id="efaa7-101">Page.LoadComplete event no longer causes System.Web.UI.WebControls.EntityDataSource control to invoke data binding</span></span>

#### <a name="details"></a><span data-ttu-id="efaa7-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="efaa7-102">Details</span></span>

<span data-ttu-id="efaa7-103"><xref:System.Web.UI.Page.LoadComplete> 事件不再导致 <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> 控件针对 create/update/delete 参数的更改来调用数据绑定。</span><span class="sxs-lookup"><span data-stu-id="efaa7-103">The <xref:System.Web.UI.Page.LoadComplete> event no longer causes the <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> control to invoke data binding for changes to create/update/delete parameters.</span></span> <span data-ttu-id="efaa7-104">此更改消除到数据库的外来行程，防止重置控件的值，并生成与其他数据控件一致的行为，例如 <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> 和 <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="efaa7-104">This change eliminates an extraneous trip to the database, prevents the values of controls from being reset, and produces behavior that is consistent with other data controls, such as <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> and <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName>.</span></span> <span data-ttu-id="efaa7-105">在应用程序依赖于在 <xref:System.Web.UI.Page.LoadComplete> 事件中调用数据绑定的极少数情况下，此更改会产生不同的行为。</span><span class="sxs-lookup"><span data-stu-id="efaa7-105">This change produces different behavior in the unlikely event that applications rely on invoking data binding in the <xref:System.Web.UI.Page.LoadComplete> event.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="efaa7-106">建议</span><span class="sxs-lookup"><span data-stu-id="efaa7-106">Suggestion</span></span>

<span data-ttu-id="efaa7-107">如果需要数据绑定，请在回发之前的事件中手动调用数据绑定。</span><span class="sxs-lookup"><span data-stu-id="efaa7-107">If there is a need for databinding, manually invoke databind in an event that is earlier in the post-back.</span></span>

| <span data-ttu-id="efaa7-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="efaa7-108">Name</span></span>    | <span data-ttu-id="efaa7-109">“值”</span><span class="sxs-lookup"><span data-stu-id="efaa7-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="efaa7-110">范围</span><span class="sxs-lookup"><span data-stu-id="efaa7-110">Scope</span></span>   |<span data-ttu-id="efaa7-111">边缘</span><span class="sxs-lookup"><span data-stu-id="efaa7-111">Edge</span></span>|
|<span data-ttu-id="efaa7-112">Version</span><span class="sxs-lookup"><span data-stu-id="efaa7-112">Version</span></span>|<span data-ttu-id="efaa7-113">4.5</span><span class="sxs-lookup"><span data-stu-id="efaa7-113">4.5</span></span>|
|<span data-ttu-id="efaa7-114">类型</span><span class="sxs-lookup"><span data-stu-id="efaa7-114">Type</span></span>|<span data-ttu-id="efaa7-115">运行时</span><span class="sxs-lookup"><span data-stu-id="efaa7-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="efaa7-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="efaa7-116">Affected APIs</span></span>

<span data-ttu-id="efaa7-117">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="efaa7-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
