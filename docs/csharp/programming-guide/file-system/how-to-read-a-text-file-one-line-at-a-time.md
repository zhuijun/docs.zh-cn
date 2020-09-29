---
title: 如何一次一行地读取文本文件 - C# 编程指南
description: 了解如何一次一行地读取文本文件。 查看代码示例和其他可用资源。
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: 93645ef78f1ceb3cc4cf1d20ac73112e86957293
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178510"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a><span data-ttu-id="08a19-104">如何一次一行地读取文本文件（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="08a19-104">How to read a text file one line at a time (C# Programming Guide)</span></span>

<span data-ttu-id="08a19-105">此示例使用 `StreamReader` 类的 `ReadLine` 方法，一次一行地将文本文件内容读入字符串。</span><span class="sxs-lookup"><span data-stu-id="08a19-105">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="08a19-106">每个文本行都存储到字符串 `line` 中并显示在屏幕上。</span><span class="sxs-lookup"><span data-stu-id="08a19-106">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08a19-107">示例</span><span class="sxs-lookup"><span data-stu-id="08a19-107">Example</span></span>  
  
```csharp
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine(line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="08a19-108">编译代码</span><span class="sxs-lookup"><span data-stu-id="08a19-108">Compiling the Code</span></span>  

 <span data-ttu-id="08a19-109">复制代码，并将其粘贴到控制台应用程序的 `Main` 方法中。</span><span class="sxs-lookup"><span data-stu-id="08a19-109">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="08a19-110">将 `"c:\test.txt"` 替换为实际文件名。</span><span class="sxs-lookup"><span data-stu-id="08a19-110">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="08a19-111">可靠编程</span><span class="sxs-lookup"><span data-stu-id="08a19-111">Robust Programming</span></span>  

 <span data-ttu-id="08a19-112">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="08a19-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="08a19-113">文件可能不存在。</span><span class="sxs-lookup"><span data-stu-id="08a19-113">The file may not exist.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="08a19-114">.NET 安全性</span><span class="sxs-lookup"><span data-stu-id="08a19-114">.NET Security</span></span>  

 <span data-ttu-id="08a19-115">不要根据文件的名称来判断文件的内容。</span><span class="sxs-lookup"><span data-stu-id="08a19-115">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="08a19-116">例如，文件 `myFile.cs` 可能不是 C# 源文件。</span><span class="sxs-lookup"><span data-stu-id="08a19-116">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08a19-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="08a19-117">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="08a19-118">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="08a19-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="08a19-119">文件系统和注册表（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="08a19-119">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
