---
title: 如何基于位置查找子元素 (XPath-LINQ to XML) (C#)
description: 了解如何使用 XPath 表达式基于位置查找子元素。 查看使用示例 XML 文件的代码示例。
ms.date: 07/20/2015
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: 2603d3ac94ace645bde1ce85a43a43af7321014e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301666"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a><span data-ttu-id="0eae7-104">如何基于位置查找子元素 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0eae7-104">How to find child elements based on position (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="0eae7-105">有时需要根据元素的位置查找元素。</span><span class="sxs-lookup"><span data-stu-id="0eae7-105">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="0eae7-106">您可能想查找第二个元素，或者查找第三到第五个元素。</span><span class="sxs-lookup"><span data-stu-id="0eae7-106">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="0eae7-107">XPath 表达式为：</span><span class="sxs-lookup"><span data-stu-id="0eae7-107">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="0eae7-108">有两种方法以迟缓方式编写此 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查询。</span><span class="sxs-lookup"><span data-stu-id="0eae7-108">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="0eae7-109">可以使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 运算符，也可以使用接受索引的 <xref:System.Linq.Enumerable.Where%2A> 重载。</span><span class="sxs-lookup"><span data-stu-id="0eae7-109">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="0eae7-110">使用 <xref:System.Linq.Enumerable.Where%2A> 重载时，要使用 lambda 表达式来获得两个参数。</span><span class="sxs-lookup"><span data-stu-id="0eae7-110">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="0eae7-111">下面的示例演示了根据位置选择的这两种方法。</span><span class="sxs-lookup"><span data-stu-id="0eae7-111">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0eae7-112">示例</span><span class="sxs-lookup"><span data-stu-id="0eae7-112">Example</span></span>  
 <span data-ttu-id="0eae7-113">本示例查找第二到第四个 `Test` 元素。</span><span class="sxs-lookup"><span data-stu-id="0eae7-113">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="0eae7-114">结果是一个元素集合。</span><span class="sxs-lookup"><span data-stu-id="0eae7-114">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="0eae7-115">本示例使用下面的 XML 文档：[示例 XML 文件：测试配置 (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="0eae7-115">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement testCfg = XElement.Load("TestConfig.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    testCfg  
    .Elements("Test")  
    .Skip(1)  
    .Take(3);  
  
// LINQ to XML query  
IEnumerable<XElement> list2 =  
    testCfg  
    .Elements("Test")  
    .Where((el, idx) => idx >= 1 && idx <= 3);  
  
// XPath expression  
IEnumerable<XElement> list3 =  
  testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]");  
  
if (list1.Count() == list2.Count() &&  
    list1.Count() == list3.Count() &&  
    list1.Intersect(list2).Count() == list1.Count() &&  
    list1.Intersect(list3).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="0eae7-116">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="0eae7-116">This example produces the following output:</span></span>  
  
```output  
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
