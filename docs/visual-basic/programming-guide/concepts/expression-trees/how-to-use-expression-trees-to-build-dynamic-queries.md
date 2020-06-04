---
title: 如何：使用表达式树生成动态查询
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: 1f686c37b5d04263ac5ae0dd6883aa8a519ed19e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410974"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="0586d-102">如何：使用表达式树生成动态查询（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="0586d-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>

<span data-ttu-id="0586d-103">在 LINQ 中，表达式树用于表示针对数据源的结构化查询，这些数据源可实现 <xref:System.Linq.IQueryable%601>。</span><span class="sxs-lookup"><span data-stu-id="0586d-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="0586d-104">例如，LINQ 提供程序可实现 <xref:System.Linq.IQueryable%601> 接口，用于查询关系数据存储。</span><span class="sxs-lookup"><span data-stu-id="0586d-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="0586d-105">Visual Basic 编译器将针对此类数据源的查询编译为在运行时生成表达式树的代码。</span><span class="sxs-lookup"><span data-stu-id="0586d-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="0586d-106">然后，查询提供程序可以遍历表达式树数据结构，并将其转换为适合于数据源的查询语言。</span><span class="sxs-lookup"><span data-stu-id="0586d-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>

<span data-ttu-id="0586d-107">表达式树还可以用在 LINQ 中，用于表示分配给类型为 <xref:System.Linq.Expressions.Expression%601> 的变量的 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="0586d-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>

<span data-ttu-id="0586d-108">本主题描述如何使用表达式树来创建动态 LINQ 查询。</span><span class="sxs-lookup"><span data-stu-id="0586d-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="0586d-109">如果在编译时不知道查询的细节，动态查询将十分有用。</span><span class="sxs-lookup"><span data-stu-id="0586d-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="0586d-110">例如，应用程序可能会提供一个用户界面，最终用户可以使用该用户界面指定一个或多个谓词来筛选数据。</span><span class="sxs-lookup"><span data-stu-id="0586d-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="0586d-111">为了使用 LINQ 进行查询，这种应用程序必须使用表达式树在运行时创建 LINQ 查询。</span><span class="sxs-lookup"><span data-stu-id="0586d-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>

## <a name="example"></a><span data-ttu-id="0586d-112">示例</span><span class="sxs-lookup"><span data-stu-id="0586d-112">Example</span></span>

<span data-ttu-id="0586d-113">下面的示例演示如何使用表达式树依据 `IQueryable` 数据源构造一个查询，然后执行该查询。</span><span class="sxs-lookup"><span data-stu-id="0586d-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="0586d-114">代码将生成一个表达式树来表示以下查询：</span><span class="sxs-lookup"><span data-stu-id="0586d-114">The code builds an expression tree to represent the following query:</span></span>

`companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`

<span data-ttu-id="0586d-115"><xref:System.Linq.Expressions> 命名空间中的工厂方法用于创建表达式树，这些表达式树表示构成总体查询的表达式。</span><span class="sxs-lookup"><span data-stu-id="0586d-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="0586d-116">表示标准查询运算符方法调用的表达式将引用这些方法的 <xref:System.Linq.Queryable> 实现。</span><span class="sxs-lookup"><span data-stu-id="0586d-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="0586d-117">最终的表达式树将传递给 `IQueryable` 数据源的提供程序的 <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> 实现，以创建 `IQueryable` 类型的可执行查询。</span><span class="sxs-lookup"><span data-stu-id="0586d-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="0586d-118">通过枚举该查询变量获得结果。</span><span class="sxs-lookup"><span data-stu-id="0586d-118">The results are obtained by enumerating that query variable.</span></span>

