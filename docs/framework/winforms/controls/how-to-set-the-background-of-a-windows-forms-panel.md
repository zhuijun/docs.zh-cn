---
title: 设置 Panel 控件的背景
description: 了解如何使用设计器设置 Windows 窗体面板的背景色和背景图像。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: 096cbd8d-45cc-47b8-b1ef-a27f60ea8be0
ms.openlocfilehash: 109ff6184de9c79d1576207bbeb29ad939670b6f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173375"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>如何：设置 Windows 窗体面板的背景
Windows 窗体 <xref:System.Windows.Forms.Panel> 控件可以同时显示背景色和背景图像。 <xref:System.Windows.Forms.Control.BackColor%2A>属性为包含的控件（如标签和单选按钮）设置背景色。 如果 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 未设置该属性，则 <xref:System.Windows.Forms.Control.BackColor%2A> 所选内容将填充整个面板。 如果 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 设置了属性，则图像将显示在包含的控件后面。  
  
### <a name="to-set-the-background-programmatically"></a>以编程方式设置背景  
  
1. 将面板的 <xref:System.Windows.Forms.Control.BackColor%2A> 属性设置为类型的值 <xref:System.Drawing.Color?displayProperty=nameWithType> 。  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. 使用类的方法设置面板的 <xref:System.Windows.Forms.Control.BackgroundImage%2A> 属性 <xref:System.Drawing.Image.FromFile%2A> <xref:System.Drawing.Image?displayProperty=nameWithType> 。  
  
    ```vb  
    ' You should replace the bolded image
    ' in the sample below with an image of your own choosing.  
    Panel1.BackgroundImage = Image.FromFile _  
        (System.Environment.GetFolderPath _  
        (System.Environment.SpecialFolder.Personal) _  
        & "\Image.gif")  
    ```  
  
    ```csharp  
    // You should replace the bolded image
    // in the sample below with an image of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    panel1.BackgroundImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // You should replace the bolded image
    // in the sample below with an image of your own choosing.  
    panel1->BackgroundImage = Image::FromFile(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Panel 控件](panel-control-windows-forms.md)
- [Panel 控件概述](panel-control-overview-windows-forms.md)
