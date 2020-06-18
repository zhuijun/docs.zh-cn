---
title: 获取 DataGridView 控件中选定的单元格、行和列
description: 了解如何使用相应的属性从 DataGridView 控件获取选定的单元格、行或列。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: 32ddae34104d23b8e5fbc0cce7da79f33fcce1d2
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904164"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="520df-103">如何：获取 Windows 窗体 DataGridView 控件中选定的单元格、行和列</span><span class="sxs-lookup"><span data-stu-id="520df-103">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="520df-104">通过使用相应的属性，可以从控件中获取选定的单元格、行或列 <xref:System.Windows.Forms.DataGridView> ： <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 、 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> 和 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> 。</span><span class="sxs-lookup"><span data-stu-id="520df-104">You can get the selected cells, rows, or columns from a <xref:System.Windows.Forms.DataGridView> control by using the corresponding properties: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, and <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span></span> <span data-ttu-id="520df-105">在下面的过程中，您将获取选定的单元格，并在中显示其行和列索引 <xref:System.Windows.Forms.MessageBox> 。</span><span class="sxs-lookup"><span data-stu-id="520df-105">In the following procedures, you will get the selected cells and display their row and column indexes in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a><span data-ttu-id="520df-106">获取 DataGridView 控件中选定的单元格</span><span class="sxs-lookup"><span data-stu-id="520df-106">To get the selected cells in a DataGridView control</span></span>  
  
- <span data-ttu-id="520df-107">使用 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="520df-107">Use the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> property.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="520df-108">使用 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> 方法可避免显示可能大量的单元格。</span><span class="sxs-lookup"><span data-stu-id="520df-108">Use the <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> method to avoid showing a potentially large number of cells.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a><span data-ttu-id="520df-109">获取 DataGridView 控件中的选定行</span><span class="sxs-lookup"><span data-stu-id="520df-109">To get the selected rows in a DataGridView control</span></span>  
  
- <span data-ttu-id="520df-110">使用 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="520df-110">Use the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> property.</span></span> <span data-ttu-id="520df-111">若要使用户能够选择行，则必须将 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 属性设置为 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> 。</span><span class="sxs-lookup"><span data-stu-id="520df-111">To enable users to select rows, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a><span data-ttu-id="520df-112">获取 DataGridView 控件中的选定列</span><span class="sxs-lookup"><span data-stu-id="520df-112">To get the selected columns in a DataGridView control</span></span>  
  
- <span data-ttu-id="520df-113">使用 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="520df-113">Use the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> property.</span></span> <span data-ttu-id="520df-114">若要使用户能够选择列，必须将 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 属性设置为 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect> 。</span><span class="sxs-lookup"><span data-stu-id="520df-114">To enable users to select columns, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="520df-115">编译代码</span><span class="sxs-lookup"><span data-stu-id="520df-115">Compiling the Code</span></span>  
 <span data-ttu-id="520df-116">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="520df-116">This example requires:</span></span>  
  
- <span data-ttu-id="520df-117"><xref:System.Windows.Forms.Button>名为 `selectedCellsButton` 、 `selectedRowsButton` 和的控件 `selectedColumnsButton` ，每个控件都具有附加事件的处理程序 <xref:System.Windows.Forms.Control.Click> 。</span><span class="sxs-lookup"><span data-stu-id="520df-117"><xref:System.Windows.Forms.Button> controls named `selectedCellsButton`, `selectedRowsButton`, and `selectedColumnsButton`, each with handlers for the <xref:System.Windows.Forms.Control.Click> event attached.</span></span>  
  
- <span data-ttu-id="520df-118">名为 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控件。</span><span class="sxs-lookup"><span data-stu-id="520df-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="520df-119">对 <xref:System?displayProperty=nameWithType><xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Text?displayProperty=nameWithType> 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="520df-119">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Text?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="520df-120">可靠编程</span><span class="sxs-lookup"><span data-stu-id="520df-120">Robust Programming</span></span>  
 <span data-ttu-id="520df-121">如果选择了大量的单元格、行或列，本主题中所述的集合将无法有效地执行。</span><span class="sxs-lookup"><span data-stu-id="520df-121">The collections described in this topic do not perform efficiently when large numbers of cells, rows, or columns are selected.</span></span> <span data-ttu-id="520df-122">有关对大量数据使用这些集合的详细信息，请参阅[缩放 Windows 窗体 DataGridView 控件的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="520df-122">For more information about using these collections with large amounts of data, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="520df-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="520df-123">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [<span data-ttu-id="520df-124">Windows 窗体 DataGridView 控件的选项和剪贴板使用</span><span class="sxs-lookup"><span data-stu-id="520df-124">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
