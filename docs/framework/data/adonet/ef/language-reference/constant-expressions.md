---
title: 常量表达式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: 163f73a7682d444214caa213751cb35f8f0e8743
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153035"
---
# <a name="constant-expressions"></a><span data-ttu-id="439d1-102">常量表达式</span><span class="sxs-lookup"><span data-stu-id="439d1-102">Constant Expressions</span></span>

<span data-ttu-id="439d1-103">常量表达式由常量值组成。</span><span class="sxs-lookup"><span data-stu-id="439d1-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="439d1-104">常量值被直接转换为常量命令目录树表达式，而无需在客户端进行任何变换。</span><span class="sxs-lookup"><span data-stu-id="439d1-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="439d1-105">这包括产生常量值的表达式。</span><span class="sxs-lookup"><span data-stu-id="439d1-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="439d1-106">因此，所有涉及常量的表达式都应具有数据源行为。</span><span class="sxs-lookup"><span data-stu-id="439d1-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="439d1-107">这可能产生与 CLR 行为不同的行为。</span><span class="sxs-lookup"><span data-stu-id="439d1-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="439d1-108">下面的示例说明了一个在服务器上求值的常量表达式。</span><span class="sxs-lookup"><span data-stu-id="439d1-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 <span data-ttu-id="439d1-109">LINQ to Entities 不支持将用户类用作常量。</span><span class="sxs-lookup"><span data-stu-id="439d1-109">LINQ to Entities does not support using a user class as a constant.</span></span> <span data-ttu-id="439d1-110">但是，用户类上的属性引用被视为常量，将转换为命令目录树常量表达式并在数据源上执行。</span><span class="sxs-lookup"><span data-stu-id="439d1-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="439d1-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="439d1-111">See also</span></span>

- [<span data-ttu-id="439d1-112">LINQ to Entities 查询中的表达式</span><span class="sxs-lookup"><span data-stu-id="439d1-112">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
