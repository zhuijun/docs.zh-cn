---
title: Lambda 表达式
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: 54a9c0cf275a67c77748c32771c3c5dcbdb916d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406698"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="89111-102">Lambda 表达式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89111-102">Lambda Expressions (Visual Basic)</span></span>

<span data-ttu-id="89111-103">*Lambda 表达式*是没有名称的函数或子例程，只要委托有效，就可以使用该函数。</span><span class="sxs-lookup"><span data-stu-id="89111-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="89111-104">Lambda 表达式可以是函数或子例程，可以是单行或多行。</span><span class="sxs-lookup"><span data-stu-id="89111-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="89111-105">可以将值从当前作用域传递到 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="89111-105">You can pass values from the current scope to a lambda expression.</span></span>

> [!NOTE]
> <span data-ttu-id="89111-106">`RemoveHandler`语句是一个异常。</span><span class="sxs-lookup"><span data-stu-id="89111-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="89111-107">不能为的委托参数传递中的 lambda 表达式 `RemoveHandler` 。</span><span class="sxs-lookup"><span data-stu-id="89111-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>

<span data-ttu-id="89111-108">您可以使用或关键字创建 lambda `Function` 表达式 `Sub` ，就像创建标准函数或子例程一样。</span><span class="sxs-lookup"><span data-stu-id="89111-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="89111-109">但是，lambda 表达式包含在语句中。</span><span class="sxs-lookup"><span data-stu-id="89111-109">However, lambda expressions are included in a statement.</span></span>

<span data-ttu-id="89111-110">下面的示例是一个 lambda 表达式，它递增其参数并返回值。</span><span class="sxs-lookup"><span data-stu-id="89111-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="89111-111">该示例显示函数的单行和多行 lambda 表达式语法。</span><span class="sxs-lookup"><span data-stu-id="89111-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

<span data-ttu-id="89111-112">下面的示例是一个将值写入控制台的 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="89111-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="89111-113">该示例显示了子程序的单行和多行 lambda 表达式语法。</span><span class="sxs-lookup"><span data-stu-id="89111-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

<span data-ttu-id="89111-114">请注意，在前面的示例中，lambda 表达式被分配给变量名。</span><span class="sxs-lookup"><span data-stu-id="89111-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="89111-115">只要引用变量，就会调用 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="89111-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="89111-116">还可以同时声明和调用 lambda 表达式，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="89111-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

