---
ms.openlocfilehash: 9d960774161fc44810f90ca30f56eb98f98de3ff
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497419"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a><span data-ttu-id="90978-101">WPF 文本框默认撤消限制是 100</span><span class="sxs-lookup"><span data-stu-id="90978-101">WPF TextBox defaults to undo limit of 100</span></span>

#### <a name="details"></a><span data-ttu-id="90978-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="90978-102">Details</span></span>

<span data-ttu-id="90978-103">在 .NET Framework 4.5 中，WPF 文本框的默认撤消限制是 100（.NET Framework 4.0 则没有限制）</span><span class="sxs-lookup"><span data-stu-id="90978-103">In .NET Framework 4.5, the default undo limit for a WPF textbox is 100 (as opposed to being unlimited in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="90978-104">建议</span><span class="sxs-lookup"><span data-stu-id="90978-104">Suggestion</span></span>

<span data-ttu-id="90978-105">如果 100 的撤消限制过低，可使用 <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit> 显式设置该限制</span><span class="sxs-lookup"><span data-stu-id="90978-105">If an undo limit of 100 is too low, the limit can be set explicitly with <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span></span>

| <span data-ttu-id="90978-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="90978-106">Name</span></span>    | <span data-ttu-id="90978-107">“值”</span><span class="sxs-lookup"><span data-stu-id="90978-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="90978-108">范围</span><span class="sxs-lookup"><span data-stu-id="90978-108">Scope</span></span>   |<span data-ttu-id="90978-109">边缘</span><span class="sxs-lookup"><span data-stu-id="90978-109">Edge</span></span>|
|<span data-ttu-id="90978-110">Version</span><span class="sxs-lookup"><span data-stu-id="90978-110">Version</span></span>|<span data-ttu-id="90978-111">4.5</span><span class="sxs-lookup"><span data-stu-id="90978-111">4.5</span></span>|
|<span data-ttu-id="90978-112">类型</span><span class="sxs-lookup"><span data-stu-id="90978-112">Type</span></span>|<span data-ttu-id="90978-113">运行时</span><span class="sxs-lookup"><span data-stu-id="90978-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="90978-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="90978-114">Affected APIs</span></span>

- <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.TextBox`

-->
