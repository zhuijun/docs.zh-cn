---
title: 如何：在独立存储中创建文件和目录
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
ms.openlocfilehash: d5e086e77ab6309fa0757ef32b620e0fdbc1f627
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413035"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="3529b-102">如何：在独立存储中创建文件和目录</span><span class="sxs-lookup"><span data-stu-id="3529b-102">How to: Create Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="3529b-103">获得独立存储区之后，您可以创建用于存储数据的目录和文件。</span><span class="sxs-lookup"><span data-stu-id="3529b-103">After you have obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="3529b-104">在存储中，文件名和目录名称是相对于虚拟文件系统的根目录进行指定。</span><span class="sxs-lookup"><span data-stu-id="3529b-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="3529b-105">若要创建目录，请使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> 实例方法。</span><span class="sxs-lookup"><span data-stu-id="3529b-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="3529b-106">如果您为不存在的目录指定了一个子目录，则会同时创建这两个目录。</span><span class="sxs-lookup"><span data-stu-id="3529b-106">If you specify a subdirectory of an directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="3529b-107">如果您指定的目录已存在，该方法将返回而不创建目录，并且不会引发异常。</span><span class="sxs-lookup"><span data-stu-id="3529b-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="3529b-108">但是，如果您指定的目录名称包含无效字符，将引发 <xref:System.IO.IsolatedStorage.IsolatedStorageException> 异常。</span><span class="sxs-lookup"><span data-stu-id="3529b-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="3529b-109">若要创建文件，请使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="3529b-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="3529b-110">在 Windows 操作系统，独立存储文件和目录名不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="3529b-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="3529b-111">这样，如果您创建了一个名为 `ThisFile.txt` 的文件，然后又创建了名为 `THISFILE.TXT` 的另一个文件，实际上只创建了一个文件。</span><span class="sxs-lookup"><span data-stu-id="3529b-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="3529b-112">文件名保留原始大小写只为了方便本文演示。</span><span class="sxs-lookup"><span data-stu-id="3529b-112">The file name keeps its original casing for display purposes.</span></span>  

 <span data-ttu-id="3529b-113">如果路径包含的目录不存在，则创建独立存储文件会引发 <xref:System.IO.IsolatedStorage.IsolatedStorageException>。</span><span class="sxs-lookup"><span data-stu-id="3529b-113">Isolated storage file creation will throw an <xref:System.IO.IsolatedStorage.IsolatedStorageException> if the path contains a directory that does not exist.</span></span>
  
## <a name="example"></a><span data-ttu-id="3529b-114">示例</span><span class="sxs-lookup"><span data-stu-id="3529b-114">Example</span></span>  
 <span data-ttu-id="3529b-115">下面的代码示例展示了如何在独立存储中创建文件和目录。</span><span class="sxs-lookup"><span data-stu-id="3529b-115">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3529b-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="3529b-116">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [<span data-ttu-id="3529b-117">独立存储</span><span class="sxs-lookup"><span data-stu-id="3529b-117">Isolated Storage</span></span>](isolated-storage.md)
