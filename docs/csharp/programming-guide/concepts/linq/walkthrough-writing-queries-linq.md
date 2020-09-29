---
title: 演练：用 C# 编写查询 (LINQ)
description: 本演练演示如何在 LINQ 查询表达式中使用 C# 语言功能。 本文使用 Visual Studio 作为开发环境。
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: bdf91f6f52a68309cfcd276b222083c8cb67a0cc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176235"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="bb77d-104">演练：用 C# 编写查询 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="bb77d-104">Walkthrough: Writing Queries in C# (LINQ)</span></span>

<span data-ttu-id="bb77d-105">此演练演示用于编写 LINQ 查询表达式的 C# 语言功能。</span><span class="sxs-lookup"><span data-stu-id="bb77d-105">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="bb77d-106">创建 C# 项目</span><span class="sxs-lookup"><span data-stu-id="bb77d-106">Create a C# Project</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb77d-107">以下说明适用于 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="bb77d-107">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="bb77d-108">如果使用其他开发环境，请创建包含对 System.Core.dll 的引用的控制台项目和用于 <xref:System.Linq?displayProperty=nameWithType> 命名空间的 `using` 指令。</span><span class="sxs-lookup"><span data-stu-id="bb77d-108">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="bb77d-109">在 Visual Studio 中创建项目</span><span class="sxs-lookup"><span data-stu-id="bb77d-109">To create a project in Visual Studio</span></span>  
  
1. <span data-ttu-id="bb77d-110">启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="bb77d-110">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="bb77d-111">在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。</span><span class="sxs-lookup"><span data-stu-id="bb77d-111">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="bb77d-112">**“新建项目”** 对话框随即打开。</span><span class="sxs-lookup"><span data-stu-id="bb77d-112">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="bb77d-113">依次展开“已安装”、“模板”、“Visual C#”，然后选择“控制台应用程序”。</span><span class="sxs-lookup"><span data-stu-id="bb77d-113">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4. <span data-ttu-id="bb77d-114">在“名称”文本框中，输入不同的名称或接受默认名称，然后选择“确定”按钮。</span><span class="sxs-lookup"><span data-stu-id="bb77d-114">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="bb77d-115">新项目将出现在“解决方案资源管理器”中。</span><span class="sxs-lookup"><span data-stu-id="bb77d-115">The new project appears in **Solution Explorer**.</span></span>  
  
5. <span data-ttu-id="bb77d-116">注意，此项目包含对 System.Core.dll 的引用和用于 <xref:System.Linq?displayProperty=nameWithType> 命名空间的 `using` 指令。</span><span class="sxs-lookup"><span data-stu-id="bb77d-116">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="bb77d-117">创建内存中的数据源</span><span class="sxs-lookup"><span data-stu-id="bb77d-117">Create an in-Memory Data Source</span></span>  

 <span data-ttu-id="bb77d-118">用于查询的数据源是 `Student` 对象的简单列表。</span><span class="sxs-lookup"><span data-stu-id="bb77d-118">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="bb77d-119">每个 `Student` 记录都有名字、姓氏和整数数组（表示该学生在课堂上的测试分数）。</span><span class="sxs-lookup"><span data-stu-id="bb77d-119">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="bb77d-120">将此代码复制到项目中。</span><span class="sxs-lookup"><span data-stu-id="bb77d-120">Copy this code into your project.</span></span> <span data-ttu-id="bb77d-121">请注意下列特性：</span><span class="sxs-lookup"><span data-stu-id="bb77d-121">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="bb77d-122">`Student` 类包含自动实现的属性。</span><span class="sxs-lookup"><span data-stu-id="bb77d-122">The `Student` class consists of auto-implemented properties.</span></span>  
  
- <span data-ttu-id="bb77d-123">列表中的每个学生都可使用对象初始值设定项进行初始化。</span><span class="sxs-lookup"><span data-stu-id="bb77d-123">Each student in the list is initialized with an object initializer.</span></span>  
  
