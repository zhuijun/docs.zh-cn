---
title: 高级查询技术 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 79be877c-fadc-4dfb-9f03-426082b13656
ms.openlocfilehash: ca4460ec4d35b1bccf1b0a48dd806cf07e79c572
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383801"
---
# <a name="advanced-query-techniques-linq-to-xml-visual-basic"></a><span data-ttu-id="53b15-102">高级查询技术（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="53b15-102">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="53b15-103">本节提供更多高级 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查询技术的示例。</span><span class="sxs-lookup"><span data-stu-id="53b15-103">This section provides examples of more advanced [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query techniques.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="53b15-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="53b15-104">In This Section</span></span>  
  
|<span data-ttu-id="53b15-105">主题</span><span class="sxs-lookup"><span data-stu-id="53b15-105">Topic</span></span>|<span data-ttu-id="53b15-106">说明</span><span class="sxs-lookup"><span data-stu-id="53b15-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="53b15-107">如何：联接两个集合（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="53b15-107">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>](how-to-join-two-collections-linq-to-xml.md)|<span data-ttu-id="53b15-108">演示如何使用 `Join` 子句来利用 XML 数据中的关系。</span><span class="sxs-lookup"><span data-stu-id="53b15-108">Shows how to use the `Join` clause to take advantage of relationships in XML data.</span></span>|  
|[<span data-ttu-id="53b15-109">如何：使用分组创建层次结构（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="53b15-109">How to: Create Hierarchy Using Grouping (Visual Basic)</span></span>](how-to-create-hierarchy-using-grouping.md)|<span data-ttu-id="53b15-110">演示如何将数据分组，再基于分组生成 XML。</span><span class="sxs-lookup"><span data-stu-id="53b15-110">Shows how to group data, and then generate XML based on the grouping.</span></span>|  
|[<span data-ttu-id="53b15-111">如何：使用 XPath 查询 LINQ to XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="53b15-111">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>](how-to-query-linq-to-xml-using-xpath.md)|<span data-ttu-id="53b15-112">演示如何基于 XPath 查询来检索集合。</span><span class="sxs-lookup"><span data-stu-id="53b15-112">Shows how to retrieve collections based on XPath queries.</span></span>|  
|[<span data-ttu-id="53b15-113">如何：编写 LINQ to XML Axis 方法（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="53b15-113">How to: Write a LINQ to XML Axis Method (Visual Basic)</span></span>](how-to-write-a-linq-to-xml-axis-method.md)|<span data-ttu-id="53b15-114">演示如何编写 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 轴方法。</span><span class="sxs-lookup"><span data-stu-id="53b15-114">Shows how to write a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axis method.</span></span>|  
|[<span data-ttu-id="53b15-115">如何：列出树中的所有节点（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="53b15-115">How to: List All Nodes in a Tree (Visual Basic)</span></span>](how-to-list-all-nodes-in-a-tree.md)|<span data-ttu-id="53b15-116">演示一种用于列出 XML 树中所有节点的实用工具方法。</span><span class="sxs-lookup"><span data-stu-id="53b15-116">Presents a utility method that lists all nodes in an XML tree.</span></span> <span data-ttu-id="53b15-117">此方法可用于调试修改 XML 树的代码。</span><span class="sxs-lookup"><span data-stu-id="53b15-117">This is useful for debugging code that modifies an XML tree.</span></span>|  
|[<span data-ttu-id="53b15-118">如何：从 Office Open XML 文档中检索段落（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="53b15-118">How to: Retrieve Paragraphs from an Office Open XML Document (Visual Basic)</span></span>](how-to-retrieve-paragraphs-from-an-office-open-xml-document.md)|<span data-ttu-id="53b15-119">演示打开 Office Open XML 文档；检索 XElement 对象集合中的段落、段落文本和段落样式的代码。</span><span class="sxs-lookup"><span data-stu-id="53b15-119">Presents code that opens an Office Open XML Document, retrieves the paragraphs in a collection of XElement objects, the text of the paragraphs, and the style of the paragraphs.</span></span>|  
|[<span data-ttu-id="53b15-120">如何：修改 Office Open XML 文档（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="53b15-120">How to: Modify an Office Open XML Document (Visual Basic)</span></span>](how-to-modify-an-office-open-xml-document.md)|<span data-ttu-id="53b15-121">演示打开、修改和保存 Office Open XML 文档的代码。</span><span class="sxs-lookup"><span data-stu-id="53b15-121">Presents code that opens, modifies, and saves an Office Open XML Document.</span></span>|  
|[<span data-ttu-id="53b15-122">如何：从文件系统填充 XML 树（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="53b15-122">How to: Populate an XML Tree from the File System (Visual Basic)</span></span>](how-to-populate-an-xml-tree-from-the-file-system.md)|<span data-ttu-id="53b15-123">演示从文件系统创建 XML 树的代码。</span><span class="sxs-lookup"><span data-stu-id="53b15-123">Presents code that creates an XML tree from the file system.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53b15-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="53b15-124">See also</span></span>

- [<span data-ttu-id="53b15-125">查询 XML 树 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53b15-125">Querying XML Trees (Visual Basic)</span></span>](querying-xml-trees.md)
