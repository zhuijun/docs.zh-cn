---
title: 使用 TextBox 控件创建密码文本框
description: 了解如何新建在用户键入字符串时显示占位符字符的 Windows 窗体文本。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
ms.openlocfilehash: 6d7e61eefa44ce3152aa77e3922bde471a4aeaf3
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904307"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>如何：使用 Windows 窗体 TextBox 控件创建密码文本框

密码框是一个 Windows 窗体文本框，在用户键入字符串时显示占位符字符。

### <a name="to-create-a-password-text-box"></a>创建密码文本框

1. 将 <xref:System.Windows.Forms.TextBox.PasswordChar%2A> 控件的属性设置 <xref:System.Windows.Forms.TextBox> 为特定字符。

    <xref:System.Windows.Forms.TextBox.PasswordChar%2A>属性指定文本框中显示的字符。 例如，如果希望在 "密码" 框中显示星号，请 <xref:System.Windows.Forms.TextBox.PasswordChar%2A> 在 "属性窗口中为属性指定" * "。 然后，无论用户在文本框中键入什么字符，都将显示一个星号。

2. 可有可无设置 <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> 属性。 属性确定在文本框中键入的字符数。 如果超过了最大长度，系统会发出嘟嘟声，文本框不接受任何其他字符。 请注意，你可能不希望这样做，因为密码的最大长度可能会被尝试猜测密码的黑客使用。

    下面的代码示例演示如何初始化一个文本框，该文本框将接受长度最长为14个字符的字符串，并显示星号来替换字符串。 此 `InitializeMyControl` 过程不会自动执行; 必须调用它。

    > [!IMPORTANT]
    > 如果使用 <xref:System.Windows.Forms.TextBox.PasswordChar%2A> 文本框上的属性，则可帮助确保其他人在观察用户输入密码时不能确定用户的密码。 此安全措施不包含任何类型的密码，无论是由于应用程序逻辑造成的，都不会出现任何类型的密码。 由于输入的文本未以任何方式进行加密，因此应将其视为任何其他机密数据。 即使它不是这样，也仍会将密码视为纯文本字符串（除非您已经实现了一些附加的安全措施）。

    ```vb
    Private Sub InitializeMyControl()
       ' Set to no text.
       TextBox1.Text = ""
       ' The password character is an asterisk.
       TextBox1.PasswordChar = "*"
       ' The control will allow no more than 14 characters.
       TextBox1.MaxLength = 14
    End Sub
    ```

    ```csharp
    private void InitializeMyControl()
    {
       // Set to no text.
       textBox1.Text = "";
       // The password character is an asterisk.
       textBox1.PasswordChar = '*';
       // The control will allow no more than 14 characters.
       textBox1.MaxLength = 14;
    }
    ```

    ```cpp
    private:
       void InitializeMyControl()
       {
          // Set to no text.
          textBox1->Text = "";
          // The password character is an asterisk.
          textBox1->PasswordChar = '*';
          // The control will allow no more than 14 characters.
          textBox1->MaxLength = 14;
       }
    ```

## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.TextBox>
- [TextBox 控件概述](textbox-control-overview-windows-forms.md)
- [如何：控制 Windows 窗体 TextBox 控件中的插入点](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [如何：创建只读文本框](how-to-create-a-read-only-text-box-windows-forms.md)
- [如何：在字符串中添加引号](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [如何：在 Windows 窗体 TextBox 控件中选择文本](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [如何：在 Windows 窗体 TextBox 控件中查看多个行](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox 控件](textbox-control-windows-forms.md)
