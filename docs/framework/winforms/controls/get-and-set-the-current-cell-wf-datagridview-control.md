---
title: 获取和设置 DataGridView 控件中的当前单元格
description: 了解如何通过获取并设置 Windows 窗体 DataGridView 控件中的当前单元格来以编程方式发现哪个单元格当前处于活动状态。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 1651ca9c8fa0329f9435a70ce777bce68f15ff63
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622206"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>如何：获取和设置 Windows 窗体 DataGridView 控件中的当前单元格
与的交互 <xref:System.Windows.Forms.DataGridView> 通常要求您以编程方式发现哪个单元格当前处于活动状态。 您可能还需要更改当前单元格。 可以通过属性执行这些任务 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> 。  
  
> [!NOTE]
> 不能将属性设置为的行或列中的当前单元格设置 <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> 为 `false` 。  
  
 <xref:System.Windows.Forms.DataGridView>更改当前单元格可能会更改选定内容，具体取决于控件的选择模式。 有关详细信息，请参阅[Windows 窗体 DataGridView 控件中的选择模式](selection-modes-in-the-windows-forms-datagridview-control.md)。  
  
### <a name="to-get-the-current-cell-programmatically"></a>以编程方式获取当前单元格  
  
- 使用 <xref:System.Windows.Forms.DataGridView> 控件的 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> 属性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>以编程方式设置当前单元格  
  
- 设置 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> 控件的属性 <xref:System.Windows.Forms.DataGridView> 。 在下面的代码示例中，当前单元格设置为第0行，第1列。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
- <xref:System.Windows.Forms.Button>名为 `getCurrentCellButton` 和 `setCurrentCellButton` 的控件。 在 Visual c # 中，必须将 <xref:System.Windows.Forms.Control.Click> 每个按钮的事件附加到示例代码中的关联事件处理程序。  
  
- 名为 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控件。  
  
- 对 <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 程序集的引用。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [Windows 窗体 DataGridView 控件中的基本列、行和单元格功能](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的选择模式](selection-modes-in-the-windows-forms-datagridview-control.md)
