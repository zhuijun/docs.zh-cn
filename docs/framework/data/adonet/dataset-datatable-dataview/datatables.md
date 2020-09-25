---
title: DataTables
description: 了解一个 ADO.NET DataTable，它代表中的一个内存中关系数据表。基于网络的应用程序所在位置。
ms.date: 03/30/2017
ms.assetid: 52ff0e32-3e5a-41de-9a3b-7b04ea52b83e
ms.openlocfilehash: d501096b4abe94653acdc5249c120abff94534d1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202300"
---
# <a name="datatables"></a><span data-ttu-id="08b3e-103">DataTables</span><span class="sxs-lookup"><span data-stu-id="08b3e-103">DataTables</span></span>

<span data-ttu-id="08b3e-104"><xref:System.Data.DataSet> 由表、关系和约束的集合组成。</span><span class="sxs-lookup"><span data-stu-id="08b3e-104">A <xref:System.Data.DataSet> is made up of a collection of tables, relationships, and constraints.</span></span> <span data-ttu-id="08b3e-105">在 ADO.NET 中， <xref:System.Data.DataTable> 对象用于表示 **数据集中**的表。</span><span class="sxs-lookup"><span data-stu-id="08b3e-105">In ADO.NET, <xref:System.Data.DataTable> objects are used to represent the tables in a **DataSet**.</span></span> <span data-ttu-id="08b3e-106">**DataTable**表示内存中关系数据的一个表;数据是的本地数据。它所在的基于网络的应用程序，但可以使用**DataAdapter**从数据源（例如 Microsoft SQL Server）进行填充。有关详细信息，请参阅[从 DataAdapter 填充数据集](../populating-a-dataset-from-a-dataadapter.md)。</span><span class="sxs-lookup"><span data-stu-id="08b3e-106">A **DataTable** represents one table of in-memory relational data; the data is local to the .NET-based application in which it resides, but can be populated from a data source such as Microsoft SQL Server using a **DataAdapter** For more information, see [Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md).</span></span>  
  
 <span data-ttu-id="08b3e-107">**DataTable**类是 .NET Framework 类库中的**system.object**命名空间的成员。</span><span class="sxs-lookup"><span data-stu-id="08b3e-107">The **DataTable** class is a member of the **System.Data** namespace within the .NET Framework class library.</span></span> <span data-ttu-id="08b3e-108">您可以独立创建和使用 **datatable** ，或将其作为 **数据集**的成员，也可以将 **datatable** 对象与其他 .NET Framework 对象结合使用，其中包括 <xref:System.Data.DataView> 。</span><span class="sxs-lookup"><span data-stu-id="08b3e-108">You can create and use a **DataTable** independently or as a member of a **DataSet**, and **DataTable** objects can also be used in conjunction with other .NET Framework objects, including the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="08b3e-109">通过**dataset**对象的**Tables**属性访问**数据集中**的表的集合。</span><span class="sxs-lookup"><span data-stu-id="08b3e-109">You access the collection of tables in a **DataSet** through the **Tables** property of the **DataSet** object.</span></span>  
  
 <span data-ttu-id="08b3e-110">表的架构或结构由列和约束表示。</span><span class="sxs-lookup"><span data-stu-id="08b3e-110">The schema, or structure of a table is represented by columns and constraints.</span></span> <span data-ttu-id="08b3e-111">使用对象以及和对象定义 **DataTable** 的架构 <xref:System.Data.DataColumn> <xref:System.Data.ForeignKeyConstraint> <xref:System.Data.UniqueConstraint> 。</span><span class="sxs-lookup"><span data-stu-id="08b3e-111">You define the schema of a **DataTable** using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="08b3e-112">表中的列可以映射到数据源中的列、包含从表达式计算所得的值、自动递增它们的值，或包含主键值。</span><span class="sxs-lookup"><span data-stu-id="08b3e-112">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="08b3e-113">除了架构以外， **DataTable** 还必须有行来包含和排序数据。</span><span class="sxs-lookup"><span data-stu-id="08b3e-113">In addition to a schema, a **DataTable** must also have rows to contain and order data.</span></span> <span data-ttu-id="08b3e-114"><xref:System.Data.DataRow> 类表示表中包含的实际数据。</span><span class="sxs-lookup"><span data-stu-id="08b3e-114">The <xref:System.Data.DataRow> class represents the actual data contained in a table.</span></span> <span data-ttu-id="08b3e-115">使用 **DataRow** 及其属性和方法可以检索、计算和处理表中的数据。</span><span class="sxs-lookup"><span data-stu-id="08b3e-115">You use the **DataRow** and its properties and methods to retrieve, evaluate, and manipulate the data in a table.</span></span> <span data-ttu-id="08b3e-116">访问和更改行中的数据时， **DataRow** 对象将同时维护其当前状态和原始状态。</span><span class="sxs-lookup"><span data-stu-id="08b3e-116">As you access and change the data within a row, the **DataRow** object maintains both its current and original state.</span></span>  
  
 <span data-ttu-id="08b3e-117">您可以使用表中的一个或多个相关的列来创建表与表之间的父子关系。</span><span class="sxs-lookup"><span data-stu-id="08b3e-117">You can create parent-child relationships between tables using one or more related columns in the tables.</span></span> <span data-ttu-id="08b3e-118">使用创建 **DataTable** 对象之间的关系 <xref:System.Data.DataRelation> 。</span><span class="sxs-lookup"><span data-stu-id="08b3e-118">You create a relationship between **DataTable** objects using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="08b3e-119">然后，可以使用**DataRelation**对象返回特定行的相关子行或父行。</span><span class="sxs-lookup"><span data-stu-id="08b3e-119">**DataRelation** objects can then be used to return the related child or parent rows of a particular row.</span></span> <span data-ttu-id="08b3e-120">有关详细信息，请参阅 [添加 datarelation](adding-datarelations.md)。</span><span class="sxs-lookup"><span data-stu-id="08b3e-120">For more information, see [Adding DataRelations](adding-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="08b3e-121">本节内容</span><span class="sxs-lookup"><span data-stu-id="08b3e-121">In This Section</span></span>  

 [<span data-ttu-id="08b3e-122">创建数据表</span><span class="sxs-lookup"><span data-stu-id="08b3e-122">Creating a DataTable</span></span>](creating-a-datatable.md)  
 <span data-ttu-id="08b3e-123">说明如何创建 **DataTable** 并将其添加到 **数据集**。</span><span class="sxs-lookup"><span data-stu-id="08b3e-123">Explains how to create a **DataTable** and add it to a **DataSet**.</span></span>  
  
 [<span data-ttu-id="08b3e-124">数据表架构定义</span><span class="sxs-lookup"><span data-stu-id="08b3e-124">DataTable Schema Definition</span></span>](datatable-schema-definition.md)  
 <span data-ttu-id="08b3e-125">提供有关创建和使用 **DataColumn** 对象和约束的信息。</span><span class="sxs-lookup"><span data-stu-id="08b3e-125">Provides information about creating and using **DataColumn** objects and constraints.</span></span>  
  
 [<span data-ttu-id="08b3e-126">操作数据表中的数据</span><span class="sxs-lookup"><span data-stu-id="08b3e-126">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)  
 <span data-ttu-id="08b3e-127">说明如何添加、修改和删除表中的数据。</span><span class="sxs-lookup"><span data-stu-id="08b3e-127">Explains how to add, modify, and delete data in a table.</span></span> <span data-ttu-id="08b3e-128">说明如何使用 **DataTable** 事件来检查对表中数据的更改。</span><span class="sxs-lookup"><span data-stu-id="08b3e-128">Explains how to use **DataTable** events to examine changes to data in the table.</span></span>  
  
 [<span data-ttu-id="08b3e-129">处理数据表事件</span><span class="sxs-lookup"><span data-stu-id="08b3e-129">Handling DataTable Events</span></span>](handling-datatable-events.md)  
 <span data-ttu-id="08b3e-130">提供可用于 **DataTable**的事件的相关信息，包括修改列值和添加或删除行时的事件。</span><span class="sxs-lookup"><span data-stu-id="08b3e-130">Provides information about the events available for use with a **DataTable**, including events when column values are modified and rows are added or deleted.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="08b3e-131">相关章节</span><span class="sxs-lookup"><span data-stu-id="08b3e-131">Related Sections</span></span>  

 [<span data-ttu-id="08b3e-132">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="08b3e-132">ADO.NET</span></span>](../index.md)  
 <span data-ttu-id="08b3e-133">描述 ADO.NET 结构和组件，并说明如何用来访问现有的数据源和管理应用程序数据。</span><span class="sxs-lookup"><span data-stu-id="08b3e-133">Describes the ADO.NET architecture and components, and how to use them to access existing data sources and manage application data.</span></span>  
  
 [<span data-ttu-id="08b3e-134">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="08b3e-134">DataSets, DataTables, and DataViews</span></span>](index.md)  
 <span data-ttu-id="08b3e-135">提供有关 ADO.NET **数据集** 的信息，包括如何创建表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="08b3e-135">Provides information about the ADO.NET **DataSet** including how to create relationships between tables.</span></span>  
  
 <xref:System.Data.Constraint>  
 <span data-ttu-id="08b3e-136">提供有关 **约束** 对象的参考信息。</span><span class="sxs-lookup"><span data-stu-id="08b3e-136">Provides reference information about the **Constraint** object.</span></span>  
  
 <xref:System.Data.DataColumn>  
 <span data-ttu-id="08b3e-137">提供有关 **DataColumn** 对象的参考信息。</span><span class="sxs-lookup"><span data-stu-id="08b3e-137">Provides reference information about the **DataColumn** object.</span></span>  
  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="08b3e-138">提供有关 **DataSet** 对象的参考信息。</span><span class="sxs-lookup"><span data-stu-id="08b3e-138">Provides reference information about the **DataSet** object.</span></span>  
  
 <xref:System.Data.DataTable>  
 <span data-ttu-id="08b3e-139">提供有关 **DataTable** 对象的参考信息。</span><span class="sxs-lookup"><span data-stu-id="08b3e-139">Provides reference information about the **DataTable** object.</span></span>  
  
 [<span data-ttu-id="08b3e-140">类库概述</span><span class="sxs-lookup"><span data-stu-id="08b3e-140">Class Library Overview</span></span>](../../../../standard/class-library-overview.md)  
 <span data-ttu-id="08b3e-141">提供 .NET Framework 类库的概述，包括 **System** 命名空间及其第二级命名空间、 **system.web**。</span><span class="sxs-lookup"><span data-stu-id="08b3e-141">Provides an overview of the .NET Framework class library, including the **System** namespace as well as its second-level namespace, **System.Data**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08b3e-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="08b3e-142">See also</span></span>

- [<span data-ttu-id="08b3e-143">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="08b3e-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
