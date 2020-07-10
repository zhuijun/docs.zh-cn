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
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>如何：向 Windows 窗体 ListView 控件中添加列
在详细信息视图中， <xref:System.Windows.Forms.ListView> 控件可以为每个列表项显示多个列。 您可以使用这些列向用户显示有关每个列表项的多种类型的信息。 例如，文件列表可以显示文件的名称、文件类型、大小和文件的上次修改日期。 有关在创建列后对其进行填充的信息，请参阅[如何：用 Windows 窗体 ListView 控件在列中显示子项](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)。  
  
### <a name="to-add-columns-programmatically"></a>以编程方式添加列  
  
1. 将控件的 <xref:System.Windows.Forms.ListView.View%2A> 属性设置为 <xref:System.Windows.Forms.View.Details> 。  
  
2. 使用 <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> 列表视图的属性的方法 <xref:System.Windows.Forms.ListView.Columns%2A> 。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.ListView>
- [ListView 控件](listview-control-windows-forms.md)
- [ListView 控件概述](listview-control-overview-windows-forms.md)
