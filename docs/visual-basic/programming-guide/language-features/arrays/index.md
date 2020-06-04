---
title: 数组
ms.date: 12/06/2017
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
ms.openlocfilehash: 5093f28f05c5b72294dce9a4e69723acafb31a9f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413087"
---
# <a name="arrays-in-visual-basic"></a><span data-ttu-id="ab728-102">Visual Basic 中的数组</span><span class="sxs-lookup"><span data-stu-id="ab728-102">Arrays in Visual Basic</span></span>

<span data-ttu-id="ab728-103">数组是一组值，这些值是逻辑上相互关联的*元素*。</span><span class="sxs-lookup"><span data-stu-id="ab728-103">An array is a set of values, which are termed *elements*, that are logically related to each other.</span></span> <span data-ttu-id="ab728-104">例如，数组可能包含语法学校每个年级的学生数;数组中的每个元素都是一年级的学生数。</span><span class="sxs-lookup"><span data-stu-id="ab728-104">For example, an array may consist of the number of students in each grade in a grammar school; each element of the array is the number of students in a single grade.</span></span> <span data-ttu-id="ab728-105">同样，数组可能包含学生对类的成绩;数组的每个元素都是一个级别。</span><span class="sxs-lookup"><span data-stu-id="ab728-105">Similarly, an array may consist of a student's grades for a class; each element of the array is a single grade.</span></span>

<span data-ttu-id="ab728-106">可以通过单独的变量存储我们的每个数据项。</span><span class="sxs-lookup"><span data-stu-id="ab728-106">It is possible individual variables to store each of our data items.</span></span> <span data-ttu-id="ab728-107">例如，如果我们的应用程序分析学生评分，则可以为每位学生的成绩使用单独的变量，如 `englishGrade1` 、等 `englishGrade2` 。此方法有三个主要限制：</span><span class="sxs-lookup"><span data-stu-id="ab728-107">For example, if our application analyzes student grades, we can use a separate variable for each student's grade, such as `englishGrade1`, `englishGrade2`, etc. This approach has three major limitations:</span></span>

- <span data-ttu-id="ab728-108">我们必须在设计时了解我们必须处理的成绩。</span><span class="sxs-lookup"><span data-stu-id="ab728-108">We have to know at design time exactly how many grades we have to handle.</span></span>
- <span data-ttu-id="ab728-109">处理大量成绩很快就会变得难以处理。</span><span class="sxs-lookup"><span data-stu-id="ab728-109">Handling large numbers of grades quickly becomes unwieldy.</span></span> <span data-ttu-id="ab728-110">这进而会使应用程序更有可能出现严重错误。</span><span class="sxs-lookup"><span data-stu-id="ab728-110">This in turn makes an application much more likely to have serious bugs.</span></span>
- <span data-ttu-id="ab728-111">很难维护。</span><span class="sxs-lookup"><span data-stu-id="ab728-111">It is difficult to maintain.</span></span> <span data-ttu-id="ab728-112">我们添加的每个新评分要求修改、重新编译和重新部署应用程序。</span><span class="sxs-lookup"><span data-stu-id="ab728-112">Each new grade that we add requires that the application be modified, recompiled, and redeployed.</span></span>

<span data-ttu-id="ab728-113">通过使用数组，可以按相同的名称引用这些相关的值，并使用名为*索引*或*下标*的数字来根据元素在数组中的位置来识别单个元素。</span><span class="sxs-lookup"><span data-stu-id="ab728-113">By using an array, you can refer to these related values by the same name, and use a number that’s called an *index* or *subscript* to identify an individual element based on its position in the array.</span></span> <span data-ttu-id="ab728-114">数组的索引范围为0到数组中元素总数减1之间的值。</span><span class="sxs-lookup"><span data-stu-id="ab728-114">The indexes of an array range from 0 to one less than the total number of elements in the array.</span></span> <span data-ttu-id="ab728-115">如果使用 Visual Basic 语法来定义数组的大小，则指定其最高索引，而不是数组中元素的总数。</span><span class="sxs-lookup"><span data-stu-id="ab728-115">When you use Visual Basic syntax to define the size of an array, you specify its highest index, not the total number of elements in the array.</span></span> <span data-ttu-id="ab728-116">您可以将数组作为一个单元处理，并能够循环访问其元素，而无需确切了解它在设计时所包含的元素数目。</span><span class="sxs-lookup"><span data-stu-id="ab728-116">You can work with the array as a unit, and the ability to iterate its elements frees you from needing to know exactly how many elements it contains at design time.</span></span>

<span data-ttu-id="ab728-117">在进行说明之前，请看几个简单的示例：</span><span class="sxs-lookup"><span data-stu-id="ab728-117">Some quick examples before explanation:</span></span>

```vb
' Declare a single-dimension array of 5 numbers.
Dim numbers(4) As Integer

' Declare a single-dimension array and set its 4 values.
Dim numbers = New Integer() {1, 2, 4, 8}

' Change the size of an existing array to 16 elements and retain the current values.
ReDim Preserve numbers(15)

' Redefine the size of an existing array and reset the values.
ReDim numbers(15)

' Declare a 6 x 6 multidimensional array.
Dim matrix(5, 5) As Double

' Declare a 4 x 3 multidimensional array and set array element values.
Dim matrix = New Integer(3, 2) {{1, 2, 3}, {2, 3, 4}, {3, 4, 5}, {4, 5, 6}}

' Declare a jagged array
Dim sales()() As Double = New Double(11)() {}
```

## <a name="array-elements-in-a-simple-array"></a><span data-ttu-id="ab728-118">简单数组中的数组元素</span><span class="sxs-lookup"><span data-stu-id="ab728-118">Array elements in a simple array</span></span>

<span data-ttu-id="ab728-119">让我们创建一个名为的数组 `students` ，用于存储语法学校每个年级的学生数量。</span><span class="sxs-lookup"><span data-stu-id="ab728-119">Let's create an array named `students` to store the number of students in each grade in a grammar school.</span></span> <span data-ttu-id="ab728-120">这些元素的索引范围为 0 到 6。</span><span class="sxs-lookup"><span data-stu-id="ab728-120">The indexes of the elements range from 0 through 6.</span></span> <span data-ttu-id="ab728-121">使用此数组比声明七个变量更简单。</span><span class="sxs-lookup"><span data-stu-id="ab728-121">Using this array is simpler than declaring seven variables.</span></span>

<span data-ttu-id="ab728-122">下图显示了 `students` 数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-122">The following illustration shows the `students` array.</span></span> <span data-ttu-id="ab728-123">对于数组的每个元素：</span><span class="sxs-lookup"><span data-stu-id="ab728-123">For each element of the array:</span></span>

- <span data-ttu-id="ab728-124">元素索引表示年级（索引 0 表示幼儿园）。</span><span class="sxs-lookup"><span data-stu-id="ab728-124">The index of the element represents the grade (index 0 represents kindergarten).</span></span>

- <span data-ttu-id="ab728-125">元素中包含的值表示每个年级的学生数量。</span><span class="sxs-lookup"><span data-stu-id="ab728-125">The value that’s contained in the element represents the number of students in that grade.</span></span>

![显示学生数数组的关系图](./media/index/students-array-elements.gif)

<span data-ttu-id="ab728-127">下面的示例包含创建和使用数组的 Visual Basic 代码：</span><span class="sxs-lookup"><span data-stu-id="ab728-127">The following example contains the Visual Basic code that creates and uses the array:</span></span>

