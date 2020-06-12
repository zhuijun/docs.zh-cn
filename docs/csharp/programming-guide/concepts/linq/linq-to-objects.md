---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: c488e49283f3e30ea729adf111fd9ca297039838
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241560"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="7cac4-102">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="7cac4-102">LINQ to Objects (C#)</span></span>
<span data-ttu-id="7cac4-103">术语“LINQ to Objects”指直接将 LINQ 查询与任何 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.Generic.IEnumerable%601> 集合一起使用，而不使用中间 LINQ 提供程序或 API，例如 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) 或 [LINQ to XML](./linq-to-xml-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="7cac4-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](./linq-to-xml-overview.md).</span></span> <span data-ttu-id="7cac4-104">可以使用 LINQ 来查询任何可枚举的集合，例如 <xref:System.Collections.Generic.List%601>、<xref:System.Array> 或 <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="7cac4-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="7cac4-105">该集合可以是用户定义的集合，也可以是由 .NET API 返回的集合。</span><span class="sxs-lookup"><span data-stu-id="7cac4-105">The collection may be user-defined or may be returned by a .NET API.</span></span>  
  
 <span data-ttu-id="7cac4-106">从根本上说，“LINQ to Objects”表示一种新的处理集合的方法。</span><span class="sxs-lookup"><span data-stu-id="7cac4-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="7cac4-107">采用旧方法，必须编写指定如何从集合检索数据的复杂的 `foreach` 循环。</span><span class="sxs-lookup"><span data-stu-id="7cac4-107">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="7cac4-108">而采用 LINQ 方法，只需编写描述要检索的内容的声明性代码。</span><span class="sxs-lookup"><span data-stu-id="7cac4-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="7cac4-109">此外，LINQ 查询与传统 `foreach` 循环相比具有三大优势：</span><span class="sxs-lookup"><span data-stu-id="7cac4-109">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
1. <span data-ttu-id="7cac4-110">它们更简明、更易读，尤其在筛选多个条件时。</span><span class="sxs-lookup"><span data-stu-id="7cac4-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="7cac4-111">它们使用最少的应用程序代码提供强大的筛选、排序和分组功能。</span><span class="sxs-lookup"><span data-stu-id="7cac4-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="7cac4-112">无需修改或只需做很小的修改即可将它们移植到其他数据源。</span><span class="sxs-lookup"><span data-stu-id="7cac4-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="7cac4-113">通常，对数据执行的操作越复杂，就越能体会到 LINQ 相较于传统迭代技术的优势。</span><span class="sxs-lookup"><span data-stu-id="7cac4-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="7cac4-114">本节的目的是使用一些精选示例来演示 LINQ 方法。</span><span class="sxs-lookup"><span data-stu-id="7cac4-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="7cac4-115">并不打算详尽说明。</span><span class="sxs-lookup"><span data-stu-id="7cac4-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7cac4-116">本节内容</span><span class="sxs-lookup"><span data-stu-id="7cac4-116">In This Section</span></span>  
 [<span data-ttu-id="7cac4-117">LINQ 和字符串 (C#)</span><span class="sxs-lookup"><span data-stu-id="7cac4-117">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)  
 <span data-ttu-id="7cac4-118">阐释如何使用 LINQ 来查询和转换字符串和字符串集合。</span><span class="sxs-lookup"><span data-stu-id="7cac4-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="7cac4-119">还包括指向演示这些原则的主题的链接。</span><span class="sxs-lookup"><span data-stu-id="7cac4-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="7cac4-120">LINQ 和反射 (C#)</span><span class="sxs-lookup"><span data-stu-id="7cac4-120">LINQ and Reflection (C#)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 <span data-ttu-id="7cac4-121">指向演示 LINQ 如何使用反射的示例的链接。</span><span class="sxs-lookup"><span data-stu-id="7cac4-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="7cac4-122">LINQ 和文件目录 (C#)</span><span class="sxs-lookup"><span data-stu-id="7cac4-122">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)  
 <span data-ttu-id="7cac4-123">阐释如何使用 LINQ 来与文件系统进行交互。</span><span class="sxs-lookup"><span data-stu-id="7cac4-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="7cac4-124">还包括指向演示这些概念的主题的链接。</span><span class="sxs-lookup"><span data-stu-id="7cac4-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="7cac4-125">如何使用 LINQ 查询 ArrayList (C#)</span><span class="sxs-lookup"><span data-stu-id="7cac4-125">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="7cac4-126">演示如何使用 C# 查询 ArrayList。</span><span class="sxs-lookup"><span data-stu-id="7cac4-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="7cac4-127">如何为 LINQ 查询添加自定义方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="7cac4-127">How to add custom methods for LINQ queries (C#)</span></span>](./how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="7cac4-128">阐释如何通过向 <xref:System.Collections.Generic.IEnumerable%601> 接口中添加扩展方法来扩展可用于 LINQ 查询的方法集。</span><span class="sxs-lookup"><span data-stu-id="7cac4-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="7cac4-129">语言集成查询 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7cac4-129">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)  
 <span data-ttu-id="7cac4-130">提供指向阐释 LINQ 并提供执行查询的代码示例的主题的链接。</span><span class="sxs-lookup"><span data-stu-id="7cac4-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
