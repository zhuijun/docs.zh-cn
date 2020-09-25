---
title: 如何：指定数据库名称
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: 82cb3f8f31af433b0299b4fec742b548d61921e4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197152"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="9cabf-102">如何：指定数据库名称</span><span class="sxs-lookup"><span data-stu-id="9cabf-102">How to: Specify Database Names</span></span>

<span data-ttu-id="9cabf-103">使用 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> 属性 (Attribute) 的 <xref:System.Data.Linq.Mapping.DatabaseAttribute> 属性 (Property) 可在连接未提供名称时指定数据库的名称。</span><span class="sxs-lookup"><span data-stu-id="9cabf-103">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="9cabf-104">有关代码示例，请参见<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>。</span><span class="sxs-lookup"><span data-stu-id="9cabf-104">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="9cabf-105">指定数据库的名称</span><span class="sxs-lookup"><span data-stu-id="9cabf-105">To specify the name of the database</span></span>  
  
1. <span data-ttu-id="9cabf-106">将 <xref:System.Data.Linq.Mapping.DatabaseAttribute> 属性添加到数据库的类声明中。</span><span class="sxs-lookup"><span data-stu-id="9cabf-106">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2. <span data-ttu-id="9cabf-107">将 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> 属性 (Property) 添加到 <xref:System.Data.Linq.Mapping.DatabaseAttribute> 属性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="9cabf-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3. <span data-ttu-id="9cabf-108">将 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> 属性值设置为您要指定的名称。</span><span class="sxs-lookup"><span data-stu-id="9cabf-108">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cabf-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="9cabf-109">See also</span></span>

- [<span data-ttu-id="9cabf-110">LINQ to SQL 对象模型</span><span class="sxs-lookup"><span data-stu-id="9cabf-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="9cabf-111">如何：通过使用代码编辑器自定义实体类</span><span class="sxs-lookup"><span data-stu-id="9cabf-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
