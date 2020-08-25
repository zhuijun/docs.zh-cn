---
title: 第一类函数
description: '了解第一类函数以及它们对于 F # 中的函数编程是非常重要的。'
ms.date: 10/29/2018
ms.openlocfilehash: 1dc8eae1655187282f05bf4e9501ecc8a17deba8
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810906"
---
# <a name="first-class-functions"></a><span data-ttu-id="8164f-103">第一类函数</span><span class="sxs-lookup"><span data-stu-id="8164f-103">First-class functions</span></span>

<span data-ttu-id="8164f-104">函数编程语言的一种定义特性是将函数提升为第一类状态。</span><span class="sxs-lookup"><span data-stu-id="8164f-104">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="8164f-105">您应该能够对使用其他内置类型的值的函数执行任何操作，并且能够以相当的工作量来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="8164f-105">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="8164f-106">第一类状态的典型度量值包括：</span><span class="sxs-lookup"><span data-stu-id="8164f-106">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="8164f-107">是否可以将函数绑定到标识符？</span><span class="sxs-lookup"><span data-stu-id="8164f-107">Can you bind functions to identifiers?</span></span> <span data-ttu-id="8164f-108">也就是说，可以为其指定名称吗？</span><span class="sxs-lookup"><span data-stu-id="8164f-108">That is, can you give them names?</span></span>

- <span data-ttu-id="8164f-109">能否在数据结构（如列表中）中存储函数？</span><span class="sxs-lookup"><span data-stu-id="8164f-109">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="8164f-110">是否可以在函数调用中将函数作为参数传递？</span><span class="sxs-lookup"><span data-stu-id="8164f-110">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="8164f-111">是否可以从函数调用返回函数？</span><span class="sxs-lookup"><span data-stu-id="8164f-111">Can you return a function from a function call?</span></span>

<span data-ttu-id="8164f-112">最后两个度量值定义了所谓的 *高阶运算* 或 *高阶函数*。</span><span class="sxs-lookup"><span data-stu-id="8164f-112">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="8164f-113">高阶函数接受函数作为参数，并返回函数作为函数调用的值。</span><span class="sxs-lookup"><span data-stu-id="8164f-113">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="8164f-114">这些操作支持将函数编程作为映射函数和函数的组合。</span><span class="sxs-lookup"><span data-stu-id="8164f-114">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>

## <a name="give-the-value-a-name"></a><span data-ttu-id="8164f-115">为值指定名称</span><span class="sxs-lookup"><span data-stu-id="8164f-115">Give the Value a Name</span></span>

<span data-ttu-id="8164f-116">如果函数是第一类值，则您必须能够命名它，就像您命名整数、字符串和其他内置类型一样。</span><span class="sxs-lookup"><span data-stu-id="8164f-116">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="8164f-117">这在函数编程文献中称为将标识符绑定到某个值。</span><span class="sxs-lookup"><span data-stu-id="8164f-117">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="8164f-118">F # 使用[ `let` 绑定](../language-reference/functions/let-bindings.md)将名称绑定到值： `let <identifier> = <value>` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-118">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="8164f-119">下面的代码演示了两个示例。</span><span class="sxs-lookup"><span data-stu-id="8164f-119">The following code shows two examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="8164f-120">您可以轻松地命名函数。</span><span class="sxs-lookup"><span data-stu-id="8164f-120">You can name a function just as easily.</span></span> <span data-ttu-id="8164f-121">下面的示例定义了一个名为的函数，该函数将 `squareIt` 标识符绑定 `squareIt` 到 [lambda 表达式](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-121">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="8164f-122">函数 `squareIt` 具有一个参数， `n` 并返回该参数的平方。</span><span class="sxs-lookup"><span data-stu-id="8164f-122">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="8164f-123">F # 提供了以下更简洁的语法，可实现相同的结果，并且键入内容更少。</span><span class="sxs-lookup"><span data-stu-id="8164f-123">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="8164f-124">下面的示例使用第一种样式 `let <function-name> = <lambda-expression>` 来强调函数声明和其他类型值的声明之间的相似之处。</span><span class="sxs-lookup"><span data-stu-id="8164f-124">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="8164f-125">但是，还可以用简洁的语法来编写所有命名函数。</span><span class="sxs-lookup"><span data-stu-id="8164f-125">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="8164f-126">其中的一些示例是以这两种方式编写的。</span><span class="sxs-lookup"><span data-stu-id="8164f-126">Some of the examples are written in both ways.</span></span>

## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="8164f-127">将值存储在数据结构中</span><span class="sxs-lookup"><span data-stu-id="8164f-127">Store the Value in a Data Structure</span></span>

<span data-ttu-id="8164f-128">第一类值可以存储在数据结构中。</span><span class="sxs-lookup"><span data-stu-id="8164f-128">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="8164f-129">下面的代码演示将值存储在列表和元组中的示例。</span><span class="sxs-lookup"><span data-stu-id="8164f-129">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="8164f-130">若要验证存储在元组中的函数名称实际上是否计算为函数，下面的示例使用 `fst` 和 `snd` 运算符从元组中提取第一个和第二个元素 `funAndArgTuple` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-130">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="8164f-131">元组中的第一个元素是 `squareIt` ，第二个元素是 `num` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-131">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="8164f-132">标识符 `num` 在前面的示例中绑定到整数10，这是函数的有效参数 `squareIt` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-132">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="8164f-133">第二个表达式将元组中的第一个元素应用到元组中的第二个元素： `squareIt num` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-133">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="8164f-134">同样， `num` 可以互换使用标识符和整数10，因此可以使用标识符 `squareIt` 和 lambda 表达式 `fun n -> n * n` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-134">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="8164f-135">将值作为参数传递</span><span class="sxs-lookup"><span data-stu-id="8164f-135">Pass the Value as an Argument</span></span>

<span data-ttu-id="8164f-136">如果某个值具有语言形式的第一类状态，则可以将其作为参数传递给函数。</span><span class="sxs-lookup"><span data-stu-id="8164f-136">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="8164f-137">例如，通常将整数和字符串作为参数传递。</span><span class="sxs-lookup"><span data-stu-id="8164f-137">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="8164f-138">下面的代码显示在 F # 中作为参数传递的整数和字符串。</span><span class="sxs-lookup"><span data-stu-id="8164f-138">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="8164f-139">如果函数具有一流状态，则您必须能够以相同的方式将它们作为参数传递。</span><span class="sxs-lookup"><span data-stu-id="8164f-139">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="8164f-140">请记住，这是高阶函数的第一个特征。</span><span class="sxs-lookup"><span data-stu-id="8164f-140">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="8164f-141">在下面的示例中，函数 `applyIt` 具有两个参数： `op` 和 `arg` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-141">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="8164f-142">如果在具有一个参数的函数中进行发送， `op` 并向提供函数的适当参数 `arg` ，则函数将返回应用到的结果 `op` `arg` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-142">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="8164f-143">在下面的示例中，函数参数和整数参数都是通过使用其名称以相同方式发送的。</span><span class="sxs-lookup"><span data-stu-id="8164f-143">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="8164f-144">将函数作为自变量发送到另一个函数的能力是在函数编程语言（例如映射或筛选器操作）中为常见的抽象。</span><span class="sxs-lookup"><span data-stu-id="8164f-144">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="8164f-145">例如，映射操作是一个高阶函数，该函数捕获逐句通过列表的函数所共享的计算，对每个元素执行一些操作，然后返回结果列表。</span><span class="sxs-lookup"><span data-stu-id="8164f-145">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="8164f-146">您可能想要在一个整数列表中递增每个元素，或在每个元素的后面递增，或将字符串列表中的每个元素更改为大写。</span><span class="sxs-lookup"><span data-stu-id="8164f-146">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="8164f-147">计算中易出错的部分是单步执行列表并生成要返回的结果列表的递归过程。</span><span class="sxs-lookup"><span data-stu-id="8164f-147">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="8164f-148">该部件在映射函数中捕获。</span><span class="sxs-lookup"><span data-stu-id="8164f-148">That part is captured in the mapping function.</span></span> <span data-ttu-id="8164f-149">对于特定应用程序，只需对每个列表元素应用一项功能， (添加、求平方、变化大小写) 。</span><span class="sxs-lookup"><span data-stu-id="8164f-149">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="8164f-150">该函数作为参数发送到 mapping 函数，就像 `squareIt` `applyIt` 在前面的示例中一样。</span><span class="sxs-lookup"><span data-stu-id="8164f-150">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="8164f-151">F # 为大多数集合类型（包括 [列表](../language-reference/lists.md)、 [数组](../language-reference/arrays.md)和 [序列](../language-reference/sequences.md)）提供映射方法。</span><span class="sxs-lookup"><span data-stu-id="8164f-151">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="8164f-152">下面的示例使用列表。</span><span class="sxs-lookup"><span data-stu-id="8164f-152">The following examples use lists.</span></span> <span data-ttu-id="8164f-153">语法为 `List.map <the function> <the list>`。</span><span class="sxs-lookup"><span data-stu-id="8164f-153">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="8164f-154">有关详细信息，请参阅 [列表](../language-reference/lists.md)。</span><span class="sxs-lookup"><span data-stu-id="8164f-154">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="8164f-155">从函数调用返回值</span><span class="sxs-lookup"><span data-stu-id="8164f-155">Return the Value from a Function Call</span></span>

