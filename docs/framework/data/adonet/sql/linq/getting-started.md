---
title: 入门
description: 使用此示例代码，开始使用 LINQ to SQL 使用 LINQ 技术来访问 SQL 数据库，就像访问内存中集合一样。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: b886518d4cff687a18f363c3e3ba43b40631a22f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194370"
---
# <a name="getting-started"></a><span data-ttu-id="0548b-103">入门</span><span class="sxs-lookup"><span data-stu-id="0548b-103">Getting Started</span></span>

<span data-ttu-id="0548b-104">使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ，可以使用 LINQ 技术访问 SQL 数据库，就像访问内存中集合一样。</span><span class="sxs-lookup"><span data-stu-id="0548b-104">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the LINQ technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="0548b-105">例如，在下面的代码中，创建了 `nw` 对象来表示 `Northwind` 数据库，将 `Customers` 表作为目标，筛选出了来自 `Customers` 的 `London` 行，并选择了一个表示 `CompanyName` 的字符串以进行检索。</span><span class="sxs-lookup"><span data-stu-id="0548b-105">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="0548b-106">执行循环时，将检索到 `CompanyName` 值的集合。</span><span class="sxs-lookup"><span data-stu-id="0548b-106">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="0548b-107">后续步骤</span><span class="sxs-lookup"><span data-stu-id="0548b-107">Next Steps</span></span>  

 <span data-ttu-id="0548b-108">有关其他一些示例，包括插入和更新，请参阅 [可以对 LINQ to SQL 执行的操作](what-you-can-do-with-linq-to-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="0548b-108">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="0548b-109">接下来，请试着按一些演练和教程中的说明动手操作，实际体验一下 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的使用。</span><span class="sxs-lookup"><span data-stu-id="0548b-109">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="0548b-110">请参阅 [通过演练学习](learning-by-walkthroughs.md)。</span><span class="sxs-lookup"><span data-stu-id="0548b-110">See [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="0548b-111">最后，请 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 阅读 [使用 LINQ to SQL 的典型步骤](typical-steps-for-using-linq-to-sql.md)，了解如何开始使用自己的项目。</span><span class="sxs-lookup"><span data-stu-id="0548b-111">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0548b-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="0548b-112">See also</span></span>

- [<span data-ttu-id="0548b-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0548b-113">LINQ to SQL</span></span>](index.md)
- [<span data-ttu-id="0548b-114">LINQ 简介 (C#)</span><span class="sxs-lookup"><span data-stu-id="0548b-114">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="0548b-115">LINQ 简介 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0548b-115">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="0548b-116">LINQ to SQL 对象模型</span><span class="sxs-lookup"><span data-stu-id="0548b-116">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
