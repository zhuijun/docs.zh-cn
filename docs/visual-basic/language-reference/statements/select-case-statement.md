---
title: Select...Case 语句
ms.date: 07/20/2015
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
ms.openlocfilehash: 3dedd43f920b493a0aca9ce48460b00815e1af5c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404234"
---
# <a name="selectcase-statement-visual-basic"></a><span data-ttu-id="76f14-102">Select...Case 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76f14-102">Select...Case Statement (Visual Basic)</span></span>
<span data-ttu-id="76f14-103">根据表达式的值运行若干组语句中的一个。</span><span class="sxs-lookup"><span data-stu-id="76f14-103">Runs one of several groups of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76f14-104">语法</span><span class="sxs-lookup"><span data-stu-id="76f14-104">Syntax</span></span>  
  
```vb  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a><span data-ttu-id="76f14-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="76f14-105">Parts</span></span>  
  
|<span data-ttu-id="76f14-106">术语</span><span class="sxs-lookup"><span data-stu-id="76f14-106">Term</span></span>|<span data-ttu-id="76f14-107">定义</span><span class="sxs-lookup"><span data-stu-id="76f14-107">Definition</span></span>|  
|---|---|  
|`testexpression`|<span data-ttu-id="76f14-108">必需。</span><span class="sxs-lookup"><span data-stu-id="76f14-108">Required.</span></span> <span data-ttu-id="76f14-109">表达式。</span><span class="sxs-lookup"><span data-stu-id="76f14-109">Expression.</span></span> <span data-ttu-id="76f14-110">的计算结果必须为其中一种基本数据类型（、、、、、、、、、、、、、、 `Boolean` `Byte` `Char` `Date` `Double` `Decimal` `Integer` `Long` `Object` `SByte` `Short` `Single` `String` `UInteger` `ULong` 和 `UShort` ）。</span><span class="sxs-lookup"><span data-stu-id="76f14-110">Must evaluate to one of the elementary data types (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, and `UShort`).</span></span>|  
|`expressionlist`|<span data-ttu-id="76f14-111">在语句中是必需的 `Case` 。</span><span class="sxs-lookup"><span data-stu-id="76f14-111">Required in a `Case` statement.</span></span> <span data-ttu-id="76f14-112">表示的匹配值的表达式子句的列表 `testexpression` 。</span><span class="sxs-lookup"><span data-stu-id="76f14-112">List of expression clauses representing match values for `testexpression`.</span></span> <span data-ttu-id="76f14-113">多个表达式子句之间用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="76f14-113">Multiple expression clauses are separated by commas.</span></span> <span data-ttu-id="76f14-114">每个子句可以采用以下形式之一：</span><span class="sxs-lookup"><span data-stu-id="76f14-114">Each clause can take one of the following forms:</span></span><br /><br /> <span data-ttu-id="76f14-115">-   *表达式* `To` =*表达式*2</span><span class="sxs-lookup"><span data-stu-id="76f14-115">-   *expression1* `To` *expression2*</span></span><br /><span data-ttu-id="76f14-116">-[ `Is` ] *.comparisonoperator* *表达式*</span><span class="sxs-lookup"><span data-stu-id="76f14-116">-   [ `Is` ] *comparisonoperator* *expression*</span></span><br /><span data-ttu-id="76f14-117">-   *表达式*</span><span class="sxs-lookup"><span data-stu-id="76f14-117">-   *expression*</span></span><br /><br /> <span data-ttu-id="76f14-118">使用 `To` 关键字可以指定的匹配值范围的边界 `testexpression` 。</span><span class="sxs-lookup"><span data-stu-id="76f14-118">Use the `To` keyword to specify the boundaries of a range of match values for `testexpression`.</span></span> <span data-ttu-id="76f14-119">的值 `expression1` 必须小于或等于的值 `expression2` 。</span><span class="sxs-lookup"><span data-stu-id="76f14-119">The value of `expression1` must be less than or equal to the value of `expression2`.</span></span><br /><br /> <span data-ttu-id="76f14-120">使用 `Is` 关键字和比较运算符（ `=` 、 `<>` 、、、 `<` `<=` `>` 或 `>=` ）来指定对的匹配值的限制 `testexpression` 。</span><span class="sxs-lookup"><span data-stu-id="76f14-120">Use the `Is` keyword with a comparison operator (`=`, `<>`, `<`, `<=`, `>`, or `>=`) to specify a restriction on the match values for `testexpression`.</span></span> <span data-ttu-id="76f14-121">如果 `Is` 未提供关键字，则自动将其插入 *.comparisonoperator*之前。</span><span class="sxs-lookup"><span data-stu-id="76f14-121">If the `Is` keyword is not supplied, it is automatically inserted before *comparisonoperator*.</span></span><br /><br /> <span data-ttu-id="76f14-122">仅指定的窗体 `expression` 被视为窗体的一种特殊情况 `Is` ，其中 *.comparisonoperator*是等号（ `=` ）。</span><span class="sxs-lookup"><span data-stu-id="76f14-122">The form specifying only `expression` is treated as a special case of the `Is` form where *comparisonoperator* is the equal sign (`=`).</span></span> <span data-ttu-id="76f14-123">此形式的计算结果为 `testexpression`  =  `expression` 。</span><span class="sxs-lookup"><span data-stu-id="76f14-123">This form is evaluated as `testexpression` = `expression`.</span></span><br /><br /> <span data-ttu-id="76f14-124">中的表达式 `expressionlist` 可以是任何数据类型，前提是它们可隐式转换为的类型 `testexpression` ，并且相应的 `comparisonoperator` 对于与之一起使用的两种类型都有效。</span><span class="sxs-lookup"><span data-stu-id="76f14-124">The expressions in `expressionlist` can be of any data type, provided they are implicitly convertible to the type of `testexpression` and the appropriate `comparisonoperator` is valid for the two types it is being used with.</span></span>|  
|`statements`|<span data-ttu-id="76f14-125">可选。</span><span class="sxs-lookup"><span data-stu-id="76f14-125">Optional.</span></span> <span data-ttu-id="76f14-126">`Case`如果 `testexpression` 与中的任何子句匹配，则为运行的一个或多个语句 `expressionlist` 。</span><span class="sxs-lookup"><span data-stu-id="76f14-126">One or more statements following `Case` that run if `testexpression` matches any clause in `expressionlist`.</span></span>|  
|`elsestatements`|<span data-ttu-id="76f14-127">可选。</span><span class="sxs-lookup"><span data-stu-id="76f14-127">Optional.</span></span> <span data-ttu-id="76f14-128">`Case Else`如果不 `testexpression` 与任何语句的中的任何子句匹配，则为运行的一个或多个语句 `expressionlist` `Case` 。</span><span class="sxs-lookup"><span data-stu-id="76f14-128">One or more statements following `Case Else` that run if `testexpression` does not match any clause in the `expressionlist` of any of the `Case` statements.</span></span>|  
|`End Select`|<span data-ttu-id="76f14-129">终止 `Select` ... 构造的定义。 `Case`</span><span class="sxs-lookup"><span data-stu-id="76f14-129">Terminates the definition of the `Select`...`Case` construction.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76f14-130">备注</span><span class="sxs-lookup"><span data-stu-id="76f14-130">Remarks</span></span>  
 <span data-ttu-id="76f14-131">如果 `testexpression` 与 any `Case` `expressionlist` 子句匹配，则该语句后面的语句将 `Case` 运行到下一个 `Case` 、 `Case Else` 或 `End Select` 语句。</span><span class="sxs-lookup"><span data-stu-id="76f14-131">If `testexpression` matches any `Case` `expressionlist` clause, the statements following that `Case` statement run up to the next `Case`, `Case Else`, or `End Select` statement.</span></span> <span data-ttu-id="76f14-132">然后，控制将传递到后面的语句 `End Select` 。</span><span class="sxs-lookup"><span data-stu-id="76f14-132">Control then passes to the statement following `End Select`.</span></span> <span data-ttu-id="76f14-133">如果 `testexpression` `expressionlist` 在多个子句中匹配某个子句 `Case` ，则只运行第一个匹配后的语句。</span><span class="sxs-lookup"><span data-stu-id="76f14-133">If `testexpression` matches an `expressionlist` clause in more than one `Case` clause, only the statements following the first match run.</span></span>  
  
 <span data-ttu-id="76f14-134">`Case Else` `elsestatements` 如果在 `testexpression` `expressionlist` 任何其他语句中的和子句之间找不到匹配项，则该语句用于引入要运行的 `Case` 。</span><span class="sxs-lookup"><span data-stu-id="76f14-134">The `Case Else` statement is used to introduce the `elsestatements` to run if no match is found between the `testexpression` and an `expressionlist` clause in any of the other `Case` statements.</span></span> <span data-ttu-id="76f14-135">尽管这不是必需的，但最好 `Case Else` 在构造中具有语句 `Select Case` 来处理不可预见的 `testexpression` 值。</span><span class="sxs-lookup"><span data-stu-id="76f14-135">Although not required, it is a good idea to have a `Case Else` statement in your `Select Case` construction to handle unforeseen `testexpression` values.</span></span> <span data-ttu-id="76f14-136">如果没有任何 `Case` `expressionlist` 子句匹配 `testexpression` 并且没有 `Case Else` 语句，控制将传递到后面的语句 `End Select` 。</span><span class="sxs-lookup"><span data-stu-id="76f14-136">If no `Case` `expressionlist` clause matches `testexpression` and there is no `Case Else` statement, control passes to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="76f14-137">可以在每个子句中使用多个表达式或范围 `Case` 。</span><span class="sxs-lookup"><span data-stu-id="76f14-137">You can use multiple expressions or ranges in each `Case` clause.</span></span> <span data-ttu-id="76f14-138">例如，下面的行是有效的。</span><span class="sxs-lookup"><span data-stu-id="76f14-138">For example, the following line is valid.</span></span>  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> <span data-ttu-id="76f14-139">`Is`和语句中使用的关键字与 `Case` `Case Else` [is 运算符](../operators/is-operator.md)不同，后者用于对象引用比较。</span><span class="sxs-lookup"><span data-stu-id="76f14-139">The `Is` keyword used in the `Case` and `Case Else` statements is not the same as the [Is Operator](../operators/is-operator.md), which is used for object reference comparison.</span></span>  
  
 <span data-ttu-id="76f14-140">您可以为字符串指定范围和多个表达式。</span><span class="sxs-lookup"><span data-stu-id="76f14-140">You can specify ranges and multiple expressions for character strings.</span></span> <span data-ttu-id="76f14-141">在下面的示例中， `Case` 匹配任何完全等于 "苹果" 的字符串，其值介于 "螺母" 和 "soup" 之间的字母顺序之间，或包含与当前值完全相同的值 `testItem` 。</span><span class="sxs-lookup"><span data-stu-id="76f14-141">In the following example, `Case` matches any string that is exactly equal to "apples", has a value between "nuts" and "soup" in alphabetical order, or contains the exact same value as the current value of `testItem`.</span></span>  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 <span data-ttu-id="76f14-142">的设置 `Option Compare` 可能会影响字符串比较。</span><span class="sxs-lookup"><span data-stu-id="76f14-142">The setting of `Option Compare` can affect string comparisons.</span></span> <span data-ttu-id="76f14-143">在下 `Option Compare Text` ，字符串 "苹果" 和 "苹果" 比较视为相等，但在下， `Option Compare Binary` 它们不会。</span><span class="sxs-lookup"><span data-stu-id="76f14-143">Under `Option Compare Text`, the strings "Apples" and "apples" compare as equal, but under `Option Compare Binary`, they do not.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76f14-144">`Case`具有多个子句的语句可以表现称为 "*短路*" 的行为。</span><span class="sxs-lookup"><span data-stu-id="76f14-144">A `Case` statement with multiple clauses can exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="76f14-145">Visual Basic 从左到右计算子句的值，并且如果一个语句生成匹配项 `testexpression` ，则不会计算剩余的子句。</span><span class="sxs-lookup"><span data-stu-id="76f14-145">Visual Basic evaluates the clauses from left to right, and if one produces a match with `testexpression`, the remaining clauses are not evaluated.</span></span> <span data-ttu-id="76f14-146">短路可以提高性能，但如果希望计算中的每个表达式，则可能产生意外的结果 `expressionlist` 。</span><span class="sxs-lookup"><span data-stu-id="76f14-146">Short-circuiting can improve performance, but it can produce unexpected results if you are expecting every expression in `expressionlist` to be evaluated.</span></span> <span data-ttu-id="76f14-147">有关短路的详细信息，请参阅[布尔表达式](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="76f14-147">For more information on short-circuiting, see [Boolean Expressions](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span></span>  
  
 <span data-ttu-id="76f14-148">如果 `Case` 或语句块内的代码 `Case Else` 不需要在块中运行任何更多语句，则可以使用语句退出块 `Exit Select` 。</span><span class="sxs-lookup"><span data-stu-id="76f14-148">If the code within a `Case` or `Case Else` statement block does not need to run any more of the statements in the block, it can exit the block by using the `Exit Select` statement.</span></span> <span data-ttu-id="76f14-149">这会将控制立即传输到后面的语句 `End Select` 。</span><span class="sxs-lookup"><span data-stu-id="76f14-149">This transfers control immediately to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="76f14-150">`Select Case`构造可以嵌套。</span><span class="sxs-lookup"><span data-stu-id="76f14-150">`Select Case` constructions can be nested.</span></span> <span data-ttu-id="76f14-151">每个嵌套 `Select Case` 构造都必须具有匹配的 `End Select` 语句，并且必须完全包含在 `Case` `Case Else` 嵌套它的外部构造的单个或语句块内 `Select Case` 。</span><span class="sxs-lookup"><span data-stu-id="76f14-151">Each nested `Select Case` construction must have a matching `End Select` statement and must be completely contained within a single `Case` or `Case Else` statement block of the outer `Select Case` construction within which it is nested.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76f14-152">示例</span><span class="sxs-lookup"><span data-stu-id="76f14-152">Example</span></span>  
 <span data-ttu-id="76f14-153">下面的示例使用 `Select Case` 构造来编写与变量的值相对应的行 `number` 。</span><span class="sxs-lookup"><span data-stu-id="76f14-153">The following example uses a `Select Case` construction to write a line corresponding to the value of the variable `number`.</span></span> <span data-ttu-id="76f14-154">第二个 `Case` 语句包含的值与的当前值匹配 `number` ，因此将运行写入 "6 到8个（含）" 的语句。</span><span class="sxs-lookup"><span data-stu-id="76f14-154">The second `Case` statement contains the value that matches the current value of `number`, so the statement that writes "Between 6 and 8, inclusive" runs.</span></span>  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a><span data-ttu-id="76f14-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76f14-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [<span data-ttu-id="76f14-156">End 语句</span><span class="sxs-lookup"><span data-stu-id="76f14-156">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="76f14-157">If...Then...Else 语句</span><span class="sxs-lookup"><span data-stu-id="76f14-157">If...Then...Else Statement</span></span>](if-then-else-statement.md)
- [<span data-ttu-id="76f14-158">Option Compare 语句</span><span class="sxs-lookup"><span data-stu-id="76f14-158">Option Compare Statement</span></span>](option-compare-statement.md)
- [<span data-ttu-id="76f14-159">Exit 语句</span><span class="sxs-lookup"><span data-stu-id="76f14-159">Exit Statement</span></span>](exit-statement.md)