<span data-ttu-id="8164f-156">最后，如果某个函数在某种语言中具有一流状态，则您必须能够将其作为函数调用的值返回，就像您返回其他类型（如整数和字符串）一样。</span><span class="sxs-lookup"><span data-stu-id="8164f-156">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="8164f-157">以下函数调用返回整数并显示它们。</span><span class="sxs-lookup"><span data-stu-id="8164f-157">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="8164f-158">以下函数调用返回一个字符串。</span><span class="sxs-lookup"><span data-stu-id="8164f-158">The following function call returns a string.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="8164f-159">以下函数调用（以内联方式声明）将返回一个布尔值。</span><span class="sxs-lookup"><span data-stu-id="8164f-159">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="8164f-160">显示的值为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-160">The value displayed is `True`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="8164f-161">将函数作为函数调用值返回的能力是高阶函数的第二个特征。</span><span class="sxs-lookup"><span data-stu-id="8164f-161">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="8164f-162">在下面的示例中， `checkFor` 将定义为一个函数，该函数采用一个参数， `item` 并返回一个新函数作为其值。</span><span class="sxs-lookup"><span data-stu-id="8164f-162">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="8164f-163">返回的函数采用列表作为其参数， `lst` 并在中进行搜索 `item` `lst` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-163">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="8164f-164">如果 `item` 存在，则该函数返回 `true` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-164">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="8164f-165">如果 `item` 不存在，则该函数将返回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-165">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="8164f-166">如上一节所示，以下代码使用提供的列表函数 [list](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists)，以搜索列表。</span><span class="sxs-lookup"><span data-stu-id="8164f-166">As in the previous section, the following code uses a provided list function, [List.exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists), to search the list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="8164f-167">下面的代码使用 `checkFor` 创建一个新函数，该函数采用一个自变量和一个列表，并在列表中搜索7。</span><span class="sxs-lookup"><span data-stu-id="8164f-167">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="8164f-168">下面的示例使用 F # 中函数的第一类状态声明一个函数，该函数 `compose` 返回两个函数参数的组合。</span><span class="sxs-lookup"><span data-stu-id="8164f-168">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet34.fs)]

> [!NOTE]
> <span data-ttu-id="8164f-169">对于更短的版本，请参阅下一节 "扩充函数"。</span><span class="sxs-lookup"><span data-stu-id="8164f-169">For an even shorter version, see the following section, "Curried Functions."</span></span>

