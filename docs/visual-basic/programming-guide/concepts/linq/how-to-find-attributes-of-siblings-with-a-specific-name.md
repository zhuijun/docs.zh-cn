---
title: 如何：查找具有特定名称的同级的属性 (XPath-LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 83b3ddca-830a-4b71-9756-9e4bdf907302
ms.openlocfilehash: 0317e03de6f671991d6d0a4247ca2e9c172439b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405269"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="c61e0-102">如何：查找具有特定名称的同级的特性（XPath LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="c61e0-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="c61e0-103">本主题演示如何查找上下文节点的同级的所有属性。</span><span class="sxs-lookup"><span data-stu-id="c61e0-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="c61e0-104">只返回集合中具有特定名称的属性。</span><span class="sxs-lookup"><span data-stu-id="c61e0-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="c61e0-105">XPath 表达式为：</span><span class="sxs-lookup"><span data-stu-id="c61e0-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="c61e0-106">示例</span><span class="sxs-lookup"><span data-stu-id="c61e0-106">Example</span></span>  
 <span data-ttu-id="c61e0-107">本示例首先查找 `Book` 元素，然后查找名为 `Book` 的所有同级元素，再查找名为 `id` 的所有属性。</span><span class="sxs-lookup"><span data-stu-id="c61e0-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="c61e0-108">结果是一个属性集合。</span><span class="sxs-lookup"><span data-stu-id="c61e0-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="c61e0-109">本示例使用以下 XML 文档：[示例 XML 文件：图书 (LINQ to XML)](sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="c61e0-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim books as XDocument = XDocument.Load("Books.xml")  
Dim book As XElement = books.Root.<Book>(0)  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XAttribute) = _  
    From el In book.Parent.<Book> _  
    Select el.Attribute("id")  
  
' XPath expression  
Dim list2 As IEnumerable(Of XAttribute) = DirectCast(book. _  
    XPathEvaluate("../Book/@id"), IEnumerable).Cast(Of XAttribute)()  
  
If list1.Count() = list2.Count() And _  
        (list1.Intersect(list2)).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XAttribute In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="c61e0-110">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="c61e0-110">This example produces the following output:</span></span>  
  
```console  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a><span data-ttu-id="c61e0-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="c61e0-111">See also</span></span>

- [<span data-ttu-id="c61e0-112">XPath 用户的 LINQ to XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="c61e0-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
