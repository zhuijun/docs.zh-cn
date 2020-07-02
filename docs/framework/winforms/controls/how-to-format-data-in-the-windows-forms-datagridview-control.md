---
title: 在 DataGridView 控件中设置数据格式
description: 了解如何使用 Windows 窗体 DataGridView 控件和控件中特定列的的 Datagridviewband.defaultcellstyle 属性设置单元值的格式。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in DataGridView control
- data grids [Windows Forms], enabling wordwrap
- currency values [Windows Forms], formatting in data grids
- data grids [Windows Forms], currency values
- data grids [Windows Forms], formatting data
- data grids [Windows Forms], text alignment
- data grids [Windows Forms], date values
- cells [Windows Forms], text alignment
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
ms.openlocfilehash: d6105c1d1120876f854332e7a10106cc1caf6276
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622804"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b8aef-103">如何：设置 Windows 窗体 DataGridView 控件中的数据格式</span><span class="sxs-lookup"><span data-stu-id="b8aef-103">How to: Format Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b8aef-104">以下过程演示了使用 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> 控件的属性 <xref:System.Windows.Forms.DataGridView> 和控件中特定列的单元格值的基本格式设置。</span><span class="sxs-lookup"><span data-stu-id="b8aef-104">The following procedures demonstrate basic formatting of cell values using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property of a <xref:System.Windows.Forms.DataGridView> control and of specific columns in a control.</span></span> <span data-ttu-id="b8aef-105">有关高级数据格式设置的信息，请参阅[如何：自定义 Windows 窗体 DataGridView 控件中的数据格式](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="b8aef-105">For information about advanced data formatting, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-format-currency-and-date-values"></a><span data-ttu-id="b8aef-106">设置货币和日期值的格式</span><span class="sxs-lookup"><span data-stu-id="b8aef-106">To format currency and date values</span></span>  
  
- <span data-ttu-id="b8aef-107">设置 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="b8aef-107">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="b8aef-108">下面的代码示例使用列的属性设置特定列的格式 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b8aef-108">The following code example sets the format for specific columns using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the columns.</span></span> <span data-ttu-id="b8aef-109">列中的值 `UnitPrice` 以当前特定于区域性的货币格式显示，其中负值括在括号中。</span><span class="sxs-lookup"><span data-stu-id="b8aef-109">Values in the `UnitPrice` column appear in the current culture-specific currency format, with negative values surrounded by parentheses.</span></span> <span data-ttu-id="b8aef-110">列中的值 `ShipDate` 以当前特定于区域性的短日期格式显示。</span><span class="sxs-lookup"><span data-stu-id="b8aef-110">Values in the `ShipDate` column appear in the current culture-specific short date format.</span></span> <span data-ttu-id="b8aef-111">有关值的详细信息 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> ，请参阅[格式设置类型](../../../standard/base-types/formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="b8aef-111">For more information about <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> values, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a><span data-ttu-id="b8aef-112">自定义 null 数据库值的显示</span><span class="sxs-lookup"><span data-stu-id="b8aef-112">To customize the display of null database values</span></span>  
  
- <span data-ttu-id="b8aef-113">设置 <xref:System.Windows.Forms.DataGridViewCellStyle> 的 <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="b8aef-113">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="b8aef-114">下面的代码示例使用 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> 属性在包含等于的值的所有单元格中显示 "no entry" <xref:System.DBNull.Value?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b8aef-114">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to display "no entry" in all cells containing values equal to <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a><span data-ttu-id="b8aef-115">在基于文本的单元中启用换行</span><span class="sxs-lookup"><span data-stu-id="b8aef-115">To enable wordwrap in text-based cells</span></span>  
  
- <span data-ttu-id="b8aef-116">将的 <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> 属性设置 <xref:System.Windows.Forms.DataGridViewCellStyle> 为 <xref:System.Windows.Forms.DataGridViewTriState> 枚举值之一。</span><span class="sxs-lookup"><span data-stu-id="b8aef-116">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewTriState> enumeration values.</span></span> <span data-ttu-id="b8aef-117">下面的代码示例使用 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> 属性设置整个控件的环绕模式。</span><span class="sxs-lookup"><span data-stu-id="b8aef-117">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the wrap mode for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a><span data-ttu-id="b8aef-118">指定 DataGridView 单元格的文本对齐方式</span><span class="sxs-lookup"><span data-stu-id="b8aef-118">To specify the text alignment of DataGridView cells</span></span>  
  
- <span data-ttu-id="b8aef-119">将的 <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> 属性设置 <xref:System.Windows.Forms.DataGridViewCellStyle> 为 <xref:System.Windows.Forms.DataGridViewContentAlignment> 枚举值之一。</span><span class="sxs-lookup"><span data-stu-id="b8aef-119">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewContentAlignment> enumeration values.</span></span> <span data-ttu-id="b8aef-120">下面的代码示例使用列的属性设置特定列的对齐方式 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b8aef-120">The following code example sets the alignment for a specific column using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the column.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a><span data-ttu-id="b8aef-121">示例</span><span class="sxs-lookup"><span data-stu-id="b8aef-121">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b8aef-122">编译代码</span><span class="sxs-lookup"><span data-stu-id="b8aef-122">Compiling the Code</span></span>  
 <span data-ttu-id="b8aef-123">这些示例需要：</span><span class="sxs-lookup"><span data-stu-id="b8aef-123">These examples require:</span></span>  
  
- <span data-ttu-id="b8aef-124">一个 <xref:System.Windows.Forms.DataGridView> 名为 `dataGridView1` 的控件，它包含一个名为的列 `UnitPrice` 、一个名为的列 `ShipDate` 和一个名为的列 `CustomerName` 。</span><span class="sxs-lookup"><span data-stu-id="b8aef-124">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `UnitPrice`, a column named `ShipDate`, and a column named `CustomerName`.</span></span>  
  
- <span data-ttu-id="b8aef-125">对 <xref:System?displayProperty=nameWithType><xref:System.Drawing?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="b8aef-125">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b8aef-126">可靠编程</span><span class="sxs-lookup"><span data-stu-id="b8aef-126">Robust Programming</span></span>  
 <span data-ttu-id="b8aef-127">为了实现最大的可伸缩性，应 <xref:System.Windows.Forms.DataGridViewCellStyle> 跨多个行、列或使用相同样式的单元格共享对象，而不是单独设置每个元素的样式属性。</span><span class="sxs-lookup"><span data-stu-id="b8aef-127">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="b8aef-128">有关详细信息，请参阅 [缩放 Windows 窗体 DataGridView 控件的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="b8aef-128">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8aef-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="b8aef-129">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="b8aef-130">Windows 窗体 DataGridView 控件中的基本格式设置和样式设置</span><span class="sxs-lookup"><span data-stu-id="b8aef-130">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b8aef-131">Windows 窗体 DataGridView 控件中的单元格样式</span><span class="sxs-lookup"><span data-stu-id="b8aef-131">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b8aef-132">Windows 窗体 DataGridView 控件中的数据格式设置</span><span class="sxs-lookup"><span data-stu-id="b8aef-132">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b8aef-133">如何：在 Windows 窗体 DataGridView 控件中自定义数据格式设置</span><span class="sxs-lookup"><span data-stu-id="b8aef-133">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b8aef-134">格式设置类型</span><span class="sxs-lookup"><span data-stu-id="b8aef-134">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
