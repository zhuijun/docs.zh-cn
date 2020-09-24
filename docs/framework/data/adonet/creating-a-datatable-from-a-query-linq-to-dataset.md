---
title: 从查询创建数据表 (LINQ to DataSet)
description: 了解如何使用 CopyToDataTable 方法获取查询的结果，并将数据复制到 DataTable，然后可以将这些数据用于数据绑定。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b97afeb-03f8-41e2-8eb3-58aff65f7d18
ms.openlocfilehash: 064688f173e375481373e9a33d66c64666e1583f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148356"
---
# <a name="creating-a-datatable-from-a-query-linq-to-dataset"></a><span data-ttu-id="90a65-103">从查询创建数据表 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="90a65-103">Creating a DataTable From a Query (LINQ to DataSet)</span></span>

<span data-ttu-id="90a65-104">数据绑定是 <xref:System.Data.DataTable> 对象的一种常用形式。</span><span class="sxs-lookup"><span data-stu-id="90a65-104">Data binding is a common use of <xref:System.Data.DataTable> object.</span></span> <span data-ttu-id="90a65-105"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法接收查询结果并将数据复制到 <xref:System.Data.DataTable> 中，后者随后会使用该数据进行数据绑定。</span><span class="sxs-lookup"><span data-stu-id="90a65-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="90a65-106">在执行数据操作后，新的 <xref:System.Data.DataTable> 将合并回源 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="90a65-106">When the data operations have been performed, the new <xref:System.Data.DataTable> is merged back into the source <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="90a65-107"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法使用下面的过程来通过查询创建 <xref:System.Data.DataTable>：</span><span class="sxs-lookup"><span data-stu-id="90a65-107">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method uses the following process to create a <xref:System.Data.DataTable> from a query:</span></span>  
  
1. <span data-ttu-id="90a65-108"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法克隆源表中的 <xref:System.Data.DataTable>（实现 <xref:System.Data.DataTable> 接口的 <xref:System.Linq.IQueryable%601> 对象）。</span><span class="sxs-lookup"><span data-stu-id="90a65-108">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method clones a <xref:System.Data.DataTable> from the source table (a <xref:System.Data.DataTable> object that implements the <xref:System.Linq.IQueryable%601> interface).</span></span> <span data-ttu-id="90a65-109"><xref:System.Collections.IEnumerable>源通常源自 LINQ to DataSet 表达式或方法查询。</span><span class="sxs-lookup"><span data-stu-id="90a65-109">The <xref:System.Collections.IEnumerable> source has generally originated from a LINQ to DataSet expression or method query.</span></span>  
  
2. <span data-ttu-id="90a65-110">克隆的 <xref:System.Data.DataTable> 的架构从源表中枚举的第一个 <xref:System.Data.DataRow> 对象的列生成，克隆表的名称是源表的名称后面追加单词“query”。</span><span class="sxs-lookup"><span data-stu-id="90a65-110">The schema of the cloned <xref:System.Data.DataTable> is built from the columns of the first enumerated <xref:System.Data.DataRow> object in the source table and the name of the cloned table is the name of the source table with the word "query" appended to it.</span></span>  
  
3. <span data-ttu-id="90a65-111">对于源表中的每一行，会将行内容复制到新 <xref:System.Data.DataRow> 对象中，然后将该对象插入到克隆表中。</span><span class="sxs-lookup"><span data-stu-id="90a65-111">For each row in the source table, the content of the row is copied into a new <xref:System.Data.DataRow> object, which is then inserted into the cloned table.</span></span> <span data-ttu-id="90a65-112"><xref:System.Data.DataRow.RowState%2A> 和 <xref:System.Data.DataRow.RowError%2A> 属性在整个复制操作过程中保留。</span><span class="sxs-lookup"><span data-stu-id="90a65-112">The <xref:System.Data.DataRow.RowState%2A> and <xref:System.Data.DataRow.RowError%2A> properties are preserved across the copy operation.</span></span> <span data-ttu-id="90a65-113">如果源中的 <xref:System.ArgumentException> 对象来自不同的表，则会引发 <xref:System.Data.DataRow>。</span><span class="sxs-lookup"><span data-stu-id="90a65-113">An <xref:System.ArgumentException> is thrown if the <xref:System.Data.DataRow> objects in the source are from different tables.</span></span>  
  
