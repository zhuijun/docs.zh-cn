---
title: 如何执行表达式树 (C#)
description: 了解如何执行表达式树以返回值或执行类似于调用方法的操作。
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: 19c3e639d64a44d180c75964261569dc0d6c2d89
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91154010"
---
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="2678c-103">如何执行表达式树 (C#)</span><span class="sxs-lookup"><span data-stu-id="2678c-103">How to execute expression trees (C#)</span></span>

<span data-ttu-id="2678c-104">本主题演示如何执行表达式树。</span><span class="sxs-lookup"><span data-stu-id="2678c-104">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="2678c-105">执行表达式树可能返回一个值，或者它可能只是执行操作，例如调用方法。</span><span class="sxs-lookup"><span data-stu-id="2678c-105">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="2678c-106">仅可以执行表示 lambda 表达式的表达式树。</span><span class="sxs-lookup"><span data-stu-id="2678c-106">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="2678c-107">表示 Lambda 表达式的表达式树的类型为 <xref:System.Linq.Expressions.LambdaExpression> 或 <xref:System.Linq.Expressions.Expression%601>。</span><span class="sxs-lookup"><span data-stu-id="2678c-107">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="2678c-108">若要执行这些表达式树，请调用 <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> 方法来创建一个可执行的委托，然后调用该委托。</span><span class="sxs-lookup"><span data-stu-id="2678c-108">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2678c-109">如果委托的类型未知，也就是说 Lambda 表达式的类型为 <xref:System.Linq.Expressions.LambdaExpression>，而不是 <xref:System.Linq.Expressions.Expression%601>，则必须对委托调用 <xref:System.Delegate.DynamicInvoke%2A> 方法，而不是直接调用委托。</span><span class="sxs-lookup"><span data-stu-id="2678c-109">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="2678c-110">如果表达式树不表示 Lambda 表达式，可以通过调用 <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> 方法创建一个新的 Lambda 表达式，此表达式的主体为原始表达式树。</span><span class="sxs-lookup"><span data-stu-id="2678c-110">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="2678c-111">然后，按本节前面所述执行此 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="2678c-111">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2678c-112">示例</span><span class="sxs-lookup"><span data-stu-id="2678c-112">Example</span></span>  

 <span data-ttu-id="2678c-113">下面的代码示例演示如何通过创建 lambda 表达式并执行它来执行代表幂运算的表达式树。</span><span class="sxs-lookup"><span data-stu-id="2678c-113">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="2678c-114">示例最后显示幂运算的结果。</span><span class="sxs-lookup"><span data-stu-id="2678c-114">The result, which represents the number raised to the power, is displayed.</span></span>  
  
```csharp  
// The expression tree to execute.  
BinaryExpression be = Expression.Power(Expression.Constant(2D), Expression.Constant(3D));  
  
// Create a lambda expression.  
Expression<Func<double>> le = Expression.Lambda<Func<double>>(be);  
  
// Compile the lambda expression.  
Func<double> compiledExpression = le.Compile();  
  
// Execute the lambda expression.  
double result = compiledExpression();  
  
// Display the result.  
Console.WriteLine(result);  
  
// This code produces the following output:  
// 8  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2678c-115">编译代码</span><span class="sxs-lookup"><span data-stu-id="2678c-115">Compiling the Code</span></span>  
  
- <span data-ttu-id="2678c-116">包括 System.Linq.Expressions 命名空间。</span><span class="sxs-lookup"><span data-stu-id="2678c-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2678c-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="2678c-117">See also</span></span>

- [<span data-ttu-id="2678c-118">表达式树 (C#)</span><span class="sxs-lookup"><span data-stu-id="2678c-118">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="2678c-119">如何修改表达式树 (C#)</span><span class="sxs-lookup"><span data-stu-id="2678c-119">How to modify expression trees (C#)</span></span>](./how-to-modify-expression-trees.md)
