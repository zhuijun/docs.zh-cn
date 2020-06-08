---
title: 使用 XmlNameTable 的对象比较
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
ms.openlocfilehash: 0dd68e8c9beadf26f858a4a5100e2824bbbd4a19
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292028"
---
# <a name="object-comparison-using-xmlnametable"></a><span data-ttu-id="6e451-102">使用 XmlNameTable 的对象比较</span><span class="sxs-lookup"><span data-stu-id="6e451-102">Object Comparison Using XmlNameTable</span></span>
<span data-ttu-id="6e451-103">创建后，XmlDocuments  会为相应文档专门创建名称表。</span><span class="sxs-lookup"><span data-stu-id="6e451-103">**XmlDocuments**, when created, have a name table created specifically for that document.</span></span> <span data-ttu-id="6e451-104">将 XML 加载到文档中或新建元素或属性后，属性名和元素名称就会被放入 XmlNameTable  中。</span><span class="sxs-lookup"><span data-stu-id="6e451-104">When XML is loaded into the document, or new elements or attributes are created, the attribute and element names are put into the **XmlNameTable**.</span></span> <span data-ttu-id="6e451-105">还可以使用另一个文档中的现有 NameTable  创建 XmlDocument  。</span><span class="sxs-lookup"><span data-stu-id="6e451-105">You can also create an **XmlDocument** using an existing **NameTable** from another document.</span></span> <span data-ttu-id="6e451-106">如果通过需要使用 XmlNameTable  参数的构造函数创建 XmlDocuments  ，文档有权访问已在 XmlNameTable  中存储的节点名称、命名空间和前缀。</span><span class="sxs-lookup"><span data-stu-id="6e451-106">When **XmlDocuments** are created with the constructor that takes an **XmlNameTable** parameter, the document has access to the node names, namespaces, and prefixes already stored in the **XmlNameTable**.</span></span> <span data-ttu-id="6e451-107">无论如何为名称表加载名称，一旦名称存储在表中，便可以使用对象比较（而不是字符串比较）来快速比较名称。</span><span class="sxs-lookup"><span data-stu-id="6e451-107">Regardless of how the name table is loaded with names, once the names are stored in the table, names can be compared quickly using object comparison instead of string comparison.</span></span> <span data-ttu-id="6e451-108">也可以使用 <xref:System.Xml.NameTable.Add%2A> 将字符串添加到名称表中。</span><span class="sxs-lookup"><span data-stu-id="6e451-108">Strings can also be added to the name table using the <xref:System.Xml.NameTable.Add%2A>.</span></span> <span data-ttu-id="6e451-109">下面的代码示例展示了创建的名称表，以及添加到表中的字符串 MyString  。</span><span class="sxs-lookup"><span data-stu-id="6e451-109">The following code sample shows a name table being created and the string **MyString** being added to the table.</span></span> <span data-ttu-id="6e451-110">完成上述操作之后，使用此表创建 XmlDocument  ，并将 Myfile.xml  中的元素名称和属性名添加到现有名称表中。</span><span class="sxs-lookup"><span data-stu-id="6e451-110">After that, an **XmlDocument** is created using that table, and the element and attribute names in **Myfile.xml** are added to the existing name table.</span></span>  
  
```vb  
Dim nt As New NameTable()  
nt.Add("MyString")  
Dim doc As New XmlDocument(nt)  
doc.Load("Myfile.xml")  
```  
  
```csharp  
NameTable nt = new NameTable();  
nt.Add("MyString");  
XmlDocument doc = new XmlDocument(nt);  
doc.Load("Myfile.xml");  
```  
  
 <span data-ttu-id="6e451-111">下面的代码示例显示文档的创建，添加到该文档中的两个新元素（同时还将这两个元素添加到文档名称表中）以及针对名称进行的对象比较。</span><span class="sxs-lookup"><span data-stu-id="6e451-111">The following code example shows the creation of a document, two new elements being added to the document, which also adds them to the document name table, and the object comparison on the names.</span></span>  
  
```vb  
Dim doc1 As XmlDocument = imp.CreateDocument()  
Dim node1 As XmlElement = doc.CreateElement("node1")  
Dim doc2 As XmlDocument = imp.CreateDocument()  
Dim node2 As XmlElement = doc.CreateElement("node2")  
if (CType(node1.Name, object) = CType(node2.Name, object))  
```  
  
```csharp  
XmlDocument doc1 = imp.CreateDocument();  
node1 = doc1.CreateElement ("node1");  
XmlDocument doc2 = imp.CreateDocument();  
node2 = doc2.CreateElement ("node1");  
if (((object)node1.Name) == ((object)node2.Name))  
{ ...  
```  
  
 <span data-ttu-id="6e451-112">当反复处理同一类型的文档（如电子商务站点的订单文档，该文档符合 XML 架构定义语言 [即 XSD] 或文档类型定义 [即 DTD]）并重复相同的字符串时，通常使用以上在两个文档之间传递名称表的方案。</span><span class="sxs-lookup"><span data-stu-id="6e451-112">The above scenario of a name table passed between two documents is typical when the same type of document is being processed repeatedly, such as order documents at an ecommerce site, which conform to an XML Schema definition language (XSD) schema or document type definition (DTD) and the same strings are repeated.</span></span> <span data-ttu-id="6e451-113">使用同一名称表可提高性能，因为同一元素名出现在多个文档中。</span><span class="sxs-lookup"><span data-stu-id="6e451-113">Using the same name table gives a performance improvement, as the same element name occurs in multiple documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e451-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="6e451-114">See also</span></span>

- [<span data-ttu-id="6e451-115">XML 文档对象模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="6e451-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
