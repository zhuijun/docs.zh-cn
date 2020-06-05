---
title: LINQ 介绍
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: b0fa27fd81b85eb89712f9e81f42e06505878f86
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397553"
---
# <a name="introduction-to-linq-visual-basic"></a><span data-ttu-id="a7cc5-102">LINQ 简介 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7cc5-102">Introduction to LINQ (Visual Basic)</span></span>
<span data-ttu-id="a7cc5-103">语言集成查询 (LINQ) 是 .NET Framework 3.5 版中引入的一项创新功能，它在对象领域和数据领域之间架起了一座桥梁。</span><span class="sxs-lookup"><span data-stu-id="a7cc5-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="a7cc5-104">数据查询历来都表示为简单的字符串，没有编译时类型检查或 IntelliSense 支持。</span><span class="sxs-lookup"><span data-stu-id="a7cc5-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="a7cc5-105">此外，需要针对每种类型的数据源了解不同的查询语言：SQL 数据库、XML 文档、各种 Web 服务等。</span><span class="sxs-lookup"><span data-stu-id="a7cc5-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="a7cc5-106">LINQ 使*查询*成为 Visual Basic 中的第一类语言构造。</span><span class="sxs-lookup"><span data-stu-id="a7cc5-106">LINQ makes a *query* a first-class language construct in Visual Basic.</span></span> <span data-ttu-id="a7cc5-107">可以使用语言关键字和熟悉的运算符针对强类型化对象集合编写查询。</span><span class="sxs-lookup"><span data-stu-id="a7cc5-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="a7cc5-108">可以在 Visual Basic 中为 SQL Server 数据库、XML 文档、ADO.NET 数据集以及支持或泛型接口的任何对象集合编写 LINQ 查询 <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> 。</span><span class="sxs-lookup"><span data-stu-id="a7cc5-108">You can write LINQ queries in Visual Basic for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="a7cc5-109">此外，第三方也为许多 Web 服务和其他数据库实现提供了 LINQ 支持。</span><span class="sxs-lookup"><span data-stu-id="a7cc5-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="a7cc5-110">LINQ 查询既可在新项目中使用，也可在现有项目中与非 LINQ 查询一起使用。</span><span class="sxs-lookup"><span data-stu-id="a7cc5-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="a7cc5-111">唯一的要求是项目应面向 .NET Framework 3.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="a7cc5-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="a7cc5-112">下图为 Visual Studio 中的图例，显示了使用 C# 和 Visual Basic 针对 SQL Server 数据库编写的不完整 LINQ 查询，并具有完全类型检查和 IntelliSense 支持。</span><span class="sxs-lookup"><span data-stu-id="a7cc5-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 ![显示具有 Intellisense 的 LINQ 查询的图表。](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a><span data-ttu-id="a7cc5-114">后续步骤</span><span class="sxs-lookup"><span data-stu-id="a7cc5-114">Next Steps</span></span>  
 <span data-ttu-id="a7cc5-115">若要了解有关 LINQ 的详细信息，请首先熟悉入门部分中的一些基本概念[入门使用 LINQ in Visual Basic](getting-started-with-linq.md)，然后阅读你感兴趣的 linq 技术的文档：</span><span class="sxs-lookup"><span data-stu-id="a7cc5-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in Visual Basic](getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
- <span data-ttu-id="a7cc5-116">SQL Server 数据库：[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="a7cc5-116">SQL Server databases: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span></span>  
  
- <span data-ttu-id="a7cc5-117">XML 文档： [LINQ to XML （Visual Basic）](linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="a7cc5-117">XML documents: [LINQ to XML (Visual Basic)](linq-to-xml.md)</span></span>  
  
- <span data-ttu-id="a7cc5-118">ADO.NET 数据集：[LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="a7cc5-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
- <span data-ttu-id="a7cc5-119">.NET 集合、文件、字符串等： [LINQ to Objects （Visual Basic）](linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="a7cc5-119">.NET collections, files, strings and so on: [LINQ to Objects (Visual Basic)](linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7cc5-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7cc5-120">See also</span></span>

- [<span data-ttu-id="a7cc5-121">语言集成查询 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7cc5-121">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
