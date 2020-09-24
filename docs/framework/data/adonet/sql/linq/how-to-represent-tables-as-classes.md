---
title: 如何：将表表示为类
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: c02922351909b097dc06085eefbcc0f131350505
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166217"
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="aaa3a-102">如何：将表表示为类</span><span class="sxs-lookup"><span data-stu-id="aaa3a-102">How to: Represent Tables as Classes</span></span>

<span data-ttu-id="aaa3a-103">使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> 属性将类指定为与数据库表关联的实体类。</span><span class="sxs-lookup"><span data-stu-id="aaa3a-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="aaa3a-104">将类映射到数据库表</span><span class="sxs-lookup"><span data-stu-id="aaa3a-104">To map a class to a database table</span></span>  
  
- <span data-ttu-id="aaa3a-105">将 <xref:System.Data.Linq.Mapping.TableAttribute> 属性添加到类声明中。</span><span class="sxs-lookup"><span data-stu-id="aaa3a-105">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aaa3a-106">示例</span><span class="sxs-lookup"><span data-stu-id="aaa3a-106">Example</span></span>  

 <span data-ttu-id="aaa3a-107">下面的代码创建作为与 `Customer` 数据库表关联的实体类的 `Customers` 类。</span><span class="sxs-lookup"><span data-stu-id="aaa3a-107">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="aaa3a-108">如果可以推断出名称，您无需指定 <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="aaa3a-108">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="aaa3a-109">如果您未指定名称，则假定此名称与此属性或字段的名称相同。</span><span class="sxs-lookup"><span data-stu-id="aaa3a-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaa3a-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="aaa3a-110">See also</span></span>

- [<span data-ttu-id="aaa3a-111">LINQ to SQL 对象模型</span><span class="sxs-lookup"><span data-stu-id="aaa3a-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="aaa3a-112">如何：通过使用代码编辑器自定义实体类</span><span class="sxs-lookup"><span data-stu-id="aaa3a-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
