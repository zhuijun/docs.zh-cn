---
title: 形参和实参
description: '了解 F # 语言支持，用于定义参数和将参数传递给函数、方法和属性。'
ms.date: 08/15/2020
ms.openlocfilehash: 6564fd31105427683af8fc6280672e638737e9b5
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811517"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="e461e-103">形参和实参</span><span class="sxs-lookup"><span data-stu-id="e461e-103">Parameters and Arguments</span></span>

<span data-ttu-id="e461e-104">本主题介绍用于定义参数和将参数传递给函数、方法和属性的语言支持。</span><span class="sxs-lookup"><span data-stu-id="e461e-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="e461e-105">它包括有关如何按引用传递的信息，以及如何定义和使用可采用可变数量的自变量的方法。</span><span class="sxs-lookup"><span data-stu-id="e461e-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="e461e-106">形参和实参</span><span class="sxs-lookup"><span data-stu-id="e461e-106">Parameters and Arguments</span></span>

<span data-ttu-id="e461e-107">术语 *参数* 用于描述应提供的值的名称。</span><span class="sxs-lookup"><span data-stu-id="e461e-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="e461e-108">术语 *参数* 用于为每个参数提供的值。</span><span class="sxs-lookup"><span data-stu-id="e461e-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="e461e-109">参数可以在元组或扩充形式中指定，也可以在这两者的某种组合中指定。</span><span class="sxs-lookup"><span data-stu-id="e461e-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="e461e-110">可以通过使用显式参数名传递参数。</span><span class="sxs-lookup"><span data-stu-id="e461e-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="e461e-111">可以将方法的参数指定为 optional，并为其指定默认值。</span><span class="sxs-lookup"><span data-stu-id="e461e-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="e461e-112">参数模式</span><span class="sxs-lookup"><span data-stu-id="e461e-112">Parameter Patterns</span></span>

<span data-ttu-id="e461e-113">通常情况下，提供给函数和方法的参数是由空格分隔的模式。</span><span class="sxs-lookup"><span data-stu-id="e461e-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="e461e-114">这意味着，可以在函数或成员的参数列表中使用 [Match 表达式](match-expressions.md) 中所述的任何模式。</span><span class="sxs-lookup"><span data-stu-id="e461e-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="e461e-115">方法通常使用元组形式传递参数。</span><span class="sxs-lookup"><span data-stu-id="e461e-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="e461e-116">这可以从其他 .NET 语言的角度获得更清晰的结果，因为元组格式与在 .NET 方法中传递参数的方式匹配。</span><span class="sxs-lookup"><span data-stu-id="e461e-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="e461e-117">扩充形式最常用于使用绑定创建的函数 `let` 。</span><span class="sxs-lookup"><span data-stu-id="e461e-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="e461e-118">以下伪代码显示了元组和扩充参数的示例。</span><span class="sxs-lookup"><span data-stu-id="e461e-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="e461e-119">当某些参数在元组中时，可能会组合窗体，而有些参数则可能不存在。</span><span class="sxs-lookup"><span data-stu-id="e461e-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="e461e-120">其他模式也可用于参数列表中，但如果参数模式与所有可能的输入都不匹配，则在运行时可能会出现不完整的匹配项。</span><span class="sxs-lookup"><span data-stu-id="e461e-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="e461e-121">`MatchFailureException`当参数的值与参数列表中指定的模式不匹配时，将生成异常。</span><span class="sxs-lookup"><span data-stu-id="e461e-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="e461e-122">当参数模式允许不完全匹配时，编译器会发出警告。</span><span class="sxs-lookup"><span data-stu-id="e461e-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="e461e-123">至少一个其他模式对于参数列表通常很有用，这是通配符模式。</span><span class="sxs-lookup"><span data-stu-id="e461e-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="e461e-124">如果只想忽略提供的任何参数，请在参数列表中使用通配符模式。</span><span class="sxs-lookup"><span data-stu-id="e461e-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="e461e-125">下面的代码说明了参数列表中通配符模式的用法。</span><span class="sxs-lookup"><span data-stu-id="e461e-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="e461e-126">如果不需要传入的参数（例如，在程序的主入口点中）对通常作为字符串数组提供的命令行参数感兴趣，则可以使用通配符模式，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="e461e-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="e461e-127">有时在参数中使用的其他模式是 `as` 模式，以及与可区分的联合和活动模式关联的标识符模式。</span><span class="sxs-lookup"><span data-stu-id="e461e-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="e461e-128">可以按如下所示使用单用例可区分联合模式。</span><span class="sxs-lookup"><span data-stu-id="e461e-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="e461e-129">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="e461e-129">The output is as follows.</span></span>

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="e461e-130">活动模式可用作参数，例如，将参数转换为所需格式时，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="e461e-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="e461e-131">您可以使用 `as` 模式将匹配的值存储为本地值，如下面的代码行所示。</span><span class="sxs-lookup"><span data-stu-id="e461e-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="e461e-132">偶尔使用的另一种模式是将未命名的最后一个参数作为函数的主体提供，该函数可立即对隐式参数执行模式匹配。</span><span class="sxs-lookup"><span data-stu-id="e461e-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="e461e-133">下面的代码行就是一个示例。</span><span class="sxs-lookup"><span data-stu-id="e461e-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="e461e-134">此代码定义一个函数，该函数采用泛型列表， `true` 如果列表为空，则返回， `false` 否则返回。</span><span class="sxs-lookup"><span data-stu-id="e461e-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="e461e-135">使用此类技术会使代码更难以阅读。</span><span class="sxs-lookup"><span data-stu-id="e461e-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="e461e-136">偶尔，涉及不完整匹配的模式非常有用，例如，如果您知道程序中的列表只有三个元素，则可以在参数列表中使用如下所示的模式。</span><span class="sxs-lookup"><span data-stu-id="e461e-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="e461e-137">使用不完整匹配的模式最适合用于快速原型和其他临时用途。</span><span class="sxs-lookup"><span data-stu-id="e461e-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="e461e-138">编译器将为此类代码发出警告。</span><span class="sxs-lookup"><span data-stu-id="e461e-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="e461e-139">此类模式无法涵盖所有可能输入的常规情况，因此不适合用于组件 Api。</span><span class="sxs-lookup"><span data-stu-id="e461e-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="e461e-140">命名实参</span><span class="sxs-lookup"><span data-stu-id="e461e-140">Named Arguments</span></span>

