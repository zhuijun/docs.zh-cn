---
title: 模式匹配
description: '了解如何在 F # 中使用模式，以便将数据与逻辑结构进行比较，将数据分解为各个构成部分，或从数据中提取信息。'
ms.date: 08/15/2020
ms.openlocfilehash: 6d284b941824bc15a8e872a4e28e22c0e159191d
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811504"
---
# <a name="pattern-matching"></a><span data-ttu-id="f47a6-103">模式匹配</span><span class="sxs-lookup"><span data-stu-id="f47a6-103">Pattern Matching</span></span>

<span data-ttu-id="f47a6-104">模式是用于转换输入数据的规则。</span><span class="sxs-lookup"><span data-stu-id="f47a6-104">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="f47a6-105">它们在整个 F # 语言中使用，以将数据与一个或多个逻辑结构进行比较，将数据分解为各个构成部分，或以各种方式从数据中提取信息。</span><span class="sxs-lookup"><span data-stu-id="f47a6-105">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>

## <a name="remarks"></a><span data-ttu-id="f47a6-106">注解</span><span class="sxs-lookup"><span data-stu-id="f47a6-106">Remarks</span></span>

<span data-ttu-id="f47a6-107">在许多语言构造（如表达式）中使用模式 `match` 。</span><span class="sxs-lookup"><span data-stu-id="f47a6-107">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="f47a6-108">当您处理 `let` 绑定、lambda 表达式和与表达式关联的异常处理程序中的函数的参数时，将使用这些参数 `try...with` 。</span><span class="sxs-lookup"><span data-stu-id="f47a6-108">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="f47a6-109">有关详细信息，请参阅 [Match 表达式](match-expressions.md)、 [let 绑定](./functions/let-bindings.md)、 [Lambda 表达式： `fun` 关键字](./functions/lambda-expressions-the-fun-keyword.md)和 [异常： `try...with` 表达式](./exception-handling/the-try-with-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="f47a6-109">For more information, see [Match Expressions](match-expressions.md), [let Bindings](./functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](./functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](./exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="f47a6-110">例如，在表达式中 `match` ，管道符号*pattern*后跟。</span><span class="sxs-lookup"><span data-stu-id="f47a6-110">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="f47a6-111">每个模式都充当以某种方式转换输入的规则。</span><span class="sxs-lookup"><span data-stu-id="f47a6-111">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="f47a6-112">在 `match` 表达式中，将依次检查每个模式，以查看输入数据是否与模式兼容。</span><span class="sxs-lookup"><span data-stu-id="f47a6-112">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="f47a6-113">如果找到匹配项，则执行结果表达式。</span><span class="sxs-lookup"><span data-stu-id="f47a6-113">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="f47a6-114">如果找不到匹配项，则测试下一个模式规则。</span><span class="sxs-lookup"><span data-stu-id="f47a6-114">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="f47a6-115">在[匹配表达式](match-expressions.md)中说明时，可选的 when*条件*部分。</span><span class="sxs-lookup"><span data-stu-id="f47a6-115">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="f47a6-116">下表显示了支持的模式。</span><span class="sxs-lookup"><span data-stu-id="f47a6-116">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="f47a6-117">在运行时，将按照表中列出的顺序针对以下每个模式对输入进行测试，并以递归方式应用模式：在代码中显示时，从第一个到最后一个，以及从左到右的每行模式。</span><span class="sxs-lookup"><span data-stu-id="f47a6-117">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="f47a6-118">名称</span><span class="sxs-lookup"><span data-stu-id="f47a6-118">Name</span></span>|<span data-ttu-id="f47a6-119">说明</span><span class="sxs-lookup"><span data-stu-id="f47a6-119">Description</span></span>|<span data-ttu-id="f47a6-120">示例</span><span class="sxs-lookup"><span data-stu-id="f47a6-120">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="f47a6-121">常量模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-121">Constant pattern</span></span>|<span data-ttu-id="f47a6-122">任何数值、字符或字符串文本、枚举常量或定义的文本标识符</span><span class="sxs-lookup"><span data-stu-id="f47a6-122">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="f47a6-123">`1.0`, `"test"`, `30`, `Color.Red`</span><span class="sxs-lookup"><span data-stu-id="f47a6-123">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="f47a6-124">标识符模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-124">Identifier pattern</span></span>|<span data-ttu-id="f47a6-125">可区分联合、异常标签或活动模式用例的 case 值</span><span class="sxs-lookup"><span data-stu-id="f47a6-125">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="f47a6-126">变量模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-126">Variable pattern</span></span>|<span data-ttu-id="f47a6-127">*identifier*</span><span class="sxs-lookup"><span data-stu-id="f47a6-127">*identifier*</span></span>|`a`|
|<span data-ttu-id="f47a6-128">`as` 化</span><span class="sxs-lookup"><span data-stu-id="f47a6-128">`as` pattern</span></span>|<span data-ttu-id="f47a6-129">作为*标识符*的*模式*</span><span class="sxs-lookup"><span data-stu-id="f47a6-129">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="f47a6-130">或模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-130">OR pattern</span></span>|<span data-ttu-id="f47a6-131">*pattern1* &#124; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="f47a6-131">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="f47a6-132">AND 模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-132">AND pattern</span></span>|<span data-ttu-id="f47a6-133">*pattern1* &amp;*pattern2*</span><span class="sxs-lookup"><span data-stu-id="f47a6-133">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="f47a6-134">缺点模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-134">Cons pattern</span></span>|<span data-ttu-id="f47a6-135">*标识符* ：： *list-标识符*</span><span class="sxs-lookup"><span data-stu-id="f47a6-135">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="f47a6-136">列表模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-136">List pattern</span></span>|<span data-ttu-id="f47a6-137">[ *pattern_1*; ...; *pattern_n* ]</span><span class="sxs-lookup"><span data-stu-id="f47a6-137">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="f47a6-138">数组模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-138">Array pattern</span></span>|<span data-ttu-id="f47a6-139">[&#124; *pattern_1*; ...; *pattern_n* &#124;]</span><span class="sxs-lookup"><span data-stu-id="f47a6-139">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="f47a6-140">带括号模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-140">Parenthesized pattern</span></span>|<span data-ttu-id="f47a6-141"> ( *模式* ) </span><span class="sxs-lookup"><span data-stu-id="f47a6-141">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="f47a6-142">元组模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-142">Tuple pattern</span></span>|<span data-ttu-id="f47a6-143"> ( *pattern_1*， *pattern_n* ) </span><span class="sxs-lookup"><span data-stu-id="f47a6-143">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="f47a6-144">记录模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-144">Record pattern</span></span>|<span data-ttu-id="f47a6-145">{ *identifier1*  = *pattern_1*;... ;*identifier_n*  = *pattern_n* }</span><span class="sxs-lookup"><span data-stu-id="f47a6-145">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="f47a6-146">通配符模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-146">Wildcard pattern</span></span>|<span data-ttu-id="f47a6-147">_</span><span class="sxs-lookup"><span data-stu-id="f47a6-147">_</span></span>|`_`|
|<span data-ttu-id="f47a6-148">模式与类型注释一起</span><span class="sxs-lookup"><span data-stu-id="f47a6-148">Pattern together with type annotation</span></span>|<span data-ttu-id="f47a6-149">*模式* ： *类型*</span><span class="sxs-lookup"><span data-stu-id="f47a6-149">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="f47a6-150">类型测试模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-150">Type test pattern</span></span>|<span data-ttu-id="f47a6-151">:?</span><span class="sxs-lookup"><span data-stu-id="f47a6-151">:?</span></span> <span data-ttu-id="f47a6-152">*类型* [作为 *标识符* ]</span><span class="sxs-lookup"><span data-stu-id="f47a6-152">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="f47a6-153">Null 模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-153">Null pattern</span></span>|<span data-ttu-id="f47a6-154">Null</span><span class="sxs-lookup"><span data-stu-id="f47a6-154">null</span></span>|`null`|

## <a name="constant-patterns"></a><span data-ttu-id="f47a6-155">常量模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-155">Constant Patterns</span></span>

<span data-ttu-id="f47a6-156">常量模式包括数值、字符和字符串文本、枚举常量 (包含) 的枚举类型名称。</span><span class="sxs-lookup"><span data-stu-id="f47a6-156">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="f47a6-157">只能将 `match` 具有恒定模式的表达式与其他语言的 case 语句进行比较。</span><span class="sxs-lookup"><span data-stu-id="f47a6-157">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="f47a6-158">如果值相等，则将输入与文本值进行比较并且模式匹配。</span><span class="sxs-lookup"><span data-stu-id="f47a6-158">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="f47a6-159">文本的类型必须与输入的类型兼容。</span><span class="sxs-lookup"><span data-stu-id="f47a6-159">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="f47a6-160">下面的示例演示如何使用文本模式，并且还使用变量模式和或模式。</span><span class="sxs-lookup"><span data-stu-id="f47a6-160">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="f47a6-161">文本模式的另一个示例是基于枚举常量的模式。</span><span class="sxs-lookup"><span data-stu-id="f47a6-161">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="f47a6-162">使用枚举常量时，必须指定枚举类型名称。</span><span class="sxs-lookup"><span data-stu-id="f47a6-162">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="f47a6-163">标识符模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-163">Identifier Patterns</span></span>

<span data-ttu-id="f47a6-164">如果模式是形成有效标识符的字符串，则标识符的形式决定了模式的匹配方式。</span><span class="sxs-lookup"><span data-stu-id="f47a6-164">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="f47a6-165">如果标识符的长度超过一个字符并且以大写字符开头，则编译器将尝试与标识符模式进行匹配。</span><span class="sxs-lookup"><span data-stu-id="f47a6-165">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="f47a6-166">此模式的标识符可以是用文本特性标记的值、可区分联合用例、异常标识符或活动模式用例。</span><span class="sxs-lookup"><span data-stu-id="f47a6-166">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="f47a6-167">如果未找到匹配的标识符，则匹配将失败，并且会将下一个模式规则（变量模式）与输入进行比较。</span><span class="sxs-lookup"><span data-stu-id="f47a6-167">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="f47a6-168">可区分联合模式可以是简单的命名事例，也可以具有值或包含多个值的元组。</span><span class="sxs-lookup"><span data-stu-id="f47a6-168">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="f47a6-169">如果有值，则必须指定值的标识符。</span><span class="sxs-lookup"><span data-stu-id="f47a6-169">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="f47a6-170">如果是元组，则必须为元组的每个元素提供一个带有标识符的元组模式，或为一个或多个命名联合字段提供字段名称的标识符。</span><span class="sxs-lookup"><span data-stu-id="f47a6-170">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="f47a6-171">有关示例，请参阅本节中的代码示例。</span><span class="sxs-lookup"><span data-stu-id="f47a6-171">See the code examples in this section for examples.</span></span>

<span data-ttu-id="f47a6-172">`option`类型是具有两个用例（和）的可区分联合 `Some` `None` 。</span><span class="sxs-lookup"><span data-stu-id="f47a6-172">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="f47a6-173">一个 (`Some`) 有一个值，但是另一个 (`None`) 只是一个命名的事例。</span><span class="sxs-lookup"><span data-stu-id="f47a6-173">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="f47a6-174">因此， `Some` 需要为与用例关联的值使用变量 `Some` ，但 `None` 必须单独出现。</span><span class="sxs-lookup"><span data-stu-id="f47a6-174">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="f47a6-175">在下面的代码中，将为变量 `var1` 提供通过匹配大小写获得的值 `Some` 。</span><span class="sxs-lookup"><span data-stu-id="f47a6-175">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="f47a6-176">在下面的示例中， `PersonName` 可区分联合包含字符串的混合和表示可能的名称形式的字符。</span><span class="sxs-lookup"><span data-stu-id="f47a6-176">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="f47a6-177">可区分联合的情况为 `FirstOnly` 、 `LastOnly` 和 `FirstLast` 。</span><span class="sxs-lookup"><span data-stu-id="f47a6-177">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="f47a6-178">对于具有命名字段的可区分联合，使用等号 (=) 提取命名字段的值。</span><span class="sxs-lookup"><span data-stu-id="f47a6-178">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="f47a6-179">例如，请考虑使用类似于下面的声明的可区分联合。</span><span class="sxs-lookup"><span data-stu-id="f47a6-179">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="f47a6-180">您可以使用模式匹配表达式中的命名字段，如下所示。</span><span class="sxs-lookup"><span data-stu-id="f47a6-180">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

<span data-ttu-id="f47a6-181">命名字段的使用是可选的，因此在前面的示例中， `Circle(r)` 和 `Circle(radius = r)` 具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="f47a6-181">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="f47a6-182">指定多个字段时，请使用分号 (; ) 作为分隔符。</span><span class="sxs-lookup"><span data-stu-id="f47a6-182">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```fsharp
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

<span data-ttu-id="f47a6-183">使用活动模式可以定义更复杂的自定义模式匹配。</span><span class="sxs-lookup"><span data-stu-id="f47a6-183">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="f47a6-184">有关活动模式的详细信息，请参阅 [活动模式](active-patterns.md)。</span><span class="sxs-lookup"><span data-stu-id="f47a6-184">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="f47a6-185">标识符为异常的情况在异常处理程序上下文的模式匹配中使用。</span><span class="sxs-lookup"><span data-stu-id="f47a6-185">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="f47a6-186">有关异常处理中的模式匹配的信息，请参阅 [异常： `try...with` 表达式](./exception-handling/the-try-with-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="f47a6-186">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](./exception-handling/the-try-with-expression.md).</span></span>

## <a name="variable-patterns"></a><span data-ttu-id="f47a6-187">变量模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-187">Variable Patterns</span></span>

<span data-ttu-id="f47a6-188">变量模式将匹配的值分配给一个变量名称，该变量可在符号右侧的执行表达式中使用 `->` 。</span><span class="sxs-lookup"><span data-stu-id="f47a6-188">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="f47a6-189">变量模式单独与任何输入匹配，但变量模式通常显示在其他模式内，因此可以将更复杂的结构（例如元组和数组）分解为变量。</span><span class="sxs-lookup"><span data-stu-id="f47a6-189">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="f47a6-190">下面的示例演示元组模式内的变量模式。</span><span class="sxs-lookup"><span data-stu-id="f47a6-190">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="f47a6-191">as 模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-191">as Pattern</span></span>

<span data-ttu-id="f47a6-192">`as`模式是一个附加了子句的模式 `as` 。</span><span class="sxs-lookup"><span data-stu-id="f47a6-192">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="f47a6-193">`as`子句将匹配的值绑定到可在表达式的执行表达式中使用的名称， `match` 或者，如果在绑定中使用此模式，则会将 `let` 该名称作为绑定添加到本地范围。</span><span class="sxs-lookup"><span data-stu-id="f47a6-193">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="f47a6-194">下面的示例使用 `as` 模式。</span><span class="sxs-lookup"><span data-stu-id="f47a6-194">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="f47a6-195">或模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-195">OR Pattern</span></span>

<span data-ttu-id="f47a6-196">当输入数据可以匹配多个模式，并且您想要执行与结果相同的代码时，可以使用或模式。</span><span class="sxs-lookup"><span data-stu-id="f47a6-196">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="f47a6-197">或模式两边的类型必须兼容。</span><span class="sxs-lookup"><span data-stu-id="f47a6-197">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="f47a6-198">下面的示例演示了或模式。</span><span class="sxs-lookup"><span data-stu-id="f47a6-198">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="f47a6-199">AND 模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-199">AND Pattern</span></span>

<span data-ttu-id="f47a6-200">和模式要求输入匹配两种模式。</span><span class="sxs-lookup"><span data-stu-id="f47a6-200">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="f47a6-201">和模式两边的类型必须兼容。</span><span class="sxs-lookup"><span data-stu-id="f47a6-201">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="f47a6-202">下面的示例类似于 `detectZeroTuple` 本主题后面的元组模式部分中所示的示例，但这两个 `var1` 和 `var2` 都是使用和模式作为值获取的。</span><span class="sxs-lookup"><span data-stu-id="f47a6-202">The following example is like `detectZeroTuple` shown in the Tuple Pattern section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="f47a6-203">缺点模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-203">Cons Pattern</span></span>

<span data-ttu-id="f47a6-204">缺点模式用于将列表分解为第一个元素、 *头*以及包含剩余元素（ *尾部*）的列表。</span><span class="sxs-lookup"><span data-stu-id="f47a6-204">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="f47a6-205">列表模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-205">List Pattern</span></span>

<span data-ttu-id="f47a6-206">列表模式使列表可分解为多个元素。</span><span class="sxs-lookup"><span data-stu-id="f47a6-206">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="f47a6-207">列表模式本身只能匹配特定数量的元素的列表。</span><span class="sxs-lookup"><span data-stu-id="f47a6-207">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="f47a6-208">数组模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-208">Array Pattern</span></span>

<span data-ttu-id="f47a6-209">数组模式类似于列表模式，可用于分解特定长度的数组。</span><span class="sxs-lookup"><span data-stu-id="f47a6-209">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="f47a6-210">带括号模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-210">Parenthesized Pattern</span></span>

<span data-ttu-id="f47a6-211">括号可以围绕模式分组，以实现所需的关联性。</span><span class="sxs-lookup"><span data-stu-id="f47a6-211">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="f47a6-212">在下面的示例中，括号用于控制和模式与缺点模式之间的相关性。</span><span class="sxs-lookup"><span data-stu-id="f47a6-212">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="f47a6-213">元组模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-213">Tuple Pattern</span></span>

<span data-ttu-id="f47a6-214">元组模式与元组格式的输入匹配，并通过对元组中的每个位置使用模式匹配变量，将元组分解为其构成元素。</span><span class="sxs-lookup"><span data-stu-id="f47a6-214">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="f47a6-215">下面的示例演示元组模式，还使用文本模式、变量模式和通配符模式。</span><span class="sxs-lookup"><span data-stu-id="f47a6-215">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="f47a6-216">记录模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-216">Record Pattern</span></span>

<span data-ttu-id="f47a6-217">记录模式用于分解记录，以便提取字段的值。</span><span class="sxs-lookup"><span data-stu-id="f47a6-217">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="f47a6-218">模式不必引用记录的所有字段;所有省略的字段不会参与匹配，也不会被提取。</span><span class="sxs-lookup"><span data-stu-id="f47a6-218">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="f47a6-219">通配符模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-219">Wildcard Pattern</span></span>

<span data-ttu-id="f47a6-220">通配符模式由下划线 () 字符表示， `_` 并与变量模式相同，只是丢弃输入，而不是分配给变量。</span><span class="sxs-lookup"><span data-stu-id="f47a6-220">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="f47a6-221">通配符模式通常用在其他模式内作为值的占位符，而在该符号右侧的表达式中不需要这些值 `->` 。</span><span class="sxs-lookup"><span data-stu-id="f47a6-221">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="f47a6-222">通配符模式还经常用于模式列表的末尾，以匹配任何不匹配的输入。</span><span class="sxs-lookup"><span data-stu-id="f47a6-222">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="f47a6-223">本主题中的许多代码示例演示了通配符模式。</span><span class="sxs-lookup"><span data-stu-id="f47a6-223">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="f47a6-224">有关示例，请参阅前面的代码。</span><span class="sxs-lookup"><span data-stu-id="f47a6-224">See the preceding code for one example.</span></span>

## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="f47a6-225">具有类型批注的模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-225">Patterns That Have Type Annotations</span></span>

<span data-ttu-id="f47a6-226">模式可以具有类型批注。</span><span class="sxs-lookup"><span data-stu-id="f47a6-226">Patterns can have type annotations.</span></span> <span data-ttu-id="f47a6-227">它们的行为与其他类型注释和其他类型注释类似。</span><span class="sxs-lookup"><span data-stu-id="f47a6-227">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="f47a6-228">在模式中的类型批注前后需要括号。</span><span class="sxs-lookup"><span data-stu-id="f47a6-228">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="f47a6-229">下面的代码演示具有类型批注的模式。</span><span class="sxs-lookup"><span data-stu-id="f47a6-229">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="f47a6-230">类型测试模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-230">Type Test Pattern</span></span>

<span data-ttu-id="f47a6-231">类型测试模式用于将输入与类型进行匹配。</span><span class="sxs-lookup"><span data-stu-id="f47a6-231">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="f47a6-232">如果输入类型与在模式中指定的类型) 的 (或派生类型匹配，则匹配成功。</span><span class="sxs-lookup"><span data-stu-id="f47a6-232">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="f47a6-233">下面的示例演示了类型测试模式。</span><span class="sxs-lookup"><span data-stu-id="f47a6-233">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

<span data-ttu-id="f47a6-234">如果只检查标识符是否为特定的派生类型，则不需要 `as identifier` 模式的一部分，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="f47a6-234">If you're only checking if an identifier is of a particular derived type, you don't need the `as identifier` part of the pattern, as shown in the following example:</span></span>

```fsharp
type A() = class end
type B() = inherit A()
type C() = inherit A()

let m (a: A) =
    match a with
    | :? B -> printfn "It's a B"
    | :? C -> printfn "It's a C"
    | _ -> ()
```

## <a name="null-pattern"></a><span data-ttu-id="f47a6-235">Null 模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-235">Null Pattern</span></span>

<span data-ttu-id="f47a6-236">Null 模式匹配可以在使用允许 null 值的类型时显示的 null 值。</span><span class="sxs-lookup"><span data-stu-id="f47a6-236">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="f47a6-237">与 .NET Framework 代码互操作时，经常使用 Null 模式。</span><span class="sxs-lookup"><span data-stu-id="f47a6-237">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="f47a6-238">例如，.NET API 的返回值可能是表达式的输入 `match` 。</span><span class="sxs-lookup"><span data-stu-id="f47a6-238">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="f47a6-239">您可以根据返回值是否为 null 以及返回值的其他特征来控制程序流。</span><span class="sxs-lookup"><span data-stu-id="f47a6-239">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="f47a6-240">可以使用 null 模式来防止空值传播到程序的其余部分。</span><span class="sxs-lookup"><span data-stu-id="f47a6-240">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="f47a6-241">下面的示例使用 null 模式和变量模式。</span><span class="sxs-lookup"><span data-stu-id="f47a6-241">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a><span data-ttu-id="f47a6-242">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f47a6-242">See also</span></span>

- [<span data-ttu-id="f47a6-243">Match 表达式</span><span class="sxs-lookup"><span data-stu-id="f47a6-243">Match Expressions</span></span>](match-expressions.md)
- [<span data-ttu-id="f47a6-244">活动模式</span><span class="sxs-lookup"><span data-stu-id="f47a6-244">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="f47a6-245">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="f47a6-245">F# Language Reference</span></span>](index.md)
