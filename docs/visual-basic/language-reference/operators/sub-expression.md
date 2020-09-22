---
title: Sub 表达式
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: e564fa3f717fc1a9f4e9961d9b3e961912a4d56b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873322"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="524a2-102">Sub 表达式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="524a2-102">Sub Expression (Visual Basic)</span></span>

<span data-ttu-id="524a2-103">声明定义子程序 lambda 表达式的参数和代码。</span><span class="sxs-lookup"><span data-stu-id="524a2-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="524a2-104">语法</span><span class="sxs-lookup"><span data-stu-id="524a2-104">Syntax</span></span>  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="524a2-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="524a2-105">Parts</span></span>  
  
|<span data-ttu-id="524a2-106">术语</span><span class="sxs-lookup"><span data-stu-id="524a2-106">Term</span></span>|<span data-ttu-id="524a2-107">定义</span><span class="sxs-lookup"><span data-stu-id="524a2-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="524a2-108">可选。</span><span class="sxs-lookup"><span data-stu-id="524a2-108">Optional.</span></span> <span data-ttu-id="524a2-109">表示过程参数的局部变量名称的列表。</span><span class="sxs-lookup"><span data-stu-id="524a2-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="524a2-110">即使此列表为空，也必须存在括号。</span><span class="sxs-lookup"><span data-stu-id="524a2-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="524a2-111">有关更多信息，请参见 [Parameter List](../statements/parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="524a2-111">For more information, see [Parameter List](../statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="524a2-112">必需。</span><span class="sxs-lookup"><span data-stu-id="524a2-112">Required.</span></span> <span data-ttu-id="524a2-113">单个语句。</span><span class="sxs-lookup"><span data-stu-id="524a2-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="524a2-114">必需。</span><span class="sxs-lookup"><span data-stu-id="524a2-114">Required.</span></span> <span data-ttu-id="524a2-115">语句的列表。</span><span class="sxs-lookup"><span data-stu-id="524a2-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="524a2-116">备注</span><span class="sxs-lookup"><span data-stu-id="524a2-116">Remarks</span></span>  

 <span data-ttu-id="524a2-117">*Lambda 表达式*是不具有名称并执行一个或多个语句的子例程。</span><span class="sxs-lookup"><span data-stu-id="524a2-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="524a2-118">可以在任何可使用委托类型的位置使用 lambda 表达式，但参数除外 `RemoveHandler` 。</span><span class="sxs-lookup"><span data-stu-id="524a2-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="524a2-119">有关委托的详细信息以及对委托使用 lambda 表达式的详细信息，请参阅 [委托语句](../statements/delegate-statement.md) 和 [宽松委托转换](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)。</span><span class="sxs-lookup"><span data-stu-id="524a2-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="524a2-120">Lambda 表达式语法</span><span class="sxs-lookup"><span data-stu-id="524a2-120">Lambda Expression Syntax</span></span>  

 <span data-ttu-id="524a2-121">Lambda 表达式的语法与标准子例程的语法相似。</span><span class="sxs-lookup"><span data-stu-id="524a2-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="524a2-122">不同之处如下：</span><span class="sxs-lookup"><span data-stu-id="524a2-122">The differences are as follows:</span></span>  
  
- <span data-ttu-id="524a2-123">Lambda 表达式没有名称。</span><span class="sxs-lookup"><span data-stu-id="524a2-123">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="524a2-124">Lambda 表达式不能具有修饰符，如 `Overloads` 或 `Overrides` 。</span><span class="sxs-lookup"><span data-stu-id="524a2-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="524a2-125">单行 lambda 表达式的主体必须是语句，而不能是表达式。</span><span class="sxs-lookup"><span data-stu-id="524a2-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="524a2-126">正文可以包含对 sub 过程的调用，但不能由对函数过程的调用组成。</span><span class="sxs-lookup"><span data-stu-id="524a2-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
- <span data-ttu-id="524a2-127">在 lambda 表达式中，所有参数都必须具有指定的数据类型，或者必须推断所有参数。</span><span class="sxs-lookup"><span data-stu-id="524a2-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
- <span data-ttu-id="524a2-128">`ParamArray`Lambda 表达式中不允许使用可选的和参数。</span><span class="sxs-lookup"><span data-stu-id="524a2-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
- <span data-ttu-id="524a2-129">Lambda 表达式中不允许使用泛型参数。</span><span class="sxs-lookup"><span data-stu-id="524a2-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="524a2-130">示例</span><span class="sxs-lookup"><span data-stu-id="524a2-130">Example</span></span>  

 <span data-ttu-id="524a2-131">下面是将值写入控制台的 lambda 表达式的示例。</span><span class="sxs-lookup"><span data-stu-id="524a2-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="524a2-132">该示例显示了子程序的单行和多行 lambda 表达式语法。</span><span class="sxs-lookup"><span data-stu-id="524a2-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="524a2-133">有关更多示例，请参阅 [Lambda 表达式](../../programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="524a2-133">For more examples, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="524a2-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="524a2-134">See also</span></span>

- [<span data-ttu-id="524a2-135">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="524a2-135">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="524a2-136">Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="524a2-136">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="524a2-137">运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="524a2-137">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="524a2-138">语句</span><span class="sxs-lookup"><span data-stu-id="524a2-138">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="524a2-139">宽松委托转换</span><span class="sxs-lookup"><span data-stu-id="524a2-139">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
