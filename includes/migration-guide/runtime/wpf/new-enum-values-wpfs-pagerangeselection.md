---
ms.openlocfilehash: bae6d7c0f8843211c721c68ce6f16000b35b4401
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619890"
---
### <a name="new-enum-values-in-wpfs-pagerangeselection"></a><span data-ttu-id="46282-101">WPF PageRangeSelection 中的新枚举值</span><span class="sxs-lookup"><span data-stu-id="46282-101">New enum values in WPF's PageRangeSelection</span></span>

#### <a name="details"></a><span data-ttu-id="46282-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="46282-102">Details</span></span>

<span data-ttu-id="46282-103">两个新成员（<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> 和 <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>）已添加到 <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> 枚举。</span><span class="sxs-lookup"><span data-stu-id="46282-103">Two new members (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> and <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>) have been added to the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> enum.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="46282-104">建议</span><span class="sxs-lookup"><span data-stu-id="46282-104">Suggestion</span></span>

<span data-ttu-id="46282-105">大多数情况下，这些更改不会影响用户代码。</span><span class="sxs-lookup"><span data-stu-id="46282-105">In most cases, these changes won't impact user code.</span></span> <span data-ttu-id="46282-106">但是，应该修改依赖于对 <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> 类型的 <xref:System.Enum.GetNames(System.Type)> 或 <xref:System.Enum.GetValues(System.Type)> 调用中所存在特定数量元素的代码。</span><span class="sxs-lookup"><span data-stu-id="46282-106">Code that depends on a particular number of elements existing in <xref:System.Enum.GetNames(System.Type)> or <xref:System.Enum.GetValues(System.Type)> calls on the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> type should be modified, though.</span></span>

| <span data-ttu-id="46282-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="46282-107">Name</span></span>    | <span data-ttu-id="46282-108">“值”</span><span class="sxs-lookup"><span data-stu-id="46282-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="46282-109">范围</span><span class="sxs-lookup"><span data-stu-id="46282-109">Scope</span></span>   |<span data-ttu-id="46282-110">边缘</span><span class="sxs-lookup"><span data-stu-id="46282-110">Edge</span></span>|
|<span data-ttu-id="46282-111">Version</span><span class="sxs-lookup"><span data-stu-id="46282-111">Version</span></span>|<span data-ttu-id="46282-112">4.5</span><span class="sxs-lookup"><span data-stu-id="46282-112">4.5</span></span>|
|<span data-ttu-id="46282-113">类型</span><span class="sxs-lookup"><span data-stu-id="46282-113">Type</span></span>|<span data-ttu-id="46282-114">运行时</span><span class="sxs-lookup"><span data-stu-id="46282-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="46282-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="46282-115">Affected APIs</span></span>

-<xref:System.Windows.Controls.PageRangeSelection?displayProperty=nameWithType></li></ul>|
