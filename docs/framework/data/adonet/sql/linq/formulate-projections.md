---
title: 构建投影
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: f0bc6dfcff7778ebc7156cbb039e13570c90467b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194396"
---
# <a name="formulate-projections"></a><span data-ttu-id="2a867-102">构建投影</span><span class="sxs-lookup"><span data-stu-id="2a867-102">Formulate Projections</span></span>

<span data-ttu-id="2a867-103">下面的示例演示了 `select` c # 中的语句和 Visual Basic 中的语句如何 `Select` 与其他功能组合起来以形成查询投影。</span><span class="sxs-lookup"><span data-stu-id="2a867-103">The following examples show how the `select` statement in C# and `Select` statement in Visual Basic can be combined with other features to form query projections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a867-104">示例</span><span class="sxs-lookup"><span data-stu-id="2a867-104">Example</span></span>  

 <span data-ttu-id="2a867-105">下面的示例使用 `Select` `select` c # ) 中 Visual Basic (子句中的子句来返回的联系人名称序列 `Customers` 。</span><span class="sxs-lookup"><span data-stu-id="2a867-105">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) to return a sequence of contact names for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a><span data-ttu-id="2a867-106">示例</span><span class="sxs-lookup"><span data-stu-id="2a867-106">Example</span></span>  

 <span data-ttu-id="2a867-107">下面的示例使用 `Select` c # 中 Visual Basic (子句中的子句 `select` ) 和 *匿名类型* 返回的联系人姓名和电话号码序列 `Customers` 。</span><span class="sxs-lookup"><span data-stu-id="2a867-107">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of contact names and telephone numbers for `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="2a867-108">示例</span><span class="sxs-lookup"><span data-stu-id="2a867-108">Example</span></span>  

 <span data-ttu-id="2a867-109">下面的示例使用 `Select` c # 中 Visual Basic (子句中的子句 `select` ) 和 *匿名类型* 返回员工的姓名和电话号码序列。</span><span class="sxs-lookup"><span data-stu-id="2a867-109">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of names and telephone numbers for employees.</span></span> <span data-ttu-id="2a867-110">在产生的序列中，`FirstName` 和 `LastName` 字段组合成单个字段 (`Name`)，`HomePhone` 字段重命名为 `Phone`。</span><span class="sxs-lookup"><span data-stu-id="2a867-110">The `FirstName` and `LastName` fields are combined into a single field (`Name`), and the `HomePhone` field is renamed to `Phone` in the resulting sequence.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a><span data-ttu-id="2a867-111">示例</span><span class="sxs-lookup"><span data-stu-id="2a867-111">Example</span></span>  

 <span data-ttu-id="2a867-112">下面的示例使用 `Select` c # 中 Visual Basic (子句中的子句 `select` ) 和 *匿名类型* 返回一个序列，其中的所有 `ProductID` 和一个名为的计算值 `HalfPrice` 。</span><span class="sxs-lookup"><span data-stu-id="2a867-112">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a sequence of all `ProductID`s and a calculated value named `HalfPrice`.</span></span> <span data-ttu-id="2a867-113">此值设置为 `UnitPrice` 的 1/2。</span><span class="sxs-lookup"><span data-stu-id="2a867-113">This value is set to the `UnitPrice` divided by 2.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a><span data-ttu-id="2a867-114">示例</span><span class="sxs-lookup"><span data-stu-id="2a867-114">Example</span></span>  

 <span data-ttu-id="2a867-115">下面的示例使用了 `Select` c # 中 Visual Basic (子句中的子句 `select` ) 和一个 *条件语句* 来返回产品名称和产品可用性的序列。</span><span class="sxs-lookup"><span data-stu-id="2a867-115">The following example uses the `Select` clause in Visual Basic (`select` clause in C#) and a *conditional statement* to return a sequence of product name and product availability.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="2a867-116">示例</span><span class="sxs-lookup"><span data-stu-id="2a867-116">Example</span></span>  

 <span data-ttu-id="2a867-117">下面的示例使用 `Select` c # 中的 Visual Basic 子句 (`select` 子句 ) 和 (名称) 的 *已知类型* 返回员工姓名的序列。</span><span class="sxs-lookup"><span data-stu-id="2a867-117">The following example uses a Visual Basic `Select` clause (`select` clause in C#) and a *known type* (Name) to return a sequence of the names of employees.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a><span data-ttu-id="2a867-118">示例</span><span class="sxs-lookup"><span data-stu-id="2a867-118">Example</span></span>  

 <span data-ttu-id="2a867-119">下面的示例在 `Select` `Where` Visual Basic (`select` 和 c # ) 中使用和， `where` 以返回伦敦的客户的联系人姓名的 *筛选序列* 。</span><span class="sxs-lookup"><span data-stu-id="2a867-119">The following example uses `Select` and `Where` in Visual Basic (`select` and `where` in C#) to return a *filtered sequence* of contact names for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a><span data-ttu-id="2a867-120">示例</span><span class="sxs-lookup"><span data-stu-id="2a867-120">Example</span></span>  

 <span data-ttu-id="2a867-121">下面的示例使用 `Select` c # 中 Visual Basic (子句中的子句 `select` ) 和 *匿名类型* 返回有关客户的数据的 *形状子集* 。</span><span class="sxs-lookup"><span data-stu-id="2a867-121">The following example uses a `Select` clause in Visual Basic (`select` clause in C#) and *anonymous types* to return a *shaped subset* of the data about customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a><span data-ttu-id="2a867-122">示例</span><span class="sxs-lookup"><span data-stu-id="2a867-122">Example</span></span>  

 <span data-ttu-id="2a867-123">下面的示例使用嵌套查询返回以下结果：</span><span class="sxs-lookup"><span data-stu-id="2a867-123">The following example uses nested queries to return the following results:</span></span>  
  
- <span data-ttu-id="2a867-124">由所有订单及其对应的 `OrderID` 组成的序列。</span><span class="sxs-lookup"><span data-stu-id="2a867-124">A sequence of all orders and their corresponding `OrderID`s.</span></span>  
  
- <span data-ttu-id="2a867-125">由订单中具有折扣的项组成的子序列。</span><span class="sxs-lookup"><span data-stu-id="2a867-125">A subsequence of the items in the order for which there is a discount.</span></span>  
  
- <span data-ttu-id="2a867-126">不含运费时节省的资金数额。</span><span class="sxs-lookup"><span data-stu-id="2a867-126">The amount of money saved if the cost of shipping is not included.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a><span data-ttu-id="2a867-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="2a867-127">See also</span></span>

- [<span data-ttu-id="2a867-128">查询示例</span><span class="sxs-lookup"><span data-stu-id="2a867-128">Query Examples</span></span>](query-examples.md)