4. <span data-ttu-id="90a65-114">复制完可查询的输入表中的所有 <xref:System.Data.DataTable> 对象后，将返回克隆的 <xref:System.Data.DataRow>。</span><span class="sxs-lookup"><span data-stu-id="90a65-114">The cloned <xref:System.Data.DataTable> is returned after all <xref:System.Data.DataRow> objects in the input queryable table have been copied.</span></span> <span data-ttu-id="90a65-115">如果源序列不包含任何 <xref:System.Data.DataRow> 对象，则该方法将返回一个空 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="90a65-115">If the source sequence does not contain any <xref:System.Data.DataRow> objects, the method returns an empty <xref:System.Data.DataTable>.</span></span>  
  
<span data-ttu-id="90a65-116">调用 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法会导致绑定到源表的查询执行。</span><span class="sxs-lookup"><span data-stu-id="90a65-116">Calling the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method causes the query bound to the source table to execute.</span></span>  
  
 <span data-ttu-id="90a65-117">当 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法在源表的行中遇到空引用或可以为 null 的值类型时，它将用 <xref:System.DBNull.Value> 替换该值。</span><span class="sxs-lookup"><span data-stu-id="90a65-117">When the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method encounters either a null reference or nullable value type in a row in the source table, it replaces the value with <xref:System.DBNull.Value>.</span></span> <span data-ttu-id="90a65-118">这样可以在返回的 <xref:System.Data.DataTable> 中正确处理 Null 值。</span><span class="sxs-lookup"><span data-stu-id="90a65-118">This way, null values are handled correctly in the returned <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="90a65-119">注意：<xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法接受可从多个 <xref:System.Data.DataTable> 或 <xref:System.Data.DataSet> 对象返回行的查询作为输入。</span><span class="sxs-lookup"><span data-stu-id="90a65-119">Note: The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method accepts as input a query that can return rows from multiple <xref:System.Data.DataTable> or <xref:System.Data.DataSet> objects.</span></span> <span data-ttu-id="90a65-120"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法将数据（不包括属性）从源 <xref:System.Data.DataTable> 或 <xref:System.Data.DataSet> 对象复制到返回的 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="90a65-120">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method will copy the data but not the properties from the source <xref:System.Data.DataTable> or <xref:System.Data.DataSet> objects to the returned <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="90a65-121">您将需要显式设置返回的 <xref:System.Data.DataTable> 的属性，例如 <xref:System.Data.DataTable.Locale%2A> 和 <xref:System.Data.DataTable.TableName%2A>。</span><span class="sxs-lookup"><span data-stu-id="90a65-121">You will need to explicitly set the properties on the returned <xref:System.Data.DataTable>, such as <xref:System.Data.DataTable.Locale%2A> and <xref:System.Data.DataTable.TableName%2A>.</span></span>  
  
 <span data-ttu-id="90a65-122">下面的示例查询 SalesOrderHeader 表中 2001 年 8 月 8 日以后的订单，并使用 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法通过查询创建 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="90a65-122">The following example queries the SalesOrderHeader table for orders after August 8, 2001 and uses the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method to create a <xref:System.Data.DataTable> from that query.</span></span> <span data-ttu-id="90a65-123">然后将 <xref:System.Data.DataTable> 绑定到作为 <xref:System.Windows.Forms.BindingSource> 的代理的 <xref:System.Windows.Forms.DataGridView>。</span><span class="sxs-lookup"><span data-stu-id="90a65-123">The <xref:System.Data.DataTable> is then bound to a <xref:System.Windows.Forms.BindingSource>, which acts as proxy for a <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#copytodatatable1)]
 [!code-vb[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#copytodatatable1)]  
  
## <a name="creating-a-custom-copytodatatablet-method"></a><span data-ttu-id="90a65-124">创建自定义 CopyToDataTable \<T> 方法</span><span class="sxs-lookup"><span data-stu-id="90a65-124">Creating a Custom CopyToDataTable\<T> Method</span></span>  

 <span data-ttu-id="90a65-125">仅在 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 源上（其中泛型参数 <xref:System.Collections.Generic.IEnumerable%601> 类型为 `T`）执行现有 <xref:System.Data.DataRow> 方法。</span><span class="sxs-lookup"><span data-stu-id="90a65-125">The existing <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="90a65-126">虽然这十分有用，但是它并不允许从标量类型的序列、返回匿名类型的查询或执行表联接的查询来创建表。</span><span class="sxs-lookup"><span data-stu-id="90a65-126">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that return anonymous types, or from queries that perform table joins.</span></span> <span data-ttu-id="90a65-127">有关如何实现两个自定义方法（ `CopyToDataTable` 这些方法从标量或匿名类型的序列加载表）的示例，请参阅 [如何：实现 CopyToDataTable \<T> ，其中泛型类型 T](implement-copytodatatable-where-type-not-a-datarow.md)不是 DataRow。</span><span class="sxs-lookup"><span data-stu-id="90a65-127">For an example of how to implement two custom `CopyToDataTable` methods that load a table from a sequence of scalar or anonymous types, see [How to: Implement CopyToDataTable\<T> Where the Generic Type T Is Not a DataRow](implement-copytodatatable-where-type-not-a-datarow.md)s.</span></span>  
  
 <span data-ttu-id="90a65-128">本节的示例使用以下自定义类型：</span><span class="sxs-lookup"><span data-stu-id="90a65-128">The examples in this section use the following custom types:</span></span>  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#itemclass)]
 [!code-vb[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#itemclass)]  
  
### <a name="example"></a><span data-ttu-id="90a65-129">示例</span><span class="sxs-lookup"><span data-stu-id="90a65-129">Example</span></span>  

 <span data-ttu-id="90a65-130">此示例在 `SalesOrderHeader` 和 `SalesOrderDetail` 表上执行联接以获得八月的联机订单，并从查询创建表。</span><span class="sxs-lookup"><span data-stu-id="90a65-130">This example performs a join over the `SalesOrderHeader` and `SalesOrderDetail` tables to get online orders from the month of August and creates a table from the query.</span></span>  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#join)]
 [!code-vb[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#join)]  
  
### <a name="example"></a><span data-ttu-id="90a65-131">示例</span><span class="sxs-lookup"><span data-stu-id="90a65-131">Example</span></span>  

 <span data-ttu-id="90a65-132">下面的示例查询价格高于 9.99 美元的商品集合，并从查询结果创建表。</span><span class="sxs-lookup"><span data-stu-id="90a65-132">The following example queries a collection for items of price greater than $9.99 and creates a table from the query results.</span></span>  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintotable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintotable)]  
  
### <a name="example"></a><span data-ttu-id="90a65-133">示例</span><span class="sxs-lookup"><span data-stu-id="90a65-133">Example</span></span>  

 <span data-ttu-id="90a65-134">下面的示例查询价格高于 9.99 的商品集合，并投影结果。</span><span class="sxs-lookup"><span data-stu-id="90a65-134">The following example queries a collection for items of price greater than 9.99 and projects the results.</span></span> <span data-ttu-id="90a65-135">返回的匿名类型序列被加载到现有表中。</span><span class="sxs-lookup"><span data-stu-id="90a65-135">The returned sequence of anonymous types is loaded into an existing table.</span></span>  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintoexistingtable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintoexistingtable)]  
  
### <a name="example"></a><span data-ttu-id="90a65-136">示例</span><span class="sxs-lookup"><span data-stu-id="90a65-136">Example</span></span>  

 <span data-ttu-id="90a65-137">下面的示例查询价格高于 9.99 美元的商品集合，并投影结果。</span><span class="sxs-lookup"><span data-stu-id="90a65-137">The following example queries a collection for items of price greater than $9.99 and projects the results.</span></span> <span data-ttu-id="90a65-138">返回的匿名类型序列被加载到现有表中。</span><span class="sxs-lookup"><span data-stu-id="90a65-138">The returned sequence of anonymous types is loaded into an existing table.</span></span> <span data-ttu-id="90a65-139">表架构自动扩展，因为 `Book` 和 `Movies` 类型是从 `Item` 类型派生的。</span><span class="sxs-lookup"><span data-stu-id="90a65-139">The table schema is automatically expanded because the `Book` and `Movies` types are derived from the `Item` type.</span></span>  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsexpandschema)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsexpandschema)]  
  
### <a name="example"></a><span data-ttu-id="90a65-140">示例</span><span class="sxs-lookup"><span data-stu-id="90a65-140">Example</span></span>  

 <span data-ttu-id="90a65-141">下面的示例查询价格高于 9.99 美元的商品集合，并返回 <xref:System.Double> 的序列，它将被加载到新表中。</span><span class="sxs-lookup"><span data-stu-id="90a65-141">The following example queries a collection for items of price greater than $9.99 and returns a sequence of <xref:System.Double>, which is loaded into a new table.</span></span>  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loadscalarsequence)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loadscalarsequence)]  
  
## <a name="see-also"></a><span data-ttu-id="90a65-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="90a65-142">See also</span></span>

- [<span data-ttu-id="90a65-143">编程指南</span><span class="sxs-lookup"><span data-stu-id="90a65-143">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)
- [<span data-ttu-id="90a65-144">泛型字段和 SetField 方法</span><span class="sxs-lookup"><span data-stu-id="90a65-144">Generic Field and SetField Methods</span></span>](generic-field-and-setfield-methods-linq-to-dataset.md)
- [<span data-ttu-id="90a65-145">LINQ to DataSet 示例</span><span class="sxs-lookup"><span data-stu-id="90a65-145">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
