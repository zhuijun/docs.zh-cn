---
title: 设置控件的 tab 键顺序
description: 了解如何设置 Windows 窗体上的控件的 tab 键顺序。 使用 Visual Studio 设置 tab 键顺序，或在属性窗口中使用 TabIndex 属性。
ms.date: 03/30/2017
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d16da1ac73cc030b92bb36c4bfa3a79985339bf
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903350"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>如何：在 Windows 窗体上设置 tab 键顺序

Tab 键顺序是用户通过按 Tab 键将焦点从一个控件移动到另一个控件的顺序。 每个窗体都具有自己的 tab 键顺序。 默认情况下，tab 键顺序与您创建控件的顺序相同。 Tab 顺序编号从0开始。

## <a name="to-set-the-tab-order-of-a-control"></a>设置控件的 tab 键顺序

1. 在 Visual Studio 的 "**视图**" 菜单上，选择 **"Tab 键顺序**"。

   这会激活窗体上的 tab 键顺序选择模式。 <xref:System.Windows.Forms.Control.TabIndex%2A>每个控件的左上角会出现一个数字（表示属性）。

2. 按顺序单击控件以建立所需的 tab 键顺序。

   > [!NOTE]
   > 控件在 tab 键顺序中的位置可设置为大于或等于0的任何值。 发生重复时，将对两个控件的 z 顺序进行计算，并使控件位于顶部。 （Z 顺序是窗体上的控件沿窗体的 z 轴 [深度] 的可视化分层。 Z 顺序确定哪些控件位于其他控件前面。）有关 z 顺序的详细信息，请参阅[Windows 窗体上的分层对象](how-to-layer-objects-on-windows-forms.md)。

3. 完成后，再次选择 "**视图**" 菜单上的 **"tab 键顺序**"，以退出 tab 键顺序模式。

   > [!NOTE]
   > 无法获得焦点的控件以及禁用和不可见控件都没有 <xref:System.Windows.Forms.Control.TabIndex%2A> 属性，并且不包含在 tab 键顺序中。 当用户按 Tab 键时，将跳过这些控件。

或者，可以使用属性在属性窗口中设置 tab 键顺序 <xref:System.Windows.Forms.Control.TabIndex%2A> 。 <xref:System.Windows.Forms.Control.TabIndex%2A>控件的属性确定它在 tab 键顺序中的位置。 默认情况下，绘制的第一个控件的 <xref:System.Windows.Forms.Control.TabIndex%2A> 值为0，第二个控件的值为 <xref:System.Windows.Forms.Control.TabIndex%2A> 1，依此类推。

此外，默认情况下， <xref:System.Windows.Forms.GroupBox> 控件的 <xref:System.Windows.Forms.Control.TabIndex%2A> 值为整数。 <xref:System.Windows.Forms.GroupBox>控件本身不能在运行时具有焦点。 因此，中的每个控件 <xref:System.Windows.Forms.GroupBox> 都具有其自己的十进制 <xref:System.Windows.Forms.Control.TabIndex%2A> 值（从0开始）。 当然，随着 <xref:System.Windows.Forms.Control.TabIndex%2A> <xref:System.Windows.Forms.GroupBox> 控件的增加，其中的控件将相应递增。 如果更改了 <xref:System.Windows.Forms.Control.TabIndex%2A> 5 到6之间的值，则 <xref:System.Windows.Forms.Control.TabIndex%2A> 该组中第一个控件的值将自动更改为6.0，依此类推。

最后，可以按 tab 键顺序跳过窗体上的多个控件。 通常，在运行时连续按 Tab 会按 tab 键顺序选择每个控件。 通过关闭 <xref:System.Windows.Forms.Control.TabStop%2A> 属性，可以使控件按窗体的 tab 键顺序传递。

## <a name="to-remove-a-control-from-the-tab-order"></a>从 tab 键顺序中删除控件

<xref:System.Windows.Forms.Control.TabStop%2A>在 "**属性**" 窗口中，将控件的属性设置为**false** 。

一个控件 <xref:System.Windows.Forms.Control.TabStop%2A> ，其属性已设置为 `false` 仍保持其在 tab 键顺序中的位置，即使当你使用 tab 键在控件之间进行切换时，也会跳过控件。

> [!NOTE]
> 单选按钮组在运行时具有单个制表位。 选定的按钮（即，其 <xref:System.Windows.Forms.RadioButton.Checked%2A> 属性设置为的按钮）的 `true` <xref:System.Windows.Forms.Control.TabStop%2A> 属性自动设置为 `true` ，而其他按钮的 <xref:System.Windows.Forms.Control.TabStop%2A> 属性设置为 `false` 。 有关分组控件的详细信息 <xref:System.Windows.Forms.RadioButton> ，请参阅将[Windows 窗体单选按钮控件分组为一个集](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)。

## <a name="see-also"></a>另请参阅

- [Windows 窗体控件](index.md)
- [在 Windows 窗体上使用的控件](controls-to-use-on-windows-forms.md)
- [根据功能列出的 Windows 窗体控件](windows-forms-controls-by-function.md)
