---
title: 如何获取有关文件、文件夹和驱动器的信息 - C# 编程指南
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: 32aced17634a1406e2fce0af9c2a92f7a5eb9b40
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241612"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a><span data-ttu-id="3b62d-102">如何获取有关文件、文件夹和驱动器的信息（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="3b62d-102">How to get information about files, folders, and drives  (C# Programming Guide)</span></span>
<span data-ttu-id="3b62d-103">在 .NET 中，可以使用以下类访问文件系统信息：</span><span class="sxs-lookup"><span data-stu-id="3b62d-103">In .NET, you can access file system information by using the following classes:</span></span>  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 <span data-ttu-id="3b62d-104"><xref:System.IO.FileInfo> 和 <xref:System.IO.DirectoryInfo> 类表示文件或目录，并包含用于公开 NTFS 文件系统所支持的许多文件特性的属性。</span><span class="sxs-lookup"><span data-stu-id="3b62d-104">The <xref:System.IO.FileInfo> and <xref:System.IO.DirectoryInfo> classes represent a file or directory and contain properties that expose many of the file attributes that are supported by the NTFS file system.</span></span> <span data-ttu-id="3b62d-105">它们还包含用于打开、关闭、移动和删除文件和文件夹的方法。</span><span class="sxs-lookup"><span data-stu-id="3b62d-105">They also contain methods for opening, closing, moving, and deleting files and folders.</span></span> <span data-ttu-id="3b62d-106">可以通过将表示文件、文件夹或驱动器名称的字符串传入构造函数来创建这些类的实例：</span><span class="sxs-lookup"><span data-stu-id="3b62d-106">You can create instances of these classes by passing a string that represents the name of the file, folder, or drive in to the constructor:</span></span>  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 <span data-ttu-id="3b62d-107">还可以使用对 <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType><xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType> 和 <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType> 的调用来获取文件、文件夹或驱动器的名称。</span><span class="sxs-lookup"><span data-stu-id="3b62d-107">You can also obtain the names of files, folders, or drives by using calls to <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, and <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="3b62d-108"><xref:System.IO.Directory?displayProperty=nameWithType> 和 <xref:System.IO.File?displayProperty=nameWithType> 类提供相关静态方法，用于检索有关目录和文件的信息。</span><span class="sxs-lookup"><span data-stu-id="3b62d-108">The <xref:System.IO.Directory?displayProperty=nameWithType> and <xref:System.IO.File?displayProperty=nameWithType> classes provide static methods for retrieving information about directories and files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b62d-109">示例</span><span class="sxs-lookup"><span data-stu-id="3b62d-109">Example</span></span>  
 <span data-ttu-id="3b62d-110">下面的示例演示用于访问有关文件和文件夹的信息的各种方法。</span><span class="sxs-lookup"><span data-stu-id="3b62d-110">The following example shows various ways to access information about files and folders.</span></span>  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="3b62d-111">可靠编程</span><span class="sxs-lookup"><span data-stu-id="3b62d-111">Robust Programming</span></span>  
 <span data-ttu-id="3b62d-112">处理用户指定的路径字符串时，还应针对以下情况处理异常：</span><span class="sxs-lookup"><span data-stu-id="3b62d-112">When you process user-specified path strings, you should also handle exceptions for the following conditions:</span></span>  
  
- <span data-ttu-id="3b62d-113">文件名格式不正确。</span><span class="sxs-lookup"><span data-stu-id="3b62d-113">The file name is malformed.</span></span> <span data-ttu-id="3b62d-114">例如，它包含无效字符或只包含空格。</span><span class="sxs-lookup"><span data-stu-id="3b62d-114">For example, it contains invalid characters or only white space.</span></span>  
  
- <span data-ttu-id="3b62d-115">文件名为 null。</span><span class="sxs-lookup"><span data-stu-id="3b62d-115">The file name is null.</span></span>  
  
- <span data-ttu-id="3b62d-116">文件名超过系统定义的最大长度。</span><span class="sxs-lookup"><span data-stu-id="3b62d-116">The file name is longer than the system-defined maximum length.</span></span>  
  
- <span data-ttu-id="3b62d-117">文件名包含冒号 (:)。</span><span class="sxs-lookup"><span data-stu-id="3b62d-117">The file name contains a colon (:).</span></span>  
  
 <span data-ttu-id="3b62d-118">如果应用程序没有足够权限来读取指定文件，`Exists` 方法会返回 `false`（无论路径是否存在）；该方法不会引发异常。</span><span class="sxs-lookup"><span data-stu-id="3b62d-118">If the application does not have sufficient permissions to read the specified file, the `Exists` method returns `false` regardless of whether a path exists; the method does not throw an exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b62d-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="3b62d-119">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="3b62d-120">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="3b62d-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3b62d-121">文件系统和注册表（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="3b62d-121">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
