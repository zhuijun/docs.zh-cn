---
title: 使用 XPath 导航选择节点
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
ms.openlocfilehash: 85f3ae9ec9f3b4d0949a893dd1e59fbbda139066
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291456"
---
# <a name="select-nodes-using-xpath-navigation"></a><span data-ttu-id="04ea5-102">使用 XPath 导航选择节点</span><span class="sxs-lookup"><span data-stu-id="04ea5-102">Select Nodes Using XPath Navigation</span></span>
<span data-ttu-id="04ea5-103">XML 文档对象模型 (DOM) 包含的方法使您可以使用 XML 路径语言 (XPath) 浏览功能查询 DOM 中的信息。</span><span class="sxs-lookup"><span data-stu-id="04ea5-103">The XML Document Object Model (DOM) contains methods that allow you to use XML Path Language (XPath) navigation to query information in the DOM.</span></span> <span data-ttu-id="04ea5-104">可以使用 XPath 查找单个特定节点，或查找与某个条件匹配的所有节点。</span><span class="sxs-lookup"><span data-stu-id="04ea5-104">You can use XPath to find a single, specific node or to find all nodes that match some criteria.</span></span>  
  
## <a name="xpath-select-methods"></a><span data-ttu-id="04ea5-105">XPath 选择方法</span><span class="sxs-lookup"><span data-stu-id="04ea5-105">XPath Select Methods</span></span>  
 <span data-ttu-id="04ea5-106">DOM 类提供两种 XPath 选择方法：<xref:System.Xml.XmlNode.SelectSingleNode%2A> 方法和 <xref:System.Xml.XmlNode.SelectNodes%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="04ea5-106">The DOM classes provide two methods for XPath selection: the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method and the <xref:System.Xml.XmlNode.SelectNodes%2A> method.</span></span> <span data-ttu-id="04ea5-107"><xref:System.Xml.XmlNode.SelectSingleNode%2A> 方法返回符合选择条件的第一个节点。</span><span class="sxs-lookup"><span data-stu-id="04ea5-107">The <xref:System.Xml.XmlNode.SelectSingleNode%2A> method returns the first node that matches the selection criteria.</span></span> <span data-ttu-id="04ea5-108"><xref:System.Xml.XmlNode.SelectNodes%2A> 方法返回包含匹配节点的 <xref:System.Xml.XmlNodeList>。</span><span class="sxs-lookup"><span data-stu-id="04ea5-108">The <xref:System.Xml.XmlNode.SelectNodes%2A> method returns an <xref:System.Xml.XmlNodeList> that contains the matching nodes.</span></span>  
  
 <span data-ttu-id="04ea5-109">下面的示例使用 <xref:System.Xml.XmlNode.SelectSingleNode%2A> 方法来选择其作者姓氏符合指定条件的第一个 `book` 节点。</span><span class="sxs-lookup"><span data-stu-id="04ea5-109">The following example uses the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method to select the first `book` node in which the author's last name meets the specified criteria.</span></span> <span data-ttu-id="04ea5-110">bookstore.xml 文件（在本主题末尾提供）用作输入文件。</span><span class="sxs-lookup"><span data-stu-id="04ea5-110">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select and display the first node in which the author's
