---
title: System.Math 方法
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: e91c8ea95d21288ad2577f1550333febd448766d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158196"
---
# <a name="systemmath-methods"></a><span data-ttu-id="5ae68-102">System.Math 方法</span><span class="sxs-lookup"><span data-stu-id="5ae68-102">System.Math Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="5ae68-103">不支持以下 <xref:System.Math> 方法。</span><span class="sxs-lookup"><span data-stu-id="5ae68-103">does not support the following <xref:System.Math> methods.</span></span>  
  
- <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a><span data-ttu-id="5ae68-104">与 .NET 的差异</span><span class="sxs-lookup"><span data-stu-id="5ae68-104">Differences from .NET</span></span>  

 <span data-ttu-id="5ae68-105">.NET Framework 在舍入语义方面与 SQL Server 不同。</span><span class="sxs-lookup"><span data-stu-id="5ae68-105">The .NET Framework has different rounding semantics from SQL Server.</span></span> <span data-ttu-id="5ae68-106"><xref:System.Math.Round%2A>.NET Framework 中的方法执行按下*舍入的舍入*，其中以0.5 结尾的数字舍入到最接近的偶数，而不是下一个较大的数字。</span><span class="sxs-lookup"><span data-stu-id="5ae68-106">The <xref:System.Math.Round%2A> method in the .NET Framework performs *Banker's rounding*, where numbers that ends in .5 round to the nearest even digit instead of to the next higher digit.</span></span> <span data-ttu-id="5ae68-107">例如，2.5 舍入为 2，而 3.5 则舍入为 4。</span><span class="sxs-lookup"><span data-stu-id="5ae68-107">For example, 2.5 rounds to 2, while 3.5 rounds to 4.</span></span> <span data-ttu-id="5ae68-108">（此方法有助于避免大型数据事务中趋向较高值的系统性偏差。）</span><span class="sxs-lookup"><span data-stu-id="5ae68-108">(This technique helps avoid systematic bias toward higher values in large data transactions.)</span></span>  
  
 <span data-ttu-id="5ae68-109">而在 SQL 中，`ROUND` 函数则始终向远离 0 的方向舍入。</span><span class="sxs-lookup"><span data-stu-id="5ae68-109">In SQL, the `ROUND` function instead always rounds away from 0.</span></span> <span data-ttu-id="5ae68-110">因此 2.5 舍入为 3，相比之下，它在 .NET Framework 中则舍入为 2。</span><span class="sxs-lookup"><span data-stu-id="5ae68-110">Therefore 2.5 rounds to 3, contrasted with its rounding to 2 in the .NET Framework.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="5ae68-111">遵照 SQL `ROUND` 语义，因而不会尝试执行“四舍六入五成双”。</span><span class="sxs-lookup"><span data-stu-id="5ae68-111">passes through to the SQL `ROUND` semantics and does not try to implement Banker's rounding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ae68-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="5ae68-112">See also</span></span>

- [<span data-ttu-id="5ae68-113">数据类型和函数</span><span class="sxs-lookup"><span data-stu-id="5ae68-113">Data Types and Functions</span></span>](data-types-and-functions.md)
