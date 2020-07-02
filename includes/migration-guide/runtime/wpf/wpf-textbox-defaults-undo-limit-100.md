---
ms.openlocfilehash: 13d3799aeede86b01aa81ce1cd69b3c4c22311ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619898"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a><span data-ttu-id="89ebb-101">WPF 文本框默认撤消限制是 100</span><span class="sxs-lookup"><span data-stu-id="89ebb-101">WPF TextBox defaults to undo limit of 100</span></span>

#### <a name="details"></a><span data-ttu-id="89ebb-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="89ebb-102">Details</span></span>

<span data-ttu-id="89ebb-103">在 .NET Framework 4.5 中，WPF 文本框的默认撤消限制是 100（.NET Framework 4.0 则没有限制）</span><span class="sxs-lookup"><span data-stu-id="89ebb-103">In .NET Framework 4.5, the default undo limit for a WPF textbox is 100 (as opposed to being unlimited in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="89ebb-104">建议</span><span class="sxs-lookup"><span data-stu-id="89ebb-104">Suggestion</span></span>

<span data-ttu-id="89ebb-105">如果 100 的撤消限制过低，可使用 <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit> 显式设置该限制</span><span class="sxs-lookup"><span data-stu-id="89ebb-105">If an undo limit of 100 is too low, the limit can be set explicitly with <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span></span>

| <span data-ttu-id="89ebb-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="89ebb-106">Name</span></span>    | <span data-ttu-id="89ebb-107">“值”</span><span class="sxs-lookup"><span data-stu-id="89ebb-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="89ebb-108">范围</span><span class="sxs-lookup"><span data-stu-id="89ebb-108">Scope</span></span>   |<span data-ttu-id="89ebb-109">边缘</span><span class="sxs-lookup"><span data-stu-id="89ebb-109">Edge</span></span>|
|<span data-ttu-id="89ebb-110">Version</span><span class="sxs-lookup"><span data-stu-id="89ebb-110">Version</span></span>|<span data-ttu-id="89ebb-111">4.5</span><span class="sxs-lookup"><span data-stu-id="89ebb-111">4.5</span></span>|
|<span data-ttu-id="89ebb-112">类型</span><span class="sxs-lookup"><span data-stu-id="89ebb-112">Type</span></span>|<span data-ttu-id="89ebb-113">运行时</span><span class="sxs-lookup"><span data-stu-id="89ebb-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="89ebb-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="89ebb-114">Affected APIs</span></span>

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
