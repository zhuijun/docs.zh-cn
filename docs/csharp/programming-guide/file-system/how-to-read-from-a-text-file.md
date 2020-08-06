---
title: 如何读取文本文件中的内容 - C# 编程指南
description: 了解如何使用 File 类中的静态方法读取文本文件中的内容。 查看代码示例和其他可用资源。
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 80ac6f8412f456b23d05ee87882dca8e16a132c3
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301653"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="4dc84-104">如何读取文本文件中的内容（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="4dc84-104">How to read from a text file (C# Programming Guide)</span></span>
<span data-ttu-id="4dc84-105">此示例通过使用 <xref:System.IO.File?displayProperty=nameWithType> 类的 <xref:System.IO.File.ReadAllText%2A> 和 <xref:System.IO.File.ReadAllLines%2A> 静态方法来确定文本文件的内容。</span><span class="sxs-lookup"><span data-stu-id="4dc84-105">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=nameWithType> class.</span></span>  
  
<span data-ttu-id="4dc84-106">有关使用 <xref:System.IO.StreamReader> 的示例，请参阅[如何一次一行地读取文本文件](./how-to-read-a-text-file-one-line-at-a-time.md)。</span><span class="sxs-lookup"><span data-stu-id="4dc84-106">For an example that uses <xref:System.IO.StreamReader>, see [How to read a text file one line at a time](./how-to-read-a-text-file-one-line-at-a-time.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="4dc84-107">此示例所用的文件是在主题[如何写入文本文件](./how-to-write-to-a-text-file.md)中创建的。</span><span class="sxs-lookup"><span data-stu-id="4dc84-107">The files that are used in this example are created in the topic [How to write to a text file](./how-to-write-to-a-text-file.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="4dc84-108">示例</span><span class="sxs-lookup"><span data-stu-id="4dc84-108">Example</span></span>  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4dc84-109">编译代码</span><span class="sxs-lookup"><span data-stu-id="4dc84-109">Compiling the Code</span></span>  
 <span data-ttu-id="4dc84-110">将代码复制并粘贴到 C# 控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="4dc84-110">Copy the code and paste it into a C# console application.</span></span>  
  
<span data-ttu-id="4dc84-111">如果不使用[如何写入文本文件](./how-to-write-to-a-text-file.md)中的文本文件，请将 `ReadAllText` 和 `ReadAllLines` 的参数替换为计算机上的适当路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="4dc84-111">If you are not using the text files from [How to write to a text file](./how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>
  
## <a name="robust-programming"></a><span data-ttu-id="4dc84-112">可靠编程</span><span class="sxs-lookup"><span data-stu-id="4dc84-112">Robust Programming</span></span>  
 <span data-ttu-id="4dc84-113">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="4dc84-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="4dc84-114">不存在该文件，或者指定位置不存在该文件。</span><span class="sxs-lookup"><span data-stu-id="4dc84-114">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="4dc84-115">检查文件名的路径和拼写。</span><span class="sxs-lookup"><span data-stu-id="4dc84-115">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="4dc84-116">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="4dc84-116">.NET Security</span></span>  
 <span data-ttu-id="4dc84-117">不要依赖文件名来确定文件的内容。</span><span class="sxs-lookup"><span data-stu-id="4dc84-117">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="4dc84-118">例如，文件 `myFile.cs` 可能不是 C# 源文件。</span><span class="sxs-lookup"><span data-stu-id="4dc84-118">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dc84-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="4dc84-119">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="4dc84-120">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="4dc84-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4dc84-121">文件系统和注册表（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="4dc84-121">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
