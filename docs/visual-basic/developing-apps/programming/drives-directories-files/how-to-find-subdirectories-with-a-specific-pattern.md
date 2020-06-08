---
title: 如何：查找具有特定模式的子目录
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: 5b57914a518b568732955e5c73bb2031824c84dd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401623"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="5e7c4-102">如何：在 Visual Basic 中查找具有特定模式的子目录</span><span class="sxs-lookup"><span data-stu-id="5e7c4-102">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>

<span data-ttu-id="5e7c4-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> 方法返回一个只读字符串集合，这些字符串表示目录中子目录的路径名称。</span><span class="sxs-lookup"><span data-stu-id="5e7c4-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="5e7c4-104">可以使用 `wildCards` 参数来指定特定模式。</span><span class="sxs-lookup"><span data-stu-id="5e7c4-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="5e7c4-105">如果要在搜索中包含子目录的内容，请将 `searchType` 参数设置为 `SearchOption.SearchAllSubDirectories`。</span><span class="sxs-lookup"><span data-stu-id="5e7c4-105">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>

<span data-ttu-id="5e7c4-106">如果没有找到与指定模式匹配的目录，则返回一个空集合。</span><span class="sxs-lookup"><span data-stu-id="5e7c4-106">An empty collection is returned if no directories matching the specified pattern are found.</span></span>

## <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="5e7c4-107">查找具有特定模式的子目录</span><span class="sxs-lookup"><span data-stu-id="5e7c4-107">To find subdirectories with a specific pattern</span></span>

<span data-ttu-id="5e7c4-108">使用 `GetDirectories` 方法，并提供要搜索的目录的名称和路径。</span><span class="sxs-lookup"><span data-stu-id="5e7c4-108">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="5e7c4-109">以下示例返回名称中包含单词“Logs”的目录结构中的所有目录，并将它们添加到 `ListBox1`。</span><span class="sxs-lookup"><span data-stu-id="5e7c4-109">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a><span data-ttu-id="5e7c4-110">可靠编程</span><span class="sxs-lookup"><span data-stu-id="5e7c4-110">Robust Programming</span></span>

<span data-ttu-id="5e7c4-111">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="5e7c4-111">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="5e7c4-112">路径由于以下原因之一而无效：是零长度字符串；仅为空白；包含无效字符；是一个设备路径（开头字符为 \\\\.\\）(<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="5e7c4-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="5e7c4-113">路径无效，因为它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="5e7c4-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="5e7c4-114">有一个或多个指定通配符是 `Nothing`、空字符串，或仅为空格 (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="5e7c4-114">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="5e7c4-115">`directory` 不存在 (<xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="5e7c4-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="5e7c4-116">`directory` 指向某个现有文件 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="5e7c4-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="5e7c4-117">路径超过了系统定义的最大长度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="5e7c4-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="5e7c4-118">路径中的文件名或文件夹名包含冒号 (:)，或其格式无效 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="5e7c4-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="5e7c4-119">该用户缺少查看该路径所必需的权限 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="5e7c4-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="5e7c4-120">该用户缺少必要的权限 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="5e7c4-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="5e7c4-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5e7c4-121">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [<span data-ttu-id="5e7c4-122">如何：查找具有特定模式的文件</span><span class="sxs-lookup"><span data-stu-id="5e7c4-122">How to: Find Files with a Specific Pattern</span></span>](how-to-find-files-with-a-specific-pattern.md)
