---
title: 如何：以特定类型返回 LINQ 查询结果
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: c8ed792bf3ffefd903d60522f621958e44546d32
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404947"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a><span data-ttu-id="5501a-102">如何：以特定类型返回 LINQ 查询结果 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5501a-102">How to: Return a LINQ Query Result as a Specific Type (Visual Basic)</span></span>
<span data-ttu-id="5501a-103">使用语言集成查询（LINQ），可以轻松地访问数据库信息和执行查询。</span><span class="sxs-lookup"><span data-stu-id="5501a-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span> <span data-ttu-id="5501a-104">默认情况下，LINQ 查询将对象列表作为匿名类型返回。</span><span class="sxs-lookup"><span data-stu-id="5501a-104">By default, LINQ queries return a list of objects as an anonymous type.</span></span> <span data-ttu-id="5501a-105">您还可以通过使用子句指定查询返回特定类型的列表 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="5501a-105">You can also specify that a query return a list of a specific type by using the `Select` clause.</span></span>  
  
 <span data-ttu-id="5501a-106">下面的示例演示如何创建一个新的应用程序，用于对 SQL Server 数据库执行查询并将结果投影为特定的命名类型。</span><span class="sxs-lookup"><span data-stu-id="5501a-106">The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type.</span></span> <span data-ttu-id="5501a-107">有关详细信息，请参阅[匿名类型](../objects-and-classes/anonymous-types.md)和[Select 子句](../../../language-reference/queries/select-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="5501a-107">For more information, see [Anonymous Types](../objects-and-classes/anonymous-types.md) and [Select Clause](../../../language-reference/queries/select-clause.md).</span></span>  
  
 <span data-ttu-id="5501a-108">本主题中的示例使用 Northwind 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="5501a-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="5501a-109">如果你的开发计算机上没有此数据库，可以从 Microsoft 下载中心进行下载。</span><span class="sxs-lookup"><span data-stu-id="5501a-109">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="5501a-110">有关说明，请参阅[下载示例数据库](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="5501a-110">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="5501a-111">创建与数据库的连接</span><span class="sxs-lookup"><span data-stu-id="5501a-111">To create a connection to a database</span></span>  
  
1. <span data-ttu-id="5501a-112">在 Visual Studio 中， **Server Explorer** / **Database Explorer**单击**Server Explorer** / "**视图**" 菜单上的 "服务器资源管理器"**数据库资源管理器**打开服务器资源管理器数据库资源管理器。</span><span class="sxs-lookup"><span data-stu-id="5501a-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2. <span data-ttu-id="5501a-113">右键单击**服务器资源管理器**数据库资源管理器中的 "**数据连接**" / **Database Explorer** ，然后单击 "**添加连接**"。</span><span class="sxs-lookup"><span data-stu-id="5501a-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3. <span data-ttu-id="5501a-114">指定与 Northwind 示例数据库的有效连接。</span><span class="sxs-lookup"><span data-stu-id="5501a-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="5501a-115">添加包含 LINQ to SQL 文件的项目</span><span class="sxs-lookup"><span data-stu-id="5501a-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1. <span data-ttu-id="5501a-116">在 Visual Studio 的 "**文件**" 菜单上，指向 "**新建**"，然后单击 "**项目**"。</span><span class="sxs-lookup"><span data-stu-id="5501a-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="5501a-117">选择 Visual Basic **Windows 窗体应用程序**作为项目类型。</span><span class="sxs-lookup"><span data-stu-id="5501a-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2. <span data-ttu-id="5501a-118">在 **“项目”** 菜单上，单击 **“添加新项”**。</span><span class="sxs-lookup"><span data-stu-id="5501a-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="5501a-119">选择 " **LINQ to SQL 类**" 项模板。</span><span class="sxs-lookup"><span data-stu-id="5501a-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3. <span data-ttu-id="5501a-120">命名文件 `northwind.dbml`。</span><span class="sxs-lookup"><span data-stu-id="5501a-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="5501a-121">单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="5501a-121">Click **Add**.</span></span> <span data-ttu-id="5501a-122">为 northwind 文件打开对象关系设计器（O/R 设计器）。</span><span class="sxs-lookup"><span data-stu-id="5501a-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="5501a-123">添加要查询到 O/R 设计器的表</span><span class="sxs-lookup"><span data-stu-id="5501a-123">To add tables to query to the O/R Designer</span></span>  
  
1. <span data-ttu-id="5501a-124">在**服务器资源管理器** / **数据库资源管理器**中，展开与 Northwind 数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="5501a-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="5501a-125">展开 **“表”** 文件夹。</span><span class="sxs-lookup"><span data-stu-id="5501a-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="5501a-126">如果关闭了 O/R 设计器，则可以通过双击先前添加的 northwind 文件来重新打开它。</span><span class="sxs-lookup"><span data-stu-id="5501a-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2. <span data-ttu-id="5501a-127">单击 "Customers" 表，并将其拖到设计器的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="5501a-127">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="5501a-128">设计器将为您的项目创建一个新 `Customer` 的对象。</span><span class="sxs-lookup"><span data-stu-id="5501a-128">The designer creates a new `Customer` object for your project.</span></span> <span data-ttu-id="5501a-129">可以将查询结果投影为 `Customer` 类型或创建的类型。</span><span class="sxs-lookup"><span data-stu-id="5501a-129">You can project a query result as the `Customer` type or as a type that you create.</span></span> <span data-ttu-id="5501a-130">此示例将在后面的过程中创建新类型，并将查询结果投影为该类型。</span><span class="sxs-lookup"><span data-stu-id="5501a-130">This sample will create a new type in a later procedure and project a query result as that type.</span></span>  
  
3. <span data-ttu-id="5501a-131">保存更改并关闭设计器。</span><span class="sxs-lookup"><span data-stu-id="5501a-131">Save your changes and close the designer.</span></span>  
  
4. <span data-ttu-id="5501a-132">保存你的项目。</span><span class="sxs-lookup"><span data-stu-id="5501a-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="5501a-133">添加代码以查询数据库并显示结果</span><span class="sxs-lookup"><span data-stu-id="5501a-133">To add code to query the database and display the results</span></span>  
  
1. <span data-ttu-id="5501a-134">从 "**工具箱**" 中，将 <xref:System.Windows.Forms.DataGridView> 控件拖动到项目的默认 Windows 窗体 "Form1"。</span><span class="sxs-lookup"><span data-stu-id="5501a-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2. <span data-ttu-id="5501a-135">双击 "Form1" 修改 Form1 类。</span><span class="sxs-lookup"><span data-stu-id="5501a-135">Double-click Form1 to modify the Form1 class.</span></span>  
  
3. <span data-ttu-id="5501a-136">在 `End Class` Form1 类的语句后面，添加以下代码以创建一个 `CustomerInfo` 类型以保存此示例的查询结果。</span><span class="sxs-lookup"><span data-stu-id="5501a-136">After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4. <span data-ttu-id="5501a-137">在将表添加到 O/R 设计器后，设计器会将 <xref:System.Data.Linq.DataContext> 对象添加到项目。</span><span class="sxs-lookup"><span data-stu-id="5501a-137">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="5501a-138">此对象包含访问这些表所需的代码，以及访问每个表的单个对象和集合的代码。</span><span class="sxs-lookup"><span data-stu-id="5501a-138">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="5501a-139"><xref:System.Data.Linq.DataContext>项目的对象根据 .dbml 文件的名称进行命名。</span><span class="sxs-lookup"><span data-stu-id="5501a-139">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="5501a-140">对于此项目，该 <xref:System.Data.Linq.DataContext> 对象的名称为 `northwindDataContext` 。</span><span class="sxs-lookup"><span data-stu-id="5501a-140">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="5501a-141">您可以在代码中创建的一个实例 <xref:System.Data.Linq.DataContext> ，并查询由 O/R 设计器指定的表。</span><span class="sxs-lookup"><span data-stu-id="5501a-141">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="5501a-142">在 `Load` Form1 类的事件中，添加以下代码以查询作为数据上下文的属性公开的表。</span><span class="sxs-lookup"><span data-stu-id="5501a-142">In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="5501a-143">`Select`查询的子句将 `CustomerInfo` 为查询结果的每一项创建一个新类型，而不是匿名类型。</span><span class="sxs-lookup"><span data-stu-id="5501a-143">The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5. <span data-ttu-id="5501a-144">按 F5 运行项目并查看结果。</span><span class="sxs-lookup"><span data-stu-id="5501a-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5501a-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5501a-145">See also</span></span>

- [<span data-ttu-id="5501a-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="5501a-146">LINQ</span></span>](index.md)
- [<span data-ttu-id="5501a-147">查询</span><span class="sxs-lookup"><span data-stu-id="5501a-147">Queries</span></span>](../../../language-reference/queries/index.md)
- [<span data-ttu-id="5501a-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5501a-148">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="5501a-149">DataContext 方法（O/R 设计器）</span><span class="sxs-lookup"><span data-stu-id="5501a-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
