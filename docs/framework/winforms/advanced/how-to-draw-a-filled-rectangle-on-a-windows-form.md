---
title: 如何：在 Windows 窗体上绘制实心矩形
description: 了解如何以编程方式在 Windows 窗体上绘制实心矩形。 还了解如何编译你的代码。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
ms.openlocfilehash: 0ad8ec97000e29b2194a9eda713aa43d5557b44c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621634"
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a>如何：在 Windows 窗体上绘制实心矩形
此示例在窗体上绘制实心矩形。  
  
## <a name="example"></a>示例  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a>编译代码  
 不能在事件处理程序中调用此方法 <xref:System.Windows.Forms.Form.Load> 。 如果窗体调整或被其他窗体遮住，则不会重新绘制所绘制的内容。 若要自动重绘内容，应重写 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。  
  
## <a name="robust-programming"></a>可靠编程  
 应始终对 <xref:System.IDisposable.Dispose%2A> 使用系统资源的任何对象（如 <xref:System.Drawing.Brush> 和对象）调用 <xref:System.Drawing.Graphics> 。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [图形编程入门](getting-started-with-graphics-programming.md)
- [Windows 窗体中的图形和绘制](graphics-and-drawing-in-windows-forms.md)
- [使用笔绘制线条和形状](using-a-pen-to-draw-lines-and-shapes.md)
- [GDI+ 中的画笔和实心形状](brushes-and-filled-shapes-in-gdi.md)
