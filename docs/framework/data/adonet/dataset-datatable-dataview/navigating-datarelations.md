---
title: 导航 DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: 5eb2ee16712be5ccd5e9aa0af4dde22dcaaeea09
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148381"
---
# <a name="navigating-datarelations"></a><span data-ttu-id="fb00c-102">导航 DataRelation</span><span class="sxs-lookup"><span data-stu-id="fb00c-102">Navigating DataRelations</span></span>

<span data-ttu-id="fb00c-103"><xref:System.Data.DataRelation> 的一项主要功能就是在 <xref:System.Data.DataTable> 中从一个 <xref:System.Data.DataSet> 浏览到另一个。</span><span class="sxs-lookup"><span data-stu-id="fb00c-103">One of the primary functions of a <xref:System.Data.DataRelation> is to allow navigation from one <xref:System.Data.DataTable> to another within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="fb00c-104"><xref:System.Data.DataRow>当给定相关**DataTable**中的单个**DataRow**时，这允许您检索一个**DataTable**中的所有相关对象。</span><span class="sxs-lookup"><span data-stu-id="fb00c-104">This allows you to retrieve all the related <xref:System.Data.DataRow> objects in one **DataTable** when given a single **DataRow** from a related **DataTable**.</span></span> <span data-ttu-id="fb00c-105">例如，在客户表和订单表之间建立 **DataRelation** 后，可以使用 **GetChildRows**检索特定客户行的所有订单行。</span><span class="sxs-lookup"><span data-stu-id="fb00c-105">For example, after establishing a **DataRelation** between a table of customers and a table of orders, you can retrieve all the order rows for a particular customer row using **GetChildRows**.</span></span>  
  
 <span data-ttu-id="fb00c-106">下面的代码示例在**Customers**表和**数据集**的**Orders**表之间创建**DataRelation** ，并返回每个客户的所有订单。</span><span class="sxs-lookup"><span data-stu-id="fb00c-106">The following code example creates a **DataRelation** between the **Customers** table and the **Orders** table of a **DataSet** and returns all the orders for each customer.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 <span data-ttu-id="fb00c-107">下一示例以上例为基础，将四个表关联在一起，并浏览这些关系。</span><span class="sxs-lookup"><span data-stu-id="fb00c-107">The next example builds on the preceding example, relating four tables together and navigating those relationships.</span></span> <span data-ttu-id="fb00c-108">如前面的示例所示， **CustomerID** 将 **Customers** 表与 **Orders** 表相关联。</span><span class="sxs-lookup"><span data-stu-id="fb00c-108">As in the previous example, **CustomerID** relates the **Customers** table to the **Orders** table.</span></span> <span data-ttu-id="fb00c-109">对于 **Customers** 表中的每个客户，将确定 **orders** 表中的所有子行，以便返回特定客户具有的订单数及其 **订单** 值。</span><span class="sxs-lookup"><span data-stu-id="fb00c-109">For each customer in the **Customers** table, all the child rows in the **Orders** table are determined, in order to return the number of orders a particular customer has and their **OrderID** values.</span></span>  
  
 <span data-ttu-id="fb00c-110">展开的示例还将返回 **OrderDetails** 和 **Products** 表中的值。</span><span class="sxs-lookup"><span data-stu-id="fb00c-110">The expanded example also returns the values from the **OrderDetails** and **Products** tables.</span></span> <span data-ttu-id="fb00c-111">**Orders**表与**OrderDetails**表相关，使用 "订单**id** " 来确定对于每个客户订单，订购了哪些产品和数量。</span><span class="sxs-lookup"><span data-stu-id="fb00c-111">The **Orders** table is related to the **OrderDetails** table using **OrderID** to determine, for each customer order, what products and quantities were ordered.</span></span> <span data-ttu-id="fb00c-112">由于**OrderDetails**表只包含已订购产品的**ProductID** ，因此**OrderDetails**与使用**ProductID**的**产品**相关，以便返回产品**名称**。</span><span class="sxs-lookup"><span data-stu-id="fb00c-112">Because the **OrderDetails** table only contains the **ProductID** of an ordered product, **OrderDetails** is related to **Products** using **ProductID** in order to return the **ProductName**.</span></span> <span data-ttu-id="fb00c-113">在此关系中， **Products** 表是父级， **Order Details** 表是子表。</span><span class="sxs-lookup"><span data-stu-id="fb00c-113">In this relation, the **Products** table is the parent and the **Order Details** table is the child.</span></span> <span data-ttu-id="fb00c-114">因此，在循环访问 **OrderDetails** 表时，将调用 **GetParentRow** 来检索相关的 **ProductName** 值。</span><span class="sxs-lookup"><span data-stu-id="fb00c-114">As a result, when iterating through the **OrderDetails** table, **GetParentRow** is called to retrieve the related **ProductName** value.</span></span>  
  
 <span data-ttu-id="fb00c-115">请注意，当为**Customers**和**Orders**表创建**DataRelation**时，没有为**createConstraints**标志指定值 (默认值为**true**) 。</span><span class="sxs-lookup"><span data-stu-id="fb00c-115">Notice that when the **DataRelation** is created for the **Customers** and **Orders** tables, no value is specified for the **createConstraints** flag (the default is **true**).</span></span> <span data-ttu-id="fb00c-116">这假设**Orders**表中的所有行都有一个存在于父**Customers**表中的**CustomerID**值。</span><span class="sxs-lookup"><span data-stu-id="fb00c-116">This assumes that all the rows in the **Orders** table have a **CustomerID** value that exists in the parent **Customers** table.</span></span> <span data-ttu-id="fb00c-117">如果**客户**表中不存在的**Orders**表中存在**CustomerID** ，则 <xref:System.Data.ForeignKeyConstraint> 会导致引发异常。</span><span class="sxs-lookup"><span data-stu-id="fb00c-117">If a **CustomerID** exists in the **Orders** table that does not exist in the **Customers** table, a <xref:System.Data.ForeignKeyConstraint> causes an exception to be thrown.</span></span>  
  
 <span data-ttu-id="fb00c-118">如果子列可能包含父列不包含的值，请在添加**DataRelation**时将**createConstraints**标志设置为**false** 。</span><span class="sxs-lookup"><span data-stu-id="fb00c-118">When the child column might contain values that the parent column does not contain, set the **createConstraints** flag to **false** when adding the **DataRelation**.</span></span> <span data-ttu-id="fb00c-119">在此示例中， **createConstraints**标志在**Orders**表和**OrderDetails**表之间的**DataRelation**设置为**false** 。</span><span class="sxs-lookup"><span data-stu-id="fb00c-119">In the example, the **createConstraints** flag is set to **false** for the **DataRelation** between the **Orders** table and the **OrderDetails** table.</span></span> <span data-ttu-id="fb00c-120">这样，应用程序便可以返回 **OrderDetails** 表中的所有记录，并只返回 **Orders** 表中记录的子集，而无需生成运行时异常。</span><span class="sxs-lookup"><span data-stu-id="fb00c-120">This enables the application to return all the records from the **OrderDetails** table and only a subset of records from the **Orders** table without generating a run-time exception.</span></span> <span data-ttu-id="fb00c-121">该扩展示例生成以下格式的输出。</span><span class="sxs-lookup"><span data-stu-id="fb00c-121">The expanded sample generates output in the following format.</span></span>  
  
```output  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 <span data-ttu-id="fb00c-122">下面的代码示例是一个展开的示例，在该示例中，将返回 **OrderDetails** 表和 **Products** 表中的值，并只返回 **Orders** 表中记录的子集。</span><span class="sxs-lookup"><span data-stu-id="fb00c-122">The following code example is an expanded sample where the values from the **OrderDetails** and **Products** tables are returned, with only a subset of the records in the **Orders** table being returned.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fb00c-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="fb00c-123">See also</span></span>

- [<span data-ttu-id="fb00c-124">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="fb00c-124">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="fb00c-125">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="fb00c-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
