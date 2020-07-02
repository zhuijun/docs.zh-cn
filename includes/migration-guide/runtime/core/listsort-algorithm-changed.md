---
ms.openlocfilehash: 9dada93c3330331064b7a944d97d61edb4dea299
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619838"
---
### <a name="listsort-algorithm-changed"></a><span data-ttu-id="25549-101">List.Sort 算法已更改</span><span class="sxs-lookup"><span data-stu-id="25549-101">List.Sort algorithm changed</span></span>

#### <a name="details"></a><span data-ttu-id="25549-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="25549-102">Details</span></span>

<span data-ttu-id="25549-103">从 .NET Framework 4.5 开始，<xref:System.Collections.Generic.List%601?displayProperty=fullName> 的排序算法就已更改（为内省排序而不是快速排序）。</span><span class="sxs-lookup"><span data-stu-id="25549-103">Beginning in .NET Framework 4.5, <xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort algorithm has changed (to be an introspective sort instead of a quick sort).</span></span> <span data-ttu-id="25549-104"><xref:System.Collections.Generic.List%601?displayProperty=fullName> 的排序一直都不稳定，但此更改可能会导致各种方案以不稳定的方式进行排序。</span><span class="sxs-lookup"><span data-stu-id="25549-104"><xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort has never been stable, but this change may cause different scenarios to sort in unstable ways.</span></span> <span data-ttu-id="25549-105">这仅仅意味着等效项目可能会在随后的 API 调用中按不同顺序排序。</span><span class="sxs-lookup"><span data-stu-id="25549-105">That simply means that equivalent items may sort in different orders in subsequent calls of the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="25549-106">建议</span><span class="sxs-lookup"><span data-stu-id="25549-106">Suggestion</span></span>

<span data-ttu-id="25549-107">由于旧的排序算法也不稳定（尽管方式略有不同），因此应该没有代码依赖于始终按特定顺序排序的等效项。</span><span class="sxs-lookup"><span data-stu-id="25549-107">Because the old sort algorithm was also unstable (though in slightly different ways), there should be no code that depends on equivalent items always sorting in a particular order.</span></span> <span data-ttu-id="25549-108">如果有代码实例依赖于此等效项，并且可以幸运地使用旧行为，则此代码应更新为使用按照所需顺序对项进行确定性排序的比较器。</span><span class="sxs-lookup"><span data-stu-id="25549-108">If there are instances of code depending upon that and being lucky with the old behavior, that code should be updated to use a comparer that will deterministically sort the items in the desired order.</span></span>

| <span data-ttu-id="25549-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="25549-109">Name</span></span>    | <span data-ttu-id="25549-110">“值”</span><span class="sxs-lookup"><span data-stu-id="25549-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="25549-111">范围</span><span class="sxs-lookup"><span data-stu-id="25549-111">Scope</span></span>   |<span data-ttu-id="25549-112">透明</span><span class="sxs-lookup"><span data-stu-id="25549-112">Transparent</span></span>|
|<span data-ttu-id="25549-113">Version</span><span class="sxs-lookup"><span data-stu-id="25549-113">Version</span></span>|<span data-ttu-id="25549-114">4.5</span><span class="sxs-lookup"><span data-stu-id="25549-114">4.5</span></span>|
|<span data-ttu-id="25549-115">类型</span><span class="sxs-lookup"><span data-stu-id="25549-115">Type</span></span>|<span data-ttu-id="25549-116">运行时</span><span class="sxs-lookup"><span data-stu-id="25549-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="25549-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="25549-117">Affected APIs</span></span>

-<xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li></ul>|
