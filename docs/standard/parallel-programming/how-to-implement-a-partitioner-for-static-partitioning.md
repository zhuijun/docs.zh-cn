---
title: 如何：实现静态分区的分区程序
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 22d2cf788d4726488512703356a75f84efd04250
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278501"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="58a7d-102">如何：实现静态分区的分区程序</span><span class="sxs-lookup"><span data-stu-id="58a7d-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="58a7d-103">下面的示例展示了一种为执行静态分区的 PLINQ 实现简单自定义分区程序的方法。</span><span class="sxs-lookup"><span data-stu-id="58a7d-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="58a7d-104">由于分区程序不支持动态分区，因此无法通过 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 使用它。</span><span class="sxs-lookup"><span data-stu-id="58a7d-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="58a7d-105">对于每个元素需要越来越多处理时间的数据源，此分区程序可能会让速度提升（与默认范围分区程序相比）。</span><span class="sxs-lookup"><span data-stu-id="58a7d-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58a7d-106">示例</span><span class="sxs-lookup"><span data-stu-id="58a7d-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="58a7d-107">此示例中的分区都基于每个元素的处理时间呈线性增加的假设。</span><span class="sxs-lookup"><span data-stu-id="58a7d-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="58a7d-108">实际上，按这种方式预测处理时间可能会很困难。</span><span class="sxs-lookup"><span data-stu-id="58a7d-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="58a7d-109">如果将静态分区程序与特定数据源结合使用，可以优化源的分区公式，也可以添加负载均衡逻辑，或使用区块分区方法（如[如何：实现动态分区](how-to-implement-dynamic-partitions.md)中所述）。</span><span class="sxs-lookup"><span data-stu-id="58a7d-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58a7d-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="58a7d-110">See also</span></span>

- [<span data-ttu-id="58a7d-111">PLINQ 和 TPL 的自定义分区程序</span><span class="sxs-lookup"><span data-stu-id="58a7d-111">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)
