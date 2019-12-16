---
title: "查询 XML 树 (C#)"
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
ms.assetid: 0913d81b-541a-4fd4-9cbf-7ec89fd817ea
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4bad11434ed2610492854d5ec4a7a84bceb189f3
ms.contentlocale: zh-cn
ms.lasthandoff: 07/28/2017

---
# <a name="querying-xml-trees-c"></a><span data-ttu-id="34f6a-102">查询 XML 树 (C#)</span><span class="sxs-lookup"><span data-stu-id="34f6a-102">Querying XML Trees (C#)</span></span>
<span data-ttu-id="34f6a-103">本节提供 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查询的示例。</span><span class="sxs-lookup"><span data-stu-id="34f6a-103">This section provides examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
 <span data-ttu-id="34f6a-104">有关编写 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查询的详细信息，请参阅 [C# 中的 LINQ 入门](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="34f6a-104">For more information about writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, see [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="34f6a-105">在实例化 XML 树之后，编写查询是从 XML 树中提取数据的最有效方法。</span><span class="sxs-lookup"><span data-stu-id="34f6a-105">After you have instantiated an XML tree, writing queries is the most effective way to extract data from the tree.</span></span> <span data-ttu-id="34f6a-106">另外，通过与函数构造相结合的查询，可以生成新的 XML 文档，该文档具有与原始文档不同的形状。</span><span class="sxs-lookup"><span data-stu-id="34f6a-106">Also, querying combined with functional construction enables you to generate a new XML document that has a different shape from the original document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="34f6a-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="34f6a-107">In This Section</span></span>  
  
|<span data-ttu-id="34f6a-108">主题</span><span class="sxs-lookup"><span data-stu-id="34f6a-108">Topic</span></span>|<span data-ttu-id="34f6a-109">描述</span><span class="sxs-lookup"><span data-stu-id="34f6a-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="34f6a-110">基本查询 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="34f6a-110">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)|<span data-ttu-id="34f6a-111">提供查询 XML 树的常见示例。</span><span class="sxs-lookup"><span data-stu-id="34f6a-111">Provides common examples of querying XML trees.</span></span>|  
|[<span data-ttu-id="34f6a-112">投影和转换 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="34f6a-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)|<span data-ttu-id="34f6a-113">提供从 XML 树进行投影以及转换 XML 树的常见示例。</span><span class="sxs-lookup"><span data-stu-id="34f6a-113">Provides common examples of projecting from and transforming XML trees.</span></span>|  
|[<span data-ttu-id="34f6a-114">高级查询技术 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="34f6a-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)|<span data-ttu-id="34f6a-115">提供可用于更高级方案的查询技术。</span><span class="sxs-lookup"><span data-stu-id="34f6a-115">Provides query techniques that are useful in more advanced scenarios.</span></span>|  
|[<span data-ttu-id="34f6a-116">针对 XPath 用户的 LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="34f6a-116">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)|<span data-ttu-id="34f6a-117">提供很多 XPath 表达式及其 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 等效表达式。</span><span class="sxs-lookup"><span data-stu-id="34f6a-117">Presents a number of XPath expressions and their [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] equivalents.</span></span>|  
|[<span data-ttu-id="34f6a-118">XML 的纯功能转换 (C#)</span><span class="sxs-lookup"><span data-stu-id="34f6a-118">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)|<span data-ttu-id="34f6a-119">提供以函数编程样式编写查询的小型教程。</span><span class="sxs-lookup"><span data-stu-id="34f6a-119">Presents a small tutorial on writing queries in the style of functional programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34f6a-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="34f6a-120">See Also</span></span>  
 <span data-ttu-id="34f6a-121">[编程指南 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="34f6a-121">[Programming Guide (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md) </span></span>  
 [<span data-ttu-id="34f6a-122">C# 中的 LINQ 入门</span><span class="sxs-lookup"><span data-stu-id="34f6a-122">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
