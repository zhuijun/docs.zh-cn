---
title: 聚合查询
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: 2085808d631d1d9f97573c557e9e66e07113df52
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554216"
---
# <a name="aggregate-queries"></a><span data-ttu-id="6815e-102">聚合查询</span><span class="sxs-lookup"><span data-stu-id="6815e-102">Aggregate Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="6815e-103">支持 `Average`、`Count`、`Max`、`Min` 和 `Sum` 聚合运算符。</span><span class="sxs-lookup"><span data-stu-id="6815e-103">supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="6815e-104">请注意 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中聚合运算符的以下特征：</span><span class="sxs-lookup"><span data-stu-id="6815e-104">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="6815e-105">聚合查询是立即执行的。</span><span class="sxs-lookup"><span data-stu-id="6815e-105">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="6815e-106">有关详细信息，请参阅 [LINQ 查询简介 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="6815e-106">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
- <span data-ttu-id="6815e-107">聚合查询通常返回一个数字，而非一个集合。</span><span class="sxs-lookup"><span data-stu-id="6815e-107">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="6815e-108">有关详细信息，请参阅 [聚合运算](/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="6815e-108">For more information, see [Aggregation Operations](/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span></span>  
  
- <span data-ttu-id="6815e-109">不能对匿名类型调用聚合。</span><span class="sxs-lookup"><span data-stu-id="6815e-109">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="6815e-110">以下主题中的示例来自 Northwind 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="6815e-110">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="6815e-111">有关详细信息，请参阅 [下载示例数据库](downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="6815e-111">For more information, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6815e-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="6815e-112">In This Section</span></span>  
 [<span data-ttu-id="6815e-113">从数值序列中返回平均值</span><span class="sxs-lookup"><span data-stu-id="6815e-113">Return the Average Value From a Numeric Sequence</span></span>](return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="6815e-114">演示如何使用 <xref:System.Linq.Enumerable.Average%2A> 运算符。</span><span class="sxs-lookup"><span data-stu-id="6815e-114">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="6815e-115">对序列中元素的数目进行计数</span><span class="sxs-lookup"><span data-stu-id="6815e-115">Count the Number of Elements in a Sequence</span></span>](count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="6815e-116">演示如何使用 <xref:System.Linq.Enumerable.Count%2A> 运算符。</span><span class="sxs-lookup"><span data-stu-id="6815e-116">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="6815e-117">查找数值序列中的最大值</span><span class="sxs-lookup"><span data-stu-id="6815e-117">Find the Maximum Value in a Numeric Sequence</span></span>](find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="6815e-118">演示如何使用 <xref:System.Linq.Enumerable.Max%2A> 运算符。</span><span class="sxs-lookup"><span data-stu-id="6815e-118">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="6815e-119">查找数值序列中的最小值</span><span class="sxs-lookup"><span data-stu-id="6815e-119">Find the Minimum Value in a Numeric Sequence</span></span>](find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="6815e-120">演示如何使用 <xref:System.Linq.Enumerable.Min%2A> 运算符。</span><span class="sxs-lookup"><span data-stu-id="6815e-120">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="6815e-121">计算数值序列中值的和</span><span class="sxs-lookup"><span data-stu-id="6815e-121">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="6815e-122">演示如何使用 <xref:System.Linq.Enumerable.Sum%2A> 运算符。</span><span class="sxs-lookup"><span data-stu-id="6815e-122">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6815e-123">相关章节</span><span class="sxs-lookup"><span data-stu-id="6815e-123">Related Sections</span></span>  
 [<span data-ttu-id="6815e-124">查询示例</span><span class="sxs-lookup"><span data-stu-id="6815e-124">Query Examples</span></span>](query-examples.md)  
 <span data-ttu-id="6815e-125">提供指向 Visual Basic 和 C# 中 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查询的链接。</span><span class="sxs-lookup"><span data-stu-id="6815e-125">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="6815e-126">查询概念</span><span class="sxs-lookup"><span data-stu-id="6815e-126">Query Concepts</span></span>](query-concepts.md)  
 <span data-ttu-id="6815e-127">提供指向一些主题的链接，这些主题说明如何在中设计 LINQ 查询 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6815e-127">Provides links to topics that explain concepts for designing LINQ queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="6815e-128">LINQ 查询简介 (C#)</span><span class="sxs-lookup"><span data-stu-id="6815e-128">Introduction to LINQ Queries (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="6815e-129">说明查询在 LINQ 中的工作方式。</span><span class="sxs-lookup"><span data-stu-id="6815e-129">Explains how queries work in LINQ.</span></span>
