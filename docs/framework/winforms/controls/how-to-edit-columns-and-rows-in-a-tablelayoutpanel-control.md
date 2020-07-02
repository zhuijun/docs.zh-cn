---
title: 如何：在 TableLayoutPanel 控件中编辑行和列
description: 了解如何使用 "列和行样式" 对话框编辑 Windows 窗体控件的行和列。
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: cfd2ca4be5d5a2658a9a129d911f1dba9670ccfd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619346"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>如何：在 TableLayoutPanel 控件中编辑行和列

您可以使用控件的集合编辑器 <xref:System.Windows.Forms.TableLayoutPanel> （称为 "**列和行样式**" 对话框）来编辑控件的行和列。

> [!NOTE]
> 如果希望控件跨多个行或列，请 `RowSpan` `ColumnSpan` 在控件上设置和属性。 有关详细信息，请参阅 [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。
>
> 如果要在单元格中对齐控件，或者希望控件在单元格内伸展，请使用控件的 <xref:System.Windows.Forms.Control.Anchor%2A> 属性。 有关详细信息，请参阅 [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)。

## <a name="to-edit-rows-and-columns"></a>编辑行和列

1. 从 <xref:System.Windows.Forms.TableLayoutPanel> “工具箱” **将** 控件拖到你的窗体上。

2. 单击 <xref:System.Windows.Forms.TableLayoutPanel> 控件的设计器操作标志符号（ ![ 较小 ](./media/designer-actions-glyph.gif) 的黑色箭头），然后选择 "**编辑行和列**" 以打开 "**列和行样式**" 对话框。 您还可以右键单击 <xref:System.Windows.Forms.TableLayoutPanel> 控件，然后从快捷菜单中选择 "**编辑行和列**"。

3. 若要添加或删除列，请从 "**成员类型**" 下拉列表框中选择 "**列**"。

4. 若要添加或删除行，请从 "**成员类型**" 下拉列表框中选择 "**行**"。

5. 单击 "**添加**" 按钮可向**成员列表**的末尾添加行或列。

6. 单击 "**插入**" 按钮，在列表中当前选定的项之前添加行或列。

7. 如果要添加行或列，请选择新行或列的**大小类型**。 有关详细信息，请参阅 <xref:System.Windows.Forms.SizeType>。

8. 若要删除行或列，请单击 "**删除**" 按钮以删除**成员列表**中当前选定的项。

## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.SizeType>
- [TableLayoutPanel 控件](tablelayoutpanel-control-windows-forms.md)
