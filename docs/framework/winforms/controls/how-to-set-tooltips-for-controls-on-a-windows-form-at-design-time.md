---
title: 如何：在设计时为 Windows 窗体上的控件设置 ToolTip
description: 了解如何在 Visual Studio 中以编程方式或在 Windows 窗体设计器中为控件设置工具提示。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 15134b38d11de30d0e6a2f998f6ea266affc40d7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325980"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>如何：在设计时在 Windows 窗体上设置控件的工具提示

可以 <xref:System.Windows.Forms.ToolTip> 在代码中或在 Visual Studio 的 Windows 窗体设计器中设置字符串。 有关组件的详细信息 <xref:System.Windows.Forms.ToolTip> ，请参阅[ToolTip 组件概述](tooltip-component-overview-windows-forms.md)。

## <a name="set-a-tooltip-programmatically"></a>以编程方式设置工具提示

1. 添加将显示工具提示的控件。

2. 使用 <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> 组件的方法 <xref:System.Windows.Forms.ToolTip> 。

    ```vb
    ' In this example, Button1 is the control to display the ToolTip.
    ToolTip1.SetToolTip(Button1, "Save changes")
    ```

    ```csharp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1.SetToolTip(button1, "Save changes");
    ```

    ```cpp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1->SetToolTip(button1, "Save changes");
    ```

## <a name="set-a-tooltip-in-the-designer"></a>在设计器中设置工具提示

1. 在 Visual Studio 中，将 <xref:System.Windows.Forms.ToolTip> 组件添加到窗体。

2. 选择将显示工具提示的控件，或将其添加到窗体中。

3. 在 "**属性**" 窗口中，将 " **ToolTip1 上的工具提示**" 设置为适当的文本字符串。

### <a name="to-remove-a-tooltip-programmatically"></a>以编程方式删除工具提示

1. 使用 <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> 组件的方法 <xref:System.Windows.Forms.ToolTip> 。

    ```vb
    ' In this example, Button1 is the control displaying the ToolTip.
    ToolTip1.SetToolTip(Button1, Nothing)
    ```

    ```csharp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1.SetToolTip(button1, null);
    ```

    ```cpp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1->SetToolTip(button1, NULL);
    ```

## <a name="remove-a-tooltip-in-the-designer"></a>在设计器中删除工具提示

1. 在 Visual Studio 中，选择显示工具提示的控件。

2. 在 "**属性**" 窗口中，删除**ToolTip1 上的工具提示**中的文本。

## <a name="see-also"></a>另请参阅

- [ToolTip 组件概述](tooltip-component-overview-windows-forms.md)
- [如何：更改 Windows 窗体 ToolTip 组件的延迟](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [ToolTip 组件](tooltip-component-windows-forms.md)
