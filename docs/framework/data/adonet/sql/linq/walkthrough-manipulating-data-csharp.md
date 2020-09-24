---
title: 演练：操作数据 (C#)
ms.date: 03/30/2017
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
ms.openlocfilehash: fefbee533634ee42785c65e0265ce1e0567561b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164059"
---
# <a name="walkthrough-manipulating-data-c"></a><span data-ttu-id="d5a64-102">演练：操作数据 (C#)</span><span class="sxs-lookup"><span data-stu-id="d5a64-102">Walkthrough: Manipulating Data (C#)</span></span>

<span data-ttu-id="d5a64-103">本演练提供了用于在数据库中添加、修改和删除数据的基本端对端 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 方案。</span><span class="sxs-lookup"><span data-stu-id="d5a64-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="d5a64-104">您将使用 Northwind 示例数据库的一个副本来添加一位客户，更改该客户的姓名，然后删除一个订单。</span><span class="sxs-lookup"><span data-stu-id="d5a64-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="d5a64-105">本演练是使用 Visual C# 开发设置编写的。</span><span class="sxs-lookup"><span data-stu-id="d5a64-105">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d5a64-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="d5a64-106">Prerequisites</span></span>  

 <span data-ttu-id="d5a64-107">本演练需要如下内容：</span><span class="sxs-lookup"><span data-stu-id="d5a64-107">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="d5a64-108">本演练使用专用文件夹（“c:\linqtest6”）来保存文件。</span><span class="sxs-lookup"><span data-stu-id="d5a64-108">This walkthrough uses a dedicated folder ("c:\linqtest6") to hold files.</span></span> <span data-ttu-id="d5a64-109">请在开始本演练前创建此文件夹。</span><span class="sxs-lookup"><span data-stu-id="d5a64-109">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="d5a64-110">Northwind 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="d5a64-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="d5a64-111">如果您的开发计算机上没有此数据库，您可以从 Microsoft 下载网站下载它。</span><span class="sxs-lookup"><span data-stu-id="d5a64-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="d5a64-112">有关说明，请参阅 [下载示例数据库](downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="d5a64-112">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="d5a64-113">下载此数据库后，请将 northwnd.mdf 文件复制到 c:\linqtest6 文件夹。</span><span class="sxs-lookup"><span data-stu-id="d5a64-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest6 folder.</span></span>  
  
- <span data-ttu-id="d5a64-114">从 Northwind 数据库生成的 C# 代码文件。</span><span class="sxs-lookup"><span data-stu-id="d5a64-114">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="d5a64-115">您可以使用对象关系设计器或 SQLMetal 工具生成此文件。</span><span class="sxs-lookup"><span data-stu-id="d5a64-115">You can generate this file by using either the Object Relational Designer or the SQLMetal tool.</span></span> <span data-ttu-id="d5a64-116">本演练是通过使用 SQLMetal 工具以及如下命令行编写的：</span><span class="sxs-lookup"><span data-stu-id="d5a64-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="d5a64-117">**sqlmetal/code： "c:\linqtest6\northwind.cs"/language： csharp "C:\linqtest6\northwnd.mdf"/pluralize**</span><span class="sxs-lookup"><span data-stu-id="d5a64-117">**sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="d5a64-118">有关详细信息，请参阅 [SqlMetal.exe（代码生成工具）](../../../../tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="d5a64-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="d5a64-119">概述</span><span class="sxs-lookup"><span data-stu-id="d5a64-119">Overview</span></span>  

 <span data-ttu-id="d5a64-120">本演练由六项主要任务组成：</span><span class="sxs-lookup"><span data-stu-id="d5a64-120">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="d5a64-121">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]在 Visual Studio 中创建解决方案。</span><span class="sxs-lookup"><span data-stu-id="d5a64-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="d5a64-122">向项目添加数据库代码文件。</span><span class="sxs-lookup"><span data-stu-id="d5a64-122">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="d5a64-123">创建新的客户对象。</span><span class="sxs-lookup"><span data-stu-id="d5a64-123">Creating a new customer object.</span></span>  
  
- <span data-ttu-id="d5a64-124">修改客户的联系人姓名。</span><span class="sxs-lookup"><span data-stu-id="d5a64-124">Modifying the contact name of a customer.</span></span>  
  
- <span data-ttu-id="d5a64-125">删除订单。</span><span class="sxs-lookup"><span data-stu-id="d5a64-125">Deleting an order.</span></span>  
  
- <span data-ttu-id="d5a64-126">将这些更改提交至 Northwind 数据库。</span><span class="sxs-lookup"><span data-stu-id="d5a64-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="d5a64-127">创建 LINQ to SQL 解决方案</span><span class="sxs-lookup"><span data-stu-id="d5a64-127">Creating a LINQ to SQL Solution</span></span>  

 <span data-ttu-id="d5a64-128">在第一个任务中，您将创建一个 Visual Studio 解决方案，其中包含生成和运行项目所必需的引用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d5a64-128">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="d5a64-129">创建 LINQ to SQL 解决方案</span><span class="sxs-lookup"><span data-stu-id="d5a64-129">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="d5a64-130">在 Visual Studio 的 " **文件** " 菜单上，指向 " **新建**"，然后单击 " **项目**"。</span><span class="sxs-lookup"><span data-stu-id="d5a64-130">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="d5a64-131">在 "**新建项目**" 对话框的 "**项目类型**" 窗格中，单击 " **Visual c #**"。</span><span class="sxs-lookup"><span data-stu-id="d5a64-131">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3. <span data-ttu-id="d5a64-132">在“模板”窗格中，单击“控制台应用程序”。</span><span class="sxs-lookup"><span data-stu-id="d5a64-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="d5a64-133">在 " **名称** " 框中，键入 **LinqDataManipulationApp**。</span><span class="sxs-lookup"><span data-stu-id="d5a64-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5. <span data-ttu-id="d5a64-134">在 " **位置** " 框中，验证要存储项目文件的位置。</span><span class="sxs-lookup"><span data-stu-id="d5a64-134">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6. <span data-ttu-id="d5a64-135">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="d5a64-135">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="d5a64-136">添加 LINQ 引用和指令</span><span class="sxs-lookup"><span data-stu-id="d5a64-136">Adding LINQ References and Directives</span></span>  

 <span data-ttu-id="d5a64-137">本演练用到默认情况下您的项目中可能未安装的程序集。</span><span class="sxs-lookup"><span data-stu-id="d5a64-137">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="d5a64-138">如果在您的项目中未将 System.Data.Linq 作为引用列出，请按照以下步骤中的说明添加它。</span><span class="sxs-lookup"><span data-stu-id="d5a64-138">If System.Data.Linq is not listed as a reference in your project, add it, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="d5a64-139">添加 System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="d5a64-139">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="d5a64-140">在 **解决方案资源管理器**中，右键单击 " **引用**"，然后单击 " **添加引用**"。</span><span class="sxs-lookup"><span data-stu-id="d5a64-140">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="d5a64-141">在 " **添加引用** " 对话框中，单击 " **.net**"，单击 "system.web" 程序集，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="d5a64-141">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d5a64-142">此程序集即被添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="d5a64-142">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="d5a64-143">在 Program.cs 的顶部添加以下指令：</span><span class="sxs-lookup"><span data-stu-id="d5a64-143">Add the following directives at the top of Program.cs:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="d5a64-144">将 Northwind 代码文件添加到项目</span><span class="sxs-lookup"><span data-stu-id="d5a64-144">Adding the Northwind Code File to the Project</span></span>  

 <span data-ttu-id="d5a64-145">以下这些步骤假定你已使用 SQLMetal 工具从 Northwind 示例数据库生成代码文件。</span><span class="sxs-lookup"><span data-stu-id="d5a64-145">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="d5a64-146">有关更多信息，请参见本演练前面部分的“先决条件”一节。</span><span class="sxs-lookup"><span data-stu-id="d5a64-146">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="d5a64-147">将 northwind 代码文件添加到项目</span><span class="sxs-lookup"><span data-stu-id="d5a64-147">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="d5a64-148">在“项目”\*\*\*\* 菜单上，单击“添加现有项”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d5a64-148">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="d5a64-149">在 " **添加现有项** " 对话框中，导航到 "c:\linqtest6\northwind.cs"，然后单击 " **添加**"。</span><span class="sxs-lookup"><span data-stu-id="d5a64-149">In the **Add Existing Item** dialog box, navigate to c:\linqtest6\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="d5a64-150">northwind.cs 文件即被添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="d5a64-150">The northwind.cs file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="d5a64-151">设置数据库连接</span><span class="sxs-lookup"><span data-stu-id="d5a64-151">Setting Up the Database Connection</span></span>  

 <span data-ttu-id="d5a64-152">首先，测试与数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="d5a64-152">First, test your connection to the database.</span></span> <span data-ttu-id="d5a64-153">特别要注意，数据库 Northwnd 不含 i 字符。</span><span class="sxs-lookup"><span data-stu-id="d5a64-153">Note especially that the database, Northwnd, has no i character.</span></span> <span data-ttu-id="d5a64-154">如果在后面的步骤中产生错误，请检查 northwind.cs 文件以确定 Northwind 分部类的拼法。</span><span class="sxs-lookup"><span data-stu-id="d5a64-154">If you generate errors in the next steps, review the northwind.cs file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="d5a64-155">设置并测试数据库连接</span><span class="sxs-lookup"><span data-stu-id="d5a64-155">To set up and test the database connection</span></span>  
  
1. <span data-ttu-id="d5a64-156">将下面的代码键入或粘贴到 Program 类的 `Main` 方法中：</span><span class="sxs-lookup"><span data-stu-id="d5a64-156">Type or paste the following code into the `Main` method in the Program class:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2. <span data-ttu-id="d5a64-157">按 F5 在此点测试应用程序。</span><span class="sxs-lookup"><span data-stu-id="d5a64-157">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="d5a64-158">此时将打开一个 **控制台** 窗口。</span><span class="sxs-lookup"><span data-stu-id="d5a64-158">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="d5a64-159">可以通过在**控制台**窗口中按 enter，或在 Visual Studio 的 "**调试**" 菜单上单击 "**停止调试**" 来关闭应用程序。</span><span class="sxs-lookup"><span data-stu-id="d5a64-159">You can close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="d5a64-160">创建新实体</span><span class="sxs-lookup"><span data-stu-id="d5a64-160">Creating a New Entity</span></span>  

 <span data-ttu-id="d5a64-161">创建新实体很简单。</span><span class="sxs-lookup"><span data-stu-id="d5a64-161">Creating a new entity is straightforward.</span></span> <span data-ttu-id="d5a64-162">可以使用 `Customer` 关键字创建对象（如 `new`）。</span><span class="sxs-lookup"><span data-stu-id="d5a64-162">You can create objects (such as `Customer`) by using the `new` keyword.</span></span>  
  
 <span data-ttu-id="d5a64-163">在本节及后续各节中，您将只对本地缓存进行更改。</span><span class="sxs-lookup"><span data-stu-id="d5a64-163">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="d5a64-164">如果您不调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A>，则不会向数据库发送任何更改，一直到本演练结束都是如此。</span><span class="sxs-lookup"><span data-stu-id="d5a64-164">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="d5a64-165">添加新的 Customer 实体对象</span><span class="sxs-lookup"><span data-stu-id="d5a64-165">To add a new Customer entity object</span></span>  
  
1. <span data-ttu-id="d5a64-166">通过在 `Customer` 方法中的 `Console.ReadLine();` 前添加如下代码，创建一个新的 `Main`：</span><span class="sxs-lookup"><span data-stu-id="d5a64-166">Create a new `Customer` by adding the following code before `Console.ReadLine();` in the `Main` method:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2. <span data-ttu-id="d5a64-167">按 F5 调试解决方案。</span><span class="sxs-lookup"><span data-stu-id="d5a64-167">Press F5 to debug the solution.</span></span>  
  
3. <span data-ttu-id="d5a64-168">在 **控制台** 窗口中按 enter 以停止调试并继续演练。</span><span class="sxs-lookup"><span data-stu-id="d5a64-168">Press Enter in the **Console** window to stop debugging and continue the walkthrough.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="d5a64-169">更新实体</span><span class="sxs-lookup"><span data-stu-id="d5a64-169">Updating an Entity</span></span>  

 <span data-ttu-id="d5a64-170">在以下步骤中，您将检索一个 `Customer` 对象并修改其属性之一。</span><span class="sxs-lookup"><span data-stu-id="d5a64-170">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="d5a64-171">更改客户的姓名</span><span class="sxs-lookup"><span data-stu-id="d5a64-171">To change the name of a Customer</span></span>  
  
- <span data-ttu-id="d5a64-172">将下面的代码添加到 `Console.ReadLine();` 上方：</span><span class="sxs-lookup"><span data-stu-id="d5a64-172">Add the following code above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="d5a64-173">删除实体</span><span class="sxs-lookup"><span data-stu-id="d5a64-173">Deleting an Entity</span></span>  

 <span data-ttu-id="d5a64-174">使用同一客户对象，您可以删除第一个订单。</span><span class="sxs-lookup"><span data-stu-id="d5a64-174">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="d5a64-175">下面的代码演示如何切断行与行之间的关系，以及如何从数据库中删除行。</span><span class="sxs-lookup"><span data-stu-id="d5a64-175">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span> <span data-ttu-id="d5a64-176">请将下面的代码添加到 `Console.ReadLine` 前面，以了解如何可以删除对象：</span><span class="sxs-lookup"><span data-stu-id="d5a64-176">Add the following code before `Console.ReadLine` to see how objects can be deleted:</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="d5a64-177">删除行</span><span class="sxs-lookup"><span data-stu-id="d5a64-177">To delete a row</span></span>  
  
- <span data-ttu-id="d5a64-178">将下面的代码添加到 `Console.ReadLine();` 上方紧靠它的位置：</span><span class="sxs-lookup"><span data-stu-id="d5a64-178">Add the following code just above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="d5a64-179">将更改提交到数据库</span><span class="sxs-lookup"><span data-stu-id="d5a64-179">Submitting Changes to the Database</span></span>  

 <span data-ttu-id="d5a64-180">创建、更新和删除对象所需执行的最后一步是将更改实际提交到数据库。</span><span class="sxs-lookup"><span data-stu-id="d5a64-180">The final step required for creating, updating, and deleting objects, is to actually submit the changes to the database.</span></span> <span data-ttu-id="d5a64-181">如不执行这一步，您所做的更改将仅限本地，不会出现在查询结果中。</span><span class="sxs-lookup"><span data-stu-id="d5a64-181">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="d5a64-182">将更改提交到数据库</span><span class="sxs-lookup"><span data-stu-id="d5a64-182">To submit changes to the database</span></span>  
  
1. <span data-ttu-id="d5a64-183">将下面的代码插入到 `Console.ReadLine` 上方紧靠它的位置：</span><span class="sxs-lookup"><span data-stu-id="d5a64-183">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2. <span data-ttu-id="d5a64-184">将下面的代码插入到 `SubmitChanges` 后面，以显示提交更改前后的效果：</span><span class="sxs-lookup"><span data-stu-id="d5a64-184">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3. <span data-ttu-id="d5a64-185">按 F5 调试解决方案。</span><span class="sxs-lookup"><span data-stu-id="d5a64-185">Press F5 to debug the solution.</span></span>  
  
4. <span data-ttu-id="d5a64-186">在 **控制台** 窗口中按 enter，以关闭应用程序。</span><span class="sxs-lookup"><span data-stu-id="d5a64-186">Press Enter in the **Console** window to close the application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5a64-187">通过提交更改添加了新的客户后，您无法再次按原样执行此解决方案。</span><span class="sxs-lookup"><span data-stu-id="d5a64-187">After you have added the new customer by submitting the changes, you cannot execute this solution again as is.</span></span> <span data-ttu-id="d5a64-188">若要再次执行此解决方案，请更改要添加的客户姓名和客户 ID。</span><span class="sxs-lookup"><span data-stu-id="d5a64-188">To execute the solution again, change the name of the customer and customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5a64-189">请参阅</span><span class="sxs-lookup"><span data-stu-id="d5a64-189">See also</span></span>

- [<span data-ttu-id="d5a64-190">通过演练学习</span><span class="sxs-lookup"><span data-stu-id="d5a64-190">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
