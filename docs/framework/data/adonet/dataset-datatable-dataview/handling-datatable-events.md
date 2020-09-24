---
title: 处理数据表事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
ms.openlocfilehash: c00e5e42508160a210d16f058c46afbf62ae0ee0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164722"
---
# <a name="handling-datatable-events"></a><span data-ttu-id="f36a1-102">处理数据表事件</span><span class="sxs-lookup"><span data-stu-id="f36a1-102">Handling DataTable Events</span></span>

<span data-ttu-id="f36a1-103"><xref:System.Data.DataTable> 对象提供一系列可以由应用程序处理的事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-103">The <xref:System.Data.DataTable> object provides a series of events that can be processed by an application.</span></span> <span data-ttu-id="f36a1-104">下表描述了 `DataTable` 事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-104">The following table describes `DataTable` events.</span></span>  
  
|<span data-ttu-id="f36a1-105">事件</span><span class="sxs-lookup"><span data-stu-id="f36a1-105">Event</span></span>|<span data-ttu-id="f36a1-106">描述</span><span class="sxs-lookup"><span data-stu-id="f36a1-106">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.Initialized>|<span data-ttu-id="f36a1-107">在调用 <xref:System.Data.DataTable.EndInit%2A> 的 `DataTable` 方法后发生。</span><span class="sxs-lookup"><span data-stu-id="f36a1-107">Occurs after the <xref:System.Data.DataTable.EndInit%2A> method of a `DataTable` is called.</span></span> <span data-ttu-id="f36a1-108">此事件主要用于支持设计时方案。</span><span class="sxs-lookup"><span data-stu-id="f36a1-108">This event is intended primarily to support design-time scenarios.</span></span>|  
|<xref:System.Data.DataTable.ColumnChanged>|<span data-ttu-id="f36a1-109">在成功更改 <xref:System.Data.DataColumn> 中的值后发生。</span><span class="sxs-lookup"><span data-stu-id="f36a1-109">Occurs after a value has been successfully changed in a <xref:System.Data.DataColumn>.</span></span>|  
|<xref:System.Data.DataTable.ColumnChanging>|<span data-ttu-id="f36a1-110">提交 `DataColumn` 的值后发生。</span><span class="sxs-lookup"><span data-stu-id="f36a1-110">Occurs when a value has been submitted for a `DataColumn`.</span></span>|  
|<xref:System.Data.DataTable.RowChanged>|<span data-ttu-id="f36a1-111">在成功更改 `DataColumn` 值或 <xref:System.Data.DataRow.RowState%2A> 中 <xref:System.Data.DataRow> 的 `DataTable` 后发生。</span><span class="sxs-lookup"><span data-stu-id="f36a1-111">Occurs after a `DataColumn` value or the <xref:System.Data.DataRow.RowState%2A> of a <xref:System.Data.DataRow> in the `DataTable` has been changed successfully.</span></span>|  
|<xref:System.Data.DataTable.RowChanging>|<span data-ttu-id="f36a1-112">在提交对 `DataColumn` 值或 `RowState` 中 `DataRow` 的 `DataTable` 的更改后发生。</span><span class="sxs-lookup"><span data-stu-id="f36a1-112">Occurs when a change has been submitted for a `DataColumn` value or the `RowState` of a `DataRow` in the `DataTable`.</span></span>|  
|<xref:System.Data.DataTable.RowDeleted>|<span data-ttu-id="f36a1-113">在 `DataRow` 中的 `DataTable` 已标记为 `Deleted` 后发生。</span><span class="sxs-lookup"><span data-stu-id="f36a1-113">Occurs after a `DataRow` in the `DataTable` has been marked as `Deleted`.</span></span>|  
|<xref:System.Data.DataTable.RowDeleting>|<span data-ttu-id="f36a1-114">在 `DataRow` 中的 `DataTable` 标记为 `Deleted` 前发生。</span><span class="sxs-lookup"><span data-stu-id="f36a1-114">Occurs before a `DataRow` in the `DataTable` is marked as `Deleted`.</span></span>|  
|<xref:System.Data.DataTable.TableCleared>|<span data-ttu-id="f36a1-115">在对 <xref:System.Data.DataTable.Clear%2A> 的 `DataTable` 方法的调用已成功清除每个 `DataRow` 后发生。</span><span class="sxs-lookup"><span data-stu-id="f36a1-115">Occurs after a call to the <xref:System.Data.DataTable.Clear%2A> method of the `DataTable` has successfully cleared every `DataRow`.</span></span>|  
|<xref:System.Data.DataTable.TableClearing>|<span data-ttu-id="f36a1-116">在调用 `Clear` 方法后，开始执行 `Clear` 操作前发生。</span><span class="sxs-lookup"><span data-stu-id="f36a1-116">Occurs after the `Clear` method is called but before the `Clear` operation begins.</span></span>|  
|<xref:System.Data.DataTable.TableNewRow>|<span data-ttu-id="f36a1-117">在对 `DataRow` 的 `NewRow` 方法的调用创建了新 `DataTable` 后发生。</span><span class="sxs-lookup"><span data-stu-id="f36a1-117">Occurs after a new `DataRow` is created by a call to the `NewRow` method of the `DataTable`.</span></span>|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|<span data-ttu-id="f36a1-118">在 `DataTable` 被 `Disposed` 时发生。</span><span class="sxs-lookup"><span data-stu-id="f36a1-118">Occurs when the `DataTable` is `Disposed`.</span></span> <span data-ttu-id="f36a1-119">从 <xref:System.ComponentModel.MarshalByValueComponent> 继承。</span><span class="sxs-lookup"><span data-stu-id="f36a1-119">Inherited from <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="f36a1-120">添加或删除行的大多数操作不会引发 `ColumnChanged` 和 `ColumnChanging` 事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-120">Most operations that add or delete rows do not raise the `ColumnChanged` and `ColumnChanging` events.</span></span> <span data-ttu-id="f36a1-121">但是，当要读取的 XML 文档为 `ReadXml` 时，除非将 `ColumnChanged` 设置为 `ColumnChanging` 或 `XmlReadMode`，否则 `DiffGram` 方法会引发 `Auto` 和 `DiffGram` 事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-121">However, the `ReadXml` method does raise `ColumnChanged` and `ColumnChanging` events, unless the `XmlReadMode` is set to `DiffGram` or is set to `Auto` when the XML document being read is a `DiffGram`.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="f36a1-122">如果在从中引发 `DataSet` 事件的 `RowChanged` 中修改数据，则会发生数据损坏。</span><span class="sxs-lookup"><span data-stu-id="f36a1-122">Data corruption can occur if data is modified in a `DataSet` from which the `RowChanged` event is raised.</span></span> <span data-ttu-id="f36a1-123">出现这类数据损坏并不会引发任何异常。</span><span class="sxs-lookup"><span data-stu-id="f36a1-123">No exception will be raised if such data corruption occurs.</span></span>  
  
