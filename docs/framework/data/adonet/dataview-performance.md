---
title: DataView 性能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: b2483becce31ab75d8b55b7a642c4ada83da59f6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183346"
---
# <a name="dataview-performance"></a><span data-ttu-id="7565e-102">DataView 性能</span><span class="sxs-lookup"><span data-stu-id="7565e-102">DataView Performance</span></span>

<span data-ttu-id="7565e-103">本主题讨论使用 <xref:System.Data.DataView.Find%2A> 类的 <xref:System.Data.DataView.FindRows%2A> 和 <xref:System.Data.DataView> 方法并在 Web 应用程序中缓存 <xref:System.Data.DataView> 时所具有的性能优势。</span><span class="sxs-lookup"><span data-stu-id="7565e-103">This topic discusses the performance benefits of using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView> class, and of caching a <xref:System.Data.DataView> in a Web application.</span></span>  
  
## <a name="find-and-findrows"></a><span data-ttu-id="7565e-104">Find 和 FindRows</span><span class="sxs-lookup"><span data-stu-id="7565e-104">Find and FindRows</span></span>  

 <span data-ttu-id="7565e-105"><xref:System.Data.DataView> 构造一个索引。</span><span class="sxs-lookup"><span data-stu-id="7565e-105"><xref:System.Data.DataView> constructs an index.</span></span> <span data-ttu-id="7565e-106">索引包含由表或视图中的一列或多列生成的键。</span><span class="sxs-lookup"><span data-stu-id="7565e-106">An index contains keys built from one or more columns in the table or view.</span></span> <span data-ttu-id="7565e-107">这些键存储在结构中，这种结构可使 <xref:System.Data.DataView> 能够快速有效地查找行或与键值关联的行。</span><span class="sxs-lookup"><span data-stu-id="7565e-107">These keys are stored in a structure that enables the <xref:System.Data.DataView> to find the row or rows associated with the key values quickly and efficiently.</span></span> <span data-ttu-id="7565e-108">使用索引的操作（如筛选和排序）会显著提高性能。</span><span class="sxs-lookup"><span data-stu-id="7565e-108">Operations that use the index, such as filtering and sorting, see significant performance increases.</span></span> <span data-ttu-id="7565e-109">创建 <xref:System.Data.DataView> 及修改任何排序或筛选信息时，均会生成 <xref:System.Data.DataView> 的索引。</span><span class="sxs-lookup"><span data-stu-id="7565e-109">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="7565e-110">创建 <xref:System.Data.DataView> 然后设置排序或筛选信息会使索引生成至少两次：一次是在创建 <xref:System.Data.DataView> 时，另一次是在修改任何排序或筛选属性时。</span><span class="sxs-lookup"><span data-stu-id="7565e-110">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span> <span data-ttu-id="7565e-111">有关对进行筛选和排序的详细信息 <xref:System.Data.DataView> ，请参阅通过 [Dataview 进行筛选](filtering-with-dataview-linq-to-dataset.md) 和 [通过 dataview 进行排序](sorting-with-dataview-linq-to-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="7565e-111">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
 <span data-ttu-id="7565e-112">如果要返回特定数据查询的结果而不是提供数据子集的动态视图，则可以使用 <xref:System.Data.DataView.Find%2A> 的 <xref:System.Data.DataView.FindRows%2A> 或 <xref:System.Data.DataView> 方法，而不设置 <xref:System.Data.DataView.RowFilter%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="7565e-112">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="7565e-113"><xref:System.Data.DataView.RowFilter%2A> 属性最适合用于用绑定控件显示筛选结果的数据绑定应用程序。</span><span class="sxs-lookup"><span data-stu-id="7565e-113">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="7565e-114">设置 <xref:System.Data.DataView.RowFilter%2A> 属性会重新生成数据的索引，从而增加应用程序的系统开销并降低性能。</span><span class="sxs-lookup"><span data-stu-id="7565e-114">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="7565e-115"><xref:System.Data.DataView.Find%2A> 和 <xref:System.Data.DataView.FindRows%2A> 方法使用当前索引，而不要求重新生成索引。</span><span class="sxs-lookup"><span data-stu-id="7565e-115">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="7565e-116">如果只想调用 <xref:System.Data.DataView.Find%2A> 或 <xref:System.Data.DataView.FindRows%2A> 一次，则应使用现有的 <xref:System.Data.DataView>。</span><span class="sxs-lookup"><span data-stu-id="7565e-116">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="7565e-117">如果想要调用 <xref:System.Data.DataView.Find%2A> 或 <xref:System.Data.DataView.FindRows%2A> 多次，则应该创建一个新的 <xref:System.Data.DataView> 以便对想要搜索的列重新生成索引，然后调用 <xref:System.Data.DataView.Find%2A> 或 <xref:System.Data.DataView.FindRows%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7565e-117">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="7565e-118">有关和方法的详细 <xref:System.Data.DataView.Find%2A> 信息 <xref:System.Data.DataView.FindRows%2A> ，请参阅 [查找行](./dataset-datatable-dataview/finding-rows.md)。</span><span class="sxs-lookup"><span data-stu-id="7565e-118">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods, see [Finding Rows](./dataset-datatable-dataview/finding-rows.md).</span></span>  
  
 <span data-ttu-id="7565e-119">下面的示例使用 <xref:System.Data.DataView.Find%2A> 方法来查找姓氏为“Zhu”的联系人。</span><span class="sxs-lookup"><span data-stu-id="7565e-119">The following example uses the <xref:System.Data.DataView.Find%2A> method to find a contact with the last name "Zhu".</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 <span data-ttu-id="7565e-120">下面的示例使用 <xref:System.Data.DataView.FindRows%2A> 方法来查找所有红颜色的产品。</span><span class="sxs-lookup"><span data-stu-id="7565e-120">The following example uses the <xref:System.Data.DataView.FindRows%2A> method to find all the red colored products.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a><span data-ttu-id="7565e-121">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7565e-121">ASP.NET</span></span>  

 <span data-ttu-id="7565e-122">ASP.NET 具有一种缓存机制，允许您在内存中存储需要创建大量服务器资源的对象。</span><span class="sxs-lookup"><span data-stu-id="7565e-122">ASP.NET has a caching mechanism that allows you to store objects that require extensive server resources to create in memory.</span></span> <span data-ttu-id="7565e-123">缓存这些类型的资源可以显著提高应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="7565e-123">Caching these types of resources can significantly improve the performance of your application.</span></span> <span data-ttu-id="7565e-124">缓存由 <xref:System.Web.Caching.Cache> 类实现，缓存实例专用于每个应用程序。</span><span class="sxs-lookup"><span data-stu-id="7565e-124">Caching is implemented by the <xref:System.Web.Caching.Cache> class, with cache instances that are private to each application.</span></span> <span data-ttu-id="7565e-125">由于创建新的 <xref:System.Data.DataView> 对象需要大量资源，因此你可能希望在 Web 应用程序中使用此缓存功能，使得每次刷新网页时，不必重新生成 <xref:System.Data.DataView>。</span><span class="sxs-lookup"><span data-stu-id="7565e-125">Because creating a new <xref:System.Data.DataView> object can be resource intensive, you might want to use this caching functionality in Web applications so that the <xref:System.Data.DataView> does not have to be rebuilt every time the Web page is refreshed.</span></span>  
  
 <span data-ttu-id="7565e-126">在下面的示例中，对 <xref:System.Data.DataView> 进行缓存以便在刷新该页时不必对数据重新排序。</span><span class="sxs-lookup"><span data-stu-id="7565e-126">In the following example, the <xref:System.Data.DataView> is cached so that the data does not have to be re-sorted when the page is refreshed.</span></span>  
  
```vb  
If (Cache("ordersView") = Nothing) Then  
  
Dim dataSet As New DataSet()  
  
   FillDataSet(dataSet)  
  
   Dim orders As DataTable = dataSet.Tables("SalesOrderHeader")  
  
   Dim query = _  
                    From order In orders.AsEnumerable() _  
                    Where order.Field(Of Boolean)("OnlineOrderFlag") = True _  
                    Order By order.Field(Of Decimal)("TotalDue") _  
                    Select order  
  
   Dim view As DataView = query.AsDataView()  
  
   Cache.Insert("ordersView", view)  
  
End If  
  
Dim ordersView = CType(Cache("ordersView"), DataView)  
  
GridView1.DataSource = ordersView  
GridView1.DataBind()  
```  
  
```csharp  
if (Cache["ordersView"] == null)  
{  
   // Fill the DataSet.
   DataSet dataSet = FillDataSet();  
  
   DataTable orders = dataSet.Tables["SalesOrderHeader"];  
  
   EnumerableRowCollection<DataRow> query =  
                        from order in orders.AsEnumerable()  
                        where order.Field<bool>("OnlineOrderFlag") == true  
                        orderby order.Field<decimal>("TotalDue")  
                        select order;  
  
   DataView view = query.AsDataView();  
   Cache.Insert("ordersView", view);  
}  
  
DataView ordersView = (DataView)Cache["ordersView"];  
  
GridView1.DataSource = ordersView;  
GridView1.DataBind();  
```  
  
## <a name="see-also"></a><span data-ttu-id="7565e-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="7565e-127">See also</span></span>

- [<span data-ttu-id="7565e-128">数据绑定和 LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="7565e-128">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
