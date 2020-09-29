---
title: 如何查询文件夹中文本文件的内容 (LINQ) (C#)
description: 了解如何使用 C# 中的 LINQ 查询目录树中的所有文件，打开每个文件并检查其内容。
ms.date: 07/20/2015
ms.assetid: f5b4dce7-1a34-4eb4-9bf1-60d5bdda264c
ms.openlocfilehash: a1f3e29751cd91ac1fd8e6601aa078d967776f5a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159015"
---
# <a name="how-to-query-the-contents-of-text-files-in-a-folder-linq-c"></a><span data-ttu-id="c96cc-103">如何查询文件夹中文本文件的内容 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="c96cc-103">How to query the contents of text files in a folder (LINQ) (C#)</span></span>

<span data-ttu-id="c96cc-104">此示例演示如何查询指定目录树中的所有文件、打开每个文件并检查其内容。</span><span class="sxs-lookup"><span data-stu-id="c96cc-104">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="c96cc-105">此类技术可用于对目录树的内容创建索引或反向索引。</span><span class="sxs-lookup"><span data-stu-id="c96cc-105">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="c96cc-106">此示例中执行的是简单的字符串搜索。</span><span class="sxs-lookup"><span data-stu-id="c96cc-106">A simple string search is performed in this example.</span></span> <span data-ttu-id="c96cc-107">但是，可使用正则表达式执行类型更复杂的模式匹配。</span><span class="sxs-lookup"><span data-stu-id="c96cc-107">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="c96cc-108">有关详细信息，请参阅[如何将 LINQ 查询与正则表达式合并 (C#)](./how-to-combine-linq-queries-with-regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="c96cc-108">For more information, see [How to combine LINQ queries with regular expressions (C#)](./how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c96cc-109">示例</span><span class="sxs-lookup"><span data-stu-id="c96cc-109">Example</span></span>  
  
```csharp  
class QueryContents  
{  
    public static void Main()  
    {  
        // Modify this path as necessary.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        string searchTerm = @"Visual Studio";  
  
        // Search the contents of each file.  
        // A regular expression created with the RegEx class  
        // could be used instead of the Contains method.  
        // queryMatchingFiles is an IEnumerable<string>.  
        var queryMatchingFiles =  
            from file in fileList  
            where file.Extension == ".htm"  
            let fileText = GetFileText(file.FullName)  
            where fileText.Contains(searchTerm)  
            select file.FullName;  
  
        // Execute the query.  
        Console.WriteLine("The term \"{0}\" was found in:", searchTerm);  
        foreach (string filename in queryMatchingFiles)  
        {  
            Console.WriteLine(filename);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Read the contents of the file.  
    static string GetFileText(string name)  
    {  
        string fileContents = String.Empty;  
  
        // If the file has been deleted since we took
        // the snapshot, ignore it and return the empty string.  
        if (System.IO.File.Exists(name))  
        {  
            fileContents = System.IO.File.ReadAllText(name);  
        }  
        return fileContents;  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c96cc-110">编译代码</span><span class="sxs-lookup"><span data-stu-id="c96cc-110">Compiling the Code</span></span>  

<span data-ttu-id="c96cc-111">使用 System.Linq 和 System.IO 命名空间的 `using` 指令创建 C# 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="c96cc-111">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c96cc-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="c96cc-112">See also</span></span>

- [<span data-ttu-id="c96cc-113">LINQ 和文件目录 (C#)</span><span class="sxs-lookup"><span data-stu-id="c96cc-113">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
- [<span data-ttu-id="c96cc-114">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="c96cc-114">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
