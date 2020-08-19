---
ms.openlocfilehash: 950c69199219cca615e403c6515239de8864d35d
ms.sourcegitcommit: d3c09791297f0edc468a4849a5f11ef62e0e90fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/12/2020
ms.locfileid: "88137474"
---
### <a name="complexity-of-linq-orderbyfirstordefault-increased"></a><span data-ttu-id="1e23e-101">增加了 LINQ OrderBy.First{OrDefault} 的复杂度</span><span class="sxs-lookup"><span data-stu-id="1e23e-101">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>

<span data-ttu-id="1e23e-102"><xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 和 <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 的实现已更改，这导致操作复杂度增加。</span><span class="sxs-lookup"><span data-stu-id="1e23e-102">The implementation of <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> and <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> has changed, resulting in increased complexity for the operation.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1e23e-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="1e23e-103">Change description</span></span>

<span data-ttu-id="1e23e-104">在 .NET Core 1.x 至 3.x 中，调用 <xref:System.Linq.Enumerable.OrderBy%2A> 或 <xref:System.Linq.Enumerable.OrderByDescending%2A>（后跟 <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 或 <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})>）需处理 `O(N)` 复杂度。</span><span class="sxs-lookup"><span data-stu-id="1e23e-104">In .NET Core 1.x - 3.x, calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N)` complexity.</span></span> <span data-ttu-id="1e23e-105">由于只需要第一个（或默认）元素，因此要找到它，只需要一次枚举。</span><span class="sxs-lookup"><span data-stu-id="1e23e-105">Since only the first (or default) element is required, only one enumeration is required to find it.</span></span> <span data-ttu-id="1e23e-106">然而，会精确调用 `N` 次提供给 <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 或 <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 的谓词，其中 `N` 是序列的长度。</span><span class="sxs-lookup"><span data-stu-id="1e23e-106">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> is invoked exactly `N` times, where `N` is the length of the sequence.</span></span>

<span data-ttu-id="1e23e-107">在 .NET 5.0 及更高版本中，[进行了一项更改](https://github.com/dotnet/runtime/pull/36643)，以致于调用 <xref:System.Linq.Enumerable.OrderBy%2A> 或 <xref:System.Linq.Enumerable.OrderByDescending%2A>（后跟 <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 或 <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})>）会处理 `O(N log N)` 复杂度，而不是 `O(N)` 复杂度。</span><span class="sxs-lookup"><span data-stu-id="1e23e-107">In .NET 5.0 and later versions, a [change was made](https://github.com/dotnet/runtime/pull/36643) such that calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N log N)` complexity instead of `O(N)` complexity.</span></span> <span data-ttu-id="1e23e-108">但是，可调用提供给 <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 或 <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 的谓词（不超过 `N` 次），这对整体性能来说更为重要。</span><span class="sxs-lookup"><span data-stu-id="1e23e-108">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> may be invoked *less* than `N` times, which is more important for overall performance.</span></span>

> [!NOTE]
> <span data-ttu-id="1e23e-109">这项更改与 .NET Framework 中操作的实现和复杂性相契合。</span><span class="sxs-lookup"><span data-stu-id="1e23e-109">This change matches the implementation and complexity of the operation in .NET Framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1e23e-110">更改原因</span><span class="sxs-lookup"><span data-stu-id="1e23e-110">Reason for change</span></span>

<span data-ttu-id="1e23e-111">减少谓词调用次数的好处大于降低整体复杂度的好处，因此 .NET Core 1.0 中引入的实现已被还原。</span><span class="sxs-lookup"><span data-stu-id="1e23e-111">The benefit of invoking the predicate fewer times outweighs a lower overall complexity, so the implementation that was introduced in .NET Core 1.0 was reverted.</span></span> <span data-ttu-id="1e23e-112">有关详细信息，请参阅[此 dotnet/runtime 问题](https://github.com/dotnet/runtime/issues/31554)。</span><span class="sxs-lookup"><span data-stu-id="1e23e-112">For more information, see [this dotnet/runtime issue](https://github.com/dotnet/runtime/issues/31554).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1e23e-113">引入的版本</span><span class="sxs-lookup"><span data-stu-id="1e23e-113">Version introduced</span></span>

<span data-ttu-id="1e23e-114">5.0</span><span class="sxs-lookup"><span data-stu-id="1e23e-114">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1e23e-115">建议操作</span><span class="sxs-lookup"><span data-stu-id="1e23e-115">Recommended action</span></span>

<span data-ttu-id="1e23e-116">开发人员方面无需执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="1e23e-116">No action is required on the developer's part.</span></span>

#### <a name="category"></a><span data-ttu-id="1e23e-117">类别</span><span class="sxs-lookup"><span data-stu-id="1e23e-117">Category</span></span>

<span data-ttu-id="1e23e-118">Core .NET 库</span><span class="sxs-lookup"><span data-stu-id="1e23e-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1e23e-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="1e23e-119">Affected APIs</span></span>

- <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>
- <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Linq.Enumerable.OrderBy`
- `Overload:System.Linq.Enumerable.OrderByDescending`
- `M:System.Linq.Enumerable.First``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`
- `M:System.Linq.Enumerable.FirstOrDefault``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`

-->
