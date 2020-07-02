---
title: 如何：通过对窗体和控件使用双缓冲来减少图形闪烁
description: 了解如何使用 Windows 窗体的双缓冲来减少图形闪烁，并使用控件解决与绘画操作相关的闪烁问题。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: f7c0425729f8a1a780124621788a1c49e06e0c4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618124"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a><span data-ttu-id="5f8cc-103">如何：通过对窗体和控件使用双缓冲来减少图形闪烁</span><span class="sxs-lookup"><span data-stu-id="5f8cc-103">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>
<span data-ttu-id="5f8cc-104">双缓冲使用内容缓冲来解决与多个画图操作相关的闪烁问题。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-104">Double buffering uses a memory buffer to address the flicker problems associated with multiple paint operations.</span></span> <span data-ttu-id="5f8cc-105">启用双缓冲后，所有画图操作会首先呈现到内存缓冲而不是屏幕上的绘图图面。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-105">When double buffering is enabled, all paint operations are first rendered to a memory buffer instead of the drawing surface on the screen.</span></span> <span data-ttu-id="5f8cc-106">所有画图操作完成后，内存缓冲会直接复制到与之关联的绘图图面。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-106">After all paint operations are completed, the memory buffer is copied directly to the drawing surface associated with it.</span></span> <span data-ttu-id="5f8cc-107">由于在屏幕上只执行一项图形操作，因此消除了与复杂绘制操作关联的图像闪烁。对于大多数应用程序，.NET Framework 提供的默认双缓冲将提供最佳结果。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-107">Because only one graphics operation is performed on the screen, the image flickering associated with complex painting operations is eliminated.For most applications, the default double buffering provided by the .NET Framework will provide the best results.</span></span> <span data-ttu-id="5f8cc-108">默认情况下，标准 Windows 窗体控件是双缓冲的。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-108">Standard Windows Forms controls are double buffered by default.</span></span> <span data-ttu-id="5f8cc-109">可以通过两种方式在窗体和创作的控件中启用默认双缓冲。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-109">You can enable default double buffering in your forms and authored controls in two ways.</span></span> <span data-ttu-id="5f8cc-110">你可以将属性设置 <xref:System.Windows.Forms.Control.DoubleBuffered%2A> 为 `true` ，或者可以调用 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法将标志设置 <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> 为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-110">You can either set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`, or you can call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span> <span data-ttu-id="5f8cc-111">这两种方法都将为窗体或控件启用默认的双缓冲，并提供无闪烁图形呈现功能。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-111">Both methods will enable default double buffering for your form or control and provide flicker-free graphics rendering.</span></span> <span data-ttu-id="5f8cc-112"><xref:System.Windows.Forms.Control.SetStyle%2A>建议仅对已为其编写所有呈现代码的自定义控件调用方法。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-112">Calling the <xref:System.Windows.Forms.Control.SetStyle%2A> method is recommended only for custom controls for which you have written all the rendering code.</span></span>  
  
 <span data-ttu-id="5f8cc-113">对于更高级的双缓冲方案，如动画或高级内存管理，可以实现自己的双缓冲逻辑。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-113">For more advanced double buffering scenarios, such as animation or advanced memory management, you can implement your own double buffering logic.</span></span> <span data-ttu-id="5f8cc-114">有关详细信息，请参阅[如何：手动管理缓冲图形](how-to-manually-manage-buffered-graphics.md)。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-114">For more information, see [How to: Manually Manage Buffered Graphics](how-to-manually-manage-buffered-graphics.md).</span></span>  
  
### <a name="to-reduce-flicker"></a><span data-ttu-id="5f8cc-115">减少闪烁</span><span class="sxs-lookup"><span data-stu-id="5f8cc-115">To reduce flicker</span></span>  
  
- <span data-ttu-id="5f8cc-116">将 <xref:System.Windows.Forms.Control.DoubleBuffered%2A> 属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-116">Set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 <span data-ttu-id="5f8cc-117">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="5f8cc-117">\- or -</span></span>  
  
- <span data-ttu-id="5f8cc-118">调用 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法以将标志设置 <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> 为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-118">Call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="5f8cc-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="5f8cc-119">See also</span></span>

- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>
- <xref:System.Windows.Forms.Control.SetStyle%2A>
- [<span data-ttu-id="5f8cc-120">双缓冲图形</span><span class="sxs-lookup"><span data-stu-id="5f8cc-120">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="5f8cc-121">Windows 窗体中的图形和绘制</span><span class="sxs-lookup"><span data-stu-id="5f8cc-121">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
