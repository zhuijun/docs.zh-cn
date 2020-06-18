---
title: 如何：使用 SaveFileDialog 组件保存文件
description: 了解如何使用 SaveFileDialog 组件浏览文件系统并选择要保存的文件。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- SaveFileDialog component [Windows Forms], saving files
- files [Windows Forms], saving
- OpenFile method [Windows Forms], saving files with SaveFileDialog component
ms.assetid: 02e8f409-b83f-4707-babb-e71f6b223d90
ms.openlocfilehash: cd773c3d4aa2b907eb09dd87c3fdbe138bf533bb
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904398"
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a><span data-ttu-id="5b566-103">如何：使用 SaveFileDialog 组件保存文件</span><span class="sxs-lookup"><span data-stu-id="5b566-103">How to: Save Files Using the SaveFileDialog Component</span></span>

<span data-ttu-id="5b566-104"><xref:System.Windows.Forms.SaveFileDialog>组件允许用户浏览文件系统并选择要保存的文件。</span><span class="sxs-lookup"><span data-stu-id="5b566-104">The <xref:System.Windows.Forms.SaveFileDialog> component allows users to browse the file system and select files to be saved.</span></span> <span data-ttu-id="5b566-105">对话框返回用户在对话框中所选的文件路径和名称。</span><span class="sxs-lookup"><span data-stu-id="5b566-105">The dialog box returns the path and name of the file the user has selected in the dialog box.</span></span> <span data-ttu-id="5b566-106">但是必须编写代码才能真正地将文件写入磁盘。</span><span class="sxs-lookup"><span data-stu-id="5b566-106">However, you must write the code to actually write the files to disk.</span></span>

### <a name="to-save-a-file-using-the-savefiledialog-component"></a><span data-ttu-id="5b566-107">使用 SaveFileDialog 组件保存文件</span><span class="sxs-lookup"><span data-stu-id="5b566-107">To save a file using the SaveFileDialog component</span></span>

