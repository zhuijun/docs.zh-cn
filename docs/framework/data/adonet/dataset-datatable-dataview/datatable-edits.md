---
title: 数据表编辑
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 4fdb19e7fa014bf4a7c924b1fbae53fa44de6e3c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153256"
---
# <a name="datatable-edits"></a><span data-ttu-id="1cb0a-102">数据表编辑</span><span class="sxs-lookup"><span data-stu-id="1cb0a-102">DataTable Edits</span></span>

<span data-ttu-id="1cb0a-103">当您在 <xref:System.Data.DataRow> 中更改列值时，所做更改会立即置于行的当前状态中。</span><span class="sxs-lookup"><span data-stu-id="1cb0a-103">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="1cb0a-104">然后，将 <xref:System.Data.DataRowState> 设置为 "**已修改**"，并使用 DataRow 的或方法来接受或拒绝更改 <xref:System.Data.DataRow.AcceptChanges%2A> <xref:System.Data.DataRow.RejectChanges%2A> 。 **DataRow**</span><span class="sxs-lookup"><span data-stu-id="1cb0a-104">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="1cb0a-105">**DataRow**还提供了三种方法，可用于在编辑行时挂起行的状态。</span><span class="sxs-lookup"><span data-stu-id="1cb0a-105">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="1cb0a-106">这三个方法是 <xref:System.Data.DataRow.BeginEdit%2A>、<xref:System.Data.DataRow.EndEdit%2A> 和 <xref:System.Data.DataRow.CancelEdit%2A>。</span><span class="sxs-lookup"><span data-stu-id="1cb0a-106">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="1cb0a-107">当直接在 **datarow** 中修改列值时， **Datarow** 会使用 **Current**、 **Default**和 **原始** 行版本来管理列值。</span><span class="sxs-lookup"><span data-stu-id="1cb0a-107">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="1cb0a-108">除了这些行版本之外， **BeginEdit**、 **EndEdit**和 **CancelEdit** 方法使用第四个行版本： "已 **建议**"。</span><span class="sxs-lookup"><span data-stu-id="1cb0a-108">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="1cb0a-109">有关行版本的详细信息，请参阅 [行状态和行版本](row-states-and-row-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="1cb0a-109">For more information about row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="1cb0a-110">**建议**的行版本在编辑操作期间存在，该操作通过调用**BeginEdit**开始，并通过使用**EndEdit**或**CancelEdit**或通过调用**AcceptChanges**或**RejectChanges**结束。</span><span class="sxs-lookup"><span data-stu-id="1cb0a-110">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="1cb0a-111">在编辑操作期间，可以通过在**DataTable**的**ColumnChanged**事件中计算**ProposedValue** ，将验证逻辑应用于单个列。</span><span class="sxs-lookup"><span data-stu-id="1cb0a-111">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="1cb0a-112">**ColumnChanged**事件保存**DataColumnChangeEventArgs** ，可保持对正在更改的列和**ProposedValue**的引用。</span><span class="sxs-lookup"><span data-stu-id="1cb0a-112">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="1cb0a-113">计算了建议值后，可以对其进行修改或取消编辑。</span><span class="sxs-lookup"><span data-stu-id="1cb0a-113">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="1cb0a-114">当编辑结束时，该行将移出 **建议** 状态。</span><span class="sxs-lookup"><span data-stu-id="1cb0a-114">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="1cb0a-115">可以通过调用 **EndEdit**来确认编辑，也可以通过调用 **CancelEdit**来取消编辑。</span><span class="sxs-lookup"><span data-stu-id="1cb0a-115">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="1cb0a-116">请注意，尽管**EndEdit**确认了您的编辑，但在调用**AcceptChanges**之前，**数据集**并不会实际接受更改。</span><span class="sxs-lookup"><span data-stu-id="1cb0a-116">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="1cb0a-117">另请注意，如果在使用**EndEdit**或**CancelEdit**结束编辑之前调用**AcceptChanges** ，编辑将结束，同时将为**当前**行版本和**原始**行版本接受**建议**的行值。</span><span class="sxs-lookup"><span data-stu-id="1cb0a-117">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="1cb0a-118">同样，调用 **RejectChanges** 会结束编辑并放弃 **当前** 和 **建议** 的行版本。</span><span class="sxs-lookup"><span data-stu-id="1cb0a-118">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="1cb0a-119">调用**AcceptChanges**或**RejectChanges**后，调用**EndEdit**或**CancelEdit**不起作用，因为编辑已结束。</span><span class="sxs-lookup"><span data-stu-id="1cb0a-119">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="1cb0a-120">下面的示例演示如何将 **BeginEdit** 与 **EndEdit** 和 **CancelEdit**一起使用。</span><span class="sxs-lookup"><span data-stu-id="1cb0a-120">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="1cb0a-121">该示例还检查**ColumnChanged**事件中的**ProposedValue** ，并决定是否取消编辑。</span><span class="sxs-lookup"><span data-stu-id="1cb0a-121">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable  
workTable.Columns.Add("LastName", Type.GetType("System.String"))  
  
AddHandler workTable.ColumnChanged, _  
  New DataColumnChangeEventHandler(AddressOf OnColumnChanged)  
  
Dim workRow As DataRow = workTable.NewRow()  
workRow(0) = "Smith"  
workTable.Rows.Add(workRow)  
  
workRow.BeginEdit()  
' Causes the ColumnChanged event to write a message and cancel the edit.  
workRow(0) = ""
workRow.EndEdit()  
  
' Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow(0), workRow.RowState)  
  
Private Shared Sub OnColumnChanged( _  
  sender As Object, args As DataColumnChangeEventArgs)  
  If args.Column.ColumnName = "LastName" Then  
    If args.ProposedValue.ToString() = "" Then  
      Console.WriteLine("Last Name cannot be blank.  Edit canceled.")  
      args.Row.CancelEdit()  
    End If  
  End If  
End Sub  
```  
  
```csharp  
DataTable workTable  = new DataTable();  
workTable.Columns.Add("LastName", typeof(String));  
  
workTable.ColumnChanged +=
  new DataColumnChangeEventHandler(OnColumnChanged);  
  
DataRow workRow = workTable.NewRow();  
workRow[0] = "Smith";  
workTable.Rows.Add(workRow);  
  
workRow.BeginEdit();  
// Causes the ColumnChanged event to write a message and cancel the edit.  
workRow[0] = "";
workRow.EndEdit();  
  
// Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow[0], workRow.RowState);
  
protected static void OnColumnChanged(  
  Object sender, DataColumnChangeEventArgs args)  
{  
  if (args.Column.ColumnName == "LastName")  
    if (args.ProposedValue.ToString() == "")  
    {  
      Console.WriteLine("Last Name cannot be blank. Edit canceled.");  
      args.Row.CancelEdit();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1cb0a-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="1cb0a-122">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [<span data-ttu-id="1cb0a-123">操作数据表中的数据</span><span class="sxs-lookup"><span data-stu-id="1cb0a-123">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="1cb0a-124">处理数据表事件</span><span class="sxs-lookup"><span data-stu-id="1cb0a-124">Handling DataTable Events</span></span>](handling-datatable-events.md)
- [<span data-ttu-id="1cb0a-125">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="1cb0a-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
