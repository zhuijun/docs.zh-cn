---
title: XAttribute 类概述
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: 5b165044b4bea83e1a0789e3dd00367ed27b43e8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413201"
---
# <a name="xattribute-class-overview-visual-basic"></a>System.xml.linq.xattribute> 类概述（Visual Basic）
属性是与元素关联的名称/值对。 <xref:System.Xml.Linq.XAttribute> 类表示 XML 属性。  
  
## <a name="overview"></a>概述  
 使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的属性，与使用元素非常相似。 它们的构造函数相似。 用于检索它们的集合的方法相似。 属性集合的 LINQ 查询表达式与元素集合的 LINQ 查询表达式看起来非常相似。  
  
 将属性添加到元素中的顺序会保留下来。 也就是说，当循环访问属性时，所见到的属性顺序与它们的添加顺序相同。  
  
## <a name="the-xattribute-constructor"></a>XAttribute 构造函数  
 下面的 <xref:System.Xml.Linq.XAttribute> 类构造函数是您将最常使用的构造函数之一：  
  
|构造函数|说明|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|创建一个 <xref:System.Xml.Linq.XAttribute> 对象。 `name` 参数指定属性的名称；`content` 指定属性的内容。|  
  
### <a name="creating-an-element-with-an-attribute"></a>创建具有属性的元素  
 下面的代码演示一个元素，该元素包含在 Visual Basic 中使用 XML 文本的属性：  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 该示例产生下面的输出：  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>属性的函数构造  
 可以构造与 <xref:System.Xml.Linq.XAttribute> 对象的构造一致的 <xref:System.Xml.Linq.XElement> 对象，如下所示：  
  
```vb  
Dim c As XElement = _  
    <Customers>  
        <Customer>  
            <Name>John Doe</Name>  
            <PhoneNumbers>  
                <Phone type="home">555-555-5555</Phone>  
                <Phone type="work">666-666-6666</Phone>  
            </PhoneNumbers>  
        </Customer>  
    </Customers>  
Console.WriteLine(c)  
```  
  
 该示例产生下面的输出：  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a>属性不是节点  
 属性与元素之间有些区别。 <xref:System.Xml.Linq.XAttribute> 对象不是 XML 树中的节点。 它们是与 XML 元素关联的名称/值对。 与文档对象模型 (DOM) 相比，这更加贴切地反映了 XML 结构。 虽然 <xref:System.Xml.Linq.XAttribute> 对象实际上不是 XML 树的节点，但使用 <xref:System.Xml.Linq.XAttribute> 对象与使用 <xref:System.Xml.Linq.XElement> 对象非常相似。  
  
 这一区别仅对编写在节点级使用 XML 树的代码的开发人员特别重要。 许多开发人员不会关心这种区别。  
  
## <a name="see-also"></a>另请参阅

- [LINQ to XML 编程概述（Visual Basic）](linq-to-xml-programming-overview.md)
