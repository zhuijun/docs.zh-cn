---
title: 隐式类型本地变量 - C# 编程指南
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 842f73b7af9671157495df961f5db22702ae897e
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240702"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="de784-102">隐式类型本地变量（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="de784-102">Implicitly typed local variables (C# Programming Guide)</span></span>

<span data-ttu-id="de784-103">可声明局部变量而无需提供显式类型。</span><span class="sxs-lookup"><span data-stu-id="de784-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="de784-104">`var` 关键字指示编译器通过初始化语句右侧的表达式推断变量的类型。</span><span class="sxs-lookup"><span data-stu-id="de784-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="de784-105">推断类型可以是内置类型、匿名类型、用户定义类型或 .NET 类库中定义的类型。</span><span class="sxs-lookup"><span data-stu-id="de784-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET class library.</span></span> <span data-ttu-id="de784-106">有关如何使用 `var` 初始化数组的详细信息，请参阅[隐式类型化数组](../arrays/implicitly-typed-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="de784-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>

<span data-ttu-id="de784-107">以下示例演示使用 `var` 声明局部变量的各种方式：</span><span class="sxs-lookup"><span data-stu-id="de784-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

<span data-ttu-id="de784-108">重要的是了解 `var` 关键字并不意味着“变体”，并且并不指示变量是松散类型或是后期绑定。</span><span class="sxs-lookup"><span data-stu-id="de784-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="de784-109">它只表示由编译器确定并分配最适合的类型。</span><span class="sxs-lookup"><span data-stu-id="de784-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>

<span data-ttu-id="de784-110">在以下上下文中，可使用 `var` 关键字：</span><span class="sxs-lookup"><span data-stu-id="de784-110">The `var` keyword may be used in the following contexts:</span></span>

- <span data-ttu-id="de784-111">在局部变量（在方法范围内声明的变量）上，如前面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="de784-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>

- <span data-ttu-id="de784-112">在 [for](../../language-reference/keywords/for.md) 初始化语句中。</span><span class="sxs-lookup"><span data-stu-id="de784-112">In a [for](../../language-reference/keywords/for.md) initialization statement.</span></span>

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- <span data-ttu-id="de784-113">在 [foreach](../../language-reference/keywords/foreach-in.md) 初始化语句中。</span><span class="sxs-lookup"><span data-stu-id="de784-113">In a [foreach](../../language-reference/keywords/foreach-in.md) initialization statement.</span></span>

    ```csharp
    foreach (var item in list) {...}
    ```

- <span data-ttu-id="de784-114">在 [using](../../language-reference/keywords/using-statement.md) 域间中。</span><span class="sxs-lookup"><span data-stu-id="de784-114">In a [using](../../language-reference/keywords/using-statement.md) statement.</span></span>

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

