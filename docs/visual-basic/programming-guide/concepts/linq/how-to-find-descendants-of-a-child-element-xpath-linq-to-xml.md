---
title: 如何：查找子元素的后代 (XPath-LINQ to XML)
ms.date: 07/20/2015
ms.assetid: a958af40-f754-4409-85f9-7746978d4cb3
ms.openlocfilehash: aa6a66f4a53fc74b5946a395f7b61218e680f530
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405217"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="63249-102">如何：查找子元素的后代（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="63249-102">How to: Find Descendants of a Child Element (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="63249-103">本主题演示如何获取具有特定名称的子元素的后代元素。</span><span class="sxs-lookup"><span data-stu-id="63249-103">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="63249-104">XPath 表达式为：</span><span class="sxs-lookup"><span data-stu-id="63249-104">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="63249-105">示例</span><span class="sxs-lookup"><span data-stu-id="63249-105">Example</span></span>  
 <span data-ttu-id="63249-106">本示例模拟从文字处理文档的 XML 表示形式中提取文本的问题。</span><span class="sxs-lookup"><span data-stu-id="63249-106">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="63249-107">示例首先选择所有 `Paragraph` 元素，然后选择每个 `Text` 元素的所有 `Paragraph` 后代元素。</span><span class="sxs-lookup"><span data-stu-id="63249-107">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="63249-108">它不选择 `Text` 元素的后代 `Comment` 元素。</span><span class="sxs-lookup"><span data-stu-id="63249-108">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Paragraph>  
            <Text>This is the start of</Text>  
        </Paragraph>  
        <Comment>  
            <Text>This comment is not part of the paragraph text.</Text>  
        </Comment>  
        <Paragraph>  
            <Annotation Emphasis='true'>  
                <Text> a sentence.</Text>  
            </Annotation>  
        </Paragraph>  
        <Paragraph>  
            <Text>This is a second sentence.</Text>  
        </Paragraph>  
    </Root>  
  
' LINQ to XML query  
Dim str1 As String = _  
    root.<Paragraph>...<Text>.Select(Function(ByVal s) s.Value). _  
    Aggregate( _  
        New StringBuilder(), _  
        Function(ByVal s, ByVal i) s.Append(i), _  
        Function(ByVal s) s.ToString())  
  
' XPath expression  
Dim str2 As String = DirectCast(root.XPathEvaluate("./Paragraph//Text/text()"), IEnumerable) _  
    .Cast(Of XText)().Select(Function(ByVal s) s.Value) _  
    .Aggregate( _  
        New StringBuilder(), _  
        Function(ByVal s, ByVal i) s.Append(i), _  
        Function(ByVal s) s.ToString())  
  
If str1 = str2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(str2)  
```  
  
 <span data-ttu-id="63249-109">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="63249-109">This example produces the following output:</span></span>  
  
```console  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  
## <a name="see-also"></a><span data-ttu-id="63249-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="63249-110">See also</span></span>

- [<span data-ttu-id="63249-111">XPath 用户的 LINQ to XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="63249-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
