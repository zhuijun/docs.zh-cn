---
title: 如何在查询中使用 Lambda 表达式 - C# 编程指南
description: 了解如何在查询中使用 Lambda 表达式。 查看代码示例和其他可用资源。
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: ef8a7e3b4cd5302d6c928ad7ad81811797777b4a
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063245"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a><span data-ttu-id="18c8e-104">如何在查询中使用 Lambda 表达式（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="18c8e-104">How to use lambda expressions in a query (C# Programming Guide)</span></span>
<span data-ttu-id="18c8e-105">不会直接在查询语法中使用 lambda 表达式，而是在方法调用中使用它们，并且查询表达式可以包含方法调用。</span><span class="sxs-lookup"><span data-stu-id="18c8e-105">You do not use lambda expressions directly in query syntax, but you do use them in method calls, and query expressions can contain method calls.</span></span> <span data-ttu-id="18c8e-106">事实上，一些查询操作只能采用方法语法进行表示。</span><span class="sxs-lookup"><span data-stu-id="18c8e-106">In fact, some query operations can only be expressed in method syntax.</span></span> <span data-ttu-id="18c8e-107">有关查询语法与方法语法之间的差异的详细信息，请参阅 [LINQ 中的查询语法和方法语法](../concepts/linq/query-syntax-and-method-syntax-in-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="18c8e-107">For more information about the difference between query syntax and method syntax, see [Query Syntax and Method Syntax in LINQ](../concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="18c8e-108">示例</span><span class="sxs-lookup"><span data-stu-id="18c8e-108">Example</span></span>  
 <span data-ttu-id="18c8e-109">下面的示例演示如何通过 <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> 标准查询运算符，在基于方法的查询中使用 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="18c8e-109">The following example demonstrates how to use a lambda expression in a method-based query by using the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> standard query operator.</span></span> <span data-ttu-id="18c8e-110">请注意，此示例中的 <xref:System.Linq.Enumerable.Where%2A> 方法具有一个 <xref:System.Func%602> 委托类型的输入参数，该委托采用整数作为输入并返回一个布尔值。</span><span class="sxs-lookup"><span data-stu-id="18c8e-110">Note that the <xref:System.Linq.Enumerable.Where%2A> method in this example has an input parameter of the delegate type <xref:System.Func%602> and that delegate takes an integer as input and returns a Boolean.</span></span> <span data-ttu-id="18c8e-111">Lambda 表达式可以转换为该委托。</span><span class="sxs-lookup"><span data-stu-id="18c8e-111">The lambda expression can be converted to that delegate.</span></span> <span data-ttu-id="18c8e-112">如果这是使用 <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> 方法的 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 查询，则参数类型会是 `Expression<Func<int,bool>>`，但 lambda 表达式看起来完全相同。</span><span class="sxs-lookup"><span data-stu-id="18c8e-112">If this were a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query that used the <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> method, the parameter type would be an `Expression<Func<int,bool>>` but the lambda expression would look exactly the same.</span></span> <span data-ttu-id="18c8e-113">有关表达式类型的详细信息，请参阅 <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="18c8e-113">For more information on the Expression type, see <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#1)]  
  
## <a name="example"></a><span data-ttu-id="18c8e-114">示例</span><span class="sxs-lookup"><span data-stu-id="18c8e-114">Example</span></span>  
 <span data-ttu-id="18c8e-115">下面的示例演示如何在查询表达式的方法调用中使用 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="18c8e-115">The following example demonstrates how to use a lambda expression in a method call of a query expression.</span></span> <span data-ttu-id="18c8e-116">需要 lambda 的原因是无法使用查询语法调用 <xref:System.Linq.Enumerable.Sum%2A> 标准查询运算符。</span><span class="sxs-lookup"><span data-stu-id="18c8e-116">The lambda is necessary because the <xref:System.Linq.Enumerable.Sum%2A> standard query operator cannot be invoked by using query syntax.</span></span>  
  
 <span data-ttu-id="18c8e-117">查询首先根据学生的年级（在 `GradeLevel` 枚举中定义）对学生进行分组。</span><span class="sxs-lookup"><span data-stu-id="18c8e-117">The query first groups the students according to their grade level, as defined in the `GradeLevel` enum.</span></span> <span data-ttu-id="18c8e-118">然后为每个组添加每个学生的总分。</span><span class="sxs-lookup"><span data-stu-id="18c8e-118">Then for each group it adds the total scores for each student.</span></span> <span data-ttu-id="18c8e-119">这需要两个 `Sum` 操作。</span><span class="sxs-lookup"><span data-stu-id="18c8e-119">This requires two `Sum` operations.</span></span> <span data-ttu-id="18c8e-120">内部 `Sum` 为每个学生计算总分，而外部 `Sum` 保留组中所有学生的正在运行的合并总分。</span><span class="sxs-lookup"><span data-stu-id="18c8e-120">The inner `Sum` calculates the total score for each student, and the outer `Sum` keeps a running, combined total for all students in the group.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="18c8e-121">编译代码</span><span class="sxs-lookup"><span data-stu-id="18c8e-121">Compiling the Code</span></span>  
 <span data-ttu-id="18c8e-122">若要运行此代码，请将方法复制并粘贴到[查询对象的集合](../../linq/query-a-collection-of-objects.md)中提供的 `StudentClass` 中，然后从 `Main` 方法调用它。</span><span class="sxs-lookup"><span data-stu-id="18c8e-122">To run this code, copy and paste the method into the `StudentClass` that is provided in [Query a collection of objects](../../linq/query-a-collection-of-objects.md) and call it from the `Main` method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="18c8e-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="18c8e-123">See also</span></span>

- [<span data-ttu-id="18c8e-124">Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="18c8e-124">Lambda Expressions</span></span>](../../language-reference/operators/lambda-expressions.md)
- [<span data-ttu-id="18c8e-125">表达式树 (C#)</span><span class="sxs-lookup"><span data-stu-id="18c8e-125">Expression Trees (C#)</span></span>](../concepts/expression-trees/index.md)
