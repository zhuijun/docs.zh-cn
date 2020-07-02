---
title: 响应按钮单击
description: 了解如何响应 Windows 窗体按钮单击。 Windows 窗体按钮控件的最基本用法是在单击按钮时运行一些代码。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], responding to Click events
- events [Windows Forms], Click events
- Click event [Windows Forms], Button control
- MouseDown event
- Button control [Windows Forms], click response
- double-clicks
- examples [Windows Forms], controls
- Click event [Windows Forms], responding to
ms.assetid: 7a4951bd-369c-4662-b246-28ad83eda484
ms.openlocfilehash: 5c458d56dbd6f1cab8e88bdbb86ede958367e5c4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619723"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>如何：响应 Windows 窗体按钮的单击
Windows 窗体控件的最基本用途 <xref:System.Windows.Forms.Button> 是在单击按钮时运行一些代码。  
  
 单击 <xref:System.Windows.Forms.Button> 控件还会生成一些其他事件，例如 <xref:System.Windows.Forms.Control.MouseEnter> 、 <xref:System.Windows.Forms.Control.MouseDown> 和 <xref:System.Windows.Forms.Control.MouseUp> 事件。 如果要为这些相关事件附加事件处理程序，请确保它们的操作不会发生冲突。 例如，如果单击该按钮会清除用户在文本框中键入的信息，则将鼠标指针暂停在按钮上不会显示工具提示，而不会显示现在不存在的信息。  
  
 如果用户尝试双击 <xref:System.Windows.Forms.Button> 控件，则每次单击都将单独处理; 也就是说，控件不支持双击事件。  
  
### <a name="to-respond-to-a-button-click"></a>响应按钮单击  
  
- 在按钮的 " `Click` <xref:System.EventHandler> 编写代码" 中，运行。 `Button1_Click`必须绑定到控件。 有关详细信息，请参阅[如何：在运行时为 Windows 窗体创建事件处理程序](../how-to-create-event-handlers-at-run-time-for-windows-forms.md)。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       MessageBox.Show("Button1 was clicked")  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       MessageBox.Show("button1 was clicked");  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          MessageBox::Show("button1 was clicked");  
       }  
    ```  
  
## <a name="see-also"></a>请参阅

- [Button 控件概述](button-control-overview-windows-forms.md)
- [选择 Windows 窗体 Button 控件的方法](ways-to-select-a-windows-forms-button-control.md)
- [Button 控件](button-control-windows-forms.md)
