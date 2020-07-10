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
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="ed7dc-103">何时使用 Windows 窗体 ComboBox 而非 ListBox</span><span class="sxs-lookup"><span data-stu-id="ed7dc-103">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="ed7dc-104"><xref:System.Windows.Forms.ComboBox>和 <xref:System.Windows.Forms.ListBox> 控件具有相似的行为，并且在某些情况下，可以互换。</span><span class="sxs-lookup"><span data-stu-id="ed7dc-104">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="ed7dc-105">但有时，当其中一项或其他项更适合某个任务时。</span><span class="sxs-lookup"><span data-stu-id="ed7dc-105">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="ed7dc-106">通常，当存在建议的选项列表时，组合框是适当的，当你想要将输入限制为列表上的内容时，可使用列表框。</span><span class="sxs-lookup"><span data-stu-id="ed7dc-106">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="ed7dc-107">组合框包含文本框字段，因此可以在列表中键入不是在列表中的选项。</span><span class="sxs-lookup"><span data-stu-id="ed7dc-107">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="ed7dc-108">当 <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> 属性设置为时，例外 <xref:System.Windows.Forms.ComboBoxStyle.DropDownList> 。</span><span class="sxs-lookup"><span data-stu-id="ed7dc-108">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="ed7dc-109">在这种情况下，如果键入第一个字母，控件将选择一项。</span><span class="sxs-lookup"><span data-stu-id="ed7dc-109">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="ed7dc-110">此外，组合框还节省了窗体上的空间。</span><span class="sxs-lookup"><span data-stu-id="ed7dc-110">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="ed7dc-111">因为在用户单击向下箭头后，不显示完整列表，所以，组合框可以轻松地放入列表框无法容纳的小空间。</span><span class="sxs-lookup"><span data-stu-id="ed7dc-111">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="ed7dc-112">当属性设置为时，例外情况是 <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> <xref:System.Windows.Forms.ComboBoxStyle.Simple> ：显示完整列表，组合框比列表框占用更多空间。</span><span class="sxs-lookup"><span data-stu-id="ed7dc-112">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed7dc-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ed7dc-113">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [<span data-ttu-id="ed7dc-114">如何：在 Windows 窗体 ComboBox 控件、ListBox 控件或 CheckedListBox 控件中添加或移除项</span><span class="sxs-lookup"><span data-stu-id="ed7dc-114">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](add-and-remove-items-from-a-wf-combobox.md)
- [<span data-ttu-id="ed7dc-115">如何：对 Windows 窗体 ComboBox 控件、ListBox 控件或 CheckedListBox 控件的内容排序</span><span class="sxs-lookup"><span data-stu-id="ed7dc-115">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="ed7dc-116">用于列出选项的 Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="ed7dc-116">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
