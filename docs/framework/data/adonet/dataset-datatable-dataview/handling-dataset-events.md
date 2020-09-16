---
title: 处理数据集事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
ms.openlocfilehash: 0f79b97b486bbc3e1150cd6aff8162d37134f62e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557991"
---
# <a name="handling-dataset-events"></a><span data-ttu-id="d0223-102">处理数据集事件</span><span class="sxs-lookup"><span data-stu-id="d0223-102">Handling DataSet Events</span></span>
<span data-ttu-id="d0223-103"><xref:System.Data.DataSet> 对象提供三个事件： <xref:System.ComponentModel.MarshalByValueComponent.Disposed>、 <xref:System.Data.DataSet.Initialized>和 <xref:System.Data.DataSet.MergeFailed>。</span><span class="sxs-lookup"><span data-stu-id="d0223-103">The <xref:System.Data.DataSet> object provides three events: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, and <xref:System.Data.DataSet.MergeFailed>.</span></span>  
  
## <a name="the-mergefailed-event"></a><span data-ttu-id="d0223-104">MergeFailed 事件</span><span class="sxs-lookup"><span data-stu-id="d0223-104">The MergeFailed Event</span></span>  
 <span data-ttu-id="d0223-105">`DataSet` 对象的最常用事件是 `MergeFailed`，当要合并的 `DataSet` 对象的架构发生冲突时，会引发该事件。</span><span class="sxs-lookup"><span data-stu-id="d0223-105">The most commonly used event of the `DataSet` object is `MergeFailed`, which is raised when the schema of the `DataSet` objects being merged are in conflict.</span></span> <span data-ttu-id="d0223-106">当目标和源 <xref:System.Data.DataRow> 有相同的主键值，且 <xref:System.Data.DataSet.EnforceConstraints%2A> 属性设置为 `true`时会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="d0223-106">This occurs when a target and source <xref:System.Data.DataRow> have the same primary key value, and the <xref:System.Data.DataSet.EnforceConstraints%2A> property is set to `true`.</span></span> <span data-ttu-id="d0223-107">例如，如果所合并表的主键列与两个 `DataSet` 对象中的表的相同，则将发生异常并引发 `MergeFailed` 事件。</span><span class="sxs-lookup"><span data-stu-id="d0223-107">For example, if the primary key columns of a table being merged are the same between the tables in the two `DataSet` objects, an exception is thrown and the `MergeFailed` event is raised.</span></span> <span data-ttu-id="d0223-108">传递给 <xref:System.Data.MergeFailedEventArgs> 事件的 `MergeFailed` 对象具有 <xref:System.Data.MergeFailedEventArgs.Conflict%2A> 属性（标识两个 `DataSet` 对象之间的架构冲突）和 <xref:System.Data.MergeFailedEventArgs.Table%2A> 属性（标识发生冲突的表的名称）。</span><span class="sxs-lookup"><span data-stu-id="d0223-108">The <xref:System.Data.MergeFailedEventArgs> object passed to the `MergeFailed` event have a <xref:System.Data.MergeFailedEventArgs.Conflict%2A> property that identifies the conflict in schema between the two `DataSet` objects, and a <xref:System.Data.MergeFailedEventArgs.Table%2A> property that identifies the name of the table in conflict.</span></span>  
  
 <span data-ttu-id="d0223-109">下面的代码段演示如何为 `MergeFailed` 事件添加事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="d0223-109">The following code fragment demonstrates how to add an event handler for the `MergeFailed` event.</span></span>  
  
```vb  
AddHandler workDS.MergeFailed, New MergeFailedEventHandler( _  
  AddressOf DataSetMergeFailed)  
  
Private Shared Sub DataSetMergeFailed(  _  
  sender As Object,args As MergeFailedEventArgs)  
  Console.WriteLine("Merge failed for table " & args.Table.TableName)  
  Console.WriteLine("Conflict = " & args.Conflict)  
End Sub  
```  
  
```csharp  
workDS.MergeFailed += new MergeFailedEventHandler(DataSetMergeFailed);  
  
private static void DataSetMergeFailed(  
  object sender, MergeFailedEventArgs args)  
{  
  Console.WriteLine("Merge failed for table " + args.Table.TableName);  
  Console.WriteLine("Conflict = " + args.Conflict);  
}  
```  
  
