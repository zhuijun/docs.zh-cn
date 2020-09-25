---
title: 数据集架构接口过程摘要
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 8d517487b96aa7f204ea9f25d326500db7df413a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198504"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a><span data-ttu-id="68e85-102">数据集架构接口过程摘要</span><span class="sxs-lookup"><span data-stu-id="68e85-102">Summary of the DataSet Schema Inference Process</span></span>

<span data-ttu-id="68e85-103">推断过程首先从 XML 文档中确定将哪些元素推断为表。</span><span class="sxs-lookup"><span data-stu-id="68e85-103">The inference process first determines, from the XML document, which elements will be inferred as tables.</span></span> <span data-ttu-id="68e85-104">从剩余的 XML 中，推断过程确定这些表的列。</span><span class="sxs-lookup"><span data-stu-id="68e85-104">From the remaining XML, the inference process determines the columns for those tables.</span></span> <span data-ttu-id="68e85-105">对于嵌套表，推断过程会生成嵌套的 <xref:System.Data.DataRelation> 和 <xref:System.Data.ForeignKeyConstraint> 对象。</span><span class="sxs-lookup"><span data-stu-id="68e85-105">For nested tables, the inference process generates nested <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects.</span></span>  
  
 <span data-ttu-id="68e85-106">下面概述了推理规则：</span><span class="sxs-lookup"><span data-stu-id="68e85-106">The following is a brief summary of inference rules:</span></span>  
  
- <span data-ttu-id="68e85-107">具有属性的元素会被推断为表。</span><span class="sxs-lookup"><span data-stu-id="68e85-107">Elements that have attributes are inferred as tables.</span></span>  
  
- <span data-ttu-id="68e85-108">具有子元素的元素会被推断为表。</span><span class="sxs-lookup"><span data-stu-id="68e85-108">Elements that have child elements are inferred as tables.</span></span>  
  
- <span data-ttu-id="68e85-109">重复的元素会被推断为单个表。</span><span class="sxs-lookup"><span data-stu-id="68e85-109">Elements that repeat are inferred as a single table.</span></span>  
  
- <span data-ttu-id="68e85-110">如果文档元素（即根元素）不具有属性和将被推断为列的子元素，则将被推断为 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="68e85-110">If the document, or root, element has no attributes, and no child elements that would be inferred as columns, it is inferred as a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="68e85-111">否则，文档元素会被推断为表。</span><span class="sxs-lookup"><span data-stu-id="68e85-111">Otherwise, the document element is inferred as a table.</span></span>  
  
- <span data-ttu-id="68e85-112">属性会被推断为列。</span><span class="sxs-lookup"><span data-stu-id="68e85-112">Attributes are inferred as columns.</span></span>  
  
- <span data-ttu-id="68e85-113">不具有属性或子元素且不重复的元素会被推断为列。</span><span class="sxs-lookup"><span data-stu-id="68e85-113">Elements that have no attributes or child elements, and that do not repeat, are inferred as columns.</span></span>  
  
- <span data-ttu-id="68e85-114">对于在其他元素中推断为嵌套表的元素，这些元素也被推断为表，则在这两个表之间创建嵌套的 **DataRelation** 。</span><span class="sxs-lookup"><span data-stu-id="68e85-114">For elements that are inferred as nested tables within other elements that are also inferred as tables, a nested **DataRelation** is created between the two tables.</span></span> <span data-ttu-id="68e85-115">名为 **TableName_Id** 的新主键列将添加到这两个表中，并由 **DataRelation**使用。</span><span class="sxs-lookup"><span data-stu-id="68e85-115">A new, primary key column named **TableName_Id** is added to both tables and used by the **DataRelation**.</span></span> <span data-ttu-id="68e85-116">使用**TableName_Id**列在两个表之间创建一个**ForeignKeyConstraint** 。</span><span class="sxs-lookup"><span data-stu-id="68e85-116">A **ForeignKeyConstraint** is created between the two tables using the **TableName_Id** column.</span></span>  
  
- <span data-ttu-id="68e85-117">对于推断为表并包含文本但没有子元素的元素，将为每个元素的文本创建一个名为 **TableName_Text** 的新列。</span><span class="sxs-lookup"><span data-stu-id="68e85-117">For elements that are inferred as tables and that contain text but have no child elements, a new column named **TableName_Text** is created for the text of each of the elements.</span></span> <span data-ttu-id="68e85-118">如果元素被推断为表并包含文本和子元素，则将忽略文本。</span><span class="sxs-lookup"><span data-stu-id="68e85-118">If an element is inferred as a table and has text, but also has child elements, the text is ignored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e85-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="68e85-119">See also</span></span>

- [<span data-ttu-id="68e85-120">从 XML 推断数据集关系结构</span><span class="sxs-lookup"><span data-stu-id="68e85-120">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="68e85-121">从 XML 加载数据集</span><span class="sxs-lookup"><span data-stu-id="68e85-121">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="68e85-122">从 XML 加载数据集架构信息</span><span class="sxs-lookup"><span data-stu-id="68e85-122">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="68e85-123">在数据集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="68e85-123">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="68e85-124">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="68e85-124">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="68e85-125">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="68e85-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
