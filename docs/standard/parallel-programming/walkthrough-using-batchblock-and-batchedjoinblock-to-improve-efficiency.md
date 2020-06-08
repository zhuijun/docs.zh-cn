---
title: 演练：使用 BatchBlock 和 BatchedJoinBlock 提高效率
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
ms.openlocfilehash: e572c5a14958ccc069ae7649af8c8ed4eb967dc1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284580"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="dbe8a-102">演练：使用 BatchBlock 和 BatchedJoinBlock 提高效率</span><span class="sxs-lookup"><span data-stu-id="dbe8a-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>

<span data-ttu-id="dbe8a-103">TPL 数据流库提供 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> 类，以便可以接收和缓冲一个或多个源的数据，再将缓冲的数据作为一个集合传播出去。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="dbe8a-104">如果从一个或多个源收集数据，再批处理多个数据元素，就会发现这种批处理机制非常有用。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="dbe8a-105">例如，假设应用使用数据流将记录插入数据库。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="dbe8a-106">如果同时插入多项，而不是顺序一次插入一个，此操作可能会更高效。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="dbe8a-107">本文档介绍了如何使用 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 类，提高此类数据库插入操作的效率。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="dbe8a-108">它还介绍了如何使用 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 类，捕获程序从数据库读取数据时的结果和发生的任何异常。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a><span data-ttu-id="dbe8a-109">系统必备</span><span class="sxs-lookup"><span data-stu-id="dbe8a-109">Prerequisites</span></span>

1. <span data-ttu-id="dbe8a-110">开始本演练前，请先阅读[数据流](dataflow-task-parallel-library.md)文档中的“联接块”部分。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-110">Read the Join Blocks section in the [Dataflow](dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>

2. <span data-ttu-id="dbe8a-111">确保计算机上有 Northwind 数据库的副本 Northwind.sdf。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-111">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="dbe8a-112">此文件通常位于 %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\ 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-112">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="dbe8a-113">在一些版本的 Windows 中，如果以非管理员模式运行 Visual Studio，便无法连接到 Northwind.sdf。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-113">In some versions of Windows, you cannot connect to Northwind.sdf if Visual Studio is running in a non-administrator mode.</span></span> <span data-ttu-id="dbe8a-114">若要连接到 Northwind.sdf，请在“以管理员身份运行”模式下启动 Visual Studio 或 Visual Studio 开发人员命令提示  。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-114">To connect to Northwind.sdf, start Visual Studio or a Developer Command Prompt for Visual Studio in the **Run as administrator** mode.</span></span>

<span data-ttu-id="dbe8a-115">本演练包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="dbe8a-115">This walkthrough contains the following sections:</span></span>

