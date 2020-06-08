---
title: 如何：分析文件路径
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: eb7714a8594c0bce344eb2e48ebc5053dc3bfbb4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359937"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="3172e-102">如何：在 Visual Basic 中分析文件路径</span><span class="sxs-lookup"><span data-stu-id="3172e-102">How to: Parse File Paths in Visual Basic</span></span>

<span data-ttu-id="3172e-103">分析文件路径时，可参考 <xref:Microsoft.VisualBasic.FileIO.FileSystem> 对象提供的多种有用的方法。</span><span class="sxs-lookup"><span data-stu-id="3172e-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
- <span data-ttu-id="3172e-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> 方法采用了两个路径并返回格式正确的组合路径。</span><span class="sxs-lookup"><span data-stu-id="3172e-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
- <span data-ttu-id="3172e-105"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> 方法将返回所提供的路径的父级的绝对路径。</span><span class="sxs-lookup"><span data-stu-id="3172e-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
- <span data-ttu-id="3172e-106"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> 方法将返回一个 <xref:System.IO.FileInfo> 对象，查询该对象可确定文件的属性，例如文件名和路径。</span><span class="sxs-lookup"><span data-stu-id="3172e-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="3172e-107">不要根据文件的扩展名来判断文件的内容。</span><span class="sxs-lookup"><span data-stu-id="3172e-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="3172e-108">例如，文件 Form1.vb 可能不是 Visual Basic 源文件。</span><span class="sxs-lookup"><span data-stu-id="3172e-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="3172e-109">确定文件的名称和路径</span><span class="sxs-lookup"><span data-stu-id="3172e-109">To determine a file's name and path</span></span>  
  
- <span data-ttu-id="3172e-110">可使用 <xref:System.IO.FileInfo.DirectoryName%2A> 对象的 <xref:System.IO.FileInfo.Name%2A> 和 <xref:System.IO.FileInfo> 属性来确定文件的名称和路径。</span><span class="sxs-lookup"><span data-stu-id="3172e-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="3172e-111">此示例确定了名称和路径，并将其显示了出来。</span><span class="sxs-lookup"><span data-stu-id="3172e-111">This example determines the name and path and displays them.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#54)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="3172e-112">组合文件的名称和目录以创建完整的路径</span><span class="sxs-lookup"><span data-stu-id="3172e-112">To combine a file's name and directory to create the full path</span></span>  
  
- <span data-ttu-id="3172e-113">使用 `CombinePath` 方法，用于提供目录和名称。</span><span class="sxs-lookup"><span data-stu-id="3172e-113">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="3172e-114">此示例采用了上例中创建的字符串 `folderPath` 和 `fileName` ，然后将其组合在一起并显示结果。</span><span class="sxs-lookup"><span data-stu-id="3172e-114">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="3172e-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3172e-115">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>
- <xref:System.IO.FileInfo>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>
- [<span data-ttu-id="3172e-116">如何：获取目录中的文件集合</span><span class="sxs-lookup"><span data-stu-id="3172e-116">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
