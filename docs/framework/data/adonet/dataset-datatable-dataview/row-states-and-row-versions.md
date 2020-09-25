---
title: 行状态和行版本
ms.date: 07/19/2018
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
ms.openlocfilehash: 1b80ae78fad22989f99fb1e992d4978a192e0c66
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204523"
---
# <a name="row-states-and-row-versions"></a><span data-ttu-id="c8e69-102">行状态和行版本</span><span class="sxs-lookup"><span data-stu-id="c8e69-102">Row States and Row Versions</span></span>

<span data-ttu-id="c8e69-103">ADO.NET 用行状态和行版本管理表中的行。</span><span class="sxs-lookup"><span data-stu-id="c8e69-103">ADO.NET manages rows in tables using row states and versions.</span></span> <span data-ttu-id="c8e69-104">行状态指示行的状态；行版本在修改行中存储的值时维护各个阶段的值，包括当前值、原始值和默认值。</span><span class="sxs-lookup"><span data-stu-id="c8e69-104">A row state indicates the status of a row; row versions maintain the values stored in a row as it is modified, including current, original, and default values.</span></span> <span data-ttu-id="c8e69-105">例如，在修改了行中的某列后，该行的行状态将为 `Modified`，并且有两个行版本：`Current`（包含行的当前值）和 `Original`（包含列修改前行的值）。</span><span class="sxs-lookup"><span data-stu-id="c8e69-105">For example, after you have made a modification to a column in a row, the row will have a row state of `Modified`, and two row versions: `Current`, which contains the current row values, and `Original`, which contains the row values before the column was modified.</span></span>  
  
 <span data-ttu-id="c8e69-106">每个 <xref:System.Data.DataRow> 对象都具有 <xref:System.Data.DataRow.RowState%2A> 属性，您可以检查此属性来确定行的当前状态。</span><span class="sxs-lookup"><span data-stu-id="c8e69-106">Each <xref:System.Data.DataRow> object has a <xref:System.Data.DataRow.RowState%2A> property that you can examine to determine the current state of the row.</span></span> <span data-ttu-id="c8e69-107">下表提供了对每个 `RowState` 枚举值的简短说明。</span><span class="sxs-lookup"><span data-stu-id="c8e69-107">The following table gives a brief description of each `RowState` enumeration value.</span></span>  
  
