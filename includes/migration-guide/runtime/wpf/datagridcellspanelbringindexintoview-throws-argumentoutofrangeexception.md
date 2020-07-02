---
ms.openlocfilehash: d78d083b16ac034c6c393dbc0f6094ee4c6c63c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622340"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a><span data-ttu-id="65a47-101">DataGridCellsPanel.BringIndexIntoView 引发 ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="65a47-101">DataGridCellsPanel.BringIndexIntoView throws ArgumentOutOfRangeException</span></span>

#### <a name="details"></a><span data-ttu-id="65a47-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="65a47-102">Details</span></span>

<span data-ttu-id="65a47-103">启用列虚拟化但尚未确定列宽时，<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> 将以异步方式执行工作。</span><span class="sxs-lookup"><span data-stu-id="65a47-103"><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> will work asynchronously when column virtualization is enabled but the column widths have not yet been determined.</span></span>  <span data-ttu-id="65a47-104">如果在异步工作执行之前删除列，可能会出现 <xref:System.ArgumentOutOfRangeException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="65a47-104">If columns are removed before the asynchronous work happens, an <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> can occur.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="65a47-105">建议</span><span class="sxs-lookup"><span data-stu-id="65a47-105">Suggestion</span></span>

<span data-ttu-id="65a47-106">以下任一项：</span><span class="sxs-lookup"><span data-stu-id="65a47-106">Any one of the following:</span></span><ol><li><span data-ttu-id="65a47-107">升级到 .NET Framework 4.7。</span><span class="sxs-lookup"><span data-stu-id="65a47-107">Upgrade to .NET Framework 4.7.</span></span></li><li><span data-ttu-id="65a47-108">安装 .NET Framework 4.6.2 的最新服务修补程序。</span><span class="sxs-lookup"><span data-stu-id="65a47-108">Install the latest servicing patch for .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="65a47-109">在对 <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> 的异步响应完成前，避免删除列。</span><span class="sxs-lookup"><span data-stu-id="65a47-109">Avoid removing columns until the asynchronous response to <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> has completed.</span></span></li></ol>

| <span data-ttu-id="65a47-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="65a47-110">Name</span></span>    | <span data-ttu-id="65a47-111">值</span><span class="sxs-lookup"><span data-stu-id="65a47-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="65a47-112">范围</span><span class="sxs-lookup"><span data-stu-id="65a47-112">Scope</span></span>   |<span data-ttu-id="65a47-113">边缘</span><span class="sxs-lookup"><span data-stu-id="65a47-113">Edge</span></span>|
|<span data-ttu-id="65a47-114">Version</span><span class="sxs-lookup"><span data-stu-id="65a47-114">Version</span></span>|<span data-ttu-id="65a47-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="65a47-115">4.6.2</span></span>|
|<span data-ttu-id="65a47-116">类型</span><span class="sxs-lookup"><span data-stu-id="65a47-116">Type</span></span>|<span data-ttu-id="65a47-117">运行时</span><span class="sxs-lookup"><span data-stu-id="65a47-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="65a47-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="65a47-118">Affected APIs</span></span>

-<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|
