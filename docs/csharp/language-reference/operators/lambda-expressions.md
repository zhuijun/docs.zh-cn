---
title: Lambda 表达式 - C# 引用
description: 了解 Lambda 表达式。 存在表达式作为其主体的表达式 Lambda，或语句块作为其主体的语句 Lambda。
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 3dd793ec000999935bff6b54b1b00e49211bd5ec
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558356"
---
# <a name="lambda-expressions-c-reference"></a><span data-ttu-id="11789-104">Lambda 表达式（C# 引用）</span><span class="sxs-lookup"><span data-stu-id="11789-104">Lambda expressions (C# reference)</span></span>

<span data-ttu-id="11789-105">“Lambda 表达式”是采用以下任意一种形式的表达式：</span><span class="sxs-lookup"><span data-stu-id="11789-105">A *lambda expression* is an expression of any of the following two forms:</span></span>

- <span data-ttu-id="11789-106">[表达式 lambda](#expression-lambdas)，表达式为其主体：</span><span class="sxs-lookup"><span data-stu-id="11789-106">[Expression lambda](#expression-lambdas) that has an expression as its body:</span></span>

  ```csharp
  (input-parameters) => expression
  ```

- <span data-ttu-id="11789-107">[语句 lambda](#statement-lambdas)，语句块作为其主体：</span><span class="sxs-lookup"><span data-stu-id="11789-107">[Statement lambda](#statement-lambdas) that has a statement block as its body:</span></span>

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

<span data-ttu-id="11789-108">使用 [lambda 声明运算符`=>`](lambda-operator.md) 从其主体中分离 lambda 参数列表。</span><span class="sxs-lookup"><span data-stu-id="11789-108">Use the [lambda declaration operator `=>`](lambda-operator.md) to separate the lambda's parameter list from its body.</span></span> <span data-ttu-id="11789-109">若要创建 Lambda 表达式，需要在 Lambda 运算符左侧指定输入参数（如果有），然后在另一侧输入表达式或语句块。</span><span class="sxs-lookup"><span data-stu-id="11789-109">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator and an expression or a statement block on the other side.</span></span>

<span data-ttu-id="11789-110">任何 Lambda 表达式都可以转换为[委托](../builtin-types/reference-types.md#the-delegate-type)类型。</span><span class="sxs-lookup"><span data-stu-id="11789-110">Any lambda expression can be converted to a [delegate](../builtin-types/reference-types.md#the-delegate-type) type.</span></span> <span data-ttu-id="11789-111">Lambda 表达式可以转换的委托类型由其参数和返回值的类型定义。</span><span class="sxs-lookup"><span data-stu-id="11789-111">The delegate type to which a lambda expression can be converted is defined by the types of its parameters and return value.</span></span> <span data-ttu-id="11789-112">如果 lambda 表达式不返回值，则可以将其转换为 `Action` 委托类型之一；否则，可将其转换为 `Func` 委托类型之一。</span><span class="sxs-lookup"><span data-stu-id="11789-112">If a lambda expression doesn't return a value, it can be converted to one of the `Action` delegate types; otherwise, it can be converted to one of the `Func` delegate types.</span></span> <span data-ttu-id="11789-113">例如，有 2 个参数且不返回值的 Lambda 表达式可转换为 <xref:System.Action%602> 委托。</span><span class="sxs-lookup"><span data-stu-id="11789-113">For example, a lambda expression that has two parameters and returns no value can be converted to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="11789-114">有 1 个参数且不返回值的 Lambda 表达式可转换为 <xref:System.Func%602> 委托。</span><span class="sxs-lookup"><span data-stu-id="11789-114">A lambda expression that has one parameter and returns a value can be converted to a <xref:System.Func%602> delegate.</span></span> <span data-ttu-id="11789-115">以下示例中，lambda 表达式 `x => x * x`（指定名为 `x` 的参数并返回 `x` 平方值）将分配给委托类型的变量：</span><span class="sxs-lookup"><span data-stu-id="11789-115">In the following example, the lambda expression `x => x * x`, which specifies a parameter that's named `x` and returns the value of `x` squared, is assigned to a variable of a delegate type:</span></span>

[!code-csharp-interactive[lambda is delegate](snippets/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="11789-116">表达式 lambda 还可以转换为[表达式树](../../programming-guide/concepts/expression-trees/index.md)类型，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="11789-116">Expression lambdas can also be converted to the [expression tree](../../programming-guide/concepts/expression-trees/index.md) types, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is expression tree](snippets/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="11789-117">可在需要委托类型或表达式树的实例的任何代码中使用 lambda 表达式，例如，作为 <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> 方法的参数传递应在后台执行的代码。</span><span class="sxs-lookup"><span data-stu-id="11789-117">You can use lambda expressions in any code that requires instances of delegate types or expression trees, for example as an argument to the <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> method to pass the code that should be executed in the background.</span></span> <span data-ttu-id="11789-118">用 C# 编写 [LINQ](../../linq/index.md) 时，还可以使用 lambda 表达式，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="11789-118">You can also use lambda expressions when you write [LINQ in C#](../../linq/index.md), as the following example shows:</span></span>

[!code-csharp-interactive[lambda is argument in LINQ](snippets/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="11789-119">如果使用基于方法的语法在 <xref:System.Linq.Enumerable?displayProperty=nameWithType> 类中（例如，在 LINQ to Objects 和 LINQ to XML 中）调用 <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> 方法，则参数为委托类型 <xref:System.Func%602?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="11789-119">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class, for example in LINQ to Objects and LINQ to XML, the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="11789-120">如果在 <xref:System.Linq.Queryable?displayProperty=nameWithType> 类中（例如，在 LINQ to SQL 中）调用 <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> 方法，则参数类型为表达式树类型 [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>)。</span><span class="sxs-lookup"><span data-stu-id="11789-120">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class, for example in LINQ to SQL, the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="11789-121">在这两种情况下，都可以使用相同的 lambda 表达式来指定参数值。</span><span class="sxs-lookup"><span data-stu-id="11789-121">In both cases you can use the same lambda expression to specify the parameter value.</span></span> <span data-ttu-id="11789-122">尽管通过 Lambda 创建的对象实际具有不同的类型，但其使得 2 个 `Select` 调用看起来类似。</span><span class="sxs-lookup"><span data-stu-id="11789-122">That makes the two `Select` calls to look similar although in fact the type of objects created from the lambdas is different.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="11789-123">表达式 lambda</span><span class="sxs-lookup"><span data-stu-id="11789-123">Expression lambdas</span></span>

<span data-ttu-id="11789-124">表达式位于 `=>` 运算符右侧的 lambda 表达式称为“表达式 lambda”。</span><span class="sxs-lookup"><span data-stu-id="11789-124">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="11789-125">表达式 lambda 广泛用于[表达式树](../../programming-guide/concepts/expression-trees/index.md)的构造。</span><span class="sxs-lookup"><span data-stu-id="11789-125">Expression lambdas are used extensively in the construction of [expression trees](../../programming-guide/concepts/expression-trees/index.md).</span></span> <span data-ttu-id="11789-126">表达式 lambda 会返回表达式的结果，并采用以下基本形式：</span><span class="sxs-lookup"><span data-stu-id="11789-126">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="11789-127">仅当 lambda 只有一个输入参数时，括号才是可选的；否则括号是必需的。</span><span class="sxs-lookup"><span data-stu-id="11789-127">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span>

<span data-ttu-id="11789-128">使用空括号指定零个输入参数：</span><span class="sxs-lookup"><span data-stu-id="11789-128">Specify zero input parameters with empty parentheses:</span></span>  

[!code-csharp[zero parameters](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

<span data-ttu-id="11789-129">括号内的两个或更多输入参数使用逗号加以分隔：</span><span class="sxs-lookup"><span data-stu-id="11789-129">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[two parameters](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

<span data-ttu-id="11789-130">有时，编译器无法推断输入类型。</span><span class="sxs-lookup"><span data-stu-id="11789-130">Sometimes it's impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="11789-131">可以显式指定类型，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="11789-131">You can specify the types explicitly as shown in the following example:</span></span>

[!code-csharp[explicitly typed parameters](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

<span data-ttu-id="11789-132">输入参数类型必须全部为显式或全部为隐式；否则，便会生成 [CS0748](../../misc/cs0748.md) 编译器错误。</span><span class="sxs-lookup"><span data-stu-id="11789-132">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="11789-133">表达式 lambda 的主体可以包含方法调用。</span><span class="sxs-lookup"><span data-stu-id="11789-133">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="11789-134">不过，若要创建在 .NET 公共语言运行时的上下文之外（如在 SQL Server 中）计算的表达式树，不得在 lambda 表达式中使用方法调用。</span><span class="sxs-lookup"><span data-stu-id="11789-134">However, if you are creating expression trees that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="11789-135">在 .NET 公共语言运行时上下文之外，方法将没有任何意义。</span><span class="sxs-lookup"><span data-stu-id="11789-135">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="11789-136">语句 lambda</span><span class="sxs-lookup"><span data-stu-id="11789-136">Statement lambdas</span></span>

<span data-ttu-id="11789-137">语句 lambda 与表达式 lambda 表达式类似，只是语句括在大括号中：</span><span class="sxs-lookup"><span data-stu-id="11789-137">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

<span data-ttu-id="11789-138">语句 lambda 的主体可以包含任意数量的语句；但是，实际上通常不会多于两个或三个。</span><span class="sxs-lookup"><span data-stu-id="11789-138">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp-interactive[statement lambda](snippets/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

<span data-ttu-id="11789-139">语句 lambda 也不能用于创建表达式目录树。</span><span class="sxs-lookup"><span data-stu-id="11789-139">Statement lambdas cannot be used to create expression trees.</span></span>
  
## <a name="async-lambdas"></a><span data-ttu-id="11789-140">异步 lambda</span><span class="sxs-lookup"><span data-stu-id="11789-140">Async lambdas</span></span>

<span data-ttu-id="11789-141">通过使用 [async](../keywords/async.md) 和 [await](await.md) 关键字，你可以轻松创建包含异步处理的 lambda 表达式和语句。</span><span class="sxs-lookup"><span data-stu-id="11789-141">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../keywords/async.md) and [await](await.md) keywords.</span></span> <span data-ttu-id="11789-142">例如，下面的 Windows 窗体示例包含一个调用和等待异步方法 `ExampleMethodAsync`的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="11789-142">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += button1_Click;
    }

    private async void button1_Click(object sender, EventArgs e)
    {
        await ExampleMethodAsync();
        textBox1.Text += "\r\nControl returned to Click event handler.\n";
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

<span data-ttu-id="11789-143">你可以使用异步 lambda 添加同一事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="11789-143">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="11789-144">若要添加此处理程序，请在 lambda 参数列表前添加 `async` 修饰符，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="11789-144">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += async (sender, e) =>
        {
            await ExampleMethodAsync();
            textBox1.Text += "\r\nControl returned to Click event handler.\n";
        };
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

<span data-ttu-id="11789-145">有关如何创建和使用异步方法的详细信息，请参阅[使用 Async 和 Await 的异步编程](../../programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="11789-145">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="11789-146">lambda 表达式和元组</span><span class="sxs-lookup"><span data-stu-id="11789-146">Lambda expressions and tuples</span></span>

<span data-ttu-id="11789-147">自 C# 7.0 起，C# 语言提供对[元组](../builtin-types/value-tuples.md)的内置支持。</span><span class="sxs-lookup"><span data-stu-id="11789-147">Starting with C# 7.0, the C# language provides built-in support for [tuples](../builtin-types/value-tuples.md).</span></span> <span data-ttu-id="11789-148">可以提供一个元组作为 Lambda 表达式的参数，同时 Lambda 表达式也可以返回元组。</span><span class="sxs-lookup"><span data-stu-id="11789-148">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="11789-149">在某些情况下，C# 编译器使用类型推理来确定元组组件的类型。</span><span class="sxs-lookup"><span data-stu-id="11789-149">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="11789-150">可通过用括号括住用逗号分隔的组件列表来定义元组。</span><span class="sxs-lookup"><span data-stu-id="11789-150">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="11789-151">下面的示例使用包含三个组件的元组，将一系列数字传递给 lambda 表达式，此表达式将每个值翻倍，然后返回包含乘法运算结果的元组（内含三个组件）。</span><span class="sxs-lookup"><span data-stu-id="11789-151">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](snippets/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="11789-152">通常，元组字段命名为 `Item1`、`Item2` 等等。但是，可以使用命名组件定义元组，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="11789-152">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](snippets/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="11789-153">若要详细了解 C# 元组，请参阅[元组类型](../../language-reference/builtin-types/value-tuples.md)。</span><span class="sxs-lookup"><span data-stu-id="11789-153">For more information about C# tuples, see [Tuple types](../../language-reference/builtin-types/value-tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="11789-154">含标准查询运算符的 lambda</span><span class="sxs-lookup"><span data-stu-id="11789-154">Lambdas with the standard query operators</span></span>

<span data-ttu-id="11789-155">在其他实现中，LINQ to Objects 有一个输入参数，其类型是泛型委托 <xref:System.Func%601> 系列中的一种。</span><span class="sxs-lookup"><span data-stu-id="11789-155">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="11789-156">这些委托使用类型参数来定义输入参数的数量和类型，以及委托的返回类型。</span><span class="sxs-lookup"><span data-stu-id="11789-156">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="11789-157">`Func` 委托对于封装用户定义的表达式非常有用，这些表达式将应用于一组源数据中的每个元素。</span><span class="sxs-lookup"><span data-stu-id="11789-157">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="11789-158">例如，假设为 <xref:System.Func%602> 委托类型：</span><span class="sxs-lookup"><span data-stu-id="11789-158">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="11789-159">可以将委托实例化为 `Func<int, bool>` 实例，其中 `int` 是输入参数，`bool` 是返回值。</span><span class="sxs-lookup"><span data-stu-id="11789-159">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="11789-160">返回值始终在最后一个类型参数中指定。</span><span class="sxs-lookup"><span data-stu-id="11789-160">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="11789-161">例如，`Func<int, string, bool>` 定义包含两个输入参数（`int` 和 `string`）且返回类型为 `bool`的委托。</span><span class="sxs-lookup"><span data-stu-id="11789-161">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="11789-162">下面的 `Func` 委托在调用后返回布尔值，以指明输入参数是否等于 5：</span><span class="sxs-lookup"><span data-stu-id="11789-162">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="11789-163">参数类型为 <xref:System.Linq.Expressions.Expression%601> 时，也可以提供 Lambda 表达式，例如在 <xref:System.Linq.Queryable> 类型内定义的标准查询运算符中提供。</span><span class="sxs-lookup"><span data-stu-id="11789-163">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="11789-164">指定 <xref:System.Linq.Expressions.Expression%601> 参数时，lambda 编译为表达式树。</span><span class="sxs-lookup"><span data-stu-id="11789-164">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="11789-165">下面的示例使用 <xref:System.Linq.Enumerable.Count%2A> 标准查询运算符：</span><span class="sxs-lookup"><span data-stu-id="11789-165">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="11789-166">编译器可以推断输入参数的类型，或者你也可以显式指定该类型。</span><span class="sxs-lookup"><span data-stu-id="11789-166">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="11789-167">这个特殊 lambda 表达式将计算那些除以 2 时余数为 1 的整数的数量 (`n`)。</span><span class="sxs-lookup"><span data-stu-id="11789-167">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="11789-168">下面的示例生成一个序列，其中包含 `numbers` 数组中位于 9 之前的所有元素，因为这是序列中第一个不符合条件的数字：</span><span class="sxs-lookup"><span data-stu-id="11789-168">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="11789-169">以下示例通过将输入参数括在括号中来指定多个输入参数。</span><span class="sxs-lookup"><span data-stu-id="11789-169">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="11789-170">此方法返回 `numbers` 数组中的所有元素，直至遇到值小于其在数组中的序号位置的数字为止：</span><span class="sxs-lookup"><span data-stu-id="11789-170">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](snippets/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="11789-171">Lambda 表达式中的类型推理</span><span class="sxs-lookup"><span data-stu-id="11789-171">Type inference in lambda expressions</span></span>

<span data-ttu-id="11789-172">编写 lambda 时，通常不必为输入参数指定类型，因为编译器可以根据 lambda 主体、参数类型以及 C# 语言规范中描述的其他因素来推断类型。</span><span class="sxs-lookup"><span data-stu-id="11789-172">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="11789-173">对于大多数标准查询运算符，第一个输入是源序列中的元素类型。</span><span class="sxs-lookup"><span data-stu-id="11789-173">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="11789-174">如果要查询 `IEnumerable<Customer>`，则输入变量将被推断为 `Customer` 对象，这意味着你可以访问其方法和属性：</span><span class="sxs-lookup"><span data-stu-id="11789-174">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="11789-175">lambda 类型推理的一般规则如下：</span><span class="sxs-lookup"><span data-stu-id="11789-175">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="11789-176">Lambda 包含的参数数量必须与委托类型包含的参数数量相同。</span><span class="sxs-lookup"><span data-stu-id="11789-176">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="11789-177">Lambda 中的每个输入参数必须都能够隐式转换为其对应的委托参数。</span><span class="sxs-lookup"><span data-stu-id="11789-177">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="11789-178">Lambda 的返回值（如果有）必须能够隐式转换为委托的返回类型。</span><span class="sxs-lookup"><span data-stu-id="11789-178">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="11789-179">请注意，lambda 表达式本身没有类型，因为通用类型系统没有“lambda 表达式”这一固有概念。</span><span class="sxs-lookup"><span data-stu-id="11789-179">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="11789-180">不过，有时以一种非正式的方式谈论 lambda 表达式的“类型”会很方便。</span><span class="sxs-lookup"><span data-stu-id="11789-180">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="11789-181">在这些情况下，类型是指委托类型或 lambda 表达式所转换到的 <xref:System.Linq.Expressions.Expression> 类型。</span><span class="sxs-lookup"><span data-stu-id="11789-181">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a><span data-ttu-id="11789-182">捕获 lambda 表达式中的外部变量和变量范围</span><span class="sxs-lookup"><span data-stu-id="11789-182">Capture of outer variables and variable scope in lambda expressions</span></span>

<span data-ttu-id="11789-183">lambda 可以引用外部变量。</span><span class="sxs-lookup"><span data-stu-id="11789-183">Lambdas can refer to *outer variables*.</span></span> <span data-ttu-id="11789-184">这些变量是在定义 lambda 表达式的方法中或包含 lambda 表达式的类型中的范围内变量。</span><span class="sxs-lookup"><span data-stu-id="11789-184">These are the variables that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="11789-185">以这种方式捕获的变量将进行存储以备在 lambda 表达式中使用，即使在其他情况下，这些变量将超出范围并进行垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="11789-185">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="11789-186">必须明确地分配外部变量，然后才能在 lambda 表达式中使用该变量。</span><span class="sxs-lookup"><span data-stu-id="11789-186">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="11789-187">下面的示例演示这些规则：</span><span class="sxs-lookup"><span data-stu-id="11789-187">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](snippets/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="11789-188">下列规则适用于 lambda 表达式中的变量范围：</span><span class="sxs-lookup"><span data-stu-id="11789-188">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="11789-189">捕获的变量将不会被作为垃圾回收，直至引用变量的委托符合垃圾回收的条件。</span><span class="sxs-lookup"><span data-stu-id="11789-189">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="11789-190">在封闭方法中看不到 lambda 表达式内引入的变量。</span><span class="sxs-lookup"><span data-stu-id="11789-190">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="11789-191">lambda 表达式无法从封闭方法中直接捕获 [in](../keywords/in-parameter-modifier.md)、[ref](../keywords/ref.md) 或 [out](../keywords/out-parameter-modifier.md) 参数。</span><span class="sxs-lookup"><span data-stu-id="11789-191">A lambda expression cannot directly capture an [in](../keywords/in-parameter-modifier.md), [ref](../keywords/ref.md), or [out](../keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="11789-192">lambda 表达式中的 [return](../keywords/return.md) 语句不会导致封闭方法返回。</span><span class="sxs-lookup"><span data-stu-id="11789-192">A [return](../keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="11789-193">如果相应跳转语句的目标位于 lambda 表达式块之外，lambda 表达式不得包含 [goto](../keywords/goto.md)、[break](../keywords/break.md) 或 [continue](../keywords/continue.md) 语句。</span><span class="sxs-lookup"><span data-stu-id="11789-193">A lambda expression cannot contain a [goto](../keywords/goto.md), [break](../keywords/break.md), or [continue](../keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="11789-194">同样，如果目标在块内部，在 lambda 表达式块外部使用跳转语句也是错误的。</span><span class="sxs-lookup"><span data-stu-id="11789-194">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="11789-195">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="11789-195">C# language specification</span></span>

<span data-ttu-id="11789-196">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的 [匿名函数表达式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)部分。</span><span class="sxs-lookup"><span data-stu-id="11789-196">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="featured-book-chapter"></a><span data-ttu-id="11789-197">特别推荐书籍章节</span><span class="sxs-lookup"><span data-stu-id="11789-197">Featured book chapter</span></span>

<span data-ttu-id="11789-198">[C# 3.0 手册（第三版）：面向 C# 3.0 程序员的超过 250 个解决方案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)中的[委托、事件和 Lambda 表达式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="11789-198">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11789-199">请参阅</span><span class="sxs-lookup"><span data-stu-id="11789-199">See also</span></span>

- [<span data-ttu-id="11789-200">C# 参考</span><span class="sxs-lookup"><span data-stu-id="11789-200">C# reference</span></span>](../index.md)
- [<span data-ttu-id="11789-201">C# 运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="11789-201">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="11789-202">LINQ（语言集成查询）</span><span class="sxs-lookup"><span data-stu-id="11789-202">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="11789-203">表达式树</span><span class="sxs-lookup"><span data-stu-id="11789-203">Expression Trees</span></span>](../../programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="11789-204">本地函数与 Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="11789-204">Local functions vs. lambda expressions</span></span>](../../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)
- [<span data-ttu-id="11789-205">Visual Studio 2008 C# 示例（请参阅 LINQ 示例查询文件和 XQuery 程序）</span><span class="sxs-lookup"><span data-stu-id="11789-205">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
