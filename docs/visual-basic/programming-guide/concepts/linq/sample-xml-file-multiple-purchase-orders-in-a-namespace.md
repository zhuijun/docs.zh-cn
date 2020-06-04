---
title: 示例 XML 文件： Namespace3 中的多个采购订单
ms.date: 07/20/2015
ms.assetid: 03f754c6-89f7-4143-8456-4963044be7e5
ms.openlocfilehash: 594ac78a884ce054645fb957b283d8c2abe649de
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413305"
---
# <a name="sample-xml-file-multiple-purchase-orders-in-a-namespace"></a><span data-ttu-id="3ab12-102">示例 XML 文件：命名空间中的多个采购订单</span><span class="sxs-lookup"><span data-stu-id="3ab12-102">Sample XML File: Multiple Purchase Orders in a Namespace</span></span>
<span data-ttu-id="3ab12-103">下面的 XML 文件用在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 文档的很多示例中。</span><span class="sxs-lookup"><span data-stu-id="3ab12-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="3ab12-104">此文件包含多个采购订单。</span><span class="sxs-lookup"><span data-stu-id="3ab12-104">This file contains several purchase orders.</span></span> <span data-ttu-id="3ab12-105">该 XML 在某个命名空间中。</span><span class="sxs-lookup"><span data-stu-id="3ab12-105">The XML is in a namespace.</span></span>  
  
## <a name="purchaseordersinnamespacexml"></a><span data-ttu-id="3ab12-106">PurchaseOrdersInNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="3ab12-106">PurchaseOrdersInNamespace.xml</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<aw:PurchaseOrders xmlns:aw="http://www.adventure-works.com">  
  <aw:PurchaseOrder aw:PurchaseOrderNumber="99503" aw:OrderDate="1999-10-20">  
    <aw:Address aw:Type="Shipping">  
      <aw:Name>Ellen Adams</aw:Name>  
      <aw:Street>123 Maple Street</aw:Street>  
      <aw:City>Mill Valley</aw:City>  
      <aw:State>CA</aw:State>  
      <aw:Zip>10999</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:Address>  
    <aw:Address aw:Type="Billing">  
      <aw:Name>Tai Yee</aw:Name>  
      <aw:Street>8 Oak Avenue</aw:Street>  
      <aw:City>Old Town</aw:City>  
      <aw:State>PA</aw:State>  
      <aw:Zip>95819</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:Address>  
    <aw:DeliveryNotes>Please leave packages in shed by driveway.</aw:DeliveryNotes>  
    <aw:Items>  
      <aw:Item aw:PartNumber="872-AA">  
        <aw:ProductName>Lawnmower</aw:ProductName>  
        <aw:Quantity>1</aw:Quantity>  
        <aw:USPrice>148.95</aw:USPrice>  
        <aw:Comment>Confirm this is electric</aw:Comment>  
      </aw:Item>  
      <aw:Item aw:PartNumber="926-AA">  
        <aw:ProductName>Baby Monitor</aw:ProductName>  
        <aw:Quantity>2</aw:Quantity>  
        <aw:USPrice>39.98</aw:USPrice>  
        <aw:ShipDate>1999-05-21</aw:ShipDate>  
      </aw:Item>  
    </aw:Items>  
  </aw:PurchaseOrder>  
  <aw:PurchaseOrder aw:PurchaseOrderNumber="99505" aw:OrderDate="1999-10-22">  
    <aw:Address aw:Type="Shipping">  
      <aw:Name>Cristian Osorio</aw:Name>  
      <aw:Street>456 Main Street</aw:Street>  
      <aw:City>Buffalo</aw:City>  
      <aw:State>NY</aw:State>  
      <aw:Zip>98112</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:Address>  
    <aw:Address aw:Type="Billing">  
      <aw:Name>Cristian Osorio</aw:Name>  
      <aw:Street>456 Main Street</aw:Street>  
      <aw:City>Buffalo</aw:City>  
      <aw:State>NY</aw:State>  
      <aw:Zip>98112</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:Address>  
    <aw:DeliveryNotes>Please notify me before shipping.</aw:DeliveryNotes>  
    <aw:Items>  
      <aw:Item aw:PartNumber="456-NM">  
        <aw:ProductName>Power Supply</aw:ProductName>  
        <aw:Quantity>1</aw:Quantity>  
        <aw:USPrice>45.99</aw:USPrice>  
      </aw:Item>  
    </aw:Items>  
  </aw:PurchaseOrder>  
  <aw:PurchaseOrder aw:PurchaseOrderNumber="99504" aw:OrderDate="1999-10-22">  
    <aw:Address aw:Type="Shipping">  
      <aw:Name>Jessica Arnold</aw:Name>  
      <aw:Street>4055 Madison Ave</aw:Street>  
      <aw:City>Seattle</aw:City>  
      <aw:State>WA</aw:State>  
      <aw:Zip>98112</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:Address>  
    <aw:Address aw:Type="Billing">  
      <aw:Name>Jessica Arnold</aw:Name>  
      <aw:Street>4055 Madison Ave</aw:Street>  
      <aw:City>Buffalo</aw:City>  
      <aw:State>NY</aw:State>  
      <aw:Zip>98112</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:Address>  
    <aw:Items>  
      <aw:Item aw:PartNumber="898-AZ">  
        <aw:ProductName>Computer Keyboard</aw:ProductName>  
        <aw:Quantity>1</aw:Quantity>  
        <aw:USPrice>29.99</aw:USPrice>  
      </aw:Item>  
      <aw:Item aw:PartNumber="898-AM">  
        <aw:ProductName>Wireless Mouse</aw:ProductName>  
        <aw:Quantity>1</aw:Quantity>  
        <aw:USPrice>14.99</aw:USPrice>  
      </aw:Item>  
    </aw:Items>  
  </aw:PurchaseOrder>  
</aw:PurchaseOrders>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ab12-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ab12-107">See also</span></span>

- [<span data-ttu-id="3ab12-108">示例 XML 文档 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="3ab12-108">Sample XML Documents (LINQ to XML)</span></span>](sample-xml-documents-linq-to-xml.md)
