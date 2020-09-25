---
title: 如何：指定数据库数据类型
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: f070ff718ac10b9681c5ab3c0f4b46547349101b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197230"
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="8e946-102">如何：指定数据库数据类型</span><span class="sxs-lookup"><span data-stu-id="8e946-102">How to: Specify Database Data Types</span></span>

<span data-ttu-id="8e946-103">使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 特性上的属性 <xref:System.Data.Linq.Mapping.ColumnAttribute> 可以指定在 t-sql 表声明中定义列的确切文本。</span><span class="sxs-lookup"><span data-stu-id="8e946-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="8e946-104">仅当您打算使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 来创建数据库实例时，才必须指定 <xref:System.Data.Linq.DataContext.CreateDatabase%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="8e946-104">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="8e946-105">有关代码示例，请参见<xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>。</span><span class="sxs-lookup"><span data-stu-id="8e946-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="8e946-106">指定用于定义 T-SQL 表中数据类型的文本</span><span class="sxs-lookup"><span data-stu-id="8e946-106">To specify text to define a data type in a T-SQL table</span></span>  
  
1. <span data-ttu-id="8e946-107">将 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 属性 (Property) 添加到 <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="8e946-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="8e946-108">将 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 属性的值设置为 T-SQL 使用的确切文本。</span><span class="sxs-lookup"><span data-stu-id="8e946-108">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e946-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="8e946-109">See also</span></span>

- [<span data-ttu-id="8e946-110">LINQ to SQL 对象模型</span><span class="sxs-lookup"><span data-stu-id="8e946-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="8e946-111">如何：通过使用代码编辑器自定义实体类</span><span class="sxs-lookup"><span data-stu-id="8e946-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
