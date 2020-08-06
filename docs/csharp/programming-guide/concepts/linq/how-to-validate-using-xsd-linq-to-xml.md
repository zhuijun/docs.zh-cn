---
title: 如何使用 XSD 进行验证 (LINQ to XML) (C#)
description: 了解如何根据 XML 架构定义语言 (XSD) 文件验证 XML 文件。 查看代码示例和其他资源。
ms.date: 07/20/2015
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
ms.openlocfilehash: 3b4d2137d511efbe20e4d31ad27e4975d5444ec9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302628"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-c"></a><span data-ttu-id="49a14-104">如何使用 XSD 进行验证 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="49a14-104">How to validate using XSD (LINQ to XML) (C#)</span></span>
<span data-ttu-id="49a14-105"><xref:System.Xml.Schema> 命名空间包含扩展方法，这些扩展方法可以简化针对 XML 架构定义语言 (XSD) 文件验证 XML 树的过程。</span><span class="sxs-lookup"><span data-stu-id="49a14-105">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="49a14-106">有关更多信息，请参见 <xref:System.Xml.Schema.Extensions.Validate%2A> 方法文档。</span><span class="sxs-lookup"><span data-stu-id="49a14-106">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49a14-107">示例</span><span class="sxs-lookup"><span data-stu-id="49a14-107">Example</span></span>  
 <span data-ttu-id="49a14-108">下面的示例创建一个 <xref:System.Xml.Schema.XmlSchemaSet>，然后针对架构集验证两个 <xref:System.Xml.Linq.XDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="49a14-108">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="49a14-109">其中一个文档为有效文档，而另一个则不是。</span><span class="sxs-lookup"><span data-stu-id="49a14-109">One of the documents is valid, the other is not.</span></span>  
  
```csharp  
string xsdMarkup =  
    @"<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'>  
       <xsd:element name='Root'>  
        <xsd:complexType>  
         <xsd:sequence>  
          <xsd:element name='Child1' minOccurs='1' maxOccurs='1'/>  
          <xsd:element name='Child2' minOccurs='1' maxOccurs='1'/>  
         </xsd:sequence>  
        </xsd:complexType>  
       </xsd:element>  
      </xsd:schema>";  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", XmlReader.Create(new StringReader(xsdMarkup)));  
  
XDocument doc1 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child2", "content1")  
    )  
);  
  
XDocument doc2 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child3", "content1")  
    )  
);  
  
Console.WriteLine("Validating doc1");  
bool errors = false;  
doc1.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc1 {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
Console.WriteLine("Validating doc2");  
errors = false;  
doc2.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc2 {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="49a14-110">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="49a14-110">This example produces the following output:</span></span>  
  
```output  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a><span data-ttu-id="49a14-111">示例</span><span class="sxs-lookup"><span data-stu-id="49a14-111">Example</span></span>  
 <span data-ttu-id="49a14-112">下面的示例按照[示例 XSD 文件：客户和订单](./sample-xsd-file-customers-and-orders1.md)中的架构验证[示例 XML 文件：客户和订单 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) 中的 XML 文档是否有效。</span><span class="sxs-lookup"><span data-stu-id="49a14-112">The following example validates that the XML document from [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) is valid per the schema from [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="49a14-113">然后修改源 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="49a14-113">It then modifies the source XML document.</span></span> <span data-ttu-id="49a14-114">它更改第一个客户的 `CustomerID` 属性。</span><span class="sxs-lookup"><span data-stu-id="49a14-114">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="49a14-115">更改后，订单将指向不存在的客户，因此该 XML 文档不再有效。</span><span class="sxs-lookup"><span data-stu-id="49a14-115">After the change, orders will then refer to a customer that does not exist, so the XML document will no longer validate.</span></span>  
  
 <span data-ttu-id="49a14-116">本示例使用下面的 XML 文档：[示例 XML 文件：客户和订单 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) 的架构定义。</span><span class="sxs-lookup"><span data-stu-id="49a14-116">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="49a14-117">本示例使用下面的 XSD 架构：[示例 XSD 文件：客户和订单](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="49a14-117">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>  
  
```csharp  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", "CustomersOrders.xsd");  
  
Console.WriteLine("Attempting to validate");  
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");  
bool errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
// Modify the source document so that it will not validate.  
custOrdDoc.Root.Element("Orders").Element("Order").Element("CustomerID").Value = "AAAAA";  
Console.WriteLine("Attempting to validate after modification");  
errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="49a14-118">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="49a14-118">This example produces the following output:</span></span>  
  
```output  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a><span data-ttu-id="49a14-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="49a14-119">See also</span></span>

- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [<span data-ttu-id="49a14-120">创建 XML 树 (C#)</span><span class="sxs-lookup"><span data-stu-id="49a14-120">Creating XML Trees (C#)</span></span>](creating-xml-trees-linq-to-xml-2.md)
