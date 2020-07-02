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
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a><span data-ttu-id="585fb-104">如何：在 Windows 窗体上绘制实心矩形</span><span class="sxs-lookup"><span data-stu-id="585fb-104">How to: Draw a Filled Rectangle on a Windows Form</span></span>
<span data-ttu-id="585fb-105">此示例在窗体上绘制实心矩形。</span><span class="sxs-lookup"><span data-stu-id="585fb-105">This example draws a filled rectangle on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="585fb-106">示例</span><span class="sxs-lookup"><span data-stu-id="585fb-106">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="585fb-107">编译代码</span><span class="sxs-lookup"><span data-stu-id="585fb-107">Compiling the Code</span></span>  
 <span data-ttu-id="585fb-108">不能在事件处理程序中调用此方法 <xref:System.Windows.Forms.Form.Load> 。</span><span class="sxs-lookup"><span data-stu-id="585fb-108">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="585fb-109">如果窗体调整或被其他窗体遮住，则不会重新绘制所绘制的内容。</span><span class="sxs-lookup"><span data-stu-id="585fb-109">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="585fb-110">若要自动重绘内容，应重写 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="585fb-110">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="585fb-111">可靠编程</span><span class="sxs-lookup"><span data-stu-id="585fb-111">Robust Programming</span></span>  
 <span data-ttu-id="585fb-112">应始终对 <xref:System.IDisposable.Dispose%2A> 使用系统资源的任何对象（如 <xref:System.Drawing.Brush> 和对象）调用 <xref:System.Drawing.Graphics> 。</span><span class="sxs-lookup"><span data-stu-id="585fb-112">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="585fb-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="585fb-113">See also</span></span>

- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="585fb-114">图形编程入门</span><span class="sxs-lookup"><span data-stu-id="585fb-114">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="585fb-115">Windows 窗体中的图形和绘制</span><span class="sxs-lookup"><span data-stu-id="585fb-115">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="585fb-116">使用笔绘制线条和形状</span><span class="sxs-lookup"><span data-stu-id="585fb-116">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="585fb-117">GDI+ 中的画笔和实心形状</span><span class="sxs-lookup"><span data-stu-id="585fb-117">Brushes and Filled Shapes in GDI+</span></span>](brushes-and-filled-shapes-in-gdi.md)
