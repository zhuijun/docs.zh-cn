---
title: 如何写入文本文件 - C# 编程指南
description: 了解如何使用 C# 编写文本文件。 查看一些代码示例和其他可用资源。
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: 4108163121d56268b810121ca3ae2b2c1338aeab
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301640"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="38b45-104">如何写入文本文件（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="38b45-104">How to write to a text file (C# Programming Guide)</span></span>
<span data-ttu-id="38b45-105">以下示例给出了将文本写入文件的各种方法。</span><span class="sxs-lookup"><span data-stu-id="38b45-105">These examples show various ways to write text to a file.</span></span> <span data-ttu-id="38b45-106">前两个示例对 <xref:System.IO.File?displayProperty=nameWithType> 类使用静态便捷方法以将任何 `IEnumerable<string>` 的每个元素和字符串写入文本文件。</span><span class="sxs-lookup"><span data-stu-id="38b45-106">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a string to a text file.</span></span> <span data-ttu-id="38b45-107">示例 3 展示了在写入文件时必须分别处理文本的每一行时，如何将文本添加到文件。</span><span class="sxs-lookup"><span data-stu-id="38b45-107">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="38b45-108">示例 1-3 覆盖文件中的所有现有内容，但示例 4 展示如何将文本追加到现有文件。</span><span class="sxs-lookup"><span data-stu-id="38b45-108">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="38b45-109">这些示例都将字符串文本写入了文件。</span><span class="sxs-lookup"><span data-stu-id="38b45-109">These examples all write string literals to files.</span></span> <span data-ttu-id="38b45-110">如果想设置写入文件的文本的格式，请使用 <xref:System.String.Format%2A> 方法或 C# [字符串内插](../../language-reference/tokens/interpolated.md)功能。</span><span class="sxs-lookup"><span data-stu-id="38b45-110">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38b45-111">示例</span><span class="sxs-lookup"><span data-stu-id="38b45-111">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="38b45-112">可靠编程</span><span class="sxs-lookup"><span data-stu-id="38b45-112">Robust Programming</span></span>  
 <span data-ttu-id="38b45-113">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="38b45-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="38b45-114">文件已存在并且为只读。</span><span class="sxs-lookup"><span data-stu-id="38b45-114">The file exists and is read-only.</span></span>  
  
- <span data-ttu-id="38b45-115">路径名可能太长。</span><span class="sxs-lookup"><span data-stu-id="38b45-115">The path name may be too long.</span></span>  
  
- <span data-ttu-id="38b45-116">磁盘可能已满。</span><span class="sxs-lookup"><span data-stu-id="38b45-116">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38b45-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="38b45-117">See also</span></span>

- [<span data-ttu-id="38b45-118">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="38b45-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="38b45-119">文件系统和注册表（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="38b45-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="38b45-120">示例：将集合保存到应用程序存储</span><span class="sxs-lookup"><span data-stu-id="38b45-120">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
