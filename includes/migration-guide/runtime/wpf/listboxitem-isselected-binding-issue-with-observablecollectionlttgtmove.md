---
ms.openlocfilehash: 196b6a13d32c7767b858d6d68ca775eb49324805
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497374"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a><span data-ttu-id="55836-101">ObservableCollection&lt;T&gt;.Move 的 ListBoxItem IsSelected 绑定问题</span><span class="sxs-lookup"><span data-stu-id="55836-101">ListBoxItem IsSelected binding issue with ObservableCollection&lt;T&gt;.Move</span></span>

#### <a name="details"></a><span data-ttu-id="55836-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="55836-102">Details</span></span>

<span data-ttu-id="55836-103">在绑定到有选中项的 <xref:System.Windows.Controls.ListBox?displayProperty=fullName> 的集合上调用 <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> 或 <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> 可能导致未来选择或不选 <xref:System.Windows.Controls.ListBox?displayProperty=fullName> 项的不稳定行为。</span><span class="sxs-lookup"><span data-stu-id="55836-103">Calling <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> or <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> on a collection bound to a <xref:System.Windows.Controls.ListBox?displayProperty=fullName> with items selected can lead to erratic behavior with future selection or unselection of <xref:System.Windows.Controls.ListBox?displayProperty=fullName> items.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="55836-104">建议</span><span class="sxs-lookup"><span data-stu-id="55836-104">Suggestion</span></span>

<span data-ttu-id="55836-105">调用 <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> 和 <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName>（而不是 <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)>）将解决此问题。</span><span class="sxs-lookup"><span data-stu-id="55836-105">Calling <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> and <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> instead of <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> will work around this issue.</span></span> <span data-ttu-id="55836-106">此外，此问题已在 .NET Framework 4.6 中解决，因此升级到该版本的 .NET Framework 即可解决该问题。</span><span class="sxs-lookup"><span data-stu-id="55836-106">Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="55836-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="55836-107">Name</span></span>    | <span data-ttu-id="55836-108">“值”</span><span class="sxs-lookup"><span data-stu-id="55836-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="55836-109">范围</span><span class="sxs-lookup"><span data-stu-id="55836-109">Scope</span></span>   |<span data-ttu-id="55836-110">次要</span><span class="sxs-lookup"><span data-stu-id="55836-110">Minor</span></span>|
|<span data-ttu-id="55836-111">Version</span><span class="sxs-lookup"><span data-stu-id="55836-111">Version</span></span>|<span data-ttu-id="55836-112">4.5</span><span class="sxs-lookup"><span data-stu-id="55836-112">4.5</span></span>|
|<span data-ttu-id="55836-113">类型</span><span class="sxs-lookup"><span data-stu-id="55836-113">Type</span></span>|<span data-ttu-id="55836-114">运行时</span><span class="sxs-lookup"><span data-stu-id="55836-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="55836-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="55836-115">Affected APIs</span></span>

- <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.ObjectModel.ObservableCollection`1.Move(System.Int32,System.Int32)``
- ``M:System.Collections.ObjectModel.ObservableCollection`1.MoveItem(System.Int32,System.Int32)``

-->
