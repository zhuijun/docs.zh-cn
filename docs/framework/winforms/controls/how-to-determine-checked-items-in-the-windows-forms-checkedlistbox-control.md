---
title: 确定 CheckedListBox 控件中的选中项
description: 了解如何通过循环访问存储在 CheckedItems 属性中的集合来确定 Windows 窗体 CheckedListBox 控件中的选中项。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: fd8845ef83da7406ff4f1468506a23e3f4d386a0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618345"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>如何：确定 Windows 窗体 CheckedListBox 控件中的选定项
在 Windows 窗体控件中显示数据时 <xref:System.Windows.Forms.CheckedListBox> ，可以循环访问存储在属性中的集合 <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> ，或使用方法单步执行列表， <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> 以确定要检查哪些项。 <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>方法使用项索引号作为其参数并返回 `true` 或 `false` 。 与您的预期不同， <xref:System.Windows.Forms.ListBox.SelectedItems%2A> 和 <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> 属性不确定哪些项已选中，它们决定哪些项已突出显示。  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>确定 CheckedListBox 控件中的选中项  
  
1. 循环访问 <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> 集合，从0开始，因为集合是从零开始的。 请注意，此方法将在选中项目列表中为您指定项目编号，而不是总体列表。 因此，如果未检查列表中的第一项并且选中第二项，则以下代码将显示类似于 "Checked Item 1 = MyListItem2" 的文本。  
  
    ```vb  
    ' Determine if there are any items checked.  
    If CheckedListBox1.CheckedItems.Count <> 0 Then  
       ' If so, loop through all checked items and print results.  
       Dim x As Integer  
       Dim s As String = ""  
       For x = 0 To CheckedListBox1.CheckedItems.Count - 1  
          s = s & "Checked Item " & (x + 1).ToString & " = " & CheckedListBox1.CheckedItems(x).ToString & ControlChars.CrLf  
       Next x  
       MessageBox.Show(s)  
    End If  
    ```  
  
    ```csharp  
    // Determine if there are any items checked.  
    if(checkedListBox1.CheckedItems.Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       string s = "";  
       for(int x = 0; x < checkedListBox1.CheckedItems.Count ; x++)  
       {  
          s = s + "Checked Item " + (x+1).ToString() + " = " + checkedListBox1.CheckedItems[x].ToString() + "\n";  
       }  
       MessageBox.Show(s);  
    }  
    ```  
  
    ```cpp  
    // Determine if there are any items checked.  
    if(checkedListBox1->CheckedItems->Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       String ^ s = "";  
       for(int x = 0; x < checkedListBox1->CheckedItems->Count; x++)  
       {  
          s = String::Concat(s, "Checked Item ", (x+1).ToString(),  
             " = ", checkedListBox1->CheckedItems[x]->ToString(),  
             "\n");  
       }  
       MessageBox::Show(s);  
    }  
    ```  
  
     - 或 -  
  
2. 单步执行 <xref:System.Windows.Forms.CheckedListBox.Items%2A> 集合，从0开始，因为集合从零开始，并 <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> 为每个项调用方法。 请注意，此方法将向你显示总体列表中的项编号，因此，如果未检查列表中的第一项并且检查第二项，则会显示类似于 "Item 2 = MyListItem2" 的内容。  
  
    ```vb  
    Dim i As Integer  
    Dim s As String  
    s = "Checked Items:" & ControlChars.CrLf  
    For i = 0 To (CheckedListBox1.Items.Count - 1)  
       If CheckedListBox1.GetItemChecked(i) = True Then  
          s = s & "Item " & (i + 1).ToString & " = " & CheckedListBox1.Items(i).ToString & ControlChars.CrLf  
       End If  
    Next  
    MessageBox.Show(s)  
    ```  
  
    ```csharp  
    int i;  
    string s;
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1.Items.Count-1); i++)  
    {  
       if (checkedListBox1.GetItemChecked(i))  
       {  
          s = s + "Item " + (i+1).ToString() + " = " + checkedListBox1.Items[i].ToString() + "\n";  
       }  
    }  
    MessageBox.Show (s);  
    ```  
  
    ```cpp  
    int i;  
    String ^ s;
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1->Items->Count-1); i++)  
    {  
       if (checkedListBox1->GetItemChecked(i))  
       {  
          s = String::Concat(s, "Item ", (i+1).ToString(), " = ",  
             checkedListBox1->Item[i]->ToString(), "\n");  
       }  
    }  
    MessageBox::Show(s);  
    ```  
  
## <a name="see-also"></a>请参阅

- [用于列出选项的 Windows 窗体控件](windows-forms-controls-used-to-list-options.md)
