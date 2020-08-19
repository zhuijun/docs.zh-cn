---
title: 运算符重载
description: '了解如何在 F # 中的类或记录类型和全局级别重载算术运算符。'
ms.date: 08/15/2020
ms.openlocfilehash: fb86ceb95101fcc1f157ec9ba17a9d8145b11a91
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557576"
---
# <a name="operator-overloading"></a><span data-ttu-id="29d77-103">运算符重载</span><span class="sxs-lookup"><span data-stu-id="29d77-103">Operator Overloading</span></span>

<span data-ttu-id="29d77-104">本主题介绍如何在类或记录类型以及全局级别重载算术运算符。</span><span class="sxs-lookup"><span data-stu-id="29d77-104">This topic describes how to overload arithmetic operators in a class or record type, and at the global level.</span></span>

## <a name="syntax"></a><span data-ttu-id="29d77-105">语法</span><span class="sxs-lookup"><span data-stu-id="29d77-105">Syntax</span></span>

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a><span data-ttu-id="29d77-106">备注</span><span class="sxs-lookup"><span data-stu-id="29d77-106">Remarks</span></span>

<span data-ttu-id="29d77-107">在前面的语法中， *运算符符号* 是 `+` 、、、、等之一 `-` `*` `/` `=` 。</span><span class="sxs-lookup"><span data-stu-id="29d77-107">In the previous syntax, the *operator-symbol* is one of `+`, `-`, `*`, `/`, `=`, and so on.</span></span> <span data-ttu-id="29d77-108">*参数列表*按操作数在该运算符的常用语法中出现的顺序指定它们。</span><span class="sxs-lookup"><span data-stu-id="29d77-108">The *parameter-list* specifies the operands in the order they appear in the usual syntax for that operator.</span></span> <span data-ttu-id="29d77-109">*方法体*构造生成的值。</span><span class="sxs-lookup"><span data-stu-id="29d77-109">The *method-body* constructs the resulting value.</span></span>

<span data-ttu-id="29d77-110">运算符的运算符重载必须是静态的。</span><span class="sxs-lookup"><span data-stu-id="29d77-110">Operator overloads for operators must be static.</span></span> <span data-ttu-id="29d77-111">一元运算符（如和）的运算符 `+` 重载 `-` 必须使用 `~` *运算符符号* 中的波形符 () ，以指示该运算符是一元运算符而不是二元运算符，如下面的声明所示。</span><span class="sxs-lookup"><span data-stu-id="29d77-111">Operator overloads for unary operators, such as `+` and `-`, must use a tilde (`~`) in the *operator-symbol* to indicate that the operator is a unary operator and not a binary operator, as shown in the following declaration.</span></span>

```fsharp
static member (~-) (v : Vector)
```

<span data-ttu-id="29d77-112">下面的代码演示一个仅包含两个运算符的矢量类，其中的一个运算符用于一元负运算，而另一个运算符用于标量乘法运算。</span><span class="sxs-lookup"><span data-stu-id="29d77-112">The following code illustrates a vector class that has just two operators, one for unary minus and one for multiplication by a scalar.</span></span> <span data-ttu-id="29d77-113">在此示例中，需要使用两种标量乘法重载，因为无论矢量和标量出现的顺序如何，运算符都必须有效。</span><span class="sxs-lookup"><span data-stu-id="29d77-113">In the example, two overloads for scalar multiplication are needed because the operator must work regardless of the order in which the vector and scalar appear.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a><span data-ttu-id="29d77-114">创建新运算符</span><span class="sxs-lookup"><span data-stu-id="29d77-114">Creating New Operators</span></span>

