---
title: 使用 DataAdapter 更新数据源
description: 了解 DataAdapter 的 Update 方法如何将数据集中的更改解析回 ADO.NET 应用程序中的数据源。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: e2348a3a89aa1c28856bfc21aaa25f2c8327aac7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286179"
---
# <a name="updating-data-sources-with-dataadapters"></a><span data-ttu-id="8e800-103">使用 DataAdapter 更新数据源</span><span class="sxs-lookup"><span data-stu-id="8e800-103">Updating Data Sources with DataAdapters</span></span>

<span data-ttu-id="8e800-104">调用 `Update` 的 <xref:System.Data.Common.DataAdapter> 方法可以将 <xref:System.Data.DataSet> 中的更改解析回数据源。</span><span class="sxs-lookup"><span data-stu-id="8e800-104">The `Update` method of the <xref:System.Data.Common.DataAdapter> is called to resolve changes from a <xref:System.Data.DataSet> back to the data source.</span></span> <span data-ttu-id="8e800-105">与 `Update` 方法类似，`Fill` 方法将 `DataSet` 的实例和可选的 <xref:System.Data.DataTable> 对象或 `DataTable` 名称用作自变量。</span><span class="sxs-lookup"><span data-stu-id="8e800-105">The `Update` method, like the `Fill` method, takes as arguments an instance of a `DataSet`, and an optional <xref:System.Data.DataTable> object or `DataTable` name.</span></span> <span data-ttu-id="8e800-106">`DataSet` 实例是包含已做的更改的 `DataSet`，`DataTable` 标识从其中检索这些更改的表。</span><span class="sxs-lookup"><span data-stu-id="8e800-106">The `DataSet` instance is the `DataSet` that contains the changes that have been made, and the `DataTable` identifies the table from which to retrieve the changes.</span></span> <span data-ttu-id="8e800-107">如果未指定 `DataTable`，则使用 `DataTable` 中的第一个 `DataSet`。</span><span class="sxs-lookup"><span data-stu-id="8e800-107">If no `DataTable` is specified, the first `DataTable` in the `DataSet` is used.</span></span>

<span data-ttu-id="8e800-108">当调用 `Update` 方法时，`DataAdapter` 会分析已做的更改并执行相应的命令（INSERT、UPDATE 或 DELETE）。</span><span class="sxs-lookup"><span data-stu-id="8e800-108">When you call the `Update` method, the `DataAdapter` analyzes the changes that have been made and executes the appropriate command (INSERT, UPDATE, or DELETE).</span></span> <span data-ttu-id="8e800-109">当 `DataAdapter` 遇到对 <xref:System.Data.DataRow> 所做的更改时，它将使用 <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>、<xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> 或 <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> 来处理该更改。</span><span class="sxs-lookup"><span data-stu-id="8e800-109">When the `DataAdapter` encounters a change to a <xref:System.Data.DataRow>, it uses the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, or <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> to process the change.</span></span> <span data-ttu-id="8e800-110">这样，您就可以通过在设计时指定命令语法并在可能时通过使用存储过程来尽量提高 ADO.NET 应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="8e800-110">This allows you to maximize the performance of your ADO.NET application by specifying command syntax at design time and, where possible, through the use of stored procedures.</span></span> <span data-ttu-id="8e800-111">在调用 `Update` 之前，必须显式设置这些命令。</span><span class="sxs-lookup"><span data-stu-id="8e800-111">You must explicitly set the commands before calling `Update`.</span></span> <span data-ttu-id="8e800-112">如果调用了 `Update` 但不存在用于特定更新的相应命令（例如，不存在用于已删除行的 `DeleteCommand`），则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="8e800-112">If `Update` is called and the appropriate command does not exist for a particular update (for example, no `DeleteCommand` for deleted rows), an exception is thrown.</span></span>

> [!NOTE]
> <span data-ttu-id="8e800-113">如果您要通过 SQL Server 存储过程使用 `DataAdapter` 来编辑或删除数据，请确保不要在存储过程定义中使用 SET NOCOUNT ON。</span><span class="sxs-lookup"><span data-stu-id="8e800-113">If you are using SQL Server stored procedures to edit or delete data using a `DataAdapter`, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="8e800-114">这将使返回的受影响的行数为零，`DataAdapter` 会将其解释为并发冲突。</span><span class="sxs-lookup"><span data-stu-id="8e800-114">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="8e800-115">在这种情况下，将引发 <xref:System.Data.DBConcurrencyException>。</span><span class="sxs-lookup"><span data-stu-id="8e800-115">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>

