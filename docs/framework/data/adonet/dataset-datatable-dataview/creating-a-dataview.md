---
title: 创建数据视图
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 539e9763c8aa4affdb6f3bd219a99dbca50cee01
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202338"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="03d98-102">创建数据视图</span><span class="sxs-lookup"><span data-stu-id="03d98-102">Creating a DataView</span></span>

<span data-ttu-id="03d98-103">创建 <xref:System.Data.DataView> 的方法有两种。</span><span class="sxs-lookup"><span data-stu-id="03d98-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="03d98-104">您可以使用 **DataView** 构造函数，也可以创建对的属性的引用 <xref:System.Data.DataTable.DefaultView%2A> <xref:System.Data.DataTable> 。</span><span class="sxs-lookup"><span data-stu-id="03d98-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="03d98-105">**DataView**构造函数可以为空，也可以采用**datatable**作为单个参数，或将**datatable**与筛选条件、排序条件和行状态筛选器一起使用。</span><span class="sxs-lookup"><span data-stu-id="03d98-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="03d98-106">有关可用于 **DataView**的其他参数的详细信息，请参阅对 [数据进行排序和筛选](sorting-and-filtering-data.md)。</span><span class="sxs-lookup"><span data-stu-id="03d98-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="03d98-107">由于在创建**dataview**时以及在修改任何**sort**、 **RowFilter**或**RowStateFilter**属性时都会生成**dataview**的索引，因此在创建**dataview**时，通过将任何初始排序顺序或筛选条件作为构造函数参数提供，可以获得最佳性能。</span><span class="sxs-lookup"><span data-stu-id="03d98-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="03d98-108">如果在不指定排序或筛选条件的情况下创建 **DataView** ，然后设置 **sort**、 **RowFilter**或 **RowStateFilter** 属性，稍后将导致索引至少生成两次：创建 **dataview** 时，以及在修改任何排序或筛选属性时。</span><span class="sxs-lookup"><span data-stu-id="03d98-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="03d98-109">请注意，如果使用不采用任何参数的构造函数来创建**dataview** ，则在设置**表**属性之前，将无法使用**dataview** 。</span><span class="sxs-lookup"><span data-stu-id="03d98-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="03d98-110">下面的代码示例演示如何使用**dataview**构造函数创建**dataview** 。</span><span class="sxs-lookup"><span data-stu-id="03d98-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="03d98-111">**RowFilter**、 **Sort**列和**DataViewRowState**随**DataTable**一起提供。</span><span class="sxs-lookup"><span data-stu-id="03d98-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],
    "Country = 'USA'",
    "ContactName",
    DataViewRowState.CurrentRows);  
```  
  
 <span data-ttu-id="03d98-112">下面的代码示例演示如何使用表的**DefaultView**属性获取对**DataTable**的默认**DataView**的引用。</span><span class="sxs-lookup"><span data-stu-id="03d98-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="03d98-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="03d98-113">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="03d98-114">DataView</span><span class="sxs-lookup"><span data-stu-id="03d98-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="03d98-115">对数据进行排序和筛选</span><span class="sxs-lookup"><span data-stu-id="03d98-115">Sorting and Filtering Data</span></span>](sorting-and-filtering-data.md)
- [<span data-ttu-id="03d98-116">DataTables</span><span class="sxs-lookup"><span data-stu-id="03d98-116">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="03d98-117">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="03d98-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
