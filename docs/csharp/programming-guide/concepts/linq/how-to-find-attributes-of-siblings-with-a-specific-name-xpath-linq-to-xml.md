---
title: 如何查找具有特定名称的同级属性 (XPath-LINQ to XML) (C#)
description: 了解如何查找上下文节点同级的所有属性。 查看使用示例 XML 文件的代码示例。
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 12bba22c91fef92fc3383d028ff9dfb8bd3cfa3e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301692"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="4cd83-104">如何查找具有特定名称的同级属性 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4cd83-104">How to find attributes of siblings with a specific name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="4cd83-105">本主题演示如何查找上下文节点的同级的所有属性。</span><span class="sxs-lookup"><span data-stu-id="4cd83-105">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="4cd83-106">只返回集合中具有特定名称的属性。</span><span class="sxs-lookup"><span data-stu-id="4cd83-106">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="4cd83-107">XPath 表达式为：</span><span class="sxs-lookup"><span data-stu-id="4cd83-107">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="4cd83-108">示例</span><span class="sxs-lookup"><span data-stu-id="4cd83-108">Example</span></span>  
 <span data-ttu-id="4cd83-109">本示例首先查找 `Book` 元素，然后查找名为 `Book` 的所有同级元素，再查找名为 `id` 的所有属性。</span><span class="sxs-lookup"><span data-stu-id="4cd83-109">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="4cd83-110">结果是一个属性集合。</span><span class="sxs-lookup"><span data-stu-id="4cd83-110">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="4cd83-111">本示例使用下面的 XML 文档：[示例 XML 文件：图书 (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="4cd83-111">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =
    books  
    .Root  
    .Element("Book");  
  
// LINQ to XML query  
IEnumerable<XAttribute> list1 =  
    from el in book.Parent.Elements("Book")  
    select el.Attribute("id");  
  
// XPath expression  
IEnumerable<XAttribute> list2 =  
  ((IEnumerable)book.XPathEvaluate("../Book/@id")).Cast<XAttribute>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XAttribute el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="4cd83-112">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="4cd83-112">This example produces the following output:</span></span>  
  
```output  
Results are identical  
id="bk101"  
id="bk102"  
```  
  