---
title: 如何：检索元素的浅值
ms.date: 07/20/2015
ms.assetid: 730a6670-fb8c-41fc-8a1b-eb97a837e432
ms.openlocfilehash: 24e6b128481f56941f0a61da9766f02813a46e97
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397812"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-visual-basic"></a><span data-ttu-id="d6fee-102">如何：检索元素的浅值（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d6fee-102">How to: Retrieve the Shallow Value of an Element (Visual Basic)</span></span>

<span data-ttu-id="d6fee-103">本主题说明如何获取元素的浅值。</span><span class="sxs-lookup"><span data-stu-id="d6fee-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="d6fee-104">浅值只是特定元素的值，与深值相反，包括串联成一个单一字符串的所有子元素的值。</span><span class="sxs-lookup"><span data-stu-id="d6fee-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>

<span data-ttu-id="d6fee-105">使用强制转换或 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 属性检索元素值时，您可以检索深值。</span><span class="sxs-lookup"><span data-stu-id="d6fee-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="d6fee-106">要检索浅值，可以使用 `ShallowValue` 扩展方法，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="d6fee-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="d6fee-107">当根据内容选择元素时，检索浅值十分有用。</span><span class="sxs-lookup"><span data-stu-id="d6fee-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>

<span data-ttu-id="d6fee-108">下面的示例声明了检索元素浅值的扩展方法。</span><span class="sxs-lookup"><span data-stu-id="d6fee-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="d6fee-109">然后在查询中使用该扩展方法列出包含计算得出的值的所有元素。</span><span class="sxs-lookup"><span data-stu-id="d6fee-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>

## <a name="example"></a><span data-ttu-id="d6fee-110">示例</span><span class="sxs-lookup"><span data-stu-id="d6fee-110">Example</span></span>

<span data-ttu-id="d6fee-111">下面的文本文件 Report.xml 是此示例的源。</span><span class="sxs-lookup"><span data-stu-id="d6fee-111">The following text file, Report.xml, is the source for this example.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Report>
  <Section>
    <Heading>
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>
      <Column Name="Name">=Customer.Name.Heading</Column>
    </Heading>
    <Detail>
      <Column Name="CustomerId">=Customer.CustomerId</Column>
      <Column Name="Name">=Customer.Name</Column>
    </Detail>
  </Section>
</Report>
```

```vb
Module Module1
    <System.Runtime.CompilerServices.Extension()> _
    Public Function ShallowValue(ByVal xe As XElement)
        Return xe _
               .Nodes() _
               .OfType(Of XText)() _
               .Aggregate(New StringBuilder(), _
                              Function(s, c) s.Append(c), _
                              Function(s) s.ToString())
    End Function

    Sub Main()
        Dim root As XElement = XElement.Load("Report.xml")

        Dim query As IEnumerable(Of XElement) = _
            From el In root.Descendants() _
            Where (el.ShallowValue().StartsWith("=")) _
            Select el

        For Each q As XElement In query
            Console.WriteLine("{0}{1}{2}", _
                q.Name.ToString().PadRight(8), _
                q.Attribute("Name").ToString().PadRight(20), _
                q.ShallowValue())
        Next
    End Sub
End Module
```

<span data-ttu-id="d6fee-112">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="d6fee-112">This example produces the following output:</span></span>

```console
Column  Name="CustomerId"   =Customer.CustomerId.Heading
Column  Name="Name"         =Customer.Name.Heading
Column  Name="CustomerId"   =Customer.CustomerId
Column  Name="Name"         =Customer.Name
```

## <a name="see-also"></a><span data-ttu-id="d6fee-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d6fee-113">See also</span></span>

- [<span data-ttu-id="d6fee-114">LINQ to XML 轴 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6fee-114">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
