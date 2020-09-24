---
title: 演练：操作数据 (Visual Basic)
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: dbf18273e69ff0977f5d16ff179b8659865ef696
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164046"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a><span data-ttu-id="debee-102">演练：操作数据 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="debee-102">Walkthrough: Manipulating Data (Visual Basic)</span></span>

<span data-ttu-id="debee-103">本演练提供了用于在数据库中添加、修改和删除数据的基本端对端 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 方案。</span><span class="sxs-lookup"><span data-stu-id="debee-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="debee-104">您将使用 Northwind 示例数据库的一个副本来添加一位客户，更改该客户的姓名，然后删除一个订单。</span><span class="sxs-lookup"><span data-stu-id="debee-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="debee-105">本演练是使用 Visual Basic 开发设置编写的。</span><span class="sxs-lookup"><span data-stu-id="debee-105">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="debee-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="debee-106">Prerequisites</span></span>  

 <span data-ttu-id="debee-107">本演练需要如下内容：</span><span class="sxs-lookup"><span data-stu-id="debee-107">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="debee-108">本演练使用专用文件夹（“c:\linqtest2”）来保存文件。</span><span class="sxs-lookup"><span data-stu-id="debee-108">This walkthrough uses a dedicated folder ("c:\linqtest2") to hold files.</span></span> <span data-ttu-id="debee-109">请在开始本演练前创建此文件夹。</span><span class="sxs-lookup"><span data-stu-id="debee-109">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="debee-110">Northwind 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="debee-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="debee-111">如果您的开发计算机上没有此数据库，您可以从 Microsoft 下载网站下载它。</span><span class="sxs-lookup"><span data-stu-id="debee-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="debee-112">有关说明，请参阅 [下载示例数据库](downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="debee-112">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="debee-113">下载此数据库后，请将 northwnd.mdf 文件复制到 c:\linqtest2 文件夹。</span><span class="sxs-lookup"><span data-stu-id="debee-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest2 folder.</span></span>  
  
- <span data-ttu-id="debee-114">从 Northwind 数据库生成的 Visual Basic 代码文件。</span><span class="sxs-lookup"><span data-stu-id="debee-114">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="debee-115">您可以使用对象关系设计器或 SQLMetal 工具生成此文件。</span><span class="sxs-lookup"><span data-stu-id="debee-115">You can generate this file by using either the Object Relational Designer or the SQLMetal tool.</span></span> <span data-ttu-id="debee-116">本演练是通过使用 SQLMetal 工具以及如下命令行编写的：</span><span class="sxs-lookup"><span data-stu-id="debee-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="debee-117">**sqlmetal/code： "c:\linqtest2\northwind.vb"/language： vb "C:\linqtest2\northwnd.mdf"/pluralize**</span><span class="sxs-lookup"><span data-stu-id="debee-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="debee-118">有关详细信息，请参阅 [SqlMetal.exe（代码生成工具）](../../../../tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="debee-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="debee-119">概述</span><span class="sxs-lookup"><span data-stu-id="debee-119">Overview</span></span>  

 <span data-ttu-id="debee-120">本演练由六项主要任务组成：</span><span class="sxs-lookup"><span data-stu-id="debee-120">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="debee-121">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]在 Visual Studio 中创建解决方案。</span><span class="sxs-lookup"><span data-stu-id="debee-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="debee-122">向项目添加数据库代码文件。</span><span class="sxs-lookup"><span data-stu-id="debee-122">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="debee-123">创建新的客户对象。</span><span class="sxs-lookup"><span data-stu-id="debee-123">Creating a new customer object.</span></span>  
  
- <span data-ttu-id="debee-124">修改客户的联系人姓名。</span><span class="sxs-lookup"><span data-stu-id="debee-124">Modifying the contact name of a customer.</span></span>  
  
- <span data-ttu-id="debee-125">删除订单。</span><span class="sxs-lookup"><span data-stu-id="debee-125">Deleting an order.</span></span>  
  
- <span data-ttu-id="debee-126">将这些更改提交至 Northwind 数据库。</span><span class="sxs-lookup"><span data-stu-id="debee-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="debee-127">创建 LINQ to SQL 解决方案</span><span class="sxs-lookup"><span data-stu-id="debee-127">Creating a LINQ to SQL Solution</span></span>  

 <span data-ttu-id="debee-128">在第一个任务中，您将创建一个 Visual Studio 解决方案，其中包含生成和运行项目所必需的引用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="debee-128">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="debee-129">创建 LINQ to SQL 解决方案</span><span class="sxs-lookup"><span data-stu-id="debee-129">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="debee-130">在 Visual Studio 的 " **文件** " 菜单上，单击 " **新建项目**"。</span><span class="sxs-lookup"><span data-stu-id="debee-130">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="debee-131">在 "**新建项目**" 对话框的 "**项目类型**" 窗格中，单击 " **Visual Basic**"。</span><span class="sxs-lookup"><span data-stu-id="debee-131">In the **Project types** pane in the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3. <span data-ttu-id="debee-132">在“模板”窗格中，单击“控制台应用程序”。</span><span class="sxs-lookup"><span data-stu-id="debee-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="debee-133">在 " **名称** " 框中，键入 **LinqDataManipulationApp**。</span><span class="sxs-lookup"><span data-stu-id="debee-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5. <span data-ttu-id="debee-134">单击“确定”。 </span><span class="sxs-lookup"><span data-stu-id="debee-134">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="debee-135">添加 LINQ 引用和指令</span><span class="sxs-lookup"><span data-stu-id="debee-135">Adding LINQ References and Directives</span></span>  

 <span data-ttu-id="debee-136">本演练用到默认情况下您的项目中可能未安装的程序集。</span><span class="sxs-lookup"><span data-stu-id="debee-136">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="debee-137">如果 `System.Data.Linq` 未在你的项目中列为引用 (请单击 "显示**解决方案资源管理器**中的**所有文件**"，然后展开 "**引用**" 节点) "添加"，如以下步骤中所述。</span><span class="sxs-lookup"><span data-stu-id="debee-137">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="debee-138">添加 System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="debee-138">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="debee-139">在 **解决方案资源管理器**中，右键单击 " **引用**"，然后单击 " **添加引用**"。</span><span class="sxs-lookup"><span data-stu-id="debee-139">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="debee-140">在 " **添加引用** " 对话框中，单击 " **.net**"，单击 "system.web" 程序集，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="debee-140">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="debee-141">此程序集即被添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="debee-141">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="debee-142">在代码编辑器中，将以下指令添加到 **Module1**上方：</span><span class="sxs-lookup"><span data-stu-id="debee-142">In the code editor, add the following directives above **Module1**:</span></span>  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="debee-143">将 Northwind 代码文件添加到项目</span><span class="sxs-lookup"><span data-stu-id="debee-143">Adding the Northwind Code File to the Project</span></span>  

 <span data-ttu-id="debee-144">以下这些步骤假定你已使用 SQLMetal 工具从 Northwind 示例数据库生成代码文件。</span><span class="sxs-lookup"><span data-stu-id="debee-144">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="debee-145">有关更多信息，请参见本演练前面部分的“先决条件”一节。</span><span class="sxs-lookup"><span data-stu-id="debee-145">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="debee-146">将 northwind 代码文件添加到项目</span><span class="sxs-lookup"><span data-stu-id="debee-146">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="debee-147">在“项目”\*\*\*\* 菜单上，单击“添加现有项”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="debee-147">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="debee-148">在 " **添加现有项** " 对话框中，导航到 "c:\linqtest2\northwind.vb"，然后单击 " **添加**"。</span><span class="sxs-lookup"><span data-stu-id="debee-148">In the **Add Existing Item** dialog box, navigate to c:\linqtest2\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="debee-149">northwind.vb 文件即被添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="debee-149">The northwind.vb file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="debee-150">设置数据库连接</span><span class="sxs-lookup"><span data-stu-id="debee-150">Setting Up the Database Connection</span></span>  

 <span data-ttu-id="debee-151">首先，测试与数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="debee-151">First, test your connection to the database.</span></span> <span data-ttu-id="debee-152">特别要注意，数据库的名称 Northwnd 不含 i 字符。</span><span class="sxs-lookup"><span data-stu-id="debee-152">Note especially that the name of the database, Northwnd, has no i character.</span></span> <span data-ttu-id="debee-153">如果在后面的步骤中产生错误，请检查 northwind.vb 文件以确定 Northwind 分部类的拼写是否正确。</span><span class="sxs-lookup"><span data-stu-id="debee-153">If you generate errors in the next steps, review the northwind.vb file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="debee-154">设置并测试数据库连接</span><span class="sxs-lookup"><span data-stu-id="debee-154">To set up and test the database connection</span></span>  
  
1. <span data-ttu-id="debee-155">将下面的代码键入或粘贴到 `Sub Main` 中：</span><span class="sxs-lookup"><span data-stu-id="debee-155">Type or paste the following code into `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2. <span data-ttu-id="debee-156">按 F5 在此点测试应用程序。</span><span class="sxs-lookup"><span data-stu-id="debee-156">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="debee-157">此时将打开一个 **控制台** 窗口。</span><span class="sxs-lookup"><span data-stu-id="debee-157">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="debee-158">在**控制台**窗口中按 enter，或在 Visual Studio 的 "**调试**" 菜单上单击 "**停止调试**"，以关闭应用程序。</span><span class="sxs-lookup"><span data-stu-id="debee-158">Close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="debee-159">创建新实体</span><span class="sxs-lookup"><span data-stu-id="debee-159">Creating a New Entity</span></span>  

 <span data-ttu-id="debee-160">创建新实体很简单。</span><span class="sxs-lookup"><span data-stu-id="debee-160">Creating a new entity is straightforward.</span></span> <span data-ttu-id="debee-161">可以使用 `Customer` 关键字创建对象（如 `New`）。</span><span class="sxs-lookup"><span data-stu-id="debee-161">You can create objects (such as `Customer`) by using the `New` keyword.</span></span>  
  
 <span data-ttu-id="debee-162">在本节及后续各节中，您将只对本地缓存进行更改。</span><span class="sxs-lookup"><span data-stu-id="debee-162">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="debee-163">如果您不调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A>，则不会向数据库发送任何更改，一直到本演练结束都是如此。</span><span class="sxs-lookup"><span data-stu-id="debee-163">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="debee-164">添加新的 Customer 实体对象</span><span class="sxs-lookup"><span data-stu-id="debee-164">To add a new Customer entity object</span></span>  
  
1. <span data-ttu-id="debee-165">通过在 `Customer` 中的 `Console.ReadLine` 前添加如下代码，创建一个新的 `Sub Main`：</span><span class="sxs-lookup"><span data-stu-id="debee-165">Create a new `Customer` by adding the following code before `Console.ReadLine` in `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2. <span data-ttu-id="debee-166">按 F5 调试解决方案。</span><span class="sxs-lookup"><span data-stu-id="debee-166">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="debee-167">控制台窗口中显示的结果如下：</span><span class="sxs-lookup"><span data-stu-id="debee-167">The results that are shown in the console window are as follows:</span></span>  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     <span data-ttu-id="debee-168">请注意，新行不会出现在结果中，</span><span class="sxs-lookup"><span data-stu-id="debee-168">Note that the new row does not appear in the results.</span></span> <span data-ttu-id="debee-169">因为新数据尚未提交到数据库。</span><span class="sxs-lookup"><span data-stu-id="debee-169">The new data has not yet been submitted to the database.</span></span>  
  
3. <span data-ttu-id="debee-170">在 **控制台** 窗口中按 enter 以停止调试。</span><span class="sxs-lookup"><span data-stu-id="debee-170">Press Enter in the **Console** window to stop debugging.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="debee-171">更新实体</span><span class="sxs-lookup"><span data-stu-id="debee-171">Updating an Entity</span></span>  

 <span data-ttu-id="debee-172">在以下步骤中，您将检索一个 `Customer` 对象并修改其属性之一。</span><span class="sxs-lookup"><span data-stu-id="debee-172">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="debee-173">更改客户的姓名</span><span class="sxs-lookup"><span data-stu-id="debee-173">To change the name of a Customer</span></span>  
  
- <span data-ttu-id="debee-174">将下面的代码添加到 `Console.ReadLine()` 上方：</span><span class="sxs-lookup"><span data-stu-id="debee-174">Add the following code above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="debee-175">删除实体</span><span class="sxs-lookup"><span data-stu-id="debee-175">Deleting an Entity</span></span>  

 <span data-ttu-id="debee-176">使用同一客户对象，您可以删除第一个订单。</span><span class="sxs-lookup"><span data-stu-id="debee-176">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="debee-177">下面的代码演示如何切断行与行之间的关系，以及如何从数据库中删除行。</span><span class="sxs-lookup"><span data-stu-id="debee-177">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="debee-178">删除行</span><span class="sxs-lookup"><span data-stu-id="debee-178">To delete a row</span></span>  
  
- <span data-ttu-id="debee-179">将下面的代码添加到 `Console.ReadLine()` 上方紧靠它的位置：</span><span class="sxs-lookup"><span data-stu-id="debee-179">Add the following code just above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="debee-180">将更改提交到数据库</span><span class="sxs-lookup"><span data-stu-id="debee-180">Submitting Changes to the Database</span></span>  

 <span data-ttu-id="debee-181">创建、更新和删除对象所需执行的最后一步是将真正将更改提交到数据库。</span><span class="sxs-lookup"><span data-stu-id="debee-181">The final step required for creating, updating, and deleting objects is to actually submit the changes to the database.</span></span> <span data-ttu-id="debee-182">如不执行这一步，您所做的更改将仅限本地，不会出现在查询结果中。</span><span class="sxs-lookup"><span data-stu-id="debee-182">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="debee-183">将更改提交到数据库</span><span class="sxs-lookup"><span data-stu-id="debee-183">To submit changes to the database</span></span>  
  
1. <span data-ttu-id="debee-184">将下面的代码插入到 `Console.ReadLine` 上方紧靠它的位置：</span><span class="sxs-lookup"><span data-stu-id="debee-184">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2. <span data-ttu-id="debee-185">将下面的代码插入到 `SubmitChanges` 后面，以显示提交更改前后的效果：</span><span class="sxs-lookup"><span data-stu-id="debee-185">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3. <span data-ttu-id="debee-186">按 F5 调试解决方案。</span><span class="sxs-lookup"><span data-stu-id="debee-186">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="debee-187">控制台窗口显示如下：</span><span class="sxs-lookup"><span data-stu-id="debee-187">The console window appears as follows:</span></span>  
  
    ```console
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4. <span data-ttu-id="debee-188">在 **控制台** 窗口中按 enter 以停止调试。</span><span class="sxs-lookup"><span data-stu-id="debee-188">Press Enter in the **Console** window to stop debugging.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="debee-189">通过提交更改添加了新的客户后，您无法再次按原样执行此解决方案，因为您无法再次按原样添加相同的客户。</span><span class="sxs-lookup"><span data-stu-id="debee-189">After you have added the new customer by submitting the changes, you cannot execute this solution again as is, because you cannot add the same customer again as is.</span></span> <span data-ttu-id="debee-190">若要再次执行此解决方案，请更改要添加的客户 ID 值。</span><span class="sxs-lookup"><span data-stu-id="debee-190">To execute the solution again, change the value of the customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="debee-191">请参阅</span><span class="sxs-lookup"><span data-stu-id="debee-191">See also</span></span>

- [<span data-ttu-id="debee-192">通过演练学习</span><span class="sxs-lookup"><span data-stu-id="debee-192">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
