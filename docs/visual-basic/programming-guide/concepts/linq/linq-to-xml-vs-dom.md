---
title: LINQ to XML 与DOM
ms.date: 07/20/2015
ms.assetid: 18c36130-d598-40b7-9007-828232252978
ms.openlocfilehash: 5813ca410e3e2b1ec284681451d0c0cec6f5e393
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389327"
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a>LINQ to XML 与DOM (Visual Basic)
本节说明 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 和当前主导 XML 编程 API（W3C 文档对象模型 (DOM)）之间的主要区别。  
  
## <a name="new-ways-to-construct-xml-trees"></a>构造 XML 树的新方式  
 在 W3C DOM 中，应当从下至上生成 XML 树；即先创建文档，然后创建元素，再将元素添加到文档。  
  
 例如，下面是使用 DOM 的 Microsoft 实现 <xref:System.Xml.XmlDocument> 创建 XML 树的典型方式：  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
Dim phone1 As XmlElement = doc.CreateElement("Phone")  
phone1.SetAttribute("Type", "Home")  
phone1.InnerText = "206-555-0144"  
Dim phone2 As XmlElement = doc.CreateElement("Phone")  
phone2.SetAttribute("Type", "Work")  
phone2.InnerText = "425-555-0145"  
Dim street1 As XmlElement = doc.CreateElement("Street1")  
street1.InnerText = "123 Main St"  
Dim city As XmlElement = doc.CreateElement("City")  
city.InnerText = "Mercer Island"  
Dim state As XmlElement = doc.CreateElement("State")  
state.InnerText = "WA"  
Dim postal As XmlElement = doc.CreateElement("Postal")  
postal.InnerText = "68042"  
Dim address As XmlElement = doc.CreateElement("Address")  
address.AppendChild(street1)  
address.AppendChild(city)  
address.AppendChild(state)  
address.AppendChild(postal)  
Dim contact As XmlElement = doc.CreateElement("Contact")  
contact.AppendChild(name)  
contact.AppendChild(phone1)  
contact.AppendChild(phone2)  
contact.AppendChild(address)  
Dim contacts As XmlElement = doc.CreateElement("Contacts")  
contacts.AppendChild(contact)  
doc.AppendChild(contacts)  
Console.WriteLine(doc.OuterXml)  
```  
  
 这种编码方式不会提供很多有关 XML 树结构的可视信息。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 支持用此方法创建 XML 树，但也支持另一种方法，即函数构造  。 在 Visual Basic 中，函数构造使用 XML 文本来生成 XML 树。  
  
 下面演示如何通过使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 功能性构造法构造相同的 XML 树：  
  
```vb  
Dim contacts = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="Home">206-555-0144</Phone>  
            <Phone Type="Work">425-555-0145</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 请注意，缩进用于构造 XML 树的代码可显示基础 XML 的结构。  
  
 有关详细信息，请参阅[创建 XML 树（Visual Basic）](creating-xml-trees.md)。  
  
## <a name="working-directly-with-xml-elements"></a>直接使用 XML 元素  
 在使用 XML 编程时，主要关注的通常是 XML 元素，也可能关注属性。 在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中，可以直接使用 XML 元素和属性。 例如，可以执行以下操作：  
  
- 创建 XML 元素而根本不使用文档对象。 当必须使用 XML 树的片段时，这可简化编程。  
  
- 直接从 XML 文件加载 `T:System.Xml.Linq.XElement` 对象。  
  
