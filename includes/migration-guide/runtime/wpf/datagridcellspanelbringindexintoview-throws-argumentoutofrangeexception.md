---
ms.openlocfilehash: 961ca545560a53fc2c1d52722b68ae460de66877
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496336"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a><span data-ttu-id="cf4dd-101">DataGridCellsPanel.BringIndexIntoView 引发 ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="cf4dd-101">DataGridCellsPanel.BringIndexIntoView throws ArgumentOutOfRangeException</span></span>

#### <a name="details"></a><span data-ttu-id="cf4dd-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="cf4dd-102">Details</span></span>

<span data-ttu-id="cf4dd-103">启用列虚拟化但尚未确定列宽时，<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> 将以异步方式执行工作。</span><span class="sxs-lookup"><span data-stu-id="cf4dd-103"><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> will work asynchronously when column virtualization is enabled but the column widths have not yet been determined.</span></span>  <span data-ttu-id="cf4dd-104">如果在异步工作执行之前删除列，可能会出现 <xref:System.ArgumentOutOfRangeException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="cf4dd-104">If columns are removed before the asynchronous work happens, an <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> can occur.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cf4dd-105">建议</span><span class="sxs-lookup"><span data-stu-id="cf4dd-105">Suggestion</span></span>

<span data-ttu-id="cf4dd-106">以下任一项：</span><span class="sxs-lookup"><span data-stu-id="cf4dd-106">Any one of the following:</span></span><ol><li><span data-ttu-id="cf4dd-107">升级到 .NET Framework 4.7。</span><span class="sxs-lookup"><span data-stu-id="cf4dd-107">Upgrade to .NET Framework 4.7.</span></span></li><li><span data-ttu-id="cf4dd-108">安装 .NET Framework 4.6.2 的最新服务修补程序。</span><span class="sxs-lookup"><span data-stu-id="cf4dd-108">Install the latest servicing patch for .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="cf4dd-109">在对 <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> 的异步响应完成前，避免删除列。</span><span class="sxs-lookup"><span data-stu-id="cf4dd-109">Avoid removing columns until the asynchronous response to <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> has completed.</span></span></li></ol>

| <span data-ttu-id="cf4dd-110">名称</span><span class="sxs-lookup"><span data-stu-id="cf4dd-110">Name</span></span>    | <span data-ttu-id="cf4dd-111">值</span><span class="sxs-lookup"><span data-stu-id="cf4dd-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cf4dd-112">范围</span><span class="sxs-lookup"><span data-stu-id="cf4dd-112">Scope</span></span>   |<span data-ttu-id="cf4dd-113">边缘</span><span class="sxs-lookup"><span data-stu-id="cf4dd-113">Edge</span></span>|
|<span data-ttu-id="cf4dd-114">Version</span><span class="sxs-lookup"><span data-stu-id="cf4dd-114">Version</span></span>|<span data-ttu-id="cf4dd-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="cf4dd-115">4.6.2</span></span>|
|<span data-ttu-id="cf4dd-116">类型</span><span class="sxs-lookup"><span data-stu-id="cf4dd-116">Type</span></span>|<span data-ttu-id="cf4dd-117">运行时</span><span class="sxs-lookup"><span data-stu-id="cf4dd-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="cf4dd-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="cf4dd-118">Affected APIs</span></span>

- <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)`
- `M:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)`

-->
