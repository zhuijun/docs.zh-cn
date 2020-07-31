---
title: 如何检索特性的集合 (LINQ to XML) (C#)
description: C# 中的 Attributes 方法检索元素的属性。 此 LINQ to XML 示例将循环访问一个元素的属性集合。
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: 5994086db6133530e63eb1328a7b524d30a0797d
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103386"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a>如何检索特性的集合 (LINQ to XML) (C#)
本主题介绍 <xref:System.Xml.Linq.XElement.Attributes%2A> 方法。 此方法检索元素的属性。  
  
## <a name="example"></a>示例  
 下面的示例演示如何循环访问一个元素的属性集合。  
  
```csharp  
XElement val = new XElement("Value",  
    new XAttribute("ID", "1243"),  
    new XAttribute("Type", "int"),  
    new XAttribute("ConvertableTo", "double"),  
    "100");  
IEnumerable<XAttribute> listOfAttributes =  
    from att in val.Attributes()  
    select att;  
foreach (XAttribute a in listOfAttributes)  
    Console.WriteLine(a);  
```  
  
 此代码生成以下输出：  
  
```output  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a>请参阅

- [LINQ to XML 轴 (C#)](./linq-to-xml-axes-overview.md)