- [<span data-ttu-id="dbe8a-116">创建控制台应用</span><span class="sxs-lookup"><span data-stu-id="dbe8a-116">Creating the Console Application</span></span>](#creating)

- [<span data-ttu-id="dbe8a-117">定义 Employee 类</span><span class="sxs-lookup"><span data-stu-id="dbe8a-117">Defining the Employee Class</span></span>](#employeeClass)

- [<span data-ttu-id="dbe8a-118">定义员工数据库操作</span><span class="sxs-lookup"><span data-stu-id="dbe8a-118">Defining Employee Database Operations</span></span>](#operations)

- [<span data-ttu-id="dbe8a-119">不使用缓冲将员工数据添加到数据库</span><span class="sxs-lookup"><span data-stu-id="dbe8a-119">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)

- [<span data-ttu-id="dbe8a-120">使用缓冲将员工数据添加到数据库</span><span class="sxs-lookup"><span data-stu-id="dbe8a-120">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)

- [<span data-ttu-id="dbe8a-121">使用已缓冲联接读取数据库中的员工数据</span><span class="sxs-lookup"><span data-stu-id="dbe8a-121">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)

- [<span data-ttu-id="dbe8a-122">完整示例</span><span class="sxs-lookup"><span data-stu-id="dbe8a-122">The Complete Example</span></span>](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a><span data-ttu-id="dbe8a-123">创建控制台应用</span><span class="sxs-lookup"><span data-stu-id="dbe8a-123">Creating the Console Application</span></span>

1. <span data-ttu-id="dbe8a-124">在 Visual Studio 中，创建 Visual C# 或 Visual Basic“控制台应用程序”  项目。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-124">In Visual Studio, create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="dbe8a-125">在本文档中，该项目名为 `DataflowBatchDatabase`。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-125">In this document, the project is named `DataflowBatchDatabase`.</span></span>

2. <span data-ttu-id="dbe8a-126">在项目中，添加对 System.Data.SqlServerCe.dll 和 System.Threading.Tasks.Dataflow.dll 的引用。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-126">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>

3. <span data-ttu-id="dbe8a-127">确保 Form1.cs（对于 Visual Basic，则为 Form1.vb）包含以下 `using`（Visual Basic 中为 `Imports`）语句。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-127">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Imports` in Visual Basic) statements.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. <span data-ttu-id="dbe8a-128">将以下数据成员添加到 `Program` 类。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-128">Add the following data members to the `Program` class.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a><span data-ttu-id="dbe8a-129">定义 Employee 类</span><span class="sxs-lookup"><span data-stu-id="dbe8a-129">Defining the Employee Class</span></span>

<span data-ttu-id="dbe8a-130">向 `Program` 类添加 `Employee` 类。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-130">Add to the `Program` class the `Employee` class.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

<span data-ttu-id="dbe8a-131">`Employee` 类包含下面三个属性：`EmployeeID`、`LastName` 和 `FirstName`。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-131">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="dbe8a-132">这些属性对应于 Northwind 数据库中 `Employees` 表的 `Employee ID`、`Last Name` 和 `First Name` 列。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-132">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="dbe8a-133">在展示的此示例中，`Employee` 类还定义了 `Random` 方法，用于创建属性值为随机值的 `Employee` 对象。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-133">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a><span data-ttu-id="dbe8a-134">定义员工数据库操作</span><span class="sxs-lookup"><span data-stu-id="dbe8a-134">Defining Employee Database Operations</span></span>

<span data-ttu-id="dbe8a-135">向 `Program` 添加 `InsertEmployees`、`GetEmployeeCount` 和 `GetEmployeeID` 方法。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-135">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

<span data-ttu-id="dbe8a-136">`InsertEmployees` 方法将新员工记录添加到数据库。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-136">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="dbe8a-137">`GetEmployeeCount` 方法检索 `Employees` 表中的条目数。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-137">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="dbe8a-138">`GetEmployeeID` 方法检索与所提供姓名匹配的首位员工的标识符。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-138">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="dbe8a-139">这三个方法全都需要对 Northwind 数据库使用连接字符串，并使用 `System.Data.SqlServerCe` 命名空间中的功能与数据库进行通信。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-139">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="dbe8a-140">不使用缓冲将员工数据添加到数据库</span><span class="sxs-lookup"><span data-stu-id="dbe8a-140">Adding Employee Data to the Database Without Using Buffering</span></span>

<span data-ttu-id="dbe8a-141">向 `Program` 类添加 `AddEmployees` 和 `PostRandomEmployees` 方法。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-141">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

<span data-ttu-id="dbe8a-142">`AddEmployees` 方法使用数据流将随机员工数据添加到数据库。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-142">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="dbe8a-143">此方法创建 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 对象，以调用 `InsertEmployees` 方法将员工条目添加到数据库。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-143">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="dbe8a-144">然后，`AddEmployees` 方法调用 `PostRandomEmployees` 方法，将多个 `Employee` 对象发布到 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 对象。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-144">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="dbe8a-145">然后，`AddEmployees` 方法等待所有插入操作完成。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-145">The `AddEmployees` method then waits for all insert operations to finish.</span></span>

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="dbe8a-146">使用缓冲将员工数据添加到数据库</span><span class="sxs-lookup"><span data-stu-id="dbe8a-146">Using Buffering to Add Employee Data to the Database</span></span>

<span data-ttu-id="dbe8a-147">向 `Program` 类添加 `AddEmployeesBatched` 方法。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-147">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

<span data-ttu-id="dbe8a-148">此方法类似于 `AddEmployees`，不同之处在于它还先使用 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 类缓冲多个 `Employee` 对象，然后再将这些对象发送给 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 对象。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-148">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="dbe8a-149">由于 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 类将多个元素以集合形式传播出去，因此 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 对象被修改为对 `Employee` 对象的数组执行操作。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-149">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="dbe8a-150">与 `AddEmployees` 方法类似，`AddEmployeesBatched` 调用 `PostRandomEmployees` 方法发布多个 `Employee` 对象；不同之处在于，`AddEmployeesBatched` 将这些对象发布到 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 对象。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-150">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="dbe8a-151">`AddEmployeesBatched` 方法还等待所有插入操作完成。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-151">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="dbe8a-152">使用已缓冲联接读取数据库中的员工数据</span><span class="sxs-lookup"><span data-stu-id="dbe8a-152">Using Buffered Join to Read Employee Data from the Database</span></span>

<span data-ttu-id="dbe8a-153">向 `Program` 类添加 `GetRandomEmployees` 方法。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-153">Add to the `Program` class the `GetRandomEmployees` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

<span data-ttu-id="dbe8a-154">此方法将随机员工信息打印到控制台中。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-154">This method prints information about random employees to the console.</span></span> <span data-ttu-id="dbe8a-155">它会创建多个随机 `Employee` 对象，并调用 `GetEmployeeID` 方法检索每个对象的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-155">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="dbe8a-156">由于 `GetEmployeeID` 方法在找不到与给定姓氏和名字匹配的员工时抛出异常，因此 `GetRandomEmployees` 方法使用 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 类存储 `GetEmployeeID` 成功调用对应的 `Employee` 对象，以及失败调用对应的 <xref:System.Exception?displayProperty=nameWithType> 对象。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-156">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="dbe8a-157">此示例中的 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 对象对保留 `Employee` 对象列表和 <xref:System.Exception> 对象列表的 <xref:System.Tuple%602> 对象执行操作。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-157">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="dbe8a-158">如果收到的 `Employee` 和 <xref:System.Exception> 对象数总和等于批大小，<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 对象就会传播出此类数据。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-158">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>

<a name="complete"></a>

## <a name="the-complete-example"></a><span data-ttu-id="dbe8a-159">完整示例</span><span class="sxs-lookup"><span data-stu-id="dbe8a-159">The Complete Example</span></span>

<span data-ttu-id="dbe8a-160">以下示例显示了完整的代码。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-160">The following example shows the complete code.</span></span> <span data-ttu-id="dbe8a-161">`Main` 方法比较执行批量数据库插入和非批量数据库插入所需的时间。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-161">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="dbe8a-162">它还展示了如何使用已缓冲联接，读取数据库中的员工数据并报告错误。</span><span class="sxs-lookup"><span data-stu-id="dbe8a-162">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a><span data-ttu-id="dbe8a-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dbe8a-163">See also</span></span>

- [<span data-ttu-id="dbe8a-164">数据流</span><span class="sxs-lookup"><span data-stu-id="dbe8a-164">Dataflow</span></span>](dataflow-task-parallel-library.md)