<span data-ttu-id="de784-115">有关详细信息，请参阅[如何在查询表达式中使用隐式类型化局部变量和数组](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="de784-115">For more information, see [How to use implicitly typed local variables and arrays in a query expression](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>

## <a name="var-and-anonymous-types"></a><span data-ttu-id="de784-116">var 和匿名类型</span><span class="sxs-lookup"><span data-stu-id="de784-116">var and anonymous types</span></span>

<span data-ttu-id="de784-117">在许多情况下，使用 `var` 是可选的，只是一种语法便利。</span><span class="sxs-lookup"><span data-stu-id="de784-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="de784-118">但是，在使用匿名类型初始化变量时，如果需要在以后访问对象的属性，则必须将变量声明为 `var`。</span><span class="sxs-lookup"><span data-stu-id="de784-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="de784-119">这是 LINQ 查询表达式中的常见方案。</span><span class="sxs-lookup"><span data-stu-id="de784-119">This is a common scenario in LINQ query expressions.</span></span> <span data-ttu-id="de784-120">有关详细信息，请参阅[匿名类型](anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="de784-120">For more information, see [Anonymous Types](anonymous-types.md).</span></span>

<span data-ttu-id="de784-121">从源代码角度来看，匿名类型没有名称。</span><span class="sxs-lookup"><span data-stu-id="de784-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="de784-122">因此，如果使用 `var` 初始化了查询变量，则访问返回对象序列中的属性的唯一方法是在 `foreach` 语句中将 `var` 用作迭代变量的类型。</span><span class="sxs-lookup"><span data-stu-id="de784-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a><span data-ttu-id="de784-123">备注</span><span class="sxs-lookup"><span data-stu-id="de784-123">Remarks</span></span>

<span data-ttu-id="de784-124">以下限制适用于隐式类型化变量声明：</span><span class="sxs-lookup"><span data-stu-id="de784-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>

- <span data-ttu-id="de784-125">仅当局部变量在相同语句中进行声明和初始化时，才能使用 `var`；变量不能初始化为 null，也不能初始化为方法组或匿名函数。</span><span class="sxs-lookup"><span data-stu-id="de784-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>

- <span data-ttu-id="de784-126">`var` 不能在类范围内对字段使用。</span><span class="sxs-lookup"><span data-stu-id="de784-126">`var` cannot be used on fields at class scope.</span></span>

- <span data-ttu-id="de784-127">使用 `var` 声明的变量不能在初始化表达式中使用。</span><span class="sxs-lookup"><span data-stu-id="de784-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="de784-128">换句话说，此表达式是合法的：`int i = (i = 20);`，但是此表达式会生成编译时错误：`var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="de784-128">In other words, this expression is legal: `int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>

- <span data-ttu-id="de784-129">不能在相同语句中初始化多个隐式类型化变量。</span><span class="sxs-lookup"><span data-stu-id="de784-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>

- <span data-ttu-id="de784-130">如果一种名为 `var` 的类型处于范围内，则 `var` 关键字会解析为该类型名称，不会被视为隐式类型化局部变量声明的一部分。</span><span class="sxs-lookup"><span data-stu-id="de784-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>

<span data-ttu-id="de784-131">带 `var` 关键字的隐式类型只能应用于本地方法范围内的变量。</span><span class="sxs-lookup"><span data-stu-id="de784-131">Implicit typing with the `var` keyword can only be applied to variables at local method scope.</span></span> <span data-ttu-id="de784-132">隐式类型不可用于类字段，因为 C# 编译器在处理代码时会遇到逻辑悖论：编译器需要知道字段的类型，但它在分析赋值表达式前无法确定类型，而表达式在不知道类型的情况下无法进行计算。</span><span class="sxs-lookup"><span data-stu-id="de784-132">Implicit typing is not available for class fields as the C# compiler would encounter a logical paradox as it processed the code: the compiler needs to know the type of the field, but it cannot determine the type until the assignment expression is analyzed, and the expression cannot be evaluated without knowing the type.</span></span> <span data-ttu-id="de784-133">考虑下列代码：</span><span class="sxs-lookup"><span data-stu-id="de784-133">Consider the following code:</span></span>

```csharp
private var bookTitles;
```

<span data-ttu-id="de784-134">`bookTitles` 是类型为 `var` 的类字段。</span><span class="sxs-lookup"><span data-stu-id="de784-134">`bookTitles` is a class field given the type `var`.</span></span> <span data-ttu-id="de784-135">由于该字段没有要计算的表达式，编译器无法推断出 `bookTitles` 应该是哪种类型。</span><span class="sxs-lookup"><span data-stu-id="de784-135">As the field has no expression to evaluate, it is impossible for the compiler to infer what type `bookTitles` is supposed to be.</span></span> <span data-ttu-id="de784-136">此外，向该字段添加表达式（就像对本地变量执行的操作一样）也是不够的：</span><span class="sxs-lookup"><span data-stu-id="de784-136">In addition, adding an expression to the field (like you would for a local variable) is also insufficient:</span></span>

```csharp
private var bookTitles = new List<string>();
```

<span data-ttu-id="de784-137">当编译器在代码编译期间遇到字段时，它会在处理与其关联的任何表达式之前记录每个字段的类型。</span><span class="sxs-lookup"><span data-stu-id="de784-137">When the compiler encounters fields during code compilation, it records each field's type before processing any expressions associated with it.</span></span> <span data-ttu-id="de784-138">编译器在尝试分析 `bookTitles` 时遇到相同的悖论：它需要知道字段的类型，但编译器通常会通过分析表达式来确定 `var` 的类型，这在事先不知道类型的情况下无法实现。</span><span class="sxs-lookup"><span data-stu-id="de784-138">The compiler encounters the same paradox trying to parse `bookTitles`: it needs to know the type of the field, but the compiler would normally determine `var`'s type by analyzing the expression, which isn't possible without knowing the type beforehand.</span></span>

<span data-ttu-id="de784-139">你可能会发现，对于在其中难以确定查询变量的确切构造类型的查询表达式，`var` 也可能会十分有用。</span><span class="sxs-lookup"><span data-stu-id="de784-139">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="de784-140">这可能会针对分组和排序操作发生。</span><span class="sxs-lookup"><span data-stu-id="de784-140">This can occur with grouping and ordering operations.</span></span>

<span data-ttu-id="de784-141">当变量的特定类型在键盘上键入时很繁琐、或是显而易见、或是不会提高代码的可读性时，`var` 关键字也可能非常有用。</span><span class="sxs-lookup"><span data-stu-id="de784-141">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="de784-142">`var` 采用此方法提供帮助的一个示例是针对嵌套泛型类型（如用于分组操作的类型）。</span><span class="sxs-lookup"><span data-stu-id="de784-142">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="de784-143">在下面的查询中，查询变量的类型是 `IEnumerable<IGrouping<string, Student>>`。</span><span class="sxs-lookup"><span data-stu-id="de784-143">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="de784-144">只要你和必须维护你的代码的其他人了解这一点，使用隐式类型化实现便利性和简便性时便不会出现问题。</span><span class="sxs-lookup"><span data-stu-id="de784-144">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

<span data-ttu-id="de784-145">使用 `var` 有助于简化代码，但是它的使用应该限制在需要使用它的情况下，或在它可使代码更易于读取的情况下。</span><span class="sxs-lookup"><span data-stu-id="de784-145">The use of `var` helps simplify your code, but its use should be restricted to cases where it is required, or when it makes your code easier to read.</span></span> <span data-ttu-id="de784-146">有关何时正确使用 `var` 的详细信息，请参阅 C# 编码指南一文中的[隐式类型本地变量](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables)节。</span><span class="sxs-lookup"><span data-stu-id="de784-146">For more information about when to use `var` properly, see the [Implicitly typed local variables](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) section on the C# Coding Guidelines article.</span></span>

## <a name="see-also"></a><span data-ttu-id="de784-147">请参阅</span><span class="sxs-lookup"><span data-stu-id="de784-147">See also</span></span>

- [<span data-ttu-id="de784-148">C# 参考</span><span class="sxs-lookup"><span data-stu-id="de784-148">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="de784-149">隐式类型化数组</span><span class="sxs-lookup"><span data-stu-id="de784-149">Implicitly Typed Arrays</span></span>](../arrays/implicitly-typed-arrays.md)
- [<span data-ttu-id="de784-150">如何在查询表达式中使用隐式类型化局部变量和数组</span><span class="sxs-lookup"><span data-stu-id="de784-150">How to use implicitly typed local variables and arrays in a query expression</span></span>](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [<span data-ttu-id="de784-151">匿名类型</span><span class="sxs-lookup"><span data-stu-id="de784-151">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="de784-152">对象和集合初始值设定项</span><span class="sxs-lookup"><span data-stu-id="de784-152">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
- [<span data-ttu-id="de784-153">var</span><span class="sxs-lookup"><span data-stu-id="de784-153">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="de784-154">C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="de784-154">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="de784-155">LINQ（语言集成查询）</span><span class="sxs-lookup"><span data-stu-id="de784-155">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="de784-156">for</span><span class="sxs-lookup"><span data-stu-id="de784-156">for</span></span>](../../language-reference/keywords/for.md)
- [<span data-ttu-id="de784-157">foreach, in</span><span class="sxs-lookup"><span data-stu-id="de784-157">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="de784-158">using 语句</span><span class="sxs-lookup"><span data-stu-id="de784-158">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
