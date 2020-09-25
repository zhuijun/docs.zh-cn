---
title: 如何：一次检索多个对象
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 18aff4d8-bde8-461b-9960-ccabb24e9d22
ms.openlocfilehash: 98827989f72b7922a325a9e13b5f46cb18ac5395
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197308"
---
# <a name="how-to-retrieve-many-objects-at-once"></a><span data-ttu-id="53607-102">如何：一次检索多个对象</span><span class="sxs-lookup"><span data-stu-id="53607-102">How to: Retrieve Many Objects At Once</span></span>

<span data-ttu-id="53607-103">通过使用 <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>，可以在一个查询中检索许多对象。</span><span class="sxs-lookup"><span data-stu-id="53607-103">You can retrieve many objects in one query by using <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53607-104">示例</span><span class="sxs-lookup"><span data-stu-id="53607-104">Example</span></span>  

 <span data-ttu-id="53607-105">下面的代码使用 <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> 方法来同时检索 `Customer` 和 `Order` 对象。</span><span class="sxs-lookup"><span data-stu-id="53607-105">The following code uses the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to retrieve both `Customer` and `Order` objects.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#9)]
 [!code-vb[DLinqQueryConcepts#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="53607-106">请参阅</span><span class="sxs-lookup"><span data-stu-id="53607-106">See also</span></span>

- [<span data-ttu-id="53607-107">查询概念</span><span class="sxs-lookup"><span data-stu-id="53607-107">Query Concepts</span></span>](query-concepts.md)
