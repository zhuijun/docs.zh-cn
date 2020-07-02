---
title: 设置控件显示的文本
description: 了解如何设置 Windows 窗体控件显示的文本。 使用 Text 属性设置或返回文本，或使用 Font 属性更改字体。
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
ms.openlocfilehash: 35bae5830bfee8ab91f7b6c7b9dcc6d6b8db00ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622843"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>如何：设置 Windows 窗体控件显示的文本

Windows 窗体控件通常会显示一些与控件的主要功能相关的文本。 例如， <xref:System.Windows.Forms.Button> 控件通常会显示一个标题，指示在单击该按钮时要执行的操作。 对于所有控件而言，都可通过使用 <xref:System.Windows.Forms.Control.Text%2A> 属性来设置或返回文本。 可以使用 <xref:System.Windows.Forms.Control.Font%2A> 属性更改字体。

还可以使用[设计器](#designer)设置文本。

## <a name="programmatic"></a>编程

1. 将 <xref:System.Windows.Forms.Control.Text%2A> 属性设置为字符串。

   若要创建带下划线的访问键，请在将作为访问密钥的字母前包含一个 "与" 符号（&）。

2. 将 <xref:System.Windows.Forms.Control.Font%2A> 属性设置为类型 <xref:System.Drawing.Font> 的对象。

    ```vb
    Button1.Text = "Click here to save changes"
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)
    ```

    ```csharp
    button1.Text = "Click here to save changes";
    button1.Font = new Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point);
    ```

    ```cpp
    button1->Text = "Click here to save changes";
    button1->Font = new System::Drawing::Font("Arial", 10, FontStyle::Bold, GraphicsUnit::Point);
    ```

    > [!NOTE]
    > 可使用转义符来显示用户界面元素中的特殊字符，通常对这些元素（如菜单项）有着不同的解释。 例如，下面的代码行将菜单项的文本设置为 "现在为完全不同的内容 &"：

    ```vb
    MPMenuItem.Text = "&& Now For Something Completely Different"
    ```

    ```csharp
    mpMenuItem.Text = "&& Now For Something Completely Different";
    ```

    ```cpp
    mpMenuItem->Text = "&& Now For Something Completely Different";
    ```

## <a name="designer"></a>设计器

1. 在 Visual Studio 的 "**属性**" 窗口中，将控件的 " **Text** " 属性设置为相应的字符串。

   若要创建带下划线的快捷键，请在将作为快捷键的字母前包含 "and" 符（&）。

2. 在 "**属性**" 窗口中，选择 "字体" 属性旁边的省略号按钮（ ![ 省略号按钮（...），位于 Visual Studio 属性窗口中 ](./media/visual-studio-ellipsis-button.png) ）。 **Font**

   在 "标准字体" 对话框中，选择所需的字体、字体样式、大小、效果（如删除线或下划线）和脚本。

## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [如何：创建 Windows 窗体控件的访问键](how-to-create-access-keys-for-windows-forms-controls.md)
- [如何：响应 Windows 窗体按钮的单击](how-to-respond-to-windows-forms-button-clicks.md)
