---
title: 转换中的 XPathNodeIterator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2bc6ddc6-674a-4f75-b264-abc35e4e5857
ms.openlocfilehash: 88b8f4acbb9fa92d71659ee006ee544275353954
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282748"
---
# <a name="xpathnodeiterator-in-transformations"></a><span data-ttu-id="a5657-102">转换中的 XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="a5657-102">XPathNodeIterator in Transformations</span></span>
<span data-ttu-id="a5657-103"><xref:System.Xml.XPath.XPathNodeIterator> 提供的方法可以循环访问执行 XML 路径语言 (XPath) 查询所创建的节点集或者使用 node-set 方法转换成节点集的结果树片段。</span><span class="sxs-lookup"><span data-stu-id="a5657-103">The <xref:System.Xml.XPath.XPathNodeIterator> provides methods to iterate over a set of nodes created as the result of an XML Path Language (XPath) query or a result tree fragment converted to a node set by use of the node-set method.</span></span> <span data-ttu-id="a5657-104"><xref:System.Xml.XPath.XPathNodeIterator> 使您能够循环访问该节点集内的节点。</span><span class="sxs-lookup"><span data-stu-id="a5657-104">The <xref:System.Xml.XPath.XPathNodeIterator> enables you to iterate over the nodes within that node set.</span></span> <span data-ttu-id="a5657-105">检索到节点集后，<xref:System.Xml.XPath.XPathNodeIterator> 类提供对选定节点集的只读、只进游标。</span><span class="sxs-lookup"><span data-stu-id="a5657-105">Once a node set is retrieved, the <xref:System.Xml.XPath.XPathNodeIterator> class provides a read-only, forward-only cursor to the selected set of nodes.</span></span> <span data-ttu-id="a5657-106">该节点集以文档顺序创建，因此调用此方法会移到文档顺序中的下一个节点。</span><span class="sxs-lookup"><span data-stu-id="a5657-106">The node set is created in document order, so calling this method moves to the next node in document order.</span></span> <span data-ttu-id="a5657-107"><xref:System.Xml.XPath.XPathNodeIterator> 不生成节点集内所有节点的节点树，</span><span class="sxs-lookup"><span data-stu-id="a5657-107"><xref:System.Xml.XPath.XPathNodeIterator> does not build a node tree of all the nodes in the set.</span></span> <span data-ttu-id="a5657-108">而是提供数据的单节点窗口，当你在树中浏览时，会公开所指向的基础节点。</span><span class="sxs-lookup"><span data-stu-id="a5657-108">Instead, it provides a single node window into the data, exposing the underlying node it points to as you move around in the tree.</span></span> <span data-ttu-id="a5657-109"><xref:System.Xml.XPath.XPathNodeIterator> 类中可用的方法和属性使您能够获取当前节点中的信息。</span><span class="sxs-lookup"><span data-stu-id="a5657-109">The methods and properties available from the <xref:System.Xml.XPath.XPathNodeIterator> class enable you to get information from the current node.</span></span> <span data-ttu-id="a5657-110">有关可用方法和属性的列表，请参阅 <xref:System.Windows.Forms.ToolBar>。</span><span class="sxs-lookup"><span data-stu-id="a5657-110">For a list of the available methods and properties, see <xref:System.Windows.Forms.ToolBar>.</span></span>  
  
 <span data-ttu-id="a5657-111">由于 <xref:System.Xml.XPath.XPathNodeIterator> 在 XPath 查询创建的节点集中移动，并且只向前移动，因此，移动方法是使用 <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a5657-111">Since an <xref:System.Xml.XPath.XPathNodeIterator> moves over a set of nodes created from an XPath query and moves forward only, the way to move is by using the <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> method.</span></span> <span data-ttu-id="a5657-112">此方法的返回类型是 `Boolean`，如果移到下一选定节点，则返回 `true`，如果再也没有其他选定节点，则返回 `false`。</span><span class="sxs-lookup"><span data-stu-id="a5657-112">The return type of this method is `Boolean`, returning `true` if it moves to the next selected node, and `false` if there are no more selected nodes.</span></span> <span data-ttu-id="a5657-113">如果返回 `true`，下表显示了可用的属性：</span><span class="sxs-lookup"><span data-stu-id="a5657-113">If it returns `true`, the following list shows the properties available:</span></span>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 <span data-ttu-id="a5657-114">第一次查看一个节点集时，必须调用 <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> 以将 <xref:System.Xml.XPath.XPathNodeIterator> 定位在选定节点集的第一个节点上。</span><span class="sxs-lookup"><span data-stu-id="a5657-114">When you are looking at a node set for the first time, a call to <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> must be made to position the <xref:System.Xml.XPath.XPathNodeIterator> on the first node of the selected set.</span></span> <span data-ttu-id="a5657-115">这样可以编写 while 循环。</span><span class="sxs-lookup"><span data-stu-id="a5657-115">This allows a while loop to be written.</span></span>  
  
 <span data-ttu-id="a5657-116">以下代码示例显示如何将 <xref:System.Xml.XPath.XPathNodeIterator> 作为 <xref:System.Xml.Xsl.XslTransform> 中的参数传递给 <xref:System.Xml.Xsl.XsltArgumentList>。</span><span class="sxs-lookup"><span data-stu-id="a5657-116">The following code example shows how to pass an <xref:System.Xml.XPath.XPathNodeIterator> to an <xref:System.Xml.Xsl.XslTransform> as a parameter in the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span> <span data-ttu-id="a5657-117">代码输入是 books.xml  ，样式表是 text.xsl  。</span><span class="sxs-lookup"><span data-stu-id="a5657-117">The input to the code is **books.xml**, and the style sheet is **text.xsl**.</span></span> <span data-ttu-id="a5657-118">文件 test.xml  是 <xref:System.Xml.XPath.XPathDocument>。</span><span class="sxs-lookup"><span data-stu-id="a5657-118">The file **test.xml** is the <xref:System.Xml.XPath.XPathDocument>.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Xsl  
