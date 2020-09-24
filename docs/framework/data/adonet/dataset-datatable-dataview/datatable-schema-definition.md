---
title: 数据表架构定义
ms.date: 03/30/2017
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
ms.openlocfilehash: 0c14c6012c65039e1e2e7e2d2d8c38c4202b45a7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153243"
---
# <a name="datatable-schema-definition"></a><span data-ttu-id="bfca3-102">数据表架构定义</span><span class="sxs-lookup"><span data-stu-id="bfca3-102">DataTable Schema Definition</span></span>

<span data-ttu-id="bfca3-103">表的架构（即结构）由列和约束表示。</span><span class="sxs-lookup"><span data-stu-id="bfca3-103">The schema, or structure, of a table is represented by columns and constraints.</span></span> <span data-ttu-id="bfca3-104">使用 <xref:System.Data.DataTable> 对象以及 <xref:System.Data.DataColumn> 和 <xref:System.Data.ForeignKeyConstraint> 对象定义 <xref:System.Data.UniqueConstraint> 的架构。</span><span class="sxs-lookup"><span data-stu-id="bfca3-104">You define the schema of a <xref:System.Data.DataTable> using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="bfca3-105">表中的列可以映射到数据源中的列、包含从表达式计算所得的值、自动递增它们的值，或包含主键值。</span><span class="sxs-lookup"><span data-stu-id="bfca3-105">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="bfca3-106">按名称引用表中的列、关系和约束是区分大小写的。</span><span class="sxs-lookup"><span data-stu-id="bfca3-106">References by name to columns, relations, and constraints in a table are case-sensitive.</span></span> <span data-ttu-id="bfca3-107">因此，一个表中可以存在两个或两个以上名称相同（但大小写不同）的列、关系或约束。</span><span class="sxs-lookup"><span data-stu-id="bfca3-107">Two or more columns, relations, or constraints can therefore exist in a table that have the same name, but that differ in case.</span></span> <span data-ttu-id="bfca3-108">例如，您可以具有 **col1** 和 **col1**。</span><span class="sxs-lookup"><span data-stu-id="bfca3-108">For example, you can have **Col1** and **col1**.</span></span> <span data-ttu-id="bfca3-109">在这种情况下，按名称引用某一列就必须完全符合该列名的大小写，否则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="bfca3-109">In such as case, a reference to one of the columns by name must match the case of the column name exactly; otherwise an exception is thrown.</span></span> <span data-ttu-id="bfca3-110">例如，如果表 **myTable** 包含列 **Col1** 和 **col1**，则可以按名称将 **col1** 称为 **列 ["col1"]**，将 **col1** 引用为 mytable 列 **["col1"]**。</span><span class="sxs-lookup"><span data-stu-id="bfca3-110">For example, if the table **myTable** contains the columns **Col1** and **col1**, you would reference **Col1** by name as **myTable.Columns["Col1"]**, and **col1** as **myTable.Columns["col1"]**.</span></span> <span data-ttu-id="bfca3-111">尝试将任一列作为 **myTable 引用。列 ["COL1"]** 将生成异常。</span><span class="sxs-lookup"><span data-stu-id="bfca3-111">Attempting to reference either of the columns as **myTable.Columns["COL1"]** would generate an exception.</span></span>  
  
 <span data-ttu-id="bfca3-112">如果某个特定名称只存在一个列、关系或约束，则不应用区分大小写规则。</span><span class="sxs-lookup"><span data-stu-id="bfca3-112">The case-sensitivity rule does not apply if only one column, relation, or constraint  with a particular name exists.</span></span> <span data-ttu-id="bfca3-113">也就是说，如果表中没有其他的列、关系或约束对象与该特定列、关系或约束对象的名称匹配，您就可以使用任意的大小写来按名称引用该对象，并且不会引发异常。</span><span class="sxs-lookup"><span data-stu-id="bfca3-113">That is, if no other column, relation, or constraint object in the table matches the name of that particular column, relation, or constraint object, you may reference the object by name using any case, and no exception is thrown.</span></span> <span data-ttu-id="bfca3-114">例如，如果表只有 **Col1**，则可以使用 my 来引用它 **。列 ["COL1"]**。</span><span class="sxs-lookup"><span data-stu-id="bfca3-114">For example, if the table has only **Col1**, you can reference it using **my.Columns["COL1"]**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bfca3-115"><xref:System.Data.DataTable.CaseSensitive%2A> **DataTable**的属性不影响此行为。</span><span class="sxs-lookup"><span data-stu-id="bfca3-115">The <xref:System.Data.DataTable.CaseSensitive%2A> property of the **DataTable** does not affect this behavior.</span></span> <span data-ttu-id="bfca3-116">**CaseSensitive**属性应用于表中的数据，并影响排序、搜索、筛选、强制约束等，但不影响对列、关系和约束的引用。</span><span class="sxs-lookup"><span data-stu-id="bfca3-116">The **CaseSensitive** property applies to the data in a table and affects sorting, searching, filtering, enforcing constraints, and so on, but not to references to the columns, relations, and constraints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bfca3-117">本节内容</span><span class="sxs-lookup"><span data-stu-id="bfca3-117">In This Section</span></span>  

 [<span data-ttu-id="bfca3-118">向数据表添加列</span><span class="sxs-lookup"><span data-stu-id="bfca3-118">Adding Columns to a DataTable</span></span>](adding-columns-to-a-datatable.md)  
 <span data-ttu-id="bfca3-119">介绍如何使用 **DataColumn** 对象定义表中的列。</span><span class="sxs-lookup"><span data-stu-id="bfca3-119">Describes how to define the columns of a table using **DataColumn** objects.</span></span>  
  
 [<span data-ttu-id="bfca3-120">创建表达式列</span><span class="sxs-lookup"><span data-stu-id="bfca3-120">Creating Expression Columns</span></span>](creating-expression-columns.md)  
 <span data-ttu-id="bfca3-121">介绍如何使用列的 **Expression** 属性根据行中的其他列中的值计算值。</span><span class="sxs-lookup"><span data-stu-id="bfca3-121">Explains how the **Expression** property of a column can be used to calculate values based on the values from other columns in the row.</span></span>  
  
 [<span data-ttu-id="bfca3-122">创建 AutoIncrement 列</span><span class="sxs-lookup"><span data-stu-id="bfca3-122">Creating AutoIncrement Columns</span></span>](creating-autoincrement-columns.md)  
 <span data-ttu-id="bfca3-123">说明如何将列设置为自动递增数值，以确保每行都有唯一的列值。</span><span class="sxs-lookup"><span data-stu-id="bfca3-123">Describes how a column can be set to automatically increment numerical values to ensure a unique column value per row.</span></span>  
  
 [<span data-ttu-id="bfca3-124">定义主键</span><span class="sxs-lookup"><span data-stu-id="bfca3-124">Defining Primary Keys</span></span>](defining-primary-keys.md)  
 <span data-ttu-id="bfca3-125">描述如何从一个或多个 **DataColumn** 对象中指定表的主键。</span><span class="sxs-lookup"><span data-stu-id="bfca3-125">Describes how to specify the primary key of a table from one or more **DataColumn** objects.</span></span>  
  
 [<span data-ttu-id="bfca3-126">数据表约束</span><span class="sxs-lookup"><span data-stu-id="bfca3-126">DataTable Constraints</span></span>](datatable-constraints.md)  
 <span data-ttu-id="bfca3-127">说明如何为表中的列定义外键和唯一约束。</span><span class="sxs-lookup"><span data-stu-id="bfca3-127">Describes how to define foreign key and unique constraints for columns in a table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfca3-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="bfca3-128">See also</span></span>

- [<span data-ttu-id="bfca3-129">DataTables</span><span class="sxs-lookup"><span data-stu-id="bfca3-129">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="bfca3-130">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="bfca3-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
