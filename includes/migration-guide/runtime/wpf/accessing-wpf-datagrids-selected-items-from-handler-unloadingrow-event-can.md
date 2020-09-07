---
ms.openlocfilehash: 1487e32ffca7b4bbebb5edac7efc8961ac05723b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497541"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="bbcd7-101">从 DataGrid 的 UnloadingRow 事件的处理程序访问 WPF DataGrid 的选定项可能会导致 NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="bbcd7-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

#### <a name="details"></a><span data-ttu-id="bbcd7-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="bbcd7-102">Details</span></span>

<span data-ttu-id="bbcd7-103">由于 .NET Framework 4.5 中的 bug，涉及删除行的 <xref:System.Windows.Controls.DataGrid> 事件的事件处理程序如果访问 <xref:System.Windows.Controls.DataGrid> 的 <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> 或 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> 属性，可能会导致引发 <xref:System.NullReferenceException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="bbcd7-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=fullName> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> properties.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bbcd7-104">建议</span><span class="sxs-lookup"><span data-stu-id="bbcd7-104">Suggestion</span></span>

<span data-ttu-id="bbcd7-105">此问题已在 .NET Framework 4.6 中解决，因此升级到该版本的 .NET Framework 即可解决该问题。</span><span class="sxs-lookup"><span data-stu-id="bbcd7-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="bbcd7-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="bbcd7-106">Name</span></span>    | <span data-ttu-id="bbcd7-107">“值”</span><span class="sxs-lookup"><span data-stu-id="bbcd7-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bbcd7-108">范围</span><span class="sxs-lookup"><span data-stu-id="bbcd7-108">Scope</span></span>   |<span data-ttu-id="bbcd7-109">次要</span><span class="sxs-lookup"><span data-stu-id="bbcd7-109">Minor</span></span>|
|<span data-ttu-id="bbcd7-110">Version</span><span class="sxs-lookup"><span data-stu-id="bbcd7-110">Version</span></span>|<span data-ttu-id="bbcd7-111">4.5</span><span class="sxs-lookup"><span data-stu-id="bbcd7-111">4.5</span></span>|
|<span data-ttu-id="bbcd7-112">类型</span><span class="sxs-lookup"><span data-stu-id="bbcd7-112">Type</span></span>|<span data-ttu-id="bbcd7-113">运行时</span><span class="sxs-lookup"><span data-stu-id="bbcd7-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="bbcd7-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="bbcd7-114">Affected APIs</span></span>

- <xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType>

<!--

#### Affected APIs

- `E:System.Windows.Controls.DataGrid.UnloadingRow`
- `E:System.Windows.Controls.DataGrid.UnloadingRowDetails`

-->
