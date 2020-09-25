---
title: 指定无嵌套的元素之间的关系
ms.date: 03/30/2017
ms.assetid: e31325da-7691-4d33-acf4-99fccca67006
ms.openlocfilehash: 6684e992242d5c695f3c237f70de61b4dae1c48f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183398"
---
# <a name="specify-relations-between-elements-with-no-nesting"></a><span data-ttu-id="10c14-102">指定无嵌套的元素之间的关系</span><span class="sxs-lookup"><span data-stu-id="10c14-102">Specify Relations Between Elements with No Nesting</span></span>

<span data-ttu-id="10c14-103">当元素不嵌套时，将不创建任何隐式关系。</span><span class="sxs-lookup"><span data-stu-id="10c14-103">When elements are not nested, no implicit relations are created.</span></span> <span data-ttu-id="10c14-104">但是，可以使用 **msdata： Relationship** 批注显式指定未嵌套的元素之间的关系。</span><span class="sxs-lookup"><span data-stu-id="10c14-104">You can, however, explicitly specify relations between elements that are not nested by using the **msdata:Relationship** annotation.</span></span>  
  
 <span data-ttu-id="10c14-105">下面的示例显示一个 XML 架构，该架构在不嵌套的**Order**和**OrderDetail**元素之间指定**msdata： Relationship**批注。</span><span class="sxs-lookup"><span data-stu-id="10c14-105">The following example shows an XML Schema in which the **msdata:Relationship** annotation is specified between the **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="10c14-106">**Msdata： Relationship**批注指定为**Schema**元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="10c14-106">The **msdata:Relationship** annotation is specified as the child element of the **Schema** element.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
             xmlns:xs="http://www.w3.org/2001/XMLSchema"
             xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:string" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNumber" type="xs:string" />  
           <xs:element name="EmpNumber" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  </xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrderDetailRelation"  
                            msdata:parent="Order"
                            msdata:child="OrderDetail"
                            msdata:parentkey="OrderNumber"
                            msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
</xs:schema>  
```  
  
 <span data-ttu-id="10c14-107">XML 架构定义语言 (XSD) 架构映射过程创建一个 <xref:System.Data.DataSet> With **Order** 和 **OrderDetail** 表以及这两个表之间指定的关系，如下所示。</span><span class="sxs-lookup"><span data-stu-id="10c14-107">The XML Schema definition language (XSD) schema mapping process creates a <xref:System.Data.DataSet> with **Order** and **OrderDetail** tables and a relationship specified between these two tables, as shown below.</span></span>  
  
```text  
RelationName: OrdOrderDetailRelation  
ParentTable: Order  
ParentColumns: OrderNumber
ChildTable: OrderDetail  
ChildColumns: OrderNo
Nested: False  
```  
  
## <a name="see-also"></a><span data-ttu-id="10c14-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="10c14-108">See also</span></span>

- [<span data-ttu-id="10c14-109">从 XML 架构生成数据集关系 (XSD)</span><span class="sxs-lookup"><span data-stu-id="10c14-109">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="10c14-110">将关键 XML 架构 (XSD) 约束映射到数据集约束</span><span class="sxs-lookup"><span data-stu-id="10c14-110">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="10c14-111">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="10c14-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