<span data-ttu-id="8164f-170">下面的代码将两个函数作为自变量发送到 `compose` ，这两个函数都采用同一类型的单个自变量。</span><span class="sxs-lookup"><span data-stu-id="8164f-170">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="8164f-171">返回值是一个新函数，它是两个函数参数的组合。</span><span class="sxs-lookup"><span data-stu-id="8164f-171">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet35.fs)]

> [!NOTE]
> <span data-ttu-id="8164f-172">F # 提供了两个 `<<` `>>` 编写函数的运算符和。</span><span class="sxs-lookup"><span data-stu-id="8164f-172">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="8164f-173">例如， `let squareAndDouble2 = doubleIt << squareIt` `let squareAndDouble = compose doubleIt squareIt` 在前面的示例中，等效于。</span><span class="sxs-lookup"><span data-stu-id="8164f-173">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="8164f-174">以下用于将函数作为函数调用值返回的示例将创建一个简单的推测游戏。</span><span class="sxs-lookup"><span data-stu-id="8164f-174">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="8164f-175">若要创建游戏，请调用，并在中调用要将其 `makeGame` 发送到的某个值 `target` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-175">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="8164f-176">函数的返回值 `makeGame` 是一个函数，它采用一个自变量 (推测) 并报告推测是否正确。</span><span class="sxs-lookup"><span data-stu-id="8164f-176">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="8164f-177">下面的代码调用 `makeGame` ，并发送的 `7` 值 `target` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-177">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="8164f-178">标识符 `playGame` 绑定到返回的 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="8164f-178">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="8164f-179">因此，它 `playGame` 是一个函数，它将作为一个参数的值 `guess` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-179">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a><span data-ttu-id="8164f-180">扩充函数</span><span class="sxs-lookup"><span data-stu-id="8164f-180">Curried Functions</span></span>

<span data-ttu-id="8164f-181">可以通过使用 F # 函数声明中的隐式 *currying* ，将上一节中的许多示例编写得更简洁。</span><span class="sxs-lookup"><span data-stu-id="8164f-181">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="8164f-182">Currying 是将具有多个参数的函数转换为一系列嵌入函数的过程，其中每个函数都有一个参数。</span><span class="sxs-lookup"><span data-stu-id="8164f-182">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="8164f-183">在 F # 中，具有多个参数的函数在本质上是扩充的。</span><span class="sxs-lookup"><span data-stu-id="8164f-183">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="8164f-184">例如， `compose` 可以按照下面的简洁样式中所示，用三个参数来编写上述部分。</span><span class="sxs-lookup"><span data-stu-id="8164f-184">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="8164f-185">但是，结果是一个参数的函数，该函数返回一个参数的函数，该函数反过来返回一个参数的另一个函数，如中所示 `compose4curried` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-185">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="8164f-186">可以通过多种方式访问此函数。</span><span class="sxs-lookup"><span data-stu-id="8164f-186">You can access this function in several ways.</span></span> <span data-ttu-id="8164f-187">下面的每个示例都返回并显示18。</span><span class="sxs-lookup"><span data-stu-id="8164f-187">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="8164f-188">您可以 `compose4` `compose4curried` 在任何示例中将替换为。</span><span class="sxs-lookup"><span data-stu-id="8164f-188">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="8164f-189">若要验证函数是否仍像以前一样工作，请再次尝试原始测试用例。</span><span class="sxs-lookup"><span data-stu-id="8164f-189">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet41.fs)]

> [!NOTE]
> <span data-ttu-id="8164f-190">可以通过在元组中包含参数来限制 currying。</span><span class="sxs-lookup"><span data-stu-id="8164f-190">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="8164f-191">有关详细信息，请参阅 [参数和参数](../language-reference/parameters-and-arguments.md)中的 "参数模式"。</span><span class="sxs-lookup"><span data-stu-id="8164f-191">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="8164f-192">下面的示例使用隐式 currying 来编写较短的版本 `makeGame` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-192">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="8164f-193">`makeGame`在此格式中，构造和返回函数的方式的详细信息 `game` 不太明确，但你可以使用结果相同的原始测试用例进行验证。</span><span class="sxs-lookup"><span data-stu-id="8164f-193">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="8164f-194">有关 currying 的详细信息，请参阅 [函数](../language-reference/functions/index.md)中的 "参数的部分应用"。</span><span class="sxs-lookup"><span data-stu-id="8164f-194">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>

## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="8164f-195">标识符和函数定义可互换</span><span class="sxs-lookup"><span data-stu-id="8164f-195">Identifier and Function Definition Are Interchangeable</span></span>

<span data-ttu-id="8164f-196">`num`前面的示例中的变量名的计算结果为整数10，并且在其中有效的情况 `num` 下，也是很奇怪的，10也是有效的。</span><span class="sxs-lookup"><span data-stu-id="8164f-196">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="8164f-197">函数标识符及其值也是如此：任何位置都可以使用函数的名称，可以使用它绑定到的 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="8164f-197">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="8164f-198">下面的示例定义了一个名为的 `Boolean` 函数 `isNegative` ，然后使用函数的名称和函数的定义。</span><span class="sxs-lookup"><span data-stu-id="8164f-198">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="8164f-199">接下来的三个示例都返回并显示 `False` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-199">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="8164f-200">若要进一步执行此操作，请将 `applyIt` 绑定到的值替换为 `applyIt` 。</span><span class="sxs-lookup"><span data-stu-id="8164f-200">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="8164f-201">函数是 F 中的第一类值\#</span><span class="sxs-lookup"><span data-stu-id="8164f-201">Functions Are First-Class Values in F\#</span></span>

<span data-ttu-id="8164f-202">前面几节中的示例演示 F # 中的函数满足 F # 中作为第一类值的条件：</span><span class="sxs-lookup"><span data-stu-id="8164f-202">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="8164f-203">可以将标识符绑定到函数定义。</span><span class="sxs-lookup"><span data-stu-id="8164f-203">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="8164f-204">您可以将函数存储在数据结构中。</span><span class="sxs-lookup"><span data-stu-id="8164f-204">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="8164f-205">可以将函数作为自变量传递。</span><span class="sxs-lookup"><span data-stu-id="8164f-205">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="8164f-206">您可以返回函数作为函数调用的值。</span><span class="sxs-lookup"><span data-stu-id="8164f-206">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="8164f-207">有关 F # 的详细信息，请参阅 [f # 语言参考](../language-reference/index.md)。</span><span class="sxs-lookup"><span data-stu-id="8164f-207">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="8164f-208">示例</span><span class="sxs-lookup"><span data-stu-id="8164f-208">Example</span></span>

### <a name="description"></a><span data-ttu-id="8164f-209">说明</span><span class="sxs-lookup"><span data-stu-id="8164f-209">Description</span></span>

<span data-ttu-id="8164f-210">下面的代码包含本主题中的所有示例。</span><span class="sxs-lookup"><span data-stu-id="8164f-210">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="8164f-211">代码</span><span class="sxs-lookup"><span data-stu-id="8164f-211">Code</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a><span data-ttu-id="8164f-212">请参阅</span><span class="sxs-lookup"><span data-stu-id="8164f-212">See also</span></span>

- [<span data-ttu-id="8164f-213">列表</span><span class="sxs-lookup"><span data-stu-id="8164f-213">Lists</span></span>](../language-reference/lists.md)
- [<span data-ttu-id="8164f-214">元组</span><span class="sxs-lookup"><span data-stu-id="8164f-214">Tuples</span></span>](../language-reference/tuples.md)
- [<span data-ttu-id="8164f-215">函数</span><span class="sxs-lookup"><span data-stu-id="8164f-215">Functions</span></span>](../language-reference/functions/index.md)
- [<span data-ttu-id="8164f-216">`let` 绑定</span><span class="sxs-lookup"><span data-stu-id="8164f-216">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)
- [<span data-ttu-id="8164f-217">Lambda 表达式： `fun` 关键字</span><span class="sxs-lookup"><span data-stu-id="8164f-217">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)
