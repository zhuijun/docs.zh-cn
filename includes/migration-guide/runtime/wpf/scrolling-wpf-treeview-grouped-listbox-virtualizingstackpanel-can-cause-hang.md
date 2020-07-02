---
ms.openlocfilehash: 1be68c2968d0eaa9024007bcf37abf9e44c36f1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621943"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a><span data-ttu-id="9f788-101">在 VirtualizingStackPanel 中滚动 WPF TreeView 或分组的 ListBox 可能导致暂停</span><span class="sxs-lookup"><span data-stu-id="9f788-101">Scrolling a WPF TreeView or grouped ListBox in a VirtualizingStackPanel can cause a hang</span></span>

#### <a name="details"></a><span data-ttu-id="9f788-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="9f788-102">Details</span></span>

<span data-ttu-id="9f788-103">在 .NET Framework v4.5 中，如果视区中存在边距（例如在 <xref:System.Windows.Controls.TreeView?displayProperty=fullName> 的项目之间或在 ItemsPresenter 元素上），则在虚拟化堆叠面板中滚动 WPF <xref:System.Windows.Controls.TreeView?displayProperty=fullName> 可能会导致暂停。</span><span class="sxs-lookup"><span data-stu-id="9f788-103">In the .NET Framework v4.5, scrolling a WPF <xref:System.Windows.Controls.TreeView?displayProperty=fullName> in a virtualized stack panel can cause hangs if there are margins in the viewport (between the items in the <xref:System.Windows.Controls.TreeView?displayProperty=fullName>, for example, or on an ItemsPresenter element).</span></span> <span data-ttu-id="9f788-104">此外，在某些情况下，即使没有边距，视图中不同大小的项目也可能会导致不稳定性。</span><span class="sxs-lookup"><span data-stu-id="9f788-104">Additionally, in some cases, different sized items in the view can cause instability even if there are no margins.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9f788-105">建议</span><span class="sxs-lookup"><span data-stu-id="9f788-105">Suggestion</span></span>

<span data-ttu-id="9f788-106">升级到 .NET Framework 4.5.1 可避免此 bug 出现。</span><span class="sxs-lookup"><span data-stu-id="9f788-106">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="9f788-107">或者，如果包含的所有项目大小相同，可从虚拟化堆叠面板的视图集合（例如 <xref:System.Windows.Controls.TreeView?displayProperty=fullName>）中删除边距。</span><span class="sxs-lookup"><span data-stu-id="9f788-107">Alternatively, margins can be removed from view collections (like <xref:System.Windows.Controls.TreeView?displayProperty=fullName>s) within virtualized stack panels if all contained items are the same size.</span></span>

| <span data-ttu-id="9f788-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="9f788-108">Name</span></span>    | <span data-ttu-id="9f788-109">“值”</span><span class="sxs-lookup"><span data-stu-id="9f788-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9f788-110">范围</span><span class="sxs-lookup"><span data-stu-id="9f788-110">Scope</span></span>   |<span data-ttu-id="9f788-111">主要</span><span class="sxs-lookup"><span data-stu-id="9f788-111">Major</span></span>|
|<span data-ttu-id="9f788-112">Version</span><span class="sxs-lookup"><span data-stu-id="9f788-112">Version</span></span>|<span data-ttu-id="9f788-113">4.5</span><span class="sxs-lookup"><span data-stu-id="9f788-113">4.5</span></span>|
|<span data-ttu-id="9f788-114">类型</span><span class="sxs-lookup"><span data-stu-id="9f788-114">Type</span></span>|<span data-ttu-id="9f788-115">运行时</span><span class="sxs-lookup"><span data-stu-id="9f788-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9f788-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="9f788-116">Affected APIs</span></span>

-<xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|
