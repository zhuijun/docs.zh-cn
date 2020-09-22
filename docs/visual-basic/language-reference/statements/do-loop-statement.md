---
title: Do...Loop 语句
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: 86a702aefeea1e5e359a579a3f29e9c06f1c619c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90865931"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="5f160-102">Do...Loop 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f160-102">Do...Loop Statement (Visual Basic)</span></span>

<span data-ttu-id="5f160-103">当 `Boolean` 条件为 `True` 或在条件变为之前，重复语句块 `True` 。</span><span class="sxs-lookup"><span data-stu-id="5f160-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f160-104">语法</span><span class="sxs-lookup"><span data-stu-id="5f160-104">Syntax</span></span>  
  
```vb  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
' -or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a><span data-ttu-id="5f160-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="5f160-105">Parts</span></span>  
  
|<span data-ttu-id="5f160-106">术语</span><span class="sxs-lookup"><span data-stu-id="5f160-106">Term</span></span>|<span data-ttu-id="5f160-107">定义</span><span class="sxs-lookup"><span data-stu-id="5f160-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="5f160-108">必需。</span><span class="sxs-lookup"><span data-stu-id="5f160-108">Required.</span></span> <span data-ttu-id="5f160-109">开始循环的定义 `Do` 。</span><span class="sxs-lookup"><span data-stu-id="5f160-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="5f160-110">必选项（除非使用了 `Until`）。</span><span class="sxs-lookup"><span data-stu-id="5f160-110">Required unless `Until` is used.</span></span> <span data-ttu-id="5f160-111">重复循环，直到 `condition` 为为止 `False` 。</span><span class="sxs-lookup"><span data-stu-id="5f160-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="5f160-112">必选项（除非使用了 `While`）。</span><span class="sxs-lookup"><span data-stu-id="5f160-112">Required unless `While` is used.</span></span> <span data-ttu-id="5f160-113">重复循环，直到 `condition` 为为止 `True` 。</span><span class="sxs-lookup"><span data-stu-id="5f160-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="5f160-114">可选。</span><span class="sxs-lookup"><span data-stu-id="5f160-114">Optional.</span></span> <span data-ttu-id="5f160-115">`Boolean` 表达式。</span><span class="sxs-lookup"><span data-stu-id="5f160-115">`Boolean` expression.</span></span> <span data-ttu-id="5f160-116">如果 `condition` 为 `Nothing` ，则 Visual Basic 将其视为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="5f160-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="5f160-117">可选。</span><span class="sxs-lookup"><span data-stu-id="5f160-117">Optional.</span></span> <span data-ttu-id="5f160-118">一个或多个重复的语句，或在之前重复 `condition` `True` 。</span><span class="sxs-lookup"><span data-stu-id="5f160-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="5f160-119">可选。</span><span class="sxs-lookup"><span data-stu-id="5f160-119">Optional.</span></span> <span data-ttu-id="5f160-120">将控制转移到循环的下一次迭代 `Do` 。</span><span class="sxs-lookup"><span data-stu-id="5f160-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="5f160-121">可选。</span><span class="sxs-lookup"><span data-stu-id="5f160-121">Optional.</span></span> <span data-ttu-id="5f160-122">将控制转移到 `Do` 循环外。</span><span class="sxs-lookup"><span data-stu-id="5f160-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="5f160-123">必需。</span><span class="sxs-lookup"><span data-stu-id="5f160-123">Required.</span></span> <span data-ttu-id="5f160-124">终止循环的定义 `Do` 。</span><span class="sxs-lookup"><span data-stu-id="5f160-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f160-125">备注</span><span class="sxs-lookup"><span data-stu-id="5f160-125">Remarks</span></span>  

 <span data-ttu-id="5f160-126">`Do...Loop`如果希望在满足条件之前重复一组语句，请使用结构。</span><span class="sxs-lookup"><span data-stu-id="5f160-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="5f160-127">如果要将语句重复一组次数 [，则下一条语句](for-next-statement.md) 通常是更好的选择。</span><span class="sxs-lookup"><span data-stu-id="5f160-127">If you want to repeat the statements a set number of times, the [For...Next Statement](for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="5f160-128">您可以使用 `While` 或 `Until` 来指定 `condition` ，但不能同时使用两者。</span><span class="sxs-lookup"><span data-stu-id="5f160-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="5f160-129">只能 `condition` 在循环的开头或结尾测试一次。</span><span class="sxs-lookup"><span data-stu-id="5f160-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="5f160-130">如果在 `condition` 语句) 中测试循环 (`Do` ，则循环可能不会运行一次。</span><span class="sxs-lookup"><span data-stu-id="5f160-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="5f160-131">如果在语句) 中测试循环 (`Loop` ，则循环始终运行至少一次。</span><span class="sxs-lookup"><span data-stu-id="5f160-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="5f160-132">这种情况通常是由两个值比较导致的，但它可以是计算结果为 [布尔数据类型](../data-types/boolean-data-type.md) 值 (或) 的任何表达式 `True` `False` 。</span><span class="sxs-lookup"><span data-stu-id="5f160-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="5f160-133">这包括已转换为的其他数据类型（如数值类型）的值 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="5f160-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="5f160-134">可以 `Do` 通过在另一个循环中放置循环来嵌套循环。</span><span class="sxs-lookup"><span data-stu-id="5f160-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="5f160-135">您还可以在彼此之间嵌套不同种类的控制结构。</span><span class="sxs-lookup"><span data-stu-id="5f160-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="5f160-136">有关详细信息，请参阅 [嵌套控制结构](../../programming-guide/language-features/control-flow/nested-control-structures.md)。</span><span class="sxs-lookup"><span data-stu-id="5f160-136">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f160-137">此 `Do...Loop` 结构提供的灵活性比 [.。。End While 语句](while-end-while-statement.md) ，因为它可用于决定是在 `condition` 停止时 `True` 还是在第一次变为时结束循环 `True` 。</span><span class="sxs-lookup"><span data-stu-id="5f160-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="5f160-138">它还使你能够 `condition` 在循环的开头或结尾进行测试。</span><span class="sxs-lookup"><span data-stu-id="5f160-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="5f160-139">退出 Do</span><span class="sxs-lookup"><span data-stu-id="5f160-139">Exit Do</span></span>  

 <span data-ttu-id="5f160-140">[Exit Do](exit-statement.md)语句可以提供退出的替代方法 `Do…Loop` 。</span><span class="sxs-lookup"><span data-stu-id="5f160-140">The [Exit Do](exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="5f160-141">`Exit Do` 将控制立即传输到语句后面的语句 `Loop` 。</span><span class="sxs-lookup"><span data-stu-id="5f160-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="5f160-142">`Exit Do` 通常在计算某些条件后（例如在结构中）使用 `If...Then...Else` 。</span><span class="sxs-lookup"><span data-stu-id="5f160-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="5f160-143">如果检测到可能导致不必要或无法继续迭代的条件（如错误值或终止请求），则可能需要退出循环。</span><span class="sxs-lookup"><span data-stu-id="5f160-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="5f160-144">的一种用途 `Exit Do` 是测试可能导致 *无限循环*的情况，这是一个可运行很大甚至无限次数的循环。</span><span class="sxs-lookup"><span data-stu-id="5f160-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="5f160-145">您可以使用 `Exit Do` 来转义循环。</span><span class="sxs-lookup"><span data-stu-id="5f160-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="5f160-146">可以在中的任意位置包含任意数量的 `Exit Do` 语句 `Do…Loop` 。</span><span class="sxs-lookup"><span data-stu-id="5f160-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="5f160-147">在嵌套循环内使用时 `Do` ， `Exit Do` 将控制转移出最内层循环，并将其转移到下一个更高的嵌套级别。</span><span class="sxs-lookup"><span data-stu-id="5f160-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f160-148">示例</span><span class="sxs-lookup"><span data-stu-id="5f160-148">Example</span></span>  

 <span data-ttu-id="5f160-149">在下面的示例中，循环中的语句将继续运行，直到 `index` 变量大于10。</span><span class="sxs-lookup"><span data-stu-id="5f160-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="5f160-150">`Until`子句位于循环的结尾。</span><span class="sxs-lookup"><span data-stu-id="5f160-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="5f160-151">示例</span><span class="sxs-lookup"><span data-stu-id="5f160-151">Example</span></span>  

 <span data-ttu-id="5f160-152">下面的示例使用 `While` 子句而不是 `Until` 子句，并 `condition` 在循环的开头而不是在结束时进行测试。</span><span class="sxs-lookup"><span data-stu-id="5f160-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="5f160-153">示例</span><span class="sxs-lookup"><span data-stu-id="5f160-153">Example</span></span>  

 <span data-ttu-id="5f160-154">在下面的示例中， `condition` 当 `index` 变量大于100时停止循环。</span><span class="sxs-lookup"><span data-stu-id="5f160-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="5f160-155">`If`但是，循环中的语句会导致语句在 `Exit Do` 索引变量大于10时停止循环。</span><span class="sxs-lookup"><span data-stu-id="5f160-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="5f160-156">示例</span><span class="sxs-lookup"><span data-stu-id="5f160-156">Example</span></span>  

 <span data-ttu-id="5f160-157">下面的示例读取文本文件中的所有行。</span><span class="sxs-lookup"><span data-stu-id="5f160-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="5f160-158"><xref:System.IO.File.OpenText%2A>方法打开文件并返回 <xref:System.IO.StreamReader> 读取字符的。</span><span class="sxs-lookup"><span data-stu-id="5f160-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="5f160-159">在 `Do...Loop` 条件中，的 <xref:System.IO.StreamReader.Peek%2A> 方法 `StreamReader` 确定是否有任何其他字符。</span><span class="sxs-lookup"><span data-stu-id="5f160-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="5f160-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f160-160">See also</span></span>

- [<span data-ttu-id="5f160-161">循环结构</span><span class="sxs-lookup"><span data-stu-id="5f160-161">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="5f160-162">For...Next 语句</span><span class="sxs-lookup"><span data-stu-id="5f160-162">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="5f160-163">布尔数据类型</span><span class="sxs-lookup"><span data-stu-id="5f160-163">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="5f160-164">嵌套的控件结构</span><span class="sxs-lookup"><span data-stu-id="5f160-164">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="5f160-165">Exit 语句</span><span class="sxs-lookup"><span data-stu-id="5f160-165">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="5f160-166">While...End While 语句</span><span class="sxs-lookup"><span data-stu-id="5f160-166">While...End While Statement</span></span>](while-end-while-statement.md)
