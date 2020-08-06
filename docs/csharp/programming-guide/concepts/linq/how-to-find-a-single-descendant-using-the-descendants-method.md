---
title: 如何使用 Descendants 方法查找单个子代 (C#)
description: 了解如何使用 Descendants 轴方法查找单个子代。 此方法适用于查找具有特定名称的特定子代。
ms.date: 07/20/2015
ms.assetid: 6f735be9-0293-4680-8007-ca9d96bfebed
ms.openlocfilehash: 993e2b45f93509cf526d0c8c5de488b50de3efef
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303330"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-c"></a><span data-ttu-id="53d60-104">如何使用 Descendants 方法查找单个子代 (C#)</span><span class="sxs-lookup"><span data-stu-id="53d60-104">How to find a single descendant using the descendants method (C#)</span></span>
<span data-ttu-id="53d60-105">可以使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 轴方法快速编写代码来查找名称唯一的单个元素。</span><span class="sxs-lookup"><span data-stu-id="53d60-105">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to quickly write code to find a single uniquely named element.</span></span> <span data-ttu-id="53d60-106">如果想要查找具有特定名称的特定后代，则此技术特别有用。</span><span class="sxs-lookup"><span data-stu-id="53d60-106">This technique is especially useful when you want to find a particular descendant with a specific name.</span></span> <span data-ttu-id="53d60-107">虽然可以编写代码以导航到需要的元素，但使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 轴编写代码通常更快更容易。</span><span class="sxs-lookup"><span data-stu-id="53d60-107">You could write the code to navigate to the desired element, but it is often faster and easier to write the code using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53d60-108">示例</span><span class="sxs-lookup"><span data-stu-id="53d60-108">Example</span></span>  
 <span data-ttu-id="53d60-109">本示例使用 <xref:System.Linq.Enumerable.First%2A> 标准查询运算符。</span><span class="sxs-lookup"><span data-stu-id="53d60-109">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <GrandChild1>GC1 Value</GrandChild1>  
  </Child1>  
  <Child2>  
    <GrandChild2>GC2 Value</GrandChild2>  
  </Child2>  
  <Child3>  
    <GrandChild3>GC3 Value</GrandChild3>  
  </Child3>  
  <Child4>  
    <GrandChild4>GC4 Value</GrandChild4>  
  </Child4>  
</Root>");  
string grandChild3 = (string)  
    (from el in root.Descendants("GrandChild3")  
    select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 <span data-ttu-id="53d60-110">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="53d60-110">This code produces the following output:</span></span>  
  
```output  
GC3 Value  
```  
  
## <a name="example"></a><span data-ttu-id="53d60-111">示例</span><span class="sxs-lookup"><span data-stu-id="53d60-111">Example</span></span>  
 <span data-ttu-id="53d60-112">下面的示例演示如何对命名空间中的 XML 进行同样的查询。</span><span class="sxs-lookup"><span data-stu-id="53d60-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="53d60-113">有关详细信息，请参阅[命名空间概述(LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="53d60-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
  <aw:Child1>  
    <aw:GrandChild1>GC1 Value</aw:GrandChild1>  
  </aw:Child1>  
  <aw:Child2>  
    <aw:GrandChild2>GC2 Value</aw:GrandChild2>  
  </aw:Child2>  
  <aw:Child3>  
    <aw:GrandChild3>GC3 Value</aw:GrandChild3>  
  </aw:Child3>  
  <aw:Child4>  
    <aw:GrandChild4>GC4 Value</aw:GrandChild4>  
  </aw:Child4>  
</aw:Root>");  
XNamespace aw = "http://www.adventure-works.com";  
string grandChild3 = (string)  
    (from el in root.Descendants(aw + "GrandChild3")  
     select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 <span data-ttu-id="53d60-114">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="53d60-114">This code produces the following output:</span></span>  
  
```output  
GC3 Value  
```  
