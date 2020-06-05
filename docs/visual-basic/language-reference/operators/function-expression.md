---
title: 函数表达式
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: a9b621ff03f833fcf0f07f876fd864ee963bef75
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371176"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="a8db6-102">函数表达式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8db6-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="a8db6-103">声明定义函数 lambda 表达式的参数和代码。</span><span class="sxs-lookup"><span data-stu-id="a8db6-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8db6-104">语法</span><span class="sxs-lookup"><span data-stu-id="a8db6-104">Syntax</span></span>  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="a8db6-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="a8db6-105">Parts</span></span>  
  
|<span data-ttu-id="a8db6-106">术语</span><span class="sxs-lookup"><span data-stu-id="a8db6-106">Term</span></span>|<span data-ttu-id="a8db6-107">定义</span><span class="sxs-lookup"><span data-stu-id="a8db6-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="a8db6-108">可选。</span><span class="sxs-lookup"><span data-stu-id="a8db6-108">Optional.</span></span> <span data-ttu-id="a8db6-109">表示此过程参数的局部变量名称的列表。</span><span class="sxs-lookup"><span data-stu-id="a8db6-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="a8db6-110">即使此列表为空，也必须存在括号。</span><span class="sxs-lookup"><span data-stu-id="a8db6-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="a8db6-111">请参阅[参数列表](../statements/parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="a8db6-111">See [Parameter List](../statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="a8db6-112">必需。</span><span class="sxs-lookup"><span data-stu-id="a8db6-112">Required.</span></span> <span data-ttu-id="a8db6-113">单个表达式。</span><span class="sxs-lookup"><span data-stu-id="a8db6-113">A single expression.</span></span> <span data-ttu-id="a8db6-114">表达式的类型为函数的返回类型。</span><span class="sxs-lookup"><span data-stu-id="a8db6-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="a8db6-115">必需。</span><span class="sxs-lookup"><span data-stu-id="a8db6-115">Required.</span></span> <span data-ttu-id="a8db6-116">使用语句返回值的语句列表 `Return` 。</span><span class="sxs-lookup"><span data-stu-id="a8db6-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="a8db6-117">（请参见[Return 语句](../statements/return-statement.md)。）返回的值的类型为函数的返回类型。</span><span class="sxs-lookup"><span data-stu-id="a8db6-117">(See [Return Statement](../statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8db6-118">备注</span><span class="sxs-lookup"><span data-stu-id="a8db6-118">Remarks</span></span>  
 <span data-ttu-id="a8db6-119">*Lambda 表达式*是没有名称的函数，用于计算并返回值。</span><span class="sxs-lookup"><span data-stu-id="a8db6-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="a8db6-120">可以在可以使用委托类型的任何位置使用 lambda 表达式，但不能使用作为的参数 `RemoveHandler` 。</span><span class="sxs-lookup"><span data-stu-id="a8db6-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="a8db6-121">有关委托的详细信息以及对委托使用 lambda 表达式的详细信息，请参阅[委托语句](../statements/delegate-statement.md)和[宽松委托转换](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="a8db6-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="a8db6-122">Lambda 表达式语法</span><span class="sxs-lookup"><span data-stu-id="a8db6-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="a8db6-123">Lambda 表达式的语法与标准函数的语法类似。</span><span class="sxs-lookup"><span data-stu-id="a8db6-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="a8db6-124">不同之处如下：</span><span class="sxs-lookup"><span data-stu-id="a8db6-124">The differences are as follows:</span></span>  
  
- <span data-ttu-id="a8db6-125">Lambda 表达式没有名称。</span><span class="sxs-lookup"><span data-stu-id="a8db6-125">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="a8db6-126">Lambda 表达式不能具有修饰符，如 `Overloads` 或 `Overrides` 。</span><span class="sxs-lookup"><span data-stu-id="a8db6-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="a8db6-127">Lambda 表达式不使用 `As` 子句来指定函数的返回类型。</span><span class="sxs-lookup"><span data-stu-id="a8db6-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="a8db6-128">相反，该类型是从单行 lambda 表达式的主体计算得出的值推断出的，或是多行 lambda 表达式的返回值。</span><span class="sxs-lookup"><span data-stu-id="a8db6-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="a8db6-129">例如，如果单行 lambda 表达式的主体为 `Where cust.City = "London"` ，则其返回类型为 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="a8db6-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
- <span data-ttu-id="a8db6-130">单行 lambda 表达式的主体必须是表达式，而不是语句。</span><span class="sxs-lookup"><span data-stu-id="a8db6-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="a8db6-131">正文可以包含对 function 过程的调用，但不能包含对 sub 过程的调用。</span><span class="sxs-lookup"><span data-stu-id="a8db6-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
- <span data-ttu-id="a8db6-132">所有参数都必须具有指定的数据类型，或者都必须被推断。</span><span class="sxs-lookup"><span data-stu-id="a8db6-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
- <span data-ttu-id="a8db6-133">不允许使用可选参数和 Paramarray 参数。</span><span class="sxs-lookup"><span data-stu-id="a8db6-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
- <span data-ttu-id="a8db6-134">不允许使用泛型参数。</span><span class="sxs-lookup"><span data-stu-id="a8db6-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8db6-135">示例</span><span class="sxs-lookup"><span data-stu-id="a8db6-135">Example</span></span>  
 <span data-ttu-id="a8db6-136">下面的示例演示了两种创建简单 lambda 表达式的方法。</span><span class="sxs-lookup"><span data-stu-id="a8db6-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="a8db6-137">第一个使用 `Dim` 来提供函数的名称。</span><span class="sxs-lookup"><span data-stu-id="a8db6-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="a8db6-138">若要调用函数，请发送参数的值。</span><span class="sxs-lookup"><span data-stu-id="a8db6-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="a8db6-139">示例</span><span class="sxs-lookup"><span data-stu-id="a8db6-139">Example</span></span>  
 <span data-ttu-id="a8db6-140">或者，可以同时声明和运行函数。</span><span class="sxs-lookup"><span data-stu-id="a8db6-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="a8db6-141">示例</span><span class="sxs-lookup"><span data-stu-id="a8db6-141">Example</span></span>  
 <span data-ttu-id="a8db6-142">下面是递增其参数并返回值的 lambda 表达式的示例。</span><span class="sxs-lookup"><span data-stu-id="a8db6-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="a8db6-143">该示例显示了函数的单行和多行 lambda 表达式语法。</span><span class="sxs-lookup"><span data-stu-id="a8db6-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="a8db6-144">有关更多示例，请参阅[Lambda 表达式](../../programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="a8db6-144">For more examples, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="a8db6-145">示例</span><span class="sxs-lookup"><span data-stu-id="a8db6-145">Example</span></span>  
 <span data-ttu-id="a8db6-146">Lambda 表达式在语言集成查询（LINQ）中采用多个查询运算符，可以在基于方法的查询中显式使用。</span><span class="sxs-lookup"><span data-stu-id="a8db6-146">Lambda expressions underlie many of the query operators in Language-Integrated Query (LINQ), and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="a8db6-147">下面的示例演示一个典型的 LINQ 查询，然后将查询转换为方法格式。</span><span class="sxs-lookup"><span data-stu-id="a8db6-147">The following example shows a typical LINQ query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="a8db6-148">有关查询方法的详细信息，请参阅[查询](../queries/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a8db6-148">For more information about query methods, see [Queries](../queries/index.md).</span></span> <span data-ttu-id="a8db6-149">有关标准查询运算符的详细信息，请参阅[标准查询运算符概述](../../programming-guide/concepts/linq/standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a8db6-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8db6-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a8db6-150">See also</span></span>

- [<span data-ttu-id="a8db6-151">Function 语句</span><span class="sxs-lookup"><span data-stu-id="a8db6-151">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="a8db6-152">Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="a8db6-152">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="a8db6-153">运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="a8db6-153">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="a8db6-154">语句</span><span class="sxs-lookup"><span data-stu-id="a8db6-154">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="a8db6-155">值的比较</span><span class="sxs-lookup"><span data-stu-id="a8db6-155">Value Comparisons</span></span>](../../programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="a8db6-156">布尔表达式</span><span class="sxs-lookup"><span data-stu-id="a8db6-156">Boolean Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="a8db6-157">If 运算符</span><span class="sxs-lookup"><span data-stu-id="a8db6-157">If Operator</span></span>](if-operator.md)
- [<span data-ttu-id="a8db6-158">宽松委托转换</span><span class="sxs-lookup"><span data-stu-id="a8db6-158">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
