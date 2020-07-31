---
title: 如何使用 XPath 查询 LINQ to XML (C#)
description: 你可通过 C# 中的扩展方法，使用 XPath 查询 XML 树。 通常，我们不建议将 XPath 与 LINQ to XML 一起使用。
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: fff45a93380b5af85aa640fc690783cc95e6298b
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104348"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a><span data-ttu-id="6bead-104">如何使用 XPath 查询 LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6bead-104">How to query LINQ to XML using XPath (C#)</span></span>
<span data-ttu-id="6bead-105">本主题介绍一些扩展方法，通过这些扩展方法可以使用 XPath 查询 XML 树。</span><span class="sxs-lookup"><span data-stu-id="6bead-105">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="6bead-106">有关使用这些扩展方法的详细信息，请参见 <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="6bead-106">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="6bead-107">除非有很特别的理由（例如大量使用旧代码）需要使用 XPath 进行查询，否则不建议将 XPath 用于 LINQ to XML。</span><span class="sxs-lookup"><span data-stu-id="6bead-107">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="6bead-108">XPath 查询的执行性能比 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查询低。</span><span class="sxs-lookup"><span data-stu-id="6bead-108">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bead-109">示例</span><span class="sxs-lookup"><span data-stu-id="6bead-109">Example</span></span>  
 <span data-ttu-id="6bead-110">下面的示例创建一个小型 XML 树，并使用 <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> 选择一组元素。</span><span class="sxs-lookup"><span data-stu-id="6bead-110">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child1", 2),  
    new XElement("Child1", 3),  
    new XElement("Child2", 4),  
    new XElement("Child2", 5),  
    new XElement("Child2", 6)  
);  
IEnumerable<XElement> list = root.XPathSelectElements("./Child2");  
foreach (XElement el in list)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="6bead-111">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="6bead-111">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  