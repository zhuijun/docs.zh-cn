---
title: 向 ListView 控件添加列
description: 了解如何向 Windows 窗体 ListView 控件添加列，以显示有关每个列表项的多种类型的信息。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: 7ca4e86ca3a9679876f2525c49596534f175096a
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174557"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a><span data-ttu-id="cd769-103">如何：向 Windows 窗体 ListView 控件中添加列</span><span class="sxs-lookup"><span data-stu-id="cd769-103">How to: Add Columns to the Windows Forms ListView Control</span></span>
<span data-ttu-id="cd769-104">在详细信息视图中， <xref:System.Windows.Forms.ListView> 控件可以为每个列表项显示多个列。</span><span class="sxs-lookup"><span data-stu-id="cd769-104">In the Details view, the <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item.</span></span> <span data-ttu-id="cd769-105">您可以使用这些列向用户显示有关每个列表项的多种类型的信息。</span><span class="sxs-lookup"><span data-stu-id="cd769-105">You can use the columns to display to the user several types of information about each list item.</span></span> <span data-ttu-id="cd769-106">例如，文件列表可以显示文件的名称、文件类型、大小和文件的上次修改日期。</span><span class="sxs-lookup"><span data-stu-id="cd769-106">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="cd769-107">有关在创建列后对其进行填充的信息，请参阅[如何：用 Windows 窗体 ListView 控件在列中显示子项](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)。</span><span class="sxs-lookup"><span data-stu-id="cd769-107">For information about populating the columns after they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>  
  
### <a name="to-add-columns-programmatically"></a><span data-ttu-id="cd769-108">以编程方式添加列</span><span class="sxs-lookup"><span data-stu-id="cd769-108">To add columns programmatically</span></span>  
  
1. <span data-ttu-id="cd769-109">将控件的 <xref:System.Windows.Forms.ListView.View%2A> 属性设置为 <xref:System.Windows.Forms.View.Details> 。</span><span class="sxs-lookup"><span data-stu-id="cd769-109">Set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
2. <span data-ttu-id="cd769-110">使用 <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> 列表视图的属性的方法 <xref:System.Windows.Forms.ListView.Columns%2A> 。</span><span class="sxs-lookup"><span data-stu-id="cd769-110">Use the <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> method of the list view's <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="cd769-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cd769-111">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="cd769-112">ListView 控件</span><span class="sxs-lookup"><span data-stu-id="cd769-112">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="cd769-113">ListView 控件概述</span><span class="sxs-lookup"><span data-stu-id="cd769-113">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
