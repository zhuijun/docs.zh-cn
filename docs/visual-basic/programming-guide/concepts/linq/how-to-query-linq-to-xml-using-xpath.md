---
title: 如何：使用 XPath 查询 LINQ to XML
ms.date: 07/20/2015
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
ms.openlocfilehash: d95e5a82d146c357f52d03375119474b042d49f6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397916"
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a><span data-ttu-id="67457-102">如何：使用 XPath 查询 LINQ to XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="67457-102">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>
<span data-ttu-id="67457-103">本主题介绍一些扩展方法，通过这些扩展方法可以使用 XPath 查询 XML 树。</span><span class="sxs-lookup"><span data-stu-id="67457-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="67457-104">有关使用这些扩展方法的详细信息，请参见 <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="67457-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="67457-105">除非有很特别的理由（例如大量使用旧代码）需要使用 XPath 进行查询，否则不建议将 XPath 用于 LINQ to XML。</span><span class="sxs-lookup"><span data-stu-id="67457-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="67457-106">XPath 查询的执行性能比 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查询低。</span><span class="sxs-lookup"><span data-stu-id="67457-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67457-107">示例</span><span class="sxs-lookup"><span data-stu-id="67457-107">Example</span></span>  
 <span data-ttu-id="67457-108">下面的示例创建一个小型 XML 树，并使用 <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> 选择一组元素。</span><span class="sxs-lookup"><span data-stu-id="67457-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child1>2</Child1>  
        <Child1>3</Child1>  
        <Child2>4</Child2>  
        <Child2>5</Child2>  
        <Child2>6</Child2>  
    </Root>  
  
Dim list As IEnumerable(Of XElement) = root.XPathSelectElements("./Child2")  
For Each el As XElement In list  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="67457-109">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="67457-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="67457-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="67457-110">See also</span></span>

- [<span data-ttu-id="67457-111">高级查询技术（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="67457-111">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](advanced-query-techniques-linq-to-xml.md)