|<span data-ttu-id="c8e69-108">RowState 值</span><span class="sxs-lookup"><span data-stu-id="c8e69-108">RowState value</span></span>|<span data-ttu-id="c8e69-109">描述</span><span class="sxs-lookup"><span data-stu-id="c8e69-109">Description</span></span>|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|<span data-ttu-id="c8e69-110">自上次调用 `AcceptChanges` 以来或由 `DataAdapter.Fill` 创建该行以来，没有进行任何更改。</span><span class="sxs-lookup"><span data-stu-id="c8e69-110">No changes have been made since the last call to `AcceptChanges` or since the row was created by `DataAdapter.Fill`.</span></span>|  
|<xref:System.Data.DataRowState.Added>|<span data-ttu-id="c8e69-111">已将该行添加到表中，但尚未调用 `AcceptChanges`。</span><span class="sxs-lookup"><span data-stu-id="c8e69-111">The row has been added to the table, but `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Modified>|<span data-ttu-id="c8e69-112">已更改了行的某个元素。</span><span class="sxs-lookup"><span data-stu-id="c8e69-112">Some element of the row has been changed.</span></span>|  
|<xref:System.Data.DataRowState.Deleted>|<span data-ttu-id="c8e69-113">已从表中删除该行，并且尚未调用 `AcceptChanges`。</span><span class="sxs-lookup"><span data-stu-id="c8e69-113">The row has been deleted from a table, and `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Detached>|<span data-ttu-id="c8e69-114">该行不是任何 `DataRowCollection` 的一部分。</span><span class="sxs-lookup"><span data-stu-id="c8e69-114">The row is not part of any `DataRowCollection`.</span></span> <span data-ttu-id="c8e69-115">新创建的行的 `RowState` 设置为 `Detached`。</span><span class="sxs-lookup"><span data-stu-id="c8e69-115">The `RowState` of a newly created row is set to `Detached`.</span></span> <span data-ttu-id="c8e69-116">通过调用 `DataRow` 方法将新的 `DataRowCollection` 添加到 `Add` 后，`RowState` 属性的值设置为 `Added`。</span><span class="sxs-lookup"><span data-stu-id="c8e69-116">After the new `DataRow` is added to the `DataRowCollection` by calling the `Add` method, the value of the `RowState` property is set to `Added`.</span></span><br /><br /> <span data-ttu-id="c8e69-117">将使用 `Detached` 方法，或使用 `DataRowCollection` 方法接着使用 `Remove` 方法从 `Delete` 中移除的行也设置为 `AcceptChanges`。</span><span class="sxs-lookup"><span data-stu-id="c8e69-117">`Detached` is also set for a row that has been removed from a `DataRowCollection` using the `Remove` method, or by the `Delete` method followed by the `AcceptChanges` method.</span></span>|  
  
 <span data-ttu-id="c8e69-118">对 `AcceptChanges`、<xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 调用 <xref:System.Data.DataRow> 时，会移除行状态为 `Deleted` 的所有行。</span><span class="sxs-lookup"><span data-stu-id="c8e69-118">When `AcceptChanges` is called on a <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , or <xref:System.Data.DataRow>, all rows with a row state of `Deleted` are removed.</span></span> <span data-ttu-id="c8e69-119">剩余行的行状态为 `Unchanged`，并且 `Original` 行版本中的值将被 `Current` 行版本值覆盖。</span><span class="sxs-lookup"><span data-stu-id="c8e69-119">The remaining rows are given a row state of `Unchanged`, and the values in the `Original` row version are overwritten with the `Current` row version values.</span></span> <span data-ttu-id="c8e69-120">调用 `RejectChanges` 时，会移除行状态为 `Added` 的所有行。</span><span class="sxs-lookup"><span data-stu-id="c8e69-120">When `RejectChanges` is called, all rows with a row state of `Added` are removed.</span></span> <span data-ttu-id="c8e69-121">剩余行的行状态为 `Unchanged`，并且 `Current` 行版本中的值将被 `Original` 行版本值覆盖。</span><span class="sxs-lookup"><span data-stu-id="c8e69-121">The remaining rows are given a row state of `Unchanged`, and the values in the `Current` row version are overwritten with the `Original` row version values.</span></span>  
  
 <span data-ttu-id="c8e69-122">通过列引用来传递 <xref:System.Data.DataRowVersion> 参数，您可以查看行的不同行版本，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="c8e69-122">You can view the different row versions of a row by passing a <xref:System.Data.DataRowVersion> parameter with the column reference, as shown in the following example.</span></span>  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 <span data-ttu-id="c8e69-123">下表提供了对每个 `DataRowVersion` 枚举值的简短说明。</span><span class="sxs-lookup"><span data-stu-id="c8e69-123">The following table gives a brief description of each `DataRowVersion` enumeration value.</span></span>  
  
