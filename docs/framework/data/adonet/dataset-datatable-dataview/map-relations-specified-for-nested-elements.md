---
title: 映射为嵌套元素指定的关系
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: f758e1ef2c3786a102dc6bb5f6dd217b20dc5b55
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198543"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="ec797-102">映射为嵌套元素指定的关系</span><span class="sxs-lookup"><span data-stu-id="ec797-102">Map Relations Specified for Nested Elements</span></span>

<span data-ttu-id="ec797-103">架构可以包含 **msdata： Relationship** 批注，以显式指定架构中任意两个元素之间的映射。</span><span class="sxs-lookup"><span data-stu-id="ec797-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="ec797-104">**Msdata： Relationship**中指定的两个元素可以嵌套在架构中，但不必是。</span><span class="sxs-lookup"><span data-stu-id="ec797-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="ec797-105">映射过程使用架构中的 **msdata： Relationship** 来生成两个列之间的主键/外键关系。</span><span class="sxs-lookup"><span data-stu-id="ec797-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="ec797-106">下面的示例显示一个 XML 架构，其中 **OrderDetail** 元素是 **Order**的子元素。</span><span class="sxs-lookup"><span data-stu-id="ec797-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="ec797-107">**Msdata： Relationship**标识这种父子关系，并指定生成的**Order**表的**OrderNumber**列与生成的**OrderDetail**表的**OrderNo**列相关。</span><span class="sxs-lookup"><span data-stu-id="ec797-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
 <xs:complexType>  
  <xs:choice maxOccurs="unbounded">  
   <xs:element name="Order">  
    <xs:complexType>  
     <xs:sequence>  
       <xs:element name="OrderNumber" type="xs:string" />  
       <xs:element name="EmpNumber" type="xs:string" />  
       <xs:element name="OrderDetail">  
          <xs:annotation>  
           <xs:appinfo>  
            <msdata:Relationship name="OrdODRelation"
                                msdata:parent="Order"
                                msdata:child="OrderDetail"
                                msdata:parentkey="OrderNumber"
                                msdata:childkey="OrderNo"/>  
           </xs:appinfo>  
          </xs:annotation>  
          <xs:complexType>  
            <xs:sequence>  
             <xs:element name="OrderNo" type="xs:string" />  
             <xs:element name="ItemNo" type="xs:string" />  
            </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:sequence>  
    </xs:complexType>  
   </xs:element>  
  </xs:choice>  
 </xs:complexType>  
</xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="ec797-108">XML 架构映射过程在 <xref:System.Data.DataSet> 中创建以下内容：</span><span class="sxs-lookup"><span data-stu-id="ec797-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="ec797-109">**Order**和**OrderDetail**表。</span><span class="sxs-lookup"><span data-stu-id="ec797-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- <span data-ttu-id="ec797-110">**Order**表和**OrderDetail**表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="ec797-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="ec797-111">此关系的 **嵌套** 属性设置为 **True** ，因为 **Order** 和 **OrderDetail** 元素嵌套在架构中。</span><span class="sxs-lookup"><span data-stu-id="ec797-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="ec797-112">映射过程不创建任何约束。</span><span class="sxs-lookup"><span data-stu-id="ec797-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec797-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="ec797-113">See also</span></span>

- [<span data-ttu-id="ec797-114">从 XML 架构生成数据集关系 (XSD)</span><span class="sxs-lookup"><span data-stu-id="ec797-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="ec797-115">将关键 XML 架构 (XSD) 约束映射到数据集约束</span><span class="sxs-lookup"><span data-stu-id="ec797-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="ec797-116">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="ec797-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
