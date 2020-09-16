---
title: 如何：调用自定义数据库函数
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: 9879803c970b7965bf152c216367b216e201af38
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540303"
---
# <a name="how-to-call-custom-database-functions"></a><span data-ttu-id="2dcf8-102">如何：调用自定义数据库函数</span><span class="sxs-lookup"><span data-stu-id="2dcf8-102">How to: Call Custom Database Functions</span></span>

<span data-ttu-id="2dcf8-103">本主题介绍如何从 LINQ to Entities 查询中调用在数据库中定义的自定义函数。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-103">This topic describes how to call custom functions that are defined in the database from within LINQ to Entities queries.</span></span>

<span data-ttu-id="2dcf8-104">从 LINQ to Entities 查询中调用的数据库函数在数据库中执行。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-104">Database functions that are called from LINQ to Entities queries are executed in the database.</span></span> <span data-ttu-id="2dcf8-105">在数据库中执行函数可以改进应用程序性能。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-105">Executing functions in the database can improve application performance.</span></span>

<span data-ttu-id="2dcf8-106">下面的过程高度概括了有关调用自定义数据库函数的信息。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-106">The procedure below provides a high-level outline for calling a custom database function.</span></span> <span data-ttu-id="2dcf8-107">后面的示例提供了有关该过程中各个步骤的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-107">The example that follows provides more detail about the steps in the procedure.</span></span>

## <a name="to-call-custom-functions-that-are-defined-in-the-database"></a><span data-ttu-id="2dcf8-108">调用在数据库中定义的自定义函数</span><span class="sxs-lookup"><span data-stu-id="2dcf8-108">To call custom functions that are defined in the database</span></span>

1. <span data-ttu-id="2dcf8-109">在数据库中创建自定义函数。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-109">Create a custom function in your database.</span></span>

     <span data-ttu-id="2dcf8-110">有关在 SQL Server 中创建自定义函数的详细信息，请参阅 [CREATE FUNCTION (transact-sql) ](/sql/t-sql/statements/create-function-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-110">For more information about creating custom functions in SQL Server, see [CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql).</span></span>

2. <span data-ttu-id="2dcf8-111">在您的 .edmx 文件的存储架构定义语言 (SSDL) 中声明一个函数。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-111">Declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="2dcf8-112">该函数的名称必须与在数据库中声明的函数的名称相同。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-112">The name of the function must be the same as the name of the function declared in the database.</span></span>

     <span data-ttu-id="2dcf8-113">有关详细信息，请参阅 [Function 元素 (SSDL) ](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl)。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-113">For more information, see [Function Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span></span>

3. <span data-ttu-id="2dcf8-114">将相应的方法添加到应用程序代码中的类，并将 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 应用于该方法。注意，该特性的 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> 和 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> 参数分别是概念模型的命名空间名称和概念模型中的函数名称。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-114">Add a corresponding method to a class in your application code and apply a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="2dcf8-115">LINQ 的函数名称解析区分大小写。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-115">Function name resolution for LINQ is case sensitive.</span></span>

4. <span data-ttu-id="2dcf8-116">在 LINQ to Entities 查询中调用此方法。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-116">Call the method in a LINQ to Entities query.</span></span>  

## <a name="example"></a><span data-ttu-id="2dcf8-117">示例</span><span class="sxs-lookup"><span data-stu-id="2dcf8-117">Example</span></span>

<span data-ttu-id="2dcf8-118">下面的示例演示如何从 LINQ to Entities 查询中调用自定义数据库函数。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-118">The following example demonstrates how to call a custom database function from within a LINQ to Entities query.</span></span> <span data-ttu-id="2dcf8-119">本示例使用 School 模型。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-119">The example uses the School model.</span></span> <span data-ttu-id="2dcf8-120">有关 School 模型的信息，请参阅 [创建 School 示例数据库](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) 和 [生成 school .edmx 文件](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-120">For information about the School model, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) and [Generating the School .edmx File](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span></span>

<span data-ttu-id="2dcf8-121">下面的代码将 `AvgStudentGrade` 函数添加到 School 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-121">The following code adds the `AvgStudentGrade` function to the School sample database.</span></span>

> [!NOTE]
> <span data-ttu-id="2dcf8-122">用于调用自定义数据库函数的步骤是相同的，与数据库服务器无关。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-122">The steps for calling a custom database function are the same regardless of the database server.</span></span> <span data-ttu-id="2dcf8-123">但是，下面的代码特定于在 SQL Server 数据库中创建函数。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-123">However, the code below is specific to creating a function in a SQL Server database.</span></span> <span data-ttu-id="2dcf8-124">在其他数据库服务器中创建自定义函数的代码可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-124">The code for creating a custom function in other database servers might differ.</span></span>

[!code-sql[DP L2E MapToDBFunction#1](~/samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]

## <a name="example"></a><span data-ttu-id="2dcf8-125">示例</span><span class="sxs-lookup"><span data-stu-id="2dcf8-125">Example</span></span>

<span data-ttu-id="2dcf8-126">接下来，使用存储架构定义语言（ (SSDL) 的 *.edmx* 文件）声明函数。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-126">Next, declare a function in the store schema definition language (SSDL) of your *.edmx* file.</span></span> <span data-ttu-id="2dcf8-127">下面的代码 `AvgStudentGrade` 在 SSDL 中声明函数：</span><span class="sxs-lookup"><span data-stu-id="2dcf8-127">The following code declares the `AvgStudentGrade` function in SSDL:</span></span>

[!code-xml[DP L2E MapToDBFunction#2](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]

## <a name="example"></a><span data-ttu-id="2dcf8-128">示例</span><span class="sxs-lookup"><span data-stu-id="2dcf8-128">Example</span></span>

<span data-ttu-id="2dcf8-129">现在，创建一个方法并将其映射到在 SSDL 中声明的函数。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-129">Now, create a method and map it to the function declared in the SSDL.</span></span> <span data-ttu-id="2dcf8-130">通过使用 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 将以下类中的方法映射到在 SSDL 中定义的函数（上述）。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-130">The method in the following class is mapped to the function defined in the SSDL (above) by using an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="2dcf8-131">调用此方法时，将执行数据库中相应的函数。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-131">When this method is called, the corresponding function in the database is executed.</span></span>

[!code-csharp[DP L2E MapToDBFunction#3](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
[!code-vb[DP L2E MapToDBFunction#3](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="2dcf8-132">示例</span><span class="sxs-lookup"><span data-stu-id="2dcf8-132">Example</span></span>

<span data-ttu-id="2dcf8-133">最后，在 LINQ to Entities 查询中调用此方法。</span><span class="sxs-lookup"><span data-stu-id="2dcf8-133">Finally, call the method in a LINQ to Entities query.</span></span> <span data-ttu-id="2dcf8-134">下面的代码将向控制台显示学生的姓氏和平均年级：</span><span class="sxs-lookup"><span data-stu-id="2dcf8-134">The following code displays students' last names and average grades to the console:</span></span>

[!code-csharp[DP L2E MapToDBFunction#4](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
[!code-vb[DP L2E MapToDBFunction#4](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="2dcf8-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="2dcf8-135">See also</span></span>

- <span data-ttu-id="2dcf8-136">[.edmx 文件概述](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2dcf8-136">[.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="2dcf8-137">LINQ to Entities 中的查询</span><span class="sxs-lookup"><span data-stu-id="2dcf8-137">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
