---
title: 函数编程与过程编程 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
ms.openlocfilehash: 0b525f13298e7402369b890516434cec47e01542
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398430"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a><span data-ttu-id="535d1-102">功能与过程编程（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="535d1-102">Functional vs. Procedural Programming (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="535d1-103">XML 应用程序有多种类型：</span><span class="sxs-lookup"><span data-stu-id="535d1-103">There are various types of XML applications:</span></span>  
  
- <span data-ttu-id="535d1-104">有些应用程序采用源 XML 文档并生成与源文档形状不同的新 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="535d1-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
- <span data-ttu-id="535d1-105">有些应用程序采用源 XML 文档并生成格式完全不同的结果文档，如 HTML 或 CSV 文本文件。</span><span class="sxs-lookup"><span data-stu-id="535d1-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
- <span data-ttu-id="535d1-106">有些应用程序采用源 XML 文档并将记录插入数据库。</span><span class="sxs-lookup"><span data-stu-id="535d1-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
- <span data-ttu-id="535d1-107">有些应用程序采用另一个源（如数据库）中的数据并从该数据创建 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="535d1-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="535d1-108">这些并不是所有的 XML 应用程序类型，但它们是 XML 程序员必须实现的一组有代表性的功能类型。</span><span class="sxs-lookup"><span data-stu-id="535d1-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="535d1-109">对于所有这些类型应用程序，开发人员可以采用两种对比方法：</span><span class="sxs-lookup"><span data-stu-id="535d1-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
- <span data-ttu-id="535d1-110">使用声明性方法的函数构造。</span><span class="sxs-lookup"><span data-stu-id="535d1-110">Functional construction using a declarative approach.</span></span>  
  
- <span data-ttu-id="535d1-111">使用过程代码的内存中 XML 树修改法。</span><span class="sxs-lookup"><span data-stu-id="535d1-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="535d1-112">LINQ to XML 同时支持这两种方法。</span><span class="sxs-lookup"><span data-stu-id="535d1-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="535d1-113">使用函数方法时，编写可采用源文档并生成具有所需形状的全新结果文档的转换。</span><span class="sxs-lookup"><span data-stu-id="535d1-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="535d1-114">就地修改 XML 树时，编写可遍历内存中 XML 树节点并在其中导航以便根据需要插入、删除和修改节点的代码。</span><span class="sxs-lookup"><span data-stu-id="535d1-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="535d1-115">可以对任一方法使用 LINQ to XML。</span><span class="sxs-lookup"><span data-stu-id="535d1-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="535d1-116">使用的类相同，在某些情况下使用的方法也相同。</span><span class="sxs-lookup"><span data-stu-id="535d1-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="535d1-117">但这两种方法的结构和目标却大相径庭。</span><span class="sxs-lookup"><span data-stu-id="535d1-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="535d1-118">例如，在不同情况下，其中一种方法通常具有更好的性能，使用更多或更少的内存。</span><span class="sxs-lookup"><span data-stu-id="535d1-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="535d1-119">另外，其中一种方法会更容易编写并生成更容易维护的代码。</span><span class="sxs-lookup"><span data-stu-id="535d1-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="535d1-120">若要查看这两种方法之间的对比，请参阅[内存中 XML 树修改与功能构造（LINQ to XML）（Visual Basic）](in-memory-xml-tree-modification-vs-functional-construction.md)。</span><span class="sxs-lookup"><span data-stu-id="535d1-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>  
  
 <span data-ttu-id="535d1-121">有关编写函数转换的教程，请参阅[XML 的纯功能转换（Visual Basic）](pure-functional-transformations-of-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="535d1-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (Visual Basic)](pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="535d1-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="535d1-122">See also</span></span>

- [<span data-ttu-id="535d1-123">LINQ to XML 编程概述（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="535d1-123">LINQ to XML Programming Overview (Visual Basic)</span></span>](linq-to-xml-programming-overview.md)
