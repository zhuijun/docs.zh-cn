---
title: 函数
description: 了解 F# 中的函数，以及 F# 如何支持常见函数编程构造。
ms.date: 05/16/2016
ms.openlocfilehash: e49183e0634dee1750757abadbfe9e9c824f51a8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596469"
---
# <a name="functions"></a><span data-ttu-id="11882-103">函数</span><span class="sxs-lookup"><span data-stu-id="11882-103">Functions</span></span>

<span data-ttu-id="11882-104">函数是任何编程语言中程序执行的基本单元。</span><span class="sxs-lookup"><span data-stu-id="11882-104">Functions are the fundamental unit of program execution in any programming language.</span></span> <span data-ttu-id="11882-105">和其他语言一样，F# 函数有一个名称，可以有形参并采用实参，且具有一个主体。</span><span class="sxs-lookup"><span data-stu-id="11882-105">As in other languages, an F# function has a name, can have parameters and take arguments, and has a body.</span></span> <span data-ttu-id="11882-106">F# 还支持函数编程构造，例如将函数视为值、在表达式中使用未命名的函数、组合函数以形成新的函数、扩充函数以及通过部分应用函数参数来隐式定义函数。</span><span class="sxs-lookup"><span data-stu-id="11882-106">F# also supports functional programming constructs such as treating functions as values, using unnamed functions in expressions, composition of functions to form new functions, curried functions, and the implicit definition of functions by way of the partial application of function arguments.</span></span>

<span data-ttu-id="11882-107">可通过使用 `let` 关键字或 `let rec` 关键字组合（如果函数为递归函数）定义函数。</span><span class="sxs-lookup"><span data-stu-id="11882-107">You define functions by using the `let` keyword, or, if the function is recursive, the `let rec` keyword combination.</span></span>

## <a name="syntax"></a><span data-ttu-id="11882-108">语法</span><span class="sxs-lookup"><span data-stu-id="11882-108">Syntax</span></span>

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a><span data-ttu-id="11882-109">备注</span><span class="sxs-lookup"><span data-stu-id="11882-109">Remarks</span></span>

<span data-ttu-id="11882-110">*function-name* 是表示函数的标识符。</span><span class="sxs-lookup"><span data-stu-id="11882-110">The *function-name* is an identifier that represents the function.</span></span> <span data-ttu-id="11882-111">*parameter-list* 包含由空格分隔的连续参数。</span><span class="sxs-lookup"><span data-stu-id="11882-111">The *parameter-list* consists of successive parameters that are separated by spaces.</span></span> <span data-ttu-id="11882-112">可按“参数”部分所述，为每个参数指定一个显式类型。</span><span class="sxs-lookup"><span data-stu-id="11882-112">You can specify an explicit type for each parameter, as described in the Parameters section.</span></span> <span data-ttu-id="11882-113">如果未指定特定参数类型，编译器将尝试通过函数体推断类型。</span><span class="sxs-lookup"><span data-stu-id="11882-113">If you do not specify a specific argument type, the compiler attempts to infer the type from the function body.</span></span> <span data-ttu-id="11882-114">*function-body* 包含一个表达式。</span><span class="sxs-lookup"><span data-stu-id="11882-114">The *function-body* consists of an expression.</span></span> <span data-ttu-id="11882-115">组成函数体的表达式通常是一个由许多表达式组成的复合表达式，组成它的那些表达式以作为返回值的最终表达式结束。</span><span class="sxs-lookup"><span data-stu-id="11882-115">The expression that makes up the function body is typically a compound expression consisting of a number of expressions that culminate in a final expression that is the return value.</span></span> <span data-ttu-id="11882-116">*return-type* 是一个冒号后跟一个类型，且为可选项。</span><span class="sxs-lookup"><span data-stu-id="11882-116">The *return-type* is a colon followed by a type and is optional.</span></span> <span data-ttu-id="11882-117">如果不显式指定返回值的类型，编译器将从最终表达式确定返回类型。</span><span class="sxs-lookup"><span data-stu-id="11882-117">If you do not specify the type of the return value explicitly, the compiler determines the return type from the final expression.</span></span>