## <a name="additional-related-events"></a><span data-ttu-id="f36a1-124">其他相关事件</span><span class="sxs-lookup"><span data-stu-id="f36a1-124">Additional Related Events</span></span>  

 <span data-ttu-id="f36a1-125"><xref:System.Data.DataTable.Constraints%2A> 属性包含 <xref:System.Data.ConstraintCollection> 实例。</span><span class="sxs-lookup"><span data-stu-id="f36a1-125">The <xref:System.Data.DataTable.Constraints%2A> property holds a <xref:System.Data.ConstraintCollection> instance.</span></span> <span data-ttu-id="f36a1-126"><xref:System.Data.ConstraintCollection> 类会公开 <xref:System.Data.ConstraintCollection.CollectionChanged> 事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-126">The <xref:System.Data.ConstraintCollection> class exposes a <xref:System.Data.ConstraintCollection.CollectionChanged> event.</span></span> <span data-ttu-id="f36a1-127">在 `ConstraintCollection` 中添加、修改约束，或从中删除约束时，会激发此事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-127">This event fires when a constraint is added, modified, or removed from the `ConstraintCollection`.</span></span>  
  
 <span data-ttu-id="f36a1-128"><xref:System.Data.DataTable.Columns%2A> 属性包含 <xref:System.Data.DataColumnCollection> 实例。</span><span class="sxs-lookup"><span data-stu-id="f36a1-128">The <xref:System.Data.DataTable.Columns%2A> property holds a <xref:System.Data.DataColumnCollection> instance.</span></span> <span data-ttu-id="f36a1-129">`DataColumnCollection` 类会公开 <xref:System.Data.DataColumnCollection.CollectionChanged> 事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-129">The `DataColumnCollection` class exposes a <xref:System.Data.DataColumnCollection.CollectionChanged> event.</span></span> <span data-ttu-id="f36a1-130">在 `DataColumn` 中添加、修改或从中删除 `DataColumnCollection` 时，会激发此事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-130">This event fires when a `DataColumn` is added, modified, or removed from the `DataColumnCollection`.</span></span> <span data-ttu-id="f36a1-131">导致激发此事件的修改包括更改列的名称、类型、表达式或序号位置。</span><span class="sxs-lookup"><span data-stu-id="f36a1-131">Modifications that cause the event to fire include changes to the name, type, expression or ordinal position of a column.</span></span>  
  
 <span data-ttu-id="f36a1-132"><xref:System.Data.DataSet.Tables%2A> 的 <xref:System.Data.DataSet> 属性包含 <xref:System.Data.DataTableCollection> 实例。</span><span class="sxs-lookup"><span data-stu-id="f36a1-132">The <xref:System.Data.DataSet.Tables%2A> property of a <xref:System.Data.DataSet> holds a <xref:System.Data.DataTableCollection> instance.</span></span> <span data-ttu-id="f36a1-133">`DataTableCollection` 类会公开 `CollectionChanged` 和 `CollectionChanging` 事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-133">The `DataTableCollection` class exposes both a `CollectionChanged` and a `CollectionChanging` event.</span></span> <span data-ttu-id="f36a1-134">向 `DataTable` 中添加或从中删除 `DataSet` 时，会激发这两个事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-134">These events fire when a `DataTable` is added to or removed from the `DataSet`.</span></span>  
  
 <span data-ttu-id="f36a1-135">更改 `DataRows` 还会触发已关联 <xref:System.Data.DataView> 的事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-135">Changes to `DataRows` can also trigger events for an associated <xref:System.Data.DataView>.</span></span> <span data-ttu-id="f36a1-136">`DataView` 类会公开 <xref:System.Data.DataView.ListChanged> 事件，当 `DataColumn` 值发生更改或视图的撰写或排序顺序发生更改时会激发此事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-136">The `DataView` class exposes a <xref:System.Data.DataView.ListChanged> event that fires when a `DataColumn` value changes or when the composition or sort order of the view changes.</span></span> <span data-ttu-id="f36a1-137"><xref:System.Data.DataRowView> 类会公开 <xref:System.Data.DataRowView.PropertyChanged> 事件，当关联的 `DataColumn` 值发生更改时会激发此事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-137">The <xref:System.Data.DataRowView> class exposes a <xref:System.Data.DataRowView.PropertyChanged> event that fires when an associated `DataColumn` value changes.</span></span>  
  
