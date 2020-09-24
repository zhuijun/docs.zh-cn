---
title: 如何：通过使用代码编辑器自定义实体类
ms.date: 03/30/2017
ms.assetid: ec28332f-9f3c-4e0a-baca-60f9141a68c0
ms.openlocfilehash: 5e61acc9de1ef2f00d5e81a3c3080a9dc46f074d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147692"
---
# <a name="how-to-customize-entity-classes-by-using-the-code-editor"></a><span data-ttu-id="6960c-102">如何：通过使用代码编辑器自定义实体类</span><span class="sxs-lookup"><span data-stu-id="6960c-102">How to: Customize Entity Classes by Using the Code Editor</span></span>

<span data-ttu-id="6960c-103">使用 Visual Studio 的开发人员可以使用对象关系设计器来创建或自定义其实体类。</span><span class="sxs-lookup"><span data-stu-id="6960c-103">Developers using Visual Studio can use the Object Relational Designer to create or customize their entity classes.</span></span>  
  
 <span data-ttu-id="6960c-104">你还可以使用 Visual Studio 代码编辑器编写你自己的映射代码或自定义已生成的代码。</span><span class="sxs-lookup"><span data-stu-id="6960c-104">You can also use the Visual Studio code editor to write your own mapping code or to customize code that has already been generated.</span></span> <span data-ttu-id="6960c-105">有关详细信息，请参阅 [基于属性的映射](attribute-based-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="6960c-105">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
 <span data-ttu-id="6960c-106">本节中的主题说明如何自定义对象模型。</span><span class="sxs-lookup"><span data-stu-id="6960c-106">The topics in this section describe how to customize your object model.</span></span>  
  
 [<span data-ttu-id="6960c-107">如何：指定数据库名称</span><span class="sxs-lookup"><span data-stu-id="6960c-107">How to: Specify Database Names</span></span>](how-to-specify-database-names.md)  
 <span data-ttu-id="6960c-108">描述如何使用 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>。</span><span class="sxs-lookup"><span data-stu-id="6960c-108">Describes how to use <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
 [<span data-ttu-id="6960c-109">如何：将表表示为类</span><span class="sxs-lookup"><span data-stu-id="6960c-109">How to: Represent Tables as Classes</span></span>](how-to-represent-tables-as-classes.md)  
 <span data-ttu-id="6960c-110">描述如何使用 <xref:System.Data.Linq.Mapping.TableAttribute>。</span><span class="sxs-lookup"><span data-stu-id="6960c-110">Describes how to use <xref:System.Data.Linq.Mapping.TableAttribute>.</span></span>  
  
 [<span data-ttu-id="6960c-111">如何：将列表示为类成员</span><span class="sxs-lookup"><span data-stu-id="6960c-111">How to: Represent Columns as Class Members</span></span>](how-to-represent-columns-as-class-members.md)  
 <span data-ttu-id="6960c-112">描述如何使用 <xref:System.Data.Linq.Mapping.ColumnAttribute>。</span><span class="sxs-lookup"><span data-stu-id="6960c-112">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span></span>  
  
 [<span data-ttu-id="6960c-113">如何：表示主键</span><span class="sxs-lookup"><span data-stu-id="6960c-113">How to: Represent Primary Keys</span></span>](how-to-represent-primary-keys.md)  
 <span data-ttu-id="6960c-114">描述如何使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="6960c-114">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
 [<span data-ttu-id="6960c-115">如何：映射数据库关系</span><span class="sxs-lookup"><span data-stu-id="6960c-115">How to: Map Database Relationships</span></span>](how-to-map-database-relationships.md)  
 <span data-ttu-id="6960c-116">提供使用 <xref:System.Data.Linq.Mapping.AssociationAttribute> 属性的示例。</span><span class="sxs-lookup"><span data-stu-id="6960c-116">Provides examples of using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span>  
  
 [<span data-ttu-id="6960c-117">如何：将列表示为数据库生成的</span><span class="sxs-lookup"><span data-stu-id="6960c-117">How to: Represent Columns as Database-Generated</span></span>](how-to-represent-columns-as-database-generated.md)  
 <span data-ttu-id="6960c-118">描述如何使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>。</span><span class="sxs-lookup"><span data-stu-id="6960c-118">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
 [<span data-ttu-id="6960c-119">如何：将列表示为时间戳列或版本列</span><span class="sxs-lookup"><span data-stu-id="6960c-119">How to: Represent Columns as Timestamp or Version Columns</span></span>](how-to-represent-columns-as-timestamp-or-version-columns.md)  
 <span data-ttu-id="6960c-120">描述如何使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>。</span><span class="sxs-lookup"><span data-stu-id="6960c-120">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 [<span data-ttu-id="6960c-121">如何：指定数据库数据类型</span><span class="sxs-lookup"><span data-stu-id="6960c-121">How to: Specify Database Data Types</span></span>](how-to-specify-database-data-types.md)  
 <span data-ttu-id="6960c-122">描述如何使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>。</span><span class="sxs-lookup"><span data-stu-id="6960c-122">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
 [<span data-ttu-id="6960c-123">如何：表示计算所得的列</span><span class="sxs-lookup"><span data-stu-id="6960c-123">How to: Represent Computed Columns</span></span>](how-to-represent-computed-columns.md)  
 <span data-ttu-id="6960c-124">描述如何使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>。</span><span class="sxs-lookup"><span data-stu-id="6960c-124">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
 [<span data-ttu-id="6960c-125">如何：指定专用存储字段</span><span class="sxs-lookup"><span data-stu-id="6960c-125">How to: Specify Private Storage Fields</span></span>](how-to-specify-private-storage-fields.md)  
 <span data-ttu-id="6960c-126">描述如何使用 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>。</span><span class="sxs-lookup"><span data-stu-id="6960c-126">Describes how to use <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
 [<span data-ttu-id="6960c-127">如何：将列表示为允许 Null 值</span><span class="sxs-lookup"><span data-stu-id="6960c-127">How to: Represent Columns as Allowing Null Values</span></span>](how-to-represent-columns-as-allowing-null-values.md)  
 <span data-ttu-id="6960c-128">描述如何使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>。</span><span class="sxs-lookup"><span data-stu-id="6960c-128">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
 [<span data-ttu-id="6960c-129">如何：映射继承层次结构</span><span class="sxs-lookup"><span data-stu-id="6960c-129">How to: Map Inheritance Hierarchies</span></span>](how-to-map-inheritance-hierarchies.md)  
 <span data-ttu-id="6960c-130">说明指定继承层次结构所需的映射。</span><span class="sxs-lookup"><span data-stu-id="6960c-130">Describes the mappings required to specify an inheritance hierarchy.</span></span>  
  
 [<span data-ttu-id="6960c-131">如何：指定并发冲突检查</span><span class="sxs-lookup"><span data-stu-id="6960c-131">How to: Specify Concurrency-Conflict Checking</span></span>](how-to-specify-concurrency-conflict-checking.md)  
 <span data-ttu-id="6960c-132">描述如何使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>。</span><span class="sxs-lookup"><span data-stu-id="6960c-132">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6960c-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="6960c-133">See also</span></span>

- [<span data-ttu-id="6960c-134">SqlMetal.exe（代码生成工具）</span><span class="sxs-lookup"><span data-stu-id="6960c-134">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
