---
title: 在 TextBox 控件中查看多行
description: 了解如何通过设置 "多行"、"换行" 和 "滚动条" 属性，在 "Windows 窗体 TextBox" 控件中查看多行。
ms.date: 03/30/2017
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
ms.openlocfilehash: e40d720bcd56366f4f06bfe2e2d347aaf9aa9d6c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174466"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>如何：在 Windows 窗体 TextBox 控件中查看多个行
默认情况下，Windows 窗体 <xref:System.Windows.Forms.TextBox> 控件显示单行文本，而不显示滚动条。 如果文本长度超过可用空间，则仅部分文本可见。 可以通过将 <xref:System.Windows.Forms.TextBox.Multiline%2A> 、 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 和 <xref:System.Windows.Forms.TextBox.ScrollBars%2A> 属性设置为合适的值来更改此默认行为。  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>在 TextBox 控件中显示回车符  
  
- 若要在多行中显示回车符 <xref:System.Windows.Forms.TextBox> ，请使用 <xref:System.Environment.NewLine%2A> 属性。  
  
     请注意， () 的转义符解释 \\ 是特定于语言的。 Visual Basic `Chr$(13) & Chr$(10)` 用于回车符和换行符的组合。  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>在 TextBox 控件中查看多行  
  
1. 将 <xref:System.Windows.Forms.TextBox.Multiline%2A> 属性设置为 `true`。 如果 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> `true` 默认)  (，则控件中的文本将显示为一个或多个段落; 否则，它将显示为一个列表，在此列表中，可能会在控件的边缘剪裁一些行。  
  
2. 将 <xref:System.Windows.Forms.TextBox.ScrollBars%2A> 属性设置为适当的值。  
  
    |值|说明|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|如果文本将是几乎始终适合控件的段落，请使用此值。 如果文本太长而无法同时显示，用户可以使用鼠标指针在控件内移动。|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|如果要显示行列表，则使用此值，其中某些行的长度可能超过控件的宽度 <xref:System.Windows.Forms.TextBox> 。|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|如果列表的长度可能超过控件的高度，则使用此值。|  
  
3. 将 <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> 属性设置为适当的值。  
  
    |值|说明|  
    |-----------|-----------------|  
    |`false`|控件中的文本不会自动换行，因此它将向右滚动，直至到达换行符。 如果选择了 <xref:System.Windows.Forms.ScrollBars.Horizontal> "滚动条" 或上方，则使用此值 <xref:System.Windows.Forms.ScrollBars.Both> 。|  
    |`true`（默认值）|不会显示水平滚动条。 如果选择了 <xref:System.Windows.Forms.ScrollBars.Vertical> "滚动条" 或上方，则使用此值 <xref:System.Windows.Forms.ScrollBars.None> 来显示一个或多个段落。|  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.TextBox>
- [TextBox 控件概述](textbox-control-overview-windows-forms.md)
- [如何：控制 Windows 窗体 TextBox 控件中的插入点](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [如何：使用 Windows 窗体 TextBox 控件创建密码文本框](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [如何：创建只读文本框](how-to-create-a-read-only-text-box-windows-forms.md)
- [如何：在字符串中添加引号](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [如何：在 Windows 窗体 TextBox 控件中选择文本](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [TextBox 控件](textbox-control-windows-forms.md)
