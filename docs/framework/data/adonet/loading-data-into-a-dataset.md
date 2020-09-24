---
title: 将数据加载到数据集中
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: c870cabc875aa0152910ce916819fb1ff1c018f7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166705"
---
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="b84bc-102">将数据加载到数据集中</span><span class="sxs-lookup"><span data-stu-id="b84bc-102">Loading Data Into a DataSet</span></span>

<span data-ttu-id="b84bc-103"><xref:System.Data.DataSet>必须先填充对象，然后才能使用 LINQ to DataSet 进行查询。</span><span class="sxs-lookup"><span data-stu-id="b84bc-103">A <xref:System.Data.DataSet> object must first be populated before you can query over it with LINQ to DataSet.</span></span> <span data-ttu-id="b84bc-104">填充 <xref:System.Data.DataSet> 有多种不同的方式。</span><span class="sxs-lookup"><span data-stu-id="b84bc-104">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b84bc-105">例如，您可以使用 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] 来查询数据库并将结果加载到 <xref:System.Data.DataSet> 中。</span><span class="sxs-lookup"><span data-stu-id="b84bc-105">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b84bc-106">有关详细信息，请参阅 [LINQ to SQL](./sql/linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b84bc-106">For more information, see [LINQ to SQL](./sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="b84bc-107">另一种将数据加载到 <xref:System.Data.DataSet> 中的常见方式是使用 <xref:System.Data.Common.DataAdapter> 类从数据库中检索数据。</span><span class="sxs-lookup"><span data-stu-id="b84bc-107">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="b84bc-108">下列示例对此进行了阐释。</span><span class="sxs-lookup"><span data-stu-id="b84bc-108">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b84bc-109">示例</span><span class="sxs-lookup"><span data-stu-id="b84bc-109">Example</span></span>  

 <span data-ttu-id="b84bc-110">此示例使用 <xref:System.Data.Common.DataAdapter> 查询 AdventureWorks 数据库中从 2002 年起的销售信息，并将结果加载到 <xref:System.Data.DataSet> 中。</span><span class="sxs-lookup"><span data-stu-id="b84bc-110">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b84bc-111">填充后 <xref:System.Data.DataSet> ，可以使用 LINQ to DataSet 来编写查询。</span><span class="sxs-lookup"><span data-stu-id="b84bc-111">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using LINQ to DataSet.</span></span> <span data-ttu-id="b84bc-112">`FillDataSet`本示例中的方法用于[LINQ to DataSet 示例](linq-to-dataset-examples.md)中的示例查询。</span><span class="sxs-lookup"><span data-stu-id="b84bc-112">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](linq-to-dataset-examples.md).</span></span> <span data-ttu-id="b84bc-113">有关详细信息，请参阅 [查询数据集](querying-datasets-linq-to-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="b84bc-113">For more information, see [Querying DataSets](querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="b84bc-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="b84bc-114">See also</span></span>

- [<span data-ttu-id="b84bc-115">LINQ to DataSet 概述</span><span class="sxs-lookup"><span data-stu-id="b84bc-115">LINQ to DataSet Overview</span></span>](linq-to-dataset-overview.md)
- [<span data-ttu-id="b84bc-116">查询数据集</span><span class="sxs-lookup"><span data-stu-id="b84bc-116">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="b84bc-117">LINQ to DataSet 示例</span><span class="sxs-lookup"><span data-stu-id="b84bc-117">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
