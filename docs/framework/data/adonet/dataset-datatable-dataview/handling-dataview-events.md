---
title: 处理数据视图事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5675663-fc91-4e0d-87a9-481b25b64c0f
ms.openlocfilehash: 2a67cb040c5d438d17ad91d41e97f24f3166262b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204536"
---
# <a name="handling-dataview-events"></a><span data-ttu-id="6c476-102">处理数据视图事件</span><span class="sxs-lookup"><span data-stu-id="6c476-102">Handling DataView Events</span></span>

<span data-ttu-id="6c476-103">可以使用 <xref:System.Data.DataView.ListChanged> 的 <xref:System.Data.DataView> 事件确定某个视图是否已更新。</span><span class="sxs-lookup"><span data-stu-id="6c476-103">You can use the <xref:System.Data.DataView.ListChanged> event of the <xref:System.Data.DataView> to determine if a view has been updated.</span></span> <span data-ttu-id="6c476-104">引发该事件的更新包括添加、删除或修改基础表中的某行；在基础表的架构中添加或删除某列；更改父或子关系。</span><span class="sxs-lookup"><span data-stu-id="6c476-104">Updates that raise the event include adding, deleting, or modifying a row in the underlying table; adding or deleting a column to the schema of the underlying table; and a change in a parent or child relationship.</span></span> <span data-ttu-id="6c476-105">如果要查看的行的列表由于应用了新的排序顺序或筛选器而发生了重大更改，则 **ListChanged** 事件也会通知您。</span><span class="sxs-lookup"><span data-stu-id="6c476-105">The **ListChanged** event also notifies you if the list of rows you are viewing has changed significantly due to the application of a new sort order or a filter.</span></span>  
  
 <span data-ttu-id="6c476-106">**ListChanged**事件实现命名空间的**ListChangedEventHandler**委托 <xref:System.ComponentModel> ，并将对象作为输入 <xref:System.ComponentModel.ListChangedEventArgs> 。</span><span class="sxs-lookup"><span data-stu-id="6c476-106">The **ListChanged** event implements the **ListChangedEventHandler** delegate of the <xref:System.ComponentModel> namespace and takes as input a <xref:System.ComponentModel.ListChangedEventArgs> object.</span></span> <span data-ttu-id="6c476-107">您可以使用 <xref:System.ComponentModel.ListChangedType> **ListChangedEventArgs**对象的**system.componentmodel.listchangedtype>** 属性中的枚举值确定发生的更改类型。</span><span class="sxs-lookup"><span data-stu-id="6c476-107">You can determine what type of change has occurred using the <xref:System.ComponentModel.ListChangedType> enumeration value in the **ListChangedType** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="6c476-108">对于涉及添加、删除或移动行的更改，可以使用**ListChangedEventArgs**对象的**NewIndex**属性来访问已添加或已移动的行和已删除行的上一索引的新索引。</span><span class="sxs-lookup"><span data-stu-id="6c476-108">For changes that involve adding, deleting, or moving rows, the new index of the added or moved row and the previous index of the deleted row can be accessed using the **NewIndex** property of the **ListChangedEventArgs** object.</span></span> <span data-ttu-id="6c476-109">在移动行的情况下，可以使用**ListChangedEventArgs**对象的**OldIndex**属性访问已移动行的上一个索引。</span><span class="sxs-lookup"><span data-stu-id="6c476-109">In the case of a moved row, the previous index of the moved row can be accessed using the **OldIndex** property of the **ListChangedEventArgs** object.</span></span>  
  
 <span data-ttu-id="6c476-110">**DataViewManager**还公开了一个**ListChanged**事件，以在表已添加或已删除或者是否对基础**数据集**的**关系**集合进行更改时通知您。</span><span class="sxs-lookup"><span data-stu-id="6c476-110">The **DataViewManager** also exposes a **ListChanged** event to notify you if a table has been added or removed, or if a change has been made to the **Relations** collection of the underlying **DataSet**.</span></span>  
  
 <span data-ttu-id="6c476-111">下面的代码示例演示如何添加 **ListChanged** 事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="6c476-111">The following code example shows how to add a **ListChanged** event handler.</span></span>  
  
```vb  
AddHandler custView.ListChanged, _  
  New System.ComponentModel.ListChangedEventHandler( _  
  AddressOf OnListChanged)  
  
Private Shared Sub OnListChanged( _  
  sender As Object, args As System.ComponentModel.ListChangedEventArgs)  
  Console.WriteLine("ListChanged:")  
  Console.WriteLine(vbTab & "    Type = " & _  
    System.Enum.GetName(args.ListChangedType.GetType(), _  
    args.ListChangedType))  
  Console.WriteLine(vbTab & "OldIndex = " & args.OldIndex)  
  Console.WriteLine(vbTab & "NewIndex = " & args.NewIndex)  
End Sub  
```  
  
```csharp  
custView.ListChanged  += new
  System.ComponentModel.ListChangedEventHandler(OnListChanged);  
  
protected static void OnListChanged(object sender,
  System.ComponentModel.ListChangedEventArgs args)  
{  
  Console.WriteLine("ListChanged:");  
  Console.WriteLine("\t    Type = " + args.ListChangedType);  
  Console.WriteLine("\tOldIndex = " + args.OldIndex);  
  Console.WriteLine("\tNewIndex = " + args.NewIndex);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c476-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="6c476-112">See also</span></span>

- <xref:System.Data.DataView>
- <xref:System.ComponentModel.ListChangedEventHandler>
- [<span data-ttu-id="6c476-113">DataView</span><span class="sxs-lookup"><span data-stu-id="6c476-113">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="6c476-114">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="6c476-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
