---
title: 表达式树 (C#)
description: 了解表达式树。 了解如何编译和运行这些数据结构表示的代码，其中每个代码都是一个表达式。
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
ms.openlocfilehash: 2fa8577dd945650edebf84459de10c0c3bd04225
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105580"
---
# <a name="expression-trees-c"></a><span data-ttu-id="8f189-104">表达式树 (C#)</span><span class="sxs-lookup"><span data-stu-id="8f189-104">Expression Trees (C#)</span></span>
<span data-ttu-id="8f189-105">表达式树以树形数据结构表示代码，其中每一个节点都是一种表达式，比如方法调用和 `x < y` 这样的二元运算等。</span><span class="sxs-lookup"><span data-stu-id="8f189-105">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="8f189-106">你可以对表达式树中的代码进行编辑和运算。</span><span class="sxs-lookup"><span data-stu-id="8f189-106">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="8f189-107">这样能够动态修改可执行代码、在不同数据库中执行 LINQ 查询以及创建动态查询。</span><span class="sxs-lookup"><span data-stu-id="8f189-107">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="8f189-108">有关 LINQ 中表达式树的详细信息，请参阅[如何使用表达式树生成动态查询 (C#)](./how-to-use-expression-trees-to-build-dynamic-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="8f189-108">For more information about expression trees in LINQ, see [How to use expression trees to build dynamic queries (C#)](./how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>
  
 <span data-ttu-id="8f189-109">表达式树还能用于动态语言运行时 (DLR) 以提供动态语言和 .NET 之间的互操作性，同时保证编译器编写员能够发射表达式树而非 Microsoft 中间语言 (MSIL)。</span><span class="sxs-lookup"><span data-stu-id="8f189-109">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and .NET and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="8f189-110">有关 DLR 的详细信息，请参阅[动态语言运行时概述](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="8f189-110">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="8f189-111">你可以基于匿名 lambda 表达式通过 C# 或者 Visual Basic 编译器创建表达式树，或者通过 <xref:System.Linq.Expressions> 名称空间手动创建。</span><span class="sxs-lookup"><span data-stu-id="8f189-111">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="8f189-112">根据 Lambda 表达式创建表达式树</span><span class="sxs-lookup"><span data-stu-id="8f189-112">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="8f189-113">若 lambda 表达式被分配给 <xref:System.Linq.Expressions.Expression%601> 类型的变量，则编译器可以发射代码以创建表示该 lambda 表达式的表达式树。</span><span class="sxs-lookup"><span data-stu-id="8f189-113">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="8f189-114">C# 编译器只能从表达式 Lambda（或单行 Lambda）生成表达式树。</span><span class="sxs-lookup"><span data-stu-id="8f189-114">The C# compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="8f189-115">它无法解析语句 lambda （或多行 lambda）。</span><span class="sxs-lookup"><span data-stu-id="8f189-115">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="8f189-116">有关 C# 中 Lambda 表达式的详细信息，请参阅 [Lambda 表达式](../../statements-expressions-operators/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="8f189-116">For more information about lambda expressions in C#, see [Lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="8f189-117">下列代码示例展示如何通过 C# 编译器创建表示 Lambda 表达式 `num => num < 5` 的表达式树。</span><span class="sxs-lookup"><span data-stu-id="8f189-117">The following code examples demonstrate how to have the C# compiler create an expression tree that represents the lambda expression `num => num < 5`.</span></span>  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="8f189-118">通过 API 创建表达式树</span><span class="sxs-lookup"><span data-stu-id="8f189-118">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="8f189-119">通过 API 创建表达式树需要使用 <xref:System.Linq.Expressions.Expression> 类。</span><span class="sxs-lookup"><span data-stu-id="8f189-119">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="8f189-120">类包含创建特定类型表达式树节点的静态工厂方法，比如表示参数变量的 <xref:System.Linq.Expressions.ParameterExpression>，或者是表示方法调用的 <xref:System.Linq.Expressions.MethodCallExpression>。</span><span class="sxs-lookup"><span data-stu-id="8f189-120">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="8f189-121"><xref:System.Linq.Expressions.ParameterExpression> 名称空间还解释了 <xref:System.Linq.Expressions.MethodCallExpression>、<xref:System.Linq.Expressions>和另一种具体表达式类型。</span><span class="sxs-lookup"><span data-stu-id="8f189-121"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="8f189-122">这些类型来源于抽象类型 <xref:System.Linq.Expressions.Expression>。</span><span class="sxs-lookup"><span data-stu-id="8f189-122">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="8f189-123">下列代码示例展示如何使用 API 创建表示 Lambda 表达式 `num => num < 5` 的表达式树。</span><span class="sxs-lookup"><span data-stu-id="8f189-123">The following code example demonstrates how to create an expression tree that represents the lambda expression `num => num < 5` by using the API.</span></span>  
  
```csharp  
// Add the following using directive to your code file:  
// using System.Linq.Expressions;  
  
// Manually build the expression tree for
// the lambda expression num => num < 5.  
ParameterExpression numParam = Expression.Parameter(typeof(int), "num");  
ConstantExpression five = Expression.Constant(5, typeof(int));  
BinaryExpression numLessThanFive = Expression.LessThan(numParam, five);  
Expression<Func<int, bool>> lambda1 =  
    Expression.Lambda<Func<int, bool>>(  
        numLessThanFive,  
        new ParameterExpression[] { numParam });  
```  
  
 <span data-ttu-id="8f189-124">在 .NET Framework 4 或更高版本中，表达式树 API 还支持赋值表达式和控制流表达式，例如循环、条件块和 `try-catch` 块等。</span><span class="sxs-lookup"><span data-stu-id="8f189-124">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="8f189-125">相对于通过 C# 编译器和 Lambda 表达式创建表达式树，还可利用 API 创建更加复杂的表达式树。</span><span class="sxs-lookup"><span data-stu-id="8f189-125">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the C# compiler.</span></span> <span data-ttu-id="8f189-126">下列示例展示如何创建计算数字阶乘的表达式树。</span><span class="sxs-lookup"><span data-stu-id="8f189-126">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
```csharp  
// Creating a parameter expression.  
ParameterExpression value = Expression.Parameter(typeof(int), "value");  
  
// Creating an expression to hold a local variable.
ParameterExpression result = Expression.Parameter(typeof(int), "result");  
  
// Creating a label to jump to from a loop.  
LabelTarget label = Expression.Label(typeof(int));  
  
// Creating a method body.  
BlockExpression block = Expression.Block(  
    // Adding a local variable.  
    new[] { result },  
    // Assigning a constant to a local variable: result = 1  
    Expression.Assign(result, Expression.Constant(1)),  
    // Adding a loop.  
        Expression.Loop(  
    // Adding a conditional block into the loop.  
           Expression.IfThenElse(  
    // Condition: value > 1  
               Expression.GreaterThan(value, Expression.Constant(1)),  
    // If true: result *= value --  
               Expression.MultiplyAssign(result,  
                   Expression.PostDecrementAssign(value)),  
    // If false, exit the loop and go to the label.  
               Expression.Break(label, result)  
           ),  
    // Label to jump to.  
       label  
    )  
);  
  
// Compile and execute an expression tree.  
int factorial = Expression.Lambda<Func<int, int>>(block, value).Compile()(5);  
  
Console.WriteLine(factorial);  
// Prints 120.  
```

<span data-ttu-id="8f189-127">有关详细信息，请参阅[在 Visual Studio 2010 中使用表达式树生成动态方法](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/)，该方法也适用于 Visual Studio 的更高版本。</span><span class="sxs-lookup"><span data-stu-id="8f189-127">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="8f189-128">解析表达式树</span><span class="sxs-lookup"><span data-stu-id="8f189-128">Parsing Expression Trees</span></span>  
 <span data-ttu-id="8f189-129">下列代码示例展示如何分解表示 Lambda 表达式 `num => num < 5` 的表达式树。</span><span class="sxs-lookup"><span data-stu-id="8f189-129">The following code example demonstrates how the expression tree that represents the lambda expression `num => num < 5` can be decomposed into its parts.</span></span>  
  
```csharp  
// Add the following using directive to your code file:  
// using System.Linq.Expressions;  
  
// Create an expression tree.  
Expression<Func<int, bool>> exprTree = num => num < 5;  
  
// Decompose the expression tree.  
ParameterExpression param = (ParameterExpression)exprTree.Parameters[0];  
BinaryExpression operation = (BinaryExpression)exprTree.Body;  
ParameterExpression left = (ParameterExpression)operation.Left;  
ConstantExpression right = (ConstantExpression)operation.Right;  
  
Console.WriteLine("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value);  
  
// This code produces the following output:  
  
// Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="8f189-130">表达式树永久性</span><span class="sxs-lookup"><span data-stu-id="8f189-130">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="8f189-131">表达式树应具有永久性。</span><span class="sxs-lookup"><span data-stu-id="8f189-131">Expression trees should be immutable.</span></span> <span data-ttu-id="8f189-132">这意味着如果你想修改某个表达式树，则必须复制该表达式树然后替换其中的节点来创建一个新的表达式树。</span><span class="sxs-lookup"><span data-stu-id="8f189-132">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="8f189-133">你可以使用表达式树访问者遍历现有表达式树。</span><span class="sxs-lookup"><span data-stu-id="8f189-133">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="8f189-134">有关详细信息，请参阅[如何修改表达式树 (C#)](./how-to-modify-expression-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="8f189-134">For more information, see [How to modify expression trees (C#)](./how-to-modify-expression-trees.md).</span></span>
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="8f189-135">编译表达式树</span><span class="sxs-lookup"><span data-stu-id="8f189-135">Compiling Expression Trees</span></span>  
 <span data-ttu-id="8f189-136"><xref:System.Linq.Expressions.Expression%601> 类型提供了 <xref:System.Linq.Expressions.Expression%601.Compile%2A> 方法以将表达式树表示的代码编译成可执行委托。</span><span class="sxs-lookup"><span data-stu-id="8f189-136">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="8f189-137">下列代码示例展示如何编译表达式树并运行结果代码。</span><span class="sxs-lookup"><span data-stu-id="8f189-137">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
```csharp  
// Creating an expression tree.  
Expression<Func<int, bool>> expr = num => num < 5;  
  
// Compiling the expression tree into a delegate.  
Func<int, bool> result = expr.Compile();  
  
// Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4));  
  
// Prints True.  
  
// You can also use simplified syntax  
// to compile and run an expression tree.  
// The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4));  
  
// Also prints True.  
```  
  
 <span data-ttu-id="8f189-138">有关详细信息，请参阅[如何执行表达式树 (C#)](./how-to-execute-expression-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="8f189-138">For more information, see [How to execute expression trees (C#)](./how-to-execute-expression-trees.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8f189-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="8f189-139">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="8f189-140">如何执行表达式树 (C#)</span><span class="sxs-lookup"><span data-stu-id="8f189-140">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="8f189-141">如何修改表达式树 (C#)</span><span class="sxs-lookup"><span data-stu-id="8f189-141">How to modify expression trees (C#)</span></span>](./how-to-modify-expression-trees.md)
- [<span data-ttu-id="8f189-142">Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="8f189-142">Lambda Expressions</span></span>](../../statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="8f189-143">动态语言运行时概述</span><span class="sxs-lookup"><span data-stu-id="8f189-143">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="8f189-144">编程概念 (C#)</span><span class="sxs-lookup"><span data-stu-id="8f189-144">Programming Concepts (C#)</span></span>](../index.md)
