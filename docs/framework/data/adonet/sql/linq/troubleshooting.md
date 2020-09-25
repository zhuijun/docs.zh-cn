---
title: 疑难解答
ms.date: 03/30/2017
ms.assetid: 8cd4401c-b12c-4116-a421-f3dcffa65670
ms.openlocfilehash: 0ac71d9a55e92161f24deb490b8df6148bfc840c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202183"
---
# <a name="troubleshooting"></a><span data-ttu-id="b117c-102">疑难解答</span><span class="sxs-lookup"><span data-stu-id="b117c-102">Troubleshooting</span></span>

<span data-ttu-id="b117c-103">下面的信息揭示您在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 应用程序中可能遇到的一些问题，并提供建议以避免这些问题或减少这些问题的影响。</span><span class="sxs-lookup"><span data-stu-id="b117c-103">The following information exposes some issues you might encounter in your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications, and provides suggestions to avoid or otherwise reduce the effect of these issues.</span></span>  
  
 <span data-ttu-id="b117c-104">其他问题在 [常见问题](frequently-asked-questions.md)中得到了解决。</span><span class="sxs-lookup"><span data-stu-id="b117c-104">Additional issues are addressed in [Frequently Asked Questions](frequently-asked-questions.md).</span></span>  
  
## <a name="unsupported-standard-query-operators"></a><span data-ttu-id="b117c-105">不支持的标准查询运算符</span><span class="sxs-lookup"><span data-stu-id="b117c-105">Unsupported Standard Query Operators</span></span>  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b117c-106">不支持某些标准查询运算符方法（例如，<xref:System.Linq.Enumerable.ElementAt%2A>）。</span><span class="sxs-lookup"><span data-stu-id="b117c-106">does not support all standard query operator methods (for example, <xref:System.Linq.Enumerable.ElementAt%2A>).</span></span> <span data-ttu-id="b117c-107">因此，编译后的项目仍然可能产生运行时错误。</span><span class="sxs-lookup"><span data-stu-id="b117c-107">As a result, projects that compile can still produce run-time errors.</span></span> <span data-ttu-id="b117c-108">有关详细信息，请参阅 [标准查询运算符转换](standard-query-operator-translation.md)。</span><span class="sxs-lookup"><span data-stu-id="b117c-108">For more information, see [Standard Query Operator Translation](standard-query-operator-translation.md).</span></span>  
  
## <a name="memory-issues"></a><span data-ttu-id="b117c-109">内存问题</span><span class="sxs-lookup"><span data-stu-id="b117c-109">Memory Issues</span></span>  

 <span data-ttu-id="b117c-110">如果查询涉及内存中集合和 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> ，则该查询可能在内存中执行，具体取决于指定这两个集合的顺序。</span><span class="sxs-lookup"><span data-stu-id="b117c-110">If a query involves an in-memory collection and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601>, the query might be executed in memory, depending on the order in which the two collections are specified.</span></span> <span data-ttu-id="b117c-111">如果该查询必须在内存中执行，则需要检索数据库表中的数据。</span><span class="sxs-lookup"><span data-stu-id="b117c-111">If the query must be executed in memory, then the data from the database table will need to be retrieved.</span></span>  
  
 <span data-ttu-id="b117c-112">此方法的效率十分低下，并可能占用大量内存和处理器时间。</span><span class="sxs-lookup"><span data-stu-id="b117c-112">This approach is inefficient and could result in significant memory and processor usage.</span></span> <span data-ttu-id="b117c-113">请尽量避免这种多域查询。</span><span class="sxs-lookup"><span data-stu-id="b117c-113">Try to avoid such multi-domain queries.</span></span>  
  
