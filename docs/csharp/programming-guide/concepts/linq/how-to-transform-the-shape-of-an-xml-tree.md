---
title: 如何转换 XML 树的形状 (C#)
description: 了解如何转换 XML 树的形状。 XML 树的形状是指它的元素名称、属性名称以及它的层次结构的特征。
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 4fa3cc18f235d061ae1778c177c4ac9b626f4b71
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302641"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a><span data-ttu-id="b7009-104">如何转换 XML 树的形状 (C#)</span><span class="sxs-lookup"><span data-stu-id="b7009-104">How to transform the shape of an XML tree (C#)</span></span>
<span data-ttu-id="b7009-105">XML 文档的*形状*是指它的元素名称、属性名称以及它的层次结构的特征。</span><span class="sxs-lookup"><span data-stu-id="b7009-105">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="b7009-106">有时，您将不得不更改 XML 文档的形状。</span><span class="sxs-lookup"><span data-stu-id="b7009-106">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="b7009-107">例如，您可能必须将一个现有 XML 文档发送到另一个系统，而该系统要求使用不同的元素和属性名称。</span><span class="sxs-lookup"><span data-stu-id="b7009-107">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="b7009-108">你可以在整个文档中，根据需要删除和重命名元素，但是，如果使用函数构造，则可获得可读性更强、更易于维护的代码。</span><span class="sxs-lookup"><span data-stu-id="b7009-108">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="b7009-109">有关函数构造的详细信息，请参阅[函数构造 (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="b7009-109">For more information about functional construction, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b7009-110">第一个示例更改 XML 文档的组织结构。</span><span class="sxs-lookup"><span data-stu-id="b7009-110">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="b7009-111">它将复杂元素从树中的一个位置移动到另一个位置。</span><span class="sxs-lookup"><span data-stu-id="b7009-111">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="b7009-112">本主题的第二个示例创建一个 XML 文档，该文档具有与源文档不同的形状。</span><span class="sxs-lookup"><span data-stu-id="b7009-112">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="b7009-113">它更改元素名称的大小写，重命名某些元素，转换后的树中不包含源树的某些元素。</span><span class="sxs-lookup"><span data-stu-id="b7009-113">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7009-114">示例</span><span class="sxs-lookup"><span data-stu-id="b7009-114">Example</span></span>  
 <span data-ttu-id="b7009-115">下面的代码使用嵌入式查询表达式更改 XML 文件的形状。</span><span class="sxs-lookup"><span data-stu-id="b7009-115">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="b7009-116">本示例中的源 XML 文档在 `Customers` 元素（它包含所有客户）下包含一个 `Root` 元素。</span><span class="sxs-lookup"><span data-stu-id="b7009-116">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="b7009-117">此外，在 `Orders` 元素（包含所有订单）下包含一个 `Root` 元素。</span><span class="sxs-lookup"><span data-stu-id="b7009-117">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="b7009-118">本示例创建一个新的 XML 树，在该树中，每个客户的订单都包含在 `Orders` 元素内的 `Customer` 元素中。</span><span class="sxs-lookup"><span data-stu-id="b7009-118">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="b7009-119">原始文档还在 `CustomerID` 元素中包含一个 `Order` 元素；此元素将从重新变形的文档中移除。</span><span class="sxs-lookup"><span data-stu-id="b7009-119">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="b7009-120">本示例使用下面的 XML 文档：[示例 XML 文件：客户和订单 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) 的架构定义。</span><span class="sxs-lookup"><span data-stu-id="b7009-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
XElement newCustOrd =  
    new XElement("Root",  
        from cust in co.Element("Customers").Elements("Customer")  
        select new XElement("Customer",  
            cust.Attributes(),  
            cust.Elements(),  
            new XElement("Orders",  
                from ord in co.Element("Orders").Elements("Order")  
                where (string)ord.Element("CustomerID") == (string)cust.Attribute("CustomerID")  
                select new XElement("Order",  
                    ord.Attributes(),  
                    ord.Element("EmployeeID"),  
                    ord.Element("OrderDate"),  
                    ord.Element("RequiredDate"),  
                    ord.Element("ShipInfo")  
                )  
            )  
        )  
    );  
Console.WriteLine(newCustOrd);  
```  
  
 <span data-ttu-id="b7009-121">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="b7009-121">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Customer CustomerID="GREAL">  
    <CompanyName>Great Lakes Food Market</CompanyName>  
    <ContactName>Howard Snyder</ContactName>  
    <ContactTitle>Marketing Manager</ContactTitle>  
    <Phone>(503) 555-7555</Phone>  
    <FullAddress>  
      <Address>2732 Baker Blvd.</Address>  
      <City>Eugene</City>  
      <Region>OR</Region>  
      <PostalCode>97403</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
    <Orders />  
  </Customer>  
  <Customer CustomerID="HUNGC">  
    <CompanyName>Hungry Coyote Import Store</CompanyName>  
    <ContactName>Yoshi Latimer</ContactName>  
    <ContactTitle>Sales Representative</ContactTitle>  
    <Phone>(503) 555-6874</Phone>  
    <Fax>(503) 555-2376</Fax>  
    <FullAddress>  
      <Address>City Center Plaza 516 Main St.</Address>  
      <City>Elgin</City>  
      <Region>OR</Region>  
      <PostalCode>97827</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
    <Orders />  
  </Customer>  
  . . .  
```  
  
## <a name="example"></a><span data-ttu-id="b7009-122">示例</span><span class="sxs-lookup"><span data-stu-id="b7009-122">Example</span></span>  
 <span data-ttu-id="b7009-123">本示例重命名某些元素并将某些属性转换为元素。</span><span class="sxs-lookup"><span data-stu-id="b7009-123">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="b7009-124">代码调用 `ConvertAddress`，它返回一个 <xref:System.Xml.Linq.XElement> 对象列表。</span><span class="sxs-lookup"><span data-stu-id="b7009-124">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="b7009-125">此方法的参数是一个查询，该查询确定 `Address` 属性值为 `Type` 的 `"Shipping"` 复杂元素。</span><span class="sxs-lookup"><span data-stu-id="b7009-125">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="b7009-126">本示例使用下面的 XML 文档：[示例 XML 文件：典型采购订单 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。</span><span class="sxs-lookup"><span data-stu-id="b7009-126">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
static IEnumerable<XElement> ConvertAddress(XElement add)  
{  
    List<XElement> fragment = new List<XElement>() {  
        new XElement("NAME", (string)add.Element("Name")),  
        new XElement("STREET", (string)add.Element("Street")),  
        new XElement("CITY", (string)add.Element("City")),  
        new XElement("ST", (string)add.Element("State")),  
        new XElement("POSTALCODE", (string)add.Element("Zip")),  
        new XElement("COUNTRY", (string)add.Element("Country"))  
    };  
    return fragment;  
}  
  
static void Main(string[] args)  
{  
    XElement po = XElement.Load("PurchaseOrder.xml");  
    XElement newPo = new XElement("PO",  
        new XElement("ID", (string)po.Attribute("PurchaseOrderNumber")),  
        new XElement("DATE", (DateTime)po.Attribute("OrderDate")),  
        ConvertAddress(  
            (from el in po.Elements("Address")  
            where (string)el.Attribute("Type") == "Shipping"  
            select el)  
            .First()  
        )  
    );  
    Console.WriteLine(newPo);  
}  
```  
  
 <span data-ttu-id="b7009-127">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="b7009-127">This code produces the following output:</span></span>  
  
```xml  
<PO>  
  <ID>99503</ID>  
  <DATE>1999-10-20T00:00:00</DATE>  
  <NAME>Ellen Adams</NAME>  
  <STREET>123 Maple Street</STREET>  
  <CITY>Mill Valley</CITY>  
  <ST>CA</ST>  
  <POSTALCODE>10999</POSTALCODE>  
  <COUNTRY>USA</COUNTRY>  
</PO>  
```  