- <span data-ttu-id="bb77d-124">列表本身可使用集合初始值设定项进行初始化。</span><span class="sxs-lookup"><span data-stu-id="bb77d-124">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="bb77d-125">将在不显式调用任何构造函数和使用显式成员访问的情况下初始化并实例化整个数据结构。</span><span class="sxs-lookup"><span data-stu-id="bb77d-125">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="bb77d-126">有关这些新功能的详细信息，请参阅[自动实现的属性](../../classes-and-structs/auto-implemented-properties.md)与[对象和集合初始值设定项](../../classes-and-structs/object-and-collection-initializers.md)。</span><span class="sxs-lookup"><span data-stu-id="bb77d-126">For more information about these new features, see [Auto-Implemented Properties](../../classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="bb77d-127">添加数据源</span><span class="sxs-lookup"><span data-stu-id="bb77d-127">To add the data source</span></span>  
  
- <span data-ttu-id="bb77d-128">向项目中的 `Program` 类添加 `Student` 类和经过初始化的学生列表。</span><span class="sxs-lookup"><span data-stu-id="bb77d-128">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="bb77d-129">向学生列表添加新学生</span><span class="sxs-lookup"><span data-stu-id="bb77d-129">To add a new Student to the Students list</span></span>  
  
1. <span data-ttu-id="bb77d-130">向 `Students` 列表添加一个新 `Student`，并按自己的选择使用名称和测试分数。</span><span class="sxs-lookup"><span data-stu-id="bb77d-130">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="bb77d-131">尝试键入所有新学生信息，以便更好地了解对象初始值设定项的语法。</span><span class="sxs-lookup"><span data-stu-id="bb77d-131">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="bb77d-132">创建查询</span><span class="sxs-lookup"><span data-stu-id="bb77d-132">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="bb77d-133">创建简单查询</span><span class="sxs-lookup"><span data-stu-id="bb77d-133">To create a simple query</span></span>  
  
- <span data-ttu-id="bb77d-134">在应用程序的 `Main` 方法中，创建简单查询，执行该查询时，将生成所有在第一次测试中分数高于 90 的学生的列表。</span><span class="sxs-lookup"><span data-stu-id="bb77d-134">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="bb77d-135">注意，由于选定全部 `Student` 对象，所以查询的类型为 `IEnumerable<Student>`。</span><span class="sxs-lookup"><span data-stu-id="bb77d-135">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="bb77d-136">尽管该代码也可以通过使用 [var](../../../language-reference/keywords/var.md) 关键字来使用隐式类型化，但可以使用显式类型化清楚地展示结果。</span><span class="sxs-lookup"><span data-stu-id="bb77d-136">Although the code could also use implicit typing by using the [var](../../../language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="bb77d-137">（有关 `var` 的详细信息，请参阅[隐式类型化局部变量](../../classes-and-structs/implicitly-typed-local-variables.md)。）</span><span class="sxs-lookup"><span data-stu-id="bb77d-137">(For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="bb77d-138">另请注意，查询的范围变量 `student` 用作指向源中每个 `Student` 引用，提供对每个对象的成员访问。</span><span class="sxs-lookup"><span data-stu-id="bb77d-138">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="bb77d-139">执行查询</span><span class="sxs-lookup"><span data-stu-id="bb77d-139">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="bb77d-140">执行查询</span><span class="sxs-lookup"><span data-stu-id="bb77d-140">To execute the query</span></span>  
  
1. <span data-ttu-id="bb77d-141">现在，编写 `foreach` 循环，用于执行查询。</span><span class="sxs-lookup"><span data-stu-id="bb77d-141">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="bb77d-142">注意以下有关代码的注意事项：</span><span class="sxs-lookup"><span data-stu-id="bb77d-142">Note the following about the code:</span></span>  
  
    - <span data-ttu-id="bb77d-143">通过 `foreach` 循环中的迭代变量，可访问返回的序列中的每个元素。</span><span class="sxs-lookup"><span data-stu-id="bb77d-143">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    - <span data-ttu-id="bb77d-144">此变量的类型是 `Student`，并且可与查询变量 `IEnumerable<Student>` 的类型兼容。</span><span class="sxs-lookup"><span data-stu-id="bb77d-144">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2. <span data-ttu-id="bb77d-145">添加此代码后，生成并运行应用程序，以在“控制台”窗口中查看结果。</span><span class="sxs-lookup"><span data-stu-id="bb77d-145">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="bb77d-146">添加其他筛选条件</span><span class="sxs-lookup"><span data-stu-id="bb77d-146">To add another filter condition</span></span>  
  
1. <span data-ttu-id="bb77d-147">在 `where` 子句中，可以组合多个布尔条件，以便进一步细化查询。</span><span class="sxs-lookup"><span data-stu-id="bb77d-147">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="bb77d-148">以下代码添加了一个条件，以便该查询返回第一个分数高于 90 分，并且最后一个分数低于 80 分的那些学生。</span><span class="sxs-lookup"><span data-stu-id="bb77d-148">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="bb77d-149">`where` 子句应与以下代码类似。</span><span class="sxs-lookup"><span data-stu-id="bb77d-149">The `where` clause should resemble the following code.</span></span>  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="bb77d-150">有关详细信息，请参阅 [where 子句](../../../language-reference/keywords/where-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="bb77d-150">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="bb77d-151">修改查询</span><span class="sxs-lookup"><span data-stu-id="bb77d-151">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="bb77d-152">对结果进行排序</span><span class="sxs-lookup"><span data-stu-id="bb77d-152">To order the results</span></span>  
  
1. <span data-ttu-id="bb77d-153">如果结果按某种顺序排列，则浏览结果会更容易。</span><span class="sxs-lookup"><span data-stu-id="bb77d-153">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="bb77d-154">你可以根据源元素中的任何可访问字段对返回的序列进行排序。</span><span class="sxs-lookup"><span data-stu-id="bb77d-154">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="bb77d-155">例如，以下 `orderby` 子句将结果按照每个学生的姓氏以字母从 A 到 Z 的顺序排列。</span><span class="sxs-lookup"><span data-stu-id="bb77d-155">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="bb77d-156">将以下 `orderby` 子句添加到查询中，紧跟 `where` 语句之后、`select` 语句之前：</span><span class="sxs-lookup"><span data-stu-id="bb77d-156">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. <span data-ttu-id="bb77d-157">现在，更改 `orderby` 子句，以便将结果根据第一次测试的分数以倒序（从最高分到最低分）的顺序排列。</span><span class="sxs-lookup"><span data-stu-id="bb77d-157">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. <span data-ttu-id="bb77d-158">更改 `WriteLine` 格式字符串，以便查看分数：</span><span class="sxs-lookup"><span data-stu-id="bb77d-158">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="bb77d-159">有关详细信息，请参阅 [orderby 子句](../../../language-reference/keywords/orderby-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="bb77d-159">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="bb77d-160">对结果进行分组</span><span class="sxs-lookup"><span data-stu-id="bb77d-160">To group the results</span></span>  
  
1. <span data-ttu-id="bb77d-161">分组是查询表达式中的强大功能。</span><span class="sxs-lookup"><span data-stu-id="bb77d-161">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="bb77d-162">包含 group 子句的查询将生成一系列组，每个组本身包含一个 `Key` 和一个序列，该序列由该组的所有成员组成。</span><span class="sxs-lookup"><span data-stu-id="bb77d-162">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="bb77d-163">以下新查询使用学生的姓的第一个字母作为关键字对学生进行分组。</span><span class="sxs-lookup"><span data-stu-id="bb77d-163">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. <span data-ttu-id="bb77d-164">注意，查询类型现已更改。</span><span class="sxs-lookup"><span data-stu-id="bb77d-164">Note that the type of the query has now changed.</span></span> <span data-ttu-id="bb77d-165">该查询现在生成一系列将 `char` 类型作为键的组，以及一系列 `Student` 对象。</span><span class="sxs-lookup"><span data-stu-id="bb77d-165">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="bb77d-166">由于查询的类型已更改，因此以下代码也将更改 `foreach` 执行循环：</span><span class="sxs-lookup"><span data-stu-id="bb77d-166">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. <span data-ttu-id="bb77d-167">在“控制台”窗口中运行应用程序并查看结果。</span><span class="sxs-lookup"><span data-stu-id="bb77d-167">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="bb77d-168">有关详细信息，请参阅 [group 子句](../../../language-reference/keywords/group-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="bb77d-168">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="bb77d-169">对变量进行隐式类型化</span><span class="sxs-lookup"><span data-stu-id="bb77d-169">To make the variables implicitly typed</span></span>  
  
1. <span data-ttu-id="bb77d-170">`IGroupings` 的显式编码 `IEnumerables` 将快速变得冗长。</span><span class="sxs-lookup"><span data-stu-id="bb77d-170">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="bb77d-171">使用 `var` 可以更方便地编写相同的查询和 `foreach` 循环。</span><span class="sxs-lookup"><span data-stu-id="bb77d-171">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="bb77d-172">`var` 关键字不会更改对象的类型；它仅指示编译器推断类型。</span><span class="sxs-lookup"><span data-stu-id="bb77d-172">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="bb77d-173">将 `studentQuery` 和迭代变量 `group` 的类型更改为 `var`，然后重新运行查询。</span><span class="sxs-lookup"><span data-stu-id="bb77d-173">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="bb77d-174">注意，在内部 `foreach` 循环中，该迭代变量仍类型化为 `Student`，并且查询的工作原理和以前一样。</span><span class="sxs-lookup"><span data-stu-id="bb77d-174">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="bb77d-175">将 `s` 迭代变量更改为 `var`，然后再次运行查询。</span><span class="sxs-lookup"><span data-stu-id="bb77d-175">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="bb77d-176">将看到完全相同的结果。</span><span class="sxs-lookup"><span data-stu-id="bb77d-176">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     <span data-ttu-id="bb77d-177">有关 [var](../../../language-reference/keywords/var.md) 的详细信息，请参阅[隐式类型化局部变量](../../classes-and-structs/implicitly-typed-local-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="bb77d-177">For more information about [var](../../../language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="bb77d-178">按照键值对组进行排序</span><span class="sxs-lookup"><span data-stu-id="bb77d-178">To order the groups by their key value</span></span>  
  
1. <span data-ttu-id="bb77d-179">运行上一查询时，会发现这些组不是按字母顺序排序的。</span><span class="sxs-lookup"><span data-stu-id="bb77d-179">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="bb77d-180">若要更改此排序，必须在 `group` 子句后提供 `orderby` 子句。</span><span class="sxs-lookup"><span data-stu-id="bb77d-180">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="bb77d-181">但若要使用 `orderby` 子句，首先需要一个标识符，用作对 `group` 子句创建的组的引用。</span><span class="sxs-lookup"><span data-stu-id="bb77d-181">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="bb77d-182">可以使用 `into` 关键字提供该标识符，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bb77d-182">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     <span data-ttu-id="bb77d-183">运行此查询时，将看到这些组现在已按字母顺序排序。</span><span class="sxs-lookup"><span data-stu-id="bb77d-183">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="bb77d-184">使用 let 引入标识符</span><span class="sxs-lookup"><span data-stu-id="bb77d-184">To introduce an identifier by using let</span></span>  
  
1. <span data-ttu-id="bb77d-185">可以使用 `let` 关键字来引入查询表达式中任何表达式结果的标识符。</span><span class="sxs-lookup"><span data-stu-id="bb77d-185">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="bb77d-186">此标识符可以提供方便（如下面的示例所示），也可以通过存储表达式的结果来避免多次计算，从而提高性能。</span><span class="sxs-lookup"><span data-stu-id="bb77d-186">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     <span data-ttu-id="bb77d-187">有关详细信息，请参阅 [let 子句](../../../language-reference/keywords/let-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="bb77d-187">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="bb77d-188">在查询表达式中使用方法语法</span><span class="sxs-lookup"><span data-stu-id="bb77d-188">To use method syntax in a query expression</span></span>  
  
1. <span data-ttu-id="bb77d-189">如 [LINQ 中的查询语法和方法语法](./query-syntax-and-method-syntax-in-linq.md) 中所述，某些查询操作只能使用方法语法来表示。</span><span class="sxs-lookup"><span data-stu-id="bb77d-189">As described in [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="bb77d-190">以下代码为源序列中的每个 `Student` 计算总分，然后对该查询的结果调用 `Average()` 方法来计算班级平均分。</span><span class="sxs-lookup"><span data-stu-id="bb77d-190">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span>
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="bb77d-191">在 select 子句转换或投影</span><span class="sxs-lookup"><span data-stu-id="bb77d-191">To transform or project in the select clause</span></span>  
  
1. <span data-ttu-id="bb77d-192">查询生成的序列的元素与源序列中的元素不同，这种情况很常见。</span><span class="sxs-lookup"><span data-stu-id="bb77d-192">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="bb77d-193">删除或注释掉以前的查询和执行循环，并将其替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="bb77d-193">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="bb77d-194">请注意，该查询将返回字符串序列，而不是 `Students`，这种情况将反映在 `foreach` 循环中。</span><span class="sxs-lookup"><span data-stu-id="bb77d-194">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. <span data-ttu-id="bb77d-195">本演练中前面的代码表明班级平均分大约为 334 分。</span><span class="sxs-lookup"><span data-stu-id="bb77d-195">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="bb77d-196">若要生成总分数高于班级平均分的 `Students` 及其 `Student ID` 的序列，可以在 `select` 语句中使用匿名类型：</span><span class="sxs-lookup"><span data-stu-id="bb77d-196">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a><span data-ttu-id="bb77d-197">后续步骤</span><span class="sxs-lookup"><span data-stu-id="bb77d-197">Next Steps</span></span>  

 <span data-ttu-id="bb77d-198">熟悉了在 C# 中使用查询的基本情况后，便可以开始阅读你感兴趣的具体类型的 LINQ 提供程序的文档和示例：</span><span class="sxs-lookup"><span data-stu-id="bb77d-198">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="bb77d-199">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="bb77d-199">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="bb77d-200">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="bb77d-200">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="bb77d-201">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="bb77d-201">LINQ to XML (C#)</span></span>](../../../../standard/linq/linq-xml-overview.md)  
  
 [<span data-ttu-id="bb77d-202">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="bb77d-202">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="bb77d-203">请参阅</span><span class="sxs-lookup"><span data-stu-id="bb77d-203">See also</span></span>

- [<span data-ttu-id="bb77d-204">语言集成查询 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="bb77d-204">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="bb77d-205">LINQ 查询表达式</span><span class="sxs-lookup"><span data-stu-id="bb77d-205">LINQ Query Expressions</span></span>](../../../linq/index.md)
