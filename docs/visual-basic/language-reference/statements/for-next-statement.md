---
title: For...Next 语句
ms.date: 07/20/2015
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
helpviewer_keywords:
- infinite loops
- Next keyword [Visual Basic], For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword [Visual Basic], For...Next statements
- operator overloading, For...Next statement
- To keyword [Visual Basic], For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement [Visual Basic], For...Next
- For...Next statements
- loop structures [Visual Basic], For...Next
- loops, infinite
- Exit statement [Visual Basic], For...Next statements
- For statement [Visual Basic]
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
ms.openlocfilehash: 6896c6cfb4ec5d6207011e56b72639c459120e53
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404636"
---
# <a name="fornext-statement-visual-basic"></a><span data-ttu-id="d189b-102">For...Next 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d189b-102">For...Next Statement (Visual Basic)</span></span>

<span data-ttu-id="d189b-103">按指定次数重复一组语句。</span><span class="sxs-lookup"><span data-stu-id="d189b-103">Repeats a group of statements a specified number of times.</span></span>

## <a name="syntax"></a><span data-ttu-id="d189b-104">语法</span><span class="sxs-lookup"><span data-stu-id="d189b-104">Syntax</span></span>

```vb
For counter [ As datatype ] = start To end [ Step step ]
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ counter ]
```

## <a name="parts"></a><span data-ttu-id="d189b-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="d189b-105">Parts</span></span>