<span data-ttu-id="e461e-141">可以通过以逗号分隔的参数列表中的位置指定方法的参数，也可以通过提供名称，后跟一个等号和要传入的值，来以显式方式将方法传递给方法。</span><span class="sxs-lookup"><span data-stu-id="e461e-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="e461e-142">如果通过提供名称指定，它们的显示顺序可能与声明中使用的顺序不同。</span><span class="sxs-lookup"><span data-stu-id="e461e-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="e461e-143">命名参数可以使代码更具可读性，更好地适应 API 中某些类型的更改，如方法参数的重新排序。</span><span class="sxs-lookup"><span data-stu-id="e461e-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="e461e-144">命名参数只允许用于方法，不允许用于 `let` 绑定函数、函数值或 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="e461e-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="e461e-145">下面的代码示例演示如何使用命名参数。</span><span class="sxs-lookup"><span data-stu-id="e461e-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="e461e-146">在对类构造函数的调用中，可以通过使用类似于命名参数的语法来设置类的属性值。</span><span class="sxs-lookup"><span data-stu-id="e461e-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="e461e-147">下面的示例演示了此语法。</span><span class="sxs-lookup"><span data-stu-id="e461e-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="e461e-148">有关详细信息，请参阅 [构造函数 (F # ) ](members/constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="e461e-148">For more information, see [Constructors (F#)](members/constructors.md).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="e461e-149">可选参数</span><span class="sxs-lookup"><span data-stu-id="e461e-149">Optional Parameters</span></span>

