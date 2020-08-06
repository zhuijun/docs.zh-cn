---
title: 如何查找子元素的后代 (XPath-LINQ to XML) (C#)
description: 了解如何使用 XPath 表达式查找具有特定名称的子元素的后代元素。
ms.date: 07/20/2015
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: b8e110abc2e0df99c3fdf6d2846c7cbbc4736c1a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303252"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="db6d4-103">如何查找子元素的后代 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="db6d4-103">How to find descendants of a child element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="db6d4-104">本主题演示如何获取具有特定名称的子元素的后代元素。</span><span class="sxs-lookup"><span data-stu-id="db6d4-104">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="db6d4-105">XPath 表达式为：</span><span class="sxs-lookup"><span data-stu-id="db6d4-105">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="db6d4-106">示例</span><span class="sxs-lookup"><span data-stu-id="db6d4-106">Example</span></span>  
 <span data-ttu-id="db6d4-107">本示例模拟从文字处理文档的 XML 表示形式中提取文本的问题。</span><span class="sxs-lookup"><span data-stu-id="db6d4-107">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="db6d4-108">示例首先选择所有 `Paragraph` 元素，然后选择每个 `Text` 元素的所有 `Paragraph` 后代元素。</span><span class="sxs-lookup"><span data-stu-id="db6d4-108">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="db6d4-109">它不选择 `Text` 元素的后代 `Comment` 元素。</span><span class="sxs-lookup"><span data-stu-id="db6d4-109">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root>  
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
    <Text>  This is a second sentence.</Text>  
  </Paragraph>  
</Root>");  
  
// LINQ to XML query  
string str1 =  
    root  
    .Elements("Paragraph")  
    .Descendants("Text")  
    .Select(s => s.Value)  
    .Aggregate(  
        new StringBuilder(),  
        (s, i) => s.Append(i),  
        s => s.ToString()  
    );  
  
// XPath expression  
string str2 =  
    ((IEnumerable)root.XPathEvaluate("./Paragraph//Text/text()"))  
    .Cast<XText>()  
    .Select(s => s.Value)  
    .Aggregate(  
        new StringBuilder(),  
        (s, i) => s.Append(i),  
        s => s.ToString()  
    );  
  
if (str1 == str2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(str2);  
```  
  
 <span data-ttu-id="db6d4-110">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="db6d4-110">This example produces the following output:</span></span>  
  
```output  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  