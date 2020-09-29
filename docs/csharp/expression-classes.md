---
title: 支持表达式树的框架类型
description: 了解支持表达式树的框架类型、创建表达式树和使用表达式树 API 的方法。
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 548f5ba6a2de00d9556621791515555b6f6a325c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180434"
---
# <a name="framework-types-supporting-expression-trees"></a><span data-ttu-id="ed848-103">支持表达式树的框架类型</span><span class="sxs-lookup"><span data-stu-id="ed848-103">Framework Types Supporting Expression Trees</span></span>

[<span data-ttu-id="ed848-104">上一步 - 已解释的表达式树</span><span class="sxs-lookup"><span data-stu-id="ed848-104">Previous -- Expression Trees Explained</span></span>](expression-trees-explained.md)

<span data-ttu-id="ed848-105">存在可与表达式树配合使用的 .NET Core framework 中的类的大型列表。</span><span class="sxs-lookup"><span data-stu-id="ed848-105">There is a large list of classes in the .NET Core framework that work with Expression Trees.</span></span>
<span data-ttu-id="ed848-106">可以在 <xref:System.Linq.Expressions> 查看完整列表。</span><span class="sxs-lookup"><span data-stu-id="ed848-106">You can see the full list at <xref:System.Linq.Expressions>.</span></span>
<span data-ttu-id="ed848-107">让我们来了解一下 framework 类的设计方式，而不是逐一查看完整列表。</span><span class="sxs-lookup"><span data-stu-id="ed848-107">Rather than run through the full list, let's understand how the framework classes have been designed.</span></span>

<span data-ttu-id="ed848-108">在语言设计中，表达式是可计算并返回值的代码主体。</span><span class="sxs-lookup"><span data-stu-id="ed848-108">In language design, an expression is a body of code that evaluates and returns a value.</span></span> <span data-ttu-id="ed848-109">表达式可能非常简单：常数表达式 `1` 返回常数值 1。</span><span class="sxs-lookup"><span data-stu-id="ed848-109">Expressions may be very simple: the constant expression `1` returns the constant value of 1.</span></span> <span data-ttu-id="ed848-110">也可能较复杂：表达式 `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` 返回二次方程的一个根（若方程有解）。</span><span class="sxs-lookup"><span data-stu-id="ed848-110">They may be more complicated: The expression `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` returns one root for a quadratic equation (in the case where the equation has a solution).</span></span>  

## <a name="it-all-starts-with-systemlinqexpression"></a><span data-ttu-id="ed848-111">这一切都始于 System.Linq.Expression</span><span class="sxs-lookup"><span data-stu-id="ed848-111">It all starts with System.Linq.Expression</span></span>

<span data-ttu-id="ed848-112">使用表达式树的其中一个难点在于许多不同类型的表达式在程序中的许多位置均有效。</span><span class="sxs-lookup"><span data-stu-id="ed848-112">One of the complexities of working with expression trees is that many different kinds of expressions are valid in many places in programs.</span></span> <span data-ttu-id="ed848-113">请思考一个赋值表达式。</span><span class="sxs-lookup"><span data-stu-id="ed848-113">Consider an assignment expression.</span></span> <span data-ttu-id="ed848-114">赋值的右侧可以是常数值、变量、方法调用表达式或其他内容。</span><span class="sxs-lookup"><span data-stu-id="ed848-114">The right hand side of an assignment could be a constant value, a variable, a method call expression, or others.</span></span> <span data-ttu-id="ed848-115">语言灵活性意味着，遍历表达式树时，可能会在树的节点中的任意位置遇到许多不同的表达式类型。</span><span class="sxs-lookup"><span data-stu-id="ed848-115">That language flexibility means that you may encounter many different expression types anywhere in the nodes of a tree when you traverse an expression tree.</span></span> <span data-ttu-id="ed848-116">因此，使用基表达式类型时，理解起来最简单。</span><span class="sxs-lookup"><span data-stu-id="ed848-116">Therefore, when you can work with the base expression type, that's the simplest way to work.</span></span> <span data-ttu-id="ed848-117">但是，有时你需要了解更多内容。</span><span class="sxs-lookup"><span data-stu-id="ed848-117">However, sometimes you need to know more.</span></span>
<span data-ttu-id="ed848-118">为此，基表达式类包含 `NodeType` 属性。</span><span class="sxs-lookup"><span data-stu-id="ed848-118">The base Expression class contains a `NodeType` property for this purpose.</span></span>
<span data-ttu-id="ed848-119">它将返回 `ExpressionType`，这是可能的表达式类型的枚举。</span><span class="sxs-lookup"><span data-stu-id="ed848-119">It returns an `ExpressionType` which is an enumeration of possible expression types.</span></span>
<span data-ttu-id="ed848-120">知道节点的类型后，可以将其转换为该类型，并执行特定操作（如果知道表达式节点的类型）。</span><span class="sxs-lookup"><span data-stu-id="ed848-120">Once you know the type of the node, you can cast it to that type, and perform specific actions knowing the type of the expression node.</span></span> <span data-ttu-id="ed848-121">可以搜索特定的节点类型，然后使用这种表达式的特定属性。</span><span class="sxs-lookup"><span data-stu-id="ed848-121">You can search for certain node types, and then work with the specific properties of that kind of expression.</span></span>