' last name is Kingsolver.  
Dim node As XmlNode = root.SelectSingleNode( _  
     "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr)  
Console.WriteLine(node.InnerXml)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select and display the first node in which the author's
// last name is Kingsolver.  
XmlNode node = root.SelectSingleNode(  
    "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr);  
Console.WriteLine(node.InnerXml);  
```  
  
 <span data-ttu-id="04ea5-111">下一个示例使用 <xref:System.Xml.XmlNode.SelectNodes%2A> 方法来选择其价格大于指定金额的所有书节点。</span><span class="sxs-lookup"><span data-stu-id="04ea5-111">The next example uses the <xref:System.Xml.XmlNode.SelectNodes%2A> method to select all the book nodes in which the price is greater than a specified amount.</span></span> <span data-ttu-id="04ea5-112">然后，以编程方式将选定列表中的每本书的价格减去 10%。</span><span class="sxs-lookup"><span data-stu-id="04ea5-112">The price for each book in the selected list is then programmatically reduced by ten percent.</span></span> <span data-ttu-id="04ea5-113">最后，将更新的文件写入控制台。</span><span class="sxs-lookup"><span data-stu-id="04ea5-113">Finally, the updated file is written to the console.</span></span> <span data-ttu-id="04ea5-114">bookstore.xml 文件（在本主题末尾提供）用作输入文件。</span><span class="sxs-lookup"><span data-stu-id="04ea5-114">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
' Load the document and set the root element.  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select all nodes where the book price is greater than 10.00.  
Dim nodeList As XmlNodeList = root.SelectNodes( _  
     "descendant::bk:book[bk:price>10.00]", nsmgr)  
For Each book As XmlNode In nodeList  
     Dim price As Double  
     price = Math.Round(Convert.ToSingle( _  
          book.LastChild.InnerText) * 0.9, 2)  
     book.LastChild.InnerText = price.ToString()  
Next  
  
' Display the updated document.  
doc.Save(Console.Out)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select all nodes where the book price is greater than 10.00.  
XmlNodeList nodeList = root.SelectNodes(  
     "descendant::bk:book[bk:price>10.00]", nsmgr);  
foreach (XmlNode book in nodeList)  
{  
     // Discount prices by 10%.  
     double price;  
     price = Math.Round(Convert.ToSingle(  
          book.LastChild.InnerText) * 0.9, 2);  
     book.LastChild.InnerText = price.ToString();  
}  
  
// Display the updated document.  
doc.Save(Console.Out);  
```  
  
 <span data-ttu-id="04ea5-115">上面的示例从文档元素开始执行 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="04ea5-115">The examples above start the XPath query at the document element.</span></span> <span data-ttu-id="04ea5-116">设置 XPath 查询的起始点即设置了上下文节点，该节点是 XPath 查询的起始点。</span><span class="sxs-lookup"><span data-stu-id="04ea5-116">Setting the starting point for the XPath query sets the context node, which is the starting point for the XPath query.</span></span> <span data-ttu-id="04ea5-117">如果不希望在文档元素处开始，而是希望从文档元素的第一个子级开始，可以编写 Select 语句的代码，如下所示：</span><span class="sxs-lookup"><span data-stu-id="04ea5-117">If you do not want to start at the document element, but want to start from the first child of the document element, you can code the select statement as follows:</span></span>  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 <span data-ttu-id="04ea5-118">所有 <xref:System.Xml.XmlNodeList> 对象都与基础文档同步。</span><span class="sxs-lookup"><span data-stu-id="04ea5-118">All <xref:System.Xml.XmlNodeList> objects are synchronized with the underlying document.</span></span> <span data-ttu-id="04ea5-119">因此，如果循环访问节点列表并修改某个节点的值，则该节点在包含它的文档中也被更新。</span><span class="sxs-lookup"><span data-stu-id="04ea5-119">Therefore, if you iterate through the node list and modify the value of a node, that node is also updated in the document it came from.</span></span> <span data-ttu-id="04ea5-120">请注意，在上一个示例中，在选定的 <xref:System.Xml.XmlNodeList> 中修改节点时，也会修改基础文档。</span><span class="sxs-lookup"><span data-stu-id="04ea5-120">Notice in the previous example that when a node is modified in the selected <xref:System.Xml.XmlNodeList> the underlying document is also modified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04ea5-121">修改基础文档时，最好重新运行此 Select 语句。</span><span class="sxs-lookup"><span data-stu-id="04ea5-121">When the underlying document is modified, it is advisable to rerun the select.</span></span> <span data-ttu-id="04ea5-122">如果修改的节点可能导致该节点被添加到节点列表（当先前没有添加它时），或者现在会导致它从节点列表中被移除，则无法保证节点列表现在是精确的。</span><span class="sxs-lookup"><span data-stu-id="04ea5-122">If the node modified is one that could cause the node to be added to the node list when it was not previously, or would now cause it to be removed from the node list, there is no guarantee that the node list is now accurate.</span></span>  
  
## <a name="namespaces-in-xpath-expressions"></a><span data-ttu-id="04ea5-123">XPath 表达式中的命名空间</span><span class="sxs-lookup"><span data-stu-id="04ea5-123">Namespaces in XPath Expressions</span></span>  
 <span data-ttu-id="04ea5-124">XPath 表达式可以包含命名空间。</span><span class="sxs-lookup"><span data-stu-id="04ea5-124">XPath expressions can include namespaces.</span></span> <span data-ttu-id="04ea5-125">使用 <xref:System.Xml.XmlNamespaceManager> 支持命名空间解析。</span><span class="sxs-lookup"><span data-stu-id="04ea5-125">Namespace resolution is supported using the <xref:System.Xml.XmlNamespaceManager>.</span></span> <span data-ttu-id="04ea5-126">如果 XPath 表达式包含前缀，前缀和命名空间 URI 对必须添加到 <xref:System.Xml.XmlNamespaceManager>，并且 <xref:System.Xml.XmlNamespaceManager> 传递给 <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> 或 <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="04ea5-126">If the XPath expression includes a prefix, the prefix and namespace URI pair must be added to the <xref:System.Xml.XmlNamespaceManager>, and the <xref:System.Xml.XmlNamespaceManager> is passed to the <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> or <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> method.</span></span> <span data-ttu-id="04ea5-127">请注意，上面的代码示例使用 <xref:System.Xml.XmlNamespaceManager> 来解析 bookstore.xml 文档的命名空间。</span><span class="sxs-lookup"><span data-stu-id="04ea5-127">Notice that the code examples above use the <xref:System.Xml.XmlNamespaceManager> to resolve the namespace of the bookstore.xml document.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04ea5-128">如果 XPath 表达式不包含前缀，则假定命名空间统一资源标识符 (URI) 是空的命名空间。</span><span class="sxs-lookup"><span data-stu-id="04ea5-128">If the XPath expression does not include a prefix, it is assumed that the namespace Uniform Resource Identifier (URI) is the empty namespace.</span></span> <span data-ttu-id="04ea5-129">如果 XML 包含默认命名空间，仍必须将前缀和命名空间 URI 添加到 <xref:System.Xml.XmlNamespaceManager>；否则，不会选择任何节点。</span><span class="sxs-lookup"><span data-stu-id="04ea5-129">If your XML includes a default namespace, you must still add a prefix and namespace URI to the <xref:System.Xml.XmlNamespaceManager>; otherwise, no nodes will be selected.</span></span>  
  
#### <a name="input-file"></a><span data-ttu-id="04ea5-130">输入文件</span><span class="sxs-lookup"><span data-stu-id="04ea5-130">Input File</span></span>  
 <span data-ttu-id="04ea5-131">下面的 bookstore.xml 文件在本主题的示例中用作输入文件。</span><span class="sxs-lookup"><span data-stu-id="04ea5-131">The following is the bookstore.xml file that is used as the input file in the examples in this topic:</span></span>  
  
```xml  
<?xml version='1.0'?>  
<bookstore xmlns="urn:newbooks-schema">  
  <book genre="novel" style="hardcover">  
    <title>The Handmaid's Tale</title>  
    <author>  
      <first-name>Margaret</first-name>  
      <last-name>Atwood</last-name>  
    </author>  
    <price>19.95</price>  
  </book>  
  <book genre="novel" style="other">  
    <title>The Poisonwood Bible</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="novel" style="paperback">  
    <title>The Bean Trees</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>5.99</price>  
  </book>  
</bookstore>  
```  
  
## <a name="see-also"></a><span data-ttu-id="04ea5-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="04ea5-132">See also</span></span>

- [<span data-ttu-id="04ea5-133">XML 文档对象模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="04ea5-133">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
