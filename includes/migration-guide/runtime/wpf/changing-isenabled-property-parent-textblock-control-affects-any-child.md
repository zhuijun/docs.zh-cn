---
ms.openlocfilehash: 12a26030a9a336d887ae9d53994a9daf13356618
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496374"
---
### <a name="changing-the-isenabled-property-of-the-parent-of-a-textblock-control-affects-any-child-controls"></a><span data-ttu-id="28dc1-101">更改 TextBlock 控件父级的 IsEnabled 属性会影响任何子控件</span><span class="sxs-lookup"><span data-stu-id="28dc1-101">Changing the IsEnabled property of the parent of a TextBlock control affects any child controls</span></span>

#### <a name="details"></a><span data-ttu-id="28dc1-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="28dc1-102">Details</span></span>

<span data-ttu-id="28dc1-103">自 .NET Framework 4.6.2 起，更改 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 控件父级的 <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> 属性会影响 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 控件的任意子控件（例如超链接和按钮）。在 .NET Framework 4.6.1 和更早版本中，<xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 中的控件并非始终反映 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 父级的 <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> 属性状态。</span><span class="sxs-lookup"><span data-stu-id="28dc1-103">Starting with the .NET Framework 4.6.2, changing the <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> property of the parent of a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control affects any child controls (such as hyperlinks and buttons) of the <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control.In the .NET Framework 4.6.1 and earlier versions, controls inside a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> did not always reflect the state of the <xref:System.Windows.UIElement.IsEnabled?displayProperty=fullName> property of the <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> parent.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="28dc1-104">建议</span><span class="sxs-lookup"><span data-stu-id="28dc1-104">Suggestion</span></span>

<span data-ttu-id="28dc1-105">无。</span><span class="sxs-lookup"><span data-stu-id="28dc1-105">None.</span></span> <span data-ttu-id="28dc1-106">此更改符合 <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> 控件中各控件的预期行为。</span><span class="sxs-lookup"><span data-stu-id="28dc1-106">This change conforms to the expected behavior for controls inside a <xref:System.Windows.Controls.TextBlock?displayProperty=fullName> control.</span></span>

| <span data-ttu-id="28dc1-107">名称</span><span class="sxs-lookup"><span data-stu-id="28dc1-107">Name</span></span>    | <span data-ttu-id="28dc1-108">值</span><span class="sxs-lookup"><span data-stu-id="28dc1-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="28dc1-109">范围</span><span class="sxs-lookup"><span data-stu-id="28dc1-109">Scope</span></span>   |<span data-ttu-id="28dc1-110">次要</span><span class="sxs-lookup"><span data-stu-id="28dc1-110">Minor</span></span>|
|<span data-ttu-id="28dc1-111">Version</span><span class="sxs-lookup"><span data-stu-id="28dc1-111">Version</span></span>|<span data-ttu-id="28dc1-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="28dc1-112">4.6.2</span></span>|
|<span data-ttu-id="28dc1-113">类型</span><span class="sxs-lookup"><span data-stu-id="28dc1-113">Type</span></span>|<span data-ttu-id="28dc1-114">运行时</span><span class="sxs-lookup"><span data-stu-id="28dc1-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="28dc1-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="28dc1-115">Affected APIs</span></span>

- <xref:System.Windows.UIElement.IsEnabled?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Windows.UIElement.IsEnabled`

-->
