---
title: 添加控件
description: 了解如何在 Windows 窗体上绘制控件。 控件是窗体上的一个组件，可用于显示信息或接受用户输入。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: d9ab0d78fa0153cce20fb17d22f6e9e781229ece
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325878"
---
# <a name="how-to-add-controls-to-windows-forms"></a>如何：向 Windows 窗体添加控件

大多数窗体都是通过将控件添加到窗体的图面来定义用户界面（UI）而设计的。 *控件*是窗体上用于显示信息或接受用户输入的组件。 有关控件的详细信息，请参阅[Windows 窗体控件](index.md)。

## <a name="to-draw-a-control-on-a-form"></a>在窗体上绘制控件

1. 打开窗体。 有关详细信息，请参阅[如何：在设计器中显示 Windows 窗体](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))。

2. 在 "**工具箱**" 中，单击要添加到窗体中的控件。

3. 在窗体上，单击要放置控件的左上角的位置，然后拖动到控件右下角所处的位置。

    控件将添加到具有指定位置和大小的窗体中。

    > [!NOTE]
    > 每个控件都定义了默认大小。 您可以通过将控件从 "**工具箱**" 拖到窗体上，将控件添加到控件的默认大小。

## <a name="to-drag-a-control-to-a-form"></a>将控件拖动到窗体

1. 打开窗体。 有关详细信息，请参阅[如何：在设计器中显示 Windows 窗体](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))。

2. 在 "**工具箱**" 中，单击所需的控件并将其拖到窗体上。

    控件将添加到窗体中指定位置的默认大小。

    > [!NOTE]
    > 您可以双击**工具箱**中的控件，将其以其默认大小添加到窗体的左上角。

    您还可以在运行时将控件动态添加到窗体中。 在下面的代码示例中， <xref:System.Windows.Forms.TextBox> 当单击控件时，控件将添加到窗体中 <xref:System.Windows.Forms.Button> 。

    > [!NOTE]
    > 下面的过程要求存在具有**按钮**控件的窗体 `Button1` 。

## <a name="to-add-a-control-to-a-form-programmatically"></a>以编程方式将控件添加到窗体

1. 在处理 `Click` 窗体的类中的按钮事件的方法中，插入类似于下面的代码以添加对控件变量的引用、设置控件的 `Location` ，然后添加控件。

    ```vb
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
       Dim MyText As New TextBox()
       MyText.Location = New Point(25, 25)
       Me.Controls.Add(MyText)
    End Sub
    ```

    ```csharp
    private void button1_Click(object sender, System.EventArgs e)
    {
       TextBox myText = new TextBox();
       myText.Location = new Point(25,25);
       this.Controls.Add (myText);
    }
    ```

    ```cpp
    private:
      System::Void button1_Click(System::Object ^  sender,
        System::EventArgs ^  e)
      {
        TextBox ^ myText = gcnew TextBox();
        myText->Location = Point(25,25);
        this->Controls->Add(myText);
      }
    ```

    > [!NOTE]
    > 你还可以添加代码以初始化控件的其他属性。

    > [!IMPORTANT]
    > 你可能会通过引用恶意网络来使你的本地计算机遭受网络安全风险 `UserControl` 。 这只是在恶意用户创建有破坏性的自定义控件时，然后错误地将其添加到项目中时需要注意的问题。

## <a name="see-also"></a>另请参阅

- [Windows 窗体控件](index.md)
- [如何：重设 Windows 窗体上控件的大小](how-to-resize-controls-on-windows-forms.md)
- [如何：设置 Windows 窗体控件所显示的文本](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [在 Windows 窗体上使用的控件](controls-to-use-on-windows-forms.md)