```vb
' Add an Imports statement for System.Linq.Expressions.

Dim companies =
    {"Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",
     "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",
     "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",
     "Blue Yonder Airlines", "Trey Research", "The Phone Company",
     "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee"}

' The IQueryable data to query.
Dim queryableData As IQueryable(Of String) = companies.AsQueryable()

' Compose the expression tree that represents the parameter to the predicate.
Dim pe As ParameterExpression = Expression.Parameter(GetType(String), "company")

' ***** Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16) *****
' Create an expression tree that represents the expression: company.ToLower() = "coho winery".
Dim left As Expression = Expression.Call(pe, GetType(String).GetMethod("ToLower", System.Type.EmptyTypes))
Dim right As Expression = Expression.Constant("coho winery")
Dim e1 As Expression = Expression.Equal(left, right)

' Create an expression tree that represents the expression: company.Length > 16.
left = Expression.Property(pe, GetType(String).GetProperty("Length"))
right = Expression.Constant(16, GetType(Integer))
Dim e2 As Expression = Expression.GreaterThan(left, right)

' Combine the expressions to create an expression tree that represents the
' expression: company.ToLower() = "coho winery" OrElse company.Length > 16).
Dim predicateBody As Expression = Expression.OrElse(e1, e2)

' Create an expression tree that represents the expression:
' queryableData.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16)
Dim whereCallExpression As MethodCallExpression = Expression.Call(
        GetType(Queryable),
        "Where",
        New Type() {queryableData.ElementType},
        queryableData.Expression,
        Expression.Lambda(Of Func(Of String, Boolean))(predicateBody, New ParameterExpression() {pe}))
' ***** End Where *****

' ***** OrderBy(Function(company) company) *****
' Create an expression tree that represents the expression:
' whereCallExpression.OrderBy(Function(company) company)
Dim orderByCallExpression As MethodCallExpression = Expression.Call(
        GetType(Queryable),
        "OrderBy",
        New Type() {queryableData.ElementType, queryableData.ElementType},
        whereCallExpression,
        Expression.Lambda(Of Func(Of String, String))(pe, New ParameterExpression() {pe}))
' ***** End OrderBy *****

' Create an executable query from the expression tree.
Dim results As IQueryable(Of String) = queryableData.Provider.CreateQuery(Of String)(orderByCallExpression)

' Enumerate the results.
For Each company As String In results
    Console.WriteLine(company)
Next

' This code produces the following output:
'
' Blue Yonder Airlines
' City Power & Light
' Coho Winery
' Consolidated Messenger
' Graphic Design Institute
' Humongous Insurance
' Lucerne Publishing
' Northwind Traders
' The Phone Company
' Wide World Importers
```

<span data-ttu-id="0586d-119">此代码在传递到 `Queryable.Where` 方法的谓词中使用固定数量的表达式。</span><span class="sxs-lookup"><span data-stu-id="0586d-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="0586d-120">但是，可以编写一个视用户输入而定来合并可变数量谓词表达式的应用程序。</span><span class="sxs-lookup"><span data-stu-id="0586d-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="0586d-121">视用户输入而定，也可以更改在查询中调用的标准查询运算符。</span><span class="sxs-lookup"><span data-stu-id="0586d-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="0586d-122">编译代码</span><span class="sxs-lookup"><span data-stu-id="0586d-122">Compile the code</span></span>

- <span data-ttu-id="0586d-123">创建新的**控制台应用程序**项目。</span><span class="sxs-lookup"><span data-stu-id="0586d-123">Create a new **Console Application** project.</span></span>

- <span data-ttu-id="0586d-124">包括 System.Linq.Expressions 命名空间。</span><span class="sxs-lookup"><span data-stu-id="0586d-124">Include the System.Linq.Expressions namespace.</span></span>

- <span data-ttu-id="0586d-125">复制该示例中的代码并将其粘贴到 `Main` `Sub` 过程中。</span><span class="sxs-lookup"><span data-stu-id="0586d-125">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="0586d-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0586d-126">See also</span></span>

- [<span data-ttu-id="0586d-127">表达式树 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0586d-127">Expression Trees (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="0586d-128">如何：执行表达式树 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0586d-128">How to: Execute Expression Trees (Visual Basic)</span></span>](how-to-execute-expression-trees.md)
