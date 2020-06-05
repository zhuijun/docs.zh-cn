---
title: Function 过程
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: b0ba96a875fd8785e45eee565beefe4b961ffc9d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388746"
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="a2760-102">Function 过程（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="a2760-102">Function procedures (Visual Basic)</span></span>

<span data-ttu-id="a2760-103">`Function`过程是由和语句括起来的一系列 Visual Basic `Function` 语句 `End Function` 。</span><span class="sxs-lookup"><span data-stu-id="a2760-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="a2760-104">该 `Function` 过程执行任务，然后将控制权返回给调用代码。</span><span class="sxs-lookup"><span data-stu-id="a2760-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="a2760-105">当它返回 control 时，它还会将值返回到调用代码。</span><span class="sxs-lookup"><span data-stu-id="a2760-105">When it returns control, it also returns a value to the calling code.</span></span>

<span data-ttu-id="a2760-106">每次调用该过程时，其语句都会运行，从语句后面的第一个可执行语句开始， `Function` 到遇到的第一个 `End Function` 、 `Exit Function` 或 `Return` 语句结束。</span><span class="sxs-lookup"><span data-stu-id="a2760-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>

<span data-ttu-id="a2760-107">您可以 `Function` 在模块、类或结构中定义过程。</span><span class="sxs-lookup"><span data-stu-id="a2760-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="a2760-108">`Public`默认情况下，这意味着您可以从应用程序中可以访问您定义它的模块、类或结构的任何位置调用它。</span><span class="sxs-lookup"><span data-stu-id="a2760-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>

<span data-ttu-id="a2760-109">`Function`过程可以采用由调用代码传递给它的参数，如常量、变量或表达式。</span><span class="sxs-lookup"><span data-stu-id="a2760-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="a2760-110">声明语法</span><span class="sxs-lookup"><span data-stu-id="a2760-110">Declaration syntax</span></span>

<span data-ttu-id="a2760-111">声明过程的语法如下所示 `Function` ：</span><span class="sxs-lookup"><span data-stu-id="a2760-111">The syntax for declaring a `Function` procedure is as follows:</span></span>

```vb
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType
    [Statements]
End Function
```

<span data-ttu-id="a2760-112">*修饰符*可以指定有关重载、重写、共享和隐藏的访问级别和信息。</span><span class="sxs-lookup"><span data-stu-id="a2760-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="a2760-113">有关详细信息，请参阅[函数语句](../../../language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="a2760-113">For more information, see [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>

<span data-ttu-id="a2760-114">声明每个参数的方式与处理[Sub 过程](./sub-procedures.md)的方式相同。</span><span class="sxs-lookup"><span data-stu-id="a2760-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="a2760-115">数据类型</span><span class="sxs-lookup"><span data-stu-id="a2760-115">Data type</span></span>

<span data-ttu-id="a2760-116">每个 `Function` 过程都有一种数据类型，就像每个变量一样。</span><span class="sxs-lookup"><span data-stu-id="a2760-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="a2760-117">此数据类型由 `As` 语句中的子句指定 `Function` ，它确定函数返回到调用代码的值的数据类型。</span><span class="sxs-lookup"><span data-stu-id="a2760-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="a2760-118">下面的示例声明阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="a2760-118">The following sample declarations illustrate this.</span></span>

```vb
Function Yesterday() As Date
End Function

Function FindSqrt(radicand As Single) As Single
End Function
```

