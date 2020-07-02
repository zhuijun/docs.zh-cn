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
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="361ea-103">如何：获取和设置 Windows 窗体 DataGridView 控件中的当前单元格</span><span class="sxs-lookup"><span data-stu-id="361ea-103">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="361ea-104">与的交互 <xref:System.Windows.Forms.DataGridView> 通常要求您以编程方式发现哪个单元格当前处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="361ea-104">Interaction with the <xref:System.Windows.Forms.DataGridView> often requires that you programmatically discover which cell is currently active.</span></span> <span data-ttu-id="361ea-105">您可能还需要更改当前单元格。</span><span class="sxs-lookup"><span data-stu-id="361ea-105">You may also need to change the current cell.</span></span> <span data-ttu-id="361ea-106">可以通过属性执行这些任务 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> 。</span><span class="sxs-lookup"><span data-stu-id="361ea-106">You can perform these tasks with the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="361ea-107">不能将属性设置为的行或列中的当前单元格设置 <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> 为 `false` 。</span><span class="sxs-lookup"><span data-stu-id="361ea-107">You cannot set the current cell in a row or column that has its <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> property set to `false`.</span></span>  
  
 <span data-ttu-id="361ea-108"><xref:System.Windows.Forms.DataGridView>更改当前单元格可能会更改选定内容，具体取决于控件的选择模式。</span><span class="sxs-lookup"><span data-stu-id="361ea-108">Depending on the <xref:System.Windows.Forms.DataGridView> control's selection mode, changing the current cell can change the selection.</span></span> <span data-ttu-id="361ea-109">有关详细信息，请参阅[Windows 窗体 DataGridView 控件中的选择模式](selection-modes-in-the-windows-forms-datagridview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="361ea-109">For more information, see [Selection Modes in the Windows Forms DataGridView Control](selection-modes-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-get-the-current-cell-programmatically"></a><span data-ttu-id="361ea-110">以编程方式获取当前单元格</span><span class="sxs-lookup"><span data-stu-id="361ea-110">To get the current cell programmatically</span></span>  
  
- <span data-ttu-id="361ea-111">使用 <xref:System.Windows.Forms.DataGridView> 控件的 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="361ea-111">Use the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a><span data-ttu-id="361ea-112">以编程方式设置当前单元格</span><span class="sxs-lookup"><span data-stu-id="361ea-112">To set the current cell programmatically</span></span>  
  
- <span data-ttu-id="361ea-113">设置 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> 控件的属性 <xref:System.Windows.Forms.DataGridView> 。</span><span class="sxs-lookup"><span data-stu-id="361ea-113">Set the <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> property of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="361ea-114">在下面的代码示例中，当前单元格设置为第0行，第1列。</span><span class="sxs-lookup"><span data-stu-id="361ea-114">In the following code example, the current cell is set to row 0, column 1.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="361ea-115">编译代码</span><span class="sxs-lookup"><span data-stu-id="361ea-115">Compiling the Code</span></span>  
 <span data-ttu-id="361ea-116">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="361ea-116">This example requires:</span></span>  
  
- <span data-ttu-id="361ea-117"><xref:System.Windows.Forms.Button>名为 `getCurrentCellButton` 和 `setCurrentCellButton` 的控件。</span><span class="sxs-lookup"><span data-stu-id="361ea-117"><xref:System.Windows.Forms.Button> controls named `getCurrentCellButton` and `setCurrentCellButton`.</span></span> <span data-ttu-id="361ea-118">在 Visual c # 中，必须将 <xref:System.Windows.Forms.Control.Click> 每个按钮的事件附加到示例代码中的关联事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="361ea-118">In Visual C#, you must attach the <xref:System.Windows.Forms.Control.Click> events for each button to the associated event handler in the example code.</span></span>  
  
- <span data-ttu-id="361ea-119">名为 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控件。</span><span class="sxs-lookup"><span data-stu-id="361ea-119">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="361ea-120">对 <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="361ea-120">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="361ea-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="361ea-121">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [<span data-ttu-id="361ea-122">Windows 窗体 DataGridView 控件中的基本列、行和单元格功能</span><span class="sxs-lookup"><span data-stu-id="361ea-122">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="361ea-123">Windows 窗体 DataGridView 控件中的选择模式</span><span class="sxs-lookup"><span data-stu-id="361ea-123">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)
