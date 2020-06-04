---
title: 表达式树
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: 5d30b2e2e66aa322e6d43b5fbf4a4baf3435b2a6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410962"
---
# <a name="expression-trees-visual-basic"></a><span data-ttu-id="9a6d4-102">表达式树 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a6d4-102">Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="9a6d4-103">表达式树以树形数据结构表示代码，其中每一个节点都是一种表达式，比如方法调用和 `x < y` 这样的二元运算等。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="9a6d4-104">你可以对表达式树中的代码进行编辑和运算。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="9a6d4-105">这样能够动态修改可执行代码、在不同数据库中执行 LINQ 查询以及创建动态查询。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="9a6d4-106">有关 LINQ 中表达式树的详细信息，请参阅[如何：使用表达式树生成动态查询 (Visual Basic)](how-to-use-expression-trees-to-build-dynamic-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)](how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="9a6d4-107">表达式树还能用于动态语言运行时 (DLR) 以提供动态语言和 .NET Framework 之间的互操作性，同时保证编译器编写员能够发射表达式树而非 Microsoft 中间语言 (MSIL)。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="9a6d4-108">有关 DLR 的详细信息，请参阅[动态语言运行时概述](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="9a6d4-109">你可以基于匿名 lambda 表达式通过 C# 或者 Visual Basic 编译器创建表达式树，或者通过 <xref:System.Linq.Expressions> 名称空间手动创建。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="9a6d4-110">根据 Lambda 表达式创建表达式树</span><span class="sxs-lookup"><span data-stu-id="9a6d4-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="9a6d4-111">若 lambda 表达式被分配给 <xref:System.Linq.Expressions.Expression%601> 类型的变量，则编译器可以发射代码以创建表示该 lambda 表达式的表达式树。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="9a6d4-112">Visual Basic 编译器只能从表达式 Lambda（或单行 Lambda）生成表达式树。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-112">The Visual Basic compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="9a6d4-113">它无法解析语句 lambda （或多行 lambda）。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="9a6d4-114">有关 Visual Basic 中 Lambda 表达式的详细信息，请参阅 [Lambda 表达式](../../language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-114">For more information about lambda expressions in Visual Basic, see [Lambda Expressions](../../language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="9a6d4-115">下列代码示例展示如何通过 Visual Basic 编译器创建表示 Lambda 表达式 `Function(num) num < 5` 的表达式树。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-115">The following code examples demonstrate how to have the Visual Basic compiler create an expression tree that represents the lambda expression `Function(num) num < 5`.</span></span>  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="9a6d4-116">通过 API 创建表达式树</span><span class="sxs-lookup"><span data-stu-id="9a6d4-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="9a6d4-117">通过 API 创建表达式树需要使用 <xref:System.Linq.Expressions.Expression> 类。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="9a6d4-118">类包含创建特定类型表达式树节点的静态工厂方法，比如表示参数变量的 <xref:System.Linq.Expressions.ParameterExpression>，或者是表示方法调用的 <xref:System.Linq.Expressions.MethodCallExpression>。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="9a6d4-119"><xref:System.Linq.Expressions.ParameterExpression> 名称空间还解释了 <xref:System.Linq.Expressions.MethodCallExpression>、<xref:System.Linq.Expressions>和另一种具体表达式类型。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="9a6d4-120">这些类型来源于抽象类型 <xref:System.Linq.Expressions.Expression>。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="9a6d4-121">下列代码示例展示如何使用 API 创建表示 Lambda 表达式 `Function(num) num < 5` 的表达式树。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `Function(num) num < 5` by using the API.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Manually build the expression tree for the lambda expression num => num < 5.  
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")  
Dim five As ConstantExpression = Expression.Constant(5, GetType(Integer))  
Dim numLessThanFive As BinaryExpression = Expression.LessThan(numParam, five)  
Dim lambda1 As Expression(Of Func(Of Integer, Boolean)) =  
  Expression.Lambda(Of Func(Of Integer, Boolean))(  
        numLessThanFive,  
        New ParameterExpression() {numParam})  
```  
  
 <span data-ttu-id="9a6d4-122">在 .NET Framework 4 或更高版本中，表达式树 API 还支持赋值表达式和控制流表达式，例如循环、条件块和 `try-catch` 块等。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="9a6d4-123">相对于通过 Visual Basic 编译器和 Lambda 表达式创建表达式树，还可利用 API 创建更加复杂的表达式树。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the Visual Basic compiler.</span></span> <span data-ttu-id="9a6d4-124">下列示例展示如何创建计算数字阶乘的表达式树。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
```vb  
' Creating a parameter expression.  
Dim value As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "value")  
  
