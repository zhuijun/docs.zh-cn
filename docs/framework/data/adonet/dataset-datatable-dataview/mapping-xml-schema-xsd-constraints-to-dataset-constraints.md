---
title: 将关键 XML 架构 (XSD) 约束映射到数据集约束
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: a2b28b0dcb2e2858c7328854650667f51e83166a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185283"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="a2474-102">将关键 XML 架构 (XSD) 约束映射到数据集约束</span><span class="sxs-lookup"><span data-stu-id="a2474-102">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>

<span data-ttu-id="a2474-103">XML 架构定义语言 (XSD) 允许对它所定义的元素和属性指定约束。</span><span class="sxs-lookup"><span data-stu-id="a2474-103">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="a2474-104">将 XML 架构映射到中的关系架构时 <xref:System.Data.DataSet> ，Xml 架构约束将映射到 **数据集中**的表和列的相应关系约束。</span><span class="sxs-lookup"><span data-stu-id="a2474-104">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="a2474-105">本节讨论以下 XML 架构约束的映射：</span><span class="sxs-lookup"><span data-stu-id="a2474-105">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
- <span data-ttu-id="a2474-106">使用 **unique** 元素指定的唯一性约束。</span><span class="sxs-lookup"><span data-stu-id="a2474-106">The uniqueness constraint specified using the **unique** element.</span></span>  
  
- <span data-ttu-id="a2474-107">使用 **key** 元素指定的键约束。</span><span class="sxs-lookup"><span data-stu-id="a2474-107">The key constraint specified using the **key** element.</span></span>  
  
- <span data-ttu-id="a2474-108">使用 **keyref** 元素指定的 keyref 约束。</span><span class="sxs-lookup"><span data-stu-id="a2474-108">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="a2474-109">使用对元素或属性的约束，可以对任何文档实例中元素的值指定特定的限制。</span><span class="sxs-lookup"><span data-stu-id="a2474-109">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="a2474-110">例如，架构中**Customer**元素的**customerid**子元素的键约束指示**customerid**子元素的值在任何文档实例中必须唯一，并且不允许空值。</span><span class="sxs-lookup"><span data-stu-id="a2474-110">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="a2474-111">为了在文档中建立关系，也可以在文档中的元素和属性之间指定约束。</span><span class="sxs-lookup"><span data-stu-id="a2474-111">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="a2474-112">key 和 keyref 约束用于在架构中指定文档中的约束，从而生成文档元素和属性之间的关系。</span><span class="sxs-lookup"><span data-stu-id="a2474-112">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="a2474-113">映射过程将这些架构约束转换为在 **数据集**内创建的表的适当约束。</span><span class="sxs-lookup"><span data-stu-id="a2474-113">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2474-114">本节内容</span><span class="sxs-lookup"><span data-stu-id="a2474-114">In This Section</span></span>  

 [<span data-ttu-id="a2474-115">将唯一 XML 架构 (XSD) 约束映射到数据集约束</span><span class="sxs-lookup"><span data-stu-id="a2474-115">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="a2474-116">介绍用于在 **数据集中**创建唯一约束的 XML 架构元素。</span><span class="sxs-lookup"><span data-stu-id="a2474-116">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="a2474-117">将关键 XML 架构 (XSD) 约束映射到数据集约束</span><span class="sxs-lookup"><span data-stu-id="a2474-117">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="a2474-118">介绍用于创建键约束的 XML 架构元素 (唯一约束，其中不允许在 **数据集中**) null 值。</span><span class="sxs-lookup"><span data-stu-id="a2474-118">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="a2474-119">将 keyref XML 架构 (XSD) 约束映射到数据集约束</span><span class="sxs-lookup"><span data-stu-id="a2474-119">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="a2474-120">介绍用于在 **数据集中**创建 keyref (外键) 约束的 XML 架构元素。</span><span class="sxs-lookup"><span data-stu-id="a2474-120">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a2474-121">相关章节</span><span class="sxs-lookup"><span data-stu-id="a2474-121">Related Sections</span></span>  

 [<span data-ttu-id="a2474-122">从 XML 架构派生数据集关系结构 (XSD)</span><span class="sxs-lookup"><span data-stu-id="a2474-122">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="a2474-123">描述从 XSD 架构创建的 **数据集** 的关系结构（或架构）。</span><span class="sxs-lookup"><span data-stu-id="a2474-123">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="a2474-124">从 XML 架构生成数据集关系 (XSD)</span><span class="sxs-lookup"><span data-stu-id="a2474-124">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="a2474-125">介绍用于在 **数据集中**的表列之间创建关系的 XML 架构元素。</span><span class="sxs-lookup"><span data-stu-id="a2474-125">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2474-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="a2474-126">See also</span></span>

- [<span data-ttu-id="a2474-127">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="a2474-127">ADO.NET Overview</span></span>](../ado-net-overview.md)
