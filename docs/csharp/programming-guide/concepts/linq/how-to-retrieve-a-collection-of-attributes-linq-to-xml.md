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
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="145e5-104">如何检索特性的集合 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="145e5-104">How to retrieve a collection of attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="145e5-105">本主题介绍 <xref:System.Xml.Linq.XElement.Attributes%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="145e5-105">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="145e5-106">此方法检索元素的属性。</span><span class="sxs-lookup"><span data-stu-id="145e5-106">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="145e5-107">示例</span><span class="sxs-lookup"><span data-stu-id="145e5-107">Example</span></span>  
 <span data-ttu-id="145e5-108">下面的示例演示如何循环访问一个元素的属性集合。</span><span class="sxs-lookup"><span data-stu-id="145e5-108">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="145e5-109">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="145e5-109">This code produces the following output:</span></span>  
  
```output  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="145e5-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="145e5-110">See also</span></span>

- [<span data-ttu-id="145e5-111">LINQ to XML 轴 (C#)</span><span class="sxs-lookup"><span data-stu-id="145e5-111">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
