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
# <a name="how-to-draw-a-line-on-a-windows-form"></a><span data-ttu-id="e1d14-103">如何：在 Windows 窗体上绘制直线</span><span class="sxs-lookup"><span data-stu-id="e1d14-103">How to: Draw a Line on a Windows Form</span></span>
<span data-ttu-id="e1d14-104">此示例在窗体上绘制线条。</span><span class="sxs-lookup"><span data-stu-id="e1d14-104">This example draws a line on a form.</span></span> <span data-ttu-id="e1d14-105">通常，当你在窗体上绘制时，将处理窗体的 <xref:System.Windows.Forms.Control.Paint> 事件，并使用 <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> 的属性执行绘制 <xref:System.Windows.Forms.PaintEventArgs> ，如本示例所示</span><span class="sxs-lookup"><span data-stu-id="e1d14-105">Typically, when you draw on a form, you handle the form’s  <xref:System.Windows.Forms.Control.Paint> event and perform the drawing using the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.PaintEventArgs>, as shown in this example</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1d14-106">示例</span><span class="sxs-lookup"><span data-stu-id="e1d14-106">Example</span></span>  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e1d14-107">编译代码</span><span class="sxs-lookup"><span data-stu-id="e1d14-107">Compiling the Code</span></span>  
 <span data-ttu-id="e1d14-108">前面的示例专用于 Windows 窗体，它需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，后者是 <xref:System.Windows.Forms.Control.Paint> 事件处理程序的参数。</span><span class="sxs-lookup"><span data-stu-id="e1d14-108">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e1d14-109">可靠编程</span><span class="sxs-lookup"><span data-stu-id="e1d14-109">Robust Programming</span></span>  
 <span data-ttu-id="e1d14-110">应始终对 <xref:System.IDisposable.Dispose%2A> 使用系统资源的任何对象（如对象）调用 <xref:System.Drawing.Pen> 。</span><span class="sxs-lookup"><span data-stu-id="e1d14-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d14-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="e1d14-111">See also</span></span>

- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="e1d14-112">图形编程入门</span><span class="sxs-lookup"><span data-stu-id="e1d14-112">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="e1d14-113">使用笔绘制线条和形状</span><span class="sxs-lookup"><span data-stu-id="e1d14-113">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="e1d14-114">Windows 窗体中的图形和绘制</span><span class="sxs-lookup"><span data-stu-id="e1d14-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