## <a name="sequence-of-operations"></a><span data-ttu-id="f36a1-138">操作顺序</span><span class="sxs-lookup"><span data-stu-id="f36a1-138">Sequence of Operations</span></span>  

 <span data-ttu-id="f36a1-139">下面是添加、修改或删除 `DataRow` 时所执行操作的顺序：</span><span class="sxs-lookup"><span data-stu-id="f36a1-139">Here is the sequence of operations that occur when a `DataRow` is added, modified, or deleted:</span></span>  
  
1. <span data-ttu-id="f36a1-140">创建建议的记录并应用任何更改。</span><span class="sxs-lookup"><span data-stu-id="f36a1-140">Create the proposed record and apply any changes.</span></span>  
  
2. <span data-ttu-id="f36a1-141">检查非表达式列的约束。</span><span class="sxs-lookup"><span data-stu-id="f36a1-141">Check constraints for non-expression columns.</span></span>  
  
3. <span data-ttu-id="f36a1-142">如适用，引发 `RowChanging` 或 `RowDeleting` 事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-142">Raise the `RowChanging` or `RowDeleting` events as applicable.</span></span>  
  
4. <span data-ttu-id="f36a1-143">将建议的记录设置为当前记录。</span><span class="sxs-lookup"><span data-stu-id="f36a1-143">Set the proposed record to be the current record.</span></span>  
  
5. <span data-ttu-id="f36a1-144">更新任何关联的索引。</span><span class="sxs-lookup"><span data-stu-id="f36a1-144">Update any associated indexes.</span></span>  
  
6. <span data-ttu-id="f36a1-145">为关联的 `ListChanged` 对象引发 `DataView` 事件；为关联的 `PropertyChanged` 对象引发 `DataRowView` 事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-145">Raise `ListChanged` events for associated `DataView` objects and `PropertyChanged` events for associated `DataRowView` objects.</span></span>  
  
7. <span data-ttu-id="f36a1-146">计算所有表达式列，但延迟检查对这些列的任何约束。</span><span class="sxs-lookup"><span data-stu-id="f36a1-146">Evaluate all expression columns, but delay checking any constraints on these columns.</span></span>  
  
