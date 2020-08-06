---
title: 使用节点进行编程 (C#)
description: 了解如何使用节点进行编程。 通过这种方式，开发人员能够编写比元素和属性更精细的程序。
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 8a31d6459ab644a682d480239cabc3d88fd7dc14
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301679"
---
# <a name="programming-with-nodes-c"></a><span data-ttu-id="5b031-104">使用节点进行编程 (C#)</span><span class="sxs-lookup"><span data-stu-id="5b031-104">Programming with Nodes (C#)</span></span>
<span data-ttu-id="5b031-105">需要编写 XML 编辑器、转换系统或报告编写器这类程序的 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 开发人员通常需要编写在比元素和属性更细的粒度下运行的程序。</span><span class="sxs-lookup"><span data-stu-id="5b031-105">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="5b031-106">开发人员通常需要在节点级别上工作，操作文本节点、处理指令和添加注释。</span><span class="sxs-lookup"><span data-stu-id="5b031-106">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="5b031-107">本主题提供有关在节点级别进行编程的一些详细信息。</span><span class="sxs-lookup"><span data-stu-id="5b031-107">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="5b031-108">节点详细信息</span><span class="sxs-lookup"><span data-stu-id="5b031-108">Node Details</span></span>  
 <span data-ttu-id="5b031-109">在节点级别上工作的程序员需要了解有关编程的许多细节。</span><span class="sxs-lookup"><span data-stu-id="5b031-109">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="5b031-110">XDocument 的子节点的父属性设置为 Null</span><span class="sxs-lookup"><span data-stu-id="5b031-110">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="5b031-111"><xref:System.Xml.Linq.XObject.Parent%2A> 属性包含父 <xref:System.Xml.Linq.XElement>，而不是父节点。</span><span class="sxs-lookup"><span data-stu-id="5b031-111">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="5b031-112"><xref:System.Xml.Linq.XDocument> 的子节点没有父 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="5b031-112">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="5b031-113">它们的父级是文档，因此这些节点的 <xref:System.Xml.Linq.XObject.Parent%2A> 属性设置为 null。</span><span class="sxs-lookup"><span data-stu-id="5b031-113">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="5b031-114">下面的示例演示这一操作：</span><span class="sxs-lookup"><span data-stu-id="5b031-114">The following example demonstrates this:</span></span>  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 <span data-ttu-id="5b031-115">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="5b031-115">This example produces the following output:</span></span>  
  
```output  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="5b031-116">可以存在相邻文本节点</span><span class="sxs-lookup"><span data-stu-id="5b031-116">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="5b031-117">在许多 XML 编程模型中，相邻的文本节点始终会合并到一起。</span><span class="sxs-lookup"><span data-stu-id="5b031-117">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="5b031-118">这有时也称为文本节点的规范化。</span><span class="sxs-lookup"><span data-stu-id="5b031-118">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5b031-119">不规范化文本节点。</span><span class="sxs-lookup"><span data-stu-id="5b031-119">does not normalize text nodes.</span></span> <span data-ttu-id="5b031-120">如果向同一个元素添加两个文本节点，则会产生相邻文本节点。</span><span class="sxs-lookup"><span data-stu-id="5b031-120">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="5b031-121">但如果将指定内容添加为字符串而不是 <xref:System.Xml.Linq.XText> 节点，则 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 可能会将该字符串与相邻的文本节点合并在一起。</span><span class="sxs-lookup"><span data-stu-id="5b031-121">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="5b031-122">下面的示例演示这一操作：</span><span class="sxs-lookup"><span data-stu-id="5b031-122">The following example demonstrates this:</span></span>  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
  
// this does not add a new text node  
xmlTree.Add("new content");  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
  
// this does add a new, adjacent text node  
xmlTree.Add(new XText("more text"));  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
```  
  
 <span data-ttu-id="5b031-123">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="5b031-123">This example produces the following output:</span></span>  
  
```output  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="5b031-124">可以存在空文本节点</span><span class="sxs-lookup"><span data-stu-id="5b031-124">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="5b031-125">在某些 XML 编程模型中，文本节点保证不包含空字符串。</span><span class="sxs-lookup"><span data-stu-id="5b031-125">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="5b031-126">原因是这种文本节点对 XML 的序列化没有影响。</span><span class="sxs-lookup"><span data-stu-id="5b031-126">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="5b031-127">但由于可以存在相邻文本节点这一相同的原因，如果您通过将文本节点的值设置为空字符串来移除文本节点中的文本，则不会删除文本节点本身。</span><span class="sxs-lookup"><span data-stu-id="5b031-127">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);
```  
  
 <span data-ttu-id="5b031-128">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="5b031-128">This example produces the following output:</span></span>  
  
```output  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="5b031-129">空文本节点影响序列化</span><span class="sxs-lookup"><span data-stu-id="5b031-129">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="5b031-130">如果一个元素仅包含一个空的子文本节点，则会用长标记语法序列化该元素：`<Child></Child>`。</span><span class="sxs-lookup"><span data-stu-id="5b031-130">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="5b031-131">如果一个元素不包含任何子节点，则会用短标记语法序列化该元素：`<Child />`。</span><span class="sxs-lookup"><span data-stu-id="5b031-131">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);
```  
  
 <span data-ttu-id="5b031-132">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="5b031-132">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="5b031-133">命名空间是 LINQ to XML 树中的属性</span><span class="sxs-lookup"><span data-stu-id="5b031-133">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="5b031-134">即使命名空间声明与特性具有完全相同的语法，在某些编程接口（如 XSLT 和 XPath）中，也不会将命名空间声明视为属性。</span><span class="sxs-lookup"><span data-stu-id="5b031-134">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="5b031-135">但在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中，命名空间存储为 XML 树中的 <xref:System.Xml.Linq.XAttribute> 对象。</span><span class="sxs-lookup"><span data-stu-id="5b031-135">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="5b031-136">如果您循环访问包含命名空间声明的元素的属性，则会在返回的集合中看到作为一项列出的命名空间声明。</span><span class="sxs-lookup"><span data-stu-id="5b031-136">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="5b031-137"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> 属性 (property) 指示某一属性 (attribute) 是否为命名空间声明。</span><span class="sxs-lookup"><span data-stu-id="5b031-137">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 <span data-ttu-id="5b031-138">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="5b031-138">This example produces the following output:</span></span>  
  
```output  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="5b031-139">XPath 轴方法不返回 XDocument 的子空白</span><span class="sxs-lookup"><span data-stu-id="5b031-139">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5b031-140">允许 <xref:System.Xml.Linq.XDocument> 具有子文本节点，但这些文本节点只能包含空白。</span><span class="sxs-lookup"><span data-stu-id="5b031-140">allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="5b031-141">不过，XPath 对象模型没有将空白符添加为文档子节点。因此，如果使用 <xref:System.Xml.Linq.XDocument> 轴循环访问 <xref:System.Xml.Linq.XContainer.Nodes%2A> 的子级，将会返回空白符文本节点。</span><span class="sxs-lookup"><span data-stu-id="5b031-141">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white-space text nodes will be returned.</span></span> <span data-ttu-id="5b031-142">然而，如果使用 XPath 轴方法循环访问 <xref:System.Xml.Linq.XDocument> 的子级，就不会返回空白符文本节点。</span><span class="sxs-lookup"><span data-stu-id="5b031-142">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white-space text nodes will not be returned.</span></span>  
  
```csharp  
// Create a document with some white-space child nodes of the document.  
XDocument root = XDocument.Parse(  
@"<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
  
<Root/>  
  
<!--a comment-->  
", LoadOptions.PreserveWhitespace);  
  
// count the white-space child nodes using LINQ to XML  
Console.WriteLine(root.Nodes().OfType<XText>().Count());  
  
// count the white-space child nodes using XPathEvaluate  
Console.WriteLine(((IEnumerable)root.XPathEvaluate("text()")).OfType<XText>().Count());
```  
  
 <span data-ttu-id="5b031-143">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="5b031-143">This example produces the following output:</span></span>  
  
```output  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="5b031-144">XDeclaration 对象不是节点</span><span class="sxs-lookup"><span data-stu-id="5b031-144">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="5b031-145">在循环访问 <xref:System.Xml.Linq.XDocument> 的子节点时，将看不到 XML 声明对象。</span><span class="sxs-lookup"><span data-stu-id="5b031-145">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="5b031-146">它是文档的属性，不是文档的子节点。</span><span class="sxs-lookup"><span data-stu-id="5b031-146">It is a property of the document, not a child node of it.</span></span>  
  
```csharp  
XDocument doc = new XDocument(  
    new XDeclaration("1.0", "utf-8", "yes"),  
    new XElement("Root")  
);  
doc.Save("Temp.xml");  
Console.WriteLine(File.ReadAllText("Temp.xml"));  
  
// this shows that there is only one child node of the document  
Console.WriteLine(doc.Nodes().Count());  
```  
  
 <span data-ttu-id="5b031-147">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="5b031-147">This example produces the following output:</span></span>  
  
```output  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  