<span data-ttu-id="29d77-115">您可以重载所有标准运算符，但也可以创建新的运算符，而不是特定字符的序列。</span><span class="sxs-lookup"><span data-stu-id="29d77-115">You can overload all the standard operators, but you can also create new operators out of sequences of certain characters.</span></span> <span data-ttu-id="29d77-116">允许的运算符字符包括 `!` 、 `%` 、、 `&` `*` 、、 `+` 、 `-` `.` `/` `<` `=` `>` `?` `@` `^` `|` `~` 、、、、、、、、和。</span><span class="sxs-lookup"><span data-stu-id="29d77-116">Allowed operator characters are `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, and `~`.</span></span> <span data-ttu-id="29d77-117">该 `~` 字符具有使运算符成为一元运算符的特殊含义，并且不是运算符字符序列的一部分。</span><span class="sxs-lookup"><span data-stu-id="29d77-117">The `~` character has the special meaning of making an operator unary, and is not part of the operator character sequence.</span></span> <span data-ttu-id="29d77-118">并非所有运算符都可以成为一元运算符。</span><span class="sxs-lookup"><span data-stu-id="29d77-118">Not all operators can be made unary.</span></span>

<span data-ttu-id="29d77-119">根据所使用的确切字符顺序，运算符将具有一定优先级和相关性。</span><span class="sxs-lookup"><span data-stu-id="29d77-119">Depending on the exact character sequence you use, your operator will have a certain precedence and associativity.</span></span> <span data-ttu-id="29d77-120">结合性可以从左到右或从右到左，在具有相同优先级的运算符出现在不带括号的序列中时使用。</span><span class="sxs-lookup"><span data-stu-id="29d77-120">Associativity can be either left to right or right to left and is used whenever operators of the same level of precedence appear in sequence without parentheses.</span></span>

<span data-ttu-id="29d77-121">运算符字符不 `.` 会影响优先级，因此，例如，如果要定义自己的乘法，它具有与普通乘法相同的优先级和相关性，则可以创建等运算符 `.*` 。</span><span class="sxs-lookup"><span data-stu-id="29d77-121">The operator character `.` does not affect precedence, so that, for example, if you want to define your own version of multiplication that has the same precedence and associativity as ordinary multiplication, you could create operators such as `.*`.</span></span>

<span data-ttu-id="29d77-122">仅操作员 `?` 和 `?<-` 可以从开始 `?` 。</span><span class="sxs-lookup"><span data-stu-id="29d77-122">Only the operators `?` and `?<-` may start with `?`.</span></span>

<span data-ttu-id="29d77-123">可在 [符号和运算符引用](./symbol-and-operator-reference/index.md)中找到一个表，其中显示 F # 中所有运算符的优先级。</span><span class="sxs-lookup"><span data-stu-id="29d77-123">A table that shows the precedence of all operators in F# can be found in [Symbol and Operator Reference](./symbol-and-operator-reference/index.md).</span></span>

## <a name="overloaded-operator-names"></a><span data-ttu-id="29d77-124">重载运算符名称</span><span class="sxs-lookup"><span data-stu-id="29d77-124">Overloaded Operator Names</span></span>

<span data-ttu-id="29d77-125">当 F # 编译器编译运算符表达式时，它将生成一个方法，该方法具有该运算符的编译器生成的名称。</span><span class="sxs-lookup"><span data-stu-id="29d77-125">When the F# compiler compiles an operator expression, it generates a method that has a compiler-generated name for that operator.</span></span> <span data-ttu-id="29d77-126">这是在 Microsoft 中间语言 (MSIL) 为方法以及在反射和 IntelliSense 中显示的名称。</span><span class="sxs-lookup"><span data-stu-id="29d77-126">This is the name that appears in the Microsoft intermediate language (MSIL) for the method, and also in reflection and IntelliSense.</span></span> <span data-ttu-id="29d77-127">通常不需要在 F # 代码中使用这些名称。</span><span class="sxs-lookup"><span data-stu-id="29d77-127">You do not normally need to use these names in F# code.</span></span>

<span data-ttu-id="29d77-128">下表显示标准运算符及其对应的生成名称。</span><span class="sxs-lookup"><span data-stu-id="29d77-128">The following table shows the standard operators and their corresponding generated names.</span></span>

|<span data-ttu-id="29d77-129">运算符</span><span class="sxs-lookup"><span data-stu-id="29d77-129">Operator</span></span>|<span data-ttu-id="29d77-130">生成的名称</span><span class="sxs-lookup"><span data-stu-id="29d77-130">Generated name</span></span>|
|--------|--------------|
|`[]`|`op_Nil`|
|`::`|`op_Cons`|
|`+`|`op_Addition`|
|`-`|`op_Subtraction`|
|`*`|`op_Multiply`|
|`/`|`op_Division`|
|`@`|`op_Append`|
|`^`|`op_Concatenate`|
|`%`|`op_Modulus`|
|`&&&`|`op_BitwiseAnd`|
|<code>&#124;&#124;&#124;</code>|`op_BitwiseOr`|
|`^^^`|`op_ExclusiveOr`|
|`<<<`|`op_LeftShift`|
|`~~~`|`op_LogicalNot`|
|`>>>`|`op_RightShift`|
|`~+`|`op_UnaryPlus`|
|`~-`|`op_UnaryNegation`|
|`=`|`op_Equality`|
|`<=`|`op_LessThanOrEqual`|
|`>=`|`op_GreaterThanOrEqual`|
|`<`|`op_LessThan`|
|`>`|`op_GreaterThan`|
|`?`|`op_Dynamic`|
|`?<-`|`op_DynamicAssignment`|
|<code>&#124;></code>|`op_PipeRight`|
|<code><&#124;</code>|`op_PipeLeft`|
|`!`|`op_Dereference`|
|`>>`|`op_ComposeRight`|
|`<<`|`op_ComposeLeft`|
|`<@ @>`|`op_Quotation`|
|`<@@ @@>`|`op_QuotationUntyped`|
|`+=`|`op_AdditionAssignment`|
|`-=`|`op_SubtractionAssignment`|
|`*=`|`op_MultiplyAssignment`|
|`/=`|`op_DivisionAssignment`|
|`..`|`op_Range`|
|`.. ..`|`op_RangeStep`|

<span data-ttu-id="29d77-131">请注意， `not` F # 中的运算符不发出， `op_Inequality` 因为它不是符号运算符。</span><span class="sxs-lookup"><span data-stu-id="29d77-131">Note that the `not` operator in F# does not emit `op_Inequality` because it is not a symbolic operator.</span></span> <span data-ttu-id="29d77-132">它是发出对布尔表达式求反的 IL 的函数。</span><span class="sxs-lookup"><span data-stu-id="29d77-132">It is a function that emits IL that negates a boolean expression.</span></span>

<span data-ttu-id="29d77-133">此处未列出的运算符字符的其他组合可用作运算符，其名称由下表中各个字符的名称连接而成。</span><span class="sxs-lookup"><span data-stu-id="29d77-133">Other combinations of operator characters that are not listed here can be used as operators and have names that are made up by concatenating names for the individual characters from the following table.</span></span> <span data-ttu-id="29d77-134">例如 +！</span><span class="sxs-lookup"><span data-stu-id="29d77-134">For example, +!</span></span> <span data-ttu-id="29d77-135"> 变为 `op_PlusBang`。</span><span class="sxs-lookup"><span data-stu-id="29d77-135">becomes `op_PlusBang`.</span></span>

|<span data-ttu-id="29d77-136">运算符字符</span><span class="sxs-lookup"><span data-stu-id="29d77-136">Operator character</span></span>|<span data-ttu-id="29d77-137">名称</span><span class="sxs-lookup"><span data-stu-id="29d77-137">Name</span></span>|
|------------------|----|
|`>`|`Greater`|
|`<`|`Less`|
|`+`|`Plus`|
|`-`|`Minus`|
|`*`|`Multiply`|
|`/`|`Divide`|
|`=`|`Equals`|
|`~`|`Twiddle`|
|`%`|`Percent`|
|`.`|`Dot`|
|`&`|`Amp`|
|<code>&#124;</code>|`Bar`|
|`@`|`At`|
|`^`|`Hat`|
|`!`|`Bang`|
|`?`|`Qmark`|
|`(`|`LParen`|
|`,`|`Comma`|
|`)`|`RParen`|
|`[`|`LBrack`|
|`]`|`RBrack`|

## <a name="prefix-and-infix-operators"></a><span data-ttu-id="29d77-138">前缀和中缀运算符</span><span class="sxs-lookup"><span data-stu-id="29d77-138">Prefix and Infix Operators</span></span>

<span data-ttu-id="29d77-139">*前缀* 运算符应放置在一个或多个操作数前面，这与函数非常类似。</span><span class="sxs-lookup"><span data-stu-id="29d77-139">*Prefix* operators are expected to be placed in front of an operand or operands, much like a function.</span></span> <span data-ttu-id="29d77-140">应将中*缀*运算符放置在两个操作数之间。</span><span class="sxs-lookup"><span data-stu-id="29d77-140">*Infix* operators are expected to be placed between the two operands.</span></span>

<span data-ttu-id="29d77-141">只有某些运算符可以用作前缀运算符。</span><span class="sxs-lookup"><span data-stu-id="29d77-141">Only certain operators can be used as prefix operators.</span></span> <span data-ttu-id="29d77-142">一些运算符始终是前缀运算符，其他运算符可以是中缀或前缀，其余运算符始终是中缀运算符。</span><span class="sxs-lookup"><span data-stu-id="29d77-142">Some operators are always prefix operators, others can be infix or prefix, and the rest are always infix operators.</span></span> <span data-ttu-id="29d77-143">除了 `!` 之外，以 `!=` 开头的运算符以及运算符 `~` 或 `~` 的重复序列始终为前缀运算符。</span><span class="sxs-lookup"><span data-stu-id="29d77-143">Operators that begin with `!`, except `!=`, and the operator `~`, or repeated sequences of`~`, are always prefix operators.</span></span> <span data-ttu-id="29d77-144">运算符、、、、、、 `+` `-` `+.` `-.` `&` `&&` `%` 和 `%%` 可以是前缀运算符或中缀运算符。</span><span class="sxs-lookup"><span data-stu-id="29d77-144">The operators `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, and `%%` can be prefix operators or infix operators.</span></span> <span data-ttu-id="29d77-145">在定义时，可以通过 `~` 在前缀运算符开头添加来区分这些运算符的前缀版本。</span><span class="sxs-lookup"><span data-stu-id="29d77-145">You distinguish the prefix version of these operators from the infix version by adding a `~` at the beginning of a prefix operator when it is defined.</span></span> <span data-ttu-id="29d77-146">`~`仅当定义了运算符时，才使用。</span><span class="sxs-lookup"><span data-stu-id="29d77-146">The `~` is not used when you use the operator, only when it is defined.</span></span>

