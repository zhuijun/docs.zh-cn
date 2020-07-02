---
ms.openlocfilehash: 171b7a3a962f8259e64b88f1ae893e649b5f24bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621058"
---
### <a name="chained-popups-with-staysopenfalse"></a><span data-ttu-id="dff0d-101">StaysOpen=False 的链接弹出窗口</span><span class="sxs-lookup"><span data-stu-id="dff0d-101">Chained Popups with StaysOpen=False</span></span>

#### <a name="details"></a><span data-ttu-id="dff0d-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="dff0d-102">Details</span></span>

<span data-ttu-id="dff0d-103">在弹出窗口外部单击时，StaysOpen=False 的弹出窗口应该关闭。</span><span class="sxs-lookup"><span data-stu-id="dff0d-103">A Popup with StaysOpen=False is supposed to close when you click outside the Popup.</span></span> <span data-ttu-id="dff0d-104">当链接两个或更多此类弹出窗口时（即一个包含另一个），会出现很多问题，包括：</span><span class="sxs-lookup"><span data-stu-id="dff0d-104">When two or more such Popups are chained (i.e. one contains another), there were many problems, including:</span></span><ul><li><span data-ttu-id="dff0d-105">打开两个级别，在 P2 外部单击，但却在 P1 内。</span><span class="sxs-lookup"><span data-stu-id="dff0d-105">Open two levels, click outside P2 but inside P1.</span></span>  <span data-ttu-id="dff0d-106">没有反应。</span><span class="sxs-lookup"><span data-stu-id="dff0d-106">Nothing happens.</span></span></li><li><span data-ttu-id="dff0d-107">打开两个级别，在 P1 外部单击。</span><span class="sxs-lookup"><span data-stu-id="dff0d-107">Open two levels, click outside P1.</span></span>  <span data-ttu-id="dff0d-108">两个弹出窗口关闭。</span><span class="sxs-lookup"><span data-stu-id="dff0d-108">Both popups close.</span></span></li><li><span data-ttu-id="dff0d-109">打开和关闭两个级别。</span><span class="sxs-lookup"><span data-stu-id="dff0d-109">Open and close two levels.</span></span>  <span data-ttu-id="dff0d-110">然后尝试再次打开 P2。</span><span class="sxs-lookup"><span data-stu-id="dff0d-110">Then try to open P2 again.</span></span>  <span data-ttu-id="dff0d-111">没有反应。</span><span class="sxs-lookup"><span data-stu-id="dff0d-111">Nothing happens.</span></span></li><li><span data-ttu-id="dff0d-112">尝试打开三个级别。</span><span class="sxs-lookup"><span data-stu-id="dff0d-112">Try to open three levels.</span></span>  <span data-ttu-id="dff0d-113">无法打开。</span><span class="sxs-lookup"><span data-stu-id="dff0d-113">You can't.</span></span>  <span data-ttu-id="dff0d-114">（要么不执行任何操作，要么前两个级别关闭，具体取决于单击的位置。）这些情况（及其他变体情况）现在按预期方式工作。</span><span class="sxs-lookup"><span data-stu-id="dff0d-114">(Either nothing happens or the first two levels close, depending on where you click.) These cases (and other variants) now work as expected.</span></span></li></ul>

| <span data-ttu-id="dff0d-115">“属性”</span><span class="sxs-lookup"><span data-stu-id="dff0d-115">Name</span></span>    | <span data-ttu-id="dff0d-116">值</span><span class="sxs-lookup"><span data-stu-id="dff0d-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="dff0d-117">范围</span><span class="sxs-lookup"><span data-stu-id="dff0d-117">Scope</span></span>   |<span data-ttu-id="dff0d-118">边缘</span><span class="sxs-lookup"><span data-stu-id="dff0d-118">Edge</span></span>|
|<span data-ttu-id="dff0d-119">Version</span><span class="sxs-lookup"><span data-stu-id="dff0d-119">Version</span></span>|<span data-ttu-id="dff0d-120">4.7.1</span><span class="sxs-lookup"><span data-stu-id="dff0d-120">4.7.1</span></span>|
|<span data-ttu-id="dff0d-121">类型</span><span class="sxs-lookup"><span data-stu-id="dff0d-121">Type</span></span>|<span data-ttu-id="dff0d-122">运行时</span><span class="sxs-lookup"><span data-stu-id="dff0d-122">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dff0d-123">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="dff0d-123">Affected APIs</span></span>

-<xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
