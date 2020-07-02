---
ms.openlocfilehash: c3c3ed44cf53625c246dfe0408bb861750ecf336
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621938"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="e708f-101">从 CellEditEnding 处理程序调用 DataGrid.CommitEdit 将丢失焦点</span><span class="sxs-lookup"><span data-stu-id="e708f-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

#### <a name="details"></a><span data-ttu-id="e708f-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="e708f-102">Details</span></span>

<span data-ttu-id="e708f-103">从 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 的一个 <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> 事件处理程序中调用 <xref:System.Windows.Controls.DataGrid.CommitEdit> 导致 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 失去焦点。</span><span class="sxs-lookup"><span data-stu-id="e708f-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> to lose focus.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e708f-104">建议</span><span class="sxs-lookup"><span data-stu-id="e708f-104">Suggestion</span></span>

<span data-ttu-id="e708f-105">此 bug 已在 .NET Framework 4.5.2 中得到修复，因此升级 .NET Framework 可避免出现此问题。</span><span class="sxs-lookup"><span data-stu-id="e708f-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="e708f-106">或者，可通过在调用 <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName> 后显式重新选择 <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 避免出现此问题。</span><span class="sxs-lookup"><span data-stu-id="e708f-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName>.</span></span>

| <span data-ttu-id="e708f-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="e708f-107">Name</span></span>    | <span data-ttu-id="e708f-108">“值”</span><span class="sxs-lookup"><span data-stu-id="e708f-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e708f-109">范围</span><span class="sxs-lookup"><span data-stu-id="e708f-109">Scope</span></span>   |<span data-ttu-id="e708f-110">边缘</span><span class="sxs-lookup"><span data-stu-id="e708f-110">Edge</span></span>|
|<span data-ttu-id="e708f-111">Version</span><span class="sxs-lookup"><span data-stu-id="e708f-111">Version</span></span>|<span data-ttu-id="e708f-112">4.5</span><span class="sxs-lookup"><span data-stu-id="e708f-112">4.5</span></span>|
|<span data-ttu-id="e708f-113">类型</span><span class="sxs-lookup"><span data-stu-id="e708f-113">Type</span></span>|<span data-ttu-id="e708f-114">运行时</span><span class="sxs-lookup"><span data-stu-id="e708f-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e708f-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="e708f-115">Affected APIs</span></span>

-<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
