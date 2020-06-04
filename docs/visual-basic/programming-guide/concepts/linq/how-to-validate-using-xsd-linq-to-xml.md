---
title: 如何：使用 XSD 进行验证 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: a0fe88d4-4e77-49e7-90de-8953feeccc21
ms.openlocfilehash: fd9931530bde2c47dcc8c7b7363a0d5ffae85b8a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383087"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-visual-basic"></a><span data-ttu-id="03f6c-102">如何：使用 XSD 进行验证（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="03f6c-102">How to: Validate Using XSD (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="03f6c-103"><xref:System.Xml.Schema> 命名空间包含扩展方法，这些扩展方法可以简化针对 XML 架构定义语言 (XSD) 文件验证 XML 树的过程。</span><span class="sxs-lookup"><span data-stu-id="03f6c-103">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="03f6c-104">有关更多信息，请参见 <xref:System.Xml.Schema.Extensions.Validate%2A> 方法文档。</span><span class="sxs-lookup"><span data-stu-id="03f6c-104">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03f6c-105">示例</span><span class="sxs-lookup"><span data-stu-id="03f6c-105">Example</span></span>  
 <span data-ttu-id="03f6c-106">下面的示例创建一个 <xref:System.Xml.Schema.XmlSchemaSet>，然后针对架构集验证两个 <xref:System.Xml.Linq.XDocument> 对象。</span><span class="sxs-lookup"><span data-stu-id="03f6c-106">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="03f6c-107">其中一个文档为有效文档，而另一个则不是。</span><span class="sxs-lookup"><span data-stu-id="03f6c-107">One of the documents is valid, the other is not.</span></span>  
  
```vb  
Dim errors As Boolean = False  
  
Private Sub XSDErrors(ByVal o As Object, ByVal e As ValidationEventArgs)  
    Console.WriteLine("{0}", e.Message)  
    errors = True  
End Sub  
  
Sub Main()  
    Dim xsdMarkup As XElement = _  
        <xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'>  
            <xsd:element name='Root'>  
                <xsd:complexType>  
                    <xsd:sequence>  
                        <xsd:element name='Child1' minOccurs='1' maxOccurs='1'/>  
                        <xsd:element name='Child2' minOccurs='1' maxOccurs='1'/>  
                    </xsd:sequence>  
                </xsd:complexType>  
            </xsd:element>  
        </xsd:schema>  
    Dim schemas As XmlSchemaSet = New XmlSchemaSet()  
    schemas.Add("", xsdMarkup.CreateReader)  
  
    Dim doc1 As XDocument = _  
        <?xml version='1.0'?>  
        <Root>  
            <Child1>content1</Child1>  
            <Child2>content1</Child2>  
        </Root>  
  
    Dim doc2 As XDocument = _  
        <?xml version='1.0'?>  
        <Root>  
            <Child1>content1</Child1>  
            <Child3>content1</Child3>  
        </Root>  
  
    Console.WriteLine("Validating doc1")  
    errors = False  
    doc1.Validate(schemas, AddressOf XSDErrors)  
    Console.WriteLine("doc1 {0}", IIf(errors = True, "did not validate", "validated"))  
  
    Console.WriteLine()  
    Console.WriteLine("Validating doc2")  
    errors = False  
    doc2.Validate(schemas, AddressOf XSDErrors)  
    Console.WriteLine("doc2 {0}", IIf(errors = True, "did not validate", "validated"))  
End Sub  
```  
  
 <span data-ttu-id="03f6c-108">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="03f6c-108">This example produces the following output:</span></span>  
  
```console  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a><span data-ttu-id="03f6c-109">示例</span><span class="sxs-lookup"><span data-stu-id="03f6c-109">Example</span></span>  
 <span data-ttu-id="03f6c-110">下面的示例按照[示例 XSD 文件：客户和订单](sample-xsd-file-customers-and-orders.md)中的架构验证[示例 XML 文件：客户和订单 (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md) 中的 XML 文档是否有效。</span><span class="sxs-lookup"><span data-stu-id="03f6c-110">The following example validates that the XML document from [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md) is valid per the schema from [Sample XSD File: Customers and Orders](sample-xsd-file-customers-and-orders.md).</span></span> <span data-ttu-id="03f6c-111">然后修改源 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="03f6c-111">It then modifies the source XML document.</span></span> <span data-ttu-id="03f6c-112">它更改第一个客户的 `CustomerID` 属性。</span><span class="sxs-lookup"><span data-stu-id="03f6c-112">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="03f6c-113">更改后，订单将指向不存在的客户，因此该 XML 文档不再有效。</span><span class="sxs-lookup"><span data-stu-id="03f6c-113">After the change, orders will then refer to a customer that does not exist, so the XML document will no longer validate.</span></span>  
  
 <span data-ttu-id="03f6c-114">本示例使用下面的 XML 文档：[示例 XML 文件：客户和订单 (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="03f6c-114">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="03f6c-115">本示例使用下面的 XSD 架构：[示例 XSD 文件：客户和订单](sample-xsd-file-customers-and-orders.md)。</span><span class="sxs-lookup"><span data-stu-id="03f6c-115">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](sample-xsd-file-customers-and-orders.md).</span></span>  
  
```vb  
Dim errors As Boolean = False  
  
Private Sub XSDErrors(ByVal o As Object, ByVal e As ValidationEventArgs)  
    Console.WriteLine("{0}", e.Message)  
    errors = True  
End Sub  
  
Sub Main()  
    Dim schemas As XmlSchemaSet = New XmlSchemaSet()  
    schemas.Add("", "CustomersOrders.xsd")  
  
    Console.WriteLine("Attempting to validate")  
    Dim custOrdDoc As XDocument = XDocument.Load("CustomersOrders.xml")  
    errors = False  
    custOrdDoc.Validate(schemas, AddressOf XSDErrors)  
    Console.WriteLine("custOrdDoc {0}", IIf(errors, "did not validate", "validated"))  
  
    Console.WriteLine()  
    ' Modify the source document so that it will not validate.  
    custOrdDoc.<Root>.<Orders>.<Order>.<CustomerID>(0).Value = "AAAAA"  
    Console.WriteLine("Attempting to validate after modification")  
    errors = False  
    custOrdDoc.Validate(schemas, AddressOf XSDErrors)  
    Console.WriteLine("custOrdDoc {0}", IIf(errors, "did not validate", "validated"))  
End Sub  
```  
  
 <span data-ttu-id="03f6c-116">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="03f6c-116">This example produces the following output:</span></span>  
  
```console  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a><span data-ttu-id="03f6c-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="03f6c-117">See also</span></span>

- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [<span data-ttu-id="03f6c-118">创建 XML 树（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="03f6c-118">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
