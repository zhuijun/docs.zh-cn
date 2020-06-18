---
title: 如何：创建用于绘制的 Graphics 对象
description: 了解如何创建一个图形对象，该对象需要使用 GDI + 绘制线条和形状、呈现文本或显示和操作图像。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
ms.openlocfilehash: 1a0884c1e9956dc6f4608e32372deeea24ef4670
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903202"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="73127-103">如何：创建用于绘制的 Graphics 对象</span><span class="sxs-lookup"><span data-stu-id="73127-103">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="73127-104">你需要创建一个对象，然后才能使用 GDI + 绘制线条和形状、呈现文本或显示和操作图像 <xref:System.Drawing.Graphics> 。</span><span class="sxs-lookup"><span data-stu-id="73127-104">Before you can draw lines and shapes, render text, or display and manipulate images with GDI+, you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="73127-105"><xref:System.Drawing.Graphics>对象表示 GDI + 绘图图面，是用于创建图形图像的对象。</span><span class="sxs-lookup"><span data-stu-id="73127-105">The <xref:System.Drawing.Graphics> object represents a GDI+ drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="73127-106">使用图形需要执行两个步骤：</span><span class="sxs-lookup"><span data-stu-id="73127-106">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="73127-107">创建 <xref:System.Drawing.Graphics> 对象。</span><span class="sxs-lookup"><span data-stu-id="73127-107">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="73127-108">使用 <xref:System.Drawing.Graphics> 对象绘制线条和形状、呈现文本或显示和操作图像。</span><span class="sxs-lookup"><span data-stu-id="73127-108">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="73127-109">创建图形对象</span><span class="sxs-lookup"><span data-stu-id="73127-109">Creating a Graphics Object</span></span>  
 <span data-ttu-id="73127-110">可以通过多种方式创建图形对象。</span><span class="sxs-lookup"><span data-stu-id="73127-110">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="73127-111">创建图形对象</span><span class="sxs-lookup"><span data-stu-id="73127-111">To create a graphics object</span></span>  
  
- <span data-ttu-id="73127-112"><xref:System.Windows.Forms.PaintEventArgs>在 <xref:System.Windows.Forms.Control.Paint> 窗体或控件的事件中，接收对图形对象的引用作为的一部分。</span><span class="sxs-lookup"><span data-stu-id="73127-112">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="73127-113">这通常是在创建控件的绘制代码时获取对图形对象的引用的方式。</span><span class="sxs-lookup"><span data-stu-id="73127-113">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="73127-114">同样，在为处理事件时，还可以获取图形对象作为的属性 <xref:System.Drawing.Printing.PrintPageEventArgs> <xref:System.Drawing.Printing.PrintDocument.PrintPage> <xref:System.Drawing.Printing.PrintDocument> 。</span><span class="sxs-lookup"><span data-stu-id="73127-114">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="73127-115">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="73127-115">-or-</span></span>  
  
- <span data-ttu-id="73127-116">调用 <xref:System.Windows.Forms.Control.CreateGraphics%2A> 控件或窗体的方法来获取对对象的引用， <xref:System.Drawing.Graphics> 该对象表示该控件或窗体的绘图图面。</span><span class="sxs-lookup"><span data-stu-id="73127-116">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="73127-117">如果要在已存在的窗体或控件上进行绘制，请使用此方法。</span><span class="sxs-lookup"><span data-stu-id="73127-117">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="73127-118">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="73127-118">-or-</span></span>  
  
