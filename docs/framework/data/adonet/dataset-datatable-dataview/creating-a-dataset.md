---
title: 创建数据集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: cbf652cc3742cb880fe060743dcc2615e6283ca7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202352"
---
# <a name="creating-a-dataset"></a><span data-ttu-id="0a530-102">创建数据集</span><span class="sxs-lookup"><span data-stu-id="0a530-102">Creating a DataSet</span></span>

<span data-ttu-id="0a530-103">可以通过调用 <xref:System.Data.DataSet> 构造函数来创建 <xref:System.Data.DataSet> 的实例。</span><span class="sxs-lookup"><span data-stu-id="0a530-103">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="0a530-104">可以选择指定一个名称自变量。</span><span class="sxs-lookup"><span data-stu-id="0a530-104">Optionally specify a name argument.</span></span> <span data-ttu-id="0a530-105">如果没有为 <xref:System.Data.DataSet> 指定名称，则该名称会设置为“NewDataSet”。</span><span class="sxs-lookup"><span data-stu-id="0a530-105">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="0a530-106">也可以基于现有的 <xref:System.Data.DataSet> 来创建新的 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="0a530-106">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="0a530-107">新的 <xref:System.Data.DataSet> 可以是：现有 <xref:System.Data.DataSet> 的原样副本；<xref:System.Data.DataSet> 的复本，它复制关系结构（即架构）但不包含现有 <xref:System.Data.DataSet> 中的任何数据；或 <xref:System.Data.DataSet> 的子集，它仅包含现有 <xref:System.Data.DataSet> 中已使用 <xref:System.Data.DataSet.GetChanges%2A> 方法修改的行。</span><span class="sxs-lookup"><span data-stu-id="0a530-107">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="0a530-108">有关详细信息，请参阅 [复制数据集内容](copying-dataset-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="0a530-108">For more information, see [Copying DataSet Contents](copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="0a530-109">以下代码示例演示了如何构造 <xref:System.Data.DataSet> 的实例。</span><span class="sxs-lookup"><span data-stu-id="0a530-109">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a530-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="0a530-110">See also</span></span>

- [<span data-ttu-id="0a530-111">从 DataAdapter 填充数据集</span><span class="sxs-lookup"><span data-stu-id="0a530-111">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="0a530-112">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="0a530-112">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="0a530-113">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="0a530-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
