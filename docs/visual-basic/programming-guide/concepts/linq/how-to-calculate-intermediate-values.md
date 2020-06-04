---
title: 如何：计算中间值
ms.date: 07/20/2015
ms.assetid: 933a97b2-dfe7-4f4d-94ad-e6e20df84abd
ms.openlocfilehash: bc38d4848a26a24aeb00581079c9dd31abb7ba1e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375091"
---
# <a name="how-to-calculate-intermediate-values-visual-basic"></a>如何：计算中间值（Visual Basic）
本示例演示如何计算可用于进行排序、筛选和选择的中间值。  
  
## <a name="example"></a>示例  
 下面的示例使用 `Let` 子句。  
  
 本示例使用下面的 XML 文档：[示例 XML 文件：数值数据 (LINQ to XML)](sample-xml-file-numerical-data-linq-to-xml.md)。  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim extensions As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
    Where extension > 25 _  
    Order By extension _  
    Select extension  
For Each ex As Decimal In extensions  
    Console.WriteLine(ex)  
Next  
```  
  
 此代码生成以下输出：  
  
```console  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何对命名空间中的 XML 进行同样的查询。 有关详细信息，请参阅[命名空间概述（LINQ to XML）（Visual Basic）](namespaces-overview-linq-to-xml.md)。  
  
 本示例使用下面的 XML 文档：[示例 XML 文件：命名空间中的数值数据](sample-xml-file-numerical-data-in-a-namespace.md)。  
  
```vb  
Imports <xmlns="http://www.adatum.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim extensions As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
            Where extension > 25 _  
            Order By extension _  
            Select extension  
        For Each ex As Decimal In extensions  
            Console.WriteLine(ex)  
        Next  
    End Sub  
End Module  
```  
  
 此代码生成以下输出：  
  
```console  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a>另请参阅

- [基本查询（LINQ to XML）（Visual Basic）](basic-queries-linq-to-xml.md)
