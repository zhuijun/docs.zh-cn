---
title: LINQ 查询操作中的类型关系 (C#)
description: 了解 LINQ 查询中的变量类型如何相互关联。 LINQ 查询操作在数据源、查询及执行中是强类型的。
ms.date: 07/20/2015
helpviewer_keywords:
- inferring type information [LINQ in C#]
- data sources [LINQ in C#], type relationships
- queries [LINQ in C#], type relationships
- relationships [LINQ in C#]
- type relationships [LINQ in C#]
- variable relationships [LINQ in C#]
- type information inferred [LINQ in C#]
- data transformations [LINQ in C#]
- LINQ [C#], type relationships
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
ms.openlocfilehash: 78cdb550e59bc82386d34f0e2bf6b1cae11d72de
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203977"
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="546d1-104">LINQ 查询操作中的类型关系 (C#)</span><span class="sxs-lookup"><span data-stu-id="546d1-104">Type Relationships in LINQ Query Operations (C#)</span></span>

<span data-ttu-id="546d1-105">若要有效编写查询，应了解完整的查询操作中的变量类型是如何全部彼此关联的。</span><span class="sxs-lookup"><span data-stu-id="546d1-105">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="546d1-106">如果了解这些关系，就能够更容易地理解文档中的 LINQ 示例和代码示例。</span><span class="sxs-lookup"><span data-stu-id="546d1-106">If you understand these relationships you will more easily comprehend the LINQ samples and code examples in the documentation.</span></span> <span data-ttu-id="546d1-107">另外，还能了解在使用 `var` 隐式对变量进行类型化时的后台操作。</span><span class="sxs-lookup"><span data-stu-id="546d1-107">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 <span data-ttu-id="546d1-108">LINQ 查询操作在数据源、查询本身及查询执行中是强类型的。</span><span class="sxs-lookup"><span data-stu-id="546d1-108">LINQ query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="546d1-109">查询中变量的类型必须与数据源中元素的类型和 `foreach` 语句中迭代变量的类型兼容。</span><span class="sxs-lookup"><span data-stu-id="546d1-109">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="546d1-110">此强类型保证在编译时捕获类型错误，以便可以在用户遇到这些错误之前更正它们。</span><span class="sxs-lookup"><span data-stu-id="546d1-110">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="546d1-111">为了演示这些类型关系，下面的大多数示例对所有变量使用显式类型。</span><span class="sxs-lookup"><span data-stu-id="546d1-111">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="546d1-112">最后一个示例演示在利用使用 [var](../../../language-reference/keywords/var.md) 的隐式类型时，如何应用相同的原则。</span><span class="sxs-lookup"><span data-stu-id="546d1-112">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="546d1-113">不转换源数据的查询</span><span class="sxs-lookup"><span data-stu-id="546d1-113">Queries that do not Transform the Source Data</span></span>  

 <span data-ttu-id="546d1-114">下图演示不对数据执行转换的 LINQ to Objects 查询操作。</span><span class="sxs-lookup"><span data-stu-id="546d1-114">The following illustration shows a LINQ to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="546d1-115">源包含一个字符串序列，查询输出也是一个字符串序列。</span><span class="sxs-lookup"><span data-stu-id="546d1-115">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 ![关系图显示 LINQ 查询中数据类型的关系。](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. <span data-ttu-id="546d1-117">数据源的类型参数决定范围变量的类型。</span><span class="sxs-lookup"><span data-stu-id="546d1-117">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="546d1-118">所选对象的类型决定查询变量的类型。</span><span class="sxs-lookup"><span data-stu-id="546d1-118">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="546d1-119">此处的 `name` 是一个字符串。</span><span class="sxs-lookup"><span data-stu-id="546d1-119">Here `name` is a string.</span></span> <span data-ttu-id="546d1-120">因此，查询变量是一个 `IEnumerable<string>`。</span><span class="sxs-lookup"><span data-stu-id="546d1-120">Therefore, the query variable is an `IEnumerable<string>`.</span></span>  
  
3. <span data-ttu-id="546d1-121">在 `foreach` 语句中循环访问查询变量。</span><span class="sxs-lookup"><span data-stu-id="546d1-121">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="546d1-122">因为查询变量是一个字符串序列，所以迭代变量也是一个字符串。</span><span class="sxs-lookup"><span data-stu-id="546d1-122">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="546d1-123">转换源数据的查询</span><span class="sxs-lookup"><span data-stu-id="546d1-123">Queries that Transform the Source Data</span></span>  

 <span data-ttu-id="546d1-124">下图演示对数据执行简单转换的 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 查询操作。</span><span class="sxs-lookup"><span data-stu-id="546d1-124">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="546d1-125">查询将一个 `Customer` 对象序列用作输入，并只选择结果中的 `Name` 属性。</span><span class="sxs-lookup"><span data-stu-id="546d1-125">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="546d1-126">因为 `Name` 是一个字符串，所以查询生成一个字符串序列作为输出。</span><span class="sxs-lookup"><span data-stu-id="546d1-126">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 ![关系图显示转换数据类型的查询。](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. <span data-ttu-id="546d1-128">数据源的类型参数决定范围变量的类型。</span><span class="sxs-lookup"><span data-stu-id="546d1-128">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="546d1-129">`select` 语句返回 `Name` 属性，而非完整的 `Customer` 对象。</span><span class="sxs-lookup"><span data-stu-id="546d1-129">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="546d1-130">因为 `Name` 是一个字符串，所以 `custNameQuery` 的类型参数是 `string`，而非 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="546d1-130">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3. <span data-ttu-id="546d1-131">因为 `custNameQuery` 是一个字符串序列，所以 `foreach` 循环的迭代变量也必须是 `string`。</span><span class="sxs-lookup"><span data-stu-id="546d1-131">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="546d1-132">下图演示稍微复杂的转换。</span><span class="sxs-lookup"><span data-stu-id="546d1-132">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="546d1-133">`select` 语句返回只捕获原始 `Customer` 对象的两个成员的匿名类型。</span><span class="sxs-lookup"><span data-stu-id="546d1-133">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 ![关系图显示转换数据类型的更复杂的查询。](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. <span data-ttu-id="546d1-135">数据源的类型参数始终为查询中范围变量的类型。</span><span class="sxs-lookup"><span data-stu-id="546d1-135">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2. <span data-ttu-id="546d1-136">因为 `select` 语句生成匿名类型，所以必须使用 `var` 隐式类型化查询变量。</span><span class="sxs-lookup"><span data-stu-id="546d1-136">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3. <span data-ttu-id="546d1-137">因为查询变量的类型是隐式的，所以 `foreach` 循环中的迭代变量也必须是隐式的。</span><span class="sxs-lookup"><span data-stu-id="546d1-137">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="546d1-138">让编译器推断类型信息</span><span class="sxs-lookup"><span data-stu-id="546d1-138">Letting the compiler infer type information</span></span>  

 <span data-ttu-id="546d1-139">虽然需要了解查询操作中的类型关系，但是也可以选择让编译器执行全部工作。</span><span class="sxs-lookup"><span data-stu-id="546d1-139">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="546d1-140">关键字 [var](../../../language-reference/keywords/var.md) 可用于查询操作中的任何本地变量。</span><span class="sxs-lookup"><span data-stu-id="546d1-140">The keyword [var](../../../language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="546d1-141">下图与前面讨论的第二个示例相似。</span><span class="sxs-lookup"><span data-stu-id="546d1-141">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="546d1-142">但是，编译器为查询操作中的各个变量提供强类型。</span><span class="sxs-lookup"><span data-stu-id="546d1-142">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 ![关系图显示具有隐式类型的类型流。](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 <span data-ttu-id="546d1-144">有关 `var` 的详细信息，请参阅[隐式类型本地变量](../../classes-and-structs/implicitly-typed-local-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="546d1-144">For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
