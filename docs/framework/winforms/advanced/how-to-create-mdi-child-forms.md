---
title: 如何：创建 MDI 子窗体
description: 了解如何使用 Visual Studio 创建多文档界面（MDI）子窗体，以显示 RichTextBox 控件。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: 7fe5cde342f0f5ee078f888b7492cd4618bea5c4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903176"
---
# <a name="how-to-create-mdi-child-forms"></a>如何：创建 MDI 子窗体

MDI 子窗体是[多文档界面（MDI）应用程序](multiple-document-interface-mdi-applications.md)的基本元素，因为这些形式是用户交互的中心。

在下面的过程中，你将使用 Visual Studio 创建显示控件的 MDI 子窗体，该窗体 <xref:System.Windows.Forms.RichTextBox> 类似于大多数字处理应用程序。 通过将控件替换为 <xref:System.Windows.Forms> 其他控件（如控件或控件的组合）， <xref:System.Windows.Forms.DataGridView> 您可以创建 mdi 子窗口（以及通过扩展的 mdi 应用程序），并且可能会有多种可能性。

## <a name="create-mdi-child-forms"></a>创建 MDI 子窗体

1. 在 Visual Studio 中创建新的 Windows 窗体应用程序项目。 在窗体的 "**属性**" 窗口中，将其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 属性设置为，并将 `true` 其属性设置 `WindowsState` 为 `Maximized` 。

   这将该表单指定为适合子窗口的 MDI 容器。

2. 将 <xref:System.Windows.Forms.MenuStrip> 控件从 `Toolbox` 中拖到窗体上。 将其 `Text` 属性设置为 " **File**"。

3. 单击 " **Items** " 属性旁边的省略号（...），然后单击 "**添加**" 以添加两个子工具栏菜单项。 将 `Text` 这些项的属性设置为 "**新建**" 和 "**窗口**"。

4. 在“解决方案资源管理器”中，右键单击项目，然后选择“添加” > “新项”。

5. 在 "**添加新项**" 对话框中，从 "**模板**" 窗格中选择**Windows 窗体**（在 Visual Basic 或 Visual c # 中）或**Windows 窗体应用程序（.net）** （在 Visual C++ 中）。 在 "**名称**" 框中，将窗体命名为**Form2**。 选择 "**打开**"，将窗体添加到项目。

    > [!NOTE]
    > 在此步骤中创建的 MDI 子窗体是标准的 Windows 窗体。 因此，它具有 <xref:System.Windows.Forms.Form.Opacity%2A> 属性，该属性允许你控制窗体的透明度。 但是，<xref:System.Windows.Forms.Form.Opacity%2A> 属性旨在用于顶级窗口。 不要将其与 MDI 子窗体同时使用，否则可能会引起绘制问题。

     此窗体将作为 MDI 子窗体的模板。

     **Windows 窗体设计器**随即打开，并显示**Form2**。

6. 从 "**工具箱**" 中，将 " **RichTextBox** " 控件拖到窗体上。

7. 在 "**属性**" 窗口中，将 `Anchor` 属性设置为**Top，Left** ，并将 `Dock` 属性设置为 " **Fill**"。

   这导致即使在调整 MDI 子窗体的大小，<xref:System.Windows.Forms.RichTextBox> 控件也会完全填充该窗体的区域。

8. 双击 "**新建**" 菜单项为其创建 <xref:System.Windows.Forms.Control.Click> 事件处理程序。

9. 插入类似于下面的代码，以便在用户单击 "**新建**" 菜单项时创建新的 MDI 子窗体。

   > [!NOTE]
   > 在下面的示例中，事件处理程序处理 `MenuItem2` 的 <xref:System.Windows.Forms.Control.Click> 事件。 请注意，根据您的应用程序体系结构的具体情况，您的**新**菜单项可能不是 `MenuItem2` 。

    ```vb
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click
       Dim NewMDIChild As New Form2()
       'Set the Parent Form of the Child window.
       NewMDIChild.MdiParent = Me
       'Display the new form.
       NewMDIChild.Show()
    End Sub
    ```

    ```csharp
    protected void MDIChildNew_Click(object sender, System.EventArgs e){
       Form2 newMDIChild = new Form2();
       // Set the Parent Form of the Child window.
       newMDIChild.MdiParent = this;
       // Display the new form.
       newMDIChild.Show();
    }
    ```

    ```cpp
    private:
       void menuItem2_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          Form2^ newMDIChild = gcnew Form2();
          // Set the Parent Form of the Child window.
          newMDIChild->MdiParent = this;
          // Display the new form.
          newMDIChild->Show();
       }
    ```

   在 c + + 中，在 Form1 的顶部添加以下 `#include` 指令：

   ```cpp
   #include "Form2.h"
   ```

10. 在 "**属性**" 窗口顶部的下拉列表中，选择与 "**文件**" 菜单条对应的菜单条，并将 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> 属性设置为窗口 <xref:System.Windows.Forms.ToolStripMenuItem> 。

    这使 "**窗口**" 菜单能够维护打开的 MDI 子窗口的列表（活动子窗口旁有一个复选标记）。

11. 按 **F5** 运行该应用程序。 通过从 "**文件**" 菜单中选择 "**新建**"，可以创建新的 MDI 子窗体，它们将在 "**窗口**" 菜单项中保持跟踪。

    > [!NOTE]
    > 当 MDI 子窗体具有一个 <xref:System.Windows.Forms.MainMenu> 组件（通常带有菜单项的菜单结构），而且它在有 <xref:System.Windows.Forms.MainMenu> 组件（通常带有菜单项的菜单结构）的 MDI 父窗体中打开时，如果设置了 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 属性（或 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 属性），这些菜单项就会自动合并。 将两个 <xref:System.Windows.Forms.MainMenu> 组件的 <xref:System.Windows.Forms.MenuItem.MergeType%2A> 属性和子窗体的所有菜单项设置为 <xref:System.Windows.Forms.MenuMerge.MergeItems>。 此外，设置 <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> 属性，以便这两个菜单的菜单项按所需顺序显示。 此外，请记住，关闭 MDI 父窗体时，每个 MDI 子窗体先引发一个 <xref:System.Windows.Forms.Form.Closing> 事件，再引发 MDI 父窗体的 <xref:System.Windows.Forms.Form.Closing> 事件。 取消 MDI 子窗体的 <xref:System.Windows.Forms.Form.Closing> 事件将不会阻止引发 MDI 父窗体的 <xref:System.Windows.Forms.Form.Closing> 事件；但是，MDI 父窗体的 <xref:System.Windows.Forms.Form.Closing> 事件的 <xref:System.ComponentModel.CancelEventArgs> 参数将设置为 `true`。 通过将 <xref:System.ComponentModel.CancelEventArgs> 参数设置为 `false` 可以强制 MDI 父窗体和所有 MDI 子窗体关闭。

## <a name="see-also"></a>另请参阅

- [多文档界面 (MDI) 应用程序](multiple-document-interface-mdi-applications.md)
- [如何：创建 MDI 父窗体](how-to-create-mdi-parent-forms.md)
- [如何：确定活动的 MDI 子窗体](how-to-determine-the-active-mdi-child.md)
- [如何：将数据发送到活动的 MDI 子窗体](how-to-send-data-to-the-active-mdi-child.md)
- [如何：排列 MDI 子窗体](how-to-arrange-mdi-child-forms.md)
