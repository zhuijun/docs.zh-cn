---
title: 如何：查询最大的文件或目录树中的文件 (LINQ)
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: 107f3457fe7361fab16c2c8ce837c90484fc7633
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397942"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="c0392-102">如何：查询目录树中的一个或多个最大的文件 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0392-102">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="c0392-103">此示例演示与文件大小（以字节为单位）相关的五个查询：</span><span class="sxs-lookup"><span data-stu-id="c0392-103">This example shows five queries related to file size in bytes:</span></span>  
  
- <span data-ttu-id="c0392-104">如何检索最大文件的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="c0392-104">How to retrieve the size in bytes of the largest file.</span></span>  
  
- <span data-ttu-id="c0392-105">如何检索最小文件的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="c0392-105">How to retrieve the size in bytes of the smallest file.</span></span>  
  
- <span data-ttu-id="c0392-106">如何从指定根文件夹下的一个或多个文件夹检索 <xref:System.IO.FileInfo> 对象最大或最小文件。</span><span class="sxs-lookup"><span data-stu-id="c0392-106">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
- <span data-ttu-id="c0392-107">如何检索序列（如 10 个最大文件）。</span><span class="sxs-lookup"><span data-stu-id="c0392-107">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
- <span data-ttu-id="c0392-108">如何基于文件大小（以字节为单位）按组对文件进行排序（忽略小于指定大小的文件）。</span><span class="sxs-lookup"><span data-stu-id="c0392-108">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0392-109">示例</span><span class="sxs-lookup"><span data-stu-id="c0392-109">Example</span></span>  
 <span data-ttu-id="c0392-110">下面的示例包含五个单独的查询，它们演示如何根据文件大小（以字节为单位）对文件进行查询和分组。</span><span class="sxs-lookup"><span data-stu-id="c0392-110">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="c0392-111">可以轻松地修改这些示例，以便使查询基于 <xref:System.IO.FileInfo> 对象的其他某个属性。</span><span class="sxs-lookup"><span data-stu-id="c0392-111">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
```vb  
Module QueryBySize  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Return the size of the largest file  
        Dim maxSize = Aggregate aFile In fileList Into Max(GetFileLength(aFile))  
  
        'Dim maxSize = fileLengths.Max  
        Console.WriteLine("The length of the largest file under {0} is {1}", _  
                          root, maxSize)  
  
        ' Return the FileInfo object of the largest file  
        ' by sorting and selecting from the beginning of the list  
        Dim filesByLengDesc = From file In fileList _  
                              Let filelength = GetFileLength(file) _  
                              Where filelength > 0 _  
                              Order By filelength Descending _  
                              Select file  
  
        Dim longestFile = filesByLengDesc.First  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes", _  
                          root, longestFile.FullName, longestFile.Length)  
  
        Dim smallestFile = filesByLengDesc.Last  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes", _  
                                root, smallestFile.FullName, smallestFile.Length)  
  
        ' Return the FileInfos for the 10 largest files  
        ' Based on a previous query, but nothing is executed  
        ' until the For Each statement below.  
        Dim tenLargest = From file In filesByLengDesc Take 10  
  
        Console.WriteLine("The 10 largest files under {0} are:", root)  
  
        For Each fi As System.IO.FileInfo In tenLargest  
            Console.WriteLine("{0}: {1} bytes", fi.FullName, fi.Length)  
        Next  
  
        ' Group files according to their size,  
        ' leaving out the ones under 200K  
        Dim sizeGroups = From file As System.IO.FileInfo In fileList _  
                         Where file.Length > 0 _  
                         Let groupLength = file.Length / 100000 _  
                         Group file By groupLength Into fileGroup = Group _  
                         Where groupLength >= 2 _  
                         Order By groupLength Descending  
  
        For Each group In sizeGroups  
            Console.WriteLine(group.groupLength + "00000")  
  
            For Each item As System.IO.FileInfo In group.fileGroup  
                Console.WriteLine("   {0}: {1}", item.Name, item.Length)  
            Next  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    ' In this particular case, it is safe to ignore the exception.  
    Function GetFileLength(ByVal fi As System.IO.FileInfo) As Long  
        Dim retval As Long  
        Try  
            retval = fi.Length  
        Catch ex As FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 <span data-ttu-id="c0392-112">若要返回一个或多个完整的 <xref:System.IO.FileInfo> 对象，查询必须首先检查数据中的每个对象，然后按其 Length 属性值对它们进行排序。</span><span class="sxs-lookup"><span data-stu-id="c0392-112">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="c0392-113">随后它便可以返回具有最大长度的单个对象或对象序列。</span><span class="sxs-lookup"><span data-stu-id="c0392-113">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="c0392-114">使用 <xref:System.Linq.Enumerable.First%2A> 返回列表中的第一个元素。</span><span class="sxs-lookup"><span data-stu-id="c0392-114">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="c0392-115">使用 <xref:System.Linq.Enumerable.Take%2A> 返回前 n 个元素。</span><span class="sxs-lookup"><span data-stu-id="c0392-115">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="c0392-116">指定降序排序顺序可将最小元素置于列表开头。</span><span class="sxs-lookup"><span data-stu-id="c0392-116">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="c0392-117">查询调用单独的方法来获取文件大小（以字节为单位），以便使用在以下情况下会引发的可能异常：自在 `GetFiles` 调用中创建了 <xref:System.IO.FileInfo> 对象以来的时间段内，在其他线程中删除了文件。</span><span class="sxs-lookup"><span data-stu-id="c0392-117">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="c0392-118">即使创建了 <xref:System.IO.FileInfo> 对象，该异常也可能出现，因为 <xref:System.IO.FileInfo> 对象会在首次访问其 <xref:System.IO.FileInfo.Length%2A> 属性时，尝试使用最新大小（以字节为单位）刷新该属性。</span><span class="sxs-lookup"><span data-stu-id="c0392-118">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="c0392-119">通过将此操作置于查询外部的 try-catch 块中，我们可遵循在查询中避免可能导致副作用的操作这一规则。</span><span class="sxs-lookup"><span data-stu-id="c0392-119">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="c0392-120">一般情况下，在使用异常时必须格外谨慎，以确保应用程序不会处于未知状态。</span><span class="sxs-lookup"><span data-stu-id="c0392-120">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="c0392-121">编译代码</span><span class="sxs-lookup"><span data-stu-id="c0392-121">Compile the code</span></span>  
<span data-ttu-id="c0392-122">使用 `Imports` System. Linq 命名空间的语句创建 Visual Basic 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="c0392-122">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c0392-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0392-123">See also</span></span>

- [<span data-ttu-id="c0392-124">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0392-124">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="c0392-125">LINQ 和文件目录 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0392-125">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
