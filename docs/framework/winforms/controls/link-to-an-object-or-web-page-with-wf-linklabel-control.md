---
title: 使用 LinkLabel 控件链接到对象或网页
description: 了解如何使用 Windows 窗体 LinkLabel 控件创建指向对象或网页的 Web 样式链接。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Windows Forms, linking to objects
- Web page link control
- linking [Windows Forms], to other forms
- Windows Forms, linking to Web pages
- links [Windows Forms], to other forms
- LinkLabel control [Windows Forms], linking to object or Web page
- LinkLabel control [Windows Forms], examples
ms.assetid: 6c91c975-3cb7-4504-82f0-fc6255f8fb85
ms.openlocfilehash: a5fb1c03e9a8d82fe77f4133ba04c42114787d23
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618307"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a>如何：使用 Windows 窗体 LinkLabel 控件链接到对象或 Web 页面

Windows 窗体 <xref:System.Windows.Forms.LinkLabel> 控件允许您在窗体上创建 Web 样式链接。 单击此链接后，可以更改其颜色以指示该链接已访问。 有关更改颜色的详细信息，请参阅[如何：更改 Windows 窗体 LinkLabel 控件的外观](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)。

## <a name="linking-to-another-form"></a>链接到其他窗体

#### <a name="to-link-to-another-form-with-a-linklabel-control"></a>使用 LinkLabel 控件链接到其他窗体

1. 将 <xref:System.Windows.Forms.LinkLabel.Text%2A> 属性设置为相应的标题。

2. 设置 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 属性以确定显示为链接的标题部分。 它的显示方式取决于链接标签与外观相关的属性。 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>该值由一个 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 对象表示，其中包含两个数字、起始字符位置和字符数。 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>可以在属性窗口中或在代码中设置属性，其方式类似于以下形式：

    ```vb
    ' In this code example, the link area has been set to begin
    ' at the first character and extend for eight characters.
    ' You may need to modify this based on the text entered in Step 1.
    LinkLabel1.LinkArea = New LinkArea(0, 8)
    ```

    ```csharp
    // In this code example, the link area has been set to begin
    // at the first character and extend for eight characters.
    // You may need to modify this based on the text entered in Step 1.
    linkLabel1.LinkArea = new LinkArea(0,8);
    ```

    ```cpp
    // In this code example, the link area has been set to begin
    // at the first character and extend for eight characters.
    // You may need to modify this based on the text entered in Step 1.
    linkLabel1->LinkArea = LinkArea(0,8);
    ```

3. 在 <xref:System.Windows.Forms.LinkLabel.LinkClicked> 事件处理程序中，调用 <xref:System.Windows.Forms.Form.Show%2A> 方法以在项目中打开另一个窗体，并 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> 将属性设置为 `true` 。

    > [!NOTE]
    > 类的实例 <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> 具有对 <xref:System.Windows.Forms.LinkLabel> 被单击的控件的引用，因此不需要强制转换 `sender` 对象。

    ```vb
    Protected Sub LinkLabel1_LinkClicked(ByVal Sender As System.Object, _
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _
       Handles LinkLabel1.LinkClicked
       ' Show another form.
       Dim f2 As New Form()
       f2.Show
       LinkLabel1.LinkVisited = True
    End Sub
    ```

    ```csharp
    protected void linkLabel1_LinkClicked(object sender, System. Windows.Forms.LinkLabelLinkClickedEventArgs e)
    {
       // Show another form.
       Form f2 = new Form();
       f2.Show();
       linkLabel1.LinkVisited = true;
    }
    ```

    ```cpp
    private:
       void linkLabel1_LinkClicked(System::Object ^  sender,
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)
       {
          // Show another form.
          Form ^ f2 = new Form();
          f2->Show();
          linkLabel1->LinkVisited = true;
       }
    ```

## <a name="linking-to-a-web-page"></a>链接到网页

该 <xref:System.Windows.Forms.LinkLabel> 控件还可用于使用默认浏览器显示网页。

#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a>使用 LinkLabel 控件启动 Internet Explorer 并链接到网页

1. 将 <xref:System.Windows.Forms.LinkLabel.Text%2A> 属性设置为相应的标题。

2. 设置 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 属性以确定显示为链接的标题部分。

3. 在 <xref:System.Windows.Forms.LinkLabel.LinkClicked> 事件处理程序中，在异常处理块的中间调用将属性设置为的第二个过程， <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> `true` 并使用 <xref:System.Diagnostics.Process.Start%2A> 方法通过 URL 启动默认浏览器。 若要使用 <xref:System.Diagnostics.Process.Start%2A> 方法，您需要添加对 <xref:System.Diagnostics?displayProperty=nameWithType> 命名空间的引用。

    > [!IMPORTANT]
    > 如果下面的代码在部分信任环境（如共享驱动器）上运行，则调用方法时 JIT 编译器会失败 `VisitLink` 。 `System.Diagnostics.Process.Start`语句导致链接请求失败。 通过在调用方法时捕获异常 `VisitLink` ，下面的代码确保了如果 JIT 编译器失败，则会适当地处理错误。

    ```vb
    Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, _
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _
       Handles LinkLabel1.LinkClicked
       Try
          VisitLink()
       Catch ex As Exception
          ' The error message
          MessageBox.Show("Unable to open link that was clicked.")
       End Try
    End Sub

    Sub VisitLink()
       ' Change the color of the link text by setting LinkVisited
       ' to True.
       LinkLabel1.LinkVisited = True
       ' Call the Process.Start method to open the default browser
       ' with a URL:
       System.Diagnostics.Process.Start("http://www.microsoft.com")
    End Sub
    ```

    ```csharp
    private void linkLabel1_LinkClicked(object sender, System.Windows.Forms.LinkLabelLinkClickedEventArgs e)
    {
       try
       {
          VisitLink();
       }
       catch (Exception ex )
       {
          MessageBox.Show("Unable to open link that was clicked.");
       }
    }

    private void VisitLink()
    {
       // Change the color of the link text by setting LinkVisited
       // to true.
       linkLabel1.LinkVisited = true;
       //Call the Process.Start method to open the default browser
       //with a URL:
       System.Diagnostics.Process.Start("http://www.microsoft.com");
    }
    ```

    ```cpp
    private:
       void linkLabel1_LinkClicked(System::Object ^  sender,
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)
       {
          try
          {
             VisitLink();
          }
          catch (Exception ^ ex)
          {
             MessageBox::Show("Unable to open link that was clicked.");
          }
       }
    private:
       void VisitLink()
       {
          // Change the color of the link text by setting LinkVisited
          // to true.
          linkLabel1->LinkVisited = true;
          // Call the Process.Start method to open the default browser
          // with a URL:
          System::Diagnostics::Process::Start("http://www.microsoft.com");
       }
    ```

## <a name="see-also"></a>请参阅

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- [LinkLabel 控件概述](linklabel-control-overview-windows-forms.md)
- [如何：更改 Windows 窗体 LinkLabel 控件的外观](how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
- [LinkLabel 控件](linklabel-control-windows-forms.md)
