---
title: DataRow 删除
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 2092d7319a398bbdeaef764d677818f78ddf9de9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153347"
---
# <a name="datarow-deletion"></a><span data-ttu-id="82bb5-102">DataRow 删除</span><span class="sxs-lookup"><span data-stu-id="82bb5-102">DataRow Deletion</span></span>

<span data-ttu-id="82bb5-103">可以使用两种方法 <xref:System.Data.DataRow> 从对象中删除对象 <xref:System.Data.DataTable> ：对象的 **Remove** 方法 <xref:System.Data.DataRowCollection> 和 <xref:System.Data.DataRow.Delete%2A> **DataRow** 对象的方法。</span><span class="sxs-lookup"><span data-stu-id="82bb5-103">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="82bb5-104">此 <xref:System.Data.DataRowCollection.Remove%2A> 方法从**DataRowCollection**中删除**DataRow** ，而 <xref:System.Data.DataRow.Delete%2A> 方法仅将行标记为要删除。</span><span class="sxs-lookup"><span data-stu-id="82bb5-104">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="82bb5-105">当应用程序调用 **AcceptChanges** 方法时，将发生实际的删除。</span><span class="sxs-lookup"><span data-stu-id="82bb5-105">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="82bb5-106">通过使用 <xref:System.Data.DataRow.Delete%2A>，您可以在实际删除行之前，先以编程方式来检查哪些行已标记为删除。</span><span class="sxs-lookup"><span data-stu-id="82bb5-106">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="82bb5-107">如果将行标记为删除，则该行的 <xref:System.Data.DataRow.RowState%2A> 属性会设置为 <xref:System.Data.DataRow.Delete%2A>。</span><span class="sxs-lookup"><span data-stu-id="82bb5-107">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="82bb5-108">在 foreach 循环中，不会调用 <xref:System.Data.DataRow.Delete%2A> 和 <xref:System.Data.DataRowCollection.Remove%2A>，而是循环访问 <xref:System.Data.DataRowCollection> 对象。</span><span class="sxs-lookup"><span data-stu-id="82bb5-108">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="82bb5-109"><xref:System.Data.DataRow.Delete%2A> 和 <xref:System.Data.DataRowCollection.Remove%2A> 不会修改该集合的状态。</span><span class="sxs-lookup"><span data-stu-id="82bb5-109"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="82bb5-110">当将 <xref:System.Data.DataSet> 或**DataTable**与**DataAdapter**和关系数据源结合使用时，请使用**DataRow**的**Delete**方法删除该行。</span><span class="sxs-lookup"><span data-stu-id="82bb5-110">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="82bb5-111">**Delete**方法会将该行标记为**已**在**DataSet**或**DataTable**中删除，但不会将其删除。</span><span class="sxs-lookup"><span data-stu-id="82bb5-111">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="82bb5-112">相反，当 **DataAdapter** 遇到标记为 **已删除**的行时，它将执行其 **DeleteCommand** 方法以删除数据源中的行。</span><span class="sxs-lookup"><span data-stu-id="82bb5-112">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="82bb5-113">然后，可以使用 **AcceptChanges** 方法永久删除该行。</span><span class="sxs-lookup"><span data-stu-id="82bb5-113">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="82bb5-114">如果使用 " **删除** " 来删除该行，则会完全从表中删除行，但 **DataAdapter** 不会删除数据源中的行。</span><span class="sxs-lookup"><span data-stu-id="82bb5-114">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="82bb5-115">**DataRowCollection**的**Remove**方法采用**DataRow**作为参数，并将其从集合中移除，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="82bb5-115">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="82bb5-116">与此相反，下面的示例演示如何对**DataRow**调用**Delete**方法，以将其**RowState**更改为 "**已删除**"。</span><span class="sxs-lookup"><span data-stu-id="82bb5-116">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="82bb5-117">如果将某行标记为删除，并且调用**datatable**对象的**AcceptChanges**方法，则将从**datatable**中删除该行。</span><span class="sxs-lookup"><span data-stu-id="82bb5-117">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="82bb5-118">与此相反，如果调用 **RejectChanges**，则行的 **RowState** 会恢复为标记为 **已删除**之前的内容。</span><span class="sxs-lookup"><span data-stu-id="82bb5-118">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82bb5-119">如果**添加**了**DataRow**的**RowState** ，这意味着它刚刚添加到表中，然后将其标记为**已删除**，则会将其从表中删除。</span><span class="sxs-lookup"><span data-stu-id="82bb5-119">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82bb5-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="82bb5-120">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="82bb5-121">操作数据表中的数据</span><span class="sxs-lookup"><span data-stu-id="82bb5-121">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="82bb5-122">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="82bb5-122">ADO.NET Overview</span></span>](../ado-net-overview.md)
