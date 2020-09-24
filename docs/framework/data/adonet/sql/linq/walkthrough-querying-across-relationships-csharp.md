---
title: 演练：跨关系查询 (C#)
ms.date: 03/30/2017
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
ms.openlocfilehash: 9dfe34136f2d0a14a12f72e22a96d1882ddbce49
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164007"
---
# <a name="walkthrough-querying-across-relationships-c"></a><span data-ttu-id="db89d-102">演练：跨关系查询 (C#)</span><span class="sxs-lookup"><span data-stu-id="db89d-102">Walkthrough: Querying Across Relationships (C#)</span></span>

<span data-ttu-id="db89d-103">本演练演示如何使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *关联* 来表示数据库中的外键关系。</span><span class="sxs-lookup"><span data-stu-id="db89d-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="db89d-104">本演练是使用 Visual C# 开发设置编写的。</span><span class="sxs-lookup"><span data-stu-id="db89d-104">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="db89d-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="db89d-105">Prerequisites</span></span>  

 <span data-ttu-id="db89d-106">必须已完成 [演练：简单对象模型和查询 (c # ) ](walkthrough-simple-object-model-and-query-csharp.md)。</span><span class="sxs-lookup"><span data-stu-id="db89d-106">You must have completed [Walkthrough: Simple Object Model and Query (C#)](walkthrough-simple-object-model-and-query-csharp.md).</span></span> <span data-ttu-id="db89d-107">本演练建立在该演练基础之上，包括在 c:\linqtest5 中须存在 northwnd.mdf 文件。</span><span class="sxs-lookup"><span data-stu-id="db89d-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest5.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="db89d-108">概述</span><span class="sxs-lookup"><span data-stu-id="db89d-108">Overview</span></span>  

 <span data-ttu-id="db89d-109">本演练由三项主要任务组成：</span><span class="sxs-lookup"><span data-stu-id="db89d-109">This walkthrough consists of three main tasks:</span></span>  
  
- <span data-ttu-id="db89d-110">添加一个实体类以表示 Northwind 示例数据库中的 Orders 表。</span><span class="sxs-lookup"><span data-stu-id="db89d-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
- <span data-ttu-id="db89d-111">向 `Customer` 类补充一些批注，以增强 `Customer` 和 `Order` 类之间的关系。</span><span class="sxs-lookup"><span data-stu-id="db89d-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
- <span data-ttu-id="db89d-112">创建并运行查询以测试能否通过使用 `Order` 类获取 `Customer` 信息。</span><span class="sxs-lookup"><span data-stu-id="db89d-112">Creating and running a query to test obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="db89d-113">跨表映射关系</span><span class="sxs-lookup"><span data-stu-id="db89d-113">Mapping Relationships Across Tables</span></span>  

 <span data-ttu-id="db89d-114">在 `Customer` 类定义的后面，创建包含如下代码的 `Order` 实体类定义，这些代码表示 `Order.Customer` 作为外键与 `Customer.CustomerID` 相关。</span><span class="sxs-lookup"><span data-stu-id="db89d-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Order.Customer` relates as a foreign key to `Customer.CustomerID`.</span></span>  
  
### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="db89d-115">添加 Order 实体类</span><span class="sxs-lookup"><span data-stu-id="db89d-115">To add the Order entity class</span></span>  
  
- <span data-ttu-id="db89d-116">在 `Customer` 类后面键入或粘贴如下代码：</span><span class="sxs-lookup"><span data-stu-id="db89d-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="db89d-117">对 Customer 类进行批注</span><span class="sxs-lookup"><span data-stu-id="db89d-117">Annotating the Customer Class</span></span>  

 <span data-ttu-id="db89d-118">在此步骤中，您要对 `Customer` 类进行批注，以指示它与 `Order` 类的关系。</span><span class="sxs-lookup"><span data-stu-id="db89d-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="db89d-119">（这种添加批注的操作并非绝对必需的，因为定义任一方向上的关系都足以满足创建链接的需要。</span><span class="sxs-lookup"><span data-stu-id="db89d-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="db89d-120">但添加此批注确实便于您在任一方向上定位对象。）</span><span class="sxs-lookup"><span data-stu-id="db89d-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="db89d-121">对 Customer 类进行批注</span><span class="sxs-lookup"><span data-stu-id="db89d-121">To annotate the Customer class</span></span>  
  
- <span data-ttu-id="db89d-122">将下面的代码键入或粘贴到 `Customer` 类中：</span><span class="sxs-lookup"><span data-stu-id="db89d-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="db89d-123">跨 Customer-Order 关系创建并运行查询</span><span class="sxs-lookup"><span data-stu-id="db89d-123">Creating and Running a Query Across the Customer-Order Relationship</span></span>  

 <span data-ttu-id="db89d-124">现在您可以直接从 `Order` 对象访问 `Customer` 对象，或反过来进行访问。</span><span class="sxs-lookup"><span data-stu-id="db89d-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="db89d-125">客户和订单之间不需要显式 *联接* 。</span><span class="sxs-lookup"><span data-stu-id="db89d-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="db89d-126">使用 Customer 对象访问 Order 对象</span><span class="sxs-lookup"><span data-stu-id="db89d-126">To access Order objects by using Customer objects</span></span>  
  
1. <span data-ttu-id="db89d-127">通过将下面的代码键入或粘贴到 `Main` 方法中修改此方法：</span><span class="sxs-lookup"><span data-stu-id="db89d-127">Modify the `Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2. <span data-ttu-id="db89d-128">按 F5 调试应用程序。</span><span class="sxs-lookup"><span data-stu-id="db89d-128">Press F5 to debug your application.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="db89d-129">你可以通过注释掉 `db.Log = Console.Out;` 来消除控制台窗口中的 SQL 代码。</span><span class="sxs-lookup"><span data-stu-id="db89d-129">You can eliminate the SQL code in the Console window by commenting out `db.Log = Console.Out;`.</span></span>  
  
3. <span data-ttu-id="db89d-130">在控制台窗口中按 Enter，以停止调试。</span><span class="sxs-lookup"><span data-stu-id="db89d-130">Press Enter in the Console window to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="db89d-131">创建数据库的强类型化视图</span><span class="sxs-lookup"><span data-stu-id="db89d-131">Creating a Strongly Typed View of Your Database</span></span>  

 <span data-ttu-id="db89d-132">从数据库的强类型化视图着手要容易得多。</span><span class="sxs-lookup"><span data-stu-id="db89d-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="db89d-133">通过将 <xref:System.Data.Linq.DataContext> 对象强类型化，您无需调用 <xref:System.Data.Linq.DataContext.GetTable%2A>。</span><span class="sxs-lookup"><span data-stu-id="db89d-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="db89d-134">当您使用强类型化的 <xref:System.Data.Linq.DataContext> 对象时，您可以在所有查询中使用强类型化表。</span><span class="sxs-lookup"><span data-stu-id="db89d-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="db89d-135">在以下步骤中，您将创建 `Customers` 作为映射到数据库中的 Customers 表的强类型化表。</span><span class="sxs-lookup"><span data-stu-id="db89d-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="db89d-136">对 DataContext 对象进行强类型化</span><span class="sxs-lookup"><span data-stu-id="db89d-136">To strongly type the DataContext object</span></span>  
  
1. <span data-ttu-id="db89d-137">将下面的代码添加到 `Customer` 类声明的上方。</span><span class="sxs-lookup"><span data-stu-id="db89d-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2. <span data-ttu-id="db89d-138">将 `Main` 方法修改为使用强类型化的 <xref:System.Data.Linq.DataContext>，如下所示：</span><span class="sxs-lookup"><span data-stu-id="db89d-138">Modify the `Main` method to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3. <span data-ttu-id="db89d-139">按 F5 调试应用程序。</span><span class="sxs-lookup"><span data-stu-id="db89d-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="db89d-140">控制台窗口输出如下：</span><span class="sxs-lookup"><span data-stu-id="db89d-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4. <span data-ttu-id="db89d-141">在控制台窗口中按 Enter，以停止调试。</span><span class="sxs-lookup"><span data-stu-id="db89d-141">Press Enter in the console window to stop debugging.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="db89d-142">后续步骤</span><span class="sxs-lookup"><span data-stu-id="db89d-142">Next Steps</span></span>  

 <span data-ttu-id="db89d-143">下一演练 ([演练：操作数据 (c # ) ](walkthrough-manipulating-data-csharp.md)) 演示如何处理数据。</span><span class="sxs-lookup"><span data-stu-id="db89d-143">The next walkthrough ([Walkthrough: Manipulating Data (C#)](walkthrough-manipulating-data-csharp.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="db89d-144">该演练不要求您保存本系列中已经完成的两个演练的结果。</span><span class="sxs-lookup"><span data-stu-id="db89d-144">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db89d-145">请参阅</span><span class="sxs-lookup"><span data-stu-id="db89d-145">See also</span></span>

- [<span data-ttu-id="db89d-146">通过演练学习</span><span class="sxs-lookup"><span data-stu-id="db89d-146">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
