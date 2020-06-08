---
title: 如何：读取固定宽度的文本文件
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 77b2e0a4ebe36b68501f821ef5731935ee3b16a7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411624"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="404f8-102">如何：在 Visual Basic 中读取定宽文本文件</span><span class="sxs-lookup"><span data-stu-id="404f8-102">How to: read from fixed-width text files in Visual Basic</span></span>

<span data-ttu-id="404f8-103">`TextFieldParser` 对象提供一种可以轻松而高效地分析结构化文本文件（如日志）的方法。</span><span class="sxs-lookup"><span data-stu-id="404f8-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="404f8-104">`TextFieldType` 属性定义分析的文件是带分隔符的文件还是具有定宽文本字段的文件。</span><span class="sxs-lookup"><span data-stu-id="404f8-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="404f8-105">在定宽文本文件中，结尾处的字段可以具有可变宽度。</span><span class="sxs-lookup"><span data-stu-id="404f8-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="404f8-106">若要指定结尾处的字段具有可变宽度，请将它定义为宽度小于或等于零。</span><span class="sxs-lookup"><span data-stu-id="404f8-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="404f8-107">分析定宽文本文件</span><span class="sxs-lookup"><span data-stu-id="404f8-107">To parse a fixed-width text file</span></span>  
  
1. <span data-ttu-id="404f8-108">创建一个新的 `TextFieldParser`。</span><span class="sxs-lookup"><span data-stu-id="404f8-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="404f8-109">下面的代码创建名为 `Reader` 的 `TextFieldParser`，并打开 `test.log` 文件。</span><span class="sxs-lookup"><span data-stu-id="404f8-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. <span data-ttu-id="404f8-110">将 `TextFieldType` 属性定义为 `FixedWidth`（定义宽度和格式）。</span><span class="sxs-lookup"><span data-stu-id="404f8-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="404f8-111">下面的代码定义文本的各列；第一列宽度为 5 个字符，第二列宽度为 10 个字符，第三列宽度为 11 个字符，而第四列宽度可变。</span><span class="sxs-lookup"><span data-stu-id="404f8-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. <span data-ttu-id="404f8-112">循环访问文件中的各个字段。</span><span class="sxs-lookup"><span data-stu-id="404f8-112">Loop through the fields in the file.</span></span> <span data-ttu-id="404f8-113">如果有任何行损坏，则报告错误，然后继续分析。</span><span class="sxs-lookup"><span data-stu-id="404f8-113">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. <span data-ttu-id="404f8-114">用 `End While` 和 `End Using` 结束 `While` 和 `Using` 块。</span><span class="sxs-lookup"><span data-stu-id="404f8-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="404f8-115">示例</span><span class="sxs-lookup"><span data-stu-id="404f8-115">Example</span></span>  

 <span data-ttu-id="404f8-116">此示例读取文件 `test.log`。</span><span class="sxs-lookup"><span data-stu-id="404f8-116">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="404f8-117">可靠编程</span><span class="sxs-lookup"><span data-stu-id="404f8-117">Robust programming</span></span>  

 <span data-ttu-id="404f8-118">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="404f8-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="404f8-119">无法使用指定的格式 (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>) 分析行。</span><span class="sxs-lookup"><span data-stu-id="404f8-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="404f8-120">此异常消息指定导致发生异常的行，同时将 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> 属性分配给该行中包含的文本。</span><span class="sxs-lookup"><span data-stu-id="404f8-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
- <span data-ttu-id="404f8-121">指定的文件不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="404f8-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="404f8-122">在部分信任的情况下，用户没有足够的权限访问文件。</span><span class="sxs-lookup"><span data-stu-id="404f8-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="404f8-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="404f8-123">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="404f8-124">路径过长 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="404f8-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="404f8-125">用户没有足够的权限访问文件 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="404f8-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="404f8-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="404f8-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="404f8-127">如何：读取逗号分隔的文本文件</span><span class="sxs-lookup"><span data-stu-id="404f8-127">How to: Read From Comma-Delimited Text Files</span></span>](how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="404f8-128">如何：读取具有多种格式的文本文件</span><span class="sxs-lookup"><span data-stu-id="404f8-128">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="404f8-129">使用 TextFieldParser 对象分析文本文件</span><span class="sxs-lookup"><span data-stu-id="404f8-129">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="404f8-130">演练：在 Visual Basic 中操作文件和目录</span><span class="sxs-lookup"><span data-stu-id="404f8-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="404f8-131">疑难解答：读取和写入文本文件</span><span class="sxs-lookup"><span data-stu-id="404f8-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