[!code-vb[simple-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]

<span data-ttu-id="ab728-128">该示例执行三个操作：</span><span class="sxs-lookup"><span data-stu-id="ab728-128">The example does three things:</span></span>

- <span data-ttu-id="ab728-129">它声明 `students` 包含七个元素的数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-129">It declares a `students` array with seven elements.</span></span> <span data-ttu-id="ab728-130">`6`数组声明中的数字指示数组中的最后一个索引; 它小于数组中元素的数目。</span><span class="sxs-lookup"><span data-stu-id="ab728-130">The number `6` in the array declaration indicates the last index in the array; it is one less than the number of elements in the array.</span></span>
- <span data-ttu-id="ab728-131">它将值分配给数组中的每个元素。</span><span class="sxs-lookup"><span data-stu-id="ab728-131">It assigns values to each element in the array.</span></span> <span data-ttu-id="ab728-132">数组元素通过使用数组名称访问，并在括号中包含单个元素的索引。</span><span class="sxs-lookup"><span data-stu-id="ab728-132">Array elements are accessed by using the array name and including the index of the individual element in parentheses.</span></span>
- <span data-ttu-id="ab728-133">它列出数组的每个值。</span><span class="sxs-lookup"><span data-stu-id="ab728-133">It lists each value of the array.</span></span> <span data-ttu-id="ab728-134">该示例使用 [`For`](../../../language-reference/statements/for-next-statement.md) 语句通过索引号来访问数组的每个元素。</span><span class="sxs-lookup"><span data-stu-id="ab728-134">The example uses a [`For`](../../../language-reference/statements/for-next-statement.md) statement to access each element of the array by its index number.</span></span>

<span data-ttu-id="ab728-135">`students`上面的示例中的数组是一维数组，因为它使用一个索引。</span><span class="sxs-lookup"><span data-stu-id="ab728-135">The `students` array in the preceding example is a one-dimensional array because it uses one index.</span></span> <span data-ttu-id="ab728-136">使用多个索引或下标的数组称为*多维*。</span><span class="sxs-lookup"><span data-stu-id="ab728-136">An array that uses more than one index or subscript is called *multidimensional*.</span></span> <span data-ttu-id="ab728-137">有关详细信息，请参阅本文的其余部分和[Visual Basic 中的数组维度](array-dimensions.md)。</span><span class="sxs-lookup"><span data-stu-id="ab728-137">For more information, see the rest of this article and [Array Dimensions in Visual Basic](array-dimensions.md).</span></span>

## <a name="creating-an-array"></a><span data-ttu-id="ab728-138">创建数组</span><span class="sxs-lookup"><span data-stu-id="ab728-138">Creating an array</span></span>

<span data-ttu-id="ab728-139">可以通过多种方式定义数组的大小：</span><span class="sxs-lookup"><span data-stu-id="ab728-139">You can define the size of an array in several ways:</span></span>

- <span data-ttu-id="ab728-140">可在声明数组时指定大小：</span><span class="sxs-lookup"><span data-stu-id="ab728-140">You can specify the size when the array is declared:</span></span>

  [!code-vb[creating1](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]

- <span data-ttu-id="ab728-141">`New`创建数组时，可以使用子句提供数组的大小：</span><span class="sxs-lookup"><span data-stu-id="ab728-141">You can use a `New` clause to supply the size of an array when it’s created:</span></span>

  [!code-vb[creating2](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]

<span data-ttu-id="ab728-142">如果你有现有的数组，则可以通过使用语句来重新定义其大小 [`ReDim`](../../../language-reference/statements/redim-statement.md) 。</span><span class="sxs-lookup"><span data-stu-id="ab728-142">If you have an existing array, you can redefine its size by using the [`ReDim`](../../../language-reference/statements/redim-statement.md) statement.</span></span> <span data-ttu-id="ab728-143">您可以指定该 `ReDim` 语句保留数组中的值，也可以指定它创建一个空数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-143">You can specify that the `ReDim` statement keep the values that are in the array, or you can specify that it create an empty array.</span></span> <span data-ttu-id="ab728-144">下面的示例演示了用 `ReDim` 语句来修改现有数组的大小的不同用法。</span><span class="sxs-lookup"><span data-stu-id="ab728-144">The following example shows different uses of the `ReDim` statement to modify the size of an existing array.</span></span>

[!code-vb[redimensioning](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]

<span data-ttu-id="ab728-145">有关详细信息，请参阅[ReDim 语句](../../../language-reference/statements/redim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ab728-145">For more information, see the [ReDim Statement](../../../language-reference/statements/redim-statement.md).</span></span>

## <a name="storing-values-in-an-array"></a><span data-ttu-id="ab728-146">在数组中存储值</span><span class="sxs-lookup"><span data-stu-id="ab728-146">Storing values in an array</span></span>

<span data-ttu-id="ab728-147">你可以通过使用类型 `Integer`的索引访问数组中的每个位置。</span><span class="sxs-lookup"><span data-stu-id="ab728-147">You can access each location in an array by using an index of type `Integer`.</span></span> <span data-ttu-id="ab728-148">你可以使用括号内的索引来引用每个数组位置，从而存储和检索数组中的值。</span><span class="sxs-lookup"><span data-stu-id="ab728-148">You can store and retrieve values in an array by referencing each array location by using its index enclosed in parentheses.</span></span> <span data-ttu-id="ab728-149">多维数组的索引用逗号（，）分隔。</span><span class="sxs-lookup"><span data-stu-id="ab728-149">Indexes for multidimensional arrays are separated by commas (,).</span></span> <span data-ttu-id="ab728-150">每个数组维度都需要一个索引。</span><span class="sxs-lookup"><span data-stu-id="ab728-150">You need one index for each array dimension.</span></span>

<span data-ttu-id="ab728-151">下面的示例演示在数组中存储和检索值的一些语句。</span><span class="sxs-lookup"><span data-stu-id="ab728-151">The following example shows some statements that store and retrieve values in arrays.</span></span>

[!code-vb[store-and-retrieve](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]

## <a name="populating-an-array-with-array-literals"></a><span data-ttu-id="ab728-152">使用数组文本填充数组</span><span class="sxs-lookup"><span data-stu-id="ab728-152">Populating an array with array literals</span></span>

<span data-ttu-id="ab728-153">通过使用数组文本，可以在创建数组时，使用初始值集来填充数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-153">By using an array literal, you can populate an array with an initial set of values at the same time that you create it.</span></span> <span data-ttu-id="ab728-154">数组文本包含用逗号分隔的值列表，这些值被括在括号内 (`{}`)。</span><span class="sxs-lookup"><span data-stu-id="ab728-154">An array literal consists of a list of comma-separated values that are enclosed in braces (`{}`).</span></span>

<span data-ttu-id="ab728-155">通过使用数组文本创建数组时，可以提供数组类型或使用类型推理功能来确定数组类型。</span><span class="sxs-lookup"><span data-stu-id="ab728-155">When you create an array by using an array literal, you can either supply the array type or use type inference to determine the array type.</span></span> <span data-ttu-id="ab728-156">下面的示例演示了这两个选项。</span><span class="sxs-lookup"><span data-stu-id="ab728-156">The following example shows both options.</span></span>

[!code-vb[create-with-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]

<span data-ttu-id="ab728-157">使用类型推理时，数组的类型由文本值列表中的*主导类型*确定。</span><span class="sxs-lookup"><span data-stu-id="ab728-157">When you use type inference, the type of the array is determined by the *dominant type* in the list of literal values.</span></span> <span data-ttu-id="ab728-158">主导类型是数组中所有其他类型可以扩大到的类型。</span><span class="sxs-lookup"><span data-stu-id="ab728-158">The dominant type is the type to which all other types in the array can widen.</span></span> <span data-ttu-id="ab728-159">如果无法确定此唯一类型，基准类型是数组中所有其他类型可以缩小到的唯一类型。</span><span class="sxs-lookup"><span data-stu-id="ab728-159">If this unique type can’t be determined, the dominant type is the unique type to which all other types in the array can narrow.</span></span> <span data-ttu-id="ab728-160">如果无法确定为这两种唯一类型之一，则基准类型是 `Object`。</span><span class="sxs-lookup"><span data-stu-id="ab728-160">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="ab728-161">例如，如果提供给数组文本的值的列表包含 `Integer`、 `Long`和 `Double`类型的值，则生成的数组类型是 `Double`。</span><span class="sxs-lookup"><span data-stu-id="ab728-161">For example, if the list of values that’s supplied to the array literal contains values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="ab728-162">由于 `Integer` 和 `Long` 仅扩大到 `Double` ，因此 `Double` 是基准类型。</span><span class="sxs-lookup"><span data-stu-id="ab728-162">Because `Integer` and `Long` widen only to `Double`, `Double` is the dominant type.</span></span> <span data-ttu-id="ab728-163">有关详细信息，请参阅 [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="ab728-163">For more information, see [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ab728-164">只能对定义为类型成员中的局部变量的数组使用类型推理。</span><span class="sxs-lookup"><span data-stu-id="ab728-164">You can use type inference only for arrays that are defined as local variables in a type member.</span></span> <span data-ttu-id="ab728-165">如果不存在显式类型定义，则在类级别使用数组文本定义的数组的类型为 `Object[]` 。</span><span class="sxs-lookup"><span data-stu-id="ab728-165">If an explicit type definition is absent, arrays defined with array literals at the class level are of type `Object[]`.</span></span> <span data-ttu-id="ab728-166">有关详细信息，请参阅[局部类型推理](../variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="ab728-166">For more information, see [Local type inference](../variables/local-type-inference.md).</span></span>

<span data-ttu-id="ab728-167">请注意，上面的示例将定义 `values` 为类型的数组， `Double` 即使所有数组文本都为类型，也是如此 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="ab728-167">Note that the previous example defines `values` as an array of type `Double` even though all the array literals are of type `Integer`.</span></span> <span data-ttu-id="ab728-168">你可以创建此数组，因为数组文本中的值可以扩大到 `Double` 值。</span><span class="sxs-lookup"><span data-stu-id="ab728-168">You can create this array because the values in the array literal can widen to `Double` values.</span></span>

<span data-ttu-id="ab728-169">还可以使用*嵌套的数组文本*来创建和填充多维数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-169">You can also create and populate a multidimensional array by using *nested array literals*.</span></span> <span data-ttu-id="ab728-170">嵌套的数组文本必须具有与生成的数组一致的多个维度。</span><span class="sxs-lookup"><span data-stu-id="ab728-170">Nested array literals must have a number of dimensions that’s consistent with the resulting array.</span></span> <span data-ttu-id="ab728-171">下面的示例通过使用嵌套的数组文本创建一个二维整数数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-171">The following example creates a two-dimensional array of integers by using nested array literals.</span></span>

[!code-vb[nested-array-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]

<span data-ttu-id="ab728-172">使用嵌套的数组文本创建和填充数组时，如果嵌套数组文本中的元素数目不匹配，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="ab728-172">When using nested array literals to create and populate an array, an error occurs if the number of elements in the nested array literals don't match.</span></span> <span data-ttu-id="ab728-173">如果显式声明数组变量的维数不同于数组文本，也会出现错误。</span><span class="sxs-lookup"><span data-stu-id="ab728-173">An error also occurs if you explicitly declare the array variable to have a different number of dimensions than the array literals.</span></span>

<span data-ttu-id="ab728-174">正如可以对一维数组使用的一样，在使用嵌套的数组文本创建多维数组时，可以依赖类型推理。</span><span class="sxs-lookup"><span data-stu-id="ab728-174">Just as you can for one-dimensional arrays, you can rely on type inference when creating a multidimensional array with nested array literals.</span></span> <span data-ttu-id="ab728-175">推断出的类型是所有嵌套级别的所有数组文本中的所有值的基准类型。</span><span class="sxs-lookup"><span data-stu-id="ab728-175">The inferred type is the dominant type for all the values in all the array literals for all nesting level.</span></span> <span data-ttu-id="ab728-176">下面的示例 `Double[,]` 从类型为和的值创建一个类型为的二维数组 `Integer` `Double` 。</span><span class="sxs-lookup"><span data-stu-id="ab728-176">The following example creates a two-dimensional array of type `Double[,]` from values that are of type `Integer` and `Double`.</span></span>

[!code-vb[nested-type-inference](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]

<span data-ttu-id="ab728-177">有关其他示例，请参阅[如何：在 Visual Basic 中初始化数组变量](how-to-initialize-an-array-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="ab728-177">For additional examples, see [How to: Initialize an Array Variable in Visual Basic](how-to-initialize-an-array-variable.md).</span></span>

## <a name="iterating-through-an-array"></a><span data-ttu-id="ab728-178">循环访问数组</span><span class="sxs-lookup"><span data-stu-id="ab728-178">Iterating through an array</span></span>

<span data-ttu-id="ab728-179">循环访问数组时，可将数组中的每个元素从最小索引访问到最高级别或从最高到最低。</span><span class="sxs-lookup"><span data-stu-id="ab728-179">When you iterate through an array, you access each element in the array from the lowest index to the highest or from the highest to the lowest.</span></span> <span data-ttu-id="ab728-180">通常，使用[For .。。下一语句](../../../language-reference/statements/for-next-statement.md)或[每个 .。。Next 语句](../../../language-reference/statements/for-each-next-statement.md)来循环访问数组的元素。</span><span class="sxs-lookup"><span data-stu-id="ab728-180">Typically, use either the [For...Next Statement](../../../language-reference/statements/for-next-statement.md) or the [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md) to iterate through the elements of an array.</span></span> <span data-ttu-id="ab728-181">如果不知道数组的上限，可以调用 <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> 方法来获取索引的最大值。</span><span class="sxs-lookup"><span data-stu-id="ab728-181">When you don't know the upper bounds of the array, you can call the <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> method to get the highest value of the index.</span></span> <span data-ttu-id="ab728-182">尽管最低索引值几乎始终为0，但您可以调用 <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> 方法来获取索引的最小值。</span><span class="sxs-lookup"><span data-stu-id="ab728-182">Although lowest index value is almost always 0, you can call the <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> method to get the lowest value of the index.</span></span>

<span data-ttu-id="ab728-183">下面的示例通过使用语句循环访问一维数组 [`For...Next`](../../../language-reference/statements/for-next-statement.md) 。</span><span class="sxs-lookup"><span data-stu-id="ab728-183">The following example iterates through a one-dimensional array by using the [`For...Next`](../../../language-reference/statements/for-next-statement.md) statement.</span></span>

[!code-vb[iterate-one-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]

<span data-ttu-id="ab728-184">下面的示例通过使用语句循环访问多维数组 [`For...Next`](../../../language-reference/statements/for-next-statement.md) 。</span><span class="sxs-lookup"><span data-stu-id="ab728-184">The following example iterates through a multidimensional array by using a [`For...Next`](../../../language-reference/statements/for-next-statement.md) statement.</span></span> <span data-ttu-id="ab728-185"><xref:System.Array.GetUpperBound%2A> 方法具有用于指定维度的参数。</span><span class="sxs-lookup"><span data-stu-id="ab728-185">The <xref:System.Array.GetUpperBound%2A> method has a parameter that specifies the dimension.</span></span> <span data-ttu-id="ab728-186">`GetUpperBound(0)`返回第一个维度的最高索引，并 `GetUpperBound(1)` 返回第二个维度的最高索引。</span><span class="sxs-lookup"><span data-stu-id="ab728-186">`GetUpperBound(0)` returns the highest index of the first dimension, and `GetUpperBound(1)` returns the highest index of the second dimension.</span></span>

[!code-vb[iterate-two-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]

<span data-ttu-id="ab728-187">下面的示例使用[For Each .。。](../../../language-reference/statements/for-each-next-statement.md)用于循环访问一维数组和二维数组的 Next 语句。</span><span class="sxs-lookup"><span data-stu-id="ab728-187">The following example uses a [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md)to iterate through a one-dimensional array and a two-dimensional array.</span></span>

[!code-vb[iterate-for-each-next](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]

## <a name="array-size"></a><span data-ttu-id="ab728-188">数组大小</span><span class="sxs-lookup"><span data-stu-id="ab728-188">Array size</span></span>

<span data-ttu-id="ab728-189">数组的大小是数组所有维度的长度的产物。</span><span class="sxs-lookup"><span data-stu-id="ab728-189">The size of an array is the product of the lengths of all its dimensions.</span></span> <span data-ttu-id="ab728-190">它表示数组中当前所包含的元素总数。</span><span class="sxs-lookup"><span data-stu-id="ab728-190">It represents the total number of elements currently contained in the array.</span></span>  <span data-ttu-id="ab728-191">例如，下面的示例声明一个二维数组，每个维度中包含四个元素。</span><span class="sxs-lookup"><span data-stu-id="ab728-191">For example, the following example declares a 2-dimensional array with four elements in each dimension.</span></span> <span data-ttu-id="ab728-192">如示例中的输出所示，数组的大小为16（或（3 + 1） \* （3 + 1）。</span><span class="sxs-lookup"><span data-stu-id="ab728-192">As the output from the example shows, the array's size is 16 (or (3 + 1) \* (3 + 1).</span></span>

[!code-vb[array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]

> [!NOTE]
> <span data-ttu-id="ab728-193">对数组大小的讨论不适用于交错数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-193">This discussion of array size does not apply to jagged arrays.</span></span> <span data-ttu-id="ab728-194">有关交错数组和确定交错数组大小的信息，请参阅[交错](#jagged-arrays)数组部分。</span><span class="sxs-lookup"><span data-stu-id="ab728-194">For information on jagged arrays and determining the size of a jagged array, see the [Jagged arrays](#jagged-arrays) section.</span></span>

<span data-ttu-id="ab728-195">可以通过使用 <xref:System.Array.Length%2A?displayProperty=nameWithType> 属性查找数组大小。</span><span class="sxs-lookup"><span data-stu-id="ab728-195">You can find the size of an array by using the <xref:System.Array.Length%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="ab728-196">您可以通过使用方法查找多维数组的每个维度的长度 <xref:System.Array.GetLength%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ab728-196">You can find the length of each dimension of a multidimensional array by using the <xref:System.Array.GetLength%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="ab728-197">可以通过向数组变量分配新数组对象或使用[ `ReDim` 语句](../../../language-reference/statements/redim-statement.md)语句来调整其大小。</span><span class="sxs-lookup"><span data-stu-id="ab728-197">You can resize an array variable by assigning a new array object to it or by using the [`ReDim` Statement](../../../language-reference/statements/redim-statement.md) statement.</span></span> <span data-ttu-id="ab728-198">下面的示例使用 `ReDim` 语句将100元素数组更改为51元素数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-198">The following example uses the `ReDim` statement to change a 100-element array to a 51-element array.</span></span>

[!code-vb[resize-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]

<span data-ttu-id="ab728-199">当处理数组大小时，需要记住几件事情。</span><span class="sxs-lookup"><span data-stu-id="ab728-199">There are several things to keep in mind when dealing with the size of an array.</span></span>

|||
|---|---|
|<span data-ttu-id="ab728-200">维度长度</span><span class="sxs-lookup"><span data-stu-id="ab728-200">Dimension Length</span></span>|<span data-ttu-id="ab728-201">每个维度的索引都是从0开始的，这意味着它的范围介于0到其上限之间。</span><span class="sxs-lookup"><span data-stu-id="ab728-201">The index of each dimension is 0-based, which means it ranges from 0 to its upper bound.</span></span> <span data-ttu-id="ab728-202">因此，给定维度的长度比该维度已声明的上限大1。</span><span class="sxs-lookup"><span data-stu-id="ab728-202">Therefore, the length of a given dimension is one greater than the declared upper bound of that dimension.</span></span>|
|<span data-ttu-id="ab728-203">长度限制</span><span class="sxs-lookup"><span data-stu-id="ab728-203">Length Limits</span></span>|<span data-ttu-id="ab728-204">数组的每个维度的长度限制为数据类型的最大值 `Integer` ，即 <xref:System.Int32.MaxValue?displayProperty=nameWithType> 或（2 ^ 31）-1。</span><span class="sxs-lookup"><span data-stu-id="ab728-204">The length of every dimension of an array is limited to the maximum value of the `Integer` data type, which is <xref:System.Int32.MaxValue?displayProperty=nameWithType> or (2 ^ 31) - 1.</span></span> <span data-ttu-id="ab728-205">但是，数组的总大小还受到系统上可用的内存限制。</span><span class="sxs-lookup"><span data-stu-id="ab728-205">However, the total size of an array is also limited by the memory available on your system.</span></span> <span data-ttu-id="ab728-206">如果你尝试初始化的数组超过可用内存量，则运行时将引发 <xref:System.OutOfMemoryException> 。</span><span class="sxs-lookup"><span data-stu-id="ab728-206">If you attempt to initialize an array that exceeds the amount of available memory, the runtime throws an <xref:System.OutOfMemoryException>.</span></span>|
|<span data-ttu-id="ab728-207">大小和元素大小</span><span class="sxs-lookup"><span data-stu-id="ab728-207">Size and Element Size</span></span>|<span data-ttu-id="ab728-208">数组的大小独立于其元素的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ab728-208">An array's size is independent of the data type of its elements.</span></span> <span data-ttu-id="ab728-209">大小始终表示元素总数，而不是在内存中使用的字节数。</span><span class="sxs-lookup"><span data-stu-id="ab728-209">The size always represents the total number of elements, not the number of bytes that they consume in memory.</span></span>|
|<span data-ttu-id="ab728-210">内存消耗</span><span class="sxs-lookup"><span data-stu-id="ab728-210">Memory Consumption</span></span>|<span data-ttu-id="ab728-211">做出关于数组如何存储在内存中的假设是不可靠的。</span><span class="sxs-lookup"><span data-stu-id="ab728-211">It is not safe to make any assumptions regarding how an array is stored in memory.</span></span> <span data-ttu-id="ab728-212">由于不同数据宽度的平台上的存储会有所变化，因此同一数组在 64 位系统上可以占用比在 32 位系统上更多的内存。</span><span class="sxs-lookup"><span data-stu-id="ab728-212">Storage varies on platforms of different data widths, so the same array can consume more memory on a 64-bit system than on a 32-bit system.</span></span> <span data-ttu-id="ab728-213">具体取决于数组初始化时的系统配置，公共语言运行时 (CLR) 可以尽可能地将存储分配到靠近包元素的地方，或者将它们全部在自然硬件边界上对齐。</span><span class="sxs-lookup"><span data-stu-id="ab728-213">Depending on system configuration when you initialize an array, the common language runtime (CLR) can assign storage either to pack elements as close together as possible, or to align them all on natural hardware boundaries.</span></span> <span data-ttu-id="ab728-214">此外，数组需要存储开销的控制信息，而且每添加一个维度，这种开销随之增加。</span><span class="sxs-lookup"><span data-stu-id="ab728-214">Also, an array requires a storage overhead for its control information, and this overhead increases with each added dimension.</span></span>|

## <a name="the-array-type"></a><span data-ttu-id="ab728-215">数组类型</span><span class="sxs-lookup"><span data-stu-id="ab728-215">The array type</span></span>

<span data-ttu-id="ab728-216">每个数组都具有一个数据类型，该数据类型不同于其元素的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ab728-216">Every array has a data type, which differs from the data type of its elements.</span></span> <span data-ttu-id="ab728-217">没有一种数据类型能用于所有数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-217">There is no single data type for all arrays.</span></span> <span data-ttu-id="ab728-218">相反，数组的数据类型由数组的维度数量或 *“排名”*，以及数组中元素的数据类型确定。</span><span class="sxs-lookup"><span data-stu-id="ab728-218">Instead, the data type of an array is determined by the number of dimensions, or *rank*, of the array, and the data type of the elements in the array.</span></span> <span data-ttu-id="ab728-219">只有当两个数组变量具有相同的秩并且它们的元素具有相同的数据类型时，它们才具有相同的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ab728-219">Two array variables are of the same data type only when they have the same rank and their elements have the same data type.</span></span> <span data-ttu-id="ab728-220">数组的维度长度不会影响数组数据类型。</span><span class="sxs-lookup"><span data-stu-id="ab728-220">The lengths of the dimensions of an array do not influence the array data type.</span></span>

<span data-ttu-id="ab728-221">每个数组都继承自 <xref:System.Array?displayProperty=nameWithType> 类，并且你可以声明一个类型为 `Array` 的变量，但不能创建一个类型为 `Array` 的数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-221">Every array inherits from the <xref:System.Array?displayProperty=nameWithType> class, and you can declare a variable to be of type `Array`, but you cannot create an array of type `Array`.</span></span> <span data-ttu-id="ab728-222">例如，虽然下面的代码将变量声明 `arr` 为类型 `Array` 并调用 <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> 方法来实例化数组，但数组的类型会证明是对象 []。</span><span class="sxs-lookup"><span data-stu-id="ab728-222">For example, although the following code declares the `arr` variable to be of type `Array` and calls the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method to instantiate the array, the array's type proves to be Object[].</span></span>

[!code-vb[array-class](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)]

<span data-ttu-id="ab728-223">此外，[ReDim 语句](../../../language-reference/statements/redim-statement.md)无法对声明为类型 `Array` 的变量执行运算。</span><span class="sxs-lookup"><span data-stu-id="ab728-223">Also, the [ReDim Statement](../../../language-reference/statements/redim-statement.md) cannot operate on a variable declared as type `Array`.</span></span> <span data-ttu-id="ab728-224">出于这些原因，以及对于类型安全，建议将每个数组声明为特定类型。</span><span class="sxs-lookup"><span data-stu-id="ab728-224">For these reasons, and for type safety, it is advisable to declare every array as a specific type.</span></span>

<span data-ttu-id="ab728-225">你可以通过几种方式了解到数组及其元素的数据类型。</span><span class="sxs-lookup"><span data-stu-id="ab728-225">You can find out the data type of either an array or its elements in several ways.</span></span>

- <span data-ttu-id="ab728-226">您可以对 <xref:System.Object.GetType%2A> 变量调用方法来获取 <xref:System.Type> 表示变量的运行时类型的对象。</span><span class="sxs-lookup"><span data-stu-id="ab728-226">You can call the <xref:System.Object.GetType%2A> method on the variable to get a <xref:System.Type> object that represents the run-time type of the variable.</span></span> <span data-ttu-id="ab728-227"><xref:System.Type> 对象可在其属性和方法中保存大量信息。</span><span class="sxs-lookup"><span data-stu-id="ab728-227">The <xref:System.Type> object holds extensive information in its properties and methods.</span></span>
- <span data-ttu-id="ab728-228">可以将变量传递给 <xref:Microsoft.VisualBasic.Information.TypeName%2A> 函数，以获取 `String` 具有运行时类型名称的。</span><span class="sxs-lookup"><span data-stu-id="ab728-228">You can pass the variable to the <xref:Microsoft.VisualBasic.Information.TypeName%2A> function to get a `String` with the name of run-time type.</span></span>

<span data-ttu-id="ab728-229">下面的示例调用 `GetType` 方法和 `TypeName` 函数来确定数组的类型。</span><span class="sxs-lookup"><span data-stu-id="ab728-229">The following example calls the both the `GetType` method and the `TypeName` function to determine the type of an array.</span></span> <span data-ttu-id="ab728-230">数组的类型为 `Byte(,)` 。</span><span class="sxs-lookup"><span data-stu-id="ab728-230">The array type is `Byte(,)`.</span></span> <span data-ttu-id="ab728-231">请注意， <xref:System.Type.BaseType%2A?displayProperty=nameWithType> 属性还指示字节数组的基类型是 <xref:System.Array> 类。</span><span class="sxs-lookup"><span data-stu-id="ab728-231">Note that the <xref:System.Type.BaseType%2A?displayProperty=nameWithType> property also indicates that the base type of the byte array is the <xref:System.Array> class.</span></span>

[!code-vb[array-type](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]

## <a name="arrays-as-return-values-and-parameters"></a><span data-ttu-id="ab728-232">作为返回值和参数的数组</span><span class="sxs-lookup"><span data-stu-id="ab728-232">Arrays as return values and parameters</span></span>

<span data-ttu-id="ab728-233">若要通过 `Function` 过程返回数组，请将数组数据类型和维度数指定为 [Function 语句](../../../language-reference/statements/function-statement.md)的返回类型。</span><span class="sxs-lookup"><span data-stu-id="ab728-233">To return an array from a `Function` procedure, specify the array data type and the number of dimensions as the return type of the [Function Statement](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="ab728-234">在函数内，声明一个具有相同数据类型和维度数的本地数组变量。</span><span class="sxs-lookup"><span data-stu-id="ab728-234">Within the function, declare a local array variable with same data type and number of dimensions.</span></span> <span data-ttu-id="ab728-235">在 [Return 语句](../../../language-reference/statements/return-statement.md)中，添加不带括号的局部数组变量。</span><span class="sxs-lookup"><span data-stu-id="ab728-235">In the [Return Statement](../../../language-reference/statements/return-statement.md), include the local array variable without parentheses.</span></span>

<span data-ttu-id="ab728-236">若要将作为参数的数组指定到 `Sub` 或 `Function` 步骤中，可将此参数定义为具有指定数据类型和维度数量的数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-236">To specify an array as a parameter to a `Sub` or `Function` procedure, define the parameter as an array with a specified data type and number of dimensions.</span></span> <span data-ttu-id="ab728-237">在对过程的调用中，传递具有相同数据类型和维度数量的数组变量。</span><span class="sxs-lookup"><span data-stu-id="ab728-237">In the call to the procedure, pass an array variable with the same data type and number of dimensions.</span></span>

<span data-ttu-id="ab728-238">在下面的示例中， `GetNumbers` 函数返回一个 `Integer()` 类型为的一维数组 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="ab728-238">In the following example, the `GetNumbers` function returns an `Integer()`, a one-dimensional array of type `Integer`.</span></span> <span data-ttu-id="ab728-239">`ShowNumbers` 过程接受 `Integer()` 参数。</span><span class="sxs-lookup"><span data-stu-id="ab728-239">The `ShowNumbers` procedure accepts an `Integer()` argument.</span></span>

[!code-vb[return-value-and-params](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]

<span data-ttu-id="ab728-240">在下面的示例中， `GetNumbersMultiDim` 函数返回一个 `Integer(,)` 类型为的二维数组 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="ab728-240">In the following example, the `GetNumbersMultiDim` function returns an `Integer(,)`, a two-dimensional array of type `Integer`.</span></span>  <span data-ttu-id="ab728-241">`ShowNumbersMultiDim` 过程接受 `Integer(,)` 参数。</span><span class="sxs-lookup"><span data-stu-id="ab728-241">The `ShowNumbersMultiDim` procedure accepts an `Integer(,)` argument.</span></span>

[!code-vb[multidimensional-return-value](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]

## <a name="jagged-arrays"></a><span data-ttu-id="ab728-242">交错数组</span><span class="sxs-lookup"><span data-stu-id="ab728-242">Jagged arrays</span></span>

<span data-ttu-id="ab728-243">有时应用程序中的数据结构是二维而不是矩形。</span><span class="sxs-lookup"><span data-stu-id="ab728-243">Sometimes the data structure in your application is two-dimensional but not rectangular.</span></span> <span data-ttu-id="ab728-244">例如，你可以使用一个数组来存储有关每个月中每一天的高温数据。</span><span class="sxs-lookup"><span data-stu-id="ab728-244">For example, you might use an array to store data about the high temperature of each day of the month.</span></span> <span data-ttu-id="ab728-245">数组的第一个维度表示月份，但第二个维度表示天数，月份中的天数不统一。</span><span class="sxs-lookup"><span data-stu-id="ab728-245">The first dimension of the array represents the month, but the second dimension represents the number of days, and the number of days in a month is not uniform.</span></span> <span data-ttu-id="ab728-246">*交错数组*（也称为*数组*）是为这种情况设计的。</span><span class="sxs-lookup"><span data-stu-id="ab728-246">A *jagged array*, which is also called an *array of arrays*, is designed for such scenarios.</span></span> <span data-ttu-id="ab728-247">交错数组是指其元素也是数组的数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-247">A jagged array is an array whose elements are also arrays.</span></span> <span data-ttu-id="ab728-248">交错数组和交错数组中的每个元素都可以具有一个或多个维度。</span><span class="sxs-lookup"><span data-stu-id="ab728-248">A jagged array and each element in a jagged array can have one or more dimensions.</span></span>

<span data-ttu-id="ab728-249">下面的示例使用月份数组，其中的每个元素是天数的数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-249">The following example uses an array of months, each element of which is an array of days.</span></span> <span data-ttu-id="ab728-250">该示例使用交错数组，因为不同的月份有不同的天数。</span><span class="sxs-lookup"><span data-stu-id="ab728-250">The example uses a jagged array because different months have different numbers of days.</span></span>  <span data-ttu-id="ab728-251">该示例演示如何创建交错数组，为其赋值，以及检索和显示其值。</span><span class="sxs-lookup"><span data-stu-id="ab728-251">The example shows how to create a jagged array, assign values to it, and retrieve and display its values.</span></span>

[!code-vb[jagged-arrays](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]

<span data-ttu-id="ab728-252">前面的示例使用循环将值逐个元素地分配给交错数组 `For...Next` 。</span><span class="sxs-lookup"><span data-stu-id="ab728-252">The previous example assigns values to the jagged array on an element-by-element basis by using a `For...Next` loop.</span></span> <span data-ttu-id="ab728-253">还可以使用嵌套的数组文本将值分配给交错数组的元素。</span><span class="sxs-lookup"><span data-stu-id="ab728-253">You can also assign values to the elements of a jagged array by using nested array literals.</span></span> <span data-ttu-id="ab728-254">不过，尝试使用嵌套的数组文本（例如 `Dim valuesjagged = {{1, 2}, {2, 3, 4}}` ）会生成编译器错误[BC30568](../../../misc/bc30568.md)。</span><span class="sxs-lookup"><span data-stu-id="ab728-254">However, the attempt to use nested array literals (for example, `Dim valuesjagged = {{1, 2}, {2, 3, 4}}`) generates compiler error [BC30568](../../../misc/bc30568.md).</span></span> <span data-ttu-id="ab728-255">若要更正此错误，请将内部数组文本括在括号中。</span><span class="sxs-lookup"><span data-stu-id="ab728-255">To correct the error, enclose the inner array literals in parentheses.</span></span> <span data-ttu-id="ab728-256">括号强制计算数组文本表达式，并将生成的值用于外部数组文本，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="ab728-256">The parentheses force the array literal expression to be evaluated, and the resulting values are used with the outer array literal, as the following example shows.</span></span>

[!code-vb[jagged-array-initialization](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)]

<span data-ttu-id="ab728-257">交错数组是其元素包含数组的一维数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-257">A jagged array is a one-dimensional array whose elements contain arrays.</span></span> <span data-ttu-id="ab728-258">因此， <xref:System.Array.Length%2A?displayProperty=nameWithType> 属性和方法将 `Array.GetLength(0)` 返回一维数组中的元素数，并 `Array.GetLength(1)` 引发， <xref:System.IndexOutOfRangeException> 因为交错数组不是多维的。</span><span class="sxs-lookup"><span data-stu-id="ab728-258">Therefore, the <xref:System.Array.Length%2A?displayProperty=nameWithType> property and the `Array.GetLength(0)` method return the number of elements in the one-dimensional array, and `Array.GetLength(1)` throws an <xref:System.IndexOutOfRangeException> because a jagged array is not multidimensional.</span></span> <span data-ttu-id="ab728-259">通过检索每个子数组的属性的值，可以确定每个子数组中的元素数 <xref:System.Array.Length%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ab728-259">You determine the number of elements in each subarray by retrieving the value of each subarray's <xref:System.Array.Length%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="ab728-260">下面的示例演示如何确定交错数组中的元素数。</span><span class="sxs-lookup"><span data-stu-id="ab728-260">The following example illustrates how to determine the number of elements in a jagged array.</span></span>

[!code-vb[jagged-array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)]

## <a name="zero-length-arrays"></a><span data-ttu-id="ab728-261">长度为零的数组</span><span class="sxs-lookup"><span data-stu-id="ab728-261">Zero-length arrays</span></span>

<span data-ttu-id="ab728-262">Visual Basic 区分未初始化的数组（值为的数组 `Nothing` ）和*零长度数组*或空数组（没有元素的数组）。未初始化的数组是指尚未对其进行尺寸或分配任何值的数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-262">Visual Basic differentiates between a uninitialized array (an array whose value is `Nothing`) and a *zero-length array* or empty array (an array that has no elements.) An uninitialized array is one that has not been dimensioned or had any values assigned to it.</span></span> <span data-ttu-id="ab728-263">例如：</span><span class="sxs-lookup"><span data-stu-id="ab728-263">For example:</span></span>

```vb
Dim arr() As String
```

<span data-ttu-id="ab728-264">使用维度-1 声明长度为零的数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-264">A zero-length array is declared with a dimension of -1.</span></span> <span data-ttu-id="ab728-265">例如：</span><span class="sxs-lookup"><span data-stu-id="ab728-265">For example:</span></span>

```vb
Dim arrZ(-1) As String
```

<span data-ttu-id="ab728-266">在下列情况下，你可能需要创建一个零长度数组：</span><span class="sxs-lookup"><span data-stu-id="ab728-266">You might need to create a zero-length array under the following circumstances:</span></span>

- <span data-ttu-id="ab728-267">如果不冒 <xref:System.NullReferenceException> 异常，你的代码必须访问类的成员（ <xref:System.Array> 如 <xref:System.Array.Length%2A> 或 <xref:System.Array.Rank%2A> ），或调用 Visual Basic 函数（如） <xref:Microsoft.VisualBasic.Information.UBound%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ab728-267">Without risking a <xref:System.NullReferenceException> exception, your code must access members of the <xref:System.Array> class, such as <xref:System.Array.Length%2A> or <xref:System.Array.Rank%2A>, or call a Visual Basic function such as <xref:Microsoft.VisualBasic.Information.UBound%2A>.</span></span>

- <span data-ttu-id="ab728-268">您希望通过无需将作为特殊情况进行检查来简化您的代码 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="ab728-268">You want to keep your code simple by not having to check for `Nothing` as a special case.</span></span>

- <span data-ttu-id="ab728-269">你的代码与应用程序编程接口 (API) 交互，该接口要求你将一个零长度数组传递到一个或多个过程，或将一个零长度数组返回到一个或多个过程。</span><span class="sxs-lookup"><span data-stu-id="ab728-269">Your code interacts with an application programming interface (API) that either requires you to pass a zero-length array to one or more procedures or returns a zero-length array from one or more procedures.</span></span>

## <a name="splitting-an-array"></a><span data-ttu-id="ab728-270">拆分数组</span><span class="sxs-lookup"><span data-stu-id="ab728-270">Splitting an array</span></span>

<span data-ttu-id="ab728-271">在某些情况下，可能需要将单个数组拆分为多个数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-271">In some cases, you may need to split a single array into multiple arrays.</span></span> <span data-ttu-id="ab728-272">这涉及到识别要拆分数组的点，然后将该数组 spitting 为两个或多个单独的数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-272">This involves identifying the point or points at which the array is to be split, and then spitting the array into two or more separate arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="ab728-273">本部分不讨论根据某些分隔符将单个字符串拆分为字符串数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-273">This section does not discuss splitting a single string into a string array based on some delimiter.</span></span> <span data-ttu-id="ab728-274">有关拆分字符串的信息，请参阅 <xref:System.String.Split%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="ab728-274">For information on splitting a string, see the <xref:System.String.Split%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="ab728-275">拆分数组最常见的条件是：</span><span class="sxs-lookup"><span data-stu-id="ab728-275">The most common criteria for splitting an array are:</span></span>

- <span data-ttu-id="ab728-276">数组中的元素数。</span><span class="sxs-lookup"><span data-stu-id="ab728-276">The number of elements in the array.</span></span> <span data-ttu-id="ab728-277">例如，你可能想要将多个指定数量的元素的数组拆分为一些大致相等的部分。</span><span class="sxs-lookup"><span data-stu-id="ab728-277">For example, you might want to split an array of more than a specified number of elements into a number of approximately equal parts.</span></span> <span data-ttu-id="ab728-278">为此，可以使用或方法返回的值 <xref:System.Array.Length%2A?displayProperty=nameWithType> <xref:System.Array.GetLength%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ab728-278">For this purpose, you can use the value returned by either the <xref:System.Array.Length%2A?displayProperty=nameWithType> or <xref:System.Array.GetLength%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="ab728-279">元素的值，它用作指示应拆分数组的位置的分隔符。</span><span class="sxs-lookup"><span data-stu-id="ab728-279">The value of an element, which serves as a delimiter that indicates where the array should be split.</span></span> <span data-ttu-id="ab728-280">可以通过调用和方法搜索特定值 <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ab728-280">You can search for a specific value by calling the <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> and <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> methods.</span></span>

<span data-ttu-id="ab728-281">确定了应拆分数组的索引后，可以通过调用方法来创建各个数组 <xref:System.Array.Copy%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ab728-281">Once you've determined the index or indexes at which the array should be split, you can then create the individual arrays by calling the <xref:System.Array.Copy%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="ab728-282">下面的示例将一个数组拆分为大小大致相等的两个数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-282">The following example splits an array into two arrays of approximately equal size.</span></span> <span data-ttu-id="ab728-283">（如果数组元素的总数为奇数，则第一个数组的元素数比第二个多。）</span><span class="sxs-lookup"><span data-stu-id="ab728-283">(If the total number of array elements is odd, the first array has one more element than the second.)</span></span>

[!code-vb[splitting-an-array-by-length](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)]

<span data-ttu-id="ab728-284">下面的示例基于是否存在值为 "zzz" 的元素，将字符串数组拆分为两个数组，该元素充当数组分隔符。</span><span class="sxs-lookup"><span data-stu-id="ab728-284">The following example splits a string array into two arrays based on the presence of an element whose value is "zzz", which serves as the array delimiter.</span></span> <span data-ttu-id="ab728-285">新数组不包括包含分隔符的元素。</span><span class="sxs-lookup"><span data-stu-id="ab728-285">The new arrays do not include the element that contains the delimiter.</span></span>

[!code-vb[splitting-an-array-by-delimiter](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)]

## <a name="joining-arrays"></a><span data-ttu-id="ab728-286">联接数组</span><span class="sxs-lookup"><span data-stu-id="ab728-286">Joining arrays</span></span>

<span data-ttu-id="ab728-287">还可以将多个数组合并成一个更大的数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-287">You can also combine a number of arrays into a single larger array.</span></span> <span data-ttu-id="ab728-288">为此，您还可以使用 <xref:System.Array.Copy%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="ab728-288">To do this, you also use the <xref:System.Array.Copy%2A?displayProperty=nameWithType> method.</span></span>

> [!NOTE]
> <span data-ttu-id="ab728-289">本部分不讨论如何将字符串数组联接成单个字符串。</span><span class="sxs-lookup"><span data-stu-id="ab728-289">This section does not discuss joining a string array into a single string.</span></span> <span data-ttu-id="ab728-290">有关联接字符串数组的信息，请参见 <xref:System.String.Join%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="ab728-290">For information on joining a string array, see the <xref:System.String.Join%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="ab728-291">在将每个数组的元素复制到新数组中之前，必须先确保已初始化数组，使其足以容纳新的数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-291">Before copying the elements of each array into the new array, you must first ensure that you have initialized the array so that it is large enough to accommodate the new array.</span></span> <span data-ttu-id="ab728-292">可以通过两种方法执行此操作：</span><span class="sxs-lookup"><span data-stu-id="ab728-292">You can do this in one of two ways:</span></span>

- <span data-ttu-id="ab728-293">在 [`ReDim Preserve`](../../../language-reference/statements/redim-statement.md) 将新元素添加到数组之前，请使用语句动态展开数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-293">Use the [`ReDim Preserve`](../../../language-reference/statements/redim-statement.md) statement to dynamically expand the array before adding new elements to it.</span></span> <span data-ttu-id="ab728-294">这是最简单的方法，但它可能会导致性能下降，并在复制大型数组时消耗过多的内存。</span><span class="sxs-lookup"><span data-stu-id="ab728-294">This is the easiest technique, but it can result in performance degradation and excessive memory consumption when you are copying large arrays.</span></span>
- <span data-ttu-id="ab728-295">计算新的大型数组所需的元素总数，然后将每个源数组的元素添加到其中。</span><span class="sxs-lookup"><span data-stu-id="ab728-295">Calculate the total number of elements needed for the new large array, then add the elements of each source array to it.</span></span>

<span data-ttu-id="ab728-296">下面的示例使用第二种方法将四个数组分别添加到一个数组中。</span><span class="sxs-lookup"><span data-stu-id="ab728-296">The following example uses the second approach to add four arrays with ten elements each to a single array.</span></span>

[!code-vb[joining-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)]

<span data-ttu-id="ab728-297">由于在这种情况下，源数组都是小的，因此我们还可以在将每个新数组的元素添加到数组时，动态扩展数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-297">Since in this case the source arrays are all small, we can also dynamically expand the array as we add the elements of each new array to it.</span></span> <span data-ttu-id="ab728-298">以下示例执行该操作。</span><span class="sxs-lookup"><span data-stu-id="ab728-298">The following example does that.</span></span>

[!code-vb[joining-an-array-dynamically](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)]

## <a name="collections-as-an-alternative-to-arrays"></a><span data-ttu-id="ab728-299">作为数组的替代方法的集合</span><span class="sxs-lookup"><span data-stu-id="ab728-299">Collections as an alternative to arrays</span></span>

<span data-ttu-id="ab728-300">数组最适用于创建和使用固定数量的强类型化对象。</span><span class="sxs-lookup"><span data-stu-id="ab728-300">Arrays are most useful for creating and working with a fixed number of strongly typed objects.</span></span> <span data-ttu-id="ab728-301">集合提供更灵活的方式来使用对象组。</span><span class="sxs-lookup"><span data-stu-id="ab728-301">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="ab728-302">与数组不同，数组要求使用[ `ReDim` 语句](../../../language-reference/statements/redim-statement.md)显式更改数组的大小，集合随着应用程序更改的需要动态地增长和收缩。</span><span class="sxs-lookup"><span data-stu-id="ab728-302">Unlike arrays, which require that you explicitly change the size of an array with the [`ReDim` Statement](../../../language-reference/statements/redim-statement.md), collections grow and shrink dynamically as the needs of an application change.</span></span>

<span data-ttu-id="ab728-303">使用 `ReDim` 对数组进行重维数时，Visual Basic 会创建一个新数组，并释放以前的数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-303">When you use `ReDim` to redimension an array, Visual Basic creates a new array and releases the previous one.</span></span> <span data-ttu-id="ab728-304">这需要执行时间。</span><span class="sxs-lookup"><span data-stu-id="ab728-304">This takes execution time.</span></span> <span data-ttu-id="ab728-305">因此，如果你正在使用的项目数量频繁变化，或者你无法预测所需的最大项目数，则通常可以使用集合获得更好的性能。</span><span class="sxs-lookup"><span data-stu-id="ab728-305">Therefore, if the number of items you are working with changes frequently, or you cannot predict the maximum number of items you need, you'll usually obtain better performance by using a collection.</span></span>

<span data-ttu-id="ab728-306">对于某些集合，你可以为放入集合中的任何对象分配一个密钥，这样你便可以使用该密钥快速检索此对象。</span><span class="sxs-lookup"><span data-stu-id="ab728-306">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>

<span data-ttu-id="ab728-307">如果集合中只包含一种数据类型的元素，则可以使用 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空间中的一个类。</span><span class="sxs-lookup"><span data-stu-id="ab728-307">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="ab728-308">泛型集合强制类型安全，因此无法向其添加任何其他数据类型。</span><span class="sxs-lookup"><span data-stu-id="ab728-308">A generic collection enforces type safety so that no other data type can be added to it.</span></span>

<span data-ttu-id="ab728-309">有关集合的详细信息，请参阅[集合](../../concepts/collections.md)。</span><span class="sxs-lookup"><span data-stu-id="ab728-309">For more information about collections, see [Collections](../../concepts/collections.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="ab728-310">相关主题</span><span class="sxs-lookup"><span data-stu-id="ab728-310">Related topics</span></span>

|<span data-ttu-id="ab728-311">术语</span><span class="sxs-lookup"><span data-stu-id="ab728-311">Term</span></span>|<span data-ttu-id="ab728-312">定义</span><span class="sxs-lookup"><span data-stu-id="ab728-312">Definition</span></span>|
|----------|----------------|
|[<span data-ttu-id="ab728-313">Array Dimensions in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab728-313">Array Dimensions in Visual Basic</span></span>](array-dimensions.md)|<span data-ttu-id="ab728-314">在数组中解释级别和维度。</span><span class="sxs-lookup"><span data-stu-id="ab728-314">Explains rank and dimensions in arrays.</span></span>|
|[<span data-ttu-id="ab728-315">如何：在 Visual Basic 中初始化数组变量</span><span class="sxs-lookup"><span data-stu-id="ab728-315">How to: Initialize an Array Variable in Visual Basic</span></span>](how-to-initialize-an-array-variable.md)|<span data-ttu-id="ab728-316">说明如何用初始值填充数组。</span><span class="sxs-lookup"><span data-stu-id="ab728-316">Describes how to populate arrays with initial values.</span></span>|
|[<span data-ttu-id="ab728-317">如何：在 Visual Basic 中对数组进行排序</span><span class="sxs-lookup"><span data-stu-id="ab728-317">How to: Sort An Array in Visual Basic</span></span>](how-to-sort-an-array.md)|<span data-ttu-id="ab728-318">显示如何按字母先后顺序对数组元素进行排序。</span><span class="sxs-lookup"><span data-stu-id="ab728-318">Shows how to sort the elements of an array alphabetically.</span></span>|
|[<span data-ttu-id="ab728-319">如何：将一个数组赋给另一个数组</span><span class="sxs-lookup"><span data-stu-id="ab728-319">How to: Assign One Array to Another Array</span></span>](how-to-assign-one-array-to-another-array.md)|<span data-ttu-id="ab728-320">说明将数组分配到另一个数组变量的规则和步骤。</span><span class="sxs-lookup"><span data-stu-id="ab728-320">Describes the rules and steps for assigning an array to another array variable.</span></span>|
|[<span data-ttu-id="ab728-321">数组疑难解答</span><span class="sxs-lookup"><span data-stu-id="ab728-321">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)|<span data-ttu-id="ab728-322">讨论在使用数组时出现的一些常见问题。</span><span class="sxs-lookup"><span data-stu-id="ab728-322">Discusses some common problems that arise when working with arrays.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ab728-323">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab728-323">See also</span></span>

- <xref:System.Array?displayProperty=nameWithType>
- [<span data-ttu-id="ab728-324">Dim 语句</span><span class="sxs-lookup"><span data-stu-id="ab728-324">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="ab728-325">ReDim 语句</span><span class="sxs-lookup"><span data-stu-id="ab728-325">ReDim Statement</span></span>](../../../language-reference/statements/redim-statement.md)
