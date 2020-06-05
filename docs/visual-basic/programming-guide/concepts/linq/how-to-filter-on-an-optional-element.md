---
title: 如何：根据可选元素进行筛选
ms.date: 07/20/2015
ms.assetid: a74b76ad-6889-4185-a189-d6ef2c63841e
ms.openlocfilehash: 9f03eee479e7c47e528a145d370472de6dfddd39
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394358"
---
# <a name="how-to-filter-on-an-optional-element-visual-basic"></a>如何：筛选可选元素（Visual Basic）
有时，尽管不能确定某个元素是否存在于 XML 文档中，您还是会尝试筛选该元素。 应当执行搜索，这样如果特定元素没有子元素，就不会因为筛选它而触发空引用异常。 在下面的示例中，`Child5` 元素没有 `Type` 子元素，但是查询仍可以正确执行。  
  
## <a name="example"></a>示例  
 本示例使用 <xref:System.Xml.Linq.Extensions.Elements%2A> 扩展方法。  
  
```vb  
Dim root As XElement = _
    <Root>  
        <Child1>  
            <Text>Child One Text</Text>  
            <Type Value="Yes"/>  
        </Child1>  
        <Child2>  
            <Text>Child Two Text</Text>  
            <Type Value="Yes"/>  
        </Child2>  
        <Child3>  
            <Text>Child Three Text</Text>  
            <Type Value="No"/>  
        </Child3>  
        <Child4>  
            <Text>Child Four Text</Text>  
            <Type Value="Yes"/>  
        </Child4>  
        <Child5>  
            <Text>Child Five Text</Text>  
        </Child5>  
    </Root>  
Dim cList As IEnumerable(Of String) = _  
    From typeElement In root.Elements().<Type> _  
    Where typeElement.@Value = "Yes" _  
    Select typeElement.Parent.<Text>.Value  
Dim str As String  
For Each str In cList  
    Console.WriteLine(str)  
Next  
```  
  
 此代码生成以下输出：  
  
```console  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何对命名空间中的 XML 进行同样的查询。 有关详细信息，请参阅[命名空间概述（LINQ to XML）（Visual Basic）](namespaces-overview-linq-to-xml.md)。  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child1>  
                    <Text>Child One Text</Text>  
                    <Type Value="Yes"/>  
                </Child1>  
                <Child2>  
                    <Text>Child Two Text</Text>  
                    <Type Value="Yes"/>  
                </Child2>  
                <Child3>  
                    <Text>Child Three Text</Text>  
                    <Type Value="No"/>  
                </Child3>  
                <Child4>  
                    <Text>Child Four Text</Text>  
                    <Type Value="Yes"/>  
                </Child4>  
                <Child5>  
                    <Text>Child Five Text</Text>  
                </Child5>  
            </Root>  
        Dim cList As IEnumerable(Of String) = _  
            From typeElement In root.Elements().<Type> _  
            Where typeElement.@Value = "Yes" _  
            Select typeElement.Parent.<Text>.Value  
        Dim str As String  
        For Each str In cList  
            Console.WriteLine(str)  
        Next  
    End Sub  
End Module  
```  
  
 此代码生成以下输出：  
  
```console  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [基本查询（LINQ to XML）（Visual Basic）](basic-queries-linq-to-xml.md)
- [XML Child Axis Property](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [XML Attribute Axis Property](../../../language-reference/xml-axis/xml-attribute-axis-property.md)
- [XML 值属性](../../../language-reference/xml-axis/xml-value-property.md)
- [标准查询运算符概述 (Visual Basic)](standard-query-operators-overview.md)
- [投影操作（Visual Basic）](projection-operations.md)
