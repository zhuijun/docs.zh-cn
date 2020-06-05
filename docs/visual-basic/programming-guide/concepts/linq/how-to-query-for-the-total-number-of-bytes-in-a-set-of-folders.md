---
title: 如何：查询一组文件夹中的总字节数 (LINQ)
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: c6490c8863b5762b0b487c6f3f3b2809e16d6519
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397929"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a><span data-ttu-id="02cb5-102">如何：查询一组文件夹中的总字节数（LINQ）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="02cb5-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="02cb5-103">此示例演示如何检索由指定文件夹及其所有子文件夹中的所有文件使用的字节总数。</span><span class="sxs-lookup"><span data-stu-id="02cb5-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02cb5-104">示例</span><span class="sxs-lookup"><span data-stu-id="02cb5-104">Example</span></span>  
 <span data-ttu-id="02cb5-105"><xref:System.Linq.Enumerable.Sum%2A> 方法可将 `select` 子句中选择的所有项的值相加。</span><span class="sxs-lookup"><span data-stu-id="02cb5-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="02cb5-106">可轻松修改此查询以检索指定目录树中的最大或最小文件，方法是调用 <xref:System.Linq.Enumerable.Min%2A> 或 <xref:System.Linq.Enumerable.Max%2A> 方法，而不是 <xref:System.Linq.Enumerable.Sum%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="02cb5-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
```vb  
Module QueryTotalBytes  
    Sub Main()  
  
        ' Change the drive\path if necessary.  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0\VB"  
  
        'Take a snapshot of the folder contents.  
        ' This method assumes that the application has discovery permissions  
        ' for all folders under the specified path.  
        Dim fileList = My.Computer.FileSystem.GetFiles _  
                  (root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")  
  
        Dim fileQuery = From file In fileList _  
                        Select GetFileLength(file)  
  
        ' Force execution and cache the results to avoid multiple trips to the file system.  
        Dim fileLengths = fileQuery.ToArray()  
  
        ' Find the largest file  
        Dim maxSize = Aggregate aFile In fileLengths Into Max()  
  
        ' Find the total number of bytes  
        Dim totalBytes = Aggregate aFile In fileLengths Into Sum()  
  
        Console.WriteLine("The largest file is " & maxSize & " bytes")  
        Console.WriteLine("There are " & totalBytes & " total bytes in " & _  
                          fileList.Count & " files under " & root)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    Function GetFileLength(ByVal filename As String) As Long  
        Dim retval As Long  
        Try  
            Dim fi As New System.IO.FileInfo(filename)  
            retval = fi.Length  
        Catch ex As System.IO.FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 <span data-ttu-id="02cb5-107">如果只需对指定目录树中的字节数进行计数，则可以更高效地执行此操作而无需创建 LINQ 查询（这会产生创建列表集合作为数据源的开销）。</span><span class="sxs-lookup"><span data-stu-id="02cb5-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="02cb5-108">随着查询变得更加复杂，或者在必须对相同数据源运行多个查询时，LINQ 方法会更加有用。</span><span class="sxs-lookup"><span data-stu-id="02cb5-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="02cb5-109">查询调用单独的方法来获取文件长度。</span><span class="sxs-lookup"><span data-stu-id="02cb5-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="02cb5-110">这是为了使用在以下情况下会引发的可能异常：在 `GetFiles` 调用中创建了 <xref:System.IO.FileInfo> 对象之后，在其他线程中删除了文件。</span><span class="sxs-lookup"><span data-stu-id="02cb5-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="02cb5-111">即使已创建 <xref:System.IO.FileInfo> 对象，该异常也可能出现，因为 <xref:System.IO.FileInfo> 对象会在首次访问其 <xref:System.IO.FileInfo.Length%2A> 属性时，尝试使用最近长度刷新该属性。</span><span class="sxs-lookup"><span data-stu-id="02cb5-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="02cb5-112">通过将此操作置于查询外部的 try-catch 块中，代码可遵循在查询中避免可能导致副作用的操作这一规则。</span><span class="sxs-lookup"><span data-stu-id="02cb5-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="02cb5-113">一般情况下，在使用异常时必须格外谨慎，以确保应用程序不会处于未知状态。</span><span class="sxs-lookup"><span data-stu-id="02cb5-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="02cb5-114">编译代码</span><span class="sxs-lookup"><span data-stu-id="02cb5-114">Compile the code</span></span>  
<span data-ttu-id="02cb5-115">使用 `Imports` System. Linq 命名空间的语句创建 Visual Basic 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="02cb5-115">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="02cb5-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="02cb5-116">See also</span></span>

- [<span data-ttu-id="02cb5-117">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02cb5-117">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="02cb5-118">LINQ 和文件目录 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02cb5-118">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
