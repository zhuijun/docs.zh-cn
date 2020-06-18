---
title: 如何：在字符串中添加引号
description: 了解如何在文本字符串中放置引号。 另外，了解如何将引号字段用作常量。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
ms.openlocfilehash: 08a3e2ab5662cbbf7825890ab430fddcd7b4a9ce
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903618"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a>如何：在字符串中放置引号（Windows 窗体）
有时可能需要将引号（“”）放入文本字符串中。 例如：  
  
 她说：“该好好款待你了！”  
  
 作为替代方法，还可以将 <xref:Microsoft.VisualBasic.ControlChars.Quote> 字段用作常量。  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a>在代码中的字符串内放置引号  
  
1. 在 Visual Basic 中，在行中插入两个用引号引起来的引号。 在 Visual c # 和 Visual C++ 中，插入转义序列 \\ "作为嵌入的引号。 例如，若要创建前面提到的字符串，请使用下面的代码。  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     \- 或 -  
  
2. 插入 ASCII 字符或 Unicode 字符表示引号。 在 Visual Basic 中，使用 ASCII 字符（34）。 在 Visual c # 中，使用 Unicode 字符（\u0022）。  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    > 在本示例中，不能使用 \u0022，因为不能使用指定基本字符集中字符的通用字符名。 否则，将产生 C3851。 有关详细信息，请参阅[编译器错误 C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851)。  
  
     \- 或 -  
  
3. 还可以为该字符定义一个常数，然后在需要时使用。  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.TextBox>
- <xref:Microsoft.VisualBasic.ControlChars.Quote>
- [TextBox 控件概述](textbox-control-overview-windows-forms.md)
- [如何：控制 Windows 窗体 TextBox 控件中的插入点](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [如何：使用 Windows 窗体 TextBox 控件创建密码文本框](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [如何：创建只读文本框](how-to-create-a-read-only-text-box-windows-forms.md)
- [如何：在 Windows 窗体 TextBox 控件中选择文本](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [如何：在 Windows 窗体 TextBox 控件中查看多个行](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox 控件](textbox-control-windows-forms.md)