## <a name="example"></a><span data-ttu-id="29d77-147">示例</span><span class="sxs-lookup"><span data-stu-id="29d77-147">Example</span></span>

<span data-ttu-id="29d77-148">下面的代码演示如何使用运算符重载来实现分数类型。</span><span class="sxs-lookup"><span data-stu-id="29d77-148">The following code illustrates the use of operator overloading to implement a fraction type.</span></span> <span data-ttu-id="29d77-149">分数由分子和分母表示。</span><span class="sxs-lookup"><span data-stu-id="29d77-149">A fraction is represented by a numerator and a denominator.</span></span> <span data-ttu-id="29d77-150">函数 `hcf` 用于确定最大公因数，用来减少分数。</span><span class="sxs-lookup"><span data-stu-id="29d77-150">The function `hcf` is used to determine the highest common factor, which is used to reduce fractions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

<span data-ttu-id="29d77-151">**输出：**</span><span class="sxs-lookup"><span data-stu-id="29d77-151">**Output:**</span></span>

```console
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a><span data-ttu-id="29d77-152">全局级别的运算符</span><span class="sxs-lookup"><span data-stu-id="29d77-152">Operators at the Global Level</span></span>

<span data-ttu-id="29d77-153">您还可以在全局级别定义运算符。</span><span class="sxs-lookup"><span data-stu-id="29d77-153">You can also define operators at the global level.</span></span> <span data-ttu-id="29d77-154">下面的代码定义运算符 `+?` 。</span><span class="sxs-lookup"><span data-stu-id="29d77-154">The following code defines an operator `+?`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

<span data-ttu-id="29d77-155">上述代码的输出为 `12` 。</span><span class="sxs-lookup"><span data-stu-id="29d77-155">The output of the above code is `12`.</span></span>

<span data-ttu-id="29d77-156">可以通过这种方式重定义常规算术运算符，因为 F # 的作用域规则规定新定义的运算符优先于内置运算符。</span><span class="sxs-lookup"><span data-stu-id="29d77-156">You can redefine the regular arithmetic operators in this manner because the scoping rules for F# dictate that newly defined operators take precedence over the built-in operators.</span></span>

<span data-ttu-id="29d77-157">关键字 `inline` 通常与全局运算符一起使用，全局运算符通常是最能集成到调用代码中的小函数。</span><span class="sxs-lookup"><span data-stu-id="29d77-157">The keyword `inline` is often used with global operators, which are often small functions that are best integrated into the calling code.</span></span> <span data-ttu-id="29d77-158">通过使 operator 函数成为内联函数，它们可以使用静态解析的类型参数来生成静态解析的泛型代码。</span><span class="sxs-lookup"><span data-stu-id="29d77-158">Making operator functions inline also enables them to work with statically resolved type parameters to produce statically resolved generic code.</span></span> <span data-ttu-id="29d77-159">有关详细信息，请参阅 [内联函数](./functions/inline-functions.md) 和 [静态解析的类型参数](./generics/statically-resolved-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="29d77-159">For more information, see [Inline Functions](./functions/inline-functions.md) and [Statically Resolved Type Parameters](./generics/statically-resolved-type-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="29d77-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="29d77-160">See also</span></span>

- [<span data-ttu-id="29d77-161">成员</span><span class="sxs-lookup"><span data-stu-id="29d77-161">Members</span></span>](./members/index.md)
