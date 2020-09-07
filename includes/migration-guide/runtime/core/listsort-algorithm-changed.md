---
ms.openlocfilehash: 09bd2c6312493f8b6369d05d8f1c4e88e4c05ece
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496484"
---
### <a name="listsort-algorithm-changed"></a><span data-ttu-id="af8aa-101">List.Sort 算法已更改</span><span class="sxs-lookup"><span data-stu-id="af8aa-101">List.Sort algorithm changed</span></span>

#### <a name="details"></a><span data-ttu-id="af8aa-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="af8aa-102">Details</span></span>

<span data-ttu-id="af8aa-103">从 .NET Framework 4.5 开始，<xref:System.Collections.Generic.List%601?displayProperty=fullName> 的排序算法就已更改（为内省排序而不是快速排序）。</span><span class="sxs-lookup"><span data-stu-id="af8aa-103">Beginning in .NET Framework 4.5, <xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort algorithm has changed (to be an introspective sort instead of a quick sort).</span></span> <span data-ttu-id="af8aa-104"><xref:System.Collections.Generic.List%601?displayProperty=fullName> 的排序一直都不稳定，但此更改可能会导致各种方案以不稳定的方式进行排序。</span><span class="sxs-lookup"><span data-stu-id="af8aa-104"><xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort has never been stable, but this change may cause different scenarios to sort in unstable ways.</span></span> <span data-ttu-id="af8aa-105">这仅仅意味着等效项目可能会在随后的 API 调用中按不同顺序排序。</span><span class="sxs-lookup"><span data-stu-id="af8aa-105">That simply means that equivalent items may sort in different orders in subsequent calls of the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="af8aa-106">建议</span><span class="sxs-lookup"><span data-stu-id="af8aa-106">Suggestion</span></span>

<span data-ttu-id="af8aa-107">由于旧的排序算法也不稳定（尽管方式略有不同），因此应该没有代码依赖于始终按特定顺序排序的等效项。</span><span class="sxs-lookup"><span data-stu-id="af8aa-107">Because the old sort algorithm was also unstable (though in slightly different ways), there should be no code that depends on equivalent items always sorting in a particular order.</span></span> <span data-ttu-id="af8aa-108">如果有代码实例依赖于此等效项，并且可以幸运地使用旧行为，则此代码应更新为使用按照所需顺序对项进行确定性排序的比较器。</span><span class="sxs-lookup"><span data-stu-id="af8aa-108">If there are instances of code depending upon that and being lucky with the old behavior, that code should be updated to use a comparer that will deterministically sort the items in the desired order.</span></span>

| <span data-ttu-id="af8aa-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="af8aa-109">Name</span></span>    | <span data-ttu-id="af8aa-110">“值”</span><span class="sxs-lookup"><span data-stu-id="af8aa-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="af8aa-111">范围</span><span class="sxs-lookup"><span data-stu-id="af8aa-111">Scope</span></span>   |<span data-ttu-id="af8aa-112">透明</span><span class="sxs-lookup"><span data-stu-id="af8aa-112">Transparent</span></span>|
|<span data-ttu-id="af8aa-113">Version</span><span class="sxs-lookup"><span data-stu-id="af8aa-113">Version</span></span>|<span data-ttu-id="af8aa-114">4.5</span><span class="sxs-lookup"><span data-stu-id="af8aa-114">4.5</span></span>|
|<span data-ttu-id="af8aa-115">类型</span><span class="sxs-lookup"><span data-stu-id="af8aa-115">Type</span></span>|<span data-ttu-id="af8aa-116">运行时</span><span class="sxs-lookup"><span data-stu-id="af8aa-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="af8aa-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="af8aa-117">Affected APIs</span></span>

- <xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Generic.List`1.Sort``
- ``M:System.Collections.Generic.List`1.Sort(System.Collections.Generic.IComparer{`0})``
- ``M:System.Collections.Generic.List`1.Sort(System.Comparison{`0})``
- ``M:System.Collections.Generic.List`1.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{`0})``

-->
