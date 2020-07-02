---
ms.openlocfilehash: 1be68c2968d0eaa9024007bcf37abf9e44c36f1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621943"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>在 VirtualizingStackPanel 中滚动 WPF TreeView 或分组的 ListBox 可能导致暂停

#### <a name="details"></a>详细信息

在 .NET Framework v4.5 中，如果视区中存在边距（例如在 <xref:System.Windows.Controls.TreeView?displayProperty=fullName> 的项目之间或在 ItemsPresenter 元素上），则在虚拟化堆叠面板中滚动 WPF <xref:System.Windows.Controls.TreeView?displayProperty=fullName> 可能会导致暂停。 此外，在某些情况下，即使没有边距，视图中不同大小的项目也可能会导致不稳定性。

#### <a name="suggestion"></a>建议

升级到 .NET Framework 4.5.1 可避免此 bug 出现。 或者，如果包含的所有项目大小相同，可从虚拟化堆叠面板的视图集合（例如 <xref:System.Windows.Controls.TreeView?displayProperty=fullName>）中删除边距。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |主要|
|Version|4.5|
|类型|运行时

#### <a name="affected-apis"></a>受影响的 API

-<xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|