<span data-ttu-id="8e800-116">可以使用命令参数为 `DataSet` 中每个已修改的行指定 SQL 语句或存储过程的输入和输出值。</span><span class="sxs-lookup"><span data-stu-id="8e800-116">Command parameters can be used to specify input and output values for an SQL statement or stored procedure for each modified row in a `DataSet`.</span></span> <span data-ttu-id="8e800-117">有关详细信息，请参阅[DataAdapter 参数](dataadapter-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="8e800-117">For more information, see [DataAdapter Parameters](dataadapter-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8e800-118">必须了解在 <xref:System.Data.DataTable> 中删除行和移除行之间的差异。</span><span class="sxs-lookup"><span data-stu-id="8e800-118">It is important to understand the difference between deleting a row in a <xref:System.Data.DataTable> and removing the row.</span></span> <span data-ttu-id="8e800-119">当调用 `Remove` 或 `RemoveAt` 方法时，会立即移除该行。</span><span class="sxs-lookup"><span data-stu-id="8e800-119">When you call the `Remove` or `RemoveAt` method, the row is removed immediately.</span></span> <span data-ttu-id="8e800-120">如果之后将 `DataTable` 或 `DataSet` 传递给 `DataAdapter` 并调用 `Update`，则不会影响后端数据源中的任何相应行。</span><span class="sxs-lookup"><span data-stu-id="8e800-120">Any corresponding rows in the back end data source will not be affected if you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`.</span></span> <span data-ttu-id="8e800-121">当您使用 `Delete` 方法时，该行仍将保留在 `DataTable` 中并会标记为删除。</span><span class="sxs-lookup"><span data-stu-id="8e800-121">When you use the `Delete` method, the row remains in the `DataTable` and is marked for deletion.</span></span> <span data-ttu-id="8e800-122">如果之后将 `DataTable` 或 `DataSet` 传递给 `DataAdapter` 并调用 `Update`，则会删除后端数据源中的相应行。</span><span class="sxs-lookup"><span data-stu-id="8e800-122">If you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`, the corresponding row in the back end data source is deleted.</span></span>

<span data-ttu-id="8e800-123">如果 `DataTable` 映射到单个数据库表或从单个数据库表生成，则可以利用 <xref:System.Data.Common.DbCommandBuilder> 对象为 `DeleteCommand` 自动生成 `InsertCommand`、`UpdateCommand` 和 `DataAdapter` 对象。</span><span class="sxs-lookup"><span data-stu-id="8e800-123">If your `DataTable` maps to or is generated from a single database table, you can take advantage of the <xref:System.Data.Common.DbCommandBuilder> object to automatically generate the `DeleteCommand`, `InsertCommand`, and `UpdateCommand` objects for the `DataAdapter`.</span></span> <span data-ttu-id="8e800-124">有关详细信息，请参阅[通过 Commandbuilder 生成命令](generating-commands-with-commandbuilders.md)。</span><span class="sxs-lookup"><span data-stu-id="8e800-124">For more information, see [Generating Commands with CommandBuilders](generating-commands-with-commandbuilders.md).</span></span>

## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a><span data-ttu-id="8e800-125">使用 UpdatedRowSource 将值映射到数据集</span><span class="sxs-lookup"><span data-stu-id="8e800-125">Using UpdatedRowSource to Map Values to a DataSet</span></span>

<span data-ttu-id="8e800-126">通过使用 `DataTable` 对象的 `DataAdapter` 属性，您可以在调用 <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> 的 Update 方法后控制从数据源返回的值映射回 <xref:System.Data.Common.DbCommand> 的方式。</span><span class="sxs-lookup"><span data-stu-id="8e800-126">You can control how the values returned from the data source are mapped back to the `DataTable` following a call to the Update method of a `DataAdapter`, by using the <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> property of a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="8e800-127">通过将 `UpdatedRowSource` 属性设置为 <xref:System.Data.UpdateRowSource> 枚举值之一，您可以控制是忽略由 `DataAdapter` 命令返回的输出参数还是将其应用于 `DataSet` 中已更改的行。</span><span class="sxs-lookup"><span data-stu-id="8e800-127">By setting the `UpdatedRowSource` property to one of the <xref:System.Data.UpdateRowSource> enumeration values, you can control whether output parameters returned by the `DataAdapter` commands are ignored or applied to the changed row in the `DataSet`.</span></span> <span data-ttu-id="8e800-128">还可以指定是否将返回的第一行（如果存在）应用于 `DataTable` 中已更改的行。</span><span class="sxs-lookup"><span data-stu-id="8e800-128">You can also specify whether the first returned row (if it exists) is applied to the changed row in the `DataTable`.</span></span>

<span data-ttu-id="8e800-129">下表说明 `UpdateRowSource` 枚举的不同值，并说明它们如何影响与 `DataAdapter` 一起使用的命令的行为。</span><span class="sxs-lookup"><span data-stu-id="8e800-129">The following table describes the different values of the `UpdateRowSource` enumeration and how they affect the behavior of a command used with a `DataAdapter`.</span></span>

|<span data-ttu-id="8e800-130">UpdatedRowSource 枚举</span><span class="sxs-lookup"><span data-stu-id="8e800-130">UpdatedRowSource Enumeration</span></span>|<span data-ttu-id="8e800-131">说明</span><span class="sxs-lookup"><span data-stu-id="8e800-131">Description</span></span>|
|----------------------------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|<span data-ttu-id="8e800-132">输出参数和返回的结果集的第一行都可以映射到 `DataSet` 中已更改的行。</span><span class="sxs-lookup"><span data-stu-id="8e800-132">Both the output parameters and the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|<span data-ttu-id="8e800-133">只有返回的结果集的第一行中的数据才可以映射到 `DataSet` 中已更改的行。</span><span class="sxs-lookup"><span data-stu-id="8e800-133">Only the data in the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|
|<xref:System.Data.UpdateRowSource.None>|<span data-ttu-id="8e800-134">忽略任何输出参数或返回的结果集中的行。</span><span class="sxs-lookup"><span data-stu-id="8e800-134">Any output parameters or rows of a returned result set are ignored.</span></span>|
|<xref:System.Data.UpdateRowSource.OutputParameters>|<span data-ttu-id="8e800-135">只有输出参数才可以映射到 `DataSet` 中已更改的行。</span><span class="sxs-lookup"><span data-stu-id="8e800-135">Only output parameters may be mapped to the changed row in the `DataSet`.</span></span>|

<span data-ttu-id="8e800-136">`Update` 方法会将更改解析回数据源；但在上次填充 `DataSet` 后，其他客户端可能已修改了数据源中的数据。</span><span class="sxs-lookup"><span data-stu-id="8e800-136">The `Update` method resolves your changes back to the data source; however other clients may have modified data at the data source since the last time you filled the `DataSet`.</span></span> <span data-ttu-id="8e800-137">若要使用当前数据刷新 `DataSet`，请使用 `DataAdapter` 和 `Fill` 方法。</span><span class="sxs-lookup"><span data-stu-id="8e800-137">To refresh your `DataSet` with current data, use the `DataAdapter` and `Fill` method.</span></span> <span data-ttu-id="8e800-138">新行将添加到该表中，更新的信息将并入现有行。</span><span class="sxs-lookup"><span data-stu-id="8e800-138">New rows will be added to the table, and updated information will be incorporated into existing rows.</span></span> <span data-ttu-id="8e800-139">`Fill` 方法通过检查 `DataSet` 中行的主键值以及 `SelectCommand` 返回的行来确定是要添加新行还是更新现有行。</span><span class="sxs-lookup"><span data-stu-id="8e800-139">The `Fill` method determines whether a new row will be added or an existing row will be updated by examining the primary key values of the rows in the `DataSet` and the rows returned by the `SelectCommand`.</span></span> <span data-ttu-id="8e800-140">如果 `Fill` 方法遇到 `DataSet` 中某行的主键值与 `SelectCommand` 返回结果中某行的主键值相匹配，则它将用 `SelectCommand` 返回的行中的信息更新现有行，并将现有行的 <xref:System.Data.DataRow.RowState%2A> 设置为 `Unchanged`。</span><span class="sxs-lookup"><span data-stu-id="8e800-140">If the `Fill` method encounters a primary key value for a row in the `DataSet` that matches a primary key value from a row in the results returned by the `SelectCommand`, it updates the existing row with the information from the row returned by the `SelectCommand` and sets the <xref:System.Data.DataRow.RowState%2A> of the existing row to `Unchanged`.</span></span> <span data-ttu-id="8e800-141">如果 `SelectCommand` 返回的行所具有的主键值与 `DataSet` 中行的任何主键值都不匹配，则 `Fill` 方法将添加 `RowState` 为 `Unchanged` 的新行。</span><span class="sxs-lookup"><span data-stu-id="8e800-141">If a row returned by the `SelectCommand` has a primary key value that does not match any of the primary key values of the rows in the `DataSet`, the `Fill` method adds a new row with a `RowState` of `Unchanged`.</span></span>

> [!NOTE]
> <span data-ttu-id="8e800-142">如果 `SelectCommand` 返回 OUTER JOIN 的结果，则 `DataAdapter` 不会为生成的 `PrimaryKey` 设置 `DataTable` 值。</span><span class="sxs-lookup"><span data-stu-id="8e800-142">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` will not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="8e800-143">您必须自己定义 `PrimaryKey` 以确保正确解析重复行。</span><span class="sxs-lookup"><span data-stu-id="8e800-143">You must define the `PrimaryKey` yourself to ensure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="8e800-144">有关详细信息，请参阅[定义主键](./dataset-datatable-dataview/defining-primary-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="8e800-144">For more information, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>

<span data-ttu-id="8e800-145">若要处理在调用方法时可能发生的异常 `Update` `RowUpdated` （请参阅[处理 DataAdapter 事件](handling-dataadapter-events.md)），或者可以在 `DataAdapter.ContinueUpdateOnError` 调用之前将设置为，并在 `true` `Update` `RowError` 更新完成后响应特定行的属性中存储的错误信息（请参阅[行错误信息](./dataset-datatable-dataview/row-error-information.md)），以处理在调用方法时可能发生的异常。</span><span class="sxs-lookup"><span data-stu-id="8e800-145">To handle exceptions that may occur when calling the `Update` method, you can use the `RowUpdated` event to respond to row update errors as they occur (see [Handling DataAdapter Events](handling-dataadapter-events.md)), or you can set `DataAdapter.ContinueUpdateOnError` to `true` before calling `Update`, and respond to the error information stored in the `RowError` property of a particular row when the update is complete (see [Row Error Information](./dataset-datatable-dataview/row-error-information.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="8e800-146">对 `AcceptChanges` `DataSet` 、或调用 `DataTable` `DataRow` 将导致 `Original` 用的值覆盖的所有值 `DataRow` `Current` `DataRow` 。</span><span class="sxs-lookup"><span data-stu-id="8e800-146">Calling `AcceptChanges` on the `DataSet`, `DataTable`, or `DataRow` will cause all `Original` values for a `DataRow` to be overwritten with the `Current` values for the `DataRow`.</span></span> <span data-ttu-id="8e800-147">如果修改了唯一标识该行的字段值，则在调用 `AcceptChanges` 后，`Original` 值将不再匹配数据源中的值。</span><span class="sxs-lookup"><span data-stu-id="8e800-147">If the field values that identify the row as unique have been modified, after calling `AcceptChanges` the `Original` values will no longer match the values in the data source.</span></span> <span data-ttu-id="8e800-148">在调用 `AcceptChanges` 的 Update 方法期间会对每一行自动调用 `DataAdapter`。</span><span class="sxs-lookup"><span data-stu-id="8e800-148">`AcceptChanges` is called automatically for each row during a call to the Update method of a `DataAdapter`.</span></span> <span data-ttu-id="8e800-149">在调用 Update 方法期间，通过先将 `AcceptChangesDuringUpdate` 的 `DataAdapter` 属性设置为 false，或为 `RowUpdated` 事件创建一个事件处理程序并将 <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> 设置为 <xref:System.Data.UpdateStatus.SkipCurrentRow>，可以保留原始值。</span><span class="sxs-lookup"><span data-stu-id="8e800-149">You can preserve the original values during a call to the Update method by first setting the `AcceptChangesDuringUpdate` property of the `DataAdapter` to false, or by creating an event handler for the `RowUpdated` event and setting the <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> to <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span></span> <span data-ttu-id="8e800-150">有关详细信息，请参阅[合并数据集内容](./dataset-datatable-dataview/merging-dataset-contents.md)和[处理 DataAdapter 事件](handling-dataadapter-events.md)。</span><span class="sxs-lookup"><span data-stu-id="8e800-150">For more information, see [Merging DataSet Contents](./dataset-datatable-dataview/merging-dataset-contents.md) and [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>

## <a name="example"></a><span data-ttu-id="8e800-151">示例</span><span class="sxs-lookup"><span data-stu-id="8e800-151">Example</span></span>

<span data-ttu-id="8e800-152">下面的示例演示如何通过显式设置 `UpdateCommand` 的 `DataAdapter` 和调用其方法来对修改的行执行更新 `Update` 。</span><span class="sxs-lookup"><span data-stu-id="8e800-152">The following examples demonstrate how to perform updates to modified rows by explicitly setting the `UpdateCommand` of a `DataAdapter` and calling its `Update` method.</span></span> <span data-ttu-id="8e800-153">请注意，在 UPDATE 语句的 WHERE 子句中指定的参数设置为使用 `Original` 的 `SourceColumn` 值。</span><span class="sxs-lookup"><span data-stu-id="8e800-153">Notice that the parameter specified in the WHERE clause of the UPDATE statement is set to use the `Original` value of the `SourceColumn`.</span></span> <span data-ttu-id="8e800-154">这一点很重要，因为 `Current` 值可能已被修改，可能会不匹配数据源中的值。</span><span class="sxs-lookup"><span data-stu-id="8e800-154">This is important, because the `Current` value may have been modified and may not match the value in the data source.</span></span> <span data-ttu-id="8e800-155">`Original` 值是用于从数据源填充 `DataTable` 的值。</span><span class="sxs-lookup"><span data-stu-id="8e800-155">The `Original` value is the value that was used to populate the `DataTable` from the data source.</span></span>

[!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]

## <a name="autoincrement-columns"></a><span data-ttu-id="8e800-156">AutoIncrement 列</span><span class="sxs-lookup"><span data-stu-id="8e800-156">AutoIncrement Columns</span></span>

<span data-ttu-id="8e800-157">如果数据源中的表具有自动递增列，则可以通过以下方式填充 `DataSet` 中的列：作为存储过程的输出参数返回自动递增值并将其映射到表中的一列、返回由存储过程或 SQL 语句返回的结果集第一行中的自动递增值或者使用 `RowUpdated` 的 `DataAdapter` 事件来执行其他 SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="8e800-157">If the tables from your data source have auto-incrementing columns, you can fill the columns in your `DataSet` either by returning the auto-increment value as an output parameter of a stored procedure and mapping that to a column in a table, by returning the auto-increment value in the first row of a result set returned by a stored procedure or SQL statement, or by using the `RowUpdated` event of the `DataAdapter` to execute an additional SELECT statement.</span></span> <span data-ttu-id="8e800-158">有关详细信息和示例，请参阅[检索标识或自动编号值](retrieving-identity-or-autonumber-values.md)。</span><span class="sxs-lookup"><span data-stu-id="8e800-158">For more information and an example, see [Retrieving Identity or Autonumber Values](retrieving-identity-or-autonumber-values.md).</span></span>

## <a name="ordering-of-inserts-updates-and-deletes"></a><span data-ttu-id="8e800-159">插入、更新和删除的排序</span><span class="sxs-lookup"><span data-stu-id="8e800-159">Ordering of Inserts, Updates, and Deletes</span></span>

<span data-ttu-id="8e800-160">在许多情况下，以何种顺序向数据源发送通过 `DataSet` 所做的更改是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="8e800-160">In many circumstances, the order in which changes made through the `DataSet` are sent to the data source is important.</span></span> <span data-ttu-id="8e800-161">例如，如果更新了现有行的主键值，并且添加了以新主键值作为外键的新行，则务必要在处理插入之前处理更新。</span><span class="sxs-lookup"><span data-stu-id="8e800-161">For example, if a primary key value for an existing row is updated, and a new row has been added with the new primary key value as a foreign key, it is important to process the update before the insert.</span></span>

<span data-ttu-id="8e800-162">可以使用 `Select` 的 `DataTable` 方法来返回仅引用具有特定 `DataRow` 的 `RowState` 数组。</span><span class="sxs-lookup"><span data-stu-id="8e800-162">You can use the `Select` method of the `DataTable` to return a `DataRow` array that only references rows with a particular `RowState`.</span></span> <span data-ttu-id="8e800-163">然后可以将返回的 `DataRow` 数组传递给 `Update` 的 `DataAdapter` 方法来处理已修改的行。</span><span class="sxs-lookup"><span data-stu-id="8e800-163">You can then pass the returned `DataRow` array to the `Update` method of the `DataAdapter` to process the modified rows.</span></span> <span data-ttu-id="8e800-164">通过指定要更新的行的子集，可以控制处理插入、更新和删除的顺序。</span><span class="sxs-lookup"><span data-stu-id="8e800-164">By specifying a subset of rows to be updated, you can control the order in which inserts, updates, and deletes are processed.</span></span>

## <a name="example"></a><span data-ttu-id="8e800-165">示例</span><span class="sxs-lookup"><span data-stu-id="8e800-165">Example</span></span>

<span data-ttu-id="8e800-166">例如，以下代码确保首先处理表中已删除的行，然后处理已更新的行，然后处理已插入的行。</span><span class="sxs-lookup"><span data-stu-id="8e800-166">For example, the following code ensures that the deleted rows of the table are processed first, then the updated rows, and then the inserted rows.</span></span>

```vb
Dim table As DataTable = dataSet.Tables("Customers")

' First process deletes.
dataSet.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.Deleted))