<span data-ttu-id="11882-118">简单的函数定义类似：</span><span class="sxs-lookup"><span data-stu-id="11882-118">A simple function definition resembles the following:</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="11882-119">在上一示例中，函数名称为 `f`，参数为 `x`（具有类型 `int`），函数体为 `x + 1`，且返回值的类型为 `int`。</span><span class="sxs-lookup"><span data-stu-id="11882-119">In the previous example, the function name is `f`, the argument is `x`, which has type `int`, the function body is `x + 1`, and the return value is of type `int`.</span></span>

<span data-ttu-id="11882-120">可将函数标记为 `inline`。</span><span class="sxs-lookup"><span data-stu-id="11882-120">Functions can be marked `inline`.</span></span> <span data-ttu-id="11882-121">有关 `inline` 的信息，请参阅[内联函数](inline-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="11882-121">For information about `inline`, see [Inline Functions](inline-functions.md).</span></span>

## <a name="scope"></a><span data-ttu-id="11882-122">范围</span><span class="sxs-lookup"><span data-stu-id="11882-122">Scope</span></span>

<span data-ttu-id="11882-123">在模块范围以外的任何级别范围上，重用某个值或函数名称不是错误。</span><span class="sxs-lookup"><span data-stu-id="11882-123">At any level of scope other than module scope, it is not an error to reuse a value or function name.</span></span> <span data-ttu-id="11882-124">重用某个名称时，后来声明的名称将隐藏前面声明的名称。</span><span class="sxs-lookup"><span data-stu-id="11882-124">If you reuse a name, the name declared later shadows the name declared earlier.</span></span> <span data-ttu-id="11882-125">但在模块中的顶级别范围内，名称必须唯一。</span><span class="sxs-lookup"><span data-stu-id="11882-125">However, at the top level scope in a module, names must be unique.</span></span> <span data-ttu-id="11882-126">例如，以下代码如果出现在模块范围内则会产生错误，而出现在某个函数内部则不会产生错误：</span><span class="sxs-lookup"><span data-stu-id="11882-126">For example, the following code produces an error when it appears at module scope, but not when it appears inside a function:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

<span data-ttu-id="11882-127">但以下代码在任何级别的范围内都可接受：</span><span class="sxs-lookup"><span data-stu-id="11882-127">But the following code is acceptable at any level of scope:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a><span data-ttu-id="11882-128">参数</span><span class="sxs-lookup"><span data-stu-id="11882-128">Parameters</span></span>

<span data-ttu-id="11882-129">参数的名称列在函数名称之后。</span><span class="sxs-lookup"><span data-stu-id="11882-129">Names of parameters are listed after the function name.</span></span> <span data-ttu-id="11882-130">可以为参数指定类型，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="11882-130">You can specify a type for a parameter, as shown in the following example:</span></span>

```fsharp
let f (x : int) = x + 1
```

<span data-ttu-id="11882-131">如果指定一个类型，则应让其跟在参数名称的后面，并用冒号与参数名称隔开。</span><span class="sxs-lookup"><span data-stu-id="11882-131">If you specify a type, it follows the name of the parameter and is separated from the name by a colon.</span></span> <span data-ttu-id="11882-132">如果省略参数的类型，编译器会推断参数类型。</span><span class="sxs-lookup"><span data-stu-id="11882-132">If you omit the type for the parameter, the parameter type is inferred by the compiler.</span></span> <span data-ttu-id="11882-133">例如，在以下函数定义中，会将参数 `x` 推断为 `int` 类型，这是因为 1 为类型 `int`。</span><span class="sxs-lookup"><span data-stu-id="11882-133">For example, in the following function definition, the argument `x` is inferred to be of type `int` because 1 is of type `int`.</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="11882-134">但编译器会尝试尽量使函数成为泛型。</span><span class="sxs-lookup"><span data-stu-id="11882-134">However, the compiler will attempt to make the function as generic as possible.</span></span> <span data-ttu-id="11882-135">例如，注意下面的代码：</span><span class="sxs-lookup"><span data-stu-id="11882-135">For example, note the following code:</span></span>

```fsharp
let f x = (x, x)
```

<span data-ttu-id="11882-136">该函数从任何类型的一个参数中创建一个元组。</span><span class="sxs-lookup"><span data-stu-id="11882-136">The function creates a tuple from one argument of any type.</span></span> <span data-ttu-id="11882-137">因为未指定类型，所以该函数可用于任何参数类型。</span><span class="sxs-lookup"><span data-stu-id="11882-137">Because the type is not specified, the function can be used with any argument type.</span></span> <span data-ttu-id="11882-138">有关详细信息，请参阅[自动泛化](../generics/automatic-generalization.md)。</span><span class="sxs-lookup"><span data-stu-id="11882-138">For more information, see [Automatic Generalization](../generics/automatic-generalization.md).</span></span>

## <a name="function-bodies"></a><span data-ttu-id="11882-139">函数体</span><span class="sxs-lookup"><span data-stu-id="11882-139">Function Bodies</span></span>

<span data-ttu-id="11882-140">函数体可包含本地变量和函数的定义。</span><span class="sxs-lookup"><span data-stu-id="11882-140">A function body can contain definitions of local variables and functions.</span></span> <span data-ttu-id="11882-141">此类变量和函数位于当前函数的主体范围内，而非其外部。</span><span class="sxs-lookup"><span data-stu-id="11882-141">Such variables and functions are in scope in the body of the current function but not outside it.</span></span> <span data-ttu-id="11882-142">如果已启用轻量语法选项，则必须使用缩进来指示定义位于函数体中，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="11882-142">When you have the lightweight syntax option enabled, you must use indentation to indicate that a definition is in a function body, as shown in the following example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

<span data-ttu-id="11882-143">有关详细信息，请参阅[代码格式设置准则](../../style-guide/formatting.md)和[详细语法](../verbose-syntax.md)。</span><span class="sxs-lookup"><span data-stu-id="11882-143">For more information, see [Code Formatting Guidelines](../../style-guide/formatting.md) and [Verbose Syntax](../verbose-syntax.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="11882-144">返回值</span><span class="sxs-lookup"><span data-stu-id="11882-144">Return Values</span></span>

<span data-ttu-id="11882-145">编译器使用函数体中的最终表达式来确定返回值和类型。</span><span class="sxs-lookup"><span data-stu-id="11882-145">The compiler uses the final expression in a function body to determine the return value and type.</span></span> <span data-ttu-id="11882-146">编译器可能会从前面的表达式来推断最终表达式的类型。</span><span class="sxs-lookup"><span data-stu-id="11882-146">The compiler might infer the type of the final expression from previous expressions.</span></span> <span data-ttu-id="11882-147">在前一部分中所示的函数 `cylinderVolume` 中，可从文本 `3.14159` 的类型确定 `pi` 的类型为 `float`。</span><span class="sxs-lookup"><span data-stu-id="11882-147">In the function `cylinderVolume`, shown in the previous section, the type of `pi` is determined from the type of the literal `3.14159` to be `float`.</span></span> <span data-ttu-id="11882-148">编译器使用 `pi` 的类型来确定表达式 `h * pi * r * r` 的类型为 `float`。</span><span class="sxs-lookup"><span data-stu-id="11882-148">The compiler uses the type of `pi` to determine the type of the expression `h * pi * r * r` to be `float`.</span></span> <span data-ttu-id="11882-149">因此，函数的总体返回类型为 `float`。</span><span class="sxs-lookup"><span data-stu-id="11882-149">Therefore, the overall return type of the function is `float`.</span></span>

<span data-ttu-id="11882-150">若要显式指定返回值，请编写如下代码：</span><span class="sxs-lookup"><span data-stu-id="11882-150">To specify the return value explicitly, write the code as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

<span data-ttu-id="11882-151">如上面编写的代码一样，编译器将 **float** 应用于整个函数；如果还打算将其应用于参数类型，可使用以下代码：</span><span class="sxs-lookup"><span data-stu-id="11882-151">As the code is written above, the compiler applies **float** to the entire function; if you mean to apply it to the parameter types as well, use the following code:</span></span>

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a><span data-ttu-id="11882-152">调用函数</span><span class="sxs-lookup"><span data-stu-id="11882-152">Calling a Function</span></span>

<span data-ttu-id="11882-153">可以通过以下方式调用函数：指定函数名称，后跟一个空格，然后是由空格分隔的任何参数。</span><span class="sxs-lookup"><span data-stu-id="11882-153">You call functions by specifying the function name followed by a space and then any arguments separated by spaces.</span></span> <span data-ttu-id="11882-154">例如，若要调用函数 **cylinderVolume**，并将结果赋给值 **vol**，可编写以下代码：</span><span class="sxs-lookup"><span data-stu-id="11882-154">For example, to call the function **cylinderVolume** and assign the result to the value **vol**, you write the following code:</span></span>

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a><span data-ttu-id="11882-155">部分应用参数</span><span class="sxs-lookup"><span data-stu-id="11882-155">Partial Application of Arguments</span></span>

<span data-ttu-id="11882-156">如果提供的参数数目少于指定的参数数目，则可创建一个应采用其余参数的新函数。</span><span class="sxs-lookup"><span data-stu-id="11882-156">If you supply fewer than the specified number of arguments, you create a new function that expects the remaining arguments.</span></span> <span data-ttu-id="11882-157">这种处理参数的方法称为“柯里化”，而且这是 F# 等函数编程语言的一个特性。</span><span class="sxs-lookup"><span data-stu-id="11882-157">This method of handling arguments is referred to as *currying* and is a characteristic of functional programming languages like F#.</span></span> <span data-ttu-id="11882-158">例如，假设正在处理两种尺寸的管道：一种管道的半径为 **2.0**，另一种管道的半径为 **3.0**。</span><span class="sxs-lookup"><span data-stu-id="11882-158">For example, suppose you are working with two sizes of pipe: one has a radius of **2.0** and the other has a radius of **3.0**.</span></span> <span data-ttu-id="11882-159">你可能会创建用于确定管道体积的函数，如下所示：</span><span class="sxs-lookup"><span data-stu-id="11882-159">You could create functions that determine the volume of pipe as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

<span data-ttu-id="11882-160">然后，会根据需要提供附加参数，用来表示两个不同尺寸的管道的各种长度：</span><span class="sxs-lookup"><span data-stu-id="11882-160">You would then supply the additional argument as needed for various lengths of pipe of the two different sizes:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a><span data-ttu-id="11882-161">递归函数</span><span class="sxs-lookup"><span data-stu-id="11882-161">Recursive Functions</span></span>

<span data-ttu-id="11882-162">递归函数是调用自身的函数。</span><span class="sxs-lookup"><span data-stu-id="11882-162">*Recursive functions* are functions that call themselves.</span></span> <span data-ttu-id="11882-163">它们要求在指定 **let** 关键字之后指定 **rec** 关键字。</span><span class="sxs-lookup"><span data-stu-id="11882-163">They require that you specify the **rec** keyword following the **let** keyword.</span></span> <span data-ttu-id="11882-164">从函数的主体内调用递归函数与调用任何函数调用是一样的。</span><span class="sxs-lookup"><span data-stu-id="11882-164">Invoke the recursive function from within the body of the function just as you would invoke any function call.</span></span> <span data-ttu-id="11882-165">以下递归函数计算第 n 个斐波纳契数<sup></sup>。</span><span class="sxs-lookup"><span data-stu-id="11882-165">The following recursive function computes the *n*<sup>th</sup> Fibonacci number.</span></span> <span data-ttu-id="11882-166">斐波纳契数序列很早就为人所知，此序列中的每个连续的数字都是序列中前两个数字之和。</span><span class="sxs-lookup"><span data-stu-id="11882-166">The Fibonacci number sequence has been known since antiquity and is a sequence in which each successive number is the sum of the previous two numbers in the sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

<span data-ttu-id="11882-167">如果在编写递归函数时不细心或者不清楚一些特殊技术（例如累加器和延续的使用），则有些递归函数可能会造成执行效率低下或使程序堆栈溢出。</span><span class="sxs-lookup"><span data-stu-id="11882-167">Some recursive functions might overflow the program stack or perform inefficiently if you do not write them with care and with awareness of special techniques, such as the use of accumulators and continuations.</span></span>

## <a name="function-values"></a><span data-ttu-id="11882-168">函数值</span><span class="sxs-lookup"><span data-stu-id="11882-168">Function Values</span></span>

<span data-ttu-id="11882-169">在 F# 中，所有函数都被视为值；实际上，它们被称为“函数值”。</span><span class="sxs-lookup"><span data-stu-id="11882-169">In F#, all functions are considered values; in fact, they are known as *function values*.</span></span> <span data-ttu-id="11882-170">因为函数是值，所以它们可用作其他函数的参数，或在需要使用值的其他上下文中使用。</span><span class="sxs-lookup"><span data-stu-id="11882-170">Because functions are values, they can be used as arguments to other functions or in other contexts where values are used.</span></span> <span data-ttu-id="11882-171">下面是一个采用函数值作为参数的函数示例：</span><span class="sxs-lookup"><span data-stu-id="11882-171">Following is an example of a function that takes a function value as an argument:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

<span data-ttu-id="11882-172">可通过使用 `->` 标记来指定函数值的类型。</span><span class="sxs-lookup"><span data-stu-id="11882-172">You specify the type of a function value by using the `->` token.</span></span> <span data-ttu-id="11882-173">此标记的左边是参数的类型，右边是返回值。</span><span class="sxs-lookup"><span data-stu-id="11882-173">On the left side of this token is the type of the argument, and on the right side is the return value.</span></span> <span data-ttu-id="11882-174">在前面的示例中，`apply1` 是一个采用函数 `transform` 作为参数的函数，其中 `transform` 是一个采用整数并返回其他整数的函数。</span><span class="sxs-lookup"><span data-stu-id="11882-174">In the previous example, `apply1` is a function that takes a function `transform` as an argument, where `transform` is a function that takes an integer and returns another integer.</span></span> <span data-ttu-id="11882-175">下面的代码演示如何使用 `apply1`：</span><span class="sxs-lookup"><span data-stu-id="11882-175">The following code shows how to use `apply1`:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

<span data-ttu-id="11882-176">运行前面的代码之后，`result` 的值将为 101。</span><span class="sxs-lookup"><span data-stu-id="11882-176">The value of `result` will be 101 after the previous code runs.</span></span>

<span data-ttu-id="11882-177">多个参数之间由连续的 `->` 标记分隔，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="11882-177">Multiple arguments are separated by successive `->` tokens, as shown in the following example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

<span data-ttu-id="11882-178">结果是 200。</span><span class="sxs-lookup"><span data-stu-id="11882-178">The result is 200.</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="11882-179">Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="11882-179">Lambda Expressions</span></span>

<span data-ttu-id="11882-180">*lambda 表达式* 是未命名的函数。</span><span class="sxs-lookup"><span data-stu-id="11882-180">A *lambda expression* is an unnamed function.</span></span> <span data-ttu-id="11882-181">在上述示例中，可以不定义命名的函数 **increment** 和 **mul**，而使用如下的 lambda 表达式：</span><span class="sxs-lookup"><span data-stu-id="11882-181">In the previous examples, instead of defining named functions **increment** and **mul**, you could use lambda expressions as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

<span data-ttu-id="11882-182">可通过使用 `fun` 关键字来定义 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="11882-182">You define lambda expressions by using the `fun` keyword.</span></span> <span data-ttu-id="11882-183">lambda 表达式类似于函数定义，只不过使用了 `->` 标记将参数列表与函数体分隔，而不是使用 `=` 标记。</span><span class="sxs-lookup"><span data-stu-id="11882-183">A lambda expression resembles a function definition, except that instead of the `=` token, the `->` token is used to separate the argument list from the function body.</span></span> <span data-ttu-id="11882-184">与在常规函数定义中一样，可推断或显式指定参数类型，并且从主体中最后一个表达式的类型推断出 lambda 表达式的返回类型。</span><span class="sxs-lookup"><span data-stu-id="11882-184">As in a regular function definition, the argument types can be inferred or specified explicitly, and the return type of the lambda expression is inferred from the type of the last expression in the body.</span></span> <span data-ttu-id="11882-185">有关详细信息，请参阅 [Lambda 表达式：`fun` 关键字](lambda-expressions-the-fun-keyword.md)。</span><span class="sxs-lookup"><span data-stu-id="11882-185">For more information, see [Lambda Expressions: The `fun` Keyword](lambda-expressions-the-fun-keyword.md).</span></span>

## <a name="function-composition-and-pipelining"></a><span data-ttu-id="11882-186">函数组合和流水线处理</span><span class="sxs-lookup"><span data-stu-id="11882-186">Function Composition and Pipelining</span></span>

<span data-ttu-id="11882-187">F# 中的函数可由其他函数组合而成。</span><span class="sxs-lookup"><span data-stu-id="11882-187">Functions in F# can be composed from other functions.</span></span> <span data-ttu-id="11882-188">由 **function1** 和 **function2** 这两个函数组合而成的另一个函数表示先应用 **function1**，接着应用 **function2**：</span><span class="sxs-lookup"><span data-stu-id="11882-188">The composition of two functions **function1** and **function2** is another function that represents the application of **function1** followed the application of **function2**:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

<span data-ttu-id="11882-189">结果为 202。</span><span class="sxs-lookup"><span data-stu-id="11882-189">The result is 202.</span></span>

<span data-ttu-id="11882-190">流水线处理可让函数调用链接在一起形成连续的操作。</span><span class="sxs-lookup"><span data-stu-id="11882-190">Pipelining enables function calls to be chained together as successive operations.</span></span> <span data-ttu-id="11882-191">以下是流水线处理的工作方式：</span><span class="sxs-lookup"><span data-stu-id="11882-191">Pipelining works as follows:</span></span>

```fsharp
let result = 100 |> function1 |> function2
```

<span data-ttu-id="11882-192">结果再次为 202。</span><span class="sxs-lookup"><span data-stu-id="11882-192">The result is again 202.</span></span>

<span data-ttu-id="11882-193">组合运算符采用两个函数并返回一个函数；相反，流水线运算符采用一个函数和一个参数并返回一个值。</span><span class="sxs-lookup"><span data-stu-id="11882-193">The composition operators take two functions and return a function; by contrast, the pipeline operators take a function and an argument and return a value.</span></span> <span data-ttu-id="11882-194">下面的代码示例通过显示函数签名和用法的差异，指出了流水线运算符和组合运算符之间的区别。</span><span class="sxs-lookup"><span data-stu-id="11882-194">The following code example shows the difference between the pipeline and composition operators by showing the differences in the function signatures and usage.</span></span>

```fsharp
// Function composition and pipeline operators compared.

let addOne x = x + 1
let timesTwo x = 2 * x

// Composition operator
// ( >> ) : ('T1 -> 'T2) -> ('T2 -> 'T3) -> 'T1 -> 'T3
let Compose2 = addOne >> timesTwo

// Backward composition operator
// ( << ) : ('T2 -> 'T3) -> ('T1 -> 'T2) -> 'T1 -> 'T3
let Compose1 = addOne << timesTwo

// Result is 5
let result1 = Compose1 2

// Result is 6
let result2 = Compose2 2

// Pipelining
// Pipeline operator
// ( |> ) : 'T1 -> ('T1 -> 'U) -> 'U
let Pipeline2 x = addOne x |> timesTwo

// Backward pipeline operator
// ( <| ) : ('T -> 'U) -> 'T -> 'U
let Pipeline1 x = addOne <| timesTwo x

// Result is 5
let result3 = Pipeline1 2

// Result is 6
let result4 = Pipeline2 2
```

## <a name="overloading-functions"></a><span data-ttu-id="11882-195">重载函数</span><span class="sxs-lookup"><span data-stu-id="11882-195">Overloading Functions</span></span>

<span data-ttu-id="11882-196">可以重载类型（而非函数）的方法。</span><span class="sxs-lookup"><span data-stu-id="11882-196">You can overload methods of a type but not functions.</span></span> <span data-ttu-id="11882-197">有关详细信息，请参阅[方法](../members/methods.md)。</span><span class="sxs-lookup"><span data-stu-id="11882-197">For more information, see [Methods](../members/methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="11882-198">请参阅</span><span class="sxs-lookup"><span data-stu-id="11882-198">See also</span></span>

- [<span data-ttu-id="11882-199">值</span><span class="sxs-lookup"><span data-stu-id="11882-199">Values</span></span>](../values/index.md)
- [<span data-ttu-id="11882-200">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="11882-200">F# Language Reference</span></span>](../index.md)
