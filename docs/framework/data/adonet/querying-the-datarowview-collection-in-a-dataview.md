---
title: 在 DataView 中查询 DataRowView 集合
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
ms.openlocfilehash: 5757079bbc0ef8c498ea1db1a88f6b356ab0409e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172744"
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a><span data-ttu-id="9903d-102">在 DataView 中查询 DataRowView 集合</span><span class="sxs-lookup"><span data-stu-id="9903d-102">Querying the DataRowView Collection in a DataView</span></span>

<span data-ttu-id="9903d-103"><xref:System.Data.DataView> 公开了 <xref:System.Data.DataRowView> 对象的可枚举集合。</span><span class="sxs-lookup"><span data-stu-id="9903d-103">The <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="9903d-104"><xref:System.Data.DataRowView> 表示 <xref:System.Data.DataRow> 的自定义视图，并在控件中显示特定版本的 <xref:System.Data.DataRow>。</span><span class="sxs-lookup"><span data-stu-id="9903d-104"><xref:System.Data.DataRowView> represents a customized view of a <xref:System.Data.DataRow> and displays a specific version of that <xref:System.Data.DataRow> in a control.</span></span> <span data-ttu-id="9903d-105">只有一种版本的 <xref:System.Data.DataRow> 可通过控件显示，例如 <xref:System.Windows.Forms.DataGridView>。</span><span class="sxs-lookup"><span data-stu-id="9903d-105">Only one version of a <xref:System.Data.DataRow> can be displayed through a control, such as a <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="9903d-106">您可以通过 <xref:System.Data.DataRow> 的 <xref:System.Data.DataRowView> 属性访问 <xref:System.Data.DataRowView.Row%2A> 公开的 <xref:System.Data.DataRowView>。</span><span class="sxs-lookup"><span data-stu-id="9903d-106">You can access the <xref:System.Data.DataRow> that is exposed by the <xref:System.Data.DataRowView> through the <xref:System.Data.DataRowView.Row%2A> property of the <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="9903d-107">当使用 <xref:System.Data.DataRowView> 查看值时，<xref:System.Data.DataView.RowStateFilter%2A> 属性决定公开基础 <xref:System.Data.DataRow> 的哪个行版本。</span><span class="sxs-lookup"><span data-stu-id="9903d-107">When you view values by using a <xref:System.Data.DataRowView>, the <xref:System.Data.DataView.RowStateFilter%2A> property determines which row version of the underlying <xref:System.Data.DataRow> is exposed.</span></span> <span data-ttu-id="9903d-108">有关使用访问不同行版本的信息 <xref:System.Data.DataRow> ，请参阅 [行状态和行版本](./dataset-datatable-dataview/row-states-and-row-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="9903d-108">For information about accessing different row versions using a <xref:System.Data.DataRow>, see [Row States and Row Versions](./dataset-datatable-dataview/row-states-and-row-versions.md).</span></span> <span data-ttu-id="9903d-109">因为公开的对象的集合 <xref:System.Data.DataRowView> <xref:System.Data.DataView> 是可枚举的，所以您可以使用 LINQ to DataSet 来对其进行查询。</span><span class="sxs-lookup"><span data-stu-id="9903d-109">Because the collection of <xref:System.Data.DataRowView> objects exposed by the <xref:System.Data.DataView> is enumerable, you can use LINQ to DataSet to query over it.</span></span>  
  
 <span data-ttu-id="9903d-110">下面的示例对 `Product` 表执行查询查找红色的产品，并从该查询创建表。</span><span class="sxs-lookup"><span data-stu-id="9903d-110">The following example queries the `Product` table for red-colored products and creates a table from that query.</span></span> <span data-ttu-id="9903d-111">从该表创建 <xref:System.Data.DataView> 并将 <xref:System.Data.DataView.RowStateFilter%2A> 属性设置为筛选已删除和修改的行。</span><span class="sxs-lookup"><span data-stu-id="9903d-111">A <xref:System.Data.DataView> is created from the table and the <xref:System.Data.DataView.RowStateFilter%2A> property is set to filter on deleted and modified rows.</span></span> <span data-ttu-id="9903d-112">然后将 <xref:System.Data.DataView> 用作 LINQ 查询中的源，并将已修改和删除的 <xref:System.Data.DataRowView> 对象绑定到 <xref:System.Windows.Forms.DataGridView> 控件。</span><span class="sxs-lookup"><span data-stu-id="9903d-112">The <xref:System.Data.DataView> is then used as a source in a LINQ query, and the <xref:System.Data.DataRowView> objects that have been modified and deleted are bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 <span data-ttu-id="9903d-113">下面的示例从绑定到 <xref:System.Windows.Forms.DataGridView> 控件的视图创建了一个产品表。</span><span class="sxs-lookup"><span data-stu-id="9903d-113">The following example creates a table of products from a view that is bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="9903d-114">对 <xref:System.Data.DataView> 进行查询查找红色的产品，并将排序的结果绑定到 <xref:System.Windows.Forms.DataGridView> 控件。</span><span class="sxs-lookup"><span data-stu-id="9903d-114">The <xref:System.Data.DataView> is queried for red-colored products and the ordered results are bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a><span data-ttu-id="9903d-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="9903d-115">See also</span></span>

- [<span data-ttu-id="9903d-116">数据绑定和 LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="9903d-116">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