<span data-ttu-id="e461e-150">可以通过在参数名称前面使用问号来指定方法的可选参数。</span><span class="sxs-lookup"><span data-stu-id="e461e-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="e461e-151">可选参数被解释为 F # 选项类型，因此，您可以通过使用带有和的表达式，以查询选项类型的常规方式查询它们 `match` `Some` `None` 。</span><span class="sxs-lookup"><span data-stu-id="e461e-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="e461e-152">仅允许在成员上使用可选参数，而不允许使用绑定创建的函数 `let` 。</span><span class="sxs-lookup"><span data-stu-id="e461e-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="e461e-153">可以按参数名称（如或）将现有可选值传递给 `?arg=None` 方法 `?arg=Some(3)` `?arg=arg` 。</span><span class="sxs-lookup"><span data-stu-id="e461e-153">You can pass existing optional values to method by parameter name, such as `?arg=None` or `?arg=Some(3)` or `?arg=arg`.</span></span> <span data-ttu-id="e461e-154">这在生成将可选自变量传递给其他方法的方法时非常有用。</span><span class="sxs-lookup"><span data-stu-id="e461e-154">This can be useful when building a method that passes optional arguments to another method.</span></span>

<span data-ttu-id="e461e-155">还可以使用函数来 `defaultArg` 设置可选参数的默认值。</span><span class="sxs-lookup"><span data-stu-id="e461e-155">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="e461e-156">`defaultArg`函数采用可选参数作为第一个参数，将默认值作为第二个参数。</span><span class="sxs-lookup"><span data-stu-id="e461e-156">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="e461e-157">下面的示例阐释了可选参数的用法。</span><span class="sxs-lookup"><span data-stu-id="e461e-157">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="e461e-158">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="e461e-158">The output is as follows.</span></span>

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

<span data-ttu-id="e461e-159">出于 c # 和 Visual Basic 互操作的目的 `[<Optional; DefaultParameterValue<(...)>]` ，可以在 F # 中使用属性，以便调用方将参数显示为可选。</span><span class="sxs-lookup"><span data-stu-id="e461e-159">For the purposes of C# and Visual Basic interop you can use the attributes `[<Optional; DefaultParameterValue<(...)>]` in F#, so that callers will see an argument as optional.</span></span> <span data-ttu-id="e461e-160">这相当于在 c # 中将参数定义为可选，如中所示 `MyMethod(int i = 3)` 。</span><span class="sxs-lookup"><span data-stu-id="e461e-160">This is equivalent to defining the argument as optional in C# as in `MyMethod(int i = 3)`.</span></span>

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

<span data-ttu-id="e461e-161">你还可以将新的对象指定为默认参数值。</span><span class="sxs-lookup"><span data-stu-id="e461e-161">You can also specify a new object as a default parameter value.</span></span> <span data-ttu-id="e461e-162">例如， `Foo` 成员可以将可选 `CancellationToken` 作为输入：</span><span class="sxs-lookup"><span data-stu-id="e461e-162">For example, the `Foo` member could have an optional `CancellationToken` as input instead:</span></span>

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

<span data-ttu-id="e461e-163">作为的参数提供的值 `DefaultParameterValue` 必须与参数的类型匹配。</span><span class="sxs-lookup"><span data-stu-id="e461e-163">The value given as argument to `DefaultParameterValue` must match the type of the parameter.</span></span> <span data-ttu-id="e461e-164">例如，不允许使用以下项：</span><span class="sxs-lookup"><span data-stu-id="e461e-164">For example, the following is not allowed:</span></span>

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

<span data-ttu-id="e461e-165">在这种情况下，编译器将生成警告，并将完全忽略这两个特性。</span><span class="sxs-lookup"><span data-stu-id="e461e-165">In this case, the compiler generates a warning and will ignore both attributes altogether.</span></span> <span data-ttu-id="e461e-166">请注意，默认值 `null` 需要为类型批注，否则编译器将推断错误的类型，即 `[<Optional; DefaultParameterValue(null:obj)>] o:obj` 。</span><span class="sxs-lookup"><span data-stu-id="e461e-166">Note that the default value `null` needs to be type-annotated, as otherwise the compiler infers the wrong type, i.e. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span></span>

## <a name="passing-by-reference"></a><span data-ttu-id="e461e-167">按引用传递</span><span class="sxs-lookup"><span data-stu-id="e461e-167">Passing by Reference</span></span>

