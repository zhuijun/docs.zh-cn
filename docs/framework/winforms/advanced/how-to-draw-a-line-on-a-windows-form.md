---
title: 如何：在 Windows 窗体上绘制直线
description: 了解如何通过处理 Paint 事件在窗体上绘制线条，然后使用 PaintEventArgs 的 Graphics 属性执行该绘图。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- Graphics.DrawLine
helpviewer_keywords:
- examples [Windows Forms], drawing lines on forms
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- drawing lines
ms.assetid: 55c1dbeb-75d0-430c-9814-a24b8971ad8c
ms.openlocfilehash: c8e92dc265c63413275561d0e2e3aa820eaec724
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621621"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a>如何：在 Windows 窗体上绘制直线
此示例在窗体上绘制线条。 通常，当你在窗体上绘制时，将处理窗体的 <xref:System.Windows.Forms.Control.Paint> 事件，并使用 <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> 的属性执行绘制 <xref:System.Windows.Forms.PaintEventArgs> ，如本示例所示  
  
## <a name="example"></a>示例  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的示例专用于 Windows 窗体，它需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，后者是 <xref:System.Windows.Forms.Control.Paint> 事件处理程序的参数。  
  
## <a name="robust-programming"></a>可靠编程  
 应始终对 <xref:System.IDisposable.Dispose%2A> 使用系统资源的任何对象（如对象）调用 <xref:System.Drawing.Pen> 。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [图形编程入门](getting-started-with-graphics-programming.md)
- [使用笔绘制线条和形状](using-a-pen-to-draw-lines-and-shapes.md)
- [Windows 窗体中的图形和绘制](graphics-and-drawing-in-windows-forms.md)
