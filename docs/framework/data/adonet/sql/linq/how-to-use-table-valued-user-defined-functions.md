---
title: 如何：使用表值用户定义的函数
description: 使用这些示例了解如何创建表值函数，该函数将返回单个行集。 像使用表一样使用此类表值函数。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: 44866367393e321d7dd2db965e2fad8a2e6b63e9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286321"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="0f37c-104">如何：使用表值用户定义的函数</span><span class="sxs-lookup"><span data-stu-id="0f37c-104">How to: Use Table-Valued User-Defined Functions</span></span>
<span data-ttu-id="0f37c-105">表值函数返回单个行集（与存储过程不同，存储过程可返回多个结果形状）。</span><span class="sxs-lookup"><span data-stu-id="0f37c-105">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="0f37c-106">由于表值函数的返回类型为 `Table`，因此在 SQL 中可以使用表的任何地方均可以使用表值函数。</span><span class="sxs-lookup"><span data-stu-id="0f37c-106">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="0f37c-107">此外，您还可以完全像处理表那样来处理表值函数。</span><span class="sxs-lookup"><span data-stu-id="0f37c-107">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f37c-108">示例</span><span class="sxs-lookup"><span data-stu-id="0f37c-108">Example</span></span>  
 <span data-ttu-id="0f37c-109">下面的 SQL 函数显式声明其返回一个 `TABLE`。</span><span class="sxs-lookup"><span data-stu-id="0f37c-109">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="0f37c-110">因此，隐式定义了所返回的行集结构。</span><span class="sxs-lookup"><span data-stu-id="0f37c-110">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```sql
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0f37c-111">按如下方式映射此函数：</span><span class="sxs-lookup"><span data-stu-id="0f37c-111">maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="0f37c-112">示例</span><span class="sxs-lookup"><span data-stu-id="0f37c-112">Example</span></span>  
 <span data-ttu-id="0f37c-113">下面的 SQL 代码说明你可以对此函数返回的表执行联接，以及像处理任何其他表一样处理它：</span><span class="sxs-lookup"><span data-stu-id="0f37c-113">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```sql
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="0f37c-114">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，此查询的呈现结果如下：</span><span class="sxs-lookup"><span data-stu-id="0f37c-114">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0f37c-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0f37c-115">See also</span></span>

- [<span data-ttu-id="0f37c-116">用户定义函数</span><span class="sxs-lookup"><span data-stu-id="0f37c-116">User-Defined Functions</span></span>](user-defined-functions.md)