' Next process updates.
adapter.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.ModifiedCurrent))

' Finally, process inserts.
adapter.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.Added))
```

```csharp
DataTable table = dataSet.Tables["Customers"];

// First process deletes.
adapter.Update(table.Select(null, null, DataViewRowState.Deleted));

// Next process updates.
adapter.Update(table.Select(null, null,
  DataViewRowState.ModifiedCurrent));

// Finally, process inserts.
adapter.Update(table.Select(null, null, DataViewRowState.Added));
```

## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a><span data-ttu-id="8e800-167">使用 DataAdapter 来检索和更新数据</span><span class="sxs-lookup"><span data-stu-id="8e800-167">Use a DataAdapter to Retrieve and Update Data</span></span>

<span data-ttu-id="8e800-168">您可以使用 DataAdapter 来检索和更新数据。</span><span class="sxs-lookup"><span data-stu-id="8e800-168">You can use a DataAdapter to retrieve and update the data.</span></span>

- <span data-ttu-id="8e800-169">此示例使用 DataAdapter.AcceptChangesDuringFill 克隆数据库中的数据。</span><span class="sxs-lookup"><span data-stu-id="8e800-169">The sample uses DataAdapter.AcceptChangesDuringFill to clone the data in the database.</span></span> <span data-ttu-id="8e800-170">如果该属性设置为 false，则在填充该表时不会调用 AcceptChanges，并将新添加的行视为插入的行。</span><span class="sxs-lookup"><span data-stu-id="8e800-170">If the property is set as false, AcceptChanges is not called when filling the table, and the newly added rows are treated as inserted rows.</span></span> <span data-ttu-id="8e800-171">因此，此示例使用这些行将新行插到数据库中。</span><span class="sxs-lookup"><span data-stu-id="8e800-171">So, the sample uses these rows to insert the new rows into the database.</span></span>

- <span data-ttu-id="8e800-172">此示例使用 DataAdapter.TableMappings 来定义源表与 DataTable 之间的映射。</span><span class="sxs-lookup"><span data-stu-id="8e800-172">The samples uses DataAdapter.TableMappings to define the mapping between the source table and DataTable.</span></span>

- <span data-ttu-id="8e800-173">此示例使用 DataAdapter.FillLoadOption 来确定适配器从 DbDataReader 填充 DataTable 的方式。</span><span class="sxs-lookup"><span data-stu-id="8e800-173">The sample uses DataAdapter.FillLoadOption to determine how the adapter fills the DataTable from the DbDataReader.</span></span> <span data-ttu-id="8e800-174">在您创建 DataTable 时，可以通过将该属性设置为 LoadOption.Upsert 或 LoadOption.PreserveChanges 而仅将数据库中的数据写入当前版本或原始版本。</span><span class="sxs-lookup"><span data-stu-id="8e800-174">When you create a DataTable, you can only write the data from database to the current version or the original version by setting the property as the LoadOption.Upsert or the LoadOption.PreserveChanges.</span></span>

- <span data-ttu-id="8e800-175">此示例还将通过使用 DbDataAdapter.UpdateBatchSize 执行批处理操作来更新表。</span><span class="sxs-lookup"><span data-stu-id="8e800-175">The sample will also update the table by using DbDataAdapter.UpdateBatchSize to perform batch operations.</span></span>

<span data-ttu-id="8e800-176">在编译并运行此示例之前，您需要创建示例数据库：</span><span class="sxs-lookup"><span data-stu-id="8e800-176">Before you compile and run the sample, you need to create the sample database:</span></span>

```sql
USE [master]
GO