|<span data-ttu-id="d189b-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="d189b-106">Part</span></span>|<span data-ttu-id="d189b-107">说明</span><span class="sxs-lookup"><span data-stu-id="d189b-107">Description</span></span>|
|----------|-----------------|
|`counter`|<span data-ttu-id="d189b-108">语句中必需 `For` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-108">Required in the `For` statement.</span></span> <span data-ttu-id="d189b-109">数值变量。</span><span class="sxs-lookup"><span data-stu-id="d189b-109">Numeric variable.</span></span> <span data-ttu-id="d189b-110">循环的控制变量。</span><span class="sxs-lookup"><span data-stu-id="d189b-110">The control variable for the loop.</span></span> <span data-ttu-id="d189b-111">有关详细信息，请参阅本主题后面的[计数器参数](#BKMK_Counter)。</span><span class="sxs-lookup"><span data-stu-id="d189b-111">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`datatype`|<span data-ttu-id="d189b-112">可选。</span><span class="sxs-lookup"><span data-stu-id="d189b-112">Optional.</span></span> <span data-ttu-id="d189b-113">的数据类型 `counter` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-113">Data type of `counter`.</span></span> <span data-ttu-id="d189b-114">有关详细信息，请参阅本主题后面的[计数器参数](#BKMK_Counter)。</span><span class="sxs-lookup"><span data-stu-id="d189b-114">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`start`|<span data-ttu-id="d189b-115">必需。</span><span class="sxs-lookup"><span data-stu-id="d189b-115">Required.</span></span> <span data-ttu-id="d189b-116">数值表达式。</span><span class="sxs-lookup"><span data-stu-id="d189b-116">Numeric expression.</span></span> <span data-ttu-id="d189b-117">`counter` 的初始值。</span><span class="sxs-lookup"><span data-stu-id="d189b-117">The initial value of `counter`.</span></span>|
|`end`|<span data-ttu-id="d189b-118">必需。</span><span class="sxs-lookup"><span data-stu-id="d189b-118">Required.</span></span> <span data-ttu-id="d189b-119">数值表达式。</span><span class="sxs-lookup"><span data-stu-id="d189b-119">Numeric expression.</span></span> <span data-ttu-id="d189b-120">的最终值 `counter` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-120">The final value of `counter`.</span></span>|
|`step`|<span data-ttu-id="d189b-121">可选。</span><span class="sxs-lookup"><span data-stu-id="d189b-121">Optional.</span></span> <span data-ttu-id="d189b-122">数值表达式。</span><span class="sxs-lookup"><span data-stu-id="d189b-122">Numeric expression.</span></span> <span data-ttu-id="d189b-123">`counter`每次通过循环增加的量。</span><span class="sxs-lookup"><span data-stu-id="d189b-123">The amount by which `counter` is incremented each time through the loop.</span></span>|
|`statements`|<span data-ttu-id="d189b-124">可选。</span><span class="sxs-lookup"><span data-stu-id="d189b-124">Optional.</span></span> <span data-ttu-id="d189b-125">`For`与之间运行指定次数的一个或多个语句 `Next` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-125">One or more statements between `For` and `Next` that run the specified number of times.</span></span>|
|`Continue For`|<span data-ttu-id="d189b-126">可选。</span><span class="sxs-lookup"><span data-stu-id="d189b-126">Optional.</span></span> <span data-ttu-id="d189b-127">将控制转移到下一个循环迭代。</span><span class="sxs-lookup"><span data-stu-id="d189b-127">Transfers control to the next loop iteration.</span></span>|
|`Exit For`|<span data-ttu-id="d189b-128">可选。</span><span class="sxs-lookup"><span data-stu-id="d189b-128">Optional.</span></span> <span data-ttu-id="d189b-129">将控制转移到 `For` 循环外。</span><span class="sxs-lookup"><span data-stu-id="d189b-129">Transfers control out of the `For` loop.</span></span>|
|`Next`|<span data-ttu-id="d189b-130">必需。</span><span class="sxs-lookup"><span data-stu-id="d189b-130">Required.</span></span> <span data-ttu-id="d189b-131">终止循环的定义 `For` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-131">Terminates the definition of the `For` loop.</span></span>|

> [!NOTE]
> <span data-ttu-id="d189b-132">`To`此语句使用关键字来指定计数器的范围。</span><span class="sxs-lookup"><span data-stu-id="d189b-132">The `To` keyword is used in this statement to specify the range for the counter.</span></span> <span data-ttu-id="d189b-133">你还可以在[Select .。。Case 语句](select-case-statement.md)和数组声明。</span><span class="sxs-lookup"><span data-stu-id="d189b-133">You can also use this keyword in the [Select...Case Statement](select-case-statement.md) and in array declarations.</span></span> <span data-ttu-id="d189b-134">有关数组声明的详细信息，请参阅[Dim 语句](dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="d189b-134">For more information about array declarations, see [Dim Statement](dim-statement.md).</span></span>

## <a name="simple-examples"></a><span data-ttu-id="d189b-135"> 简单示例</span><span class="sxs-lookup"><span data-stu-id="d189b-135">Simple Examples</span></span>

<span data-ttu-id="d189b-136">`For` `Next` 如果要对一组语句重复一组次数，请使用 ... 结构。</span><span class="sxs-lookup"><span data-stu-id="d189b-136">You use a `For`...`Next` structure when you want to repeat a set of statements a set number of times.</span></span>

<span data-ttu-id="d189b-137">在下面的示例中， `index` 变量的值为1，并与循环的每次迭代递增，在的值达到5之后结束 `index` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-137">In the following example, the `index` variable starts with a value of 1 and is incremented with each iteration of the loop, ending after the value of `index` reaches 5.</span></span>

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

<span data-ttu-id="d189b-138">在下面的示例中， `number` 变量从2开始，在循环的每次迭代后减0.25，截止值为 `number` 0。</span><span class="sxs-lookup"><span data-stu-id="d189b-138">In the following example, the `number` variable starts at 2 and is reduced by 0.25 on each iteration of the loop, ending after the value of `number` reaches 0.</span></span> <span data-ttu-id="d189b-139">的 `Step` 自变量会 `-.25` 在循环的每次迭代时减少值0.25。</span><span class="sxs-lookup"><span data-stu-id="d189b-139">The `Step` argument of `-.25` reduces the value by 0.25 on each iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> <span data-ttu-id="d189b-140">... [End While 语句](while-end-while-statement.md)或[Do .。。](do-loop-statement.md)当您事先不知道在循环中运行语句的次数时，Loop 语句可以正常工作。</span><span class="sxs-lookup"><span data-stu-id="d189b-140">A [While...End While Statement](while-end-while-statement.md) or [Do...Loop Statement](do-loop-statement.md) works well when you don't know in advance how many times to run the statements in the loop.</span></span> <span data-ttu-id="d189b-141">但是，当你想要运行循环特定次数时，" `For` ..." `Next` 循环是更好的选择。</span><span class="sxs-lookup"><span data-stu-id="d189b-141">However, when you expect to run the loop a specific number of times, a `For`...`Next` loop is a better choice.</span></span> <span data-ttu-id="d189b-142">您在第一次进入循环时确定迭代次数。</span><span class="sxs-lookup"><span data-stu-id="d189b-142">You determine the number of iterations when you first enter the loop.</span></span>

## <a name="nesting-loops"></a><span data-ttu-id="d189b-143">嵌套循环</span><span class="sxs-lookup"><span data-stu-id="d189b-143">Nesting Loops</span></span>

<span data-ttu-id="d189b-144">可以 `For` 通过在另一个循环中放置循环来嵌套循环。</span><span class="sxs-lookup"><span data-stu-id="d189b-144">You can nest `For` loops by putting one loop within another.</span></span> <span data-ttu-id="d189b-145">下面的示例演示 `For` `Next` 具有不同步长值的嵌套 ... 结构。</span><span class="sxs-lookup"><span data-stu-id="d189b-145">The following example demonstrates nested `For`...`Next` structures that have different step values.</span></span> <span data-ttu-id="d189b-146">外部循环为循环的每次迭代创建字符串。</span><span class="sxs-lookup"><span data-stu-id="d189b-146">The outer loop creates a string for every iteration of the loop.</span></span> <span data-ttu-id="d189b-147">内部循环为循环的每次迭代递减循环计数器变量。</span><span class="sxs-lookup"><span data-stu-id="d189b-147">The inner loop decrements a loop counter variable for every iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

<span data-ttu-id="d189b-148">嵌套循环时，每个循环必须具有唯一 `counter` 变量。</span><span class="sxs-lookup"><span data-stu-id="d189b-148">When nesting loops, each loop must have a unique `counter` variable.</span></span>

<span data-ttu-id="d189b-149">你还可以在彼此之间嵌套不同种类的控制结构。</span><span class="sxs-lookup"><span data-stu-id="d189b-149">You can also nest different kinds control structures within each other.</span></span> <span data-ttu-id="d189b-150">有关详细信息，请参阅[嵌套控制结构](../../programming-guide/language-features/control-flow/nested-control-structures.md)。</span><span class="sxs-lookup"><span data-stu-id="d189b-150">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>

## <a name="exit-for-and-continue-for"></a><span data-ttu-id="d189b-151">退出并继续进行</span><span class="sxs-lookup"><span data-stu-id="d189b-151">Exit For and Continue For</span></span>

<span data-ttu-id="d189b-152">`Exit For`语句立即退出 `For` .。。`Next`</span><span class="sxs-lookup"><span data-stu-id="d189b-152">The `Exit For` statement immediately exits the `For`…`Next`</span></span> <span data-ttu-id="d189b-153">循环并将控制转移到语句后面的语句 `Next` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-153">loop and transfers control to the statement that follows the `Next` statement.</span></span>

<span data-ttu-id="d189b-154">`Continue For`语句将控制立即传输到循环的下一次迭代。</span><span class="sxs-lookup"><span data-stu-id="d189b-154">The `Continue For` statement transfers control immediately to the next iteration of the loop.</span></span> <span data-ttu-id="d189b-155">有关详细信息，请参阅[Continue 语句](continue-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="d189b-155">For more information, see [Continue Statement](continue-statement.md).</span></span>

<span data-ttu-id="d189b-156">下面的示例演示如何使用 `Continue For` 和 `Exit For` 语句。</span><span class="sxs-lookup"><span data-stu-id="d189b-156">The following example illustrates the use of the `Continue For` and `Exit For` statements.</span></span>

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

<span data-ttu-id="d189b-157">可以将任意数量的语句放入 `Exit For` `For` .。。`Next`</span><span class="sxs-lookup"><span data-stu-id="d189b-157">You can put any number of `Exit For` statements in a `For`…`Next`</span></span> <span data-ttu-id="d189b-158">圈.</span><span class="sxs-lookup"><span data-stu-id="d189b-158">loop.</span></span> <span data-ttu-id="d189b-159">当在嵌套 `For` .。。`Next`</span><span class="sxs-lookup"><span data-stu-id="d189b-159">When used within nested `For`…`Next`</span></span> <span data-ttu-id="d189b-160">循环， `Exit For` 退出最内层的循环，并将控制转移到下一个更高的嵌套级别。</span><span class="sxs-lookup"><span data-stu-id="d189b-160">loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

<span data-ttu-id="d189b-161">`Exit For`在你计算某个条件（例如，在 `If` ... `Then`...`Else`结构）。</span><span class="sxs-lookup"><span data-stu-id="d189b-161">`Exit For` is often used after you evaluate some condition (for example, in an `If`...`Then`...`Else` structure).</span></span> <span data-ttu-id="d189b-162">你可能想要将 `Exit For` 用于以下情况：</span><span class="sxs-lookup"><span data-stu-id="d189b-162">You might want to use `Exit For` for the following conditions:</span></span>

- <span data-ttu-id="d189b-163">不需要继续循环访问。</span><span class="sxs-lookup"><span data-stu-id="d189b-163">Continuing to iterate is unnecessary or impossible.</span></span> <span data-ttu-id="d189b-164">错误的值或终止请求可能会创建此条件。</span><span class="sxs-lookup"><span data-stu-id="d189b-164">An erroneous value or a termination request might create this condition.</span></span>

- <span data-ttu-id="d189b-165">`Try`... `Catch`...`Finally`语句捕获异常。</span><span class="sxs-lookup"><span data-stu-id="d189b-165">A `Try`...`Catch`...`Finally` statement catches an exception.</span></span> <span data-ttu-id="d189b-166">可以 `Exit For` 在块的末尾使用 `Finally` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-166">You might use `Exit For` at the end of the `Finally` block.</span></span>

- <span data-ttu-id="d189b-167">您有一个无限循环，该循环是一种循环，它可以运行很大甚至无限次。</span><span class="sxs-lookup"><span data-stu-id="d189b-167">You have an endless loop, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="d189b-168">如果检测到这种情况，则可以使用 `Exit For` 来转义循环。</span><span class="sxs-lookup"><span data-stu-id="d189b-168">If you detect such a condition, you can use `Exit For` to escape the loop.</span></span> <span data-ttu-id="d189b-169">有关详细信息，请参阅[Do .。。循环语句](do-loop-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="d189b-169">For more information, see [Do...Loop Statement](do-loop-statement.md).</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="d189b-170">技术实现</span><span class="sxs-lookup"><span data-stu-id="d189b-170">Technical Implementation</span></span>

<span data-ttu-id="d189b-171">当 `For` ... `Next` 循环启动时，Visual Basic 将计算 `start` 、 `end` 和 `step` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-171">When a `For`...`Next` loop starts, Visual Basic evaluates `start`, `end`, and `step`.</span></span> <span data-ttu-id="d189b-172">Visual Basic 此时仅计算这些值，然后将赋值 `start` 给 `counter` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-172">Visual Basic evaluates these values only at this time and then assigns `start` to `counter`.</span></span> <span data-ttu-id="d189b-173">在语句块运行之前，Visual Basic 与进行比较 `counter` `end` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-173">Before the statement block runs, Visual Basic compares `counter` to `end`.</span></span> <span data-ttu-id="d189b-174">如果已大于 `counter` `end` 值（如果为负，则为较小的值 `step` ）， `For` 循环将结束并控制传递到语句后面的语句 `Next` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-174">If `counter` is already larger than the `end` value (or smaller if `step` is negative), the `For` loop ends and control passes to the statement that follows the `Next` statement.</span></span> <span data-ttu-id="d189b-175">否则，语句块将运行。</span><span class="sxs-lookup"><span data-stu-id="d189b-175">Otherwise, the statement block runs.</span></span>

<span data-ttu-id="d189b-176">每次 Visual Basic 遇到 `Next` 语句时，它会 `counter` 递增 `step` 并返回到 `For` 语句。</span><span class="sxs-lookup"><span data-stu-id="d189b-176">Each time Visual Basic encounters the `Next` statement, it increments `counter` by `step` and returns to the `For` statement.</span></span> <span data-ttu-id="d189b-177">同样，它与进行比较 `counter` `end` ，并再次运行该块或退出循环，具体取决于结果。</span><span class="sxs-lookup"><span data-stu-id="d189b-177">Again it compares `counter` to `end`, and again it either runs the block or exits the loop, depending on the result.</span></span> <span data-ttu-id="d189b-178">此过程将一直 `counter` 继续 `end` ，直到 `Exit For` 遇到传递或语句。</span><span class="sxs-lookup"><span data-stu-id="d189b-178">This process continues until `counter` passes `end` or an `Exit For` statement is encountered.</span></span>

<span data-ttu-id="d189b-179">直到经过传递后循环才会停止 `counter` `end` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-179">The loop doesn't stop until `counter` has passed `end`.</span></span> <span data-ttu-id="d189b-180">如果 `counter` 等于 `end` ，则循环将继续。</span><span class="sxs-lookup"><span data-stu-id="d189b-180">If `counter` is equal to `end`, the loop continues.</span></span> <span data-ttu-id="d189b-181">确定是否运行块的比较是否为 `counter`  <=  `end` `step` 正且为 `counter`  >=  `end` `step` 负。</span><span class="sxs-lookup"><span data-stu-id="d189b-181">The comparison that determines whether to run the block is `counter` <= `end` if `step` is positive and `counter` >= `end` if `step` is negative.</span></span>

<span data-ttu-id="d189b-182">如果在循环内更改的值 `counter` ，则可能会更难读取和调试代码。</span><span class="sxs-lookup"><span data-stu-id="d189b-182">If you change the value of `counter` while inside a loop, your code might be more difficult to read and debug.</span></span> <span data-ttu-id="d189b-183">更改 `start` 、或的值 `end` `step` 不会影响在第一次输入循环时确定的迭代值。</span><span class="sxs-lookup"><span data-stu-id="d189b-183">Changing the value of `start`, `end`, or `step` doesn't affect the iteration values that were determined when the loop was first entered.</span></span>

<span data-ttu-id="d189b-184">如果嵌套循环，编译器在 `Next` 内部级别的语句之前遇到外部嵌套级别的语句时，会发出错误信号 `Next` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-184">If you nest loops, the compiler signals an error if it encounters the `Next` statement of an outer nesting level before the `Next` statement of an inner level.</span></span> <span data-ttu-id="d189b-185">但是，只有在 `counter` 每个语句中指定时，编译器才能检测到此重叠错误 `Next` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-185">However, the compiler can detect this overlapping error only if you specify `counter` in every `Next` statement.</span></span>

### <a name="step-argument"></a><span data-ttu-id="d189b-186">步骤参数</span><span class="sxs-lookup"><span data-stu-id="d189b-186">Step Argument</span></span>

<span data-ttu-id="d189b-187">的值 `step` 可以是正数也可以是负数。</span><span class="sxs-lookup"><span data-stu-id="d189b-187">The value of `step` can be either positive or negative.</span></span> <span data-ttu-id="d189b-188">此参数根据下表确定循环处理：</span><span class="sxs-lookup"><span data-stu-id="d189b-188">This parameter determines loop processing according to the following table:</span></span>

|<span data-ttu-id="d189b-189">**步骤值**</span><span class="sxs-lookup"><span data-stu-id="d189b-189">**Step value**</span></span>|<span data-ttu-id="d189b-190">**如果**</span><span class="sxs-lookup"><span data-stu-id="d189b-190">**Loop executes if**</span></span>|
|--------------------|--------------------------|
|<span data-ttu-id="d189b-191">正或零</span><span class="sxs-lookup"><span data-stu-id="d189b-191">Positive or zero</span></span>|`counter` <= `end`|
|<span data-ttu-id="d189b-192">负</span><span class="sxs-lookup"><span data-stu-id="d189b-192">Negative</span></span>|`counter` >= `end`|

<span data-ttu-id="d189b-193">`step` 的默认值为 1。</span><span class="sxs-lookup"><span data-stu-id="d189b-193">The default value of `step` is 1.</span></span>

### <a name="counter-argument"></a><a name="BKMK_Counter"></a><span data-ttu-id="d189b-194">计数器参数</span><span class="sxs-lookup"><span data-stu-id="d189b-194">Counter Argument</span></span>

<span data-ttu-id="d189b-195">下表指示是否 `counter` 定义了作用域为整个循环的新局部变量 `For…Next` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-195">The following table indicates whether `counter` defines a new local variable that’s scoped to the entire `For…Next` loop.</span></span> <span data-ttu-id="d189b-196">此确定取决于是否 `datatype` 存在以及是否 `counter` 已定义。</span><span class="sxs-lookup"><span data-stu-id="d189b-196">This determination depends on whether `datatype` is present and whether `counter` is already defined.</span></span>

|<span data-ttu-id="d189b-197">是否 `datatype` 存在？</span><span class="sxs-lookup"><span data-stu-id="d189b-197">Is `datatype` present?</span></span>|<span data-ttu-id="d189b-198">已 `counter` 定义？</span><span class="sxs-lookup"><span data-stu-id="d189b-198">Is `counter` already defined?</span></span>|<span data-ttu-id="d189b-199">Result （是否 `counter` 定义一个作用域为整个循环的新局部变量 `For...Next` ）</span><span class="sxs-lookup"><span data-stu-id="d189b-199">Result (whether `counter` defines a new local variable that’s scoped to the entire `For...Next` loop)</span></span>|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="d189b-200">否</span><span class="sxs-lookup"><span data-stu-id="d189b-200">No</span></span>|<span data-ttu-id="d189b-201">是</span><span class="sxs-lookup"><span data-stu-id="d189b-201">Yes</span></span>|<span data-ttu-id="d189b-202">不是，因为已 `counter` 定义。</span><span class="sxs-lookup"><span data-stu-id="d189b-202">No, because `counter` is already defined.</span></span> <span data-ttu-id="d189b-203">如果该过程的作用域 `counter` 不是本地的，则会发生编译时警告。</span><span class="sxs-lookup"><span data-stu-id="d189b-203">If the scope of `counter` isn't local to the procedure, a compile-time warning occurs.</span></span>|
|<span data-ttu-id="d189b-204">否</span><span class="sxs-lookup"><span data-stu-id="d189b-204">No</span></span>|<span data-ttu-id="d189b-205">否</span><span class="sxs-lookup"><span data-stu-id="d189b-205">No</span></span>|<span data-ttu-id="d189b-206">是。</span><span class="sxs-lookup"><span data-stu-id="d189b-206">Yes.</span></span> <span data-ttu-id="d189b-207">数据类型是从 `start` 、和表达式中推断出来的 `end` `step` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-207">The data type is inferred from the `start`, `end`, and `step` expressions.</span></span> <span data-ttu-id="d189b-208">有关类型推理的信息，请参阅[选项推断语句](option-infer-statement.md)和[局部类型推理](../../programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="d189b-208">For information about type inference, see [Option Infer Statement](option-infer-statement.md) and [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>|
|<span data-ttu-id="d189b-209">是</span><span class="sxs-lookup"><span data-stu-id="d189b-209">Yes</span></span>|<span data-ttu-id="d189b-210">是</span><span class="sxs-lookup"><span data-stu-id="d189b-210">Yes</span></span>|<span data-ttu-id="d189b-211">是，但仅当现有 `counter` 变量在过程外定义时才存在。</span><span class="sxs-lookup"><span data-stu-id="d189b-211">Yes, but only if the existing `counter` variable is defined outside the procedure.</span></span> <span data-ttu-id="d189b-212">该变量保持独立。</span><span class="sxs-lookup"><span data-stu-id="d189b-212">That variable remains separate.</span></span> <span data-ttu-id="d189b-213">如果现有变量的作用域 `counter` 是过程的本地值，则会发生编译时错误。</span><span class="sxs-lookup"><span data-stu-id="d189b-213">If the scope of the existing `counter` variable is local to the procedure, a compile-time error occurs.</span></span>|
|<span data-ttu-id="d189b-214">是</span><span class="sxs-lookup"><span data-stu-id="d189b-214">Yes</span></span>|<span data-ttu-id="d189b-215">否</span><span class="sxs-lookup"><span data-stu-id="d189b-215">No</span></span>|<span data-ttu-id="d189b-216">是。</span><span class="sxs-lookup"><span data-stu-id="d189b-216">Yes.</span></span>|

<span data-ttu-id="d189b-217">的数据类型 `counter` 确定迭代的类型，该类型必须是以下类型之一：</span><span class="sxs-lookup"><span data-stu-id="d189b-217">The data type of `counter` determines the type of the iteration, which must be one of the following types:</span></span>

- <span data-ttu-id="d189b-218">`Byte`、、 `SByte` 、 `UShort` `Short` 、 `UInteger` 、、、、、 `Integer` `ULong` `Long` `Decimal` `Single` 或 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-218">A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, or `Double`.</span></span>

- <span data-ttu-id="d189b-219">使用[Enum 语句](enum-statement.md)声明的枚举。</span><span class="sxs-lookup"><span data-stu-id="d189b-219">An enumeration that you declare by using an [Enum Statement](enum-statement.md).</span></span>

- <span data-ttu-id="d189b-220">一个`Object`。</span><span class="sxs-lookup"><span data-stu-id="d189b-220">An `Object`.</span></span>

- <span data-ttu-id="d189b-221">`T`具有以下运算符的类型，其中 `B` 是可在表达式中使用的类型 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-221">A type `T` that has the following operators, where `B` is a type that can be used in a `Boolean` expression.</span></span>

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

<span data-ttu-id="d189b-222">您可以选择 `counter` 在语句中指定变量 `Next` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-222">You can optionally specify the `counter` variable in the `Next` statement.</span></span> <span data-ttu-id="d189b-223">此语法可提高程序的可读性，尤其是在具有嵌套循环的情况下 `For` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-223">This syntax improves the readability of your program, especially if you have nested `For` loops.</span></span> <span data-ttu-id="d189b-224">您必须指定出现在相应语句中的变量 `For` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-224">You must specify the variable that appears in the corresponding `For` statement.</span></span>

<span data-ttu-id="d189b-225">`start`、 `end` 和表达式的 `step` 计算结果可以是扩大到类型的任何数据类型 `counter` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-225">The `start`, `end`, and `step` expressions can evaluate to any data type that widens to the type of `counter`.</span></span> <span data-ttu-id="d189b-226">如果对使用用户定义的类型 `counter` ，则可能需要定义 `CType` 转换运算符，以将、或的类型转换 `start` `end` `step` 为类型 `counter` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-226">If you use a user-defined type for `counter`, you might have to define the `CType` conversion operator to convert the types of `start`, `end`, or `step` to the type of `counter`.</span></span>

## <a name="example"></a><span data-ttu-id="d189b-227">示例</span><span class="sxs-lookup"><span data-stu-id="d189b-227">Example</span></span>

<span data-ttu-id="d189b-228">下面的示例从泛型列表中移除所有元素。</span><span class="sxs-lookup"><span data-stu-id="d189b-228">The following example removes all elements from a generic list.</span></span> <span data-ttu-id="d189b-229">而不是[为每个 .。。下一条语句](for-each-next-statement.md)中，该示例显示了一个 `For` `Next` "..." 语句，该语句将按降序循环访问。</span><span class="sxs-lookup"><span data-stu-id="d189b-229">Instead of a [For Each...Next Statement](for-each-next-statement.md), the example shows a `For`...`Next` statement that iterates in descending order.</span></span> <span data-ttu-id="d189b-230">该示例使用此方法，因为 `removeAt` 方法会使删除的元素之后的元素具有更低的索引值。</span><span class="sxs-lookup"><span data-stu-id="d189b-230">The example uses this technique because the `removeAt` method causes elements after the removed element to have a lower index value.</span></span>

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a><span data-ttu-id="d189b-231">示例</span><span class="sxs-lookup"><span data-stu-id="d189b-231">Example</span></span>

<span data-ttu-id="d189b-232">下面的示例循环访问通过使用[Enum 语句](enum-statement.md)声明的枚举。</span><span class="sxs-lookup"><span data-stu-id="d189b-232">The following example iterates through an enumeration that's declared by using an [Enum Statement](enum-statement.md).</span></span>

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a><span data-ttu-id="d189b-233">示例</span><span class="sxs-lookup"><span data-stu-id="d189b-233">Example</span></span>

<span data-ttu-id="d189b-234">在下面的示例中，语句参数使用具有 `+` 、、 `-` `>=` 和运算符的运算符重载的类 `<=` 。</span><span class="sxs-lookup"><span data-stu-id="d189b-234">In the following example, the statement parameters use a class that has operator overloads for the `+`, `-`, `>=`, and `<=` operators.</span></span>

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a><span data-ttu-id="d189b-235">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d189b-235">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="d189b-236">循环结构</span><span class="sxs-lookup"><span data-stu-id="d189b-236">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="d189b-237">While...End While 语句</span><span class="sxs-lookup"><span data-stu-id="d189b-237">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="d189b-238">Do...Loop 语句</span><span class="sxs-lookup"><span data-stu-id="d189b-238">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="d189b-239">嵌套的控件结构</span><span class="sxs-lookup"><span data-stu-id="d189b-239">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="d189b-240">Exit 语句</span><span class="sxs-lookup"><span data-stu-id="d189b-240">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="d189b-241">集合</span><span class="sxs-lookup"><span data-stu-id="d189b-241">Collections</span></span>](../../programming-guide/concepts/collections.md)
