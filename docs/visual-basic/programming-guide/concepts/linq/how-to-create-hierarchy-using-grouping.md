---
title: 如何：使用分组创建层次结构
ms.date: 07/20/2015
ms.assetid: 4eb3ca6b-1aed-43de-b8b9-41c769c993f8
ms.openlocfilehash: 551a1b8909eb36fea17c93563895296f65794cac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414577"
---
# <a name="how-to-create-hierarchy-using-grouping-visual-basic"></a><span data-ttu-id="30635-102">如何：使用分组创建层次结构（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="30635-102">How to: Create Hierarchy Using Grouping (Visual Basic)</span></span>
<span data-ttu-id="30635-103">本示例演示如何将数据分组，再基于分组生成 XML。</span><span class="sxs-lookup"><span data-stu-id="30635-103">This example shows how to group data, and then generate XML based on the grouping.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30635-104">示例</span><span class="sxs-lookup"><span data-stu-id="30635-104">Example</span></span>  
 <span data-ttu-id="30635-105">本示例首先按类别对数据分组，再生成新的 XML 文件，其中的 XML 层次结构反映了分组。</span><span class="sxs-lookup"><span data-stu-id="30635-105">This example first groups data by a category, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>  
  
 <span data-ttu-id="30635-106">本示例使用下面的 XML 文档：[示例 XML 文件：数值数据 (LINQ to XML)](sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="30635-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim doc As XElement = XElement.Load("Data.xml")  
Dim newData As XElement = _  
    <Root>  
        <%= _  
            From data In doc.<Data> _  
            Group By category = data.<Category>(0).Value _  
            Into groupedData = Group _  
            Select <Group ID=<%= category %>>  
                       <%= _  
                           From g In groupedData _  
                           Select _  
                           <Data>  
                               <%= g.<Quantity>(0) %>  
                               <%= g.<Price>(0) %>  
                           </Data> _  
                       %>  
                   </Group> _  
        %>  
    </Root>  
Console.WriteLine(newData)  
```  
  
 <span data-ttu-id="30635-107">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="30635-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Group ID="A">  
    <Data>  
      <Quantity>3</Quantity>  
      <Price>24.50</Price>  
    </Data>  
    <Data>  
      <Quantity>5</Quantity>  
      <Price>4.95</Price>  
    </Data>  
    <Data>  
      <Quantity>3</Quantity>  
      <Price>66.00</Price>  
    </Data>  
    <Data>  
      <Quantity>15</Quantity>  
      <Price>29.00</Price>  
    </Data>  
  </Group>  
  <Group ID="B">  
    <Data>  
      <Quantity>1</Quantity>  
      <Price>89.99</Price>  
    </Data>  
    <Data>  
      <Quantity>10</Quantity>  
      <Price>.99</Price>  
    </Data>  
    <Data>  
      <Quantity>8</Quantity>  
      <Price>6.99</Price>  
    </Data>  
  </Group>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="30635-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="30635-108">See also</span></span>

- [<span data-ttu-id="30635-109">高级查询技术（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="30635-109">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](advanced-query-techniques-linq-to-xml.md)
