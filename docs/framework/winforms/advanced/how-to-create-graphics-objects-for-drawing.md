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
# <a name="how-to-create-graphics-objects-for-drawing"></a>如何：创建用于绘制的 Graphics 对象
你需要创建一个对象，然后才能使用 GDI + 绘制线条和形状、呈现文本或显示和操作图像 <xref:System.Drawing.Graphics> 。 <xref:System.Drawing.Graphics>对象表示 GDI + 绘图图面，是用于创建图形图像的对象。  
  
 使用图形需要执行两个步骤：  
  
1. 创建 <xref:System.Drawing.Graphics> 对象。  
  
2. 使用 <xref:System.Drawing.Graphics> 对象绘制线条和形状、呈现文本或显示和操作图像。  
  
## <a name="creating-a-graphics-object"></a>创建图形对象  
 可以通过多种方式创建图形对象。  
  
#### <a name="to-create-a-graphics-object"></a>创建图形对象  
  
- <xref:System.Windows.Forms.PaintEventArgs>在 <xref:System.Windows.Forms.Control.Paint> 窗体或控件的事件中，接收对图形对象的引用作为的一部分。 这通常是在创建控件的绘制代码时获取对图形对象的引用的方式。 同样，在为处理事件时，还可以获取图形对象作为的属性 <xref:System.Drawing.Printing.PrintPageEventArgs> <xref:System.Drawing.Printing.PrintDocument.PrintPage> <xref:System.Drawing.Printing.PrintDocument> 。  
  
     \- 或 -  
  
- 调用 <xref:System.Windows.Forms.Control.CreateGraphics%2A> 控件或窗体的方法来获取对对象的引用， <xref:System.Drawing.Graphics> 该对象表示该控件或窗体的绘图图面。 如果要在已存在的窗体或控件上进行绘制，请使用此方法。  
  
     \- 或 -  
  
- <xref:System.Drawing.Graphics>从继承自的任何对象创建对象 <xref:System.Drawing.Image> 。 当您想要更改现有的映像时，此方法非常有用。  
  
     以下各节将详细介绍其中每个过程。  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>Paint 事件处理程序中的 PaintEventArgs  
 在 <xref:System.Windows.Forms.PaintEventHandler> 对控件或的进行编程时 <xref:System.Drawing.Printing.PrintDocument.PrintPage> <xref:System.Drawing.Printing.PrintDocument> ，图形对象作为或的属性之一提供 <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs> 。  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>从画图事件的 PaintEventArgs 中获取对图形对象的引用  
  
1. 声明 <xref:System.Drawing.Graphics> 对象。  
  
2. 分配变量以引用 <xref:System.Drawing.Graphics> 作为的一部分传递的对象 <xref:System.Windows.Forms.PaintEventArgs> 。  
  
3. 插入用于绘制窗体或控件的代码。  
  
     下面的示例演示如何 <xref:System.Drawing.Graphics> <xref:System.Windows.Forms.PaintEventArgs> 在事件中引用对象 <xref:System.Windows.Forms.Control.Paint> ：  
  
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
  
## <a name="creategraphics-method"></a>CreateGraphics 方法  
 你还可以使用 <xref:System.Windows.Forms.Control.CreateGraphics%2A> 控件或窗体的方法来获取对对象的引用， <xref:System.Drawing.Graphics> 该对象表示该控件或窗体的绘图图面。  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>使用 CreateGraphics 方法创建图形对象  
  
- 调用 <xref:System.Windows.Forms.Control.CreateGraphics%2A> 要在其上呈现图形的窗体或控件的方法。  
  
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
  
## <a name="create-from-an-image-object"></a>从 Image 对象创建  
 此外，还可以从派生自类的任何对象创建图形对象 <xref:System.Drawing.Image> 。  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>从图像创建图形对象  
  
- 调用 <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> 方法，并提供要从中创建对象的图像变量的名称 <xref:System.Drawing.Graphics> 。  
  
     下面的示例演示如何使用 <xref:System.Drawing.Bitmap> 对象：  
  
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
> 只能 <xref:System.Drawing.Graphics> 从非索引的 .bmp 文件创建对象，例如16位、24位和32位 .bmp 文件。 非索引 .bmp 文件的每个像素都包含一种颜色，这与用于保存颜色表的索引的索引 .bmp 文件的像素不同。  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>绘制和操作形状和图像  
 创建对象后， <xref:System.Drawing.Graphics> 可以使用对象来绘制线条和形状、呈现文本或显示和操作图像。 与对象一起使用的主体对象 <xref:System.Drawing.Graphics> 包括：  
  
- <xref:System.Drawing.Pen>类-用于绘制线条、显示形状或呈现其他几何表示形式。  
  
- <xref:System.Drawing.Brush>类-用于填充图形区域，如填充的形状、图像或文本。  
  
- <xref:System.Drawing.Font>类-提供要在呈现文本时使用的形状的说明。  
  
- <xref:System.Drawing.Color>结构-表示要显示的不同颜色。  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>使用已创建的图形对象  
  
- 使用上面列出的相应对象来绘制您需要的内容。  
  
     有关详细信息，请参阅下列主题：  
  
    |呈现|查看|  
    |---------------|---------|  
    |线条|[如何：在 Windows 窗体上绘制直线](how-to-draw-a-line-on-a-windows-form.md)|  
    |形状|[如何：绘制轮廓形状](how-to-draw-an-outlined-shape.md)|  
    |文本|[如何：在 Windows 窗体上绘制文本](how-to-draw-text-on-a-windows-form.md)|  
    |映像|[如何：使用 GDI+ 呈现图像](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>另请参阅

- [图形编程入门](getting-started-with-graphics-programming.md)
- [Windows 窗体中的图形和绘制](graphics-and-drawing-in-windows-forms.md)
- [直线、曲线和图形](lines-curves-and-shapes.md)
- [如何：使用 GDI+ 呈现图像](how-to-render-images-with-gdi.md)
