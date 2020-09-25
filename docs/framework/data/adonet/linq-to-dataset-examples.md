---
title: LINQ to DataSet 示例
ms.date: 03/30/2017
ms.assetid: dfd91658-8d8a-45a4-a356-e327e809f21d
ms.openlocfilehash: 48511dc7ae249e35b9bd76e0d6d3d9f1ef39dde0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169513"
---
# <a name="linq-to-dataset-examples"></a><span data-ttu-id="b151c-102">LINQ to DataSet 示例</span><span class="sxs-lookup"><span data-stu-id="b151c-102">LINQ to DataSet Examples</span></span>

<span data-ttu-id="b151c-103">本节提供使用标准查询运算符的 LINQ to DataSet 编程示例。</span><span class="sxs-lookup"><span data-stu-id="b151c-103">This section provides LINQ to DataSet programming examples that use the standard query operators.</span></span> <span data-ttu-id="b151c-104"><xref:System.Data.DataSet>这些示例中使用的是使用方法填充的 `FillDataSet` ，该方法是在将[数据加载到数据集](loading-data-into-a-dataset.md)时指定的。</span><span class="sxs-lookup"><span data-stu-id="b151c-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="b151c-105">有关详细信息，请参阅 [标准查询运算符概述 (c # ) ](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) 或 [标准查询运算符概述 (Visual Basic) ](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b151c-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b151c-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="b151c-106">In This Section</span></span>  

 [<span data-ttu-id="b151c-107">查询表达式示例</span><span class="sxs-lookup"><span data-stu-id="b151c-107">Query Expression Examples</span></span>](query-expression-examples-linq-to-dataset.md)  
 <span data-ttu-id="b151c-108">包含下面的示例：</span><span class="sxs-lookup"><span data-stu-id="b151c-108">Contains the following examples:</span></span>  
  
- [<span data-ttu-id="b151c-109">投影</span><span class="sxs-lookup"><span data-stu-id="b151c-109">Projection</span></span>](query-expression-syntax-examples-projection-linq-to-dataset.md)  
  
- [<span data-ttu-id="b151c-110">限制</span><span class="sxs-lookup"><span data-stu-id="b151c-110">Restriction</span></span>](query-expression-syntax-examples-restriction-linq-to-dataset.md)  
  
- [<span data-ttu-id="b151c-111">分区</span><span class="sxs-lookup"><span data-stu-id="b151c-111">Partitioning</span></span>](query-expression-syntax-examples-partitioning.md)  
  
- [<span data-ttu-id="b151c-112">中间件排序</span><span class="sxs-lookup"><span data-stu-id="b151c-112">Ordering</span></span>](query-expression-syntax-examples-ordering-linq-to-dataset.md)  
  
- [<span data-ttu-id="b151c-113">元素运算符</span><span class="sxs-lookup"><span data-stu-id="b151c-113">Element Operators</span></span>](query-expression-syntax-examples-element-operators.md)  
  
- [<span data-ttu-id="b151c-114">聚合运算符</span><span class="sxs-lookup"><span data-stu-id="b151c-114">Aggregate Operators</span></span>](query-expression-syntax-examples-aggregate-operators.md)  
  
- [<span data-ttu-id="b151c-115">联接运算符</span><span class="sxs-lookup"><span data-stu-id="b151c-115">Join Operators</span></span>](query-expression-syntax-examples-join-operators.md)  
  
 [<span data-ttu-id="b151c-116">基于方法的查询示例</span><span class="sxs-lookup"><span data-stu-id="b151c-116">Method-Based Query Examples</span></span>](method-based-query-examples-linq-to-dataset.md)  
 <span data-ttu-id="b151c-117">包含下面的示例：</span><span class="sxs-lookup"><span data-stu-id="b151c-117">Contains the following examples:</span></span>  
  
- [<span data-ttu-id="b151c-118">投影</span><span class="sxs-lookup"><span data-stu-id="b151c-118">Projection</span></span>](method-based-query-syntax-examples-projection.md)  
  
- [<span data-ttu-id="b151c-119">分区</span><span class="sxs-lookup"><span data-stu-id="b151c-119">Partitioning</span></span>](method-based-query-syntax-examples-partitioning-linq.md)  
  
- [<span data-ttu-id="b151c-120">中间件排序</span><span class="sxs-lookup"><span data-stu-id="b151c-120">Ordering</span></span>](method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
  
- [<span data-ttu-id="b151c-121">集合运算符</span><span class="sxs-lookup"><span data-stu-id="b151c-121">Set Operators</span></span>](method-based-query-syntax-examples-set-operators.md)  
  
- [<span data-ttu-id="b151c-122">转换运算符</span><span class="sxs-lookup"><span data-stu-id="b151c-122">Conversion Operators</span></span>](method-based-query-syntax-examples-conversion-operators.md)  
  
- [<span data-ttu-id="b151c-123">元素运算符</span><span class="sxs-lookup"><span data-stu-id="b151c-123">Element Operators</span></span>](method-based-query-syntax-examples-element-operators.md)  
  
- [<span data-ttu-id="b151c-124">聚合运算符</span><span class="sxs-lookup"><span data-stu-id="b151c-124">Aggregate Operators</span></span>](method-based-query-syntax-examples-aggregate-operators.md)  
  
- [<span data-ttu-id="b151c-125">Join</span><span class="sxs-lookup"><span data-stu-id="b151c-125">Join</span></span>](method-based-query-syntax-examples-join-linq-to-dataset.md)  
  
 [<span data-ttu-id="b151c-126">数据集特定的运算符示例</span><span class="sxs-lookup"><span data-stu-id="b151c-126">DataSet-Specific Operator Examples</span></span>](dataset-specific-operator-examples-linq-to-dataset.md)  
 <span data-ttu-id="b151c-127">包含演示如何使用 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 方法和 <xref:System.Data.DataRowComparer> 类的示例。</span><span class="sxs-lookup"><span data-stu-id="b151c-127">Contains examples that demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b151c-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="b151c-128">See also</span></span>

- [<span data-ttu-id="b151c-129">编程指南</span><span class="sxs-lookup"><span data-stu-id="b151c-129">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)
- [<span data-ttu-id="b151c-130">将数据加载到数据集中</span><span class="sxs-lookup"><span data-stu-id="b151c-130">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