<span data-ttu-id="a2760-119">有关详细信息，请参阅[Function 语句](../../../language-reference/statements/function-statement.md)中的 "part"。</span><span class="sxs-lookup"><span data-stu-id="a2760-119">For more information, see "Parts" in [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>

### <a name="returning-values"></a><span data-ttu-id="a2760-120">返回值</span><span class="sxs-lookup"><span data-stu-id="a2760-120">Returning values</span></span>

<span data-ttu-id="a2760-121">`Function`过程返回到调用代码的值称为其返回值。</span><span class="sxs-lookup"><span data-stu-id="a2760-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="a2760-122">此过程通过以下两种方式之一返回此值：</span><span class="sxs-lookup"><span data-stu-id="a2760-122">The procedure returns this value in one of two ways:</span></span>

- <span data-ttu-id="a2760-123">它使用 `Return` 语句来指定返回值，并立即将控制权返回给调用程序。</span><span class="sxs-lookup"><span data-stu-id="a2760-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="a2760-124">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="a2760-124">The following example illustrates this.</span></span>

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement immediately transfers control back
      ' to the calling code and returns the value of Expression.
      Return Expression
  End Function
  ```

- <span data-ttu-id="a2760-125">它在过程的一个或多个语句中为其自己的函数名称赋值。</span><span class="sxs-lookup"><span data-stu-id="a2760-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="a2760-126">直到 `Exit Function` 执行或语句后，控件才会返回到调用程序 `End Function` 。</span><span class="sxs-lookup"><span data-stu-id="a2760-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="a2760-127">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="a2760-127">The following example illustrates this.</span></span>

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement does not transfer control back to the calling code.
      FunctionName = Expression
      ' When control returns to the calling code, Expression is the return value.
  End Function
  ```

<span data-ttu-id="a2760-128">将返回值分配给函数名称的优点是，在遇到或语句之前，控件不会从过程返回 `Exit Function` `End Function` 。</span><span class="sxs-lookup"><span data-stu-id="a2760-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="a2760-129">这使您可以分配一个初步的值并在以后必要时进行调整。</span><span class="sxs-lookup"><span data-stu-id="a2760-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>

<span data-ttu-id="a2760-130">有关返回值的详细信息，请参阅[函数语句](../../../language-reference/statements/function-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="a2760-130">For more information about returning values, see [Function Statement](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="a2760-131">有关返回数组的信息，请参阅[数组](../arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a2760-131">For information about returning arrays, see [Arrays](../arrays/index.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="a2760-132">调用语法</span><span class="sxs-lookup"><span data-stu-id="a2760-132">Calling syntax</span></span>

<span data-ttu-id="a2760-133">`Function`通过在赋值语句或表达式的右侧包含其名称和参数来调用过程。</span><span class="sxs-lookup"><span data-stu-id="a2760-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="a2760-134">必须为所有非可选参数提供值，并且必须将参数列表括在括号中。</span><span class="sxs-lookup"><span data-stu-id="a2760-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="a2760-135">如果未提供任何参数，则可以选择省略括号。</span><span class="sxs-lookup"><span data-stu-id="a2760-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="a2760-136">对过程的调用语法如下所示 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="a2760-136">The syntax for a call to a `Function` procedure is as follows.</span></span>

<span data-ttu-id="a2760-137">*lvalue* `=`*functionname* `[(`*argumentlist*    `)]`</span><span class="sxs-lookup"><span data-stu-id="a2760-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>

<span data-ttu-id="a2760-138">`If ((`*functionname* `[(`*argumentlist* `)] / 3) <=`*表达式*  `) Then`</span><span class="sxs-lookup"><span data-stu-id="a2760-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>

<span data-ttu-id="a2760-139">调用 `Function` 过程时，无需使用其返回值。</span><span class="sxs-lookup"><span data-stu-id="a2760-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="a2760-140">否则，将执行该函数的所有操作，但将忽略返回值。</span><span class="sxs-lookup"><span data-stu-id="a2760-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="a2760-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>通常以这种方式调用。</span><span class="sxs-lookup"><span data-stu-id="a2760-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="a2760-142">声明和调用的插图</span><span class="sxs-lookup"><span data-stu-id="a2760-142">Illustration of declaration and call</span></span>

<span data-ttu-id="a2760-143">下面的 `Function` 过程计算直角三角形的最长边（或斜边），并给出另一方的值。</span><span class="sxs-lookup"><span data-stu-id="a2760-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>

[!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

<span data-ttu-id="a2760-144">下面的示例演示对的典型调用 `hypotenuse` 。</span><span class="sxs-lookup"><span data-stu-id="a2760-144">The following example shows a typical call to `hypotenuse`.</span></span>

[!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]

## <a name="see-also"></a><span data-ttu-id="a2760-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a2760-145">See also</span></span>

- [<span data-ttu-id="a2760-146">过程</span><span class="sxs-lookup"><span data-stu-id="a2760-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="a2760-147">Sub 过程</span><span class="sxs-lookup"><span data-stu-id="a2760-147">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="a2760-148">Property 过程</span><span class="sxs-lookup"><span data-stu-id="a2760-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="a2760-149">运算符过程</span><span class="sxs-lookup"><span data-stu-id="a2760-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="a2760-150">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="a2760-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="a2760-151">Function 语句</span><span class="sxs-lookup"><span data-stu-id="a2760-151">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="a2760-152">如何：创建返回值的过程</span><span class="sxs-lookup"><span data-stu-id="a2760-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="a2760-153">如何：从过程返回值</span><span class="sxs-lookup"><span data-stu-id="a2760-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="a2760-154">如何：调用返回值的过程</span><span class="sxs-lookup"><span data-stu-id="a2760-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
