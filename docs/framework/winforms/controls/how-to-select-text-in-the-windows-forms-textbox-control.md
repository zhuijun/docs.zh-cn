---
title: 在 TextBox 控件中选择文本
description: 了解如何在 Windows 窗体 TextBox 控件中以编程方式选择文本。 还了解如何以视觉方式向读者提醒找到的字符串位置。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], selecting text programmatically
- text boxes [Windows Forms], selecting text programmatically
- text [Windows Forms], selecting in text boxes programmatically
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
ms.openlocfilehash: b8fdaff76461c4d6766dfc6afaef5e814d982834
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621556"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a>如何：在 Windows 窗体 TextBox 控件中选择文本
可以在 Windows 窗体控件中以编程方式选择文本 <xref:System.Windows.Forms.TextBox> 。 例如，如果您创建一个函数，用于在文本中搜索特定字符串，则可以选择该文本以直观地向读者提醒找到的字符串位置。  
  
### <a name="to-select-text-programmatically"></a>以编程方式选择文本  
  
1. 将 <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> 属性设置为要选择的文本的开头。  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>属性是一个数字，用于指示文本字符串中的插入点，0表示最左侧的位置。 如果 <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> 将属性设置为等于或大于文本框中字符数的值，则会将插入点放在最后一个字符之后。  
  
2. 将 <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> 属性设置为要选择的文本长度。  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>属性是用于设置插入点宽度的数值。 如果将设置 <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> 为大于0的数字，则会从当前插入点开始选择要选择的字符数。  
  
3. 可有可无通过属性访问选定的文本 <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> 。  
  
     下面的代码在控件的事件发生时选择文本框的内容 <xref:System.Windows.Forms.Control.Enter> 。 此示例将检查文本框是否具有 <xref:System.Windows.Forms.TextBox.Text%2A> 不为或空字符串的属性的值 `null` 。 当文本框接收到焦点时，文本框中的当前文本处于选中状态。 `TextBox1_Enter`事件处理程序必须绑定到控件; 有关详细信息，请参阅[如何：在运行时为 Windows 窗体创建事件处理程序](../how-to-create-event-handlers-at-run-time-for-windows-forms.md)。  
  
     若要测试此示例，请按 Tab 键，直到文本框具有焦点。 如果在文本框中单击，则不会选择文本。  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       If (Not String.IsNullOrEmpty(TextBox1.Text)) Then  
          TextBox1.SelectionStart = 0  
          TextBox1.SelectionLength = TextBox1.Text.Length  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(object sender, System.EventArgs e){  
       if (!String.IsNullOrEmpty(textBox1.Text))  
       {  
          textBox1.SelectionStart = 0;  
          textBox1.SelectionLength = textBox1.Text.Length;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^ sender,  
          System::EventArgs ^ e) {  
       if (!System::String::IsNullOrEmpty(textBox1->Text))  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = textBox1->Text->Length;  
       }  
    }  
    ```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.TextBox>
- [TextBox 控件概述](textbox-control-overview-windows-forms.md)
- [如何：控制 Windows 窗体 TextBox 控件中的插入点](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [如何：使用 Windows 窗体 TextBox 控件创建密码文本框](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [如何：创建只读文本框](how-to-create-a-read-only-text-box-windows-forms.md)
- [如何：在字符串中添加引号](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [如何：在 Windows 窗体 TextBox 控件中查看多个行](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox 控件](textbox-control-windows-forms.md)
