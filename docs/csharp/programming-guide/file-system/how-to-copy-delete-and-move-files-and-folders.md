---
title: 如何复制、删除和移动文件和文件夹 - C# 编程指南
description: 了解如何使用 File、Directory、FileInfo 和 DirectoryInfo 类复制、删除和移动文件和文件夹。
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 208502651080f4fd614e34d1bf5b088dfb1207a6
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303356"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="8954e-103">如何复制、删除和移动文件和文件夹（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="8954e-103">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>
<span data-ttu-id="8954e-104">以下示例演示如何从 <xref:System.IO?displayProperty=nameWithType> 命名空间使用 <xref:System.IO.File?displayProperty=nameWithType>、<xref:System.IO.Directory?displayProperty=nameWithType>、<xref:System.IO.FileInfo?displayProperty=nameWithType> 和 <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> 类以同步方式复制、移动和删除文件与文件夹。</span><span class="sxs-lookup"><span data-stu-id="8954e-104">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="8954e-105">这些示例未提供进度栏或其他任何用户界面。</span><span class="sxs-lookup"><span data-stu-id="8954e-105">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="8954e-106">如果希望提供一个标准进度对话框，请参阅[如何提供文件操作进度对话框](how-to-provide-a-progress-dialog-box-for-file-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="8954e-106">If you want to provide a standard progress dialog box, see [How to provide a progress dialog box for file operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="8954e-107">操作多个文件时，请使用 <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> 提供事件，以便可以计算进度。</span><span class="sxs-lookup"><span data-stu-id="8954e-107">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="8954e-108">另一种方法是使用平台调用来调用 Windows Shell 中相应的文件相关方法。</span><span class="sxs-lookup"><span data-stu-id="8954e-108">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="8954e-109">有关如何异步执行这些文件操作的信息，请参阅[异步文件 I/O](../../../standard/io/asynchronous-file-i-o.md)。</span><span class="sxs-lookup"><span data-stu-id="8954e-109">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8954e-110">示例</span><span class="sxs-lookup"><span data-stu-id="8954e-110">Example</span></span>  
 <span data-ttu-id="8954e-111">以下示例演示如何复制文件和目录。</span><span class="sxs-lookup"><span data-stu-id="8954e-111">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a><span data-ttu-id="8954e-112">示例</span><span class="sxs-lookup"><span data-stu-id="8954e-112">Example</span></span>  
 <span data-ttu-id="8954e-113">以下示例演示如何移动文件和目录。</span><span class="sxs-lookup"><span data-stu-id="8954e-113">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a><span data-ttu-id="8954e-114">示例</span><span class="sxs-lookup"><span data-stu-id="8954e-114">Example</span></span>  
 <span data-ttu-id="8954e-115">以下示例演示如何删除文件和目录。</span><span class="sxs-lookup"><span data-stu-id="8954e-115">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="8954e-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8954e-116">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="8954e-117">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="8954e-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8954e-118">文件系统和注册表（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="8954e-118">File System and the Registry (C# Programming Guide)</span></span>](index.md)
- [<span data-ttu-id="8954e-119">如何提供文件操作进度对话框</span><span class="sxs-lookup"><span data-stu-id="8954e-119">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [<span data-ttu-id="8954e-120">文件和流 I/O</span><span class="sxs-lookup"><span data-stu-id="8954e-120">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="8954e-121">通用 I/O 任务</span><span class="sxs-lookup"><span data-stu-id="8954e-121">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
