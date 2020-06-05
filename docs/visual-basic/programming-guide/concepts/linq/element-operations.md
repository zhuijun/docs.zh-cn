---
title: 元素运算
ms.date: 07/20/2015
ms.assetid: 5fcb0631-dce5-45ff-8abb-353cae21e14f
ms.openlocfilehash: 73d8b5b308b4d1cb8863f38592647a71e62dd15a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375286"
---
# <a name="element-operations-visual-basic"></a>元素操作（Visual Basic）
元素运算从序列中返回唯一、特定的元素。  
  
 下节列出了执行元素运算的标准查询运算符方法。  
  
## <a name="methods"></a>方法  
  
|方法名|说明|Visual Basic 查询表达式语法|详细信息|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|ElementAt|返回集合中指定索引处的元素。|不适用。|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=nameWithType>|  
|ElementAtOrDefault|返回集合中指定索引处的元素；如果索引超出范围，则返回默认值。|不适用。|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=nameWithType>|  
|First|返回集合的第一个元素或满足条件的第一个元素。|不适用。|<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=nameWithType>|  
|FirstOrDefault|返回集合的第一个元素或满足条件的第一个元素。 如果此类元素不存在，则返回默认值。|不适用。|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=nameWithType>|  
|上一个|返回集合的最后一个元素或满足条件的最后一个元素。|不适用。|<xref:System.Linq.Enumerable.Last%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=nameWithType>|  
|LastOrDefault|返回集合的最后一个元素或满足条件的最后一个元素。 如果此类元素不存在，则返回默认值。|不适用。|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=nameWithType>|  
|Single|返回集合的唯一一个元素或满足条件的唯一一个元素。|不适用。|<xref:System.Linq.Enumerable.Single%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=nameWithType>|  
|SingleOrDefault|返回集合的唯一一个元素或满足条件的唯一一个元素。 如果此类元素不存在，或该集合不是仅包含一个元素，则返回默认值。|不适用。|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Linq>
- [标准查询运算符概述 (Visual Basic)](standard-query-operators-overview.md)
- [如何：查询目录树中的一个或多个最大的文件 (LINQ) (Visual Basic)](how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
