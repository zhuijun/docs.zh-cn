---
title: LINQ to XML 与DOM (C#)
description: 了解 LINQ to XML 和 W3C 文档对象模型 (DOM) XML 编程 API 之间的一些主要区别。
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: f5fc3fd7869079d47d7c9031e3668afeed7a117b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165347"
---
# <a name="linq-to-xml-vs-dom-c"></a><span data-ttu-id="ac3e7-103">LINQ to XML 与DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="ac3e7-103">LINQ to XML vs. DOM (C#)</span></span>
<span data-ttu-id="ac3e7-104">本节说明 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 和当前主导 XML 编程 API（W3C 文档对象模型 (DOM)）之间的主要区别。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-104">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="ac3e7-105">构造 XML 树的新方式</span><span class="sxs-lookup"><span data-stu-id="ac3e7-105">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="ac3e7-106">在 W3C DOM 中，应当从下至上生成 XML 树；即先创建文档，然后创建元素，再将元素添加到文档。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-106">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="ac3e7-107">例如，下面是使用 DOM 的 Microsoft 实现 <xref:System.Xml.XmlDocument> 创建 XML 树的典型方式：</span><span class="sxs-lookup"><span data-stu-id="ac3e7-107">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
XmlElement phone1 = doc.CreateElement("Phone");  
phone1.SetAttribute("Type", "Home");  
phone1.InnerText = "206-555-0144";
XmlElement phone2 = doc.CreateElement("Phone");  
phone2.SetAttribute("Type", "Work");  
phone2.InnerText = "425-555-0145";
XmlElement street1 = doc.CreateElement("Street1");
street1.InnerText = "123 Main St";  
XmlElement city = doc.CreateElement("City");  
city.InnerText = "Mercer Island";  
XmlElement state = doc.CreateElement("State");  
state.InnerText = "WA";  
XmlElement postal = doc.CreateElement("Postal");  
postal.InnerText = "68042";  
XmlElement address = doc.CreateElement("Address");  
address.AppendChild(street1);  
address.AppendChild(city);  
address.AppendChild(state);  
address.AppendChild(postal);  
XmlElement contact = doc.CreateElement("Contact");  
contact.AppendChild(name);  
contact.AppendChild(phone1);  
contact.AppendChild(phone2);  
contact.AppendChild(address);  
XmlElement contacts = doc.CreateElement("Contacts");  
contacts.AppendChild(contact);  
doc.AppendChild(contacts);  
```  
  
 <span data-ttu-id="ac3e7-108">这种编码方式不会提供很多有关 XML 树结构的可视信息。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-108">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="ac3e7-109">支持用此方法创建 XML 树，但也支持另一种方法，即函数构造。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-109">supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="ac3e7-110">函数构造使用 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XAttribute> 构造函数生成 XML 树。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-110">Functional construction uses the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors to build an XML tree.</span></span>  
  
 <span data-ttu-id="ac3e7-111">下面演示如何通过使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 功能性构造法构造相同的 XML 树：</span><span class="sxs-lookup"><span data-stu-id="ac3e7-111">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144",
                new XAttribute("Type", "Home")),  
            new XElement("phone", "425-555-0145",  
                new XAttribute("Type", "Work")),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="ac3e7-112">请注意，缩进用于构造 XML 树的代码可显示基础 XML 的结构。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-112">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="ac3e7-113">有关详细信息，请参阅[创建 XML 树 (C#)](./linq-to-xml-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-113">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="ac3e7-114">直接使用 XML 元素</span><span class="sxs-lookup"><span data-stu-id="ac3e7-114">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="ac3e7-115">在使用 XML 编程时，主要关注的通常是 XML 元素，也可能关注属性。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-115">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="ac3e7-116">在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中，可以直接使用 XML 元素和属性。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-116">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="ac3e7-117">例如，可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="ac3e7-117">For example, you can do the following:</span></span>  
  
- <span data-ttu-id="ac3e7-118">创建 XML 元素而根本不使用文档对象。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-118">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="ac3e7-119">当必须使用 XML 树的片段时，这可简化编程。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-119">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
- <span data-ttu-id="ac3e7-120">直接从 XML 文件加载 `T:System.Xml.Linq.XElement` 对象。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-120">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
- <span data-ttu-id="ac3e7-121">将 `T:System.Xml.Linq.XElement` 对象序列化为文件或流。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-121">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="ac3e7-122">比较而言，W3C DOM 中的 XML 文档用作 XML 树的逻辑容器。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-122">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="ac3e7-123">在 DOM 中，必须在 XML 文档的上下文中创建 XML 节点，包括元素和属性。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-123">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="ac3e7-124">下面是在 DOM 中创建一个 name 元素的代码片段：</span><span class="sxs-lookup"><span data-stu-id="ac3e7-124">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 <span data-ttu-id="ac3e7-125">如果要跨多个文档使用某个元素，则必须跨文档导入节点。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-125">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="ac3e7-126">避免了这一复杂操作。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-126">avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="ac3e7-127">使用 LINQ to XML 时，仅在文档的根级别添加注释或处理说明时，才需使用 <xref:System.Xml.Linq.XDocument> 类。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-127">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="ac3e7-128">名称和命名空间的简化处理</span><span class="sxs-lookup"><span data-stu-id="ac3e7-128">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="ac3e7-129">处理名称、命名空间和命名空间前缀通常是 XML 编程的复杂部分。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-129">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="ac3e7-130">完全不需要处理命名空间前缀，从而简化了名称和命名空间。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-130">simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="ac3e7-131">可以轻松控制命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-131">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="ac3e7-132">但如果您决定不显式控制命名空间前缀，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 将会在序列化过程中分配命名空间前缀（如果需要）或使用默认命名空间进行序列化（如果不需要）。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-132">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="ac3e7-133">如果使用默认命名空间，则生成的文档中将没有命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-133">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="ac3e7-134">有关详细信息，请参阅[命名空间概述(LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-134">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="ac3e7-135">DOM 的另一个问题是它不允许您更改节点的名称。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-135">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="ac3e7-136">您必须创建新节点并将所有子节点复制到此节点，从而会失去原始节点标识。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-136">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="ac3e7-137">允许对节点设置 <xref:System.Xml.Linq.XName> 属性，因此可避免此问题。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-137">avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="ac3e7-138">对加载 XML 的静态方法支持</span><span class="sxs-lookup"><span data-stu-id="ac3e7-138">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="ac3e7-139">允许您通过使用静态方法而不是实例方法来加载 XML。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-139">lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="ac3e7-140">这简化了加载和分析。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-140">This simplifies loading and parsing.</span></span> <span data-ttu-id="ac3e7-141">有关详细信息，请参阅[如何从文件加载 XML (C#)](./how-to-load-xml-from-a-file.md)。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-141">For more information, see [How to load XML from a file (C#)](./how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="ac3e7-142">移除对 DTD 构造的支持</span><span class="sxs-lookup"><span data-stu-id="ac3e7-142">Removal of Support for DTD Constructs</span></span>  
 <span data-ttu-id="ac3e7-143">通过移除对实体和实体引用的支持，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 进一步简化了 XML 编程。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-143">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="ac3e7-144">实体因管理复杂而很少使用。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-144">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="ac3e7-145">移除对它们的支持可提高性能并简化编程接口。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-145">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="ac3e7-146">在填充 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 树时，会展开所有 DTD 实体。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-146">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="ac3e7-147">对片段的支持</span><span class="sxs-lookup"><span data-stu-id="ac3e7-147">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="ac3e7-148">未提供 `XmlDocumentFragment` 类的等效项。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-148">does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="ac3e7-149">但在很多情况下，`XmlDocumentFragment` 概念都可以通过执行类型化为<xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XNode> 或 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement> 的查询来进行处理。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-149">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="ac3e7-150">对 XPathNavigator 的支持</span><span class="sxs-lookup"><span data-stu-id="ac3e7-150">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="ac3e7-151">通过 <xref:System.Xml.XPath.XPathNavigator> 命名空间中的扩展方法提供对 <xref:System.Xml.XPath?displayProperty=nameWithType> 的支持。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-151">provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="ac3e7-152">有关详细信息，请参阅 <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-152">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="ac3e7-153">对空白和缩进的支持</span><span class="sxs-lookup"><span data-stu-id="ac3e7-153">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="ac3e7-154">处理空白的方式比 DOM 更简单。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-154">handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="ac3e7-155">一种常用情况是读取缩进的 XML，在内存中创建一个没有任何空白文本节点（即不保留空白）的 XML 树，对该 XML 执行某些操作，然后保存带缩进的 XML。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-155">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="ac3e7-156">在序列化带格式的 XML 时，只保留 XML 树中有意义的空白。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-156">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="ac3e7-157">这是 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的默认行为。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-157">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="ac3e7-158">另一个常见的情况是读取和修改已经有意缩进的 XML。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-158">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="ac3e7-159">您可能不想以任何方式更改这种缩进。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-159">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="ac3e7-160">在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中，可以通过在加载或解析 XML 时保留空白，并在序列化 XML 时禁用格式设置来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-160">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="ac3e7-161">将空白存储为 <xref:System.Xml.Linq.XText> 节点，而不像 DOM 那样具有专门的 <xref:System.Xml.XmlNodeType.Whitespace> 节点类型。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-161">stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="ac3e7-162">对批注的支持</span><span class="sxs-lookup"><span data-stu-id="ac3e7-162">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="ac3e7-163">元素支持可扩展的批注集。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-163">elements support an extensible set of annotations.</span></span> <span data-ttu-id="ac3e7-164">这对于跟踪有关元素的杂项信息（如架构信息、关于元素是否绑定到 UI 的信息或应用程序特定的任何其他信息）很有用。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-164">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="ac3e7-165">有关详细信息，请参阅 [LINQ to XML 批注](./linq-to-xml-annotations.md)。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-165">For more information, see [LINQ to XML Annotations](./linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="ac3e7-166">对架构信息的支持</span><span class="sxs-lookup"><span data-stu-id="ac3e7-166">Support for Schema Information</span></span>  
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="ac3e7-167">通过 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空间中的扩展方法提供对 XSD 验证的支持。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-167">provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="ac3e7-168">你可以验证 XML 树是否符合 XSD。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-168">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="ac3e7-169">你可以用架构验证后信息集 (PSVI) 填充 XML 树。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-169">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="ac3e7-170">有关详细信息，请参阅[如何使用 XSD 进行验证](./how-to-validate-using-xsd-linq-to-xml.md)和 <xref:System.Xml.Schema.Extensions>。</span><span class="sxs-lookup"><span data-stu-id="ac3e7-170">For more information, see [How to validate using XSD](./how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ac3e7-171">请参阅</span><span class="sxs-lookup"><span data-stu-id="ac3e7-171">See also</span></span>

- [<span data-ttu-id="ac3e7-172">入门 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="ac3e7-172">Getting Started (LINQ to XML)</span></span>](./linq-to-xml-overview.md)