8. <span data-ttu-id="f36a1-147">为关联的 `ListChanged` 对象引发 `DataView` 事件；为受表达式列计算影响的 `PropertyChanged` 对象引发 `DataRowView` 事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-147">Raise `ListChanged` events for associated `DataView` objects and `PropertyChanged` events for associated `DataRowView` objects affected by the expression column evaluations.</span></span>  
  
9. <span data-ttu-id="f36a1-148">如适用，引发 `RowChanged` 或 `RowDeleted` 事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-148">Raise `RowChanged` or `RowDeleted` events as applicable.</span></span>  
  
10. <span data-ttu-id="f36a1-149">检查对表达式列的约束。</span><span class="sxs-lookup"><span data-stu-id="f36a1-149">Check constraints on expression columns.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f36a1-150">更改表达式列绝不会引发 `DataTable` 事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-150">Changes to expression columns never raise `DataTable` events.</span></span> <span data-ttu-id="f36a1-151">更改表达式列只会引发 `DataView` 和 `DataRowView` 事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-151">Changes to expression columns only raise `DataView` and `DataRowView` events.</span></span> <span data-ttu-id="f36a1-152">表达式列可与多个其他列存在相关性，并且在单个 `DataRow` 操作期间可计算多次。</span><span class="sxs-lookup"><span data-stu-id="f36a1-152">Expression columns can have dependencies on multiple other columns, and can be evaluated multiple times during a single `DataRow` operation.</span></span> <span data-ttu-id="f36a1-153">每个表达式计算都可引发事件，并且当表达式列受影响时，单个 `DataRow` 操作可引发多个 `ListChanged` 和 `PropertyChanged` 事件，其中可能包括同一表达式列的多个事件。</span><span class="sxs-lookup"><span data-stu-id="f36a1-153">Each expression evaluation raises events, and a single `DataRow` operation can raise multiple `ListChanged` and `PropertyChanged` events when expression columns are affected, possibly including multiple events for the same expression column.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="f36a1-154">请勿在 <xref:System.NullReferenceException> 事件处理程序中引发 `RowChanged`。</span><span class="sxs-lookup"><span data-stu-id="f36a1-154">Do not throw a <xref:System.NullReferenceException> within the `RowChanged` event handler.</span></span> <span data-ttu-id="f36a1-155">如果在 <xref:System.NullReferenceException> 的 `RowChanged` 事件中引发了 `DataTable`，`DataTable` 将被损坏。</span><span class="sxs-lookup"><span data-stu-id="f36a1-155">If a <xref:System.NullReferenceException> is thrown within the `RowChanged` event of a `DataTable`, then the `DataTable` will be corrupted.</span></span>  
  
### <a name="example"></a><span data-ttu-id="f36a1-156">示例</span><span class="sxs-lookup"><span data-stu-id="f36a1-156">Example</span></span>  

 <span data-ttu-id="f36a1-157">下面的示例演示如何为 `RowChanged`、`RowChanging`、`RowDeleted`、`RowDeleting`、`ColumnChanged`、`ColumnChanging`、`TableNewRow`、`TableCleared` 和 `TableClearing` 事件创建事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="f36a1-157">The following example demonstrates how to create event handlers for the `RowChanged`, `RowChanging`, `RowDeleted`, `RowDeleting`, `ColumnChanged`, `ColumnChanging`, `TableNewRow`, `TableCleared`, and `TableClearing` events.</span></span> <span data-ttu-id="f36a1-158">在激发每个事件处理程序时，都会在控制台窗口中显示相关输出。</span><span class="sxs-lookup"><span data-stu-id="f36a1-158">Each event handler displays output in the console window when it is fired.</span></span>  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f36a1-159">请参阅</span><span class="sxs-lookup"><span data-stu-id="f36a1-159">See also</span></span>

- [<span data-ttu-id="f36a1-160">操作数据表中的数据</span><span class="sxs-lookup"><span data-stu-id="f36a1-160">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="f36a1-161">处理 DataAdapter 事件</span><span class="sxs-lookup"><span data-stu-id="f36a1-161">Handling DataAdapter Events</span></span>](../handling-dataadapter-events.md)
- [<span data-ttu-id="f36a1-162">处理数据集事件</span><span class="sxs-lookup"><span data-stu-id="f36a1-162">Handling DataSet Events</span></span>](handling-dataset-events.md)
- [<span data-ttu-id="f36a1-163">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="f36a1-163">ADO.NET Overview</span></span>](../ado-net-overview.md)
