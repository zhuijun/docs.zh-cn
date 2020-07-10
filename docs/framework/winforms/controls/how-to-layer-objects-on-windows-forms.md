---
title: 对对象进行分层
description: 了解如何在 Windows 窗体控件和子窗体上对对象进行分层，以创建更复杂的用户界面。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6269b09c56963fefd500b9e1e6c9d7f51f9619cf
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174505"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>如何：在 Windows 窗体上的层对象

当你创建复杂的用户界面，或使用多个文档界面 (MDI) 窗体时，通常需要将控件和子窗体分层以创建更复杂的用户界面 (UI) 。 若要在组的上下文中移动和跟踪控件和窗口，请处理其*z 顺序*。 Z 顺序是窗体上的控件沿窗体 z 轴的可视化分层 (深度) 。 Z 顺序顶部的窗口与所有其他窗口重叠。 所有其他窗口都与 z 顺序底部的窗口重叠。

## <a name="to-layer-controls-at-design-time"></a>在设计时将控件分层

1. 在 Visual Studio 中，选择要分层的控件。

2. 在 "**格式**" 菜单上，选择 "**顺序**"，然后选择 "**置于顶层**" 或 "置于**底层**"。

## <a name="to-layer-controls-programmatically"></a>以编程方式对控件进行分层

使用 <xref:System.Windows.Forms.Control.BringToFront%2A> 和 <xref:System.Windows.Forms.Control.SendToBack%2A> 方法来操作控件的 z 顺序。

例如，如果 <xref:System.Windows.Forms.TextBox> 控件 `txtFirstName` 位于另一个控件之下，并且你想要将其置于顶层，请使用以下代码：

```vb
txtFirstName.BringToFront()
```

```csharp
txtFirstName.BringToFront();
```

```cpp
txtFirstName->BringToFront();
```

> [!NOTE]
> Windows 窗体支持*控件包含*。 控件包含涉及到在包含控件中放置许多控件，如控件中的多个 <xref:System.Windows.Forms.RadioButton> 控件 <xref:System.Windows.Forms.GroupBox> 。 然后，可以将控件分层到包含控件中。 移动组框也将移动控件，因为这些控件包含在其中。

## <a name="see-also"></a>另请参阅

- [Windows 窗体控件](index.md)
- [标记单个 Windows 窗体控件并提供它们的快捷方式](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [在 Windows 窗体上使用的控件](controls-to-use-on-windows-forms.md)
- [根据功能列出的 Windows 窗体控件](windows-forms-controls-by-function.md)
