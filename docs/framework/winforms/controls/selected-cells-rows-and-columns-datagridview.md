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
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a>如何：获取 Windows 窗体 DataGridView 控件中选定的单元格、行和列
通过使用相应的属性，可以从控件中获取选定的单元格、行或列 <xref:System.Windows.Forms.DataGridView> ： <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 、 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> 和 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> 。 在下面的过程中，您将获取选定的单元格，并在中显示其行和列索引 <xref:System.Windows.Forms.MessageBox> 。  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a>获取 DataGridView 控件中选定的单元格  
  
- 使用 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 属性。  
  
    > [!NOTE]
    > 使用 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> 方法可避免显示可能大量的单元格。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a>获取 DataGridView 控件中的选定行  
  
- 使用 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> 属性。 若要使用户能够选择行，则必须将 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 属性设置为 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> 。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a>获取 DataGridView 控件中的选定列  
  
- 使用 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> 属性。 若要使用户能够选择列，必须将 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> 属性设置为 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> 或 <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect> 。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
- <xref:System.Windows.Forms.Button>名为 `selectedCellsButton` 、 `selectedRowsButton` 和的控件 `selectedColumnsButton` ，每个控件都具有附加事件的处理程序 <xref:System.Windows.Forms.Control.Click> 。  
  
- 名为 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控件。  
  
- 对 <xref:System?displayProperty=nameWithType><xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Text?displayProperty=nameWithType> 程序集的引用。  
  
## <a name="robust-programming"></a>可靠编程  
 如果选择了大量的单元格、行或列，本主题中所述的集合将无法有效地执行。 有关对大量数据使用这些集合的详细信息，请参阅[缩放 Windows 窗体 DataGridView 控件的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [Windows 窗体 DataGridView 控件的选项和剪贴板使用](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