## <a name="file-names-and-sqlmetal"></a><span data-ttu-id="b117c-114">文件名和 SQLMetal</span><span class="sxs-lookup"><span data-stu-id="b117c-114">File Names and SQLMetal</span></span>  

 <span data-ttu-id="b117c-115">若要指定一个输入文件名，请将该名称作为输入文件添加到命令行。</span><span class="sxs-lookup"><span data-stu-id="b117c-115">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="b117c-116">不支持在连接字符串中包含文件名（使用 **/conn** 选项）。</span><span class="sxs-lookup"><span data-stu-id="b117c-116">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span> <span data-ttu-id="b117c-117">有关详细信息，请参阅 [SqlMetal.exe（代码生成工具）](../../../../tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="b117c-117">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="class-library-projects"></a><span data-ttu-id="b117c-118">类库项目</span><span class="sxs-lookup"><span data-stu-id="b117c-118">Class Library Projects</span></span>  

 <span data-ttu-id="b117c-119">对象关系设计器在项目的文件中创建一个连接字符串 `app.config` 。</span><span class="sxs-lookup"><span data-stu-id="b117c-119">The Object Relational Designer creates a connection string in the `app.config` file of the project.</span></span> <span data-ttu-id="b117c-120">在类库项目中，不使用 `app.config` 文件。</span><span class="sxs-lookup"><span data-stu-id="b117c-120">In class library projects, the `app.config` file is not used.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b117c-121">使用在设计时文件中提供的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="b117c-121">uses the Connection String provided in the design-time files.</span></span> <span data-ttu-id="b117c-122">更改 `app.config` 中的值不会更改应用程序连接到的数据库。</span><span class="sxs-lookup"><span data-stu-id="b117c-122">Changing the value in `app.config` does not change the database to which your application connects.</span></span>  
  
## <a name="cascade-delete"></a><span data-ttu-id="b117c-123">级联删除</span><span class="sxs-lookup"><span data-stu-id="b117c-123">Cascade Delete</span></span>  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b117c-124">不支持且无法识别级联删除操作。</span><span class="sxs-lookup"><span data-stu-id="b117c-124">does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="b117c-125">如果要在表中删除一个具有约束的行，必须执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="b117c-125">If you want to delete a row in a table that has constraints against it, you must do either of the following:</span></span>  
  
- <span data-ttu-id="b117c-126">在数据库的外键约束中设置 `ON DELETE CASCADE` 规则。</span><span class="sxs-lookup"><span data-stu-id="b117c-126">Set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database.</span></span>  
  
- <span data-ttu-id="b117c-127">使用你自己的代码先删除阻止删除父对象的子对象。</span><span class="sxs-lookup"><span data-stu-id="b117c-127">Use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span>  
  
 <span data-ttu-id="b117c-128">否则，将引发 <xref:System.Data.SqlClient.SqlException> 异常。</span><span class="sxs-lookup"><span data-stu-id="b117c-128">Otherwise, a <xref:System.Data.SqlClient.SqlException> exception is thrown.</span></span>  
  
 <span data-ttu-id="b117c-129">有关详细信息，请参阅 [如何：从数据库中删除行](how-to-delete-rows-from-the-database.md)。</span><span class="sxs-lookup"><span data-stu-id="b117c-129">For more information, see [How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md).</span></span>  
  
## <a name="expression-not-queryable"></a><span data-ttu-id="b117c-130">不可查询的表达式</span><span class="sxs-lookup"><span data-stu-id="b117c-130">Expression Not Queryable</span></span>  

 <span data-ttu-id="b117c-131">如果收到错误消息“表达式 [表达式] 不可查询；是否缺少程序集引用?”</span><span class="sxs-lookup"><span data-stu-id="b117c-131">If you get the "Expression [expression] is not queryable; are you missing an assembly reference?"</span></span> <span data-ttu-id="b117c-132">，请确保满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="b117c-132">error, make sure of the following:</span></span>  
  
- <span data-ttu-id="b117c-133">应用程序面向 .NET Compact Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="b117c-133">Your application is targeting .NET Compact Framework 3.5.</span></span>  
  
- <span data-ttu-id="b117c-134">您具有对 `System.Core.dll` 和 `System.Data.Linq.dll` 的引用。</span><span class="sxs-lookup"><span data-stu-id="b117c-134">You have a reference to `System.Core.dll` and `System.Data.Linq.dll`.</span></span>  
  
- <span data-ttu-id="b117c-135">你有 `Imports` (Visual Basic) 或 `using` (c # ) 指令用于 <xref:System.Linq> 和 <xref:System.Data.Linq> 。</span><span class="sxs-lookup"><span data-stu-id="b117c-135">You have an `Imports` (Visual Basic) or `using` (C#) directive for <xref:System.Linq> and <xref:System.Data.Linq>.</span></span>  
  
## <a name="duplicatekeyexception"></a><span data-ttu-id="b117c-136">DuplicateKeyException</span><span class="sxs-lookup"><span data-stu-id="b117c-136">DuplicateKeyException</span></span>  

 <span data-ttu-id="b117c-137">在调试 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 项目的过程中，可能会遍历某个实体的关系。</span><span class="sxs-lookup"><span data-stu-id="b117c-137">In the course of debugging a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project, you might traverse an entity's relations.</span></span> <span data-ttu-id="b117c-138">这样做会使这些项进入缓存，而 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会检测到这些项的存在。</span><span class="sxs-lookup"><span data-stu-id="b117c-138">Doing so brings these items into the cache, and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] becomes aware of their presence.</span></span> <span data-ttu-id="b117c-139">如果随后试图执行 <xref:System.Data.Linq.Table%601.Attach%2A> 或 <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>，或者执行一个生成具有相同键的多个行的类似方法，则会引发 <xref:System.Data.Linq.DuplicateKeyException>。</span><span class="sxs-lookup"><span data-stu-id="b117c-139">If you then try to execute <xref:System.Data.Linq.Table%601.Attach%2A> or <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> or a similar method that produces multiple rows that have the same key, a <xref:System.Data.Linq.DuplicateKeyException> is thrown.</span></span>  
  
## <a name="string-concatenation-exceptions"></a><span data-ttu-id="b117c-140">字符串串联异常</span><span class="sxs-lookup"><span data-stu-id="b117c-140">String Concatenation Exceptions</span></span>  

 <span data-ttu-id="b117c-141">不支持映射到 `[n]text` 和其他 `[n][var]char` 的操作数的串联。</span><span class="sxs-lookup"><span data-stu-id="b117c-141">Concatenation on operands mapped to `[n]text` and other `[n][var]char` is not supported.</span></span> <span data-ttu-id="b117c-142">映射到两个不同类型集的字符串的串联会引发异常。</span><span class="sxs-lookup"><span data-stu-id="b117c-142">An exception is thrown for concatenation of strings mapped to the two different sets of types.</span></span> <span data-ttu-id="b117c-143">有关详细信息，请参阅 [System.string 方法](system-string-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="b117c-143">For more information, see [System.String Methods](system-string-methods.md).</span></span>  
  
## <a name="skip-and-take-exceptions-in-sql-server-2000"></a><span data-ttu-id="b117c-144">SQL Server 2000 中的 Skip 和 Take 异常</span><span class="sxs-lookup"><span data-stu-id="b117c-144">Skip and Take Exceptions in SQL Server 2000</span></span>  

 <span data-ttu-id="b117c-145">在对 SQL Server 2000 数据库使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> 或 <xref:System.Linq.Queryable.Take%2A> 时，必须使用标识成员 (<xref:System.Linq.Queryable.Skip%2A>)。</span><span class="sxs-lookup"><span data-stu-id="b117c-145">You must use identity members (<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>) when you use <xref:System.Linq.Queryable.Take%2A> or <xref:System.Linq.Queryable.Skip%2A> against a SQL Server 2000 database.</span></span> <span data-ttu-id="b117c-146">查询必须针对单个表（即，不是联接），或必须为 <xref:System.Linq.Queryable.Distinct%2A>、<xref:System.Linq.Queryable.Except%2A>、<xref:System.Linq.Queryable.Intersect%2A> 或 <xref:System.Linq.Queryable.Union%2A> 操作，且不得包含 <xref:System.Linq.Queryable.Concat%2A> 操作。</span><span class="sxs-lookup"><span data-stu-id="b117c-146">The query must be against a single table (that is, not a join), or be a <xref:System.Linq.Queryable.Distinct%2A>, <xref:System.Linq.Queryable.Except%2A>, <xref:System.Linq.Queryable.Intersect%2A>, or <xref:System.Linq.Queryable.Union%2A> operation, and must not include a <xref:System.Linq.Queryable.Concat%2A> operation.</span></span> <span data-ttu-id="b117c-147">有关详细信息，请参阅 [标准查询运算符转换](standard-query-operator-translation.md)中的 "SQL Server 2000 支持" 部分。</span><span class="sxs-lookup"><span data-stu-id="b117c-147">For more information, see the "SQL Server 2000 Support" section in [Standard Query Operator Translation](standard-query-operator-translation.md).</span></span>  
  
 <span data-ttu-id="b117c-148">此要求不适用于 SQL Server 2005。</span><span class="sxs-lookup"><span data-stu-id="b117c-148">This requirement does not apply to SQL Server 2005.</span></span>  
  
## <a name="groupby-invalidoperationexception"></a><span data-ttu-id="b117c-149">GroupBy InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="b117c-149">GroupBy InvalidOperationException</span></span>  

 <span data-ttu-id="b117c-150">如果在按 <xref:System.Linq.Enumerable.GroupBy%2A> 表达式进行分组的 `boolean` 查询（如 `group x by (Phone==@phone)`）中有一个列值为 null，则会引发此异常。</span><span class="sxs-lookup"><span data-stu-id="b117c-150">This exception is thrown when a column value is null in a <xref:System.Linq.Enumerable.GroupBy%2A> query that groups by a `boolean` expression, such as `group x by (Phone==@phone)`.</span></span> <span data-ttu-id="b117c-151">由于表达式为，因此会将 `boolean` 该键推断为 `boolean` ，而不是 `nullable` `boolean` 。</span><span class="sxs-lookup"><span data-stu-id="b117c-151">Because the expression is a `boolean`, the key is inferred to be `boolean`, not `nullable` `boolean`.</span></span> <span data-ttu-id="b117c-152">当转换的比较产生 null 时，会尝试将分配给 `nullable` `boolean` `boolean` ，并引发异常。</span><span class="sxs-lookup"><span data-stu-id="b117c-152">When the translated comparison produces a null, an attempt is made to assign a `nullable` `boolean` to a `boolean`, and the exception is thrown.</span></span>  
  
 <span data-ttu-id="b117c-153">若要避免发生这种情况（假定您希望将 null 视为 false），请使用如下方式：</span><span class="sxs-lookup"><span data-stu-id="b117c-153">To avoid this situation (assuming you want to treat nulls as false), use an approach such as the following:</span></span>  
  
 `GroupBy="(Phone != null) && (Phone=@Phone)"`  
  
## <a name="oncreated-partial-method"></a><span data-ttu-id="b117c-154">OnCreated() 分部方法</span><span class="sxs-lookup"><span data-stu-id="b117c-154">OnCreated() Partial Method</span></span>  

 <span data-ttu-id="b117c-155">每次调用对象构造函数时都会调用生成的方法 `OnCreated()`，这包括以下这种情况，即 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 调用构造函数以生成原始值的副本。</span><span class="sxs-lookup"><span data-stu-id="b117c-155">The generated method `OnCreated()` is called each time the object constructor is called, including the scenario in which [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] calls the constructor to make a copy for original values.</span></span> <span data-ttu-id="b117c-156">如果您在自己的分部类中实现 `OnCreated()` 方法，请考虑此行为。</span><span class="sxs-lookup"><span data-stu-id="b117c-156">Take this behavior into account if you implement the `OnCreated()` method in your own partial class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b117c-157">请参阅</span><span class="sxs-lookup"><span data-stu-id="b117c-157">See also</span></span>

- [<span data-ttu-id="b117c-158">调试支持</span><span class="sxs-lookup"><span data-stu-id="b117c-158">Debugging Support</span></span>](debugging-support.md)
- [<span data-ttu-id="b117c-159">常见问题解答</span><span class="sxs-lookup"><span data-stu-id="b117c-159">Frequently Asked Questions</span></span>](frequently-asked-questions.md)
