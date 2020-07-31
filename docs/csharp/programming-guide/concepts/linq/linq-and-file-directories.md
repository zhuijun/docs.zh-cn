---
title: LINQ 和文件目录 (C#)
description: 这些用于文件系统操作的 C# LINQ 资源不可用于更改文件或文件夹的内容。
ms.date: 07/20/2015
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
ms.openlocfilehash: ac00e29f90ee1c04ab9978b6ada3ae5f28991a1c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165665"
---
# <a name="linq-and-file-directories-c"></a><span data-ttu-id="b9fa4-103">LINQ 和文件目录 (C#)</span><span class="sxs-lookup"><span data-stu-id="b9fa4-103">LINQ and file directories (C#)</span></span>

<span data-ttu-id="b9fa4-104">许多文件系统操作实质上是查询，因此非常适合使用 LINQ 方法。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-104">Many file system operations are essentially queries and are therefore well suited to the LINQ approach.</span></span>  
  
 <span data-ttu-id="b9fa4-105">本部分中的查询是非破坏性查询。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-105">The queries in this section are non-destructive.</span></span> <span data-ttu-id="b9fa4-106">它们不用于更改原始文件或文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-106">They are not used to change the contents of the original files or folders.</span></span> <span data-ttu-id="b9fa4-107">这遵循了查询不应引起任何副作用这条规则。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-107">This follows the rule that queries should not cause any side-effects.</span></span> <span data-ttu-id="b9fa4-108">通常，修改源数据的任何代码（包括执行创建/更新/删除运算符的查询）应与只查询数据的代码分开。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-108">In general, any code (including queries that perform create / update / delete operators) that modifies source data should be kept separate from the code that just queries the data.</span></span>  
  
 <span data-ttu-id="b9fa4-109">本节包含下列主题：</span><span class="sxs-lookup"><span data-stu-id="b9fa4-109">This section contains the following topics:</span></span>  
  
 <span data-ttu-id="b9fa4-110">[如何查询具有指定特性或名称的文件 (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)</span><span class="sxs-lookup"><span data-stu-id="b9fa4-110">[How to query for files with a specified attribute or name (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)</span></span>\
 <span data-ttu-id="b9fa4-111">演示如何通过检查文件的 <xref:System.IO.FileInfo> 对象的一个或多个属性来搜索文件。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-111">Shows how to search for files by examining one or more properties of its <xref:System.IO.FileInfo> object.</span></span>  
  
 <span data-ttu-id="b9fa4-112">[如何按扩展名对文件进行分组 (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)</span><span class="sxs-lookup"><span data-stu-id="b9fa4-112">[How to group files by extension (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)</span></span>\
 <span data-ttu-id="b9fa4-113">演示如何根据文件扩展名返回 <xref:System.IO.FileInfo> 对象组。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-113">Shows how to return groups of <xref:System.IO.FileInfo> object based on their file name extension.</span></span>  
  
 <span data-ttu-id="b9fa4-114">[如何查询一组文件夹中的总字节数 (LINQ) (C#)](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)</span><span class="sxs-lookup"><span data-stu-id="b9fa4-114">[How to query for the total number of bytes in a set of folders (LINQ) (C#)](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)</span></span>\
 <span data-ttu-id="b9fa4-115">演示如何返回指定目录树中所有文件的总字节数。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-115">Shows how to return the total number of bytes in all the files in a specified directory tree.</span></span>  
  
 <span data-ttu-id="b9fa4-116">[如何比较两个文件夹的内容 (LINQ) (C#)](./how-to-compare-the-contents-of-two-folders-linq.md)</span><span class="sxs-lookup"><span data-stu-id="b9fa4-116">[How to compare the contents of two folders (LINQ) (C#)](./how-to-compare-the-contents-of-two-folders-linq.md)s</span></span>  
 <span data-ttu-id="b9fa4-117">演示如何返回位于两个指定文件夹中的所有文件，以及仅位于其中一个文件夹中的所有文件。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-117">Shows how to return all the files that are present in two specified folders, and also all the files that are present in one folder but not the other.</span></span>  
  
 <span data-ttu-id="b9fa4-118">[如何查询目录树中的一个或多个最大的文件 (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)</span><span class="sxs-lookup"><span data-stu-id="b9fa4-118">[How to query for the largest file or files in a directory tree (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)</span></span>\
 <span data-ttu-id="b9fa4-119">演示如何返回目录树中的最大文件、最小文件或指定数量的文件。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-119">Shows how to return the largest or smallest file, or a specified number of files, in a directory tree.</span></span>  
  
 <span data-ttu-id="b9fa4-120">[如何在目录树中查询重复文件 (LINQ) (C#)](./how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)</span><span class="sxs-lookup"><span data-stu-id="b9fa4-120">[How to query for duplicate files in a directory tree (LINQ) (C#)](./how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)</span></span>\
 <span data-ttu-id="b9fa4-121">演示如何对出现在指定目录树中多个位置的所有文件名进行分组。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-121">Shows how to group for all file names that occur in more than one location in a specified directory tree.</span></span> <span data-ttu-id="b9fa4-122">此外，还演示如何根据自定义比较器执行更复杂的比较。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-122">Also shows how to perform more complex comparisons based on a custom comparer.</span></span>  
  
 <span data-ttu-id="b9fa4-123">[如何查询文件夹中文件的内容 (LINQ) (C#)](./how-to-query-the-contents-of-files-in-a-folder-lin.md)</span><span class="sxs-lookup"><span data-stu-id="b9fa4-123">[How to query the contents of files in a folder (LINQ) (C#)](./how-to-query-the-contents-of-files-in-a-folder-lin.md)</span></span>\
 <span data-ttu-id="b9fa4-124">演示如何循环访问树中的文件夹，打开每个文件以及查询文件的内容。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-124">Shows how to iterate through folders in a tree, open each file, and query the file's contents.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="b9fa4-125">注释</span><span class="sxs-lookup"><span data-stu-id="b9fa4-125">Comments</span></span>  
 <span data-ttu-id="b9fa4-126">创建准确表示文件系统的内容并适当处理异常的数据源，存在一定难度。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-126">There is some complexity involved in creating a data source that accurately represents the contents of the file system and handles exceptions gracefully.</span></span> <span data-ttu-id="b9fa4-127">本部分中的示例创建 <xref:System.IO.FileInfo> 对象的快照集合，该集合表示指定的根文件夹及其所有子文件夹下的所有文件。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-127">The examples in this section create a snapshot collection of <xref:System.IO.FileInfo> objects that represents all the files under a specified root folder and all its subfolders.</span></span> <span data-ttu-id="b9fa4-128">每个 <xref:System.IO.FileInfo> 的实际状态可能会在开始和结束执行查询期间发生更改。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-128">The actual state of each <xref:System.IO.FileInfo> may change in the time between when you begin and end executing a query.</span></span> <span data-ttu-id="b9fa4-129">例如，可以创建 <xref:System.IO.FileInfo> 对象的列表来用作数据源。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-129">For example, you can create a list of <xref:System.IO.FileInfo> objects to use as a data source.</span></span> <span data-ttu-id="b9fa4-130">如果尝试通过查询访问 `Length` 属性，则 <xref:System.IO.FileInfo> 对象会尝试访问文件系统来更新 `Length` 的值。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-130">If you try to access the `Length` property in a query, the <xref:System.IO.FileInfo> object will try to access the file system to update the value of `Length`.</span></span> <span data-ttu-id="b9fa4-131">如果该文件不再存在，则你会在查询中获得 <xref:System.IO.FileNotFoundException>，即使未直接查询文件系统也是如此。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-131">If the file no longer exists, you will get a <xref:System.IO.FileNotFoundException> in your query, even though you are not querying the file system directly.</span></span> <span data-ttu-id="b9fa4-132">本部分中的一些查询使用不同的方法，在某些情况下使用该方法不会出现这些特定异常。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-132">Some queries in this section use a separate method that consumes these particular exceptions in certain cases.</span></span> <span data-ttu-id="b9fa4-133">另一种方法是使用 <xref:System.IO.FileSystemWatcher> 保持数据源动态更新。</span><span class="sxs-lookup"><span data-stu-id="b9fa4-133">Another option is to keep your data source updated dynamically by using the <xref:System.IO.FileSystemWatcher>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9fa4-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="b9fa4-134">See also</span></span>

- [<span data-ttu-id="b9fa4-135">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="b9fa4-135">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
