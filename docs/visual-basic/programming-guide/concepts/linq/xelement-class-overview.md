---
title: XElement 类概述
ms.date: 07/20/2015
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
ms.openlocfilehash: a0e50c8a5a14150ee09a328f4dcdd5bc88363621
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413214"
---
# <a name="xelement-class-overview-visual-basic"></a><span data-ttu-id="0ba2d-102">System.xml.linq.xelement> 类概述（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="0ba2d-102">XElement Class Overview (Visual Basic)</span></span>
<span data-ttu-id="0ba2d-103"><xref:System.Xml.Linq.XElement> 类是 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的基础类之一。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="0ba2d-104">它表示一个 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-104">It represents an XML element.</span></span> <span data-ttu-id="0ba2d-105">可以使用该类创建元素；更改元素内容；添加、更改或删除子元素；向元素中添加属性；或以文本格式序列化元素内容。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="0ba2d-106">还可以与 <xref:System.Xml?displayProperty=nameWithType> 中的其他类（例如 <xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter> 和 <xref:System.Xml.Xsl.XslCompiledTransform>）进行互操作。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="0ba2d-107">XElement 功能</span><span class="sxs-lookup"><span data-stu-id="0ba2d-107">XElement Functionality</span></span>  
 <span data-ttu-id="0ba2d-108">本主题描述 <xref:System.Xml.Linq.XElement> 类提供的功能。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="0ba2d-109">构造 XML 树</span><span class="sxs-lookup"><span data-stu-id="0ba2d-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="0ba2d-110">可以使用各种方式构造 XML 树，包括以下方式：</span><span class="sxs-lookup"><span data-stu-id="0ba2d-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="0ba2d-111">可以在代码中构造 XML 树。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="0ba2d-112">有关详细信息，请参阅[创建 XML 树（Visual Basic）](creating-xml-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-112">For more information, see [Creating XML Trees (Visual Basic)](creating-xml-trees.md).</span></span>  
  
- <span data-ttu-id="0ba2d-113">可以从包括 <xref:System.IO.TextReader>、文本文件或 Web 地址 (URL) 在内的各种源解析 XML。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="0ba2d-114">有关详细信息，请参阅[分析 XML （Visual Basic）](parsing-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-114">For more information, see [Parsing XML (Visual Basic)](parsing-xml.md).</span></span>  
  
- <span data-ttu-id="0ba2d-115">可以使用 <xref:System.Xml.XmlReader> 来填充树。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="0ba2d-116">有关详细信息，请参阅 <xref:System.Xml.Linq.XNode.ReadFrom%2A>。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="0ba2d-117">如果您有一个可以将内容写入 <xref:System.Xml.XmlWriter> 的模块，则可以使用 <xref:System.Xml.Linq.XContainer.CreateWriter%2A> 方法来创建编写器，将该编写器传递到该模块，然后使用写入 <xref:System.Xml.XmlWriter> 的内容来填充 XML 树。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="0ba2d-118">但是，创建 XML 树的最常见的方法如下：</span><span class="sxs-lookup"><span data-stu-id="0ba2d-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 <span data-ttu-id="0ba2d-119">另一个创建 XML 树的十分常用的方法是使用 LINQ 查询的结果来填充 XML 树，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="0ba2d-119">Another very common technique for creating an XML tree involves using the results of a LINQ query to populate an XML tree, as shown in the following example:</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 <span data-ttu-id="0ba2d-120">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="0ba2d-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="0ba2d-121">序列化 XML 树</span><span class="sxs-lookup"><span data-stu-id="0ba2d-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="0ba2d-122">可以将 XML 树序列化为 <xref:System.IO.File>、<xref:System.IO.TextWriter> 或 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="0ba2d-123">有关详细信息，请参阅[序列化 XML 树（Visual Basic）](serializing-xml-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-123">For more information, see [Serializing XML Trees (Visual Basic)](serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="0ba2d-124">通过轴方法检索 XML 数据</span><span class="sxs-lookup"><span data-stu-id="0ba2d-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="0ba2d-125">可以使用轴方法检索属性、子元素、子代元素和上级元素。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="0ba2d-126">LINQ 查询对轴方法进行操作，并提供了多种灵活而有效的方法导航和处理 XML 树。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-126">LINQ queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="0ba2d-127">有关详细信息，请参阅[LINQ to XML 轴（Visual Basic）](linq-to-xml-axes.md)。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-127">For more information, see [LINQ to XML Axes (Visual Basic)](linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="0ba2d-128">查询 XML 树</span><span class="sxs-lookup"><span data-stu-id="0ba2d-128">Querying XML Trees</span></span>  
 <span data-ttu-id="0ba2d-129">可以编写从 XML 树提取数据的 LINQ 查询。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-129">You can write LINQ queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="0ba2d-130">有关详细信息，请参阅[查询 XML 树（Visual Basic）](querying-xml-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-130">For more information, see [Querying XML Trees (Visual Basic)](querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="0ba2d-131">修改 XML 树</span><span class="sxs-lookup"><span data-stu-id="0ba2d-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="0ba2d-132">可以通过各种方式修改元素，例如更改元素的内容或属性。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="0ba2d-133">还可以从元素的父级移除元素。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="0ba2d-134">有关详细信息，请参阅[修改 XML 树（LINQ to XML）（Visual Basic）](modifying-xml-trees-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="0ba2d-134">For more information, see [Modifying XML Trees (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ba2d-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ba2d-135">See also</span></span>

- [<span data-ttu-id="0ba2d-136">LINQ to XML 编程概述（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="0ba2d-136">LINQ to XML Programming Overview (Visual Basic)</span></span>](linq-to-xml-programming-overview.md)
