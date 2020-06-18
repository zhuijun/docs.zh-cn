---
title: 如何：在字符串中添加引号
description: 了解如何在文本字符串中放置引号。 另外，了解如何将引号字段用作常量。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
ms.openlocfilehash: 08a3e2ab5662cbbf7825890ab430fddcd7b4a9ce
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903618"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a><span data-ttu-id="e81ec-104">如何：在字符串中放置引号（Windows 窗体）</span><span class="sxs-lookup"><span data-stu-id="e81ec-104">How to: Put Quotation Marks in a String (Windows Forms)</span></span>
<span data-ttu-id="e81ec-105">有时可能需要将引号（“”）放入文本字符串中。</span><span class="sxs-lookup"><span data-stu-id="e81ec-105">Sometimes you might want to place quotation marks (" ") in a string of text.</span></span> <span data-ttu-id="e81ec-106">例如：</span><span class="sxs-lookup"><span data-stu-id="e81ec-106">For example:</span></span>  
  
 <span data-ttu-id="e81ec-107">她说：“该好好款待你了！”</span><span class="sxs-lookup"><span data-stu-id="e81ec-107">She said, "You deserve a treat!"</span></span>  
  
 <span data-ttu-id="e81ec-108">作为替代方法，还可以将 <xref:Microsoft.VisualBasic.ControlChars.Quote> 字段用作常量。</span><span class="sxs-lookup"><span data-stu-id="e81ec-108">As an alternative, you can also use the <xref:Microsoft.VisualBasic.ControlChars.Quote> field as a constant.</span></span>  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a><span data-ttu-id="e81ec-109">在代码中的字符串内放置引号</span><span class="sxs-lookup"><span data-stu-id="e81ec-109">To place quotation marks in a string in your code</span></span>  
  
1. <span data-ttu-id="e81ec-110">在 Visual Basic 中，在行中插入两个用引号引起来的引号。</span><span class="sxs-lookup"><span data-stu-id="e81ec-110">In Visual Basic, insert two quotation marks in a row as an embedded quotation mark.</span></span> <span data-ttu-id="e81ec-111">在 Visual c # 和 Visual C++ 中，插入转义序列 \\ "作为嵌入的引号。</span><span class="sxs-lookup"><span data-stu-id="e81ec-111">In Visual C# and Visual C++, insert the escape sequence \\" as an embedded quotation mark.</span></span> <span data-ttu-id="e81ec-112">例如，若要创建前面提到的字符串，请使用下面的代码。</span><span class="sxs-lookup"><span data-stu-id="e81ec-112">For example, to create the preceding string, use the following code.</span></span>  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     <span data-ttu-id="e81ec-113">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="e81ec-113">-or-</span></span>  
  
2. <span data-ttu-id="e81ec-114">插入 ASCII 字符或 Unicode 字符表示引号。</span><span class="sxs-lookup"><span data-stu-id="e81ec-114">Insert the ASCII or Unicode character for a quotation mark.</span></span> <span data-ttu-id="e81ec-115">在 Visual Basic 中，使用 ASCII 字符（34）。</span><span class="sxs-lookup"><span data-stu-id="e81ec-115">In Visual Basic, use the ASCII character (34).</span></span> <span data-ttu-id="e81ec-116">在 Visual c # 中，使用 Unicode 字符（\u0022）。</span><span class="sxs-lookup"><span data-stu-id="e81ec-116">In Visual C#, use the Unicode character (\u0022).</span></span>  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="e81ec-117">在本示例中，不能使用 \u0022，因为不能使用指定基本字符集中字符的通用字符名。</span><span class="sxs-lookup"><span data-stu-id="e81ec-117">In this example, you cannot use \u0022 because you cannot use a universal character name that designates a character in the basic character set.</span></span> <span data-ttu-id="e81ec-118">否则，将产生 C3851。</span><span class="sxs-lookup"><span data-stu-id="e81ec-118">Otherwise, you produce C3851.</span></span> <span data-ttu-id="e81ec-119">有关详细信息，请参阅[编译器错误 C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851)。</span><span class="sxs-lookup"><span data-stu-id="e81ec-119">For more information, see [Compiler Error C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851).</span></span>  
  
     <span data-ttu-id="e81ec-120">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="e81ec-120">-or-</span></span>  
  
3. <span data-ttu-id="e81ec-121">还可以为该字符定义一个常数，然后在需要时使用。</span><span class="sxs-lookup"><span data-stu-id="e81ec-121">You can also define a constant for the character, and use it where needed.</span></span>  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e81ec-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e81ec-122">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- <xref:Microsoft.VisualBasic.ControlChars.Quote>
- [<span data-ttu-id="e81ec-123">TextBox 控件概述</span><span class="sxs-lookup"><span data-stu-id="e81ec-123">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="e81ec-124">如何：控制 Windows 窗体 TextBox 控件中的插入点</span><span class="sxs-lookup"><span data-stu-id="e81ec-124">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="e81ec-125">如何：使用 Windows 窗体 TextBox 控件创建密码文本框</span><span class="sxs-lookup"><span data-stu-id="e81ec-125">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="e81ec-126">如何：创建只读文本框</span><span class="sxs-lookup"><span data-stu-id="e81ec-126">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="e81ec-127">如何：在 Windows 窗体 TextBox 控件中选择文本</span><span class="sxs-lookup"><span data-stu-id="e81ec-127">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="e81ec-128">如何：在 Windows 窗体 TextBox 控件中查看多个行</span><span class="sxs-lookup"><span data-stu-id="e81ec-128">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="e81ec-129">TextBox 控件</span><span class="sxs-lookup"><span data-stu-id="e81ec-129">TextBox Control</span></span>](textbox-control-windows-forms.md)