Imports System.Xml.XPath  
Imports System.Text  
  
Public Class sample  
  
   Public Shared Sub Main()  
      Dim Doc As New XPathDocument("books.xml")  
      Dim nav As XPathNavigator = Doc.CreateNavigator()  
      Dim Iterator As XPathNodeIterator = nav.Select("/bookstore/book")  
  
      Dim arg As New XsltArgumentList()  
      arg.AddParam("param1", "", Iterator)  
  
      Dim xslt As New XslTransform()  
      xslt.Load("test.xsl")  
  
      Dim xd As New XPathDocument("test.xml")  
  
      Dim strmTemp = New FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite)  
      xslt.Transform(xd, arg, strmTemp, Nothing)  
   End Sub 'Main  
End Class 'sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Xsl;  
using System.Xml.XPath;  
using System.Text;  
  
public class sample  
{  
    public static void Main()  
    {  
        XPathDocument Doc = new XPathDocument("books.xml");  
        XPathNavigator nav = Doc.CreateNavigator();  
        XPathNodeIterator Iterator = nav.Select("/bookstore/book");  
  
        XsltArgumentList arg = new XsltArgumentList();  
        arg.AddParam("param1", "", Iterator);  
  
        XslTransform xslt = new XslTransform();  
        xslt.Load("test.xsl");  
  
        XPathDocument xd = new XPathDocument("test.xml");  
  
        Stream strmTemp = new FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite);  
        xslt.Transform(xd, arg, strmTemp, null);  
    }  
}  
```  
  
## <a name="booksxml"></a><span data-ttu-id="a5657-119">books.xml</span><span class="sxs-lookup"><span data-stu-id="a5657-119">books.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<!-- This file represents a fragment of a book store inventory database. -->  
<bookstore specialty="novel">  
    <book style="autobiography">  
    <title>Seven Years in Trenton</title>  
        <author>  
            <first-name>Jay</first-name>  
            <last-name>Adams</last-name>  
            <award>Trenton Literary Review Honorable Mention</award>  
            <country>USA</country>  
        </author>  
        <price>12</price>  
    </book>  
    <book style="textbook">  
        <title>History of Trenton</title>  
        <author>  
            <first-name>Kim</first-name>  
            <last-name>Akers</last-name>  
            <publication>  
                Selected Short Stories of  
                <first-name>Scott</first-name>  
                <last-name>Bishop</last-name>  
                <country>US</country>  
            </publication>  
        </author>  
        <price>55</price>  
    </book>  
</bookstore>  
```  
  
## <a name="testxsl"></a><span data-ttu-id="a5657-120">test.xsl</span><span class="sxs-lookup"><span data-stu-id="a5657-120">test.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
xmlns:msxsl="urn:schemas-microsoft-com:xslt" exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes"/>  
<xsl:param name="param1"/>  
  
<xsl:template match="/">  
    <out>  
        <xsl:for-each select="$param1/title">  
            <title><xsl:value-of select="."/></title>  
        </xsl:for-each>  
    </out>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="testxml"></a><span data-ttu-id="a5657-121">test.xml</span><span class="sxs-lookup"><span data-stu-id="a5657-121">test.xml</span></span>  
  
```xml  
<Title attr="Test">this is a test</Title>  
```  
  
## <a name="output-outxml"></a><span data-ttu-id="a5657-122">输出 (out.xml)</span><span class="sxs-lookup"><span data-stu-id="a5657-122">Output (out.xml)</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<out>  
  <title>Seven Years in Trenton</title>  
  <title>History of Trenton</title>  
</out>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5657-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="a5657-123">See also</span></span>

- [<span data-ttu-id="a5657-124">XslTransform 类实现 XSLT 处理器</span><span class="sxs-lookup"><span data-stu-id="a5657-124">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
