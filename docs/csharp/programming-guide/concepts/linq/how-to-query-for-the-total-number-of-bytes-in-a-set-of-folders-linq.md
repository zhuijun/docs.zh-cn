---
title: 如何查询一组文件夹中的总字节数 (LINQ) (C#)
description: 了解如何使用 C# 中的 LINQ 来查找由指定文件夹及其所有子文件夹中的所有文件使用的字节总数。
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: 562fd32ad9e9040a5898322d840718f25b56e2cd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159028"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a><span data-ttu-id="9b0ca-103">如何查询一组文件夹中的总字节数 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9b0ca-103">How to query for the total number of bytes in a set of folders (LINQ) (C#)</span></span>

<span data-ttu-id="9b0ca-104">此示例演示如何检索由指定文件夹及其所有子文件夹中的所有文件使用的字节总数。</span><span class="sxs-lookup"><span data-stu-id="9b0ca-104">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b0ca-105">示例</span><span class="sxs-lookup"><span data-stu-id="9b0ca-105">Example</span></span>  

 <span data-ttu-id="9b0ca-106"><xref:System.Linq.Enumerable.Sum%2A> 方法可将 `select` 子句中选择的所有项的值相加。</span><span class="sxs-lookup"><span data-stu-id="9b0ca-106">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="9b0ca-107">可轻松修改此查询以检索指定目录树中的最大或最小文件，方法是调用 <xref:System.Linq.Enumerable.Min%2A> 或 <xref:System.Linq.Enumerable.Max%2A> 方法，而不是 <xref:System.Linq.Enumerable.Sum%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9b0ca-107">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
```csharp  
class QuerySize  
{  
    public static void Main()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\VC#";  
  
        // Take a snapshot of the file system.  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<string> fileList = System.IO.Directory.GetFiles(startFolder, "*.*", System.IO.SearchOption.AllDirectories);  
  
        var fileQuery = from file in fileList  
                        select GetFileLength(file);  
  
        // Cache the results to avoid multiple trips to the file system.  
        long[] fileLengths = fileQuery.ToArray();  
  
        // Return the size of the largest file  
        long largestFile = fileLengths.Max();  
  
        // Return the total number of bytes in all the files under the specified folder.  
        long totalBytes = fileLengths.Sum();  
  
        Console.WriteLine("There are {0} bytes in {1} files under {2}",  
            totalBytes, fileList.Count(), startFolder);  
        Console.WriteLine("The largest files is {0} bytes.", largestFile);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.");  
        Console.ReadKey();  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the System.IO.FileInfo.Length property.  
    static long GetFileLength(string filename)  
    {  
        long retval;  
        try  
        {  
            System.IO.FileInfo fi = new System.IO.FileInfo(filename);  
            retval = fi.Length;  
        }  
        catch (System.IO.FileNotFoundException)  
        {  
            // If a file is no longer present,  
            // just add zero bytes to the total.  
            retval = 0;  
        }  
        return retval;  
    }  
}  
```  
  
 <span data-ttu-id="9b0ca-108">如果只需对指定目录树中的字节数进行计数，则可以更高效地执行此操作而无需创建 LINQ 查询（这会产生创建列表集合作为数据源的开销）。</span><span class="sxs-lookup"><span data-stu-id="9b0ca-108">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="9b0ca-109">随着查询变得更加复杂，或者在必须对相同数据源运行多个查询时，LINQ 方法会更加有用。</span><span class="sxs-lookup"><span data-stu-id="9b0ca-109">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="9b0ca-110">查询调用单独的方法来获取文件长度。</span><span class="sxs-lookup"><span data-stu-id="9b0ca-110">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="9b0ca-111">这是为了使用在以下情况下会引发的可能异常：在 `GetFiles` 调用中创建了 <xref:System.IO.FileInfo> 对象之后，在其他线程中删除了文件。</span><span class="sxs-lookup"><span data-stu-id="9b0ca-111">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="9b0ca-112">即使已创建 <xref:System.IO.FileInfo> 对象，该异常也可能出现，因为 <xref:System.IO.FileInfo> 对象会在首次访问其 <xref:System.IO.FileInfo.Length%2A> 属性时，尝试使用最近长度刷新该属性。</span><span class="sxs-lookup"><span data-stu-id="9b0ca-112">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="9b0ca-113">通过将此操作置于查询外部的 try-catch 块中，代码可遵循在查询中避免可能导致副作用的操作这一规则。</span><span class="sxs-lookup"><span data-stu-id="9b0ca-113">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="9b0ca-114">一般情况下，在使用异常时必须格外谨慎，以确保应用程序不会处于未知状态。</span><span class="sxs-lookup"><span data-stu-id="9b0ca-114">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9b0ca-115">编译代码</span><span class="sxs-lookup"><span data-stu-id="9b0ca-115">Compiling the Code</span></span>  

<span data-ttu-id="9b0ca-116">使用 System.Linq 和 System.IO 命名空间的 `using` 指令创建 C# 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="9b0ca-116">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9b0ca-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="9b0ca-117">See also</span></span>

- [<span data-ttu-id="9b0ca-118">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="9b0ca-118">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="9b0ca-119">LINQ 和文件目录 (C#)</span><span class="sxs-lookup"><span data-stu-id="9b0ca-119">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
