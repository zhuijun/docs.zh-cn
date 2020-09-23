---
title: 如何：通过 LINQ 使用联接合并数据
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: ebda8d3b7fa2e712c337ed2c1fadc580bed7fe61
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075065"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="4388a-102">如何：通过 LINQ 使用联接合并数据 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4388a-102">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>

<span data-ttu-id="4388a-103">Visual Basic 提供了 `Join` 和 `Group Join` 查询子句，使你能够基于集合之间的公共值组合多个集合的内容。</span><span class="sxs-lookup"><span data-stu-id="4388a-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="4388a-104">这些值称为 *键值* 。</span><span class="sxs-lookup"><span data-stu-id="4388a-104">These values are known as *key* values.</span></span> <span data-ttu-id="4388a-105">熟悉关系数据库概念的开发人员将该 `Join` 子句识别为内部联接，将 `Group Join` 子句视为有效的左外部联接。</span><span class="sxs-lookup"><span data-stu-id="4388a-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="4388a-106">本主题中的示例演示了使用 `Join` 和查询子句合并数据的几种方法 `Group Join` 。</span><span class="sxs-lookup"><span data-stu-id="4388a-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="4388a-107">创建项目并添加示例数据</span><span class="sxs-lookup"><span data-stu-id="4388a-107">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="4388a-108">创建包含示例数据和类型的项目</span><span class="sxs-lookup"><span data-stu-id="4388a-108">To create a project that contains sample data and types</span></span>  
  
1. <span data-ttu-id="4388a-109">若要运行本主题中的示例，请打开 Visual Studio 并添加新的 Visual Basic 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="4388a-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="4388a-110">双击 Visual Basic 创建的 Module1 文件。</span><span class="sxs-lookup"><span data-stu-id="4388a-110">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2. <span data-ttu-id="4388a-111">本主题中的示例使用 `Person` 和 `Pet` 类型以及以下代码示例中的数据。</span><span class="sxs-lookup"><span data-stu-id="4388a-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="4388a-112">将此代码复制到 `Module1` Visual Basic 创建的默认模块。</span><span class="sxs-lookup"><span data-stu-id="4388a-112">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#2)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="4388a-113">使用 Join 子句执行内部联接</span><span class="sxs-lookup"><span data-stu-id="4388a-113">Perform an Inner Join by Using the Join Clause</span></span>  

 <span data-ttu-id="4388a-114">内部联接结合了两个集合中的数据。</span><span class="sxs-lookup"><span data-stu-id="4388a-114">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="4388a-115">包含指定键值匹配的项。</span><span class="sxs-lookup"><span data-stu-id="4388a-115">Items for which the specified key values match are included.</span></span> <span data-ttu-id="4388a-116">不会排除在其他集合中没有匹配项的任何集合中的任何项。</span><span class="sxs-lookup"><span data-stu-id="4388a-116">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="4388a-117">在 Visual Basic 中，LINQ 提供了两个用于执行内部联接的选项：隐式联接和显式联接。</span><span class="sxs-lookup"><span data-stu-id="4388a-117">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="4388a-118">隐式联接指定要在子句中联接的集合 `From` ，并在子句中标识匹配的键字段 `Where` 。</span><span class="sxs-lookup"><span data-stu-id="4388a-118">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="4388a-119">Visual Basic 基于指定的键字段隐式联接两个集合。</span><span class="sxs-lookup"><span data-stu-id="4388a-119">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="4388a-120">`Join`当您想要了解要在联接中使用哪些键字段时，可以通过使用子句来指定显式联接。</span><span class="sxs-lookup"><span data-stu-id="4388a-120">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="4388a-121">在这种情况下， `Where` 仍可以使用子句来筛选查询结果。</span><span class="sxs-lookup"><span data-stu-id="4388a-121">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="4388a-122">使用 Join 子句执行内部联接</span><span class="sxs-lookup"><span data-stu-id="4388a-122">To perform an Inner Join by using the Join clause</span></span>  
  