## <a name="the-initialized-event"></a><span data-ttu-id="d0223-110">初始化事件</span><span class="sxs-lookup"><span data-stu-id="d0223-110">The Initialized Event</span></span>  
 <span data-ttu-id="d0223-111">在 <xref:System.Data.DataSet.Initialized> 构造函数初始化 `DataSet` 的新实例后会发生 `DataSet`事件。</span><span class="sxs-lookup"><span data-stu-id="d0223-111">The <xref:System.Data.DataSet.Initialized> event occurs after the `DataSet` constructor initializes a new instance of the `DataSet`.</span></span>  
  
 <span data-ttu-id="d0223-112">如果 <xref:System.Data.DataSet.IsInitialized%2A> 已完成初始化， `true` 属性会返回 `DataSet` ；否则，返回 `false`。</span><span class="sxs-lookup"><span data-stu-id="d0223-112">The <xref:System.Data.DataSet.IsInitialized%2A> property returns `true` if the `DataSet` has completed initialization; otherwise it returns `false`.</span></span> <span data-ttu-id="d0223-113"><xref:System.Data.DataSet.BeginInit%2A> 方法，它开始初始化 `DataSet`，将 <xref:System.Data.DataSet.IsInitialized%2A> 设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="d0223-113">The <xref:System.Data.DataSet.BeginInit%2A> method, which begins the initialization of a `DataSet`, sets <xref:System.Data.DataSet.IsInitialized%2A> to `false`.</span></span> <span data-ttu-id="d0223-114"><xref:System.Data.DataSet.EndInit%2A> 方法（用于结束 `DataSet`的初始化）将它设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="d0223-114">The <xref:System.Data.DataSet.EndInit%2A> method, which ends the initialization of the `DataSet`, sets it to `true`.</span></span> <span data-ttu-id="d0223-115">Visual Studio 设计环境使用这些方法初始化 `DataSet` 其他组件使用的。</span><span class="sxs-lookup"><span data-stu-id="d0223-115">These methods are used by the Visual Studio design environment to initialize a `DataSet` that is being used by another component.</span></span> <span data-ttu-id="d0223-116">通常不会在代码中使用这些方法。</span><span class="sxs-lookup"><span data-stu-id="d0223-116">You will not commonly use them in your code.</span></span>  
  
## <a name="the-disposed-event"></a><span data-ttu-id="d0223-117">释放事件</span><span class="sxs-lookup"><span data-stu-id="d0223-117">The Disposed Event</span></span>  
 <span data-ttu-id="d0223-118">`DataSet` 派生自 <xref:System.ComponentModel.MarshalByValueComponent> 类，该类可公开 <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> 方法和 <xref:System.ComponentModel.MarshalByValueComponent.Disposed> 事件。</span><span class="sxs-lookup"><span data-stu-id="d0223-118">`DataSet` is derived from the <xref:System.ComponentModel.MarshalByValueComponent> class, which exposes both the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method and the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event.</span></span> <span data-ttu-id="d0223-119"><xref:System.ComponentModel.MarshalByValueComponent.Disposed>事件添加事件处理程序以侦听组件上已释放的事件。</span><span class="sxs-lookup"><span data-stu-id="d0223-119">The <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event adds an event handler to listen to the disposed event on the component.</span></span> <span data-ttu-id="d0223-120"><xref:System.ComponentModel.MarshalByValueComponent.Disposed> `DataSet` 如果要在调用方法时执行代码，则可以使用的事件 <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> 。</span><span class="sxs-lookup"><span data-stu-id="d0223-120">You can use the <xref:System.ComponentModel.MarshalByValueComponent.Disposed> event of a `DataSet` if you want to execute code when the <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> method is called.</span></span> <span data-ttu-id="d0223-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> 释放由使用的资源 <xref:System.ComponentModel.MarshalByValueComponent> 。</span><span class="sxs-lookup"><span data-stu-id="d0223-121"><xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> releases the resources used by the <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0223-122">`DataSet`和 `DataTable` 对象从继承 <xref:System.ComponentModel.MarshalByValueComponent> 并且支持 <xref:System.Runtime.Serialization.ISerializable> 用于远程处理的接口。</span><span class="sxs-lookup"><span data-stu-id="d0223-122">The `DataSet` and `DataTable` objects inherit from <xref:System.ComponentModel.MarshalByValueComponent> and support the <xref:System.Runtime.Serialization.ISerializable> interface for remoting.</span></span> <span data-ttu-id="d0223-123">这两个对象是唯一可远程处理的 ADO.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="d0223-123">These are the only ADO.NET objects that can be remoted.</span></span> <span data-ttu-id="d0223-124">有关详细信息，请参阅 [.Net 远程处理](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="d0223-124">For more information, see [.NET Remoting](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100)).</span></span>  
  
 <span data-ttu-id="d0223-125">有关使用时的其他可用事件的信息 `DataSet` ，请参阅 [处理 DataTable 事件](handling-datatable-events.md) 和 [处理 DataAdapter 事件](../handling-dataadapter-events.md)。</span><span class="sxs-lookup"><span data-stu-id="d0223-125">For information about other events available when working with a `DataSet`, see [Handling DataTable Events](handling-datatable-events.md) and [Handling DataAdapter Events](../handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0223-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="d0223-126">See also</span></span>

- [<span data-ttu-id="d0223-127">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="d0223-127">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="d0223-128">[验证数据](/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="d0223-128">[Validating Data](/previous-versions/visualstudio/visual-studio-2013/t3b36awf(v=vs.120))</span></span>
- [<span data-ttu-id="d0223-129">在 ADO.NET 中检索和修改数据</span><span class="sxs-lookup"><span data-stu-id="d0223-129">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="d0223-130">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="d0223-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
