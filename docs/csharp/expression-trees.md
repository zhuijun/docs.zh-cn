---
title: 表达式树
description: 介绍 .NET Core 中的表达式树，以及如何用它们将代码表示为可以检查、修改和执行的结构。
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: 62f5b93097ee8ad2177fc0bb484c656408f91f30
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062504"
---
# <a name="expression-trees"></a><span data-ttu-id="28123-103">表达式树</span><span class="sxs-lookup"><span data-stu-id="28123-103">Expression Trees</span></span>

<span data-ttu-id="28123-104">如果你使用过 LINQ，则会有丰富库（其中 `Func` 类型是 API 集的一部分）的经验。</span><span class="sxs-lookup"><span data-stu-id="28123-104">If you have used LINQ, you have experience with a rich library where the `Func` types are part of the API set.</span></span> <span data-ttu-id="28123-105">（如果尚不熟悉 LINQ，建议阅读 [LINQ 教程](linq/index.md)，以及本文前面有关 [lambda 表达式](language-reference/operators/lambda-expressions.md)的文章。）表达式树  提供与作为函数的参数的更丰富的交互。</span><span class="sxs-lookup"><span data-stu-id="28123-105">(If you are not familiar with LINQ, you probably want to read [the LINQ tutorial](linq/index.md) and the article about [lambda expressions](language-reference/operators/lambda-expressions.md) before this one.) *Expression Trees* provide richer interaction with the arguments that are functions.</span></span>

<span data-ttu-id="28123-106">在创建 LINQ 查询时，通常使用 Lambda 表达式编写函数参数。</span><span class="sxs-lookup"><span data-stu-id="28123-106">You write function arguments, typically using Lambda Expressions, when you create LINQ queries.</span></span> <span data-ttu-id="28123-107">在典型的 LINQ 查询中，这些函数参数会被转换为编译器创建的委托。</span><span class="sxs-lookup"><span data-stu-id="28123-107">In a typical LINQ query, those function arguments are transformed into a delegate the compiler creates.</span></span>

<span data-ttu-id="28123-108">当想要进行更丰富的交互时，需要使用*表达式树*。</span><span class="sxs-lookup"><span data-stu-id="28123-108">When you want to have a richer interaction, you need to use *Expression Trees*.</span></span>
<span data-ttu-id="28123-109">表达式树将代码表示为可以检查、修改或执行的结构。</span><span class="sxs-lookup"><span data-stu-id="28123-109">Expression Trees represent code as a structure that you can examine, modify, or execute.</span></span> <span data-ttu-id="28123-110">这些工具让你能够在运行时操作代码。</span><span class="sxs-lookup"><span data-stu-id="28123-110">These tools give you the power to manipulate code during run time.</span></span> <span data-ttu-id="28123-111">可以编写检查正在运行的算法的代码，或插入新的功能。</span><span class="sxs-lookup"><span data-stu-id="28123-111">You can write code that examines running algorithms, or injects new capabilities.</span></span> <span data-ttu-id="28123-112">在更加高级的方案中，你可以修改正在运行的算法，甚至可以将 C# 表达式转换为另一种形式从而可在另一环境中执行。</span><span class="sxs-lookup"><span data-stu-id="28123-112">In more advanced scenarios, you can modify running algorithms, and even translate C# expressions into another form for execution in another environment.</span></span>

<span data-ttu-id="28123-113">你可能已经编写过使用表达式树的代码。</span><span class="sxs-lookup"><span data-stu-id="28123-113">You've likely already written code that uses Expression Trees.</span></span> <span data-ttu-id="28123-114">实体框架的 LINQ API 接受表达式树，以此作为 LINQ 查询表达式模式的参数。</span><span class="sxs-lookup"><span data-stu-id="28123-114">Entity Framework's LINQ APIs accept Expression Trees as the arguments for the LINQ Query Expression Pattern.</span></span>
<span data-ttu-id="28123-115">这使得 [Entity Framework](/ef/)（实体框架）能够将使用 C# 编写的查询转换为在数据库引擎中执行的 SQL。</span><span class="sxs-lookup"><span data-stu-id="28123-115">That enables [Entity Framework](/ef/) to translate the query you wrote in C# into SQL that executes in the database engine.</span></span> <span data-ttu-id="28123-116">另一个示例是 [Moq](https://github.com/Moq/moq)，它是用于 .NET 的热门模拟框架。</span><span class="sxs-lookup"><span data-stu-id="28123-116">Another example is [Moq](https://github.com/Moq/moq), which is a popular mocking framework for .NET.</span></span>

