---
ms.openlocfilehash: 7bf5f7e8a49acc2918dd0d68a1c54a5c277091b0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496318"
---
### <a name="chained-popups-with-staysopenfalse"></a><span data-ttu-id="5502a-101">StaysOpen=False 的链接弹出窗口</span><span class="sxs-lookup"><span data-stu-id="5502a-101">Chained Popups with StaysOpen=False</span></span>

#### <a name="details"></a><span data-ttu-id="5502a-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="5502a-102">Details</span></span>

<span data-ttu-id="5502a-103">在弹出窗口外部单击时，StaysOpen=False 的弹出窗口应该关闭。</span><span class="sxs-lookup"><span data-stu-id="5502a-103">A Popup with StaysOpen=False is supposed to close when you click outside the Popup.</span></span> <span data-ttu-id="5502a-104">当链接两个或更多此类弹出窗口时（即一个包含另一个），会出现很多问题，包括：</span><span class="sxs-lookup"><span data-stu-id="5502a-104">When two or more such Popups are chained (i.e. one contains another), there were many problems, including:</span></span><ul><li><span data-ttu-id="5502a-105">打开两个级别，在 P2 外部单击，但却在 P1 内。</span><span class="sxs-lookup"><span data-stu-id="5502a-105">Open two levels, click outside P2 but inside P1.</span></span>  <span data-ttu-id="5502a-106">没有反应。</span><span class="sxs-lookup"><span data-stu-id="5502a-106">Nothing happens.</span></span></li><li><span data-ttu-id="5502a-107">打开两个级别，在 P1 外部单击。</span><span class="sxs-lookup"><span data-stu-id="5502a-107">Open two levels, click outside P1.</span></span>  <span data-ttu-id="5502a-108">两个弹出窗口关闭。</span><span class="sxs-lookup"><span data-stu-id="5502a-108">Both popups close.</span></span></li><li><span data-ttu-id="5502a-109">打开和关闭两个级别。</span><span class="sxs-lookup"><span data-stu-id="5502a-109">Open and close two levels.</span></span>  <span data-ttu-id="5502a-110">然后尝试再次打开 P2。</span><span class="sxs-lookup"><span data-stu-id="5502a-110">Then try to open P2 again.</span></span>  <span data-ttu-id="5502a-111">没有反应。</span><span class="sxs-lookup"><span data-stu-id="5502a-111">Nothing happens.</span></span></li><li><span data-ttu-id="5502a-112">尝试打开三个级别。</span><span class="sxs-lookup"><span data-stu-id="5502a-112">Try to open three levels.</span></span>  <span data-ttu-id="5502a-113">无法打开。</span><span class="sxs-lookup"><span data-stu-id="5502a-113">You can't.</span></span>  <span data-ttu-id="5502a-114">（要么不执行任何操作，要么前两个级别关闭，具体取决于单击的位置。）这些情况（及其他变体情况）现在按预期方式工作。</span><span class="sxs-lookup"><span data-stu-id="5502a-114">(Either nothing happens or the first two levels close, depending on where you click.) These cases (and other variants) now work as expected.</span></span></li></ul>

| <span data-ttu-id="5502a-115">名称</span><span class="sxs-lookup"><span data-stu-id="5502a-115">Name</span></span>    | <span data-ttu-id="5502a-116">值</span><span class="sxs-lookup"><span data-stu-id="5502a-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5502a-117">范围</span><span class="sxs-lookup"><span data-stu-id="5502a-117">Scope</span></span>   |<span data-ttu-id="5502a-118">边缘</span><span class="sxs-lookup"><span data-stu-id="5502a-118">Edge</span></span>|
|<span data-ttu-id="5502a-119">Version</span><span class="sxs-lookup"><span data-stu-id="5502a-119">Version</span></span>|<span data-ttu-id="5502a-120">4.7.1</span><span class="sxs-lookup"><span data-stu-id="5502a-120">4.7.1</span></span>|
|<span data-ttu-id="5502a-121">类型</span><span class="sxs-lookup"><span data-stu-id="5502a-121">Type</span></span>|<span data-ttu-id="5502a-122">运行时</span><span class="sxs-lookup"><span data-stu-id="5502a-122">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="5502a-123">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="5502a-123">Affected APIs</span></span>

- <xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Windows.Controls.Primitives.Popup.StaysOpen`

-->
