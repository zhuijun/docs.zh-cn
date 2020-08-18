---
title: 本地函数 - C# 编程指南
description: C# 中的本地函数是嵌套在另一成员中并且可以从其包含成员中调用的私有方法。
ms.date: 06/14/2017
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 854ec7ab4a4cc637c0a5ad03e0344d2f1f7679d2
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063297"
---
# <a name="local-functions-c-programming-guide"></a><span data-ttu-id="15541-103">本地函数（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="15541-103">Local functions (C# Programming Guide)</span></span>

<span data-ttu-id="15541-104">从 C# 7.0 开始，C# *支持本地函数*。</span><span class="sxs-lookup"><span data-stu-id="15541-104">Starting with C# 7.0, C# supports *local functions*.</span></span> <span data-ttu-id="15541-105">本地函数是一种嵌套在另一成员中的类型的私有方法。</span><span class="sxs-lookup"><span data-stu-id="15541-105">Local functions are private methods of a type that are nested in another member.</span></span> <span data-ttu-id="15541-106">仅能从其包含成员中调用它们。</span><span class="sxs-lookup"><span data-stu-id="15541-106">They can only be called from their containing member.</span></span> <span data-ttu-id="15541-107">可以在以下位置中声明和调用本地函数：</span><span class="sxs-lookup"><span data-stu-id="15541-107">Local functions can be declared in and called from:</span></span>

- <span data-ttu-id="15541-108">方法（尤其是迭代器方法和异步方法）</span><span class="sxs-lookup"><span data-stu-id="15541-108">Methods, especially iterator methods and async methods</span></span>
- <span data-ttu-id="15541-109">构造函数</span><span class="sxs-lookup"><span data-stu-id="15541-109">Constructors</span></span>
- <span data-ttu-id="15541-110">属性访问器</span><span class="sxs-lookup"><span data-stu-id="15541-110">Property accessors</span></span>
- <span data-ttu-id="15541-111">事件访问器</span><span class="sxs-lookup"><span data-stu-id="15541-111">Event accessors</span></span>
- <span data-ttu-id="15541-112">匿名方法</span><span class="sxs-lookup"><span data-stu-id="15541-112">Anonymous methods</span></span>
- <span data-ttu-id="15541-113">Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="15541-113">Lambda expressions</span></span>
- <span data-ttu-id="15541-114">终结器</span><span class="sxs-lookup"><span data-stu-id="15541-114">Finalizers</span></span>
- <span data-ttu-id="15541-115">其他本地函数</span><span class="sxs-lookup"><span data-stu-id="15541-115">Other local functions</span></span>

<span data-ttu-id="15541-116">但是，不能在 expression-bodied 成员中声明本地函数。</span><span class="sxs-lookup"><span data-stu-id="15541-116">However, local functions can't be declared inside an expression-bodied member.</span></span>

