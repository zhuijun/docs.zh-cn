---
title: 查询操作中的类型关系
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: 73a287541ddf115510bf6ab5c830eafac370cc3a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406724"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="999cb-102">查询操作中的类型关系 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="999cb-102">Type Relationships in Query Operations (Visual Basic)</span></span>

<span data-ttu-id="999cb-103">在语言集成查询（LINQ）查询操作中使用的变量是强类型化的，并且必须彼此兼容。</span><span class="sxs-lookup"><span data-stu-id="999cb-103">Variables used in Language-Integrated Query (LINQ) query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="999cb-104">强类型化在数据源、查询本身和查询执行中使用。</span><span class="sxs-lookup"><span data-stu-id="999cb-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="999cb-105">下图标识用于描述 LINQ 查询的术语。</span><span class="sxs-lookup"><span data-stu-id="999cb-105">The following illustration identifies terms used to describe a LINQ query.</span></span> <span data-ttu-id="999cb-106">有关查询各个部分的详细信息，请参阅[基本查询操作（Visual Basic）](basic-query-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="999cb-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](basic-query-operations.md).</span></span>

![显示突出显示了元素的伪代码查询的屏幕截图。](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

<span data-ttu-id="999cb-108">查询中范围变量的类型必须与数据源中的元素类型兼容。</span><span class="sxs-lookup"><span data-stu-id="999cb-108">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="999cb-109">查询变量的类型必须与子句中定义的序列元素兼容 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="999cb-109">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="999cb-110">最后，序列元素的类型还必须与用于执行查询的语句中使用的循环控制变量的类型兼容 `For Each` 。</span><span class="sxs-lookup"><span data-stu-id="999cb-110">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="999cb-111">这种强类型化有助于在编译时标识错误的类型。</span><span class="sxs-lookup"><span data-stu-id="999cb-111">This strong typing facilitates identification of type errors at compile time.</span></span>

<span data-ttu-id="999cb-112">通过实现局部类型推理（也称为*隐式*类型），Visual Basic 使强类型化变得非常方便。</span><span class="sxs-lookup"><span data-stu-id="999cb-112">Visual Basic makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="999cb-113">上一示例中使用了该功能，您将看到它在整个 LINQ 示例和文档中使用。</span><span class="sxs-lookup"><span data-stu-id="999cb-113">That feature is used in the previous example, and you will see it used throughout the LINQ samples and documentation.</span></span> <span data-ttu-id="999cb-114">在 Visual Basic 中，只需使用没有子句的语句即可完成本地类型推断 `Dim` `As` 。</span><span class="sxs-lookup"><span data-stu-id="999cb-114">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="999cb-115">在下面的示例中， `city` 强类型化为字符串。</span><span class="sxs-lookup"><span data-stu-id="999cb-115">In the following example, `city` is strongly typed as a string.</span></span>

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="999cb-116">仅当设置为时，局部类型推理才有效 `Option Infer` `On` 。</span><span class="sxs-lookup"><span data-stu-id="999cb-116">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="999cb-117">有关详细信息，请参阅[Option 推理语句](../../../language-reference/statements/option-infer-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="999cb-117">For more information, see [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>

<span data-ttu-id="999cb-118">但是，即使在查询中使用局部类型推理，数据源、查询变量和查询执行循环中的变量也存在相同的类型关系。</span><span class="sxs-lookup"><span data-stu-id="999cb-118">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="999cb-119">编写 LINQ 查询或使用文档中的示例和代码示例时，基本了解这些类型关系非常有用。</span><span class="sxs-lookup"><span data-stu-id="999cb-119">It is useful to have a basic understanding of these type relationships when you are writing LINQ queries, or working with the samples and code examples in the documentation.</span></span>

<span data-ttu-id="999cb-120">对于与从数据源返回的类型不匹配的范围变量，可能需要指定显式类型。</span><span class="sxs-lookup"><span data-stu-id="999cb-120">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="999cb-121">您可以通过使用子句指定范围变量的类型 `As` 。</span><span class="sxs-lookup"><span data-stu-id="999cb-121">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="999cb-122">但是，如果转换是[收缩转换](../../language-features/data-types/widening-and-narrowing-conversions.md)并且设置为，则会导致错误 `Option Strict` `On` 。</span><span class="sxs-lookup"><span data-stu-id="999cb-122">However, this results in an error if the conversion is a [narrowing conversion](../../language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="999cb-123">因此，建议您对从数据源检索的值执行转换。</span><span class="sxs-lookup"><span data-stu-id="999cb-123">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="999cb-124">您可以使用方法将数据源中的值转换为显式范围变量类型 <xref:System.Linq.Enumerable.Cast%2A> 。</span><span class="sxs-lookup"><span data-stu-id="999cb-124">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="999cb-125">还可以将子句中选择的值强制转换 `Select` 为与范围变量的类型不同的显式类型。</span><span class="sxs-lookup"><span data-stu-id="999cb-125">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="999cb-126">下面的代码演示了这些要点。</span><span class="sxs-lookup"><span data-stu-id="999cb-126">These points are illustrated in the following code.</span></span>

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="999cb-127">返回源数据的整个元素的查询</span><span class="sxs-lookup"><span data-stu-id="999cb-127">Queries That Return Entire Elements of the Source Data</span></span>

<span data-ttu-id="999cb-128">下面的示例演示一个 LINQ 查询操作，该操作返回从源数据中选择的一系列元素。</span><span class="sxs-lookup"><span data-stu-id="999cb-128">The following example shows a LINQ query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="999cb-129">源 `names` 包含一个字符串数组，并且查询输出是一个序列，其中包含以字母 M 开头的字符串。</span><span class="sxs-lookup"><span data-stu-id="999cb-129">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

<span data-ttu-id="999cb-130">这等效于以下代码，但更短且更易于编写。</span><span class="sxs-lookup"><span data-stu-id="999cb-130">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="999cb-131">在查询中，依赖于本地类型推理是 Visual Basic 中的首选样式。</span><span class="sxs-lookup"><span data-stu-id="999cb-131">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

<span data-ttu-id="999cb-132">上述两个代码示例都存在以下关系，无论类型是隐式还是显式确定的。</span><span class="sxs-lookup"><span data-stu-id="999cb-132">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>

1. <span data-ttu-id="999cb-133">数据源中的元素的类型 `names` 是查询中范围变量的类型 `name` 。</span><span class="sxs-lookup"><span data-stu-id="999cb-133">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>

2. <span data-ttu-id="999cb-134">选择的对象的类型 `name` 决定查询变量的类型 `mNames` 。</span><span class="sxs-lookup"><span data-stu-id="999cb-134">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="999cb-135">下面 `name` 是一个字符串，因此查询变量是 Visual Basic 中的 IEnumerable （的字符串）。</span><span class="sxs-lookup"><span data-stu-id="999cb-135">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>

3. <span data-ttu-id="999cb-136">在 `mNames` 循环中执行中定义的查询 `For Each` 。</span><span class="sxs-lookup"><span data-stu-id="999cb-136">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="999cb-137">循环将循环访问执行查询的结果。</span><span class="sxs-lookup"><span data-stu-id="999cb-137">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="999cb-138">由于 `mNames` 在执行时将返回一个字符串序列，所以循环迭代变量 `nm` 也是一个字符串。</span><span class="sxs-lookup"><span data-stu-id="999cb-138">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>

## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="999cb-139">从选定元素返回一个字段的查询</span><span class="sxs-lookup"><span data-stu-id="999cb-139">Queries That Return One Field from Selected Elements</span></span>

<span data-ttu-id="999cb-140">下面的示例演示一个 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 查询操作，该操作返回一个序列，该序列仅包含从数据源中选择的每个元素的一个部分。</span><span class="sxs-lookup"><span data-stu-id="999cb-140">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="999cb-141">查询采用对象的集合 `Customer` 作为其数据源，并仅在 `Name` 结果中的属性中进行投影。</span><span class="sxs-lookup"><span data-stu-id="999cb-141">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="999cb-142">因为客户名称是字符串，所以查询生成一个字符串序列作为输出。</span><span class="sxs-lookup"><span data-stu-id="999cb-142">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim custNames = From cust In customers
                Where cust.City = "London"
                Select cust.Name

For Each custName In custNames
    Console.WriteLine(custName)
Next
```

<span data-ttu-id="999cb-143">变量之间的关系类似于简单示例中的关系。</span><span class="sxs-lookup"><span data-stu-id="999cb-143">The relationships between variables are like those in the simpler example.</span></span>

1. <span data-ttu-id="999cb-144">数据源中的元素的类型 `customers` 是查询中范围变量的类型 `cust` 。</span><span class="sxs-lookup"><span data-stu-id="999cb-144">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="999cb-145">在此示例中，该类型为 `Customer` 。</span><span class="sxs-lookup"><span data-stu-id="999cb-145">In this example, that type is `Customer`.</span></span>

2. <span data-ttu-id="999cb-146">`Select`语句返回 `Name` 每个对象的属性， `Customer` 而非整个对象。</span><span class="sxs-lookup"><span data-stu-id="999cb-146">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="999cb-147">因为 `Name` 是一个字符串，所以查询变量 `custNames` 将再次为 IEnumerable （字符串），而不是 `Customer` 。</span><span class="sxs-lookup"><span data-stu-id="999cb-147">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>

3. <span data-ttu-id="999cb-148">因为 `custNames` 表示一个字符串序列，所以 `For Each` 循环的迭代变量 `custName` 必须是字符串。</span><span class="sxs-lookup"><span data-stu-id="999cb-148">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>

<span data-ttu-id="999cb-149">如果没有局部类型推理，则上一个示例将更难编写和理解，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="999cb-149">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>

```vb
' Method GetTable returns a table of Customer objects.
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()
 Dim custNames As IEnumerable(Of String) =
     From cust As Customer In customers
     Where cust.City = "London"
     Select cust.Name

 For Each custName As String In custNames
     Console.WriteLine(custName)
 Next
```

## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="999cb-150">需要匿名类型的查询</span><span class="sxs-lookup"><span data-stu-id="999cb-150">Queries That Require Anonymous Types</span></span>

<span data-ttu-id="999cb-151">下面的示例演示一个更复杂的情况。</span><span class="sxs-lookup"><span data-stu-id="999cb-151">The following example shows a more complex situation.</span></span> <span data-ttu-id="999cb-152">在上面的示例中，显式指定所有变量的类型是不方便的。</span><span class="sxs-lookup"><span data-stu-id="999cb-152">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="999cb-153">在此示例中，这是不可能的。</span><span class="sxs-lookup"><span data-stu-id="999cb-153">In this example, it is impossible.</span></span> <span data-ttu-id="999cb-154">`Customer`此查询中的子句不是从数据源中选择整个元素，也不是从每个元素中选择单个字段，而是 `Select` 返回原始对象的两个属性 `Customer` ： `Name` 和 `City` 。</span><span class="sxs-lookup"><span data-stu-id="999cb-154">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="999cb-155">在响应 `Select` 子句时，编译器会定义包含这两个属性的匿名类型。</span><span class="sxs-lookup"><span data-stu-id="999cb-155">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="999cb-156">`nameCityQuery`在循环中执行的结果 `For Each` 是新匿名类型的实例的集合。</span><span class="sxs-lookup"><span data-stu-id="999cb-156">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="999cb-157">由于匿名类型没有可使用的名称，因此不能指定 `nameCityQuery` 或显式指定类型 `custInfo` 。</span><span class="sxs-lookup"><span data-stu-id="999cb-157">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="999cb-158">也就是说，如果使用匿名类型，则没有要在中使用的类型名称 `String` `IEnumerable(Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="999cb-158">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="999cb-159">有关详细信息，请参阅[匿名类型](../../language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="999cb-159">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>

```vb
' Method GetTable returns a table of Customer objects.
Dim customers = db.GetTable(Of Customer)()
Dim nameCityQuery = From cust In customers
                    Where cust.City = "London"
                    Select cust.Name, cust.City

For Each custInfo In nameCityQuery
    Console.WriteLine(custInfo.Name)
Next
```

<span data-ttu-id="999cb-160">尽管不能为上一示例中的所有变量指定类型，但关系仍保持不变。</span><span class="sxs-lookup"><span data-stu-id="999cb-160">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>

1. <span data-ttu-id="999cb-161">数据源中元素的类型再次为查询中范围变量的类型。</span><span class="sxs-lookup"><span data-stu-id="999cb-161">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="999cb-162">在此示例中， `cust` 是的实例 `Customer` 。</span><span class="sxs-lookup"><span data-stu-id="999cb-162">In this example, `cust` is an instance of `Customer`.</span></span>

2. <span data-ttu-id="999cb-163">由于 `Select` 语句生成匿名类型，因此 `nameCityQuery` 必须以匿名类型的形式隐式类型化查询变量。</span><span class="sxs-lookup"><span data-stu-id="999cb-163">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="999cb-164">匿名类型没有可使用的名称，因此不能显式指定。</span><span class="sxs-lookup"><span data-stu-id="999cb-164">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>

3. <span data-ttu-id="999cb-165">循环中迭代变量的类型 `For Each` 是步骤2中创建的匿名类型。</span><span class="sxs-lookup"><span data-stu-id="999cb-165">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="999cb-166">因为类型没有可用名称，所以必须隐式确定循环迭代变量的类型。</span><span class="sxs-lookup"><span data-stu-id="999cb-166">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>

## <a name="see-also"></a><span data-ttu-id="999cb-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="999cb-167">See also</span></span>

- [<span data-ttu-id="999cb-168">Visual Basic 中的 LINQ 入门</span><span class="sxs-lookup"><span data-stu-id="999cb-168">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="999cb-169">匿名类型</span><span class="sxs-lookup"><span data-stu-id="999cb-169">Anonymous Types</span></span>](../../language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="999cb-170">局部类型推理</span><span class="sxs-lookup"><span data-stu-id="999cb-170">Local Type Inference</span></span>](../../language-features/variables/local-type-inference.md)
- [<span data-ttu-id="999cb-171">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="999cb-171">Introduction to LINQ in Visual Basic</span></span>](../../language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="999cb-172">LINQ</span><span class="sxs-lookup"><span data-stu-id="999cb-172">LINQ</span></span>](../../language-features/linq/index.md)
- [<span data-ttu-id="999cb-173">查询</span><span class="sxs-lookup"><span data-stu-id="999cb-173">Queries</span></span>](../../../language-reference/queries/index.md)