<span data-ttu-id="89111-117">Lambda 表达式可以作为函数调用的值返回（如本主题后面的[上下文](#context)部分的示例中所示），或者作为参数传递给采用委托类型的参数，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="89111-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a><span data-ttu-id="89111-118">Lambda 表达式语法</span><span class="sxs-lookup"><span data-stu-id="89111-118">Lambda Expression Syntax</span></span>

<span data-ttu-id="89111-119">Lambda 表达式的语法与标准函数或子例程的语法相似。</span><span class="sxs-lookup"><span data-stu-id="89111-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="89111-120">不同之处如下：</span><span class="sxs-lookup"><span data-stu-id="89111-120">The differences are as follows:</span></span>

- <span data-ttu-id="89111-121">Lambda 表达式没有名称。</span><span class="sxs-lookup"><span data-stu-id="89111-121">A lambda expression does not have a name.</span></span>

- <span data-ttu-id="89111-122">Lambda 表达式不能具有修饰符，如 `Overloads` 或 `Overrides` 。</span><span class="sxs-lookup"><span data-stu-id="89111-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>

- <span data-ttu-id="89111-123">单行 lambda 函数不使用 `As` 子句来指定返回类型。</span><span class="sxs-lookup"><span data-stu-id="89111-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="89111-124">相反，该类型是从 lambda 表达式体的计算结果为的值推断出来的。</span><span class="sxs-lookup"><span data-stu-id="89111-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="89111-125">例如，如果 lambda 表达式的主体为 `cust.City = "London"` ，则其返回类型为 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="89111-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>

- <span data-ttu-id="89111-126">在多行 lambda 函数中，可以使用子句指定返回类型 `As` ，或省略 `As` 子句以便推断返回类型。</span><span class="sxs-lookup"><span data-stu-id="89111-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="89111-127">如果 `As` 为多行 lambda 函数省略子句，则会将返回类型推断为来自 `Return` 多行 lambda 函数中所有语句的基准类型。</span><span class="sxs-lookup"><span data-stu-id="89111-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="89111-128">*主导类型*是所有其他类型可以扩大到的唯一类型。</span><span class="sxs-lookup"><span data-stu-id="89111-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="89111-129">如果无法确定此唯一类型，则主导类型是数组中所有其他类型可以缩小到的唯一类型。</span><span class="sxs-lookup"><span data-stu-id="89111-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="89111-130">如果无法确定为这两种唯一类型之一，则基准类型是 `Object`。</span><span class="sxs-lookup"><span data-stu-id="89111-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="89111-131">在这种情况下，如果将 `Option Strict` 设置为 `On` ，则会发生编译器错误。</span><span class="sxs-lookup"><span data-stu-id="89111-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>

     <span data-ttu-id="89111-132">例如，如果提供给语句的表达式 `Return` 包含类型为、和的值， `Integer` `Long` `Double` 则生成的数组的类型为 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="89111-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="89111-133">`Integer`和都 `Long` 仅扩大到 `Double` 和 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="89111-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="89111-134">因此， `Double` 是基准类型。</span><span class="sxs-lookup"><span data-stu-id="89111-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="89111-135">有关详细信息，请参阅 [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="89111-135">For more information, see [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md).</span></span>

- <span data-ttu-id="89111-136">单行函数的主体必须是返回值的表达式，而不是语句。</span><span class="sxs-lookup"><span data-stu-id="89111-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="89111-137">没有 `Return` 适用于单行函数的语句。</span><span class="sxs-lookup"><span data-stu-id="89111-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="89111-138">单行函数返回的值是函数体中表达式的值。</span><span class="sxs-lookup"><span data-stu-id="89111-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>

- <span data-ttu-id="89111-139">单行子例程的主体必须是单行语句。</span><span class="sxs-lookup"><span data-stu-id="89111-139">The body of a single-line subroutine must be single-line statement.</span></span>

- <span data-ttu-id="89111-140">单行函数和子例程不包含 `End Function` 或 `End Sub` 语句。</span><span class="sxs-lookup"><span data-stu-id="89111-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>

- <span data-ttu-id="89111-141">您可以使用关键字指定 lambda 表达式参数的数据类型 `As` ，也可以推断参数的数据类型。</span><span class="sxs-lookup"><span data-stu-id="89111-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="89111-142">所有参数都必须具有指定的数据类型，或者都必须被推断。</span><span class="sxs-lookup"><span data-stu-id="89111-142">Either all parameters must have specified data types or all must be inferred.</span></span>

- <span data-ttu-id="89111-143">`Optional``Paramarray`不允许使用和参数。</span><span class="sxs-lookup"><span data-stu-id="89111-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>

- <span data-ttu-id="89111-144">不允许使用泛型参数。</span><span class="sxs-lookup"><span data-stu-id="89111-144">Generic parameters are not permitted.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="89111-145">异步 lambda</span><span class="sxs-lookup"><span data-stu-id="89111-145">Async Lambdas</span></span>

<span data-ttu-id="89111-146">通过使用[Async](../../../language-reference/modifiers/async.md)和[Await 运算符](../../../language-reference/operators/await-operator.md)关键字，你可以轻松创建包含异步处理的 lambda 表达式和语句。</span><span class="sxs-lookup"><span data-stu-id="89111-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../language-reference/modifiers/async.md) and [Await Operator](../../../language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="89111-147">例如，下面的 Windows 窗体示例包含一个调用和等待异步方法 `ExampleMethodAsync`的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="89111-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

```vb
Public Class Form1

    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        ' ExampleMethodAsync returns a Task.
        Await ExampleMethodAsync()
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."
    End Sub

    Async Function ExampleMethodAsync() As Task
        ' The following line simulates a task-returning asynchronous process.
        Await Task.Delay(1000)
    End Function

End Class
```

<span data-ttu-id="89111-148">可以通过在[AddHandler 语句](../../../language-reference/statements/addhandler-statement.md)中使用 async lambda 来添加同一事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="89111-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="89111-149">若要添加此处理程序，请在 lambda 参数列表前添加一个 `Async` 修饰符，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="89111-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>

```vb
Public Class Form1

    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AddHandler Button1.Click,
            Async Sub(sender1, e1)
                ' ExampleMethodAsync returns a Task.
                Await ExampleMethodAsync()
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."
            End Sub
    End Sub

    Async Function ExampleMethodAsync() As Task
        ' The following line simulates a task-returning asynchronous process.
        Await Task.Delay(1000)
    End Function

End Class
```

<span data-ttu-id="89111-150">有关如何创建和使用异步方法的详细信息，请参阅[使用 async 和 Await 进行异步编程](../../concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="89111-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../concepts/async/index.md).</span></span>

## <a name="context"></a><span data-ttu-id="89111-151">上下文</span><span class="sxs-lookup"><span data-stu-id="89111-151">Context</span></span>

<span data-ttu-id="89111-152">Lambda 表达式将其上下文与定义它的范围共享。</span><span class="sxs-lookup"><span data-stu-id="89111-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="89111-153">它与在包含范围内编写的任何代码具有相同的访问权限。</span><span class="sxs-lookup"><span data-stu-id="89111-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="89111-154">这包括访问包含作用域中的成员变量、函数和 sub、以及 `Me` 参数和局部变量。</span><span class="sxs-lookup"><span data-stu-id="89111-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>

<span data-ttu-id="89111-155">对包含作用域中的局部变量和参数的访问可以超出该范围的生存期。</span><span class="sxs-lookup"><span data-stu-id="89111-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="89111-156">只要引用 lambda 表达式的委托不可用于垃圾回收，就会保留对原始环境中的变量的访问。</span><span class="sxs-lookup"><span data-stu-id="89111-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="89111-157">在下面的示例中，变量 `target` 是的局部变量 `makeTheGame` ，其中定义了 lambda 表达式的方法 `playTheGame` 。</span><span class="sxs-lookup"><span data-stu-id="89111-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="89111-158">请注意，分配给中的返回的 lambda 表达式 `takeAGuess` `Main` 仍有权访问本地变量 `target` 。</span><span class="sxs-lookup"><span data-stu-id="89111-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

<span data-ttu-id="89111-159">下面的示例演示了嵌套 lambda 表达式的各种访问权限。</span><span class="sxs-lookup"><span data-stu-id="89111-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="89111-160">当从执行返回的 lambda 表达式时 `Main` `aDel` ，它将访问这些元素：</span><span class="sxs-lookup"><span data-stu-id="89111-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>

- <span data-ttu-id="89111-161">定义它的类的字段：`aField`</span><span class="sxs-lookup"><span data-stu-id="89111-161">A field of the class in which it is defined: `aField`</span></span>

- <span data-ttu-id="89111-162">定义它的类的属性：`aProp`</span><span class="sxs-lookup"><span data-stu-id="89111-162">A property of the class in which it is defined: `aProp`</span></span>

- <span data-ttu-id="89111-163">定义它的方法的参数 `functionWithNestedLambda` ：`level1`</span><span class="sxs-lookup"><span data-stu-id="89111-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>

- <span data-ttu-id="89111-164">的局部变量 `functionWithNestedLambda` ：`localVar`</span><span class="sxs-lookup"><span data-stu-id="89111-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>

- <span data-ttu-id="89111-165">它在其中进行嵌套的 lambda 表达式的参数：`level2`</span><span class="sxs-lookup"><span data-stu-id="89111-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="89111-166">转换为委托类型</span><span class="sxs-lookup"><span data-stu-id="89111-166">Converting to a Delegate Type</span></span>

<span data-ttu-id="89111-167">Lambda 表达式可隐式转换为兼容的委托类型。</span><span class="sxs-lookup"><span data-stu-id="89111-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="89111-168">有关兼容性的一般要求的信息，请参阅[宽松委托转换](../delegates/relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="89111-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="89111-169">例如，下面的代码示例演示一个隐式转换为 `Func(Of Integer, Boolean)` 或匹配的委托签名的 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="89111-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

<span data-ttu-id="89111-170">下面的代码示例演示一个隐式转换为 `Sub(Of Double, String, Double)` 或匹配的委托签名的 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="89111-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

<span data-ttu-id="89111-171">当你将 lambda 表达式分配给委托或将其作为参数传递给过程时，可以指定参数名称但省略其数据类型，从而使类型从委托中获取。</span><span class="sxs-lookup"><span data-stu-id="89111-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>

## <a name="examples"></a><span data-ttu-id="89111-172">示例</span><span class="sxs-lookup"><span data-stu-id="89111-172">Examples</span></span>

- <span data-ttu-id="89111-173">下面的示例定义一个 lambda 表达式，该表达式 `True` 在可以为 null 的值类型参数具有赋值时返回， `False` 如果其值为，则返回 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="89111-173">The following example defines a lambda expression that returns `True` if the nullable value type argument has an assigned value, and `False` if its value is `Nothing`.</span></span>

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- <span data-ttu-id="89111-174">下面的示例定义了一个 lambda 表达式，该表达式返回数组中最后一个元素的索引。</span><span class="sxs-lookup"><span data-stu-id="89111-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="89111-175">另请参阅</span><span class="sxs-lookup"><span data-stu-id="89111-175">See also</span></span>

- [<span data-ttu-id="89111-176">过程</span><span class="sxs-lookup"><span data-stu-id="89111-176">Procedures</span></span>](./index.md)
- [<span data-ttu-id="89111-177">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="89111-177">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="89111-178">委托</span><span class="sxs-lookup"><span data-stu-id="89111-178">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="89111-179">Function 语句</span><span class="sxs-lookup"><span data-stu-id="89111-179">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="89111-180">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="89111-180">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="89111-181">可以为 null 的值类型</span><span class="sxs-lookup"><span data-stu-id="89111-181">Nullable Value Types</span></span>](../data-types/nullable-value-types.md)
- [<span data-ttu-id="89111-182">如何：在 Visual Basic 中将过程传递给另一过程</span><span class="sxs-lookup"><span data-stu-id="89111-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="89111-183">如何：创建 lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="89111-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)
- [<span data-ttu-id="89111-184">宽松委托转换</span><span class="sxs-lookup"><span data-stu-id="89111-184">Relaxed Delegate Conversion</span></span>](../delegates/relaxed-delegate-conversion.md)