- <span data-ttu-id="5b566-108">显示“保存文件”\*\*\*\* 对话框，并调用来方法保存用户选择的文件。</span><span class="sxs-lookup"><span data-stu-id="5b566-108">Display the **Save File** dialog box and call a method to save the file selected by the user.</span></span>

  <span data-ttu-id="5b566-109">使用 <xref:System.Windows.Forms.SaveFileDialog> 组件的 <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> 方法保存文件。</span><span class="sxs-lookup"><span data-stu-id="5b566-109">Use the <xref:System.Windows.Forms.SaveFileDialog> component's <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="5b566-110">此方法提供了一个 <xref:System.IO.Stream> 可以写入的对象。</span><span class="sxs-lookup"><span data-stu-id="5b566-110">This method gives you a <xref:System.IO.Stream> object you can write to.</span></span>

  <span data-ttu-id="5b566-111">下面的示例使用 <xref:System.Windows.Forms.DialogResult> 属性获取文件的名称，并使用 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 方法来保存文件。</span><span class="sxs-lookup"><span data-stu-id="5b566-111">The example below uses the <xref:System.Windows.Forms.DialogResult> property to get the name of the file, and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="5b566-112"><xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>方法提供要将文件写入到的流。</span><span class="sxs-lookup"><span data-stu-id="5b566-112">The <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method gives you a stream to write the file to.</span></span>

  <span data-ttu-id="5b566-113">在下面的示例中，有一个 <xref:System.Windows.Forms.Button> 分配有图像的控件。</span><span class="sxs-lookup"><span data-stu-id="5b566-113">In the example below, there is a <xref:System.Windows.Forms.Button> control with an image assigned to it.</span></span> <span data-ttu-id="5b566-114">单击该按钮时， <xref:System.Windows.Forms.SaveFileDialog> 组件将使用允许类型为 .gif、jpeg 和 .bmp 的文件的筛选器来实例化。</span><span class="sxs-lookup"><span data-stu-id="5b566-114">When you click the button, a <xref:System.Windows.Forms.SaveFileDialog> component is instantiated with a filter that allows files of type .gif, .jpeg, and .bmp.</span></span> <span data-ttu-id="5b566-115">如果在“保存文件”对话框中选择了此类型的文件，那么按钮的图像将会保存。</span><span class="sxs-lookup"><span data-stu-id="5b566-115">If a file of this type is selected in the Save File dialog box, the button's image is saved.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="5b566-116">若要获取或设置 <xref:System.Windows.Forms.FileDialog.FileName%2A> 属性，程序集需要类授予的特权级别 <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="5b566-116">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="5b566-117">如果在部分信任上下文中运行，该进程可能会因特权不足而引发异常。</span><span class="sxs-lookup"><span data-stu-id="5b566-117">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="5b566-118">有关详细信息，请参阅 [Code Access Security Basics](../../misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="5b566-118">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

  <span data-ttu-id="5b566-119">该示例假设窗体具有一个 <xref:System.Windows.Forms.Button> 控件，其 <xref:System.Windows.Forms.ButtonBase.Image%2A> 属性设置为类型为 .gif、jpeg 或 .bmp 的文件。</span><span class="sxs-lookup"><span data-stu-id="5b566-119">The example assumes your form has a <xref:System.Windows.Forms.Button> control with its <xref:System.Windows.Forms.ButtonBase.Image%2A> property set to a file of type .gif, .jpeg, or .bmp.</span></span>

  > [!NOTE]
  > <span data-ttu-id="5b566-120"><xref:System.Windows.Forms.FileDialog>类的 <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> 属性（该属性由于继承而成为类的一部分 <xref:System.Windows.Forms.SaveFileDialog> ）使用从1开始的索引。</span><span class="sxs-lookup"><span data-stu-id="5b566-120">The <xref:System.Windows.Forms.FileDialog> class's <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> property (which, due to inheritance, is part of the <xref:System.Windows.Forms.SaveFileDialog> class) uses a one-based index.</span></span> <span data-ttu-id="5b566-121">如果要通过编写代码以特定格式保存数据（例如，以纯文本或二进制格式保存文件），那么这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="5b566-121">This is important if you are writing code to save data in a specific format (for example, saving a file in plain text versus binary format).</span></span> <span data-ttu-id="5b566-122">以下示例介绍了该属性。</span><span class="sxs-lookup"><span data-stu-id="5b566-122">This property is featured in the example below.</span></span>

  ```vb
  Private Sub Button2_Click(ByVal sender As System.Object, _
  ByVal e As System.EventArgs) Handles Button2.Click
      ' Displays a SaveFileDialog so the user can save the Image
      ' assigned to Button2.
      Dim saveFileDialog1 As New SaveFileDialog()
      saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif"
      saveFileDialog1.Title = "Save an Image File"
      saveFileDialog1.ShowDialog()

      ' If the file name is not an empty string open it for saving.
      If saveFileDialog1.FileName <> "" Then
        ' Saves the Image via a FileStream created by the OpenFile method.
        Dim fs As System.IO.FileStream = Ctype _
            (saveFileDialog1.OpenFile(), System.IO.FileStream)
        ' Saves the Image in the appropriate ImageFormat based upon the
        ' file type selected in the dialog box.
        ' NOTE that the FilterIndex property is one-based.
        Select Case saveFileDialog1.FilterIndex
            Case 1
              Me.button2.Image.Save(fs, _
                  System.Drawing.Imaging.ImageFormat.Jpeg)

            Case 2
              Me.button2.Image.Save(fs, _
                  System.Drawing.Imaging.ImageFormat.Bmp)

            Case 3
              Me.button2.Image.Save(fs, _
                  System.Drawing.Imaging.ImageFormat.Gif)
          End Select

          fs.Close()
      End If
  End Sub
  ```

  ```csharp
  private void button2_Click(object sender, System.EventArgs e)
  {
      // Displays a SaveFileDialog so the user can save the Image
      // assigned to Button2.
      SaveFileDialog saveFileDialog1 = new SaveFileDialog();
      saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";
      saveFileDialog1.Title = "Save an Image File";
      saveFileDialog1.ShowDialog();

      // If the file name is not an empty string open it for saving.
      if(saveFileDialog1.FileName != "")
      {
        // Saves the Image via a FileStream created by the OpenFile method.
        System.IO.FileStream fs =
            (System.IO.FileStream)saveFileDialog1.OpenFile();
        // Saves the Image in the appropriate ImageFormat based upon the
        // File type selected in the dialog box.
        // NOTE that the FilterIndex property is one-based.
        switch(saveFileDialog1.FilterIndex)
        {
            case 1 :
            this.button2.Image.Save(fs,
              System.Drawing.Imaging.ImageFormat.Jpeg);
            break;

            case 2 :
            this.button2.Image.Save(fs,
              System.Drawing.Imaging.ImageFormat.Bmp);
            break;

            case 3 :
            this.button2.Image.Save(fs,
              System.Drawing.Imaging.ImageFormat.Gif);
            break;
        }

      fs.Close();
      }
  }
  ```

  ```cpp
  private:
      System::Void button2_Click(System::Object ^ sender,
        System::EventArgs ^ e)
      {
        // Displays a SaveFileDialog so the user can save the Image
        // assigned to Button2.
        SaveFileDialog ^ saveFileDialog1 = new SaveFileDialog();
        saveFileDialog1->Filter =
            "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";
        saveFileDialog1->Title = "Save an Image File";
        saveFileDialog1->ShowDialog();
        // If the file name is not an empty string, open it for saving.
        if(saveFileDialog1->FileName != "")
        {
            // Saves the Image through a FileStream created by
            // the OpenFile method.
            System::IO::FileStream ^ fs =
              safe_cast\<System::IO::FileStream*>(
              saveFileDialog1->OpenFile());
            // Saves the Image in the appropriate ImageFormat based on
            // the file type selected in the dialog box.
            // Note that the FilterIndex property is one based.
            switch(saveFileDialog1->FilterIndex)
            {
              case 1 :
                  this->button2->Image->Save(fs,
                    System::Drawing::Imaging::ImageFormat::Jpeg);
                  break;
              case 2 :
                  this->button2->Image->Save(fs,
                    System::Drawing::Imaging::ImageFormat::Bmp);
                  break;
              case 3 :
                  this->button2->Image->Save(fs,
                    System::Drawing::Imaging::ImageFormat::Gif);
                  break;
            }
        fs->Close();
        }
      }
  ```

  <span data-ttu-id="5b566-123">（Visual c # 和 Visual C++）将以下代码放在窗体的构造函数中以注册事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="5b566-123">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

  ```csharp
  this.button2.Click += new System.EventHandler(this.button2_Click);
  ```

  ```cpp
  this->button2->Click += gcnew
      System::EventHandler(this, &Form1::button2_Click);
  ```

  <span data-ttu-id="5b566-124">有关写入文件流的详细信息，请参阅 <xref:System.IO.FileStream.BeginWrite%2A> 和 <xref:System.IO.FileStream.Write%2A> 。</span><span class="sxs-lookup"><span data-stu-id="5b566-124">For more information about writing file streams, see <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.Write%2A>.</span></span>

  > [!NOTE]
  > <span data-ttu-id="5b566-125">某些控件（如 <xref:System.Windows.Forms.RichTextBox> 控件）能够保存文件。</span><span class="sxs-lookup"><span data-stu-id="5b566-125">Certain controls, such as the <xref:System.Windows.Forms.RichTextBox> control, have the ability to save files.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b566-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b566-126">See also</span></span>

- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="5b566-127">SaveFileDialog 组件</span><span class="sxs-lookup"><span data-stu-id="5b566-127">SaveFileDialog Component</span></span>](savefiledialog-component-windows-forms.md)
