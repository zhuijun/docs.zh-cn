---
title: 如何：使用针对多个结果形状映射的存储过程
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 26cc30790da26949fba889106d060cdef89013a3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184997"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a><span data-ttu-id="a6942-102">如何：使用针对多个结果形状映射的存储过程</span><span class="sxs-lookup"><span data-stu-id="a6942-102">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>

<span data-ttu-id="a6942-103">当存储过程可以返回多个结果形状时，返回类型无法强类型化为单个投影形状。</span><span class="sxs-lookup"><span data-stu-id="a6942-103">When a stored procedure can return multiple result shapes, the return type cannot be strongly typed to a single projection shape.</span></span> <span data-ttu-id="a6942-104">尽管 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可以生成所有可能的投影类型，但它无法获知将以何种顺序返回它们。</span><span class="sxs-lookup"><span data-stu-id="a6942-104">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can generate all possible projection types, it cannot know the order in which they will be returned.</span></span>  
  
 <span data-ttu-id="a6942-105">请将这种情况与按顺序产生多个结果形状的存储过程作一个对比。</span><span class="sxs-lookup"><span data-stu-id="a6942-105">Contrast this scenario with stored procedures that produce multiple result shapes sequentially.</span></span> <span data-ttu-id="a6942-106">有关详细信息，请参阅 [如何：使用为顺序结果形状映射的存储过程](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)。</span><span class="sxs-lookup"><span data-stu-id="a6942-106">For more information, see [How to: Use Stored Procedures Mapped for Sequential Result Shapes](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span></span>  
  
 <span data-ttu-id="a6942-107"><xref:System.Data.Linq.Mapping.ResultTypeAttribute> 属性适用于返回多个结果类型的存储过程，用以指定该过程可以返回的类型的集合。</span><span class="sxs-lookup"><span data-stu-id="a6942-107">The <xref:System.Data.Linq.Mapping.ResultTypeAttribute> attribute is applied to stored procedures that return multiple result types to specify the set of types the procedure can return.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6942-108">示例</span><span class="sxs-lookup"><span data-stu-id="a6942-108">Example</span></span>  

 <span data-ttu-id="a6942-109">在下面的 SQL 代码示例中，结果形状取决于输入（`shape =1` 或 `shape = 2`）。</span><span class="sxs-lookup"><span data-stu-id="a6942-109">In the following SQL code example, the result shape depends on the input (`shape =1` or `shape = 2`).</span></span> <span data-ttu-id="a6942-110">您不知道将先返回哪个投影。</span><span class="sxs-lookup"><span data-stu-id="a6942-110">You do not know which projection will be returned first.</span></span>  
  
``` sql
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="a6942-111">示例</span><span class="sxs-lookup"><span data-stu-id="a6942-111">Example</span></span>  

 <span data-ttu-id="a6942-112">你将使用类似于以下内容的代码来执行此存储过程。</span><span class="sxs-lookup"><span data-stu-id="a6942-112">You would use code similar to the following to execute this stored procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6942-113">您必须根据您对存储过程的认识，使用 <xref:System.Data.Linq.IMultipleResults.GetResult%2A> 模式获取正确类型的枚举数。</span><span class="sxs-lookup"><span data-stu-id="a6942-113">You must use the <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pattern to obtain an enumerator of the correct type, based on your knowledge of the stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="a6942-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="a6942-114">See also</span></span>

- [<span data-ttu-id="a6942-115">存储过程</span><span class="sxs-lookup"><span data-stu-id="a6942-115">Stored Procedures</span></span>](stored-procedures.md)