> [!NOTE]
> <span data-ttu-id="15541-117">在某些情况下，可以使用 lambda 表达式实现本地函数也支持的功能。</span><span class="sxs-lookup"><span data-stu-id="15541-117">In some cases, you can use a lambda expression to implement functionality also supported by a local function.</span></span> <span data-ttu-id="15541-118">有关比较，请参阅[本地函数与 lambda 表达式](#local-functions-vs-lambda-expressions)。</span><span class="sxs-lookup"><span data-stu-id="15541-118">For a comparison, see [Local functions vs. lambda expressions](#local-functions-vs-lambda-expressions).</span></span>

<span data-ttu-id="15541-119">本地函数可使代码意图明确。</span><span class="sxs-lookup"><span data-stu-id="15541-119">Local functions make the intent of your code clear.</span></span> <span data-ttu-id="15541-120">任何读取代码的人都可以看到，此方法不可调用，包含方法除外。</span><span class="sxs-lookup"><span data-stu-id="15541-120">Anyone reading your code can see that the method is not callable except by the containing method.</span></span> <span data-ttu-id="15541-121">对于团队项目，它们也使得其他开发人员无法直接从类或结构中的其他位置错误调用此方法。</span><span class="sxs-lookup"><span data-stu-id="15541-121">For team projects, they also make it impossible for another developer to mistakenly call the method directly from elsewhere in the class or struct.</span></span>

## <a name="local-function-syntax"></a><span data-ttu-id="15541-122">本地函数语法</span><span class="sxs-lookup"><span data-stu-id="15541-122">Local function syntax</span></span>

<span data-ttu-id="15541-123">本地函数被定义为包含成员中的嵌套方法。</span><span class="sxs-lookup"><span data-stu-id="15541-123">A local function is defined as a nested method inside a containing member.</span></span> <span data-ttu-id="15541-124">其定义具有以下语法：</span><span class="sxs-lookup"><span data-stu-id="15541-124">Its definition has the following syntax:</span></span>

```csharp
<modifiers: async | unsafe> <return-type> <method-name> <parameter-list>
```

<span data-ttu-id="15541-125">本地函数可以使用 [async](../../language-reference/keywords/async.md) 和 [unsafe](../../language-reference/keywords/unsafe.md) 修饰符。</span><span class="sxs-lookup"><span data-stu-id="15541-125">Local functions can use the [async](../../language-reference/keywords/async.md) and [unsafe](../../language-reference/keywords/unsafe.md) modifiers.</span></span>

<span data-ttu-id="15541-126">请注意，在包含成员中定义的所有本地变量（包括其方法参数）都可在本地函数中访问。</span><span class="sxs-lookup"><span data-stu-id="15541-126">Note that all local variables that are defined in the containing member, including its method parameters, are accessible in the local function.</span></span>

<span data-ttu-id="15541-127">与方法定义不同，本地函数定义不能包含成员访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="15541-127">Unlike a method definition, a local function definition cannot include the member access modifier.</span></span> <span data-ttu-id="15541-128">因为所有本地函数都是私有的，包括访问修饰符（如 `private` 关键字）会生成编译器错误 CS0106“修饰符‘private’对于此项无效”。</span><span class="sxs-lookup"><span data-stu-id="15541-128">Because all local functions are private, including an access modifier, such as the `private` keyword, generates compiler error CS0106, "The modifier 'private' is not valid for this item."</span></span>

> [!NOTE]
> <span data-ttu-id="15541-129">在 C# 8.0 之前，本地函数不能包含 `static` 修饰符。</span><span class="sxs-lookup"><span data-stu-id="15541-129">Prior to C# 8.0, local functions cannot include the `static` modifier.</span></span> <span data-ttu-id="15541-130">包括 `static` 关键字将生成编译器错误 CS0106“修饰符‘static’对于此项无效”。</span><span class="sxs-lookup"><span data-stu-id="15541-130">Including the `static` keyword generates compiler error CS0106, "The modifier 'static' is not valid for this item."</span></span>

<span data-ttu-id="15541-131">此外，属性不能应用于本地函数或其参数和类型参数。</span><span class="sxs-lookup"><span data-stu-id="15541-131">In addition, attributes can't be applied to the local function or to its parameters and type parameters.</span></span>

<span data-ttu-id="15541-132">以下示例定义了一个名为 `AppendPathSeparator` 的本地函数，该函数对于名为 `GetText` 的方法是私有的：</span><span class="sxs-lookup"><span data-stu-id="15541-132">The following example defines a local function named `AppendPathSeparator` that is private to a method named `GetText`:</span></span>

[!code-csharp[LocalFunctionExample](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions1.cs)]  

## <a name="local-functions-and-exceptions"></a><span data-ttu-id="15541-133">本地函数和异常</span><span class="sxs-lookup"><span data-stu-id="15541-133">Local functions and exceptions</span></span>

<span data-ttu-id="15541-134">本地函数的一个实用功能是可以允许立即显示异常。</span><span class="sxs-lookup"><span data-stu-id="15541-134">One of the useful features of local functions is that they can allow exceptions to surface immediately.</span></span> <span data-ttu-id="15541-135">对于方法迭代器，仅在枚举返回的序列时才显示异常，而非在检索迭代器时。</span><span class="sxs-lookup"><span data-stu-id="15541-135">For method iterators, exceptions are surfaced only when the returned sequence is enumerated, and not when the iterator is retrieved.</span></span> <span data-ttu-id="15541-136">对于异步方法，在等待返回的任务时，将观察到异步方法中引发的任何异常。</span><span class="sxs-lookup"><span data-stu-id="15541-136">For async methods, any exceptions thrown in an async method are observed when the returned task is awaited.</span></span>

<span data-ttu-id="15541-137">以下示例定义 `OddSequence` 方法，用于枚举指定范围之间的奇数。</span><span class="sxs-lookup"><span data-stu-id="15541-137">The following example defines an `OddSequence` method that enumerates odd numbers between a specified range.</span></span> <span data-ttu-id="15541-138">因为它会将一个大于 100 的数字传递到 `OddSequence` 迭代器方法，该方法将引发 <xref:System.ArgumentOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="15541-138">Because it passes a number greater than 100 to the `OddSequence` enumerator method, the method throws an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="15541-139">如示例中的输出所示，仅当循环访问数字时才显示异常，而非检索迭代器时。</span><span class="sxs-lookup"><span data-stu-id="15541-139">As the output from the example shows, the exception surfaces only when you iterate the numbers, and not when you retrieve the enumerator.</span></span>

[!code-csharp[LocalFunctionIterator1](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator1.cs)]

<span data-ttu-id="15541-140">相反，可以在执行验证时和通过从本地函数返回迭代器检索迭代器之前引发异常，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="15541-140">Instead, you can throw an exception when performing validation and before retrieving the iterator by returning the iterator from a local function, as the following example shows.</span></span>

[!code-csharp[LocalFunctionIterator2](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-iterator2.cs)]

<span data-ttu-id="15541-141">可以通过类似的方式使用本地函数来处理异步操作之外的异常。</span><span class="sxs-lookup"><span data-stu-id="15541-141">Local functions can be used in a similar way to handle exceptions outside of the asynchronous operation.</span></span> <span data-ttu-id="15541-142">异步方法中引发的异常通常都需要检查 <xref:System.AggregateException> 的内部异常。</span><span class="sxs-lookup"><span data-stu-id="15541-142">Ordinarily, exceptions thrown in async method require that you examine the inner exceptions of an <xref:System.AggregateException>.</span></span> <span data-ttu-id="15541-143">本地函数允许代码快速失败，并允许同步引发和观察异常。</span><span class="sxs-lookup"><span data-stu-id="15541-143">Local functions allow your code to fail fast and allow your exception to be both thrown and observed synchronously.</span></span>

<span data-ttu-id="15541-144">以下示例使用名为 `GetMultipleAsync` 的异步方法暂停指定的秒数并返回一个值，该值是该秒数的任意倍数。</span><span class="sxs-lookup"><span data-stu-id="15541-144">The following example uses an asynchronous method named `GetMultipleAsync` to pause for a specified number of seconds and return a value that is a random multiple of that number of seconds.</span></span> <span data-ttu-id="15541-145">最大延迟为 5 秒；如果该值大于 5，则结果为 <xref:System.ArgumentOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="15541-145">The maximum delay is 5 seconds; an <xref:System.ArgumentOutOfRangeException> results if the value is greater than 5.</span></span> <span data-ttu-id="15541-146">如以下示例所示，开始执行 `GetMultipleAsync` 方法后，将值 6 传递到 `GetMultipleAsync` 方法时引发的异常将在 <xref:System.AggregateException> 中进行包装。</span><span class="sxs-lookup"><span data-stu-id="15541-146">As the following example shows, the exception that is thrown when a value of 6 is passed to the `GetMultipleAsync` method is wrapped in an <xref:System.AggregateException> after the `GetMultipleAsync` method begins execution.</span></span>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async1.cs)]

