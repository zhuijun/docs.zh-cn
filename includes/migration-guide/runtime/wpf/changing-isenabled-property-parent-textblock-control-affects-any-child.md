---
ms.openlocfilehash: 395463225e3c1f1d168dd019ea75966ad54e5a8a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621059"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a><span data-ttu-id="220d5-101">更改 TextBlock 控件父级的 IsEnabled 属性会影响任何子控件</span><span class="sxs-lookup"><span data-stu-id="220d5-101">Changing the IsEnabled property of the parent of a TextBlock control affects any child controls</span></span>

#### <a name="details"></a><span data-ttu-id="220d5-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="220d5-102">Details</span></span>

<span data-ttu-id="220d5-103">自 .NET Framework 4.6.2 起，更改 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 控件父级的 <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> 属性会影响 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 控件的任意子控件（例如超链接和按钮）。在 .NET Framework 4.6.1 和更早版本中，<xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 中的控件并非始终反映 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 父级的 <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> 属性状态。</span><span class="sxs-lookup"><span data-stu-id="220d5-103">Starting with the .NET Framework 4.6.2, changing the <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> property of the parent of a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control affects any child controls (such as hyperlinks and buttons) of the <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control.In the .NET Framework 4.6.1 and earlier versions, controls inside a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> did not always reflect the state of the <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> property of the <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> parent.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="220d5-104">建议</span><span class="sxs-lookup"><span data-stu-id="220d5-104">Suggestion</span></span>

<span data-ttu-id="220d5-105">无。</span><span class="sxs-lookup"><span data-stu-id="220d5-105">None.</span></span> <span data-ttu-id="220d5-106">此更改符合 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 控件中各控件的预期行为。</span><span class="sxs-lookup"><span data-stu-id="220d5-106">This change conforms to the expected behavior for controls inside a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control.</span></span>

| <span data-ttu-id="220d5-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="220d5-107">Name</span></span>    | <span data-ttu-id="220d5-108">值</span><span class="sxs-lookup"><span data-stu-id="220d5-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="220d5-109">范围</span><span class="sxs-lookup"><span data-stu-id="220d5-109">Scope</span></span>   |<span data-ttu-id="220d5-110">次要</span><span class="sxs-lookup"><span data-stu-id="220d5-110">Minor</span></span>|
|<span data-ttu-id="220d5-111">Version</span><span class="sxs-lookup"><span data-stu-id="220d5-111">Version</span></span>|<span data-ttu-id="220d5-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="220d5-112">4.6.2</span></span>|
|<span data-ttu-id="220d5-113">类型</span><span class="sxs-lookup"><span data-stu-id="220d5-113">Type</span></span>|<span data-ttu-id="220d5-114">运行时</span><span class="sxs-lookup"><span data-stu-id="220d5-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="220d5-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="220d5-115">Affected APIs</span></span>

-<xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType></li></ul>|
