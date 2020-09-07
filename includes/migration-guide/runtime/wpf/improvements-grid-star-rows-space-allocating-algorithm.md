---
ms.openlocfilehash: 415eb1960c20fb662469e126560d6f366309eb0d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496828"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="920f6-101">网格星型行空格分配算法的改进</span><span class="sxs-lookup"><span data-stu-id="920f6-101">Improvements to Grid star-rows space allocating algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="920f6-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="920f6-102">Details</span></span>

<span data-ttu-id="920f6-103">修复了在 .NET Framework 4.7 中引入的 <xref:System.Windows.Controls.Grid> 中[用于分配大小的算法](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)的问题。</span><span class="sxs-lookup"><span data-stu-id="920f6-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="920f6-104">在某些情况下，例如，<code>Height=&quot;Auto&quot;</code> 包含空行的网格，行排列在错误的位置，可能完全在网格之外。</span><span class="sxs-lookup"><span data-stu-id="920f6-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="920f6-105">建议</span><span class="sxs-lookup"><span data-stu-id="920f6-105">Suggestion</span></span>

<span data-ttu-id="920f6-106">为使应用程序从这些更改中获益，它必须在 .NET Framework 4.8 或更高版本上运行。</span><span class="sxs-lookup"><span data-stu-id="920f6-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>

| <span data-ttu-id="920f6-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="920f6-107">Name</span></span>    | <span data-ttu-id="920f6-108">“值”</span><span class="sxs-lookup"><span data-stu-id="920f6-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="920f6-109">范围</span><span class="sxs-lookup"><span data-stu-id="920f6-109">Scope</span></span>   |<span data-ttu-id="920f6-110">主要</span><span class="sxs-lookup"><span data-stu-id="920f6-110">Major</span></span>|
|<span data-ttu-id="920f6-111">Version</span><span class="sxs-lookup"><span data-stu-id="920f6-111">Version</span></span>|<span data-ttu-id="920f6-112">4.8</span><span class="sxs-lookup"><span data-stu-id="920f6-112">4.8</span></span>|
|<span data-ttu-id="920f6-113">类型</span><span class="sxs-lookup"><span data-stu-id="920f6-113">Type</span></span>|<span data-ttu-id="920f6-114">运行时</span><span class="sxs-lookup"><span data-stu-id="920f6-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="920f6-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="920f6-115">Affected APIs</span></span>

<span data-ttu-id="920f6-116">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="920f6-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
