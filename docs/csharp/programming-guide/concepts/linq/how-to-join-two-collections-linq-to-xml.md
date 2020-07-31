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
# <a name="how-to-join-two-collections-linq-to-xml-c"></a>如何联接两个集合 (LINQ to XML) (C#)

XML 文档中的元素或属性有时可以引用另一个其他元素或属性。 例如，[示例 XML 文件：客户和订单 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML 文档包含一个客户列表和一个订单列表。 每个 `Customer` 元素都包含一个 `CustomerID` 属性。 每个 `Order` 元素都包含一个 `CustomerID` 元素。 每个订单中的 `CustomerID` 元素都引用客户中的 `CustomerID` 属性。

主题[示例 XSD 文件：客户和订单](./sample-xsd-file-customers-and-orders1.md)包含可用于验证此文档的 XSD。 它使用 XSD 的 `xs:key` 和 `xs:keyref` 功能，将 `CustomerID` 元素的 `Customer` 属性设置为键，并在每个 `CustomerID` 元素的 `Order` 元素和每个 `CustomerID` 元素的 `Customer` 属性之间建立关系。

使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，可以通过使用 `join` 子句利用这种关系。

由于没有可用的索引，这种联接的运行时性能较差。

有关 `join` 的详细信息，请参阅[联接操作 (C#)](./join-operations.md)。

## <a name="example"></a>示例

下面的示例将 `Customer` 元素与 `Order` 元素联接在一起，并生成一个新的 XML 文档，该文档包含订单中的 `CompanyName` 元素。

执行查询之前，示例确认文档符合[示例 XSD 文件：客户和订单](./sample-xsd-file-customers-and-orders1.md)中的架构。 这样可确保联接子句始终能运行。

此查询首先检索所有 `Customer` 元素，然后将它们联接到 `Order` 元素。 此查询仅选择 `CustomerID` 大于“K”的客户的订单。 然后投影一个新的 `Order` 元素，该元素包含每个订单内的客户信息。

本示例使用下面的 XML 文档：[示例 XML 文件：客户和订单 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) 的架构定义。

本示例使用下面的 XSD 架构：[示例 XSD 文件：客户和订单](./sample-xsd-file-customers-and-orders1.md).

这种方式的联接将不能很好地执行。 联接是通过线性搜索执行的。 没有任何哈希表或索引来帮助改善性能。

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

此代码生成以下输出：

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