- 将 `T:System.Xml.Linq.XElement` 对象序列化为文件或流。  
  
 比较而言，W3C DOM 中的 XML 文档用作 XML 树的逻辑容器。 在 DOM 中，必须在 XML 文档的上下文中创建 XML 节点，包括元素和属性。 下面是在 DOM 中创建一个 name 元素的代码片段：  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 如果要跨多个文档使用某个元素，则必须跨文档导入节点。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 避免了这一复杂操作。  
  
 使用 LINQ to XML 时，仅在文档的根级别添加注释或处理说明时，才需使用 <xref:System.Xml.Linq.XDocument> 类。  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>名称和命名空间的简化处理  
 处理名称、命名空间和命名空间前缀通常是 XML 编程的复杂部分。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 完全不需要处理命名空间前缀，从而简化了名称和命名空间。 可以轻松控制命名空间前缀。 但如果您决定不显式控制命名空间前缀，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 将会在序列化过程中分配命名空间前缀（如果需要）或使用默认命名空间进行序列化（如果不需要）。 如果使用默认命名空间，则生成的文档中将没有命名空间前缀。 有关详细信息，请参阅[命名空间概述（LINQ to XML）（Visual Basic）](namespaces-overview-linq-to-xml.md)。  
  
 DOM 的另一个问题是它不允许您更改节点的名称。 您必须创建新节点并将所有子节点复制到此节点，从而会失去原始节点标识。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 允许对节点设置 <xref:System.Xml.Linq.XName> 属性，因此可避免此问题。  
  
## <a name="static-method-support-for-loading-xml"></a>对加载 XML 的静态方法支持  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 允许您通过使用静态方法而不是实例方法来加载 XML。 这简化了加载和分析。 有关详细信息，请参阅[如何：从文件加载 XML （Visual Basic）](how-to-load-xml-from-a-file.md)。  
  
## <a name="removal-of-support-for-dtd-constructs"></a>移除对 DTD 构造的支持  
 通过移除对实体和实体引用的支持，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 进一步简化了 XML 编程。 实体因管理复杂而很少使用。 移除对它们的支持可提高性能并简化编程接口。 在填充 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 树时，会展开所有 DTD 实体。  
  
## <a name="support-for-fragments"></a>对片段的支持  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 未提供 `XmlDocumentFragment` 类的等效项。 但在很多情况下，`XmlDocumentFragment` 概念都可以通过执行类型化为<xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XNode> 或 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement> 的查询来进行处理。  
  
## <a name="support-for-xpathnavigator"></a>对 XPathNavigator 的支持  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 通过 <xref:System.Xml.XPath.XPathNavigator> 命名空间中的扩展方法提供对 <xref:System.Xml.XPath?displayProperty=nameWithType> 的支持。 有关详细信息，请参阅 <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>。  
  
## <a name="support-for-white-space-and-indentation"></a>对空白和缩进的支持  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 处理空白的方式比 DOM 更简单。  
  
 一种常用情况是读取缩进的 XML，在内存中创建一个没有任何空白文本节点（即不保留空白）的 XML 树，对该 XML 执行某些操作，然后保存带缩进的 XML。 在序列化带格式的 XML 时，只保留 XML 树中有意义的空白。 这是 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的默认行为。  
  
 另一个常见的情况是读取和修改已经有意缩进的 XML。 您可能不想以任何方式更改这种缩进。 在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中，可以通过在加载或解析 XML 时保留空白，并在序列化 XML 时禁用格式设置来实现此目的。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 将空白存储为 <xref:System.Xml.Linq.XText> 节点，而不像 DOM 那样具有专门的 <xref:System.Xml.XmlNodeType.Whitespace> 节点类型。  
  
## <a name="support-for-annotations"></a>对批注的支持  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 元素支持可扩展的批注集。 这对于跟踪有关元素的杂项信息（如架构信息、关于元素是否绑定到 UI 的信息或应用程序特定的任何其他信息）很有用。 有关详细信息，请参阅 [LINQ to XML 批注](linq-to-xml-annotations.md)。  
  
## <a name="support-for-schema-information"></a>对架构信息的支持  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 通过 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空间中的扩展方法提供对 XSD 验证的支持。 你可以验证 XML 树是否符合 XSD。 你可以用架构验证后信息集 (PSVI) 填充 XML 树。 有关详细信息，请参阅[如何：使用 XSD 和进行验证](how-to-validate-using-xsd-linq-to-xml.md) <xref:System.Xml.Schema.Extensions> 。  
  
## <a name="see-also"></a>请参阅

- [入门 (LINQ to XML)](getting-started-linq-to-xml.md)
