---
title: 如何：在同一目录中创建文件副本
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 741f0c80ba268369ebdd598460e9d5fa13d09571
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401675"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="bb3bb-102">如何：在同一目录中创建文件副本 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb3bb-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>

<span data-ttu-id="bb3bb-103">使用 `My.Computer.FileSystem.CopyFile` 方法复制文件。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="bb3bb-104">使用参数可以覆盖现有文件、重命名文件、显示操作的进度以及允许用户取消操作。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="bb3bb-105">在同一文件夹中创建文件副本</span><span class="sxs-lookup"><span data-stu-id="bb3bb-105">To create a copy of a file in the same folder</span></span>  
  
- <span data-ttu-id="bb3bb-106">使用 `CopyFile` 方法，提供目标文件和位置。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="bb3bb-107">下面的示例创建名为 `test2.txt` 的 `test.txt` 副本。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="bb3bb-108">通过覆盖现有文件在同一文件夹中创建文件副本</span><span class="sxs-lookup"><span data-stu-id="bb3bb-108">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
- <span data-ttu-id="bb3bb-109">使用 `CopyFile` 方法，提供目标文件和位置，并将 `overwrite` 设置为 `True`。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-109">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="bb3bb-110">下面的示例创建名为 `test2.txt` 的 `test.txt` 副本，并用该名称覆盖任何现有文件。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-110">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a><span data-ttu-id="bb3bb-111">可靠编程</span><span class="sxs-lookup"><span data-stu-id="bb3bb-111">Robust Programming</span></span>  

 <span data-ttu-id="bb3bb-112">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="bb3bb-112">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="bb3bb-113">路径由于以下原因之一而无效：是零长度字符串；仅为空白；包含无效字符；是一个设备路径（开头字符为 \\\\.\\）(<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="bb3bb-114">系统无法检索绝对路径 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-114">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="bb3bb-115">路径无效，因为它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="bb3bb-116">源文件无效或不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-116">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="bb3bb-117">合并路径指向现有目录 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-117">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="bb3bb-118">存在目标文件，并且 `overwrite` 设置为 `False` (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-118">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="bb3bb-119">用户没有足够的权限访问文件 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-119">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="bb3bb-120">目标文件夹中的同名文件正在使用中 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-120">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="bb3bb-121">路径中的文件名或文件夹名包含冒号 (:)，或其格式无效 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-121">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="bb3bb-122">`ShowUI` 设置为 `True`、`onUserCancel` 设置为 `ThrowException`，并且用户已取消操作 (<xref:System.OperationCanceledException>)。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-122">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="bb3bb-123">`ShowUI` 设置为 `True`、`onUserCancel` 设置为 `ThrowException`，并出现未指定的 I/O 错误 (<xref:System.OperationCanceledException>)。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="bb3bb-124">路径超过了系统定义的最大长度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-124">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="bb3bb-125">用户没有必需的权限 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="bb3bb-126">该用户缺少查看该路径所必需的权限 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="bb3bb-126">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb3bb-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bb3bb-127">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="bb3bb-128">如何：将具有特定模式的文件复制到目录中</span><span class="sxs-lookup"><span data-stu-id="bb3bb-128">How to: Copy Files with a Specific Pattern to a Directory</span></span>](how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="bb3bb-129">如何：在不同的目录中创建文件的副本</span><span class="sxs-lookup"><span data-stu-id="bb3bb-129">How to: Create a Copy of a File in a Different Directory</span></span>](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="bb3bb-130">如何：将一个目录复制到另一个目录</span><span class="sxs-lookup"><span data-stu-id="bb3bb-130">How to: Copy a Directory to Another Directory</span></span>](how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="bb3bb-131">如何：重命名文件</span><span class="sxs-lookup"><span data-stu-id="bb3bb-131">How to: Rename a File</span></span>](how-to-rename-a-file.md)
