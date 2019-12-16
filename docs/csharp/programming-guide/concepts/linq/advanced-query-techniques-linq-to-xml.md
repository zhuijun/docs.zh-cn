---
title: "高级查询技术 (LINQ to XML) (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 028d978e-215b-4d50-ba70-adce0659386d
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 91460ed99854edda829503d451728c4274d7ba2b
ms.contentlocale: zh-cn
ms.lasthandoff: 07/28/2017

---
# <a name="advanced-query-techniques-linq-to-xml-c"></a><span data-ttu-id="09fd1-102">高级查询技术 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="09fd1-102">Advanced Query Techniques (LINQ to XML) (C#)</span></span>
<span data-ttu-id="09fd1-103">本节提供更多高级 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查询技术的示例。</span><span class="sxs-lookup"><span data-stu-id="09fd1-103">This section provides examples of more advanced [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query techniques.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="09fd1-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="09fd1-104">In This Section</span></span>  
  
|<span data-ttu-id="09fd1-105">主题</span><span class="sxs-lookup"><span data-stu-id="09fd1-105">Topic</span></span>|<span data-ttu-id="09fd1-106">描述</span><span class="sxs-lookup"><span data-stu-id="09fd1-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="09fd1-107">如何：联接两个集合 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="09fd1-107">How to: Join Two Collections (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-join-two-collections-linq-to-xml.md)|<span data-ttu-id="09fd1-108">演示如何使用 `Join` 子句来利用 XML 数据中的关系。</span><span class="sxs-lookup"><span data-stu-id="09fd1-108">Shows how to use the `Join` clause to take advantage of relationships in XML data.</span></span>|  
|[<span data-ttu-id="09fd1-109">如何：使用分组创建层次结构 (C#)</span><span class="sxs-lookup"><span data-stu-id="09fd1-109">How to: Create Hierarchy Using Grouping (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-create-hierarchy-using-grouping.md)|<span data-ttu-id="09fd1-110">演示如何将数据分组，再基于分组生成 XML。</span><span class="sxs-lookup"><span data-stu-id="09fd1-110">Shows how to group data, and then generate XML based on the grouping.</span></span>|  
|[<span data-ttu-id="09fd1-111">如何：使用 XPath 查询 LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="09fd1-111">How to: Query LINQ to XML Using XPath (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-linq-to-xml-using-xpath.md)|<span data-ttu-id="09fd1-112">演示如何基于 XPath 查询来检索集合。</span><span class="sxs-lookup"><span data-stu-id="09fd1-112">Shows how to retrieve collections based on XPath queries.</span></span>|  
|[<span data-ttu-id="09fd1-113">如何：编写 LINQ to XML 轴方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="09fd1-113">How to: Write a LINQ to XML Axis Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md)|<span data-ttu-id="09fd1-114">演示如何编写 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 轴方法。</span><span class="sxs-lookup"><span data-stu-id="09fd1-114">Shows how to write a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axis method.</span></span>|  
|[<span data-ttu-id="09fd1-115">如何：执行文本到 XML 的流式转换 (C#)</span><span class="sxs-lookup"><span data-stu-id="09fd1-115">How to: Perform Streaming Transformations of Text to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transformations-of-text-to-xml.md)|<span data-ttu-id="09fd1-116">演示如何在保持很小的内存需求量的同时将非常大的文本文件转换为 XML。</span><span class="sxs-lookup"><span data-stu-id="09fd1-116">Shows how to transform very large text files into XML while maintaining a small memory footprint.</span></span>|  
|[<span data-ttu-id="09fd1-117">如何：列出树中的所有节点 (C#)</span><span class="sxs-lookup"><span data-stu-id="09fd1-117">How to: List All Nodes in a Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-list-all-nodes-in-a-tree.md)|<span data-ttu-id="09fd1-118">演示一种用于列出 XML 树中所有节点的实用工具方法。</span><span class="sxs-lookup"><span data-stu-id="09fd1-118">Presents a utility method that lists all nodes in an XML tree.</span></span> <span data-ttu-id="09fd1-119">此方法可用于调试修改 XML 树的代码。</span><span class="sxs-lookup"><span data-stu-id="09fd1-119">This is useful for debugging code that modifies an XML tree.</span></span>|  
|[<span data-ttu-id="09fd1-120">如何：从 Office Open XML 文档中检索段落 (C#)</span><span class="sxs-lookup"><span data-stu-id="09fd1-120">How to: Retrieve Paragraphs from an Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-paragraphs-from-an-office-open-xml-document.md)|<span data-ttu-id="09fd1-121">演示打开 Office Open XML 文档；检索 XElement 对象集合中的段落、段落文本和段落样式的代码。</span><span class="sxs-lookup"><span data-stu-id="09fd1-121">Presents code that opens an Office Open XML Document, retrieves the paragraphs in a collection of XElement objects, the text of the paragraphs, and the style of the paragraphs.</span></span>|  
|[<span data-ttu-id="09fd1-122">如何：修改 Office Open XML 文档 (C#)</span><span class="sxs-lookup"><span data-stu-id="09fd1-122">How to: Modify an Office Open XML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-modify-an-office-open-xml-document.md)|<span data-ttu-id="09fd1-123">演示打开、修改和保存 Office Open XML 文档的代码。</span><span class="sxs-lookup"><span data-stu-id="09fd1-123">Presents code that opens, modifies, and saves an Office Open XML Document.</span></span>|  
|[<span data-ttu-id="09fd1-124">如何：从文件系统填充 XML 树 (C#)</span><span class="sxs-lookup"><span data-stu-id="09fd1-124">How to: Populate an XML Tree from the File System (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-an-xml-tree-from-the-file-system.md)|<span data-ttu-id="09fd1-125">演示从文件系统创建 XML 树的代码。</span><span class="sxs-lookup"><span data-stu-id="09fd1-125">Presents code that creates an XML tree from the file system.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09fd1-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="09fd1-126">See Also</span></span>  
 [<span data-ttu-id="09fd1-127">查询 XML 树 (C#)</span><span class="sxs-lookup"><span data-stu-id="09fd1-127">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