<span data-ttu-id="e461e-168">按引用传递 F # 值涉及 [byref](byrefs.md)，这是托管指针类型。</span><span class="sxs-lookup"><span data-stu-id="e461e-168">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="e461e-169">使用哪种类型的指南如下：</span><span class="sxs-lookup"><span data-stu-id="e461e-169">Guidance for which type to use is as follows:</span></span>

- <span data-ttu-id="e461e-170">`inref<'T>`如果只需要读取指针，请使用。</span><span class="sxs-lookup"><span data-stu-id="e461e-170">Use `inref<'T>` if you only need to read the pointer.</span></span>
- <span data-ttu-id="e461e-171">`outref<'T>`如果只需要写入指针，请使用。</span><span class="sxs-lookup"><span data-stu-id="e461e-171">Use `outref<'T>` if you only need to write to the pointer.</span></span>
- <span data-ttu-id="e461e-172">`byref<'T>`如果需要读取和写入指针，请使用。</span><span class="sxs-lookup"><span data-stu-id="e461e-172">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

let test () =
    // No need to make it mutable, since it's read-only
    let x = 1
    example1 &x

    // Needs to be mutable, since we write to it
    let mutable y = 2
    example2 &y
    example3 &y // Now 'y' is 3
```

<span data-ttu-id="e461e-173">由于参数是一个指针，并且值是可变的，因此在执行函数后将保留对值所做的任何更改。</span><span class="sxs-lookup"><span data-stu-id="e461e-173">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="e461e-174">您可以使用元组作为返回值，以 `out` 在 .net 库方法中存储任何参数。</span><span class="sxs-lookup"><span data-stu-id="e461e-174">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="e461e-175">或者，您可以将 `out` 参数视为 `byref` 参数。</span><span class="sxs-lookup"><span data-stu-id="e461e-175">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="e461e-176">下面的代码示例演示了这两种方法。</span><span class="sxs-lookup"><span data-stu-id="e461e-176">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="e461e-177">参数数组</span><span class="sxs-lookup"><span data-stu-id="e461e-177">Parameter Arrays</span></span>

<span data-ttu-id="e461e-178">有时，有必要定义一个函数，该函数采用任意数量的异类类型的参数。</span><span class="sxs-lookup"><span data-stu-id="e461e-178">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="e461e-179">创建所有可能的重载方法以考虑可以使用的所有类型是不可行的。</span><span class="sxs-lookup"><span data-stu-id="e461e-179">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="e461e-180">.NET 实现通过参数数组功能为此类方法提供支持。</span><span class="sxs-lookup"><span data-stu-id="e461e-180">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="e461e-181">在其签名中采用参数数组的方法可以使用任意数量的参数提供。</span><span class="sxs-lookup"><span data-stu-id="e461e-181">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="e461e-182">参数放入数组中。</span><span class="sxs-lookup"><span data-stu-id="e461e-182">The parameters are put into an array.</span></span> <span data-ttu-id="e461e-183">数组元素的类型决定了可传递给函数的参数类型。</span><span class="sxs-lookup"><span data-stu-id="e461e-183">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="e461e-184">如果用 `System.Object` 作为元素类型定义参数数组，则客户端代码可以传递任何类型的值。</span><span class="sxs-lookup"><span data-stu-id="e461e-184">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="e461e-185">在 F # 中，只能在方法中定义参数数组。</span><span class="sxs-lookup"><span data-stu-id="e461e-185">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="e461e-186">它们不能用于独立函数或模块中定义的函数。</span><span class="sxs-lookup"><span data-stu-id="e461e-186">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="e461e-187">使用特性定义参数数组 `ParamArray` 。</span><span class="sxs-lookup"><span data-stu-id="e461e-187">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="e461e-188">`ParamArray`特性只能应用于最后一个参数。</span><span class="sxs-lookup"><span data-stu-id="e461e-188">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="e461e-189">下面的代码演示了如何在 F # 中调用采用参数数组的 .NET 方法和具有采用参数数组的方法的类型的定义。</span><span class="sxs-lookup"><span data-stu-id="e461e-189">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="e461e-190">在项目中运行时，上一代码的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="e461e-190">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="e461e-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e461e-191">See also</span></span>

- [<span data-ttu-id="e461e-192">成员</span><span class="sxs-lookup"><span data-stu-id="e461e-192">Members</span></span>](./members/index.md)