|<span data-ttu-id="c8e69-124">DataRowVersion 值</span><span class="sxs-lookup"><span data-stu-id="c8e69-124">DataRowVersion value</span></span>|<span data-ttu-id="c8e69-125">描述</span><span class="sxs-lookup"><span data-stu-id="c8e69-125">Description</span></span>|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|<span data-ttu-id="c8e69-126">行的当前值。</span><span class="sxs-lookup"><span data-stu-id="c8e69-126">The current values for the row.</span></span> <span data-ttu-id="c8e69-127">如果行的 `RowState` 为 `Deleted`，则不存在此行版本。</span><span class="sxs-lookup"><span data-stu-id="c8e69-127">This row version does not exist for rows with a `RowState` of `Deleted`.</span></span>|  
|<xref:System.Data.DataRowVersion.Default>|<span data-ttu-id="c8e69-128">特定行的默认行版本。</span><span class="sxs-lookup"><span data-stu-id="c8e69-128">The default row version for a particular row.</span></span> <span data-ttu-id="c8e69-129">`Added`、`Modified` 或 `Deleted` 行的默认行版本是 `Current`。</span><span class="sxs-lookup"><span data-stu-id="c8e69-129">The default row version for an `Added`, `Modified`, or `Deleted` row is `Current`.</span></span> <span data-ttu-id="c8e69-130">`Detached` 行的默认行版本是 `Proposed`。</span><span class="sxs-lookup"><span data-stu-id="c8e69-130">The default row version for a `Detached` row is `Proposed`.</span></span>|  
|<xref:System.Data.DataRowVersion.Original>|<span data-ttu-id="c8e69-131">行的原始值。</span><span class="sxs-lookup"><span data-stu-id="c8e69-131">The original values for the row.</span></span> <span data-ttu-id="c8e69-132">如果行的 `RowState` 为 `Added`，则不存在此行版本。</span><span class="sxs-lookup"><span data-stu-id="c8e69-132">This row version does not exist for rows with a `RowState` of `Added`.</span></span>|  
|<xref:System.Data.DataRowVersion.Proposed>|<span data-ttu-id="c8e69-133">行的建议值。</span><span class="sxs-lookup"><span data-stu-id="c8e69-133">The proposed values for the row.</span></span> <span data-ttu-id="c8e69-134">在对行进行编辑操作的过程中，或者对于不属于 `DataRowCollection` 的行，存在此行版本。</span><span class="sxs-lookup"><span data-stu-id="c8e69-134">This row version exists during an edit operation on a row, or for a row that is not part of a `DataRowCollection`.</span></span>|  
  
 <span data-ttu-id="c8e69-135">通过调用 `DataRow` 方法并将 <xref:System.Data.DataRow.HasVersion%2A> 作为参数传递，您可以测试 `DataRowVersion` 是否具有特定的行版本。</span><span class="sxs-lookup"><span data-stu-id="c8e69-135">You can test whether a `DataRow` has a particular row version by calling the <xref:System.Data.DataRow.HasVersion%2A> method and passing a `DataRowVersion` as an argument.</span></span> <span data-ttu-id="c8e69-136">例如，在调用 `DataRow.HasVersion(DataRowVersion.Original)` 之前，`false` 对新添加的行将返回 `AcceptChanges`。</span><span class="sxs-lookup"><span data-stu-id="c8e69-136">For example, `DataRow.HasVersion(DataRowVersion.Original)` will return `false` for newly added rows before `AcceptChanges` has been called.</span></span>  
  
 <span data-ttu-id="c8e69-137">下面的代码示例演示表中所有已删除行中的值。</span><span class="sxs-lookup"><span data-stu-id="c8e69-137">The following code example displays the values in all the deleted rows of a table.</span></span> <span data-ttu-id="c8e69-138">`Deleted` 行没有 `Current` 行版本，因此在访问列值时必须传递 `DataRowVersion.Original`。</span><span class="sxs-lookup"><span data-stu-id="c8e69-138">`Deleted` rows do not have a `Current` row version, so you must pass `DataRowVersion.Original` when accessing the column values.</span></span>  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
  
Dim delRows() As DataRow = catTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
Console.WriteLine("Deleted rows:" & vbCrLf)  
  
Dim catCol As DataColumn  
Dim delRow As DataRow  
  
For Each catCol In catTable.Columns  
  Console.Write(catCol.ColumnName & vbTab)  
Next  
Console.WriteLine()  
  
For Each delRow In delRows  
  For Each catCol In catTable.Columns  
    Console.Write(delRow(catCol, DataRowVersion.Original) & vbTab)  
  Next  
  Console.WriteLine()  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
  
DataRow[] delRows = catTable.Select(null, null, DataViewRowState.Deleted);  
  
Console.WriteLine("Deleted rows:\n");  
  
foreach (DataColumn catCol in catTable.Columns)  
  Console.Write(catCol.ColumnName + "\t");  
Console.WriteLine();  
  
foreach (DataRow delRow in delRows)  
{  
  foreach (DataColumn catCol in catTable.Columns)  
    Console.Write(delRow[catCol, DataRowVersion.Original] + "\t");  
  Console.WriteLine();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8e69-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="c8e69-139">See also</span></span>

- [<span data-ttu-id="c8e69-140">操作数据表中的数据</span><span class="sxs-lookup"><span data-stu-id="c8e69-140">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="c8e69-141">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="c8e69-141">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="c8e69-142">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="c8e69-142">DataAdapters and DataReaders</span></span>](../dataadapters-and-datareaders.md)
- [<span data-ttu-id="c8e69-143">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="c8e69-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
