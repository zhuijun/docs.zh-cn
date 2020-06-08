---
title: 如何：将具有特定模式的文件复制到目录中
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: 7e263e2c9035db54dbb58c6c78c0647d5442504e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401701"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a><span data-ttu-id="82167-102">如何：在 Visual Basic 中将具有特定模式的文件复制到目录中</span><span class="sxs-lookup"><span data-stu-id="82167-102">How to: Copy Files with a Specific Pattern to a Directory in Visual Basic</span></span>

<span data-ttu-id="82167-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> 方法返回表示文件的路径名的只读字符串集合。</span><span class="sxs-lookup"><span data-stu-id="82167-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="82167-104">可以使用 `wildCards` 参数来指定特定模式。</span><span class="sxs-lookup"><span data-stu-id="82167-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span>  
  
 <span data-ttu-id="82167-105">如果找不到匹配的文件，则返回空集合。</span><span class="sxs-lookup"><span data-stu-id="82167-105">An empty collection is returned if no matching files are found.</span></span>  
  
 <span data-ttu-id="82167-106">可以使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> 方法将文件复制到目录。</span><span class="sxs-lookup"><span data-stu-id="82167-106">You can use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> method to copy the files to a directory.</span></span>  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a><span data-ttu-id="82167-107">将具有特定模式的文件复制到目录中</span><span class="sxs-lookup"><span data-stu-id="82167-107">To copy files with a specific pattern to a directory</span></span>  
  
1. <span data-ttu-id="82167-108">使用 `GetFiles` 方法返回文件的列表。</span><span class="sxs-lookup"><span data-stu-id="82167-108">Use the `GetFiles` method to return the list of files.</span></span> <span data-ttu-id="82167-109">此示例在指定的目录中返回所有 .rtf 文件。</span><span class="sxs-lookup"><span data-stu-id="82167-109">This example returns all .rtf files in the specified directory.</span></span>  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2. <span data-ttu-id="82167-110">使用 `CopyFile` 方法复制文件。</span><span class="sxs-lookup"><span data-stu-id="82167-110">Use the `CopyFile` method to copy the files.</span></span> <span data-ttu-id="82167-111">此示例将文件复制到名为 `testdirectory`的目录中。</span><span class="sxs-lookup"><span data-stu-id="82167-111">This example copies the files to the directory named `testdirectory`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3. <span data-ttu-id="82167-112">使用 `For` 语句关闭 `Next` 语句。</span><span class="sxs-lookup"><span data-stu-id="82167-112">Close the `For` statement with a `Next` statement.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a><span data-ttu-id="82167-113">示例</span><span class="sxs-lookup"><span data-stu-id="82167-113">Example</span></span>  

 <span data-ttu-id="82167-114">下面的示例完整地显示了上述代码片段，该示例将指定目录中的所有 .rtf 文件复制到名为 `testdirectory`的目录。</span><span class="sxs-lookup"><span data-stu-id="82167-114">The following example, which presents the above snippets in complete form, copies all .rtf files in the specified directory to the directory named `testdirectory`.</span></span>  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="82167-115">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="82167-115">.NET Framework Security</span></span>  

 <span data-ttu-id="82167-116">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="82167-116">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="82167-117">路径由于以下原因之一而无效：是零长度字符串；仅为空白；包含无效字符；是一个设备路径（开头字符为 \\\\.\\）(<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="82167-117">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="82167-118">路径无效，因为它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="82167-118">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="82167-119">目录不存在 (<xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="82167-119">The directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="82167-120">指向某个现有文件的目录 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="82167-120">The directory points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="82167-121">路径超过了系统定义的最大长度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="82167-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="82167-122">路径中的文件名或目录名包含冒号 (:)，或格式无效 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="82167-122">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="82167-123">该用户缺少查看该路径所必需的权限 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="82167-123">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span> <span data-ttu-id="82167-124">该用户缺少必要的权限 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="82167-124">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82167-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="82167-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="82167-126">如何：查找具有特定模式的子目录</span><span class="sxs-lookup"><span data-stu-id="82167-126">How to: Find Subdirectories with a Specific Pattern</span></span>](how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="82167-127">疑难解答：读取和写入文本文件</span><span class="sxs-lookup"><span data-stu-id="82167-127">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="82167-128">如何：获取目录中的文件集合</span><span class="sxs-lookup"><span data-stu-id="82167-128">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