<span data-ttu-id="15541-147">正如处理方法迭代器一样，可以在调用异步方法之前重构本示例中的代码以执行验证。</span><span class="sxs-lookup"><span data-stu-id="15541-147">As we did with the method iterator, we can refactor the code from this example to perform the validation before calling the asynchronous method.</span></span> <span data-ttu-id="15541-148">如以下示例中的输出所示，<xref:System.ArgumentOutOfRangeException> 不在 <xref:System.AggregateException> 中进行包装。</span><span class="sxs-lookup"><span data-stu-id="15541-148">As the output from the following example shows, the <xref:System.ArgumentOutOfRangeException> is not wrapped in a <xref:System.AggregateException>.</span></span>

[!code-csharp[LocalFunctionAsync](~/samples/snippets/csharp/programming-guide/classes-and-structs/local-functions-async2.cs)]

## <a name="local-functions-vs-lambda-expressions"></a><span data-ttu-id="15541-149">本地函数与 Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="15541-149">Local functions vs. lambda expressions</span></span>

<span data-ttu-id="15541-150">乍看之下，本地函数和 [lambda 表达式](../../language-reference/operators/lambda-expressions.md)非常相似。</span><span class="sxs-lookup"><span data-stu-id="15541-150">At first glance, local functions and [lambda expressions](../../language-reference/operators/lambda-expressions.md) are very similar.</span></span> <span data-ttu-id="15541-151">在许多情况下，选择使用 Lambda 表达式还是本地函数是风格和个人偏好的问题。</span><span class="sxs-lookup"><span data-stu-id="15541-151">In many cases, the choice between using lambda expressions and local functions is a matter of style and personal preference.</span></span> <span data-ttu-id="15541-152">但是，应该注意，从两者中选用一种的时机和条件其实是存在差别的。</span><span class="sxs-lookup"><span data-stu-id="15541-152">However, there are real differences in where you can use one or the other that you should be aware of.</span></span>

