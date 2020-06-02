---
title: 将数据表添加到数据集中
description: 请参阅此示例代码，了解如何创建 DataTable 对象并将其添加到 ADO.NET 中的现有数据集。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 556d29a3-8fc9-4e38-b3ee-c188f7e7b155
ms.openlocfilehash: 42bd36b394de560884a2ec607f4cbc65d1171e4e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286955"
---
# <a name="adding-a-datatable-to-a-dataset"></a><span data-ttu-id="9219e-103">将数据表添加到数据集中</span><span class="sxs-lookup"><span data-stu-id="9219e-103">Adding a DataTable to a DataSet</span></span>
<span data-ttu-id="9219e-104">ADO.NET 使您能够创建 <xref:System.Data.DataTable> 对象并将其添加到现有 <xref:System.Data.DataSet> 中。</span><span class="sxs-lookup"><span data-stu-id="9219e-104">ADO.NET enables you to create <xref:System.Data.DataTable> objects and add them to an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9219e-105">可以使用 <xref:System.Data.DataTable> 和 <xref:System.Data.DataTable.PrimaryKey%2A> 属性为 <xref:System.Data.DataColumn.Unique%2A> 设置约束信息。</span><span class="sxs-lookup"><span data-stu-id="9219e-105">You can set constraint information for a <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.PrimaryKey%2A> and <xref:System.Data.DataColumn.Unique%2A> properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9219e-106">示例</span><span class="sxs-lookup"><span data-stu-id="9219e-106">Example</span></span>  
 <span data-ttu-id="9219e-107">以下示例构造一个 <xref:System.Data.DataSet>，将一个新的 <xref:System.Data.DataTable> 对象添加到该 <xref:System.Data.DataSet> 中，然后将三个 <xref:System.Data.DataColumn> 对象添加到该表中。</span><span class="sxs-lookup"><span data-stu-id="9219e-107">The following example constructs a <xref:System.Data.DataSet>, adds a new <xref:System.Data.DataTable> object to the <xref:System.Data.DataSet>, and then adds three <xref:System.Data.DataColumn> objects to the table.</span></span> <span data-ttu-id="9219e-108">最后，该代码将一个列设置为主键列。</span><span class="sxs-lookup"><span data-stu-id="9219e-108">Finally, the code sets one column as the primary key column.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableAdd#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableAdd/VB/source.vb#1)]  
  
## <a name="case-sensitivity"></a><span data-ttu-id="9219e-109">区分大小写</span><span class="sxs-lookup"><span data-stu-id="9219e-109">Case Sensitivity</span></span>  
 <span data-ttu-id="9219e-110"><xref:System.Data.DataSet> 中可以存在两个或两个以上的同名但是大小写不同的表或关系。</span><span class="sxs-lookup"><span data-stu-id="9219e-110">Two or more tables or relations with the same name, but different casing, can exist in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9219e-111">在这种情况下，通过名称对表和关系的引用将区分大小写。</span><span class="sxs-lookup"><span data-stu-id="9219e-111">In such cases, references by name to tables and relations are case sensitive.</span></span> <span data-ttu-id="9219e-112">例如，如果 <xref:System.Data.DataSet> **数据集**包含表表**Table1** 1 和**table1**表1，则将按 name 作为 Dataset 引用**table1** 。**表 ["Table1"]**， **table1**表1作为**数据集。表 ["table1"]**。</span><span class="sxs-lookup"><span data-stu-id="9219e-112">For example, if the <xref:System.Data.DataSet> **dataSet** contains tables **Table1** and **table1**, you would reference **Table1** by name as **dataSet.Tables["Table1"]**, and **table1** as **dataSet.Tables["table1"]**.</span></span> <span data-ttu-id="9219e-113">尝试将其中一个表作为 DataSet 引用 **。表 ["TABLE1"]** 将生成异常。</span><span class="sxs-lookup"><span data-stu-id="9219e-113">Attempting to reference either of the tables as **dataSet.Tables["TABLE1"]** would generate an exception.</span></span>  
  
 <span data-ttu-id="9219e-114">如果只有一个具有特定名称的表或关系，则区分大小写行为不适用。</span><span class="sxs-lookup"><span data-stu-id="9219e-114">The case-sensitivity behavior does not apply if only one table or relation has a particular name.</span></span> <span data-ttu-id="9219e-115">例如，如果 <xref:System.Data.DataSet> 只有**Table1**，则可以使用 dataSet 引用它 **。表 ["Table1"]**。</span><span class="sxs-lookup"><span data-stu-id="9219e-115">For example, if the <xref:System.Data.DataSet> has only **Table1**, you can reference it using **dataSet.Tables["TABLE1"]**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9219e-116"><xref:System.Data.DataSet.CaseSensitive%2A> 的 <xref:System.Data.DataSet> 属性不影响此行为。</span><span class="sxs-lookup"><span data-stu-id="9219e-116">The <xref:System.Data.DataSet.CaseSensitive%2A> property of the <xref:System.Data.DataSet> does not affect this behavior.</span></span> <span data-ttu-id="9219e-117"><xref:System.Data.DataSet.CaseSensitive%2A> 属性应用于 <xref:System.Data.DataSet> 中的数据，并会影响排序、搜索、筛选、执行约束，等等。</span><span class="sxs-lookup"><span data-stu-id="9219e-117">The <xref:System.Data.DataSet.CaseSensitive%2A> property applies to the data in the <xref:System.Data.DataSet> and affects sorting, searching, filtering, enforcing constraints, and so on.</span></span>  
  
## <a name="namespace-support"></a><span data-ttu-id="9219e-118">命名空间支持</span><span class="sxs-lookup"><span data-stu-id="9219e-118">Namespace Support</span></span>  
 <span data-ttu-id="9219e-119">在 2.0 之前的 ADO.NET 版本中，两个表即使处于不同的命名空间中也不能同名。</span><span class="sxs-lookup"><span data-stu-id="9219e-119">In versions of ADO.NET earlier than 2.0, two tables could not have the same name, even if they were in different namespaces.</span></span> <span data-ttu-id="9219e-120">ADO.NET 2.0 中取消了此限制。</span><span class="sxs-lookup"><span data-stu-id="9219e-120">This limitation was removed in ADO.NET 2.0.</span></span> <span data-ttu-id="9219e-121"><xref:System.Data.DataSet> 可以包含具有相同 <xref:System.Data.DataTable.TableName%2A> 属性值但是具有不同 <xref:System.Data.DataTable.Namespace%2A> 属性值的两个表。</span><span class="sxs-lookup"><span data-stu-id="9219e-121">A <xref:System.Data.DataSet> can contain two tables that have the same <xref:System.Data.DataTable.TableName%2A> property value but different <xref:System.Data.DataTable.Namespace%2A> property values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9219e-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9219e-122">See also</span></span>

- [<span data-ttu-id="9219e-123">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="9219e-123">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="9219e-124">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="9219e-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
