---
title: 如何：执行表达式树
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: 7b7b08ea1a7a1310b1d98876be96f1fa28ecba91
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375325"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="1c494-102">如何：执行表达式树 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c494-102">How to: Execute Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="1c494-103">本主题演示如何执行表达式树。</span><span class="sxs-lookup"><span data-stu-id="1c494-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="1c494-104">执行表达式树可能返回一个值，或者它可能只是执行操作，例如调用方法。</span><span class="sxs-lookup"><span data-stu-id="1c494-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="1c494-105">仅可以执行表示 lambda 表达式的表达式树。</span><span class="sxs-lookup"><span data-stu-id="1c494-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="1c494-106">表示 Lambda 表达式的表达式树的类型为 <xref:System.Linq.Expressions.LambdaExpression> 或 <xref:System.Linq.Expressions.Expression%601>。</span><span class="sxs-lookup"><span data-stu-id="1c494-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="1c494-107">若要执行这些表达式树，请调用 <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> 方法来创建一个可执行的委托，然后调用该委托。</span><span class="sxs-lookup"><span data-stu-id="1c494-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c494-108">如果委托的类型未知，也就是说 Lambda 表达式的类型为 <xref:System.Linq.Expressions.LambdaExpression>，而不是 <xref:System.Linq.Expressions.Expression%601>，则必须对委托调用 <xref:System.Delegate.DynamicInvoke%2A> 方法，而不是直接调用委托。</span><span class="sxs-lookup"><span data-stu-id="1c494-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="1c494-109">如果表达式树不表示 Lambda 表达式，可以通过调用 <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> 方法创建一个新的 Lambda 表达式，此表达式的主体为原始表达式树。</span><span class="sxs-lookup"><span data-stu-id="1c494-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="1c494-110">然后，按本节前面所述执行此 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="1c494-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c494-111">示例</span><span class="sxs-lookup"><span data-stu-id="1c494-111">Example</span></span>  
 <span data-ttu-id="1c494-112">下面的代码示例演示如何通过创建 lambda 表达式并执行它来执行代表幂运算的表达式树。</span><span class="sxs-lookup"><span data-stu-id="1c494-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="1c494-113">示例最后显示幂运算的结果。</span><span class="sxs-lookup"><span data-stu-id="1c494-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
```vb  
' The expression tree to execute.  
Dim be As BinaryExpression = Expression.Power(Expression.Constant(2.0R), Expression.Constant(3.0R))  
  
' Create a lambda expression.  
Dim le As Expression(Of Func(Of Double)) = Expression.Lambda(Of Func(Of Double))(be)  
  
' Compile the lambda expression.  
Dim compiledExpression As Func(Of Double) = le.Compile()  
  
' Execute the lambda expression.  
Dim result As Double = compiledExpression()  
  
' Display the result.  
MsgBox(result)  
  
' This code produces the following output:  
' 8  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="1c494-114">编译代码</span><span class="sxs-lookup"><span data-stu-id="1c494-114">Compile the code</span></span>  
  
- <span data-ttu-id="1c494-115">包括 System.Linq.Expressions 命名空间。</span><span class="sxs-lookup"><span data-stu-id="1c494-115">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c494-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c494-116">See also</span></span>

- [<span data-ttu-id="1c494-117">表达式树 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c494-117">Expression Trees (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="1c494-118">如何：修改表达式树 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c494-118">How to: Modify Expression Trees (Visual Basic)</span></span>](how-to-modify-expression-trees.md)