' Creating an expression to hold a local variable.
Dim result As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "result")  
  
' Creating a label to jump to from a loop.  
Dim label As LabelTarget = Expression.Label(GetType(Integer))  
  
' Creating a method body.  
Dim block As BlockExpression = Expression.Block(  
    New ParameterExpression() {result},  
    Expression.Assign(result, Expression.Constant(1)),  
    Expression.Loop(  
        Expression.IfThenElse(  
            Expression.GreaterThan(value, Expression.Constant(1)),  
            Expression.MultiplyAssign(result,  
                Expression.PostDecrementAssign(value)),  
            Expression.Break(label, result)  
        ),  
        label  
    )  
)  
  
' Compile an expression tree and return a delegate.  
Dim factorial As Integer =  
    Expression.Lambda(Of Func(Of Integer, Integer))(block, value).Compile()(5)  
  
Console.WriteLine(factorial)  
' Prints 120.  
```

<span data-ttu-id="9a6d4-125">有关详细信息，请参阅[在 Visual Studio 2010 中使用表达式树生成动态方法](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/)，该方法也适用于 Visual Studio 的更高版本。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="9a6d4-126">解析表达式树</span><span class="sxs-lookup"><span data-stu-id="9a6d4-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="9a6d4-127">下列代码示例展示如何分解表示 Lambda 表达式 `Function(num) num < 5` 的表达式树。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-127">The following code example demonstrates how the expression tree that represents the lambda expression `Function(num) num < 5` can be decomposed into its parts.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Create an expression tree.  
Dim exprTree As Expression(Of Func(Of Integer, Boolean)) = Function(num) num < 5  
  
' Decompose the expression tree.  
Dim param As ParameterExpression = exprTree.Parameters(0)  
Dim operation As BinaryExpression = exprTree.Body  
Dim left As ParameterExpression = operation.Left  
Dim right As ConstantExpression = operation.Right  
  
Console.WriteLine(String.Format("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value))  
  
' This code produces the following output:  
'  
' Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="9a6d4-128">表达式树永久性</span><span class="sxs-lookup"><span data-stu-id="9a6d4-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="9a6d4-129">表达式树应具有永久性。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-129">Expression trees should be immutable.</span></span> <span data-ttu-id="9a6d4-130">这意味着如果你想修改某个表达式树，则必须复制该表达式树然后替换其中的节点来创建一个新的表达式树。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="9a6d4-131">你可以使用表达式树访问者遍历现有表达式树。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="9a6d4-132">有关详细信息，请参阅[如何：修改表达式树 (Visual Basic)](how-to-modify-expression-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-132">For more information, see [How to: Modify Expression Trees (Visual Basic)](how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="9a6d4-133">编译表达式树</span><span class="sxs-lookup"><span data-stu-id="9a6d4-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="9a6d4-134"><xref:System.Linq.Expressions.Expression%601> 类型提供了 <xref:System.Linq.Expressions.Expression%601.Compile%2A> 方法以将表达式树表示的代码编译成可执行委托。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="9a6d4-135">下列代码示例展示如何编译表达式树并运行结果代码。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
```vb  
' Creating an expression tree.  
Dim expr As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
  
' Compiling the expression tree into a delegate.  
Dim result As Func(Of Integer, Boolean) = expr.Compile()  
  
' Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4))  
  
' Prints True.  
  
' You can also use simplified syntax  
' to compile and run an expression tree.  
' The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4))  
  
' Also prints True.  
```  
  
 <span data-ttu-id="9a6d4-136">有关详细信息，请参阅[如何：执行表达式树 (Visual Basic)](how-to-execute-expression-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="9a6d4-136">For more information, see [How to: Execute Expression Trees (Visual Basic)](how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a6d4-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9a6d4-137">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="9a6d4-138">如何：执行表达式树 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a6d4-138">How to: Execute Expression Trees (Visual Basic)</span></span>](how-to-execute-expression-trees.md)
- [<span data-ttu-id="9a6d4-139">如何：修改表达式树 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a6d4-139">How to: Modify Expression Trees (Visual Basic)</span></span>](how-to-modify-expression-trees.md)
- [<span data-ttu-id="9a6d4-140">Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="9a6d4-140">Lambda Expressions</span></span>](../../language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="9a6d4-141">动态语言运行时概述</span><span class="sxs-lookup"><span data-stu-id="9a6d4-141">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="9a6d4-142">编程概念（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="9a6d4-142">Programming Concepts (Visual Basic)</span></span>](../index.md)
