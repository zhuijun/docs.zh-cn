---
title: 演练：执行拖放操作
description: 了解如何在 Windows 窗体中执行拖放操作，方法是处理一系列事件，最值得注意的是 System.windows.dragdrop.dragenter>、System.windows.dragdrop.dragleave> 和 System.windows.dragdrop.drop> 事件。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 83bfda875e2fdec3981bbcb8f8f7be00db342440
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325824"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>演练：在 Windows 窗体中执行拖放操作
若要在基于 Windows 的应用程序中执行拖放操作，必须处理一系列事件，最值得注意的是 <xref:System.Windows.Forms.Control.DragEnter> 、 <xref:System.Windows.Forms.Control.DragLeave> 和 <xref:System.Windows.Forms.Control.DragDrop> 事件。 通过使用这些事件的事件参数中的可用信息，可以轻松地实现拖放操作。  
  
## <a name="dragging-data"></a>拖动数据  
 所有拖放操作都从拖动开始。 在方法中实现了开始拖动时要收集的数据的功能 <xref:System.Windows.Forms.Control.DoDragDrop%2A> 。  
  
 在下面的示例中，该 <xref:System.Windows.Forms.Control.MouseDown> 事件用于启动拖动操作，因为它是最直观的（在按下鼠标按钮时，大多数拖放操作都将开始）。 但是，请记住，任何事件都可用于启动拖放过程。  
  
> [!NOTE]
> 某些控件具有特定于拖动的自定义事件。 <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.TreeView> 例如，和控件都有一个 <xref:System.Windows.Forms.TreeView.ItemDrag> 事件。  
  
#### <a name="to-start-a-drag-operation"></a>启动拖动操作  
  
1. 在将 <xref:System.Windows.Forms.Control.MouseDown> 开始拖动的控件的事件中，使用 `DoDragDrop` 方法设置要拖动的数据，并允许拖动的效果。 有关详细信息，请参阅 <xref:System.Windows.Forms.DragEventArgs.Data%2A> 和 <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>。  
  
     下面的示例演示如何启动拖动操作。 拖放开始的控件是一个 <xref:System.Windows.Forms.Button> 控件，要拖动的数据是表示控件属性的字符串 <xref:System.Windows.Forms.Control.Text%2A> <xref:System.Windows.Forms.Button> ，而允许的效果可以是复制或移动。  
  
    ```vb  
    Private Sub Button1_MouseDown(ByVal sender As Object, ByVal e As System.Windows.Forms.MouseEventArgs) Handles Button1.MouseDown  
       Button1.DoDragDrop(Button1.Text, DragDropEffects.Copy Or DragDropEffects.Move)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_MouseDown(object sender,
    System.Windows.Forms.MouseEventArgs e)  
    {  
       button1.DoDragDrop(button1.Text, DragDropEffects.Copy |
          DragDropEffects.Move);  
    }  
    ```  
  
    > [!NOTE]
    > 任何数据都可用作方法中的参数 `DoDragDrop` ; 在上面的示例中，使用了 <xref:System.Windows.Forms.Control.Text%2A> 控件的属性 <xref:System.Windows.Forms.Button> （而不是对值进行硬编码或从数据集检索数据），因为该属性与要拖动的位置（ <xref:System.Windows.Forms.Button> 控件）相关。 在将拖放操作合并到基于 Windows 的应用程序中时，请牢记这一点。  
  
 当拖动操作生效时，您可以处理 <xref:System.Windows.Forms.Control.QueryContinueDrag> 事件，该事件将 "询问" 系统的权限才能继续执行拖动操作。 当处理此方法时，它还是调用将对拖动操作产生影响的方法（例如， <xref:System.Windows.Forms.TreeNode> 当光标悬停在控件中时展开控件中的）的适当点 <xref:System.Windows.Forms.TreeView> 。  
  
## <a name="dropping-data"></a>放置数据  
 开始从 Windows 窗体或控件上的某个位置拖动数据后，当然会想要将其放置在某处。 当光标经过为放置数据而进行了正确配置的窗体或控件区域时，会发生改变。 Windows 窗体或控件内的任何区域都可以通过设置 <xref:System.Windows.Forms.Control.AllowDrop%2A> 属性并处理 <xref:System.Windows.Forms.Control.DragEnter> 和事件来接受删除的数据 <xref:System.Windows.Forms.Control.DragDrop> 。  
  
#### <a name="to-perform-a-drop"></a>执行放置  
  
1. 将 <xref:System.Windows.Forms.Control.AllowDrop%2A> 属性设置为 true。  
  
2. 在 `DragEnter` 将发生放置的控件的事件中，确保正在拖动的数据为可接受的类型（在本例中为 <xref:System.Windows.Forms.Control.Text%2A> ）。 然后，该代码设置在将其放到枚举中的某个值时发生的效果 <xref:System.Windows.Forms.DragDropEffects> 。 有关详细信息，请参阅 <xref:System.Windows.Forms.DragEventArgs.Effect%2A>。  
  
    ```vb  
    Private Sub TextBox1_DragEnter(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
         e.Effect = DragDropEffects.Copy  
       Else  
         e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragEnter(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    > [!NOTE]
    > 您可以 <xref:System.Windows.Forms.DataFormats> 通过将自己的对象指定为方法的参数来定义自己的 <xref:System.Object> <xref:System.Windows.Forms.DataObject.SetData%2A> 。 在进行该操作时，请确保指定的对象可序列化。 有关详细信息，请参阅 <xref:System.Runtime.Serialization.ISerializable>。  
  
3. 在 <xref:System.Windows.Forms.Control.DragDrop> 将发生放置的控件的事件中，使用 <xref:System.Windows.Forms.DataObject.GetData%2A> 方法检索要拖动的数据。 有关详细信息，请参阅 <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>。  
  
     在下面的示例中， <xref:System.Windows.Forms.TextBox> 控件是要拖动到的控件（将在其中发生放置）。 该代码将 <xref:System.Windows.Forms.Control.Text%2A> 控件的属性设置 <xref:System.Windows.Forms.TextBox> 为等于正在拖动的数据。  
  
    ```vb  
    Private Sub TextBox1_DragDrop(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragDrop  
       TextBox1.Text = e.Data.GetData(DataFormats.Text).ToString  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragDrop(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       textBox1.Text = e.Data.GetData(DataFormats.Text).ToString();  
    }  
    ```  
  
    > [!NOTE]
    > 此外，还可以使用 <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> 属性，这样，根据拖放操作期间按下的键，会发生某些效果（例如，在按下 CTRL 键时复制拖动数据的标准）。  
  
## <a name="see-also"></a>另请参阅

- [如何：将数据添加到剪贴板](how-to-add-data-to-the-clipboard.md)
- [如何：从剪贴板检索数据](how-to-retrieve-data-from-the-clipboard.md)
- [拖放操作和剪贴板支持](drag-and-drop-operations-and-clipboard-support.md)
