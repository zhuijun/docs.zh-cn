---
ms.openlocfilehash: 61749f59f9379a6d18bb013b2612a07cb7822b3a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497119"
---
### <a name="new-enum-values-in-wpfs-pagerangeselection"></a><span data-ttu-id="90ac4-101">WPF PageRangeSelection 中的新枚举值</span><span class="sxs-lookup"><span data-stu-id="90ac4-101">New enum values in WPF's PageRangeSelection</span></span>

#### <a name="details"></a><span data-ttu-id="90ac4-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="90ac4-102">Details</span></span>

<span data-ttu-id="90ac4-103">两个新成员（<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> 和 <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>）已添加到 <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> 枚举。</span><span class="sxs-lookup"><span data-stu-id="90ac4-103">Two new members (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> and <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>) have been added to the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> enum.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="90ac4-104">建议</span><span class="sxs-lookup"><span data-stu-id="90ac4-104">Suggestion</span></span>

<span data-ttu-id="90ac4-105">大多数情况下，这些更改不会影响用户代码。</span><span class="sxs-lookup"><span data-stu-id="90ac4-105">In most cases, these changes won't impact user code.</span></span> <span data-ttu-id="90ac4-106">但是，应该修改依赖于对 <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> 类型的 <xref:System.Enum.GetNames(System.Type)> 或 <xref:System.Enum.GetValues(System.Type)> 调用中所存在特定数量元素的代码。</span><span class="sxs-lookup"><span data-stu-id="90ac4-106">Code that depends on a particular number of elements existing in <xref:System.Enum.GetNames(System.Type)> or <xref:System.Enum.GetValues(System.Type)> calls on the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> type should be modified, though.</span></span>

| <span data-ttu-id="90ac4-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="90ac4-107">Name</span></span>    | <span data-ttu-id="90ac4-108">“值”</span><span class="sxs-lookup"><span data-stu-id="90ac4-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="90ac4-109">范围</span><span class="sxs-lookup"><span data-stu-id="90ac4-109">Scope</span></span>   |<span data-ttu-id="90ac4-110">边缘</span><span class="sxs-lookup"><span data-stu-id="90ac4-110">Edge</span></span>|
|<span data-ttu-id="90ac4-111">Version</span><span class="sxs-lookup"><span data-stu-id="90ac4-111">Version</span></span>|<span data-ttu-id="90ac4-112">4.5</span><span class="sxs-lookup"><span data-stu-id="90ac4-112">4.5</span></span>|
|<span data-ttu-id="90ac4-113">类型</span><span class="sxs-lookup"><span data-stu-id="90ac4-113">Type</span></span>|<span data-ttu-id="90ac4-114">运行时</span><span class="sxs-lookup"><span data-stu-id="90ac4-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="90ac4-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="90ac4-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.PageRangeSelection?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.PageRangeSelection`

-->
