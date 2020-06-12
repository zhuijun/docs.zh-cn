---
title: 使用 LINQ 进行数据转换 (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], data transformations
- source elements [LINQ in C#]
- joining multiple inputs [LINQ in C#]
- multiple outputs for one output sequence [LINQ in C#]
- subset of source elements [LINQ in C#]
- data sources [LINQ in C#], data transformations
- data transformations [LINQ in C#]
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
ms.openlocfilehash: d20f5d826620ad8654ddf1e9471ecc894b2c0391
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408518"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="91f32-102">使用 LINQ 进行数据转换 (C#)</span><span class="sxs-lookup"><span data-stu-id="91f32-102">Data Transformations with LINQ (C#)</span></span>
<span data-ttu-id="91f32-103">语言集成查询 (LINQ) 不只是检索数据。</span><span class="sxs-lookup"><span data-stu-id="91f32-103">Language-Integrated Query (LINQ) is not only about retrieving data.</span></span> <span data-ttu-id="91f32-104">它也是用于转换数据的强大工具。</span><span class="sxs-lookup"><span data-stu-id="91f32-104">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="91f32-105">通过使用 LINQ 查询，可以使用源序列作为输入，并通过多种方式对其进行修改，以创建新的输出序列。</span><span class="sxs-lookup"><span data-stu-id="91f32-105">By using a LINQ query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="91f32-106">通过排序和分组，你可以修改序列本身，而无需修改这些元素本身。</span><span class="sxs-lookup"><span data-stu-id="91f32-106">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="91f32-107">但也许 LINQ 查询最强大的功能是创建新类型。</span><span class="sxs-lookup"><span data-stu-id="91f32-107">But perhaps the most powerful feature of LINQ queries is the ability to create new types.</span></span> <span data-ttu-id="91f32-108">这可以在 [select](../../../language-reference/keywords/select-clause.md) 子句中完成。</span><span class="sxs-lookup"><span data-stu-id="91f32-108">This is accomplished in the [select](../../../language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="91f32-109">例如，可以执行下列任务：</span><span class="sxs-lookup"><span data-stu-id="91f32-109">For example, you can perform the following tasks:</span></span>  
  
- <span data-ttu-id="91f32-110">将多个输入序列合并为具有新类型的单个输出序列。</span><span class="sxs-lookup"><span data-stu-id="91f32-110">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
- <span data-ttu-id="91f32-111">创建其元素由源序列中每个元素的一个或多个属性组成的输出序列。</span><span class="sxs-lookup"><span data-stu-id="91f32-111">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
- <span data-ttu-id="91f32-112">创建其元素由对源数据执行的操作结果组成的输出序列。</span><span class="sxs-lookup"><span data-stu-id="91f32-112">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
- <span data-ttu-id="91f32-113">创建其他格式的输出序列。</span><span class="sxs-lookup"><span data-stu-id="91f32-113">Create output sequences in a different format.</span></span> <span data-ttu-id="91f32-114">例如，可以将数据从 SQL 行或文本文件转换为 XML。</span><span class="sxs-lookup"><span data-stu-id="91f32-114">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="91f32-115">这只是几个例子。</span><span class="sxs-lookup"><span data-stu-id="91f32-115">These are just several examples.</span></span> <span data-ttu-id="91f32-116">当然，可以以各种方式在同一查询中组合这些转换。</span><span class="sxs-lookup"><span data-stu-id="91f32-116">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="91f32-117">此外，一个查询的输出序列可以用作新查询的输入序列。</span><span class="sxs-lookup"><span data-stu-id="91f32-117">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="91f32-118">将多个输入联接到一个输出序列中</span><span class="sxs-lookup"><span data-stu-id="91f32-118">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="91f32-119">可以使用 LINQ 查询创建包含元素的输出序列，这些元素来自多个输入序列。</span><span class="sxs-lookup"><span data-stu-id="91f32-119">You can use a LINQ query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="91f32-120">以下示例演示如何组合两个内存中数据结构，但相同的原则可应用于组合来自 XML 或 SQL 或数据集源的数据。</span><span class="sxs-lookup"><span data-stu-id="91f32-120">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="91f32-121">假设以下两种类类型：</span><span class="sxs-lookup"><span data-stu-id="91f32-121">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 <span data-ttu-id="91f32-122">以下示例演示了查询：</span><span class="sxs-lookup"><span data-stu-id="91f32-122">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 <span data-ttu-id="91f32-123">有关详细信息，请参阅 [join 子句](../../../language-reference/keywords/join-clause.md)和 [select 子句](../../../language-reference/keywords/select-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="91f32-123">For more information, see [join clause](../../../language-reference/keywords/join-clause.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="91f32-124">选择每个源元素的子集</span><span class="sxs-lookup"><span data-stu-id="91f32-124">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="91f32-125">有两种主要方法来选择源序列中每个元素的子集：</span><span class="sxs-lookup"><span data-stu-id="91f32-125">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1. <span data-ttu-id="91f32-126">若要仅选择源元素的一个成员，请使用点操作。</span><span class="sxs-lookup"><span data-stu-id="91f32-126">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="91f32-127">在以下示例中，假设 `Customer` 对象包含多个公共属性，包括名为 `City` 的字符串。</span><span class="sxs-lookup"><span data-stu-id="91f32-127">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="91f32-128">在执行时，此查询将生成字符串的输出序列。</span><span class="sxs-lookup"><span data-stu-id="91f32-128">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. <span data-ttu-id="91f32-129">若要创建包含多个源元素属性的元素，可以使用带有命名对象或匿名类型的对象初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="91f32-129">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="91f32-130">以下示例演示如何使用匿名类型封装每个 `Customer` 元素的两个属性：</span><span class="sxs-lookup"><span data-stu-id="91f32-130">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="91f32-131">有关详细信息，请参阅[对象和集合初始值设定项](../../classes-and-structs/object-and-collection-initializers.md)和[匿名类型](../../classes-and-structs/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="91f32-131">For more information, see [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="91f32-132">将内存中对象转换为 XML</span><span class="sxs-lookup"><span data-stu-id="91f32-132">Transforming in-Memory Objects into XML</span></span>  
 <span data-ttu-id="91f32-133">LINQ 查询可以轻松地在内存中数据结构、SQL 数据库、ADO.NET 数据集和 XML 流或文档之间转换数据。</span><span class="sxs-lookup"><span data-stu-id="91f32-133">LINQ queries make it easy to transform data between in-memory data structures, SQL databases, ADO.NET Datasets and XML streams or documents.</span></span> <span data-ttu-id="91f32-134">以下示例将内存中数据结构中的对象转换为 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="91f32-134">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 <span data-ttu-id="91f32-135">此代码生成以下 XML 输出：</span><span class="sxs-lookup"><span data-stu-id="91f32-135">The code produces the following XML output:</span></span>  
  
```xml  
<Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 <span data-ttu-id="91f32-136">有关详细信息，请参阅[在 C# 中创建 XML 树 (LINQ to XML)](./creating-xml-trees-linq-to-xml-2.md)。</span><span class="sxs-lookup"><span data-stu-id="91f32-136">For more information, see [Creating XML Trees in C# (LINQ to XML)](./creating-xml-trees-linq-to-xml-2.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="91f32-137">对源元素执行操作</span><span class="sxs-lookup"><span data-stu-id="91f32-137">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="91f32-138">输出序列可能不包含源序列中的任何元素或元素属性。</span><span class="sxs-lookup"><span data-stu-id="91f32-138">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="91f32-139">输出可能是使用源元素作为输入参数而计算得出的值序列。</span><span class="sxs-lookup"><span data-stu-id="91f32-139">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span>

 <span data-ttu-id="91f32-140">以下查询将采用表示圆半径的数字序列，计算每个半径范围的面积，并返回输出序列，其中包含以所计算面积进行格式设置的字符串。</span><span class="sxs-lookup"><span data-stu-id="91f32-140">The following query will take a sequence of numbers that represent radii of circles, calculate the area for each radius, and return an output sequence containing strings formatted with the calculated area.</span></span>

 <span data-ttu-id="91f32-141">输出序列的每个字符串都将使用[字符串内插](../../../language-reference/tokens/interpolated.md)进行格式设置。</span><span class="sxs-lookup"><span data-stu-id="91f32-141">Each string for the output sequence will be formatted using [string interpolation](../../../language-reference/tokens/interpolated.md).</span></span> <span data-ttu-id="91f32-142">内插字符串的左引号前有一个 `$`，并且可以在内插字符串内部的大括号内执行操作。</span><span class="sxs-lookup"><span data-stu-id="91f32-142">An interpolated string will have a `$` in front of the string's opening quotation mark, and operations can be performed within curly braces placed inside the interpolated string.</span></span> <span data-ttu-id="91f32-143">执行这些操作后，结果将进行串联。</span><span class="sxs-lookup"><span data-stu-id="91f32-143">Once those operations are performed, the results will be concatenated.</span></span>
  
> [!NOTE]
> <span data-ttu-id="91f32-144">如果查询将被转换为另一个域，则不支持在查询表达式中调用方法。</span><span class="sxs-lookup"><span data-stu-id="91f32-144">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="91f32-145">例如，不能在 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 中调用普通的 C# 方法，因为 SQL Server 没有用于它的上下文。</span><span class="sxs-lookup"><span data-stu-id="91f32-145">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="91f32-146">但是，可以将存储过程映射到方法并调用这些方法。</span><span class="sxs-lookup"><span data-stu-id="91f32-146">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="91f32-147">有关详细信息，请参阅[存储过程](../../../../framework/data/adonet/sql/linq/stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="91f32-147">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a><span data-ttu-id="91f32-148">请参阅</span><span class="sxs-lookup"><span data-stu-id="91f32-148">See also</span></span>

- [<span data-ttu-id="91f32-149">语言集成查询 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="91f32-149">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="91f32-150">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="91f32-150">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="91f32-151">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="91f32-151">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)
- [<span data-ttu-id="91f32-152">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="91f32-152">LINQ to XML (C#)</span></span>](./linq-to-xml-overview.md)
- [<span data-ttu-id="91f32-153">LINQ 查询表达式</span><span class="sxs-lookup"><span data-stu-id="91f32-153">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="91f32-154">select 子句</span><span class="sxs-lookup"><span data-stu-id="91f32-154">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