CREATE DATABASE [MySchool]

GO

USE [MySchool]
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Course]([CourseID] [nvarchar](10) NOT NULL,
[Year] [smallint] NOT NULL,
[Title] [nvarchar](100) NOT NULL,
[Credits] [int] NOT NULL,
[DepartmentID] [int] NOT NULL,
 CONSTRAINT [PK_Course] PRIMARY KEY CLUSTERED
(
[CourseID] ASC,
[Year] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Department]([DepartmentID] [int] IDENTITY(1,1) NOT NULL,
[Name] [nvarchar](50) NOT NULL,
[Budget] [money] NOT NULL,
[StartDate] [datetime] NOT NULL,
[Administrator] [int] NULL,
 CONSTRAINT [PK_Department] PRIMARY KEY CLUSTERED
(
[DepartmentID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1045', 2012, N'Calculus', 4, 7)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1061', 2012, N'Physics', 4, 1)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2021', 2012, N'Composition', 3, 2)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2042', 2012, N'Literature', 4, 2)

SET IDENTITY_INSERT [dbo].[Department] ON

INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (1, N'Engineering', 350000.0000, CAST(0x0000999C00000000 AS DateTime), 2)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (2, N'English', 120000.0000, CAST(0x0000999C00000000 AS DateTime), 6)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (4, N'Economics', 200000.0000, CAST(0x0000999C00000000 AS DateTime), 4)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (7, N'Mathematics', 250024.0000, CAST(0x0000999C00000000 AS DateTime), 3)
SET IDENTITY_INSERT [dbo].[Department] OFF

ALTER TABLE [dbo].[Course]  WITH CHECK ADD  CONSTRAINT [FK_Course_Department] FOREIGN KEY([DepartmentID])
REFERENCES [dbo].[Department] ([DepartmentID])
GO
ALTER TABLE [dbo].[Course] CHECK CONSTRAINT [FK_Course_Department]
GO
```

<span data-ttu-id="8e800-177">带有此代码示例的 c # 和 Visual Basic 项目可在[开发人员代码示例](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D)中找到。</span><span class="sxs-lookup"><span data-stu-id="8e800-177">C# and Visual Basic projects with this code sample can be found on [Developer Code Samples](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span></span>

```csharp
using System;
using System.Data;
using System.Data.Common;
using System.Data.SqlClient;
using System.Linq;
using CSDataAdapterOperations.Properties;

namespace CSDataAdapterOperations.Properties {
   internal sealed partial class Settings : global::System.Configuration.ApplicationSettingsBase {

      private static Settings defaultInstance = ((Settings)(global::System.Configuration.ApplicationSettingsBase.Synchronized(new Settings())));

      public static Settings Default {
         get {
            return defaultInstance;
         }
      }

      [global::System.Configuration.ApplicationScopedSettingAttribute()]
      [global::System.Configuration.DefaultSettingValueAttribute("Data Source=(local);Initial Catalog=MySchool;Integrated Security=True")]
      public string MySchoolConnectionString {
         get {
            return ((string)(this["MySchoolConnectionString"]));
         }
      }
   }
}

class Program {
   static void Main(string[] args) {
      Settings settings = new Settings();

      // Copy the data from the database.  Get the table Department and Course from the database.
      String selectString = @"SELECT [DepartmentID],[Name],[Budget],[StartDate],[Administrator]
                                     FROM [MySchool].[dbo].[Department];

                                   SELECT [CourseID],@Year as [Year],Max([Title]) as [Title],
                                   Max([Credits]) as [Credits],Max([DepartmentID]) as [DepartmentID]
                                   FROM [MySchool].[dbo].[Course]
                                   Group by [CourseID]";

      DataSet mySchool = new DataSet();

      SqlCommand selectCommand = new SqlCommand(selectString);
      SqlParameter parameter = selectCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2);
      parameter.Value = new Random(DateTime.Now.Millisecond).Next(9999);

      // Use DataTableMapping to map the source tables and the destination tables.
      DataTableMapping[] tableMappings = {new DataTableMapping("Table", "Department"), new DataTableMapping("Table1", "Course")};
      CopyData(mySchool, settings.MySchoolConnectionString, selectCommand, tableMappings);

      Console.WriteLine("The following tables are from the database.");
      foreach (DataTable table in mySchool.Tables) {
         Console.WriteLine(table.TableName);
         ShowDataTable(table);
      }

      // Roll back the changes
      DataTable department = mySchool.Tables["Department"];
      DataTable course = mySchool.Tables["Course"];

      department.Rows[0]["Name"] = "New" + department.Rows[0][1];
      course.Rows[0]["Title"] = "New" + course.Rows[0]["Title"];
      course.Rows[0]["Credits"] = 10;

      Console.WriteLine("After we changed the tables:");
      foreach (DataTable table in mySchool.Tables) {
         Console.WriteLine(table.TableName);
         ShowDataTable(table);
      }

      department.RejectChanges();
      Console.WriteLine("After use the RejectChanges method in Department table to roll back the changes:");
      ShowDataTable(department);

      DataColumn[] primaryColumns = { course.Columns["CourseID"] };
      DataColumn[] resetColumns = { course.Columns["Title"] };
      ResetCourse(course, settings.MySchoolConnectionString, primaryColumns, resetColumns);
      Console.WriteLine("After use the ResetCourse method in Course table to roll back the changes:");
      ShowDataTable(course);

      // Batch update the table.
      String insertString = @"Insert into [MySchool].[dbo].[Course]([CourseID],[Year],[Title],
                                   [Credits],[DepartmentID])
             values (@CourseID,@Year,@Title,@Credits,@DepartmentID)";
      SqlCommand insertCommand = new SqlCommand(insertString);
      insertCommand.Parameters.Add("@CourseID", SqlDbType.NVarChar, 10, "CourseID");
      insertCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2, "Year");
      insertCommand.Parameters.Add("@Title", SqlDbType.NVarChar, 100, "Title");
      insertCommand.Parameters.Add("@Credits", SqlDbType.Int, 4, "Credits");
      insertCommand.Parameters.Add("@DepartmentID", SqlDbType.Int, 4, "DepartmentID");

      const Int32 batchSize = 10;
      BatchInsertUpdate(course, settings.MySchoolConnectionString, insertCommand, batchSize);
   }

   private static void CopyData(DataSet dataSet, String connectionString, SqlCommand selectCommand, DataTableMapping[] tableMappings) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         selectCommand.Connection = connection;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {adapter.TableMappings.AddRange(tableMappings);
            // If set the AcceptChangesDuringFill as the false, AcceptChanges will not be called on a
            // DataRow after it is added to the DataTable during any of the Fill operations.
            adapter.AcceptChangesDuringFill = false;

            adapter.Fill(dataSet);
         }
      }
   }

   // Roll back only one column or several columns data of the Course table by call ResetDataTable method.
   private static void ResetCourse(DataTable table, String connectionString,
       DataColumn[] primaryColumns, DataColumn[] resetColumns) {
      table.PrimaryKey = primaryColumns;

      // Build the query string
      String primaryCols = String.Join(",", primaryColumns.Select(col => col.ColumnName));
      String resetCols = String.Join(",", resetColumns.Select(col => $"Max({col.ColumnName}) as {col.ColumnName}"));

      String selectString = $"Select {primaryCols},{resetCols} from Course Group by {primaryCols}");

      SqlCommand selectCommand = new SqlCommand(selectString);

      ResetDataTable(table, connectionString, selectCommand);
   }

   // RejectChanges will roll back all changes made to the table since it was loaded, or the last time AcceptChanges
   // was called. When you copy from the database, you can lose all the data after calling RejectChanges
   // The ResetDataTable method rolls back one or more columns of data.
   private static void ResetDataTable(DataTable table, String connectionString,
       SqlCommand selectCommand) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         selectCommand.Connection = connection;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {
            // The incoming values for this row will be written to the current version of each
            // column. The original version of each column's data will not be changed.
            adapter.FillLoadOption = LoadOption.Upsert;

            adapter.Fill(table);
         }
      }
   }

   private static void BatchInsertUpdate(DataTable table, String connectionString,
       SqlCommand insertCommand, Int32 batchSize) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         insertCommand.Connection = connection;
         // When setting UpdateBatchSize to a value other than 1, all the commands
         // associated with the SqlDataAdapter have to have their UpdatedRowSource
         // property set to None or OutputParameters. An exception is thrown otherwise.
         insertCommand.UpdatedRowSource = UpdateRowSource.None;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter()) {
            adapter.InsertCommand = insertCommand;
            // Gets or sets the number of rows that are processed in each round-trip to the server.
            // Setting it to 1 disables batch updates, as rows are sent one at a time.
            adapter.UpdateBatchSize = batchSize;

            adapter.Update(table);

            Console.WriteLine("Successfully to update the table.");
         }
      }
   }

   private static void ShowDataTable(DataTable table) {
      foreach (DataColumn col in table.Columns) {
         Console.Write("{0,-14}", col.ColumnName);
      }
      Console.WriteLine("{0,-14}", "RowState");

      foreach (DataRow row in table.Rows) {
         foreach (DataColumn col in table.Columns) {
            if (col.DataType.Equals(typeof(DateTime)))
               Console.Write("{0,-14:d}", row[col]);
            else if (col.DataType.Equals(typeof(Decimal)))
               Console.Write("{0,-14:C}", row[col]);
            else
               Console.Write("{0,-14}", row[col]);
         }
         Console.WriteLine("{0,-14}", row.RowState);
      }
   }
}
```

## <a name="see-also"></a><span data-ttu-id="8e800-178">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8e800-178">See also</span></span>

- [<span data-ttu-id="8e800-179">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="8e800-179">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="8e800-180">行状态和行版本</span><span class="sxs-lookup"><span data-stu-id="8e800-180">Row States and Row Versions</span></span>](./dataset-datatable-dataview/row-states-and-row-versions.md)
- [<span data-ttu-id="8e800-181">AcceptChange 和 RejectChange</span><span class="sxs-lookup"><span data-stu-id="8e800-181">AcceptChanges and RejectChanges</span></span>](./dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [<span data-ttu-id="8e800-182">合并数据集内容</span><span class="sxs-lookup"><span data-stu-id="8e800-182">Merging DataSet Contents</span></span>](./dataset-datatable-dataview/merging-dataset-contents.md)
- [<span data-ttu-id="8e800-183">检索标识或自动编号值</span><span class="sxs-lookup"><span data-stu-id="8e800-183">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)
- [<span data-ttu-id="8e800-184">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="8e800-184">ADO.NET Overview</span></span>](ado-net-overview.md)
