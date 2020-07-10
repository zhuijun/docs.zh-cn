---
title: ComboBox 与 ListBox
description: 了解如何使用 Windows 窗体 ComboBox 和 Windows 窗体 ListBox，并了解如何判断一个或另一个对任务更合适的时间。
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], vs. ComboBox
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- ComboBox control [Windows Forms], compared to ListBox
- combo boxes [Windows Forms], compared to list boxes
- ListBox control [Windows Forms], accessing items
- ListCount property
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
ms.openlocfilehash: ca6ad6bec2dbc30128ea09808af2806687b17a8c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174414"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>何时使用 Windows 窗体 ComboBox 而非 ListBox
<xref:System.Windows.Forms.ComboBox>和 <xref:System.Windows.Forms.ListBox> 控件具有相似的行为，并且在某些情况下，可以互换。 但有时，当其中一项或其他项更适合某个任务时。  
  
 通常，当存在建议的选项列表时，组合框是适当的，当你想要将输入限制为列表上的内容时，可使用列表框。 组合框包含文本框字段，因此可以在列表中键入不是在列表中的选项。 当 <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> 属性设置为时，例外 <xref:System.Windows.Forms.ComboBoxStyle.DropDownList> 。 在这种情况下，如果键入第一个字母，控件将选择一项。  
  
 此外，组合框还节省了窗体上的空间。 因为在用户单击向下箭头后，不显示完整列表，所以，组合框可以轻松地放入列表框无法容纳的小空间。 当属性设置为时，例外情况是 <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> <xref:System.Windows.Forms.ComboBoxStyle.Simple> ：显示完整列表，组合框比列表框占用更多空间。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [如何：在 Windows 窗体 ComboBox 控件、ListBox 控件或 CheckedListBox 控件中添加或移除项](add-and-remove-items-from-a-wf-combobox.md)
- [如何：对 Windows 窗体 ComboBox 控件、ListBox 控件或 CheckedListBox 控件的内容排序](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [用于列出选项的 Windows 窗体控件](windows-forms-controls-used-to-list-options.md)
