---
ms.openlocfilehash: 8dc1b4d94d01813a8124d1340b50fa78a9b157f8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496099"
---
### <a name="resizing-a-grid-can-hang"></a><span data-ttu-id="e22e4-101">调整网格可能会挂起</span><span class="sxs-lookup"><span data-stu-id="e22e4-101">Resizing a Grid can hang</span></span>

#### <a name="details"></a><span data-ttu-id="e22e4-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="e22e4-102">Details</span></span>

<span data-ttu-id="e22e4-103">出现以下情况时，在 <code>T:System.Windows.Controls.Grid</code> 布局期间可能会发生无限循环：</span><span class="sxs-lookup"><span data-stu-id="e22e4-103">An infinite loop can occur during layout of a <code>T:System.Windows.Controls.Grid</code> under the following circumstances:</span></span><ul><li><span data-ttu-id="e22e4-104">行定义包含两个 \*-行，各声明一个 MinHeight 和一个 MaxHeight。</span><span class="sxs-lookup"><span data-stu-id="e22e4-104">Row definitions contain two \*-rows, both declaring a MinHeight and a MaxHeight.</span></span></li><li><span data-ttu-id="e22e4-105">\*-行的内容不超过相应的 MaxHeight</span><span class="sxs-lookup"><span data-stu-id="e22e4-105">Content of the \*-rows doesn't exceed the corresponding MaxHeight</span></span></li><li><span data-ttu-id="e22e4-106">第一个 MinHeight（加上其他任何固定行或自动行）超过了网格的可用高度</span><span class="sxs-lookup"><span data-stu-id="e22e4-106">The Grid's available height is exceeded by the first MinHeight (plus any other fixed or Auto rows)</span></span></li><li><span data-ttu-id="e22e4-107">此应用面向 .NET Framework 4.7，或通过设置 <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code> 选择启用 4.7 分配算法</span><span class="sxs-lookup"><span data-stu-id="e22e4-107">The app targets .NET Framework 4.7, or opts in to the 4.7 allocation algorithm by setting <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code></span></span></li></ul><span data-ttu-id="e22e4-108">在超过两行时或在列出现类似情况时，也可能发生该循环。</span><span class="sxs-lookup"><span data-stu-id="e22e4-108">The loop would also happen with more than two rows, or in the analogous case for columns.</span></span> <span data-ttu-id="e22e4-109">此问题已在 .NET Framework 4.7.1 中解决。</span><span class="sxs-lookup"><span data-stu-id="e22e4-109">The issue is fixed in .NET Framework 4.7.1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e22e4-110">建议</span><span class="sxs-lookup"><span data-stu-id="e22e4-110">Suggestion</span></span>

<span data-ttu-id="e22e4-111">升级到 .NET Framework 4.7.1。</span><span class="sxs-lookup"><span data-stu-id="e22e4-111">Upgrade to .NET Framework 4.7.1.</span></span>  <span data-ttu-id="e22e4-112">或者，如果不需要 4.7 分配算法，也可以使用以下配置设置：</span><span class="sxs-lookup"><span data-stu-id="e22e4-112">Alternatively, if you don't need the 4.7 allocation algorithm you can use the following configuration setting:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="e22e4-113">名称</span><span class="sxs-lookup"><span data-stu-id="e22e4-113">Name</span></span>    | <span data-ttu-id="e22e4-114">值</span><span class="sxs-lookup"><span data-stu-id="e22e4-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e22e4-115">范围</span><span class="sxs-lookup"><span data-stu-id="e22e4-115">Scope</span></span>   |<span data-ttu-id="e22e4-116">边缘</span><span class="sxs-lookup"><span data-stu-id="e22e4-116">Edge</span></span>|
|<span data-ttu-id="e22e4-117">Version</span><span class="sxs-lookup"><span data-stu-id="e22e4-117">Version</span></span>|<span data-ttu-id="e22e4-118">4.7</span><span class="sxs-lookup"><span data-stu-id="e22e4-118">4.7</span></span>|
|<span data-ttu-id="e22e4-119">类型</span><span class="sxs-lookup"><span data-stu-id="e22e4-119">Type</span></span>|<span data-ttu-id="e22e4-120">运行时</span><span class="sxs-lookup"><span data-stu-id="e22e4-120">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="e22e4-121">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="e22e4-121">Affected APIs</span></span>

<span data-ttu-id="e22e4-122">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="e22e4-122">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