- <span data-ttu-id="73127-119"><xref:System.Drawing.Graphics>从继承自的任何对象创建对象 <xref:System.Drawing.Image> 。</span><span class="sxs-lookup"><span data-stu-id="73127-119">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="73127-120">当您想要更改现有的映像时，此方法非常有用。</span><span class="sxs-lookup"><span data-stu-id="73127-120">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="73127-121">以下各节将详细介绍其中每个过程。</span><span class="sxs-lookup"><span data-stu-id="73127-121">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="73127-122">Paint 事件处理程序中的 PaintEventArgs</span><span class="sxs-lookup"><span data-stu-id="73127-122">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="73127-123">在 <xref:System.Windows.Forms.PaintEventHandler> 对控件或的进行编程时 <xref:System.Drawing.Printing.PrintDocument.PrintPage> <xref:System.Drawing.Printing.PrintDocument> ，图形对象作为或的属性之一提供 <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs> 。</span><span class="sxs-lookup"><span data-stu-id="73127-123">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="73127-124">从画图事件的 PaintEventArgs 中获取对图形对象的引用</span><span class="sxs-lookup"><span data-stu-id="73127-124">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="73127-125">声明 <xref:System.Drawing.Graphics> 对象。</span><span class="sxs-lookup"><span data-stu-id="73127-125">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="73127-126">分配变量以引用 <xref:System.Drawing.Graphics> 作为的一部分传递的对象 <xref:System.Windows.Forms.PaintEventArgs> 。</span><span class="sxs-lookup"><span data-stu-id="73127-126">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="73127-127">插入用于绘制窗体或控件的代码。</span><span class="sxs-lookup"><span data-stu-id="73127-127">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="73127-128">下面的示例演示如何 <xref:System.Drawing.Graphics> <xref:System.Windows.Forms.PaintEventArgs> 在事件中引用对象 <xref:System.Windows.Forms.Control.Paint> ：</span><span class="sxs-lookup"><span data-stu-id="73127-128">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
    ```vb  
    Private Sub Form1_Paint(sender As Object, pe As PaintEventArgs) Handles _  
       MyBase.Paint  
       ' Declares the Graphics object and sets it to the Graphics object  
       ' supplied in the PaintEventArgs.  
       Dim g As Graphics = pe.Graphics  
       ' Insert code to paint the form here.  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Paint(object sender,
       System.Windows.Forms.PaintEventArgs pe)
    {  
       // Declares the Graphics object and sets it to the Graphics object  
       // supplied in the PaintEventArgs.  
       Graphics g = pe.Graphics;  
       // Insert code to paint the form here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void Form1_Paint(System::Object ^ sender,  
          System::Windows::Forms::PaintEventArgs ^ pe)  
       {  
          // Declares the Graphics object and sets it to the Graphics object  
          // supplied in the PaintEventArgs.  
          Graphics ^ g = pe->Graphics;  
          // Insert code to paint the form here.  
       }  
    ```  
  
## <a name="creategraphics-method"></a><span data-ttu-id="73127-129">CreateGraphics 方法</span><span class="sxs-lookup"><span data-stu-id="73127-129">CreateGraphics Method</span></span>  
 <span data-ttu-id="73127-130">你还可以使用 <xref:System.Windows.Forms.Control.CreateGraphics%2A> 控件或窗体的方法来获取对对象的引用， <xref:System.Drawing.Graphics> 该对象表示该控件或窗体的绘图图面。</span><span class="sxs-lookup"><span data-stu-id="73127-130">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="73127-131">使用 CreateGraphics 方法创建图形对象</span><span class="sxs-lookup"><span data-stu-id="73127-131">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="73127-132">调用 <xref:System.Windows.Forms.Control.CreateGraphics%2A> 要在其上呈现图形的窗体或控件的方法。</span><span class="sxs-lookup"><span data-stu-id="73127-132">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
    ```vb  
    Dim g as Graphics  
    ' Sets g to a Graphics object representing the drawing surface of the  
    ' control or form g is a member of.  
    g = Me.CreateGraphics  
    ```  
  
    ```csharp  
    Graphics g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this.CreateGraphics();  
    ```  
  
    ```cpp  
    Graphics ^ g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this->CreateGraphics();  
    ```  
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="73127-133">从 Image 对象创建</span><span class="sxs-lookup"><span data-stu-id="73127-133">Create from an Image Object</span></span>  
 <span data-ttu-id="73127-134">此外，还可以从派生自类的任何对象创建图形对象 <xref:System.Drawing.Image> 。</span><span class="sxs-lookup"><span data-stu-id="73127-134">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="73127-135">从图像创建图形对象</span><span class="sxs-lookup"><span data-stu-id="73127-135">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="73127-136">调用 <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> 方法，并提供要从中创建对象的图像变量的名称 <xref:System.Drawing.Graphics> 。</span><span class="sxs-lookup"><span data-stu-id="73127-136">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="73127-137">下面的示例演示如何使用 <xref:System.Drawing.Bitmap> 对象：</span><span class="sxs-lookup"><span data-stu-id="73127-137">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
    ```vb  
    Dim myBitmap as New Bitmap("C:\Documents and Settings\Joe\Pics\myPic.bmp")  
    Dim g as Graphics = Graphics.FromImage(myBitmap)  
    ```  
  
    ```csharp  
    Bitmap myBitmap = new Bitmap(@"C:\Documents and
       Settings\Joe\Pics\myPic.bmp");  
    Graphics g = Graphics.FromImage(myBitmap);  
    ```  
  
    ```cpp  
    Bitmap ^ myBitmap = gcnew  
       Bitmap("D:\\Documents and Settings\\Joe\\Pics\\myPic.bmp");  
    Graphics ^ g = Graphics::FromImage(myBitmap);  
    ```  
  
