---
title: 如何：创建目录
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 0da915054a2e38c778f15bc0b472fe9b02521189
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401662"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a><span data-ttu-id="60aa5-102">如何：在 Visual Basic 中创建目录</span><span class="sxs-lookup"><span data-stu-id="60aa5-102">How to: Create a Directory in Visual Basic</span></span>

<span data-ttu-id="60aa5-103">使用 `My.Computer.FileSystem` 对象的 `CreateDirectory` 方法来创建目录。</span><span class="sxs-lookup"><span data-stu-id="60aa5-103">Use the `CreateDirectory` method of the `My.Computer.FileSystem` object to create directories.</span></span>  
  
 <span data-ttu-id="60aa5-104">如果该目录已存在，则不引发任何异常。</span><span class="sxs-lookup"><span data-stu-id="60aa5-104">If the directory already exists, no exception is thrown.</span></span>  
  
### <a name="to-create-a-directory"></a><span data-ttu-id="60aa5-105">创建目录</span><span class="sxs-lookup"><span data-stu-id="60aa5-105">To create a directory</span></span>  
  
- <span data-ttu-id="60aa5-106">使用 `CreateDirectory` 方法，指定将在其中创建目录的位置的完整路径。</span><span class="sxs-lookup"><span data-stu-id="60aa5-106">Use the `CreateDirectory` method by specifying the full path of the location where the directory should be created.</span></span> <span data-ttu-id="60aa5-107">此示例在 `NewDirectory` 中创建目录 `C:\Documents and Settings\All Users\Documents`。</span><span class="sxs-lookup"><span data-stu-id="60aa5-107">This example creates the directory `NewDirectory` in `C:\Documents and Settings\All Users\Documents`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="60aa5-108">可靠编程</span><span class="sxs-lookup"><span data-stu-id="60aa5-108">Robust Programming</span></span>  

 <span data-ttu-id="60aa5-109">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="60aa5-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="60aa5-110">目录名称格式不正确。</span><span class="sxs-lookup"><span data-stu-id="60aa5-110">The directory name is malformed.</span></span> <span data-ttu-id="60aa5-111">例如，它包含非法字符或仅为空白 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="60aa5-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="60aa5-112">要创建的目录的父目录为只读 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="60aa5-112">The parent directory of the directory to be created is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="60aa5-113">目录名称为 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="60aa5-113">The directory name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="60aa5-114">目录名称过长 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="60aa5-114">The directory name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="60aa5-115">目录名称是一个冒号“:”(<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="60aa5-115">The directory name is a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="60aa5-116">用户无权创建目录 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="60aa5-116">The user does not have permission to create the directory (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="60aa5-117">用户在部分信任情况下缺少权限 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="60aa5-117">The user lacks permissions in a partial-trust situation (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60aa5-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="60aa5-118">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [<span data-ttu-id="60aa5-119">创建、删除和移动文件和目录</span><span class="sxs-lookup"><span data-stu-id="60aa5-119">Creating, Deleting, and Moving Files and Directories</span></span>](creating-deleting-and-moving-files-and-directories.md)
