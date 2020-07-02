---
ms.openlocfilehash: cd59818fe674e10a206725bea8a74c4aceed99b1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619894"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="a17ce-101">WPF 文本框选定文本在文本框处于非活动状态时，将显示其他颜色</span><span class="sxs-lookup"><span data-stu-id="a17ce-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

#### <a name="details"></a><span data-ttu-id="a17ce-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="a17ce-102">Details</span></span>

<span data-ttu-id="a17ce-103">在 .NET Framework 4.5 中，当 WPF 文本框控件处于非活动状态（该控件没有焦点）时，文本框中选定文本所显示的颜色与该控件处于活动状态时所显示的颜色不同。</span><span class="sxs-lookup"><span data-stu-id="a17ce-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a17ce-104">建议</span><span class="sxs-lookup"><span data-stu-id="a17ce-104">Suggestion</span></span>

<span data-ttu-id="a17ce-105">可通过将 <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> 属性设置为 <code>false</code> 来还原以前的 (.NET Framework 4.0) 行为。</span><span class="sxs-lookup"><span data-stu-id="a17ce-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>

| <span data-ttu-id="a17ce-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="a17ce-106">Name</span></span>    | <span data-ttu-id="a17ce-107">“值”</span><span class="sxs-lookup"><span data-stu-id="a17ce-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a17ce-108">范围</span><span class="sxs-lookup"><span data-stu-id="a17ce-108">Scope</span></span>   |<span data-ttu-id="a17ce-109">边缘</span><span class="sxs-lookup"><span data-stu-id="a17ce-109">Edge</span></span>|
|<span data-ttu-id="a17ce-110">Version</span><span class="sxs-lookup"><span data-stu-id="a17ce-110">Version</span></span>|<span data-ttu-id="a17ce-111">4.5</span><span class="sxs-lookup"><span data-stu-id="a17ce-111">4.5</span></span>|
|<span data-ttu-id="a17ce-112">类型</span><span class="sxs-lookup"><span data-stu-id="a17ce-112">Type</span></span>|<span data-ttu-id="a17ce-113">运行时</span><span class="sxs-lookup"><span data-stu-id="a17ce-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a17ce-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="a17ce-114">Affected APIs</span></span>

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
