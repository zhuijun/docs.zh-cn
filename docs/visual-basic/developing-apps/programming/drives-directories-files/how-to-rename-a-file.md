---
title: 如何：重命名文件
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: 3de41ee6627315f0e26964b75f564ff98fe472ec
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411585"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a><span data-ttu-id="4f3e0-102">如何：在 Visual Basic 中重命名文件</span><span class="sxs-lookup"><span data-stu-id="4f3e0-102">How to: Rename a File in Visual Basic</span></span>

<span data-ttu-id="4f3e0-103">使用 `My.Computer.FileSystem` 对象的 `RenameFile` 方法可通过提供当前位置、文件名和新文件名来重命名文件。</span><span class="sxs-lookup"><span data-stu-id="4f3e0-103">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span></span> <span data-ttu-id="4f3e0-104">此方法不能用于移动文件；使用 `MoveFile` 方法可移动并重命名文件。</span><span class="sxs-lookup"><span data-stu-id="4f3e0-104">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span></span>  
  
### <a name="to-rename-a-file"></a><span data-ttu-id="4f3e0-105">重命名文件</span><span class="sxs-lookup"><span data-stu-id="4f3e0-105">To rename a file</span></span>  
  
- <span data-ttu-id="4f3e0-106">使用 `My.Computer.FileSystem.RenameFile` 方法可重命名文件。</span><span class="sxs-lookup"><span data-stu-id="4f3e0-106">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span></span> <span data-ttu-id="4f3e0-107">此示例将名为 `Test.txt` 的文件重命名为 `SecondTest.txt`。</span><span class="sxs-lookup"><span data-stu-id="4f3e0-107">This example renames the file named `Test.txt` to `SecondTest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 <span data-ttu-id="4f3e0-108">此代码示例也可作为 IntelliSense 代码片段。</span><span class="sxs-lookup"><span data-stu-id="4f3e0-108">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="4f3e0-109">在代码片段选取器中，该代码段位于“文件系统 - 处理驱动器、文件夹和文件”。 </span><span class="sxs-lookup"><span data-stu-id="4f3e0-109">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="4f3e0-110">有关详细信息，请参阅[代码片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="4f3e0-110">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4f3e0-111">可靠编程</span><span class="sxs-lookup"><span data-stu-id="4f3e0-111">Robust Programming</span></span>  

 <span data-ttu-id="4f3e0-112">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="4f3e0-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="4f3e0-113">路径由于以下原因之一而无效：是零长度字符串；仅为空白；包含无效字符；是一个设备路径（开头字符为 \\\\.\\）(<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="4f3e0-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="4f3e0-114">`newName` 包含路径信息 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="4f3e0-114">`newName` contains path information (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="4f3e0-115">路径无效，因为它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="4f3e0-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="4f3e0-116">`newName` 为 `Nothing` 或空字符串 (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="4f3e0-116">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="4f3e0-117">源文件无效或不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="4f3e0-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="4f3e0-118">不存在具有 `newName` (<xref:System.IO.IOException>) 中指定名称的现有文件或目录。</span><span class="sxs-lookup"><span data-stu-id="4f3e0-118">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="4f3e0-119">路径超过了系统定义的最大长度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="4f3e0-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="4f3e0-120">路径中的文件名或目录名包含冒号 (:)，或格式无效 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="4f3e0-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="4f3e0-121">该用户缺少查看该路径所必需的权限 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="4f3e0-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="4f3e0-122">用户没有所必需的权限 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="4f3e0-122">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f3e0-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4f3e0-123">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [<span data-ttu-id="4f3e0-124">如何：移动文件</span><span class="sxs-lookup"><span data-stu-id="4f3e0-124">How to: Move a File</span></span>](how-to-move-a-file.md)
- [<span data-ttu-id="4f3e0-125">创建、删除和移动文件和目录</span><span class="sxs-lookup"><span data-stu-id="4f3e0-125">Creating, Deleting, and Moving Files and Directories</span></span>](creating-deleting-and-moving-files-and-directories.md)
- [<span data-ttu-id="4f3e0-126">如何：在同一目录中创建文件副本</span><span class="sxs-lookup"><span data-stu-id="4f3e0-126">How to: Create a Copy of a File in the Same Directory</span></span>](how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="4f3e0-127">如何：在不同的目录中创建文件的副本</span><span class="sxs-lookup"><span data-stu-id="4f3e0-127">How to: Create a Copy of a File in a Different Directory</span></span>](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
