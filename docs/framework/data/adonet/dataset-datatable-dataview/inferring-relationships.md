---
title: 推断关系
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: ee691eee95c34afdb6374cdd7448d4b44ece3055
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177561"
---
# <a name="inferring-relationships"></a><span data-ttu-id="8e25b-102">推断关系</span><span class="sxs-lookup"><span data-stu-id="8e25b-102">Inferring Relationships</span></span>

<span data-ttu-id="8e25b-103">如果被推断为表的元素具有一个同样被推断为表的子元素，则将在这两个表之间创建 <xref:System.Data.DataRelation>。</span><span class="sxs-lookup"><span data-stu-id="8e25b-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="8e25b-104">名称为 " **ParentTableName_Id** " 的新列将添加到为父元素创建的表和为子元素创建的表中。</span><span class="sxs-lookup"><span data-stu-id="8e25b-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="8e25b-105">此标识列的 **ColumnMapping** 属性将设置为 **mappingtype.attribute**。</span><span class="sxs-lookup"><span data-stu-id="8e25b-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="8e25b-106">列将是父表的自动递增主键，并将用于这两个表之间的 **DataRelation** 。</span><span class="sxs-lookup"><span data-stu-id="8e25b-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="8e25b-107">添加的标识列的数据类型将为 system.exception，这与所有其他推断列的数据类型 **不同，后者**为 **system.string**。</span><span class="sxs-lookup"><span data-stu-id="8e25b-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="8e25b-108"><xref:System.Data.ForeignKeyConstraint>还将**DeleteRule**  =  使用父表和子表中的新列来创建具有 DeleteRule**级联**的。</span><span class="sxs-lookup"><span data-stu-id="8e25b-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="8e25b-109">例如，考虑以下 XML：</span><span class="sxs-lookup"><span data-stu-id="8e25b-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="8e25b-110">推理过程将生成两个表： **Element1** 和 **ChildElement1**。</span><span class="sxs-lookup"><span data-stu-id="8e25b-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="8e25b-111">**Element1**表包含两列： **Element1_Id**和**ChildElement2**。</span><span class="sxs-lookup"><span data-stu-id="8e25b-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="8e25b-112">**Element1_Id**列的**ColumnMapping**属性将设置为**mappingtype.attribute**。</span><span class="sxs-lookup"><span data-stu-id="8e25b-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="8e25b-113">**ChildElement2**列的**ColumnMapping**属性将设置为**mappingtype.attribute**。</span><span class="sxs-lookup"><span data-stu-id="8e25b-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="8e25b-114">**Element1_Id**列将设置为**Element1**表的主键。</span><span class="sxs-lookup"><span data-stu-id="8e25b-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="8e25b-115">**ChildElement1**表包含三列： **attr1**、 **attr2**和**Element1_Id**。</span><span class="sxs-lookup"><span data-stu-id="8e25b-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="8e25b-116">**Attr1**和**Attr2**列的**ColumnMapping**属性将设置为**mappingtype.attribute**。</span><span class="sxs-lookup"><span data-stu-id="8e25b-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="8e25b-117">**Element1_Id**列的**ColumnMapping**属性将设置为**mappingtype.attribute**。</span><span class="sxs-lookup"><span data-stu-id="8e25b-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="8e25b-118">将使用两个表中的**Element1_Id**列创建**DataRelation**和**ForeignKeyConstraint** 。</span><span class="sxs-lookup"><span data-stu-id="8e25b-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="8e25b-119">**数据集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="8e25b-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="8e25b-120">**表：** Element1</span><span class="sxs-lookup"><span data-stu-id="8e25b-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="8e25b-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="8e25b-121">Element1_Id</span></span>|<span data-ttu-id="8e25b-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="8e25b-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="8e25b-123">0</span><span class="sxs-lookup"><span data-stu-id="8e25b-123">0</span></span>|<span data-ttu-id="8e25b-124">Text2</span><span class="sxs-lookup"><span data-stu-id="8e25b-124">Text2</span></span>|  
  
 <span data-ttu-id="8e25b-125">**表：** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="8e25b-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="8e25b-126">attr1</span><span class="sxs-lookup"><span data-stu-id="8e25b-126">attr1</span></span>|<span data-ttu-id="8e25b-127">attr2</span><span class="sxs-lookup"><span data-stu-id="8e25b-127">attr2</span></span>|<span data-ttu-id="8e25b-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="8e25b-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="8e25b-129">value1</span><span class="sxs-lookup"><span data-stu-id="8e25b-129">value1</span></span>|<span data-ttu-id="8e25b-130">value2</span><span class="sxs-lookup"><span data-stu-id="8e25b-130">value2</span></span>|<span data-ttu-id="8e25b-131">0</span><span class="sxs-lookup"><span data-stu-id="8e25b-131">0</span></span>|  
  
 <span data-ttu-id="8e25b-132">**DataRelation：** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="8e25b-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="8e25b-133">**ParentTable：** Element1</span><span class="sxs-lookup"><span data-stu-id="8e25b-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="8e25b-134">**ParentColumn：** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="8e25b-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="8e25b-135">**ChildTable：** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="8e25b-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="8e25b-136">**ChildColumn：** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="8e25b-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="8e25b-137">**嵌套：** True</span><span class="sxs-lookup"><span data-stu-id="8e25b-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="8e25b-138">**ForeignKeyConstraint：** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="8e25b-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="8e25b-139">**列：** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="8e25b-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="8e25b-140">**ParentTable：** Element1</span><span class="sxs-lookup"><span data-stu-id="8e25b-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="8e25b-141">**ChildTable：** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="8e25b-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="8e25b-142">**DeleteRule：** Cascade</span><span class="sxs-lookup"><span data-stu-id="8e25b-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="8e25b-143">**AcceptRejectRule：** 内容</span><span class="sxs-lookup"><span data-stu-id="8e25b-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e25b-144">请参阅</span><span class="sxs-lookup"><span data-stu-id="8e25b-144">See also</span></span>

- [<span data-ttu-id="8e25b-145">从 XML 推断数据集关系结构</span><span class="sxs-lookup"><span data-stu-id="8e25b-145">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="8e25b-146">从 XML 加载数据集</span><span class="sxs-lookup"><span data-stu-id="8e25b-146">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="8e25b-147">从 XML 加载数据集架构信息</span><span class="sxs-lookup"><span data-stu-id="8e25b-147">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="8e25b-148">嵌套 DataRelation</span><span class="sxs-lookup"><span data-stu-id="8e25b-148">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="8e25b-149">在数据集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="8e25b-149">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="8e25b-150">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="8e25b-150">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="8e25b-151">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="8e25b-151">ADO.NET Overview</span></span>](../ado-net-overview.md)
