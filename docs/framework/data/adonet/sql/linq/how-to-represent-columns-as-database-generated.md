---
title: 如何：将列表示为数据库生成的
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: 914fdcb78efbaaddf08330e32e1d7f7c4e62436e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166308"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="459b1-102">如何：将列表示为数据库生成的</span><span class="sxs-lookup"><span data-stu-id="459b1-102">How to: Represent Columns as Database-Generated</span></span>

<span data-ttu-id="459b1-103">使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> 特性上的属性 <xref:System.Data.Linq.Mapping.ColumnAttribute> 可将字段或属性指定为表示数据库生成的列。</span><span class="sxs-lookup"><span data-stu-id="459b1-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="459b1-104">有关代码示例，请参见<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>。</span><span class="sxs-lookup"><span data-stu-id="459b1-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="459b1-105">指定字段或属性表示数据库生成的列</span><span class="sxs-lookup"><span data-stu-id="459b1-105">To designate a field or property as representing a database-generated column</span></span>  
  
1. <span data-ttu-id="459b1-106">将 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> 属性 (Property) 添加到 <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="459b1-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="459b1-107">请将该属性值设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="459b1-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="459b1-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="459b1-108">See also</span></span>

- [<span data-ttu-id="459b1-109">LINQ to SQL 对象模型</span><span class="sxs-lookup"><span data-stu-id="459b1-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="459b1-110">如何：通过使用代码编辑器自定义实体类</span><span class="sxs-lookup"><span data-stu-id="459b1-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
