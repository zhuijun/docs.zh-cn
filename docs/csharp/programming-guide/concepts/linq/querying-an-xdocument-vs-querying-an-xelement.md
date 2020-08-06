---
title: 查询 XDocument 与查询 XElement (C#)
description: 了解查询 XDocument 与查询 XElement 之间的差异。 查看展示这些差异的代码示例。
ms.date: 07/20/2015
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 0c81768f06148308a639f96f4041e464b24edd33
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300301"
---
# <a name="querying-an-xdocument-vs-querying-an-xelement-c"></a><span data-ttu-id="1319f-104">查询 XDocument 与查询 XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="1319f-104">Querying an XDocument vs. Querying an XElement (C#)</span></span>
<span data-ttu-id="1319f-105">通过 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> 加载文档时，您会注意到，您要编写的查询与通过 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 加载文档时稍有不同。</span><span class="sxs-lookup"><span data-stu-id="1319f-105">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="1319f-106">XDocument.Load 与 XElement.Load 的比较</span><span class="sxs-lookup"><span data-stu-id="1319f-106">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="1319f-107">通过 <xref:System.Xml.Linq.XElement> 将 XML 文档加载到 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 中时，位于 XML 树根部的 <xref:System.Xml.Linq.XElement> 包含所加载文档的根元素。</span><span class="sxs-lookup"><span data-stu-id="1319f-107">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="1319f-108">然而，通过 <xref:System.Xml.Linq.XDocument> 将同一个 XML 文档加载到 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> 中时，树根部为 <xref:System.Xml.Linq.XDocument> 节点，所加载文档的根元素为 <xref:System.Xml.Linq.XElement> 所允许的一个子 <xref:System.Xml.Linq.XDocument> 节点。</span><span class="sxs-lookup"><span data-stu-id="1319f-108">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="1319f-109">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 轴相对于根节点进行操作。</span><span class="sxs-lookup"><span data-stu-id="1319f-109">The [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="1319f-110">第一个示例使用 <xref:System.Xml.Linq.XElement.Load%2A> 加载 XML 树。</span><span class="sxs-lookup"><span data-stu-id="1319f-110">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="1319f-111">然后它查询树根部的子元素。</span><span class="sxs-lookup"><span data-stu-id="1319f-111">It then queries for the child elements of the root of the tree.</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XElement.Load");  
Console.WriteLine("----");  
XElement doc = XElement.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="1319f-112">此示例将按预期产生以下输出：</span><span class="sxs-lookup"><span data-stu-id="1319f-112">As expected, this example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="1319f-113">下面的示例与上面的基本相同，不同之处在于 XML 树是加载到 <xref:System.Xml.Linq.XDocument>，而不是加载到 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="1319f-113">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="1319f-114">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="1319f-114">This example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="1319f-115">请注意，同样的查询返回一个 `Root` 节点，而不是返回三个子节点。</span><span class="sxs-lookup"><span data-stu-id="1319f-115">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="1319f-116">处理这一问题的一种方法是在访问轴方法之前使用 <xref:System.Xml.Linq.XDocument.Root%2A> 属性，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1319f-116">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
```csharp  
// Create a simple document and write it to a file  
File.WriteAllText("Test.xml", @"<Root>  
    <Child1>1</Child1>  
    <Child2>2</Child2>  
    <Child3>3</Child3>  
</Root>");  
  
Console.WriteLine("Querying tree loaded with XDocument.Load");  
Console.WriteLine("----");  
XDocument doc = XDocument.Load("Test.xml");  
IEnumerable<XElement> childList =  
    from el in doc.Root.Elements()  
    select el;  
foreach (XElement e in childList)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="1319f-117">此查询现在的执行方式与根部位于 <xref:System.Xml.Linq.XElement> 中的树中的查询相同。</span><span class="sxs-lookup"><span data-stu-id="1319f-117">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="1319f-118">此示例产生以下输出：</span><span class="sxs-lookup"><span data-stu-id="1319f-118">The example produces the following output:</span></span>  
  
```output  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  