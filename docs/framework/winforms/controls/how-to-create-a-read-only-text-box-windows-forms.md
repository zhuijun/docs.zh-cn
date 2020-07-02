---
title: 如何：创建只读文本框
description: 了解如何将可编辑的 Windows 窗体文本框转换为只读 Windows 窗体文本框。
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 5baa7c66d5f16560a4ea23861d563b099592957f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619359"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>如何：创建只读文本框（Windows 窗体）

可以将可编辑 Windows 窗体文本框转换为只读控件。 例如，文本框可能会显示一个值，该值通常是编辑的，但由于应用程序的状态，它当前可能不存在。

## <a name="to-create-a-read-only-text-box"></a>创建只读文本框

1. 将 <xref:System.Windows.Forms.TextBox> 控件的 <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> 属性设置为 `true` 。 当属性设置为时 `true` ，用户仍可以滚动和突出显示文本框中的文本而不允许更改。 "**复制**" 命令在文本框中起作用，但 "**剪切**" 和 "**粘贴**" 命令不是这样。

    > [!NOTE]
    > <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>属性仅在运行时影响用户交互。 你仍可以通过更改文本框的属性，在运行时以编程方式更改文本框内容 <xref:System.Windows.Forms.TextBox.Text%2A> 。

## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.TextBox>
- [TextBox 控件概述](textbox-control-overview-windows-forms.md)
- [如何：控制 Windows 窗体 TextBox 控件中的插入点](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [如何：使用 Windows 窗体 TextBox 控件创建密码文本框](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [如何：在字符串中添加引号](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [如何：在 Windows 窗体 TextBox 控件中选择文本](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [如何：在 Windows 窗体 TextBox 控件中查看多个行](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox 控件](textbox-control-windows-forms.md)