<span data-ttu-id="ed848-122">例如，此代码将打印变量访问表达式的变量的名称。</span><span class="sxs-lookup"><span data-stu-id="ed848-122">For example, this code will print the name of a variable for a variable access expression.</span></span> <span data-ttu-id="ed848-123">我的做法是，先查看节点类型，再转换为变量访问表达式，然后查看特定表达式类型的属性：</span><span class="sxs-lookup"><span data-stu-id="ed848-123">I've followed the practice of checking the node type, then casting to a variable access expression and then checking the properties of the specific expression type:</span></span>

```csharp
Expression<Func<int, int>> addFive = (num) => num + 5;

if (addFive.NodeType == ExpressionType.Lambda)
{
    var lambdaExp = (LambdaExpression)addFive;

    var parameter = lambdaExp.Parameters.First();

    Console.WriteLine(parameter.Name);
    Console.WriteLine(parameter.Type);
}
```

## <a name="creating-expression-trees"></a><span data-ttu-id="ed848-124">创建表达式树</span><span class="sxs-lookup"><span data-stu-id="ed848-124">Creating Expression Trees</span></span>

<span data-ttu-id="ed848-125">`System.Linq.Expression` 类还包含许多创建表达式的静态方法。</span><span class="sxs-lookup"><span data-stu-id="ed848-125">The `System.Linq.Expression` class also contains many static methods to create expressions.</span></span> <span data-ttu-id="ed848-126">这些方法使用为子节点提供的参数创建表达式节点。</span><span class="sxs-lookup"><span data-stu-id="ed848-126">These methods create an expression node using the arguments supplied for its children.</span></span> <span data-ttu-id="ed848-127">通过这种方式，可以从其叶节点构建一个表达式。</span><span class="sxs-lookup"><span data-stu-id="ed848-127">In this way, you build an expression up from its leaf nodes.</span></span> <span data-ttu-id="ed848-128">例如，此代码将生成一个 Add 表达式：</span><span class="sxs-lookup"><span data-stu-id="ed848-128">For example, this code builds an Add expression:</span></span>

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

<span data-ttu-id="ed848-129">从这个简单的示例中，你会发现创建和使用表达式树涉及了许多类型。</span><span class="sxs-lookup"><span data-stu-id="ed848-129">You can see from this simple example that many types are involved in creating and working with expression trees.</span></span> <span data-ttu-id="ed848-130">该复杂性是提供由 C# 语言提供的丰富词汇的功能所必需的。</span><span class="sxs-lookup"><span data-stu-id="ed848-130">That complexity is necessary to provide the capabilities of the rich vocabulary provided by the C# language.</span></span>

## <a name="navigating-the-apis"></a><span data-ttu-id="ed848-131">导航 API</span><span class="sxs-lookup"><span data-stu-id="ed848-131">Navigating the APIs</span></span>

<span data-ttu-id="ed848-132">存在映射到 C# 语言的几乎所有语法元素的表达式节点类型。</span><span class="sxs-lookup"><span data-stu-id="ed848-132">There are Expression node types that map to almost all of the syntax elements of the C# language.</span></span> <span data-ttu-id="ed848-133">每种类型都有针对该种语言元素的特定方法。</span><span class="sxs-lookup"><span data-stu-id="ed848-133">Each type has specific methods for that type of language element.</span></span> <span data-ttu-id="ed848-134">需要一次性记住的内容很多。</span><span class="sxs-lookup"><span data-stu-id="ed848-134">It's a lot to keep in your head at one time.</span></span> <span data-ttu-id="ed848-135">我不会记住所有内容，而是会采用有关使用表达式树的技巧，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ed848-135">Rather than try to memorize everything, here are the techniques I use to work with Expression trees:</span></span>

1. <span data-ttu-id="ed848-136">查看 `ExpressionType` 枚举的成员以确定应检查的可能节点。</span><span class="sxs-lookup"><span data-stu-id="ed848-136">Look at the members of the `ExpressionType` enum to determine possible nodes you should be examining.</span></span> <span data-ttu-id="ed848-137">如果想要遍历和理解表达式树，这将非常有用。</span><span class="sxs-lookup"><span data-stu-id="ed848-137">This really helps when you want to traverse and understand an expression tree.</span></span>
2. <span data-ttu-id="ed848-138">查看 `Expression` 类的静态成员以生成表达式。</span><span class="sxs-lookup"><span data-stu-id="ed848-138">Look at the static members of the `Expression` class to build an expression.</span></span> <span data-ttu-id="ed848-139">这些方法可以从其子节点集生成任何表达式类型。</span><span class="sxs-lookup"><span data-stu-id="ed848-139">Those methods can build any expression type from a set of its child nodes.</span></span>
3. <span data-ttu-id="ed848-140">查看 `ExpressionVisitor` 类，以生成一个经过修改的表达式树。</span><span class="sxs-lookup"><span data-stu-id="ed848-140">Look at the `ExpressionVisitor` class to build a modified expression tree.</span></span>

<span data-ttu-id="ed848-141">如果查看这三个部分的每个部分，可以发现更多内容。</span><span class="sxs-lookup"><span data-stu-id="ed848-141">You'll find more as you look at each of those three areas.</span></span> <span data-ttu-id="ed848-142">通过使用这三个步骤中的任意一个步骤，你一定会发现所需的内容。</span><span class="sxs-lookup"><span data-stu-id="ed848-142">Invariably, you will find what you need when you start with one of those three steps.</span></span>

 [<span data-ttu-id="ed848-143">下一步 - 执行表达式树</span><span class="sxs-lookup"><span data-stu-id="ed848-143">Next -- Executing Expression Trees</span></span>](expression-trees-execution.md)
