---
title: 如何从文件加载 XML (C#)
description: 了解如何使用 C# 中的 XElement.Load 方法从 URI 加载 XML。 此示例加载 XML 文件并将 XML 树输出到控制台。
ms.date: 07/20/2015
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: 29de914139d1e9abcda2097addca9219d44d2696
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104950"
---
# <a name="how-to-load-xml-from-a-file-c"></a><span data-ttu-id="79171-104">如何从文件加载 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="79171-104">How to load XML from a file (C#)</span></span>
<span data-ttu-id="79171-105">本主题演示如何通过使用 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 方法从 URI 加载 XML。</span><span class="sxs-lookup"><span data-stu-id="79171-105">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79171-106">示例</span><span class="sxs-lookup"><span data-stu-id="79171-106">Example</span></span>  
 <span data-ttu-id="79171-107">下面的示例演示如何从文件加载 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="79171-107">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="79171-108">下面的示例加载 books.xml 并将 XML 树输出到控制台。</span><span class="sxs-lookup"><span data-stu-id="79171-108">The following example loads books.xml and outputs the XML tree to the console.</span></span>  
  
 <span data-ttu-id="79171-109">本示例使用下面的 XML 文档：[示例 XML 文件：图书 (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="79171-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XElement booksFromFile = XElement.Load(@"books.xml");  
Console.WriteLine(booksFromFile);  
```  
  
 <span data-ttu-id="79171-110">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="79171-110">This code produces the following output:</span></span>  
  
```xml  
<Catalog>  
  <Book id="bk101">  
    <Author>Garghentini, Davide</Author>  
    <Title>XML Developer's Guide</Title>  
    <Genre>Computer</Genre>  
    <Price>44.95</Price>  
    <PublishDate>2000-10-01</PublishDate>  
    <Description>An in-depth look at creating applications
      with XML.</Description>  
  </Book>  
  <Book id="bk102">  
    <Author>Garcia, Debra</Author>  
    <Title>Midnight Rain</Title>  
    <Genre>Fantasy</Genre>  
    <Price>5.95</Price>  
    <PublishDate>2000-12-16</PublishDate>  
    <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>  
  </Book>  
</Catalog>  
```  
  