<span data-ttu-id="28123-117">本教程的其余部分将探索表达式树是什么、检查支持表达式树的框架类，并介绍如何使用表达式树。</span><span class="sxs-lookup"><span data-stu-id="28123-117">The remaining sections of this tutorial will explore what Expression Trees are, examine the framework classes that support expression trees, and show you how to work with expression trees.</span></span> <span data-ttu-id="28123-118">你将学习如何阅读表达式树、如何创建表达式树、如何创建修改的表达式树，以及如何执行表达式树所表示的代码。</span><span class="sxs-lookup"><span data-stu-id="28123-118">You'll learn how to read expression trees, how to create expression trees, how to create modified expression trees, and how to execute the code represented by expression trees.</span></span> <span data-ttu-id="28123-119">阅读后，便可以开始使用这些结构来创建丰富的自适应算法。</span><span class="sxs-lookup"><span data-stu-id="28123-119">After reading, you will be ready to use these structures to create rich adaptive algorithms.</span></span>

1. [<span data-ttu-id="28123-120">已解释的表达式树</span><span class="sxs-lookup"><span data-stu-id="28123-120">Expression Trees Explained</span></span>](expression-trees-explained.md)

    <span data-ttu-id="28123-121">了解表达式树的结构和概念  。</span><span class="sxs-lookup"><span data-stu-id="28123-121">Understand the structure and concepts behind *Expression Trees*.</span></span>

2. [<span data-ttu-id="28123-122">框架类型支持表达式树</span><span class="sxs-lookup"><span data-stu-id="28123-122">Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

    <span data-ttu-id="28123-123">了解定义和控制表达式树的结构和类。</span><span class="sxs-lookup"><span data-stu-id="28123-123">Learn about the structures and classes that define and manipulate expression trees.</span></span>

3. [<span data-ttu-id="28123-124">执行表达式</span><span class="sxs-lookup"><span data-stu-id="28123-124">Executing Expressions</span></span>](expression-trees-execution.md)

    <span data-ttu-id="28123-125">了解如何将表示为 Lambda 表达式的表达式树转换为委托，并执行结果委托。</span><span class="sxs-lookup"><span data-stu-id="28123-125">Learn how to convert an expression tree represented as a Lambda Expression into a delegate and execute the resulting delegate.</span></span>

4. [<span data-ttu-id="28123-126">解释表达式</span><span class="sxs-lookup"><span data-stu-id="28123-126">Interpreting Expressions</span></span>](expression-trees-interpreting.md)

    <span data-ttu-id="28123-127">了解如何遍历并检查表达式树  ，以理解表达式树表示的代码。</span><span class="sxs-lookup"><span data-stu-id="28123-127">Learn how to traverse and examine *expression trees* to understand what code the expression tree represents.</span></span>

5. [<span data-ttu-id="28123-128">生成表达式</span><span class="sxs-lookup"><span data-stu-id="28123-128">Building Expressions</span></span>](expression-trees-building.md)

    <span data-ttu-id="28123-129">了解如何构造表达式树的节点并生成表达式树。</span><span class="sxs-lookup"><span data-stu-id="28123-129">Learn how to construct the nodes for an expression tree and build expression trees.</span></span>

6. [<span data-ttu-id="28123-130">转换表达式</span><span class="sxs-lookup"><span data-stu-id="28123-130">Translating Expressions</span></span>](expression-trees-translating.md)

    <span data-ttu-id="28123-131">了解如何生成表达式树的修改副本，或将表达式树转换为另一种格式。</span><span class="sxs-lookup"><span data-stu-id="28123-131">Learn how to build a modified copy of an expression tree, or translate an expression tree into a different format.</span></span>

7. [<span data-ttu-id="28123-132">总结</span><span class="sxs-lookup"><span data-stu-id="28123-132">Summing up</span></span>](expression-trees-summary.md)

    <span data-ttu-id="28123-133">查看表达式树上的信息。</span><span class="sxs-lookup"><span data-stu-id="28123-133">Review the information on expression trees.</span></span>
