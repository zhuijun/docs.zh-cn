---
description: if-else - C# 参考
title: if-else - C# 参考
ms.date: 07/20/2015
f1_keywords:
- if_CSharpKeyword
- else
- else_CSharpKeyword
- if
helpviewer_keywords:
- else keyword [C#]
- if keyword [C#]
ms.assetid: d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2
ms.openlocfilehash: e2de84807a049bd47ea277db9fb010d0c2e4857d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118502"
---
# <a name="if-else-c-reference"></a><span data-ttu-id="2ba72-103">if-else（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="2ba72-103">if-else (C# Reference)</span></span>

<span data-ttu-id="2ba72-104">`if` 语句基于布尔表达式的值来识别运行哪个语句。</span><span class="sxs-lookup"><span data-stu-id="2ba72-104">An `if` statement identifies which statement to run based on the value of a Boolean expression.</span></span> <span data-ttu-id="2ba72-105">在下面的示例中， `bool` 变量 `condition` 已被设置为 `true` ，然后被签入到了 `if` 语句。</span><span class="sxs-lookup"><span data-stu-id="2ba72-105">In the following example, the `bool` variable `condition` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="2ba72-106">输出为 `The variable is set to true.`。</span><span class="sxs-lookup"><span data-stu-id="2ba72-106">The output is `The variable is set to true.`.</span></span>

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

<span data-ttu-id="2ba72-107">你可以通过将本主题中的示例放入控制台应用的 `Main` 方法中来运行它们。</span><span class="sxs-lookup"><span data-stu-id="2ba72-107">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>

<span data-ttu-id="2ba72-108">C# 中的 `if` 语句可以采用两种形式，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="2ba72-108">An `if` statement in C# can take two forms, as the following example shows.</span></span>

```csharp
// if-else statement
if (condition)
{
    then-statement;
}
else
{
    else-statement;
}
// Next statement in the program.

// if statement without an else
if (condition)
{
    then-statement;
}
// Next statement in the program.
```

<span data-ttu-id="2ba72-109">在 `if-else` 语句中，如果 `condition` 计算结果为 true，则 `then-statement` 将运行。</span><span class="sxs-lookup"><span data-stu-id="2ba72-109">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="2ba72-110">如果 `condition` 为 false，则 `else-statement` 将运行。</span><span class="sxs-lookup"><span data-stu-id="2ba72-110">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="2ba72-111">由于 `condition` 不能同时为 true 和 false，因此， `then-statement` 语句的 `else-statement` 和 `if-else` 永远不能同时运行。</span><span class="sxs-lookup"><span data-stu-id="2ba72-111">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="2ba72-112">`then-statement` 或 `else-statement` 运行后，控件将转移到 `if` 语句之后的下一个语句。</span><span class="sxs-lookup"><span data-stu-id="2ba72-112">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="2ba72-113">在不包括 `if` 语句的 `else` 语句中，如果 `condition` 为 true，则 `then-statement` 将运行。</span><span class="sxs-lookup"><span data-stu-id="2ba72-113">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="2ba72-114">如果 `condition` 为 false，则控件将转移到 `if` 语句之后的下一个语句。</span><span class="sxs-lookup"><span data-stu-id="2ba72-114">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="2ba72-115">`then-statement` 和 `else-statement` 都可由单个语句或包含在括号中 (`{}`) 的多个语句组成。</span><span class="sxs-lookup"><span data-stu-id="2ba72-115">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="2ba72-116">对于单个语句，括号是可选的，但建议选择。</span><span class="sxs-lookup"><span data-stu-id="2ba72-116">For a single statement, the braces are optional but recommended.</span></span>

<span data-ttu-id="2ba72-117">`then-statement` 和 `else-statement` 中的语句可为任何类型，包括嵌套在原始 `if` 语句中的另一个 `if` 语句。</span><span class="sxs-lookup"><span data-stu-id="2ba72-117">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="2ba72-118">在嵌套的 `if` 语句中，每个 `else` 子句都属于上一个无相应 `if` 的 `else`。</span><span class="sxs-lookup"><span data-stu-id="2ba72-118">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="2ba72-119">在下面的示例中，如果 `Result1` 和 `m > 10` 计算结果都为 true，则将显示 `n > 20` 。</span><span class="sxs-lookup"><span data-stu-id="2ba72-119">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="2ba72-120">如果 `m > 10` 为 true 但 `n > 20` 为 false，则将显示 `Result2` 。</span><span class="sxs-lookup"><span data-stu-id="2ba72-120">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

<span data-ttu-id="2ba72-121">相反，如果你希望在 `Result2` 为 false 的时候显示 `(m > 10)` ，则可以通过使用括号来指定此关联，以建立嵌套的 `if` 语句的开头和结尾，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="2ba72-121">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

<span data-ttu-id="2ba72-122">如果条件 `(m > 10)` 的计算结果为 false，则显示 `Result2`。</span><span class="sxs-lookup"><span data-stu-id="2ba72-122">`Result2` appears if the condition `(m > 10)` evaluates to false.</span></span>

## <a name="example"></a><span data-ttu-id="2ba72-123">示例</span><span class="sxs-lookup"><span data-stu-id="2ba72-123">Example</span></span>

<span data-ttu-id="2ba72-124">在下例中，当通过键盘输入字符时，该程序将使用嵌套的 `if` 语句来确定输入的字符是否为字母字符。</span><span class="sxs-lookup"><span data-stu-id="2ba72-124">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="2ba72-125">如果输入的字符是字母字符，则程序将检查输入的字符是大写还是小写。</span><span class="sxs-lookup"><span data-stu-id="2ba72-125">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="2ba72-126">每种情况都会显示一条消息。</span><span class="sxs-lookup"><span data-stu-id="2ba72-126">A message appears for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a><span data-ttu-id="2ba72-127">示例</span><span class="sxs-lookup"><span data-stu-id="2ba72-127">Example</span></span>

<span data-ttu-id="2ba72-128">你也可以将 `if` 语句嵌套到 else 块中，如以下部分代码所示。</span><span class="sxs-lookup"><span data-stu-id="2ba72-128">You can also nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="2ba72-129">示例将 `if` 语句嵌套在两个 else 块和一个 then 块中。</span><span class="sxs-lookup"><span data-stu-id="2ba72-129">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="2ba72-130">注释指定每个块中哪些条件为 true 哪些条件为 false。</span><span class="sxs-lookup"><span data-stu-id="2ba72-130">The comments specify which conditions are true or false in each block.</span></span>

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a><span data-ttu-id="2ba72-131">示例</span><span class="sxs-lookup"><span data-stu-id="2ba72-131">Example</span></span>

<span data-ttu-id="2ba72-132">下面的示例确定了输入的字符是一个小写字母，还是大写字母，还是一个数字。</span><span class="sxs-lookup"><span data-stu-id="2ba72-132">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="2ba72-133">如果所有三个条件都为 false，该字符不是字母数字字符。</span><span class="sxs-lookup"><span data-stu-id="2ba72-133">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="2ba72-134">此示例显示了每种情况的消息内容。</span><span class="sxs-lookup"><span data-stu-id="2ba72-134">The example displays a message for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

<span data-ttu-id="2ba72-135">正如 else 块或 then 块中的语句可以是任何有效的语句一样，你可以将任何有效的布尔表达式用于此条件。</span><span class="sxs-lookup"><span data-stu-id="2ba72-135">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="2ba72-136">可使用 `!`、`&&`、`||`、`&`、`|` 和 `^` 等[逻辑运算符](../operators/boolean-logical-operators.md)来创建复合条件。</span><span class="sxs-lookup"><span data-stu-id="2ba72-136">You can use [logical operators](../operators/boolean-logical-operators.md) such as `!`, `&&`, `||`, `&`, `|`, and `^` to make compound conditions.</span></span> <span data-ttu-id="2ba72-137">下面的代码演示了示例。</span><span class="sxs-lookup"><span data-stu-id="2ba72-137">The following code shows examples.</span></span>

```csharp
// NOT
bool result = true;
if (!result)
{
    Console.WriteLine("The condition is true (result is false).");
}
else
{
    Console.WriteLine("The condition is false (result is true).");
}

// Short-circuit AND
int m = 9;
int n = 7;
int p = 5;
if (m >= n && m >= p)
{
    Console.WriteLine("Nothing is larger than m.");
}

// AND and NOT
if (m >= n && !(p > m))
{
    Console.WriteLine("Nothing is larger than m.");
}

// Short-circuit OR
if (m > n || m > p)
{
    Console.WriteLine("m isn't the smallest.");
}

// NOT and OR
m = 4;
if (!(m >= n || m >= p))
{
    Console.WriteLine("Now m is the smallest.");
}
// Output:
// The condition is false (result is true).
// Nothing is larger than m.
// Nothing is larger than m.
// m isn't the smallest.
// Now m is the smallest.
```

## <a name="c-language-specification"></a><span data-ttu-id="2ba72-138">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="2ba72-138">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2ba72-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="2ba72-139">See also</span></span>

- [<span data-ttu-id="2ba72-140">C# 参考</span><span class="sxs-lookup"><span data-stu-id="2ba72-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2ba72-141">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="2ba72-141">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2ba72-142">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="2ba72-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2ba72-143">?:运算符</span><span class="sxs-lookup"><span data-stu-id="2ba72-143">?: Operator</span></span>](../operators/conditional-operator.md)
- [<span data-ttu-id="2ba72-144">if-else 语句 (C++)</span><span class="sxs-lookup"><span data-stu-id="2ba72-144">if-else Statement (C++)</span></span>](/cpp/cpp/if-else-statement-cpp)
- [<span data-ttu-id="2ba72-145">switch</span><span class="sxs-lookup"><span data-stu-id="2ba72-145">switch</span></span>](switch.md)
