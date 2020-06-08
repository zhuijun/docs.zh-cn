---
title: 如何：删除文件
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 0c8213786b8073d784f1f3ea51417741d5ad4cba
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401649"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="5f20b-102">如何：在 Visual Basic 中删除文件</span><span class="sxs-lookup"><span data-stu-id="5f20b-102">How to: Delete a File in Visual Basic</span></span>

<span data-ttu-id="5f20b-103">通过 `My.Computer.FileSystem` 对象的 `DeleteFile` 方法，可以删除文件。</span><span class="sxs-lookup"><span data-stu-id="5f20b-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="5f20b-104">它提供的选项包括：是否将已删除的文件发送到“回收站”  、是否要求用户确认应删除该文件，以及当用户取消操作时要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="5f20b-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="5f20b-105">删除文本文件</span><span class="sxs-lookup"><span data-stu-id="5f20b-105">To delete a text file</span></span>  
  
- <span data-ttu-id="5f20b-106">使用 `DeleteFile` 方法删除文件。</span><span class="sxs-lookup"><span data-stu-id="5f20b-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="5f20b-107">以下代码演示如何删除名为 `test.txt` 的文件。</span><span class="sxs-lookup"><span data-stu-id="5f20b-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="5f20b-108">删除文本文件，并要求用户确认应删除该文件</span><span class="sxs-lookup"><span data-stu-id="5f20b-108">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
- <span data-ttu-id="5f20b-109">使用 `DeleteFile` 方法删除文件，同时将 `showUI` 设置为 `AllDialogs`。</span><span class="sxs-lookup"><span data-stu-id="5f20b-109">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="5f20b-110">以下代码演示如何删除名为 `test.txt` 的文件，并允许用户确认是否应删除该文件。</span><span class="sxs-lookup"><span data-stu-id="5f20b-110">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="5f20b-111">删除文本文件并将其发送到“回收站”</span><span class="sxs-lookup"><span data-stu-id="5f20b-111">To delete a text file and send it to the Recycle Bin</span></span>  
  
- <span data-ttu-id="5f20b-112">使用 `DeleteFile` 方法删除文件，并为 `recycle` 参数指定 `SendToRecycleBin`。</span><span class="sxs-lookup"><span data-stu-id="5f20b-112">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="5f20b-113">以下代码演示如何删除名为 `test.txt` 的文件并将其发送到“回收站”  。</span><span class="sxs-lookup"><span data-stu-id="5f20b-113">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5f20b-114">可靠编程</span><span class="sxs-lookup"><span data-stu-id="5f20b-114">Robust Programming</span></span>  

 <span data-ttu-id="5f20b-115">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="5f20b-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="5f20b-116">路径由于以下原因之一而无效：是零长度字符串；仅为空白；包含无效字符；是一个设备路径（开头字符为 \\\\.\\）(<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="5f20b-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="5f20b-117">路径无效，因为它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="5f20b-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="5f20b-118">路径超过了系统定义的最大长度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="5f20b-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="5f20b-119">路径中的文件名或文件夹名包含冒号 (:)，或其格式无效 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="5f20b-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="5f20b-120">该文件正在使用中 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="5f20b-120">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="5f20b-121">该用户缺少查看该路径所必需的权限 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="5f20b-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="5f20b-122">该文件不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="5f20b-122">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="5f20b-123">用户无权删除文件，或文件为只读 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="5f20b-123">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="5f20b-124">存在部分信任的情况，在此情况下用户没有足够的权限 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="5f20b-124">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="5f20b-125">用户取消了该操作，并且 `onUserCancel` 设置为 `ThrowException` (<xref:System.OperationCanceledException>)。</span><span class="sxs-lookup"><span data-stu-id="5f20b-125">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f20b-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f20b-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [<span data-ttu-id="5f20b-127">如何：获取目录中的文件集合</span><span class="sxs-lookup"><span data-stu-id="5f20b-127">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
