---
title: LINQ to XML 中的延迟执行和迟缓计算 (C#)
description: 查询和轴操作可以使用 C# 中的延迟执行。 了解延迟执行的要求和优点，以及实现注意事项。
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 8559505572404f895d75e0d9895f9ae2c07b795e
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105461"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a>LINQ to XML 中的延迟执行和迟缓计算 (C#)
实现查询和轴操作通常是为了使用延迟执行。 本主题解释延迟执行的要求和优点，以及某些实现注意事项。  
  
## <a name="deferred-execution"></a>延迟执行  
 延迟执行意味着表达式的计算延迟，直到真正需要其实现值为止。 当必须操作大型数据集合，特别是在包含一系列链接的查询或操作的程序中操作时，延迟执行可以大大改善性能。 在最佳情况下，延迟执行只允许对源集合的单个循环访问。  
  
 LINQ 技术广泛应用了延迟执行，包括在核心 <xref:System.Linq?displayProperty=nameWithType> 类的成员和不同 LINQ 命名空间中的扩展方法（如 <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>）中使用。  
  
 在迭代器块内使用时，C# 语言可以通过 [yield](../../../language-reference/keywords/yield.md) 关键字（以 `yield-return` 语句形式），直接支持延迟执行。 此类迭代器必须返回类型为 <xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>（或派生类型）的集合。  
  
## <a name="eager-vs-lazy-evaluation"></a>积极计算与迟缓计算  
 当您编写实现延迟执行的方法时，还必须确定是使用迟缓计算还是积极计算来实现该方法。  
  
- 在迟缓计算中，每次调用迭代器时都会处理源集合的一个元素。 这是实现迭代器的典型方式。  
  
- 在积极计算中，第一次调用迭代器时就会对整个集合进行处理。 还可能需要源集合的临时副本。 例如，<xref:System.Linq.Enumerable.OrderBy%2A> 方法必须在返回第一个元素前对整个集合进行排序。  
  
 迟缓计算通常产生更好的性能，因为它将系统开销处理平均分配到整个集合的计算中，并将临时数据的使用降至最低。 当然，对于某些操作，除了具体化中间结果之外，再没有其他选择。  
  
## <a name="next-steps"></a>后续步骤  
 本教程的下一个主题将解释延迟执行：  
  
- [延迟执行示例 (C#)](./deferred-execution-example.md)  
  
## <a name="see-also"></a>请参阅

- [教程：将查询链接在一起 (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
- [概念和术语（功能转换）(C#)](./concepts-and-terminology-functional-transformation.md)
- [聚合运算 (C#)](./aggregation-operations.md)
- [yield](../../../language-reference/keywords/yield.md)
