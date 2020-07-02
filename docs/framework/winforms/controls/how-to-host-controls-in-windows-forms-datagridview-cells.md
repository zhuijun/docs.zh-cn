---
title: DataGridView 单元格中的宿主控件
description: 了解如何在 Windows 窗体 DataGridView 单元格中承载控件，使用户能够以多种方式输入和编辑值。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: 87901cbf86689bec49f5692feeabdae79f6b93ba
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619541"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a>如何：在 Windows 窗体 DataGridView 单元格中托管控件
<xref:System.Windows.Forms.DataGridView> 控件提供了几种列类型，使用户能够以多种方式输入和编辑值。 但是如果这些列类型无法满足数据录入的需求，可以自主创建带有承载所选控件的单元格的列类型。 为此，必须定义派生自 <xref:System.Windows.Forms.DataGridViewColumn> 和 <xref:System.Windows.Forms.DataGridViewCell> 的类。 还必须定义派生自 <xref:System.Windows.Forms.Control> 的类并实现 <xref:System.Windows.Forms.IDataGridViewEditingControl> 接口。  
  
 下面的代码示例演示如何创建日历列。 此列的单元格将显示普通的文本框单元格中的日期，但当用户编辑单元格时，将出现 <xref:System.Windows.Forms.DateTimePicker> 控件。 为了避免再次实现文本框显示功能，`CalendarCell` 类会从 <xref:System.Windows.Forms.DataGridViewTextBoxCell> 类派生，而不是直接继承 <xref:System.Windows.Forms.DataGridViewCell> 类。  
  
> [!NOTE]
> 当从 <xref:System.Windows.Forms.DataGridViewCell> 或 <xref:System.Windows.Forms.DataGridViewColumn> 进行派生并将新属性添加到派生的类时，请确保重写 `Clone` 方法以在克隆操作过程中复制新属性。 还应调用基类的 `Clone` 方法，以便将基类的属性复制到新的单元格或列。  
  
## <a name="example"></a>示例  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a>编译代码  
 以下示例需要：  
  
- 对 System 和 System.Windows.Forms 程序集的引用。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [自定义 Windows 窗体 DataGridView 控件](customizing-the-windows-forms-datagridview-control.md)
- [DataGridView 控件体系结构](datagridview-control-architecture-windows-forms.md)
- [Windows 窗体 DataGridView 控件中的列类型](column-types-in-the-windows-forms-datagridview-control.md)
