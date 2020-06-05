---
title: 如何：根据位置查找子元素 (XPath-LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 6831e1db-5e97-444f-a7a1-d0a87104b005
ms.openlocfilehash: d6dd1150ae3e4ad586e476b777b1f7d47d60c261
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405256"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="a40ee-102">如何：基于位置查找子元素（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="a40ee-102">How to: Find Child Elements Based on Position (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="a40ee-103">有时需要根据元素的位置查找元素。</span><span class="sxs-lookup"><span data-stu-id="a40ee-103">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="a40ee-104">您可能想查找第二个元素，或者查找第三到第五个元素。</span><span class="sxs-lookup"><span data-stu-id="a40ee-104">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="a40ee-105">XPath 表达式为：</span><span class="sxs-lookup"><span data-stu-id="a40ee-105">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="a40ee-106">有两种方法以迟缓方式编写此 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查询。</span><span class="sxs-lookup"><span data-stu-id="a40ee-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="a40ee-107">可以使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 运算符，也可以使用接受索引的 <xref:System.Linq.Enumerable.Where%2A> 重载。</span><span class="sxs-lookup"><span data-stu-id="a40ee-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="a40ee-108">使用 <xref:System.Linq.Enumerable.Where%2A> 重载时，要使用 lambda 表达式来获得两个参数。</span><span class="sxs-lookup"><span data-stu-id="a40ee-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="a40ee-109">下面的示例演示了根据位置选择的这两种方法。</span><span class="sxs-lookup"><span data-stu-id="a40ee-109">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a40ee-110">示例</span><span class="sxs-lookup"><span data-stu-id="a40ee-110">Example</span></span>  
 <span data-ttu-id="a40ee-111">本示例查找第二到第四个 `Test` 元素。</span><span class="sxs-lookup"><span data-stu-id="a40ee-111">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="a40ee-112">结果是一个元素集合。</span><span class="sxs-lookup"><span data-stu-id="a40ee-112">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="a40ee-113">本示例使用以下 XML 文档：[示例 XML 文件：测试配置 (LINQ to XML)](sample-xml-file-test-configuration-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="a40ee-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```vb  
Dim testCfg As XElement = XElement.Load("TestConfig.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    testCfg.Elements("Test").Skip(1).Take(3)  
  
'LINQ to XML query  
Dim list2 As IEnumerable(Of XElement) = _  
    testCfg.Elements("Test"). _  
    Where(Function(ByVal el, ByVal idx) idx >= 1 And idx <= 3)  
  
' XPath expression  
Dim list3 As IEnumerable(Of XElement) = _  
    testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]")  
  
If list1.Count() = list2.Count() And _  
       list1.Count() = list3.Count() And _  
       list1.Intersect(list2).Count() = list1.Count() And _  
       list1.Intersect(list3).Count() = list1.Count() Then  
  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="a40ee-114">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="a40ee-114">This example produces the following output:</span></span>  
  
```console  
Results are identical  
<Test TestId="0002" TestType="CMD">  
  <Name>Find succeeding characters</Name>  
  <CommandLine>Examp2.EXE</CommandLine>  
  <Input>abc</Input>  
  <Output>def</Output>  
</Test>  
<Test TestId="0003" TestType="GUI">  
  <Name>Convert multiple numbers to strings</Name>  
  <CommandLine>Examp2.EXE /Verbose</CommandLine>  
  <Input>123</Input>  
  <Output>One Two Three</Output>  
</Test>  
<Test TestId="0004" TestType="GUI">  
  <Name>Find correlated key</Name>  
  <CommandLine>Examp3.EXE</CommandLine>  
  <Input>a1</Input>  
  <Output>b1</Output>  
</Test>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a40ee-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="a40ee-115">See also</span></span>

- [<span data-ttu-id="a40ee-116">XPath 用户的 LINQ to XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="a40ee-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