<span data-ttu-id="15541-153">让我们检查一下阶乘算法的本地函数实现和 lambda 表达式实现之间的差异。</span><span class="sxs-lookup"><span data-stu-id="15541-153">Let's examine the differences between the local function and lambda expression implementations of the factorial algorithm.</span></span> <span data-ttu-id="15541-154">首先使用本地函数的版本：</span><span class="sxs-lookup"><span data-stu-id="15541-154">First the version using a local function:</span></span>

[!code-csharp[LocalFunctionFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

<span data-ttu-id="15541-155">将该实现与使用 Lambda 表达式的版本对比：</span><span class="sxs-lookup"><span data-stu-id="15541-155">Contrast that implementation with a version that uses lambda expressions:</span></span>

[!code-csharp[26_LambdaFactorial](../../../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

<span data-ttu-id="15541-156">本地函数具有名称。</span><span class="sxs-lookup"><span data-stu-id="15541-156">The local functions have names.</span></span> <span data-ttu-id="15541-157">Lambda 表达式是赋给 `Func` 或 `Action` 类型变量的匿名方法。</span><span class="sxs-lookup"><span data-stu-id="15541-157">The lambda expressions are anonymous methods that are assigned to variables that are `Func` or `Action` types.</span></span> <span data-ttu-id="15541-158">在声明本地函数时，参数类型和返回类型是函数声明的一部分。</span><span class="sxs-lookup"><span data-stu-id="15541-158">When you declare a local function, the argument types and return type are part of the function declaration.</span></span> <span data-ttu-id="15541-159">参数类型和返回类型不是 Lambda 表达式主体的一部分，而是 Lambda 表达式变量类型声明的一部分。</span><span class="sxs-lookup"><span data-stu-id="15541-159">Instead of being part of the body of the lambda expression, the argument types and return type are part of the lambda expression's variable type declaration.</span></span> <span data-ttu-id="15541-160">这两种差别可以产生跟清楚的代码。</span><span class="sxs-lookup"><span data-stu-id="15541-160">Those two differences may result in clearer code.</span></span>

<span data-ttu-id="15541-161">本地函数的明确赋值规则与 Lambda 表达式的不同。</span><span class="sxs-lookup"><span data-stu-id="15541-161">Local functions have different rules for definite assignment than lambda expressions.</span></span> <span data-ttu-id="15541-162">从范围内的任意代码位置都可以引用本地函数声明。</span><span class="sxs-lookup"><span data-stu-id="15541-162">A local function declaration can be referenced from any code location where it is in scope.</span></span> <span data-ttu-id="15541-163">在可以访问（或通过引用 Lambda 表达式的委托调用）Lambda 表达式之前，必须先将 Lambda 表达式赋给委托变量。</span><span class="sxs-lookup"><span data-stu-id="15541-163">A lambda expression must be assigned to a delegate variable before it can be accessed (or called through the delegate referencing the lambda expression).</span></span> <span data-ttu-id="15541-164">请注意，使用 lambda 表达式的版本必须先定义 lambda 表达式 `nthFactorial`，然后再对其进行声明并实例化。</span><span class="sxs-lookup"><span data-stu-id="15541-164">Notice that the version using the lambda expression must declare and initialize the lambda expression `nthFactorial` before defining it.</span></span> <span data-ttu-id="15541-165">否则，会导致分配前引用 `nthFactorial` 时出现编译时错误。</span><span class="sxs-lookup"><span data-stu-id="15541-165">Not doing so results in a compile time error for referencing `nthFactorial` before assigning it.</span></span> <span data-ttu-id="15541-166">这些区别意味着使用本地函数创建递归算法会更轻松。</span><span class="sxs-lookup"><span data-stu-id="15541-166">These differences mean that recursive algorithms are easier to create using local functions.</span></span> <span data-ttu-id="15541-167">你可以声明和定义一个调用自身的本地函数。</span><span class="sxs-lookup"><span data-stu-id="15541-167">You can declare and define a local function that calls itself.</span></span> <span data-ttu-id="15541-168">必须声明 Lambda 表达式，赋给默认值，然后才能将其重新赋给引用相同 Lambda 表达式的主体。</span><span class="sxs-lookup"><span data-stu-id="15541-168">Lambda expressions must be declared, and assigned a default value before they can be re-assigned to a body that references the same lambda expression.</span></span>

<span data-ttu-id="15541-169">明确分配规则也会影响本地函数或 Lambda 表达式捕获的任何变量。</span><span class="sxs-lookup"><span data-stu-id="15541-169">Definite assignment rules also affect any variables that are captured by the local function or lambda expression.</span></span> <span data-ttu-id="15541-170">本地函数和 Lambda 表达式规则都要求在将本地函数或 Lambda 表达式转换为委托时，明确分配任何捕获的变量。</span><span class="sxs-lookup"><span data-stu-id="15541-170">Both local functions and lambda expression rules demand that any captured variables are definitely assigned at the point when the local function or lambda expression is converted to a delegate.</span></span> <span data-ttu-id="15541-171">区别在于 Lambda 表达式在声明时转换为委托。</span><span class="sxs-lookup"><span data-stu-id="15541-171">The difference is that lambda expressions are converted to delegates when they are declared.</span></span> <span data-ttu-id="15541-172">只有在用作委托时，本地函数才转换为委托。</span><span class="sxs-lookup"><span data-stu-id="15541-172">Local functions are converted to delegates only when used as a delegate.</span></span> <span data-ttu-id="15541-173">如果声明了本地函数，但只是通过像调用方法一样调用该函数来引用该函数，它将不会转换成委托。</span><span class="sxs-lookup"><span data-stu-id="15541-173">If you declare a local function and only reference it by calling it like a method, it will not be converted to a delegate.</span></span> <span data-ttu-id="15541-174">使用该规则可在封闭范围内的任何方便的位置声明本地函数。</span><span class="sxs-lookup"><span data-stu-id="15541-174">That rule enables you to declare a local function at any convenient location in its enclosing scope.</span></span> <span data-ttu-id="15541-175">声明本地函数的位置常见于父方法的末尾和返回任何语句后方。</span><span class="sxs-lookup"><span data-stu-id="15541-175">It's common to declare local functions at the end of the parent method, after any return statements.</span></span>

<span data-ttu-id="15541-176">第三，编译器可以执行静态分析，因此本地函数能够在封闭范围内明确分配捕获的变量。</span><span class="sxs-lookup"><span data-stu-id="15541-176">Third, the compiler can perform static analysis that enables local functions to definitely assign captured variables in the enclosing scope.</span></span> <span data-ttu-id="15541-177">请看以下示例：</span><span class="sxs-lookup"><span data-stu-id="15541-177">Consider this example:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="15541-178">编译器可以确定 `LocalFunction` 在调用时明确分配 `y`。</span><span class="sxs-lookup"><span data-stu-id="15541-178">The compiler can determine that `LocalFunction` definitely assigns `y` when called.</span></span> <span data-ttu-id="15541-179">因为在 `return` 语句之前调用了 `LocalFunction`，所以在 `return` 语句中明确分配了 `y`。</span><span class="sxs-lookup"><span data-stu-id="15541-179">Because `LocalFunction` is called before the `return` statement, `y` is definitely assigned at the `return` statement.</span></span>

<span data-ttu-id="15541-180">可实现示例分析的分析允许第四个差异。</span><span class="sxs-lookup"><span data-stu-id="15541-180">The analysis that enables the example analysis enables the fourth difference.</span></span> <span data-ttu-id="15541-181">根据它们的用途，本地函数可以避免 Lambda 表达式始终需要的堆分配。</span><span class="sxs-lookup"><span data-stu-id="15541-181">Depending on their use, local functions can avoid heap allocations that are always necessary for lambda expressions.</span></span> <span data-ttu-id="15541-182">如果本地函数永远不会转换为委托，并且本地函数捕获的变量都不会被其他转换为委托的 lambda 或本地函数捕获，则编译器可以避免堆分配。</span><span class="sxs-lookup"><span data-stu-id="15541-182">If a local function is never converted to a delegate, and none of the variables captured by the local function is captured by other lambdas or local functions that are converted to delegates, the compiler can avoid heap allocations.</span></span>

<span data-ttu-id="15541-183">请看以下异步示例：</span><span class="sxs-lookup"><span data-stu-id="15541-183">Consider this async example:</span></span>

[!code-csharp[TaskLambdaExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

<span data-ttu-id="15541-184">该 lambda 表达式的闭包包含 `address`、`index` 和 `name` 变量。</span><span class="sxs-lookup"><span data-stu-id="15541-184">The closure for this lambda expression contains the `address`, `index` and `name` variables.</span></span> <span data-ttu-id="15541-185">就本地函数而言，实现闭包的对象可能为 `struct` 类型。</span><span class="sxs-lookup"><span data-stu-id="15541-185">In the case of local functions, the object that implements the closure may be a `struct` type.</span></span> <span data-ttu-id="15541-186">该结构类型将通过引用传递给本地函数。</span><span class="sxs-lookup"><span data-stu-id="15541-186">That struct type would be passed by reference to the local function.</span></span> <span data-ttu-id="15541-187">实现中的这个差异将保存在分配上。</span><span class="sxs-lookup"><span data-stu-id="15541-187">This difference in implementation would save on an allocation.</span></span>

<span data-ttu-id="15541-188">Lambda 表达式所需的实例化意味着额外的内存分配，后者可能是时间关键代码路径中的性能因素。</span><span class="sxs-lookup"><span data-stu-id="15541-188">The instantiation necessary for lambda expressions means extra memory allocations, which may be a performance factor in time-critical code paths.</span></span> <span data-ttu-id="15541-189">本地函数不会产生这种开销。</span><span class="sxs-lookup"><span data-stu-id="15541-189">Local functions do not incur this overhead.</span></span> <span data-ttu-id="15541-190">在以上示例中，本地函数版本具有的分配比 lambda 表达式版本少 2 个。</span><span class="sxs-lookup"><span data-stu-id="15541-190">In the example above, the local functions version has 2 fewer allocations than the lambda expression version.</span></span>

> [!NOTE]
> <span data-ttu-id="15541-191">等效于此方法的本地函数还将类用于闭包。</span><span class="sxs-lookup"><span data-stu-id="15541-191">The local function equivalent of this method also uses a class for the closure.</span></span> <span data-ttu-id="15541-192">实现详细信息包括本地函数的闭包是作为 `class` 还是 `struct` 实现。</span><span class="sxs-lookup"><span data-stu-id="15541-192">Whether the closure for a local function is implemented as a `class` or a `struct` is an implementation detail.</span></span> <span data-ttu-id="15541-193">本地函数可能使用 `struct`，而 lambda 将始终使用 `class`。</span><span class="sxs-lookup"><span data-stu-id="15541-193">A local function may use a `struct` whereas a lambda will always use a `class`.</span></span>

[!code-csharp[TaskLocalFunctionExample](../../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

<span data-ttu-id="15541-194">在本示例中尚未演示的最后一个优点是，可将本地函数作为迭代器实现，使用 `yield return` 语法生成一系列值。</span><span class="sxs-lookup"><span data-stu-id="15541-194">One final advantage not demonstrated in this sample is that local functions can be implemented as iterators, using the `yield return` syntax to produce a sequence of values.</span></span> <span data-ttu-id="15541-195">Lambda 表达式中不允许使用 `yield return` 语句。</span><span class="sxs-lookup"><span data-stu-id="15541-195">The `yield return` statement is not allowed in lambda expressions.</span></span>

<span data-ttu-id="15541-196">虽然本地函数对 lambda 表达式可能有点冗余，但实际上它们的目的和用法都不一样。</span><span class="sxs-lookup"><span data-stu-id="15541-196">While local functions may seem redundant to lambda expressions, they actually serve different purposes and have different uses.</span></span> <span data-ttu-id="15541-197">如果想要编写仅从上下文或其他方法中调用的函数，则使用本地函数更高效。</span><span class="sxs-lookup"><span data-stu-id="15541-197">Local functions are more efficient for the case when you want to write a function that is called only from the context of another method.</span></span>

## <a name="see-also"></a><span data-ttu-id="15541-198">请参阅</span><span class="sxs-lookup"><span data-stu-id="15541-198">See also</span></span>

- [<span data-ttu-id="15541-199">方法</span><span class="sxs-lookup"><span data-stu-id="15541-199">Methods</span></span>](methods.md)
