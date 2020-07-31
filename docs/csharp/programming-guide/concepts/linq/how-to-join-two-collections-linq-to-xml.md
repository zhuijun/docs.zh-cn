---
title: 如何联接两个集合 (LINQ to XML) (C#)
description: 此 C# 示例将 LINQ to XML 中的元素联接到其他元素，并生成一个新的 XML 文档。
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: 10792ed4907e778b41821c9b32574bd8fc0ab35f
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104999"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="4eebf-103">如何联接两个集合 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4eebf-103">How to join two collections (LINQ to XML) (C#)</span></span>

<span data-ttu-id="4eebf-104">XML 文档中的元素或属性有时可以引用另一个其他元素或属性。</span><span class="sxs-lookup"><span data-stu-id="4eebf-104">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="4eebf-105">例如，[示例 XML 文件：客户和订单 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML 文档包含一个客户列表和一个订单列表。</span><span class="sxs-lookup"><span data-stu-id="4eebf-105">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="4eebf-106">每个 `Customer` 元素都包含一个 `CustomerID` 属性。</span><span class="sxs-lookup"><span data-stu-id="4eebf-106">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="4eebf-107">每个 `Order` 元素都包含一个 `CustomerID` 元素。</span><span class="sxs-lookup"><span data-stu-id="4eebf-107">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="4eebf-108">每个订单中的 `CustomerID` 元素都引用客户中的 `CustomerID` 属性。</span><span class="sxs-lookup"><span data-stu-id="4eebf-108">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>

<span data-ttu-id="4eebf-109">主题[示例 XSD 文件：客户和订单](./sample-xsd-file-customers-and-orders1.md)包含可用于验证此文档的 XSD。</span><span class="sxs-lookup"><span data-stu-id="4eebf-109">The topic [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="4eebf-110">它使用 XSD 的 `xs:key` 和 `xs:keyref` 功能，将 `CustomerID` 元素的 `Customer` 属性设置为键，并在每个 `CustomerID` 元素的 `Order` 元素和每个 `CustomerID` 元素的 `Customer` 属性之间建立关系。</span><span class="sxs-lookup"><span data-stu-id="4eebf-110">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>

<span data-ttu-id="4eebf-111">使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，可以通过使用 `join` 子句利用这种关系。</span><span class="sxs-lookup"><span data-stu-id="4eebf-111">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>

<span data-ttu-id="4eebf-112">由于没有可用的索引，这种联接的运行时性能较差。</span><span class="sxs-lookup"><span data-stu-id="4eebf-112">Because there is no index available, such joining will have poor run-time performance.</span></span>

<span data-ttu-id="4eebf-113">有关 `join` 的详细信息，请参阅[联接操作 (C#)](./join-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="4eebf-113">For more detailed information about `join`, see [Join Operations (C#)](./join-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="4eebf-114">示例</span><span class="sxs-lookup"><span data-stu-id="4eebf-114">Example</span></span>

<span data-ttu-id="4eebf-115">下面的示例将 `Customer` 元素与 `Order` 元素联接在一起，并生成一个新的 XML 文档，该文档包含订单中的 `CompanyName` 元素。</span><span class="sxs-lookup"><span data-stu-id="4eebf-115">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>

<span data-ttu-id="4eebf-116">执行查询之前，示例确认文档符合[示例 XSD 文件：客户和订单](./sample-xsd-file-customers-and-orders1.md)中的架构。</span><span class="sxs-lookup"><span data-stu-id="4eebf-116">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="4eebf-117">这样可确保联接子句始终能运行。</span><span class="sxs-lookup"><span data-stu-id="4eebf-117">This ensures that the join clause will always work.</span></span>

<span data-ttu-id="4eebf-118">此查询首先检索所有 `Customer` 元素，然后将它们联接到 `Order` 元素。</span><span class="sxs-lookup"><span data-stu-id="4eebf-118">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="4eebf-119">此查询仅选择 `CustomerID` 大于“K”的客户的订单。</span><span class="sxs-lookup"><span data-stu-id="4eebf-119">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="4eebf-120">然后投影一个新的 `Order` 元素，该元素包含每个订单内的客户信息。</span><span class="sxs-lookup"><span data-stu-id="4eebf-120">It then projects a new `Order` element that contains the customer information within each order.</span></span>

<span data-ttu-id="4eebf-121">本示例使用下面的 XML 文档：[示例 XML 文件：客户和订单 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) 的架构定义。</span><span class="sxs-lookup"><span data-stu-id="4eebf-121">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>

<span data-ttu-id="4eebf-122">本示例使用下面的 XSD 架构：[示例 XSD 文件：客户和订单](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="4eebf-122">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>

<span data-ttu-id="4eebf-123">这种方式的联接将不能很好地执行。</span><span class="sxs-lookup"><span data-stu-id="4eebf-123">Joining in this fashion will not perform well.</span></span> <span data-ttu-id="4eebf-124">联接是通过线性搜索执行的。</span><span class="sxs-lookup"><span data-stu-id="4eebf-124">Joins are performed via a linear search.</span></span> <span data-ttu-id="4eebf-125">没有任何哈希表或索引来帮助改善性能。</span><span class="sxs-lookup"><span data-stu-id="4eebf-125">There are no hash tables or indexes to help with performance.</span></span>

```csharp
XmlSchemaSet schemas = new XmlSchemaSet();
schemas.Add("", "CustomersOrders.xsd");

Console.Write("Attempting to validate, ");
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");

bool errors = false;
custOrdDoc.Validate(schemas, (o, e) =>
                     {
                         Console.WriteLine("{0}", e.Message);
                         errors = true;
                     });
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");

if (!errors)
{
    // Join customers and orders, and create a new XML document with
    // a different shape.

    // The new document contains orders only for customers with a
    // CustomerID > 'K'
    XElement custOrd = custOrdDoc.Element("Root");
    XElement newCustOrd = new XElement("Root",
        from c in custOrd.Element("Customers").Elements("Customer")
        join o in custOrd.Element("Orders").Elements("Order")
                   on (string)c.Attribute("CustomerID") equals
                      (string)o.Element("CustomerID")
        where ((string)c.Attribute("CustomerID")).CompareTo("K") > 0
        select new XElement("Order",
            new XElement("CustomerID", (string)c.Attribute("CustomerID")),
            new XElement("CompanyName", (string)c.Element("CompanyName")),
            new XElement("ContactName", (string)c.Element("ContactName")),
            new XElement("EmployeeID", (string)o.Element("EmployeeID")),
            new XElement("OrderDate", (DateTime)o.Element("OrderDate"))
        )
    );
    Console.WriteLine(newCustOrd);
}
```

<span data-ttu-id="4eebf-126">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="4eebf-126">This code produces the following output:</span></span>

```output
Attempting to validate, custOrdDoc validated
<Root>
  <Order>
    <CustomerID>LAZYK</CustomerID>
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <EmployeeID>1</EmployeeID>
    <OrderDate>1997-03-21T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LAZYK</CustomerID>
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <EmployeeID>8</EmployeeID>
    <OrderDate>1997-05-22T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>1</EmployeeID>
    <OrderDate>1997-06-25T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>8</EmployeeID>
    <OrderDate>1997-10-27T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>6</EmployeeID>
    <OrderDate>1997-11-10T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>4</EmployeeID>
    <OrderDate>1998-02-12T00:00:00</OrderDate>
  </Order>
</Root>
```
