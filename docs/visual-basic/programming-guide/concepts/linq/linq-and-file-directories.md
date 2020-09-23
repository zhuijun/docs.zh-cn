---
title: LINQ 和文件目录
ms.date: 07/20/2015
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
ms.openlocfilehash: 670611cd285a1b1f2602e2c700c2bdeb56db943f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100160"
---
# <a name="linq-and-file-directories-visual-basic"></a><span data-ttu-id="75095-102">LINQ 和文件目录 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75095-102">LINQ and File Directories (Visual Basic)</span></span>

<span data-ttu-id="75095-103">许多文件系统操作实质上是查询，因此非常适合使用 LINQ 方法。</span><span class="sxs-lookup"><span data-stu-id="75095-103">Many file system operations are essentially queries and are therefore well-suited to the LINQ approach.</span></span>  
  
 <span data-ttu-id="75095-104">请注意，本部分中的查询是非破坏性查询。</span><span class="sxs-lookup"><span data-stu-id="75095-104">Note that the queries in this section are non-destructive.</span></span> <span data-ttu-id="75095-105">它们不用于更改原始文件或文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="75095-105">They are not used to change the contents of the original files or folders.</span></span> <span data-ttu-id="75095-106">这遵循了查询不应引起任何副作用这条规则。</span><span class="sxs-lookup"><span data-stu-id="75095-106">This follows the rule that queries should not cause any side-effects.</span></span> <span data-ttu-id="75095-107">通常，修改源数据的任何代码（包括执行创建/更新/删除运算符的查询）应与只查询数据的代码分开。</span><span class="sxs-lookup"><span data-stu-id="75095-107">In general, any code (including queries that perform create / update / delete operators) that modifies source data should be kept separate from the code that just queries the data.</span></span>  
  
 <span data-ttu-id="75095-108">本节包含下列主题：</span><span class="sxs-lookup"><span data-stu-id="75095-108">This section contains the following topics:</span></span>  
  
 [<span data-ttu-id="75095-109">如何：查询具有指定特性或名称的文件 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="75095-109">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 <span data-ttu-id="75095-110">演示如何通过检查文件的 <xref:System.IO.FileInfo> 对象的一个或多个属性来搜索文件。</span><span class="sxs-lookup"><span data-stu-id="75095-110">Shows how to search for files by examining one or more properties of its <xref:System.IO.FileInfo> object.</span></span>  
  
 [<span data-ttu-id="75095-111">如何：按扩展名对文件进行分组 (LINQ)  (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="75095-111">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](how-to-group-files-by-extension-linq.md)  
 <span data-ttu-id="75095-112">演示如何根据文件扩展名返回 <xref:System.IO.FileInfo> 对象组。</span><span class="sxs-lookup"><span data-stu-id="75095-112">Shows how to return groups of <xref:System.IO.FileInfo> object based on their file name extension.</span></span>  
  
 [<span data-ttu-id="75095-113">如何：查询一组文件夹中的总字节数 (LINQ)  (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="75095-113">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 <span data-ttu-id="75095-114">演示如何返回指定目录树中所有文件的总字节数。</span><span class="sxs-lookup"><span data-stu-id="75095-114">Shows how to return the total number of bytes in all the files in a specified directory tree.</span></span>  
  
 <span data-ttu-id="75095-115">[如何：比较两个文件夹 (LINQ)  (Visual Basic) ](how-to-compare-the-contents-of-two-folders-linq.md)s 的内容</span><span class="sxs-lookup"><span data-stu-id="75095-115">[How to: Compare the Contents of Two Folders (LINQ) (Visual Basic)](how-to-compare-the-contents-of-two-folders-linq.md)s</span></span>  
 <span data-ttu-id="75095-116">演示如何返回位于两个指定文件夹中的所有文件，以及仅位于其中一个文件夹中的所有文件。</span><span class="sxs-lookup"><span data-stu-id="75095-116">Shows how to return all the files that are present in two specified folders, and also all the files that are present in one folder but not the other.</span></span>  
  
 [<span data-ttu-id="75095-117">如何：查询目录树中的一个或多个最大的文件 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75095-117">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 <span data-ttu-id="75095-118">演示如何返回目录树中的最大文件、最小文件或指定数量的文件。</span><span class="sxs-lookup"><span data-stu-id="75095-118">Shows how to return the largest or smallest file, or a specified number of files, in a directory tree.</span></span>  
  
 [<span data-ttu-id="75095-119">如何：在目录树中查询重复文件 (LINQ)  (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="75095-119">How to: Query for Duplicate Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 <span data-ttu-id="75095-120">演示如何对出现在指定目录树中多个位置的所有文件名进行分组。</span><span class="sxs-lookup"><span data-stu-id="75095-120">Shows how to group for all file names that occur in more than one location in a specified directory tree.</span></span> <span data-ttu-id="75095-121">此外，还演示如何根据自定义比较器执行更复杂的比较。</span><span class="sxs-lookup"><span data-stu-id="75095-121">Also shows how to perform more complex comparisons based on a custom comparer.</span></span>  
  
 [<span data-ttu-id="75095-122">如何查询文件夹中文件的内容 (LINQ)  (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="75095-122">How to query the contents of files in a folder (LINQ) (Visual Basic)</span></span>](how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 <span data-ttu-id="75095-123">演示如何循环访问树中的文件夹，打开每个文件以及查询文件的内容。</span><span class="sxs-lookup"><span data-stu-id="75095-123">Shows how to iterate through folders in a tree, open each file, and query the file's contents.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="75095-124">注释</span><span class="sxs-lookup"><span data-stu-id="75095-124">Comments</span></span>  

 <span data-ttu-id="75095-125">创建准确表示文件系统的内容并适当处理异常的数据源，存在一定难度。</span><span class="sxs-lookup"><span data-stu-id="75095-125">There is some complexity involved in creating a data source that accurately represents the contents of the file system and handles exceptions gracefully.</span></span> <span data-ttu-id="75095-126">本部分中的示例创建 <xref:System.IO.FileInfo> 对象的快照集合，该集合表示指定的根文件夹及其所有子文件夹下的所有文件。</span><span class="sxs-lookup"><span data-stu-id="75095-126">The examples in this section create a snapshot collection of <xref:System.IO.FileInfo> objects that represents all the files under a specified root folder and all its subfolders.</span></span> <span data-ttu-id="75095-127">每个 <xref:System.IO.FileInfo> 的实际状态可能会在开始和结束执行查询期间发生更改。</span><span class="sxs-lookup"><span data-stu-id="75095-127">The actual state of each <xref:System.IO.FileInfo> may change in the time between when you begin and end executing a query.</span></span> <span data-ttu-id="75095-128">例如，可以创建 <xref:System.IO.FileInfo> 对象的列表来用作数据源。</span><span class="sxs-lookup"><span data-stu-id="75095-128">For example, you can create a list of <xref:System.IO.FileInfo> objects to use as a data source.</span></span> <span data-ttu-id="75095-129">如果尝试通过查询访问 `Length` 属性，则 <xref:System.IO.FileInfo> 对象会尝试访问文件系统来更新 `Length` 的值。</span><span class="sxs-lookup"><span data-stu-id="75095-129">If you try to access the `Length` property in a query, the <xref:System.IO.FileInfo> object will try to access the file system to update the value of `Length`.</span></span> <span data-ttu-id="75095-130">如果该文件不再存在，则你会在查询中获得 <xref:System.IO.FileNotFoundException>，即使未直接查询文件系统也是如此。</span><span class="sxs-lookup"><span data-stu-id="75095-130">If the file no longer exists, you will get a <xref:System.IO.FileNotFoundException> in your query, even though you are not querying the file system directly.</span></span> <span data-ttu-id="75095-131">本部分中的一些查询使用不同的方法，在某些情况下使用该方法不会出现这些特定异常。</span><span class="sxs-lookup"><span data-stu-id="75095-131">Some queries in this section use a separate method that consumes these particular exceptions in certain cases.</span></span> <span data-ttu-id="75095-132">另一种方法是使用 <xref:System.IO.FileSystemWatcher> 保持数据源动态更新。</span><span class="sxs-lookup"><span data-stu-id="75095-132">Another option is to keep your data source updated dynamically by using the <xref:System.IO.FileSystemWatcher>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75095-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="75095-133">See also</span></span>

- [<span data-ttu-id="75095-134">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75095-134">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