> [!NOTE]
> <span data-ttu-id="73127-138">只能 <xref:System.Drawing.Graphics> 从非索引的 .bmp 文件创建对象，例如16位、24位和32位 .bmp 文件。</span><span class="sxs-lookup"><span data-stu-id="73127-138">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="73127-139">非索引 .bmp 文件的每个像素都包含一种颜色，这与用于保存颜色表的索引的索引 .bmp 文件的像素不同。</span><span class="sxs-lookup"><span data-stu-id="73127-139">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="73127-140">绘制和操作形状和图像</span><span class="sxs-lookup"><span data-stu-id="73127-140">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="73127-141">创建对象后， <xref:System.Drawing.Graphics> 可以使用对象来绘制线条和形状、呈现文本或显示和操作图像。</span><span class="sxs-lookup"><span data-stu-id="73127-141">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="73127-142">与对象一起使用的主体对象 <xref:System.Drawing.Graphics> 包括：</span><span class="sxs-lookup"><span data-stu-id="73127-142">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="73127-143"><xref:System.Drawing.Pen>类-用于绘制线条、显示形状或呈现其他几何表示形式。</span><span class="sxs-lookup"><span data-stu-id="73127-143">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="73127-144"><xref:System.Drawing.Brush>类-用于填充图形区域，如填充的形状、图像或文本。</span><span class="sxs-lookup"><span data-stu-id="73127-144">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="73127-145"><xref:System.Drawing.Font>类-提供要在呈现文本时使用的形状的说明。</span><span class="sxs-lookup"><span data-stu-id="73127-145">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="73127-146"><xref:System.Drawing.Color>结构-表示要显示的不同颜色。</span><span class="sxs-lookup"><span data-stu-id="73127-146">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="73127-147">使用已创建的图形对象</span><span class="sxs-lookup"><span data-stu-id="73127-147">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="73127-148">使用上面列出的相应对象来绘制您需要的内容。</span><span class="sxs-lookup"><span data-stu-id="73127-148">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="73127-149">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="73127-149">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="73127-150">呈现</span><span class="sxs-lookup"><span data-stu-id="73127-150">To render</span></span>|<span data-ttu-id="73127-151">查看</span><span class="sxs-lookup"><span data-stu-id="73127-151">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="73127-152">线条</span><span class="sxs-lookup"><span data-stu-id="73127-152">Lines</span></span>|[<span data-ttu-id="73127-153">如何：在 Windows 窗体上绘制直线</span><span class="sxs-lookup"><span data-stu-id="73127-153">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="73127-154">形状</span><span class="sxs-lookup"><span data-stu-id="73127-154">Shapes</span></span>|[<span data-ttu-id="73127-155">如何：绘制轮廓形状</span><span class="sxs-lookup"><span data-stu-id="73127-155">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="73127-156">文本</span><span class="sxs-lookup"><span data-stu-id="73127-156">Text</span></span>|[<span data-ttu-id="73127-157">如何：在 Windows 窗体上绘制文本</span><span class="sxs-lookup"><span data-stu-id="73127-157">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="73127-158">映像</span><span class="sxs-lookup"><span data-stu-id="73127-158">Images</span></span>|[<span data-ttu-id="73127-159">如何：使用 GDI+ 呈现图像</span><span class="sxs-lookup"><span data-stu-id="73127-159">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="73127-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="73127-160">See also</span></span>

- [<span data-ttu-id="73127-161">图形编程入门</span><span class="sxs-lookup"><span data-stu-id="73127-161">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="73127-162">Windows 窗体中的图形和绘制</span><span class="sxs-lookup"><span data-stu-id="73127-162">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="73127-163">直线、曲线和图形</span><span class="sxs-lookup"><span data-stu-id="73127-163">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="73127-164">如何：使用 GDI+ 呈现图像</span><span class="sxs-lookup"><span data-stu-id="73127-164">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
