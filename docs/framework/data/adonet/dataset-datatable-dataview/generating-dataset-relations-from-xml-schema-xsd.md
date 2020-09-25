---
title: 从 XML 架构生成数据集关系 (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: 2673280ebb94dcc10c130f3969f3e3250d3706a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198582"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="59064-102">从 XML 架构生成数据集关系 (XSD)</span><span class="sxs-lookup"><span data-stu-id="59064-102">Generating DataSet Relations from XML Schema (XSD)</span></span>

<span data-ttu-id="59064-103">在 <xref:System.Data.DataSet> 中，可通过创建父子关系来形成两个或更多个列之间的关联。</span><span class="sxs-lookup"><span data-stu-id="59064-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="59064-104">有三种方法可以表示 XML 架构定义语言中的 **数据集** 关系 (XSD) 架构：</span><span class="sxs-lookup"><span data-stu-id="59064-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
- <span data-ttu-id="59064-105">指定嵌套复杂类型。</span><span class="sxs-lookup"><span data-stu-id="59064-105">Specify nested complex types.</span></span>  
  
- <span data-ttu-id="59064-106">使用 **msdata： Relationship** 批注。</span><span class="sxs-lookup"><span data-stu-id="59064-106">Use the **msdata:Relationship** annotation.</span></span>  
  
- <span data-ttu-id="59064-107">指定不带**msdata： ConstraintOnly**批注的**xs： keyref** 。</span><span class="sxs-lookup"><span data-stu-id="59064-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="59064-108">嵌套的复杂类型</span><span class="sxs-lookup"><span data-stu-id="59064-108">Nested Complex Types</span></span>  

 <span data-ttu-id="59064-109">架构中的嵌套复杂类型定义指示元素的父子关系。</span><span class="sxs-lookup"><span data-stu-id="59064-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="59064-110">下面的 XML 架构片段显示， **OrderDetail** 是 **Order** 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="59064-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
```xml  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>
       <xs:element name="OrderDetail" />  
           <xs:complexType>
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="59064-111">XML 架构映射过程在 **数据集中** 创建与架构中的嵌套复杂类型相对应的表。</span><span class="sxs-lookup"><span data-stu-id="59064-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="59064-112">它还将创建用作 **-** 生成的表的父子列的其他列。</span><span class="sxs-lookup"><span data-stu-id="59064-112">It also creates additional columns that are used as parent**-** child columns for the generated tables.</span></span> <span data-ttu-id="59064-113">请注意，这些父子 **-** 列指定关系，这不同于指定主键/外键约束。</span><span class="sxs-lookup"><span data-stu-id="59064-113">Note that these parent**-** child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="59064-114">msdata:Relationship 批注</span><span class="sxs-lookup"><span data-stu-id="59064-114">msdata:Relationship Annotation</span></span>  

 <span data-ttu-id="59064-115">**Msdata： Relationship**批注允许您显式指定架构中未嵌套的元素之间的父子关系。</span><span class="sxs-lookup"><span data-stu-id="59064-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="59064-116">下面的示例显示了 **关系** 元素的结构。</span><span class="sxs-lookup"><span data-stu-id="59064-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"
msdata:parent=""
msdata:child=""
msdata:parentkey=""
msdata:childkey="" />  
```  
  
 <span data-ttu-id="59064-117">**Msdata： Relationship**批注的属性标识父子关系中涉及的元素，以及关系中涉及的**parentkey**和**childkey**元素和属性。</span><span class="sxs-lookup"><span data-stu-id="59064-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="59064-118">映射过程使用此信息在 **数据集中** 生成表，并在这些表之间创建主键/外键关系。</span><span class="sxs-lookup"><span data-stu-id="59064-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="59064-119">例如，下面的架构片段指定 (未嵌套) 的同一级别的 **Order** 和 **OrderDetail** 元素。</span><span class="sxs-lookup"><span data-stu-id="59064-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="59064-120">该架构指定 **msdata： Relationship** 批注，该批注指定这两个元素之间的父子关系。</span><span class="sxs-lookup"><span data-stu-id="59064-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="59064-121">在这种情况下，必须使用 **msdata： relationship** 批注指定显式关系。</span><span class="sxs-lookup"><span data-stu-id="59064-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
```xml  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
```  
  
 <span data-ttu-id="59064-122">映射过程使用**Relationship**元素在**Order**表的**OrderNumber**列和**数据集**的**OrderDetail**表中的**OrderNo**列之间创建父子关系。</span><span class="sxs-lookup"><span data-stu-id="59064-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="59064-123">映射进程仅指定关系；与关系数据库中的主键/外键约束不同，它并不会自动为这些列中的值指定任何约束。</span><span class="sxs-lookup"><span data-stu-id="59064-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="59064-124">本节内容</span><span class="sxs-lookup"><span data-stu-id="59064-124">In This Section</span></span>  

 [<span data-ttu-id="59064-125">映射嵌套架构元素之间的隐式关系</span><span class="sxs-lookup"><span data-stu-id="59064-125">Map Implicit Relations Between Nested Schema Elements</span></span>](map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="59064-126">描述在 XML 架构中遇到嵌套元素时在 **数据集中** 隐式创建的约束和关系。</span><span class="sxs-lookup"><span data-stu-id="59064-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="59064-127">映射为嵌套元素指定的关系</span><span class="sxs-lookup"><span data-stu-id="59064-127">Map Relations Specified for Nested Elements</span></span>](map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="59064-128">介绍如何在 **数据集中** 为 XML 架构中的嵌套元素显式设置关系。</span><span class="sxs-lookup"><span data-stu-id="59064-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="59064-129">指定无嵌套的元素之间的关系</span><span class="sxs-lookup"><span data-stu-id="59064-129">Specify Relations Between Elements with No Nesting</span></span>](specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="59064-130">介绍如何在未嵌套的 XML 架构元素之间创建 **数据集中** 的关系。</span><span class="sxs-lookup"><span data-stu-id="59064-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="59064-131">相关章节</span><span class="sxs-lookup"><span data-stu-id="59064-131">Related Sections</span></span>  

 [<span data-ttu-id="59064-132">从 XML 架构派生数据集关系结构 (XSD)</span><span class="sxs-lookup"><span data-stu-id="59064-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="59064-133">描述从 XML 架构定义语言 (XSD) 架构创建的 **数据集** 的关系结构（或架构）。</span><span class="sxs-lookup"><span data-stu-id="59064-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="59064-134">将关键 XML 架构 (XSD) 约束映射到数据集约束</span><span class="sxs-lookup"><span data-stu-id="59064-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="59064-135">介绍用于在 **数据集中**创建唯一约束和外键约束的 XML 架构元素。</span><span class="sxs-lookup"><span data-stu-id="59064-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59064-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="59064-136">See also</span></span>

- [<span data-ttu-id="59064-137">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="59064-137">ADO.NET Overview</span></span>](../ado-net-overview.md)
