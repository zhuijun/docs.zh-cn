---
title: 如何：读取二进制文件
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: 3b4108034b86d99143fff6943e68ca0077ebd21b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359924"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a><span data-ttu-id="07446-102">如何：在 Visual Basic 中读取二进制文件</span><span class="sxs-lookup"><span data-stu-id="07446-102">How to: Read From Binary Files in Visual Basic</span></span>

<span data-ttu-id="07446-103">`My.Computer.FileSystem` 对象提供用于读取二进制文件的 `ReadAllBytes` 方法。</span><span class="sxs-lookup"><span data-stu-id="07446-103">The `My.Computer.FileSystem` object provides the `ReadAllBytes` method for reading from binary files.</span></span>  
  
### <a name="to-read-from-a-binary-file"></a><span data-ttu-id="07446-104">读取二进制文件</span><span class="sxs-lookup"><span data-stu-id="07446-104">To read from a binary file</span></span>  
  
- <span data-ttu-id="07446-105">使用 `ReadAllBytes` 方法可将文件的内容作为字节数组返回。</span><span class="sxs-lookup"><span data-stu-id="07446-105">Use the `ReadAllBytes` method, which returns the contents of a file as a byte array.</span></span> <span data-ttu-id="07446-106">此示例读取文件 `C:/Documents and Settings/selfportrait.jpg`。</span><span class="sxs-lookup"><span data-stu-id="07446-106">This example reads from the file `C:/Documents and Settings/selfportrait.jpg`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
- <span data-ttu-id="07446-107">对于大型二进制文件，可以使用 <xref:System.IO.FileStream.Read%2A> 对象的 <xref:System.IO.FileStream> 方法从文件中一次只读取指定数量的内容。</span><span class="sxs-lookup"><span data-stu-id="07446-107">For large binary files, you can use the <xref:System.IO.FileStream.Read%2A> method of the <xref:System.IO.FileStream> object to read from the file only a specified amount at a time.</span></span> <span data-ttu-id="07446-108">然后，可以限制每次读取操作将文件加载进内存的数量。</span><span class="sxs-lookup"><span data-stu-id="07446-108">You can then limit how much of the file is loaded into memory for each read operation.</span></span> <span data-ttu-id="07446-109">以下代码示例将复制文件，并允许调用方指定每次读取操作将文件读入内存的数量。</span><span class="sxs-lookup"><span data-stu-id="07446-109">The following code example copies a file and allows the caller to specify how much of the file is read into memory per read operation.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a><span data-ttu-id="07446-110">可靠编程</span><span class="sxs-lookup"><span data-stu-id="07446-110">Robust Programming</span></span>  

 <span data-ttu-id="07446-111">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="07446-111">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="07446-112">路径由于以下原因之一而无效：它是零长度字符串；它仅包含空白；它包含无效字符；或者它是一个设备路径 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="07446-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="07446-113">路径无效，因为它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="07446-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="07446-114">该文件不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="07446-114">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="07446-115">文件正由另一个进程使用，或者出现 I/O 错误 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="07446-115">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="07446-116">路径超过了系统定义的最大长度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="07446-116">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="07446-117">路径中的文件名或目录名包含冒号 (:)，或格式无效 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="07446-117">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="07446-118">内存不足，无法将字符串写入缓冲区 (<xref:System.OutOfMemoryException>)。</span><span class="sxs-lookup"><span data-stu-id="07446-118">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>  
  
- <span data-ttu-id="07446-119">该用户缺少查看该路径所必需的权限 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="07446-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
 <span data-ttu-id="07446-120">不要根据文件的名称来判断文件的内容。</span><span class="sxs-lookup"><span data-stu-id="07446-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="07446-121">例如，文件 Form1.vb 可能不是 Visual Basic 源文件。</span><span class="sxs-lookup"><span data-stu-id="07446-121">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="07446-122">在应用程序中使用输入的数据之前，需验证所有的输入内容。</span><span class="sxs-lookup"><span data-stu-id="07446-122">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="07446-123">文件的内容可能不是预期内容，并且用来读取该文件的方法可能失败。</span><span class="sxs-lookup"><span data-stu-id="07446-123">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07446-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="07446-124">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="07446-125">从文件读取</span><span class="sxs-lookup"><span data-stu-id="07446-125">Reading from Files</span></span>](reading-from-files.md)
- [<span data-ttu-id="07446-126">如何：读取具有多种格式的文本文件</span><span class="sxs-lookup"><span data-stu-id="07446-126">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="07446-127">将数据存储到剪贴板以及从剪贴板读取数据</span><span class="sxs-lookup"><span data-stu-id="07446-127">Storing Data to and Reading from the Clipboard</span></span>](../computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