1. <span data-ttu-id="4388a-123">将以下代码添加到 `Module1` 项目中的模块，以查看隐式和显式内部联接的示例。</span><span class="sxs-lookup"><span data-stu-id="4388a-123">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#4)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="4388a-124">使用 Group Join 子句执行左外部联接</span><span class="sxs-lookup"><span data-stu-id="4388a-124">Perform a Left Outer Join by Using the Group Join Clause</span></span>  

 <span data-ttu-id="4388a-125">左外部联接包含联接的左侧集合中的所有项，并仅包含联接的右侧集合中的匹配值。</span><span class="sxs-lookup"><span data-stu-id="4388a-125">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="4388a-126">不会从查询结果中排除联接的右侧集合中没有匹配项的联接的任何项。</span><span class="sxs-lookup"><span data-stu-id="4388a-126">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="4388a-127">`Group Join`子句实际上是左外部联接。</span><span class="sxs-lookup"><span data-stu-id="4388a-127">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="4388a-128">通常称为左外部联接和子句返回的内容之间的区别在于， `Group Join` `Group Join` 子句会对左侧集合中每个项的联接的右端集合中的结果进行分组。</span><span class="sxs-lookup"><span data-stu-id="4388a-128">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="4388a-129">在关系数据库中，左外部联接返回未分组的结果，其中，查询结果中的每一项都包含联接中两个集合中的匹配项。</span><span class="sxs-lookup"><span data-stu-id="4388a-129">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="4388a-130">在这种情况下，将为右侧集合中的每个匹配项重复联接左侧集合中的项。</span><span class="sxs-lookup"><span data-stu-id="4388a-130">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="4388a-131">完成下一个过程后，你将看到如下所示的内容。</span><span class="sxs-lookup"><span data-stu-id="4388a-131">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="4388a-132">您可以 `Group Join` 通过扩展查询以返回每个分组查询结果的项来检索查询结果作为未分组的结果。</span><span class="sxs-lookup"><span data-stu-id="4388a-132">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="4388a-133">若要实现此目的，必须确保对 `DefaultIfEmpty` 分组集合的方法进行查询。</span><span class="sxs-lookup"><span data-stu-id="4388a-133">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="4388a-134">这可确保联接的左侧集合中的项仍包含在查询结果中，即使它们在右侧集合中没有匹配的结果。</span><span class="sxs-lookup"><span data-stu-id="4388a-134">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="4388a-135">您可以向查询中添加代码，以便在联接的右侧集合中没有匹配的值时提供默认结果值。</span><span class="sxs-lookup"><span data-stu-id="4388a-135">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="4388a-136">使用 Group Join 子句执行左外部联接</span><span class="sxs-lookup"><span data-stu-id="4388a-136">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1. <span data-ttu-id="4388a-137">将以下代码添加到 `Module1` 项目中的模块，以查看分组左外部联接和未分组左外部联接的示例。</span><span class="sxs-lookup"><span data-stu-id="4388a-137">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#3)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="4388a-138">使用组合键执行联接</span><span class="sxs-lookup"><span data-stu-id="4388a-138">Perform a Join by Using a Composite Key</span></span>  

 <span data-ttu-id="4388a-139">可以 `And` 在或子句中使用关键字 `Join` `Group Join` 来标识从要联接的集合中匹配值时要使用的多个键字段。</span><span class="sxs-lookup"><span data-stu-id="4388a-139">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="4388a-140">`And`关键字为要联接的项指定所有指定的键字段必须匹配。</span><span class="sxs-lookup"><span data-stu-id="4388a-140">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="4388a-141">使用组合键执行联接</span><span class="sxs-lookup"><span data-stu-id="4388a-141">To perform a Join by using a composite key</span></span>  
  
1. <span data-ttu-id="4388a-142">将以下代码添加到 `Module1` 项目中的模块，以查看使用组合键的联接的示例。</span><span class="sxs-lookup"><span data-stu-id="4388a-142">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#5)]  
  
## <a name="run-the-code"></a><span data-ttu-id="4388a-143">运行代码</span><span class="sxs-lookup"><span data-stu-id="4388a-143">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="4388a-144">添加用于运行示例的代码</span><span class="sxs-lookup"><span data-stu-id="4388a-144">To add code to run the examples</span></span>  
  
1. <span data-ttu-id="4388a-145">将项目中的模块中的替换为 `Sub Main` `Module1` 以下代码，以运行本主题中的示例。</span><span class="sxs-lookup"><span data-stu-id="4388a-145">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQHowTos/VB/Module1.vb#6)]  
  
2. <span data-ttu-id="4388a-146">按 F5 运行示例。</span><span class="sxs-lookup"><span data-stu-id="4388a-146">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4388a-147">请参阅</span><span class="sxs-lookup"><span data-stu-id="4388a-147">See also</span></span>

- [<span data-ttu-id="4388a-148">LINQ</span><span class="sxs-lookup"><span data-stu-id="4388a-148">LINQ</span></span>](index.md)
- [<span data-ttu-id="4388a-149">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="4388a-149">Introduction to LINQ in Visual Basic</span></span>](introduction-to-linq.md)
- [<span data-ttu-id="4388a-150">Join 子句</span><span class="sxs-lookup"><span data-stu-id="4388a-150">Join Clause</span></span>](../../../language-reference/queries/join-clause.md)
- [<span data-ttu-id="4388a-151">Group Join 子句</span><span class="sxs-lookup"><span data-stu-id="4388a-151">Group Join Clause</span></span>](../../../language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="4388a-152">From 子句</span><span class="sxs-lookup"><span data-stu-id="4388a-152">From Clause</span></span>](../../../language-reference/queries/from-clause.md)
- [<span data-ttu-id="4388a-153">Where 子句</span><span class="sxs-lookup"><span data-stu-id="4388a-153">Where Clause</span></span>](../../../language-reference/queries/where-clause.md)
- [<span data-ttu-id="4388a-154">查询</span><span class="sxs-lookup"><span data-stu-id="4388a-154">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="4388a-155">使用 LINQ 进行数据转换 (C#)</span><span class="sxs-lookup"><span data-stu-id="4388a-155">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
