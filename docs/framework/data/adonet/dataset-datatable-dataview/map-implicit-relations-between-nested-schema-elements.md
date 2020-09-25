---
title: 映射嵌套架构元素之间的隐式关系
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 32f8bf67242143098717b47c3b7aa175317ba274
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201312"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="3ad89-102">映射嵌套架构元素之间的隐式关系</span><span class="sxs-lookup"><span data-stu-id="3ad89-102">Map Implicit Relations Between Nested Schema Elements</span></span>

<span data-ttu-id="3ad89-103">XML 架构定义语言 (XSD) 架构可以具有相互嵌套的复杂类型。</span><span class="sxs-lookup"><span data-stu-id="3ad89-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="3ad89-104">在这种情况下，映射过程将应用默认映射并在 <xref:System.Data.DataSet> 中创建以下内容：</span><span class="sxs-lookup"><span data-stu-id="3ad89-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="3ad89-105">为每个复杂类型（父和子）创建一个表。</span><span class="sxs-lookup"><span data-stu-id="3ad89-105">One table for each of the complex types (parent and child).</span></span>  
  
- <span data-ttu-id="3ad89-106">如果父代中不存在任何唯一约束，则每个表定义都有一个名为 *TableName*的附加主键列 _Id 其中 *tablename* 是父表的名称。</span><span class="sxs-lookup"><span data-stu-id="3ad89-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
- <span data-ttu-id="3ad89-107">父表上的主键约束，通过将 **IsPrimaryKey** 属性设置为 **True**) ，将其他列标识为主键 (。</span><span class="sxs-lookup"><span data-stu-id="3ad89-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="3ad89-108">该约束以 Constraint\# 的形式来命名，其中 \# 为 1、2、3...。</span><span class="sxs-lookup"><span data-stu-id="3ad89-108">The constraint is named Constraint\# where \# is 1, 2, 3, and so on.</span></span> <span data-ttu-id="3ad89-109">例如，第一个约束的默认名称为 Constraint1。</span><span class="sxs-lookup"><span data-stu-id="3ad89-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
- <span data-ttu-id="3ad89-110">在子表上创建外键约束，该约束将附加列标识为引用父表主键的外键。</span><span class="sxs-lookup"><span data-stu-id="3ad89-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="3ad89-111">约束名为 *ParentTable_ChildTable* 其中 *ParentTable* 是父表的名称， *ChildTable* 是子表的名称。</span><span class="sxs-lookup"><span data-stu-id="3ad89-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
- <span data-ttu-id="3ad89-112">在父表和子表之间创建数据关系。</span><span class="sxs-lookup"><span data-stu-id="3ad89-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="3ad89-113">下面的示例显示一个架构，其中 **OrderDetail** 是 **Order**的子元素。</span><span class="sxs-lookup"><span data-stu-id="3ad89-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
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
  
 <span data-ttu-id="3ad89-114">XML 架构映射过程会在 **数据集中**创建以下内容：</span><span class="sxs-lookup"><span data-stu-id="3ad89-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
- <span data-ttu-id="3ad89-115">**Order**和**OrderDetail**表。</span><span class="sxs-lookup"><span data-stu-id="3ad89-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- <span data-ttu-id="3ad89-116">**Order**表的唯一约束。</span><span class="sxs-lookup"><span data-stu-id="3ad89-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="3ad89-117">请注意， **IsPrimaryKey** 属性设置为 **True**。</span><span class="sxs-lookup"><span data-stu-id="3ad89-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id
    IsPrimaryKey: True  
    ```  
  
- <span data-ttu-id="3ad89-118">**OrderDetail**表的外键约束。</span><span class="sxs-lookup"><span data-stu-id="3ad89-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id
    RelatedTable: Order  
    RelatedColumns: Order_Id
    ```  
  
- <span data-ttu-id="3ad89-119">**Order**表和**OrderDetail**表之间的关系。</span><span class="sxs-lookup"><span data-stu-id="3ad89-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="3ad89-120">此关系的 **嵌套** 属性设置为 **True** ，因为 **Order** 和 **OrderDetail** 元素嵌套在架构中。</span><span class="sxs-lookup"><span data-stu-id="3ad89-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: Order_Id
    ChildTable: OrderDetail  
    ChildColumns: Order_Id
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3ad89-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="3ad89-121">See also</span></span>

- [<span data-ttu-id="3ad89-122">从 XML 架构生成数据集关系 (XSD)</span><span class="sxs-lookup"><span data-stu-id="3ad89-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="3ad89-123">将关键 XML 架构 (XSD) 约束映射到数据集约束</span><span class="sxs-lookup"><span data-stu-id="3ad89-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="3ad89-124">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="3ad89-